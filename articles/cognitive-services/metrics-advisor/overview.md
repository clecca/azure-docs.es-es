---
title: ¿Qué es el servicio Metrics Advisor?
titleSuffix: Azure Cognitive Services
description: ¿Qué es Metrics Advisor?
services: cognitive-services
author: mrbullwinkle
manager: nitinme
ms.service: cognitive-services
ms.subservice: metrics-advisor
ms.topic: overview
ms.date: 09/14/2020
ms.author: mbullwin
ms.openlocfilehash: 1a57660733b7257b224c38a55059f1bf069495a0
ms.sourcegitcommit: 4064234b1b4be79c411ef677569f29ae73e78731
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92890262"
---
# <a name="what-is-metrics-advisor-preview"></a>¿Qué es Metrics Advisor (versión preliminar)? 

Metrics Advisor forma parte de Azure Cognitive Services que usa inteligencia artificial para realizar la supervisión de datos y la detección de anomalías en los datos de series temporales. El servicio automatiza el proceso de aplicación de modelos a los datos y proporciona un conjunto de áreas de trabajo basadas en Web de API para la ingesta de datos, la detección de anomalías y los diagnósticos, sin necesidad de conocer el aprendizaje automático. Use Metrics Advisor para:

* Analizar los datos multidimensionales de varios orígenes de datos 
* Identificar y correlacionar las anomalías
* Configurar y ajustar el modelo de detección de anomalías usado en los datos
* Diagnosticar las anomalías y ayudar con el análisis de la causa principal. 

:::image type="content" source="media/metrics-advisor-overview.png" alt-text="Introducción a Metrics Advisor":::

## <a name="connect-to-a-variety-of-data-sources"></a>Conexión a diferentes orígenes de datos

Metrics Advisor puede conectarse e [ingerir datos de métricas multidimensionales](how-tos/onboard-your-data.md) de muchos almacenes de datos, entre los que se incluyen lo siguientes: SQL Server, Azure Blob Storage, MongoDB y otros. 

## <a name="easy-to-use-and-customizable-anomaly-detection"></a>Detección de anomalías fácil de usar y personalizable

* Metrics Advisor selecciona automáticamente el mejor modelo para los datos, sin necesidad de realizar ningún aprendizaje automático. 
* Supervise automáticamente cada serie temporal dentro de las [métricas multidimensionales](glossary.md#multi-dimensional-metric).
* Use la [optimización de parámetros](how-tos/configure-metrics.md) y los [comentarios interactivos](how-tos/anomaly-feedback.md) para personalizar el modelo que se aplica a los datos y los futuros resultados de la detección de anomalías.


## <a name="real-time-alerts-through-multiple-channels"></a>Alertas en tiempo real en varios canales

Cada vez que se detecten anomalías, Metrics Advisor puede [enviar alertas en tiempo real](how-tos/alerts.md) mediante varios canales con enlaces, como son los de correo electrónico, los canales Web y los de Azure DevOps. Las reglas de alerta flexibles permiten personalizar las alertas que se envían y a dónde.

## <a name="smart-diagnostic-insights-by-analyzing-anomalies"></a>Información de diagnóstico inteligente mediante el análisis de anomalías

Analice las anomalías detectadas en las métricas multidimensionales y genere [información de diagnóstico inteligente](how-tos/diagnose-incident.md) como las causas más probables, los árboles de diagnóstico, la exploración de métricas, etc. Al configurar el [grafo de métricas](how-tos/metrics-graph.md), puede habilitarse el análisis de las métricas cruzadas para ayudarle a visualizar los incidentes.


## <a name="typical-workflow"></a>Flujo de trabajo típico

El flujo de trabajo es sencillo: después de incorporar los datos, puede ajustar la detección de anomalías y crear configuraciones para que se adapten a su escenario.

1. [Cree un recurso de Azure](../cognitive-services-apis-create-account.md) para Metrics Advisor. 
2. Cree su primer monitor con el portal web.
    1. Incorporación de los datos
    2. Ajuste de la detección de anomalías
    3. Suscripción a alertas
    4. Visualización de la Información de diagnóstico
3. Use la API de REST para personalizar la instancia.

## <a name="next-steps"></a>Pasos siguientes

* Explore una guía de inicio rápido: [Supervisión de la primera métrica en la web](quickstarts/web-portal.md).
* Explore una guía de inicio rápido: [Uso de las API de REST para personalizar su solución](quickstarts/rest-api.md).
