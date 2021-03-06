---
title: Reglas para asignar nombres a entidades de Azure Data Factory
description: Describe las reglas de nomenclatura para las entidades de Factoría de datos.
services: data-factory
documentationcenter: ''
author: djpmsft
ms.author: daperlov
manager: jroth
ms.reviewer: maghan
ms.service: data-factory
ms.workload: data-services
ms.topic: conceptual
ms.date: 10/15/2020
ms.openlocfilehash: 85e1e7fbea6033fde7c5f46b2ef566672bbe1fea
ms.sourcegitcommit: ae6e7057a00d95ed7b828fc8846e3a6281859d40
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92105879"
---
# <a name="azure-data-factory---naming-rules"></a>Azure Data Factory: reglas de nomenclatura

[!INCLUDE[appliesto-adf-xxx-md](includes/appliesto-adf-xxx-md.md)]

La tabla siguiente proporciona las reglas de nomenclatura para los artefactos de Factoría de datos.

| Nombre | Exclusividad del nombre | Comprobaciones de validación |
|:--- |:--- |:--- |
| Factoría de datos | Único en Microsoft Azure. Los nombres no distinguen mayúsculas de minúsculas, es decir, `MyDF` y `mydf` hacen referencia a la misma factoría de datos. |<ul><li>Cada factoría de datos está asociada exactamente a una suscripción de Azure.</li><li>Los nombres de objeto deben comenzar por una letra o un número, y pueden contener solo letras, números y el carácter de guión (-).</li><li>Los caracteres de guión (-) debe estar inmediatamente precedidos y seguidos por una letra o un número. No se permiten guiones consecutivos en los nombres de contenedor.</li><li>El nombre puede tener entre 3 y 63 caracteres.</li></ul> |
| Servicios vinculados, conjuntos de datos, canalizaciones o flujos de datos | Único en una factoría de datos. Los nombres no distinguen mayúsculas de minúsculas. |<ul><li>Los nombres de objeto deben comenzar con una letra.</li><li>No se permiten los caracteres siguientes: “.”, “+”, “?”, “/”, “<”, ”>”, ”*”, ”%”, ”&”, ”:” y ”\\”.</li><li>No se permiten guiones ("-") en los nombres de los servicios, los flujos de datos ni los conjuntos de datos vinculados.</li></ul>  |
| Integration Runtime |Único en una factoría de datos. Los nombres no distinguen mayúsculas de minúsculas. |<ul><li>El nombre de Integration Runtime solo puede contener letras, números y el carácter de guion (-).</li><li>El primer y el último caracteres deben ser una letra o un número. Los caracteres de guión (-) debe estar inmediatamente precedidos y seguidos por una letra o un número.</li><li>No se permiten guiones consecutivos en el nombre del entorno de ejecución de integración. </li></ul> |
| Transformaciones de flujos de datos | Es único en un flujo de datos. Los nombres no distinguen mayúsculas de minúsculas. | <ul><li>Los nombres de transformación de flujo de datos solo pueden contener letras y números.</li><li>El primer carácter debe ser una letra. </li></ul> |
| Grupo de recursos |Único en Microsoft Azure. Los nombres no distinguen mayúsculas de minúsculas. | Para más información, consulte [Reglas y restricciones de nomenclatura de Azure](/azure/cloud-adoption-framework/ready/azure-best-practices/naming-and-tagging#resource-naming). |

## <a name="next-steps"></a>Pasos siguientes
Aprenda a crear factorías de datos siguiendo las instrucciones paso a paso del artículo [Inicio rápido: Creación de una factoría de datos](quickstart-create-data-factory-powershell.md). 
