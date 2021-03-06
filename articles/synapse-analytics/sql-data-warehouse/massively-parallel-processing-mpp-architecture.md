---
title: Arquitectura de Azure Synapse Analytics (anteriormente SQL DW)
description: Obtenga información acerca de cómo combina Azure Synapse Analytics (anteriormente SQL DW) las funcionalidades de procesamiento de consultas distribuidas con Azure Storage para lograr un alto rendimiento y escalabilidad.
services: synapse-analytics
author: mlee3gsd
manager: craigg
ms.service: synapse-analytics
ms.topic: conceptual
ms.subservice: sql-dw
ms.date: 11/04/2019
ms.author: martinle
ms.reviewer: igorstan
ms.openlocfilehash: 1d32aa011e9e816f97b050d43f9558af0cf82e90
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93319648"
---
# <a name="azure-synapse-analytics-formerly-sql-dw-architecture"></a>Arquitectura de Azure Synapse Analytics (anteriormente SQL DW)

Azure Synapse es un servicio de análisis ilimitado que reúne el almacenamiento de datos empresariales y el análisis de macrodatos. Le ofrece la libertad de consultar los datos como prefiera, ya sea a petición sin servidor o con recursos aprovisionados, a escala. Azure Synapse reúne estos dos mundos con una experiencia unificada para ingerir, preparar, administrar y servir datos para las necesidades inmediatas de inteligencia empresarial y aprendizaje automático.

 Azure Synapse tiene cuatro componentes:

- SQL de Synapse: análisis completo basado en T-SQL.

  - Grupo de SQL dedicado (pago por DWU aprovisionada): disponible con carácter general.
  - Grupo de SQL sin servidor (pago por TB procesado): versión preliminar
- Spark: profunda integración con Apache Spark (versión preliminar).
- Integración de datos: integración de datos híbridos (versión preliminar).
- Studio: experiencia de usuario unificada.  (versión preliminar)

> [!VIDEO https://www.youtube.com/embed/PlyQ8yOb8kc]

## <a name="synapse-sql-architecture-components"></a>Componentes de la arquitectura de SQL de Synapse

[SQL de Synapse](sql-data-warehouse-overview-what-is.md#dedicated-sql-pool-in-azure-synapse) aprovecha una arquitectura de escalabilidad horizontal para distribuir el procesamiento de cálculo de datos entre varios nodos. La unidad de escalado es una abstracción de la eficacia de proceso que se conoce como [unidad de almacenamiento de datos](what-is-a-data-warehouse-unit-dwu-cdwu.md). Como el proceso está separado del almacenamiento, se puede escalar con independencia de los datos del sistema.

![Arquitectura de SQL de Synapse](./media/massively-parallel-processing-mpp-architecture/massively-parallel-processing-mpp-architecture.png)

SQL de Synapse usa una arquitectura basada en nodos. Las aplicaciones se conectan y emiten comandos de T-SQL a un nodo de control, que es el único punto de entrada de SQL de Synapse. El nodo de control hospeda el motor de consultas distribuidas, que optimiza las consultas para el procesamiento en paralelo y, después, pasa las operaciones a los nodos de ejecución para hacer su trabajo en paralelo.

Los nodos de ejecución almacenan todos los datos del usuario en Azure Storage y ejecutan las consultas en paralelo. El servicio de movimiento de datos (DMS) es un servicio interno de nivel de sistema que mueve datos entre los nodos según sea necesario para ejecutar consultas en paralelo y devolver resultados precisos.

Con el almacenamiento y el proceso desacoplados, el uso del grupo de SQL de Synapse permite:

- Cambiar la potencia del proceso independientemente de las necesidades de almacenamiento.
- Aumentar o reducir la capacidad de proceso en un grupo de SQL (almacenamiento de datos), sin mover los datos.
- Pausar la capacidad de proceso mientras se dejan los datos intactos, por lo que solo paga por el almacenamiento.
- Reanudar la capacidad de proceso durante las horas operativas.

### <a name="azure-storage"></a>Azure Storage

SQL de Synapse aprovecha Azure Storage para proteger los datos del usuario.  Puesto que los datos se almacenan y administran en Azure Storage, el consumo de almacenamiento se cobra aparte. Los datos están particionados en **distribuciones** para optimizar el rendimiento del sistema. Puede elegir qué modelo de particionamiento quiere usar para distribuir los datos cuando define la tabla. Se admiten estos patrones de particionamiento:

- Hash
- Round Robin
- Replicar

### <a name="control-node"></a>Nodo de control

El nodo de control es el cerebro de la arquitectura. Es el front-end que interactúa con todas las aplicaciones y conexiones. El motor de consultas distribuidas se ejecuta en el nodo de control para optimizar y coordinar las consultas en paralelo. Al enviar una consulta T-SQL, el nodo de control la transforma en consultas que se ejecutan en cada distribución en paralelo.

### <a name="compute-nodes"></a>Nodos de proceso

Los nodos de proceso proporcionan la eficacia de cálculo. Las distribuciones se asignan a nodos de proceso para su procesamiento. A medida que paga por más recursos de proceso, las distribuciones se reasignan a los nodos de ejecución disponibles. El número de nodos de ejecución va de 1 a 60, y viene determinado por el nivel de servicio de SQL de Synapse.

Cada nodo de cálculo tiene un identificador de nodo que está visible en las vistas del sistema. Para ver el identificador del nodo de ejecución, busque la columna node_id en las vistas del sistema cuyos nombres comiencen por sys.pdw_nodes. Para obtener una lista de las vistas del sistema, consulte [Vistas del sistema de Synapse SQL](/sql/relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json&view=azure-sqldw-latest).

### <a name="data-movement-service"></a>Servicio de movimiento de datos

Servicio de movimiento de datos (DMS) es la tecnología de transporte de datos que coordina el movimiento de los datos entre los nodos de proceso. Algunas consultas requieren el movimiento de datos para asegurarse de que las consultas paralelas devuelven resultados precisos. Cuando un movimiento de datos es necesario, DMS asegura que los datos adecuados llegan a la ubicación adecuada.

## <a name="distributions"></a>Distribuciones

Una distribución es la unidad básica de almacenamiento y procesamiento de consultas en paralelo que se ejecutan en datos distribuidos. Cuando Synapse SQL ejecuta una consulta, el trabajo se divide en 60 consultas más pequeñas que se ejecutan en paralelo.

Cada una de estas 60 consultas más pequeñas se ejecuta en una de las distribuciones de datos. Cada nodo de ejecución administra una o más de las 60 distribuciones. Un grupo de SQL con recursos de proceso máximos tiene una distribución por nodo de proceso. Un grupo de SQL con recursos de proceso mínimos tiene todas las distribuciones en un nodo de proceso.  

## <a name="hash-distributed-tables"></a>Tablas distribuidas mediante una función hash

Una tabla con distribución por hash puede ofrecer el máximo rendimiento de consultas para combinaciones y agregaciones en tablas grandes.

Para particionar los datos en una tabla con distribución por hash, se usa una función hash para asignar de una manera determinista cada fila a una distribución. En la definición de tabla, una de las columnas se designa como columna de distribución. La función hash usa el valor de la columna de distribución para asignar cada fila a una distribución.

El siguiente diagrama muestra cómo se almacena una tabla completa (no distribuida) como una tabla distribuida mediante una función hash.

![Tabla distribuida](./media/massively-parallel-processing-mpp-architecture/hash-distributed-table.png "Tabla distribuida")  

- Cada fila pertenece a una distribución.  
- Un algoritmo hash determinista asigna cada fila a una distribución.  
- El número de filas de la tabla por cada distribución varía, lo que se hace patente en los diferentes tamaños de tablas.

Es preciso tener en cuenta consideraciones de rendimiento al seleccionar una columna de distribución, tales como la diferenciación, la asimetría de datos o los tipos de consultas que se ejecutan en el sistema.

## <a name="round-robin-distributed-tables"></a>Tablas distribuidas con el método round robin

Una tabla round robin es la tabla más sencilla de crear y ofrece un rendimiento rápido cuando se usa como tabla de almacenamiento provisional para las cargas.

Una tabla distribuida con el método round robin distribuye los datos uniformemente en la tabla, pero sin ninguna optimización adicional. Una distribución se elige primero de manera aleatoria y, después, los búferes de filas se asignan a las distribuciones secuencialmente. Es rápido cargar datos en una tabla round robin, pero el rendimiento de las consultas puede mejorar con tablas con distribución por hash. Las combinaciones de tablas round robin requieren reconstruir los datos, y esto requiere tiempo adicional.

## <a name="replicated-tables"></a>Tablas replicadas

Una tabla replicada proporciona el rendimiento de consultas más rápido para tablas pequeñas.

Una tabla que se replica tiene una copia completa de la tabla almacenada en la caché de cada nodo de proceso. Por lo tanto, al replicar una tabla se elimina la necesidad de transferir sus datos de un nodo de proceso a otro antes de una combinación o agregación. Las tablas replicadas se usan mejor con tablas pequeñas. Se requiere almacenamiento adicional y hay sobrecargas adicionales que se producen al escribir datos que hacen que las tablas grandes sean poco prácticas.  

En el diagrama siguiente se muestra una tabla replicada que se almacena en caché en la primera distribución de cada nodo de proceso.  

![Tabla replicada](./media/massively-parallel-processing-mpp-architecture/replicated-table.png "Tabla replicada")

## <a name="next-steps"></a>Pasos siguientes

Ahora que sabe un poco sobre Azure Synapse, aprenda a [crear un grupo de SQL](create-data-warehouse-portal.md) rápidamente y [cargar los datos de ejemplo](load-data-from-azure-blob-storage-using-polybase.md). Si no está familiarizado con Azure, el [Glosario de Azure](../../azure-glossary-cloud-terminology.md?toc=/azure/synapse-analytics/sql-data-warehouse/toc.json&bc=/azure/synapse-analytics/sql-data-warehouse/breadcrumb/toc.json) le puede resultar útil para consultar la nueva terminología que se encuentre. También, puede examinar algunos de estos otros recursos de Azure Synapse.  

- [Casos de éxito de clientes](https://azure.microsoft.com/case-studies/?service=sql-data-warehouse)
- [Blogs](https://azure.microsoft.com/blog/tag/azure-sql-data-warehouse/)
- [Solicitud de función](https://feedback.azure.com/forums/307516-sql-data-warehouse)
- [Vídeos](https://azure.microsoft.com/documentation/videos/index/?services=sql-data-warehouse)
- [Creación de una incidencia de soporte técnico](sql-data-warehouse-get-started-create-support-ticket.md)
- [Página de preguntas y respuestas de Microsoft](https://docs.microsoft.com/answers/topics/azure-synapse-analytics.html)
- [Foro Stack Overflow](https://stackoverflow.com/questions/tagged/azure-sqldw)
- [Twitter](https://twitter.com/hashtag/SQLDW)
