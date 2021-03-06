---
title: 'Idiomas admitidos: Bing Custom Search API'
titleSuffix: Azure Cognitive Services
description: Una lista de los idiomas y las regiones admitidos para Bing Custom Search API.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-custom-search
ms.topic: conceptual
ms.date: 09/25/2018
ms.author: aahi
ms.openlocfilehash: 2579d24e1a1754e873c6591b6d86ec12dd0dfa60
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2020
ms.locfileid: "94367325"
---
# <a name="language-and-region-support-for-the-bing-custom-search-api"></a>Compatibilidad de idiomas y regiones para Bing Custom Search API

> [!WARNING]
> Bing Search APIs se mueve de Cognitive Services a Bing Search Services. A partir del **30 de octubre de 2020** , las nuevas instancias de Bing Search deben aprovisionarse siguiendo el proceso documentado [aquí](https://aka.ms/cogsvcs/bingmove).
> El aprovisionamiento de Bing Search APIs con Cognitive Services será posible durante los próximos tres años o hasta que finalice el Contrato Enterprise, lo que suceda primero.
> Puede encontrar instrucciones sobre la migración en [Bing Search Services](https://aka.ms/cogsvcs/bingmigration).

Bing Custom Search API admite más de 36 países o regiones, muchos de ellos con más de un idioma.

Aunque es opcional, la solicitud debe especificar el parámetro de consulta [mkt](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#mkt), que identifica el mercado de donde desea que procedan los resultados. Para ver una lista de parámetros de consulta opcionales, consulte [Query Parameters](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#query-parameters) (Parámetros de consulta).

Puede especificar un país o región utilizando el parámetro de consulta `cc`. Si especifica un país o región, también debe especificar uno o más códigos de idioma con el encabezado `Accept-Language`. Los idiomas admitidos varían según el país o región; se facilitan para cada país en la tabla **Mercados**.

El encabezado `Accept-Language` y el parámetro de consulta `setLang` son mutuamente excluyentes, no especifique ambos. Para obtener más información, consulte [Accept-Language](/rest/api/cognitiveservices-bingsearch/bing-custom-search-api-v7-reference#acceptlanguage).

## <a name="countriesregions"></a>Países o regiones

|País/región|Código|
|-------|----|
|Argentina|AR|
|Australia|AU|
|Austria|AT|
|Bélgica|BE|
|Brasil|BR|
|Canadá|CA|
|Chile|CL|
|Dinamarca|DK|
|Finlandia|FI|
|Francia|VF|
|Alemania|DE|
|RAE de Hong Kong|HK|
|India|IN|
|Indonesia|ID|
|Italia|IT|
|Japón|JP|
|Corea|KR|
|Malasia|MY|
|México|MX|
|Países Bajos|NL|
|Nueva Zelanda|NZ|
|Noruega|No|
|China|CN|
|Polonia|PL|
|Portugal|PT|
|Filipinas|PH|
|Rusia|RU|
|Arabia Saudí|SA|
|Sudáfrica|ZA|
|España|ES|
|Suecia|SE|
|Suiza|CH|
|Taiwán|TW|
|Turquía|TR|
|Reino Unido|GB|
|Estados Unidos|US|


## <a name="markets"></a>Mercados

|País/región|Idioma|Código de mercado|
|-------|--------|-----------|
|Argentina|Español|es-AR|
|Australia|Inglés|en-AU|
|Austria|Alemán|de-AT|
|Bélgica|Neerlandés|nl-BE|
|Bélgica|Francés|fr-BE|
|Brasil|Portugués|pt-BR|
|Canadá|Inglés|en-CA|
|Canadá|Francés|fr-CA|
|Chile|Español|es-CL|
|Dinamarca|Danés|da-DK|
|Finlandia|Finés|fi-FI|
|Francia|Francés|fr-FR|
|Alemania|Alemán|de-DE|
|RAE de Hong Kong|Chino tradicional|zh-HK|
|India|Inglés|en-IN|
|Indonesia|Inglés|en-ID|
|Italia|Italiano|it-IT|
|Japón|Japonés|ja-JP|
|Corea|Coreano|ko-KR|
|Malasia|Inglés|en-MY|
|México|Español|es-MX|
|Países Bajos|Neerlandés|nl-NL|
|Nueva Zelanda|Inglés|en-NZ|
|Noruega|Noruego|no-NO|
|China|Chino|zh-CN|
|Polonia|Polaco|pl-PL|
|Portugal|Portugués|pt-PT|
|Filipinas|Inglés|en-PH|
|Rusia|Ruso|ru-RU|
|Arabia Saudí|Árabe|ar-SA|
|Sudáfrica|Inglés|en-ZA|
|España|Español|es-ES|
|Suecia|Sueco|sv-SE|
|Suiza|Francés|fr-CH|
|Suiza|Alemán|de-CH|
|Taiwán|Chino tradicional|zh-TW|
|Turquía|Turco|tr-TR|
|Reino Unido|Inglés|en-GB|
|Estados Unidos|Inglés|es-ES|
|Estados Unidos|Español|es-US|