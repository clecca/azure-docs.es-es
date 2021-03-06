---
title: 'Inicio rápido: Envío de una solicitud de búsqueda a la API REST mediante C#: Bing Entity Search'
titleSuffix: Azure Cognitive Services
description: Use esta guía de inicio rápido para enviar una solicitud a la API de REST Bing Entity Search mediante C# y reciba una respuesta JSON.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: bing-entity-search
ms.topic: quickstart
ms.date: 10/19/2020
ms.author: aahi
ms.custom: devx-track-csharp
ms.openlocfilehash: 1b0cac94ac3a0c8dff24cf154e4dd7ab7ddf4dd9
ms.sourcegitcommit: 22da82c32accf97a82919bf50b9901668dc55c97
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2020
ms.locfileid: "94368430"
---
# <a name="quickstart-send-a-search-request-to-the-bing-entity-search-rest-api-using-c"></a>Inicio rápido: Envío de una solicitud de búsqueda a Bing Entity Search REST API con C#

> [!WARNING]
> Las Bing Search API se mueven de Cognitive Services a Bing Search Services. A partir del  **30 de octubre de 2020** las nuevas instancias de Bing Search deben aprovisionarse siguiendo el proceso documentado [aquí](https://aka.ms/cogsvcs/bingmove).
> El aprovisionamiento de las Bing Search API mediante Cognitive Services será posible durante los próximos tres años o hasta que finalice el Contrato Enterprise, lo que antes suceda.
> Puede encontrar instrucciones sobre la migración en [Bing Search Services](https://aka.ms/cogsvcs/bingmigration).

Use este inicio rápido para realizar la primera llamada a Bing Entity Search API y ver la respuesta JSON. Esta sencilla aplicación de C# envía una consulta de búsqueda de noticias a la API y muestra la respuesta. El código fuente de esta aplicación está disponible en [GitHub](https://github.com/Azure-Samples/cognitive-services-REST-api-samples/blob/master/dotnet/Search/BingEntitySearchv7.cs).

Aunque esta aplicación está escrita en C#, la API es un servicio web RESTful compatible con la mayoría de los lenguajes de programación.


## <a name="prerequisites"></a>Requisitos previos

- Cualquier edición de [Visual Studio 2017 o versiones posteriores](https://www.visualstudio.com/downloads/).
- O bien, si usa Linux o MacOS, puede seguir este inicio rápido con [Visual Studio Code](https://code.visualstudio.com/) y [.NET Core](/dotnet/core/install/macos).
- [Cuenta gratuita de Azure](https://azure.microsoft.com/free/dotnet).


[!INCLUDE [cognitive-services-bing-news-search-signup-requirements](../../../../includes/cognitive-services-bing-entity-search-signup-requirements.md)]

## <a name="create-and-initialize-a-project"></a>Creación e inicialización de un proyecto

1. Cree una solución de consola de C# en Visual Studio. 
1. Agregue el paquete NuGet [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/).
    1. En el **Explorador de soluciones** , haga clic con el botón derecho en el proyecto.
    2. Seleccione **Administrar paquetes NuGet**.
    3. Busque *Newtonsoft.json* y selecciónelo, a continuación instale el paquete.
1. Después, agregue los siguientes espacios de nombres en el archivo de código principal:
    
    ```csharp
    using Newtonsoft.Json;
    using System;
    using System.Net.Http;
    using System.Text;
    ```

2. Cree una nueva clase y agregue variables para el punto de conexión de la API, la clave de suscripción y la consulta que desea realizar. Puede usar el punto de conexión global en el código siguiente, o el punto de conexión del [subdominio personalizado](../../../cognitive-services/cognitive-services-custom-subdomains.md) que se muestra en Azure Portal para el recurso.

    ```csharp
    namespace EntitySearchSample
    {
        class Program
        {
            static string host = "https://api.cognitive.microsoft.com";
            static string path = "/bing/v7.0/entities";
    
            static string market = "en-US";
    
            // NOTE: Replace this example key with a valid subscription key.
            static string key = "ENTER YOUR KEY HERE";
    
            static string query = "italian restaurant near me";
        //...
        }
    }
    ```

## <a name="send-a-request-and-get-the-api-response"></a>Envío de una solicitud y obtención de la respuesta de la API

1. Dentro de la clase, cree una función denominada `Search()`. Dentro de esta función cree un nuevo objeto `HttpClient` y agregue su clave de suscripción al encabezado `Ocp-Apim-Subscription-Key`.

2. Construya el identificador URI de la solicitud mediante la combinación del host y la ruta de acceso. A continuación, agregue el mercado y codifique como URL la consulta.

3. Espere hasta que `client.GetAsync()` obtenga una respuesta HTTP y, a continuación, almacene la respuesta JSON a la espera de `ReadAsStringAsync()`.

4. Asigne formato a la cadena JSON con `JsonConvert.DeserializeObject()` e imprímala en la consola.

      ```csharp
      async static void Search()
      {
       //...
       HttpClient client = new HttpClient();
       client.DefaultRequestHeaders.Add("Ocp-Apim-Subscription-Key", key);

       string uri = host + path + "?mkt=" + market + "&q=" + System.Net.WebUtility.UrlEncode(query);

       HttpResponseMessage response = await client.GetAsync(uri);

       string contentString = await response.Content.ReadAsStringAsync();
       dynamic parsedJson = JsonConvert.DeserializeObject(contentString);
       Console.WriteLine(parsedJson);
      }
      ```

5. En el método `Main()` de la aplicación, llame a la función `Search()`.
    
    ```csharp
    static void Main(string[] args)
    {
        Search();
        Console.ReadLine();
    }
    ```


## <a name="example-json-response"></a>Ejemplo de respuesta JSON

Se devuelve una respuesta correcta en JSON, como se muestra en el siguiente ejemplo: 

```json
{
  "_type": "SearchResponse",
  "queryContext": {
    "originalQuery": "italian restaurant near me",
    "askUserForLocation": true
  },
  "places": {
    "value": [
      {
        "_type": "LocalBusiness",
        "webSearchUrl": "https://www.bing.com/search?q=sinful+bakery&filters=local...",
        "name": "Liberty's Delightful Sinful Bakery & Cafe",
        "url": "https://www.contoso.com/",
        "entityPresentationInfo": {
          "entityScenario": "ListItem",
          "entityTypeHints": [
            "Place",
            "LocalBusiness"
          ]
        },
        "address": {
          "addressLocality": "Seattle",
          "addressRegion": "WA",
          "postalCode": "98112",
          "addressCountry": "US",
          "neighborhood": "Madison Park"
        },
        "telephone": "(800) 555-1212"
      },

      . . .
      {
        "_type": "Restaurant",
        "webSearchUrl": "https://www.bing.com/search?q=Pickles+and+Preserves...",
        "name": "Munson's Pickles and Preserves Farm",
        "url": "https://www.princi.com/",
        "entityPresentationInfo": {
          "entityScenario": "ListItem",
          "entityTypeHints": [
            "Place",
            "LocalBusiness",
            "Restaurant"
          ]
        },
        "address": {
          "addressLocality": "Seattle",
          "addressRegion": "WA",
          "postalCode": "98101",
          "addressCountry": "US",
          "neighborhood": "Capitol Hill"
        },
        "telephone": "(800) 555-1212"
      },
      
      . . .
    ]
  }
}
```

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Compilar una aplicación web de una sola página](../tutorial-bing-entities-search-single-page-app.md)

* [¿Qué es Bing Entity Search API?](../overview.md )
* [Referencia de la API Bing Entity Search](/rest/api/cognitiveservices-bingsearch/bing-entities-api-v7-reference).