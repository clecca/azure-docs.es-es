---
author: ggailey777
ms.service: azure-functions
ms.topic: include
ms.date: 03/25/2020
ms.author: glenga
ms.openlocfilehash: 7ddceb2808874e531cfda81e5a9ce74be3a4fab4
ms.sourcegitcommit: 59f506857abb1ed3328fda34d37800b55159c91d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2020
ms.locfileid: "92517093"
---
## <a name="configure-your-local-environment"></a>Configuración del entorno local

Antes de empezar, debe disponer de lo siguiente:

+ Una cuenta de Azure con una suscripción activa. [Cree una cuenta gratuita](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio).

::: zone pivot="programming-language-csharp,programming-language-javascript,programming-language-typescript,programming-language-powershell,programming-language-java"  
+ [Azure Functions Core Tools](../articles/azure-functions/functions-run-local.md#v2), versión 2.7.1846, o cualquier versión 2.x posterior.
::: zone-end  
::: zone pivot="programming-language-python"
+ La versión de Azure Functions Core Tools correspondiente a la versión instalada de Python:

   | Versión de Python | Versión de Core Tools |
   | -------------- | ------------------ |
   | Python 3.8     | [versión 3.x](../articles/azure-functions/functions-run-local.md#v2) |
   | Python 3.6<br/>Python 3.7 | [Versión 2.7.1846 o posterior](../articles/azure-functions/functions-run-local.md#v2) |
  
::: zone-end

+ La [CLI de Azure](/cli/azure/install-azure-cli), versión 2.4 o cualquier versión posterior. 
::: zone pivot="programming-language-javascript,programming-language-typescript"
+ Versiones de [Node.js](https://nodejs.org/), Active LTS y Maintenance LTS (se recomiendan 8.11.1 y 10.14.1).
::: zone-end

::: zone pivot="programming-language-python"
+ [Python 3.8 (64 bits)](https://www.python.org/downloads/release/python-382/), [Python 3.7 (64 bits)](https://www.python.org/downloads/release/python-375/), [Python 3.6 (64 bits)](https://www.python.org/downloads/release/python-368/), que son compatibles con Azure Functions. 
::: zone-end
::: zone pivot="programming-language-powershell"
+ [.NET Core SDK 3.1](https://www.microsoft.com/net/download)
::: zone-end
::: zone pivot="programming-language-java"  
+ [Kit para desarrolladores de Java](https://aka.ms/azure-jdks), versión 8 u 11. 

+ [Apache Maven](https://maven.apache.org), versión 3.0 o posterior.

::: zone-end
