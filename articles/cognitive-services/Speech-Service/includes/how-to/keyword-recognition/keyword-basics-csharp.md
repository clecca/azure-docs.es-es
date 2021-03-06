---
author: trevorbye
ms.service: cognitive-services
ms.topic: include
ms.date: 11/03/2020
ms.author: trbye
ms.openlocfilehash: 040ffea69f76255dcb1bfc6787cad45a95baa904
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93305889"
---
En primer lugar, cargue el archivo del modelo de palabra clave mediante la función estática `FromFile()`, que devuelve un `KeywordRecognitionModel`. Use la ruta de acceso al archivo `.table` que descargó de Speech Studio. Además, debe crear una configuración `AudioConfig` con el micrófono predeterminado y, a continuación, cree una instancia nueva de `KeywordRecognizer` mediante la configuración de audio.

```csharp
using Microsoft.CognitiveServices.Speech;
using Microsoft.CognitiveServices.Speech.Audio;

var keywordModel = KeywordRecognitionModel.FromFile("your/path/to/Activate_device.table");
using var audioConfig = AudioConfig.FromDefaultMicrophoneInput();
using var keywordRecognizer = new KeywordRecognizer(audioConfig);
```

A continuación, se ejecuta el reconocimiento de palabras clave mediante una llamada a `RecognizeOnceAsync()` en la que se pasa el objeto de modelo. De este modo, se inicia una sesión de reconocimiento de palabras clave que continúa hasta que se reconoce la palabra clave. Por lo tanto, normalmente se usa este modelo de diseño en aplicaciones multiproceso o en casos de uso en los que puede esperar una palabra de activación indefinidamente.

```csharp
KeywordRecognitionResult result = await keywordRecognizer.RecognizeOnceAsync(keywordModel);
```

> [!NOTE]
> El ejemplo que se muestra aquí usa el reconocimiento de palabras clave local, ya que no requiere un objeto `SpeechConfig` para el contexto de autenticación y no se comunica con el servidor back-end. Sin embargo, puede ejecutar el reconocimiento de palabras clave y la comprobación [mediante una conexión continua con el servidor back-end](https://docs.microsoft.com/azure/cognitive-services/speech-service/tutorial-voice-enable-your-bot-speech-sdk#view-the-source-code-that-enables-keyword).