---
title: 'Personalización de la traducción: Traductor'
titleSuffix: Azure Cognitive Services
description: Use Microsoft Translator Hub para crear su propio sistema de traducción automática con su terminología y estilo preferidos.
services: cognitive-services
author: swmachan
manager: nitinme
ms.service: cognitive-services
ms.subservice: translator-text
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: swmachan
ms.openlocfilehash: 95cb4aa5827190abf125669f2423c808cf8c92a5
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2020
ms.locfileid: "94368940"
---
# <a name="customize-your-text-translations"></a>Personalización de las traducciones de texto

Traductor personalizado es una característica del servicio Traductor que permite a los usuarios personalizar la traducción automática neuronal avanzada de Microsoft Translator cuando se traduce texto con Traductor (solo la versión 3).

Esta característica solamente puede utilizarse para personalizar la traducción de voz cuando se usa con el [servicio Voz de Cognitive Services](../speech-service/index.yml).

## <a name="custom-translator"></a>Custom Translator

Con Custom Translator puede crear sistemas de traducción neuronal que comprendan la terminología usada en su propia empresa y sector. El sistema de traducción personalizada se integrará en las aplicaciones, los flujos de trabajo y los sitios web existentes.

### <a name="how-does-it-work"></a>¿Cómo funciona?

Utilice los documentos traducidos anteriormente (prospectos, páginas web, documentación, etc.) para crear un sistema de traducción que refleje la terminología y el estilo específicos de su dominio, mejor que un sistema de traducción estándar. Los usuarios pueden cargar documentos TMX, XLIFF, TXT, DOCX y XLSX.  

El sistema también acepta datos que sean paralelos a nivel de documento, pero que aún no estén alineados a nivel de frase. Si los usuarios tienen acceso a versiones del mismo contenido en varios idiomas, pero en documentos independientes Custom Translator podrá hace concordar automáticamente las frases de los distintos documentos.  El sistema también puede utilizar datos monolingües en uno de los idiomas, o en ambos, para complementar los datos de aprendizaje paralelos, con el fin de mejorar las traducciones.

A partir de ese momento, el sistema personalizado está disponible con una llamada normal a Traductor con el parámetro de categoría.

Si se proporcionan el tipo y la cantidad apropiados de datos de aprendizaje, no es extraño que con Custom Translator la calidad de la traducción mejore entre 5 y 10 puntos BLEU, o incluso más.

Puede encontrar más detalles acerca de los diferentes niveles de personalización en función de los datos disponibles en el [Manual del usuario de Custom Translator](./custom-translator/overview.md).


## <a name="microsoft-translator-hub"></a>Microsoft Translator Hub

> [!NOTE]
> Microsoft Translator Hub (heredado) se retirará el 17 de mayo de 2019. [Ver información importante y fechas de migración](https://www.microsoft.com/translator/business/hub/).  

## <a name="custom-translator-versus-hub"></a>Custom Translator frente a Hub

| Característica | Hub | Custom Translator |
| ------- | :-: | :---------------: |
|Estado de la característica de personalización    | Disponibilidad general    | Disponibilidad general |
| Versión de Text API    | Solo v2    | Solo v3 |
| Personalización de SMT    | Sí    | No |
| Personalización de NMT    | No    | Sí |
| Nueva personalización unificada de servicios de voz    | No    | Sí |
| [Sin seguimiento](https://www.aka.ms/notrace) | Sí    | Sí |

## <a name="collaborative-translations-framework"></a>Marco de traducciones en colaboración

> [!NOTE]
> A partir del 1 de febrero de 2018, AddTranslation() y AddTranslationArray() no se pueden usar con la versión 2.0 de Traductor. Estos métodos generarán un error y no se escribirá nada. La versión 3.0 de Traductor no admite estos métodos.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Configuración de un sistema de idiomas personalizado mediante Custom Translator](./custom-translator/overview.md)