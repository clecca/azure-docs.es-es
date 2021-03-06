---
title: Uso del SDK de voz para evaluar la pronunciación
titleSuffix: Azure Cognitive Services
description: El SDK de voz admite la evaluación de la pronunciación, que evalúa la calidad de la pronunciación de la entrada de voz, con indicadores de precisión, fluidez, integridad, etc.
services: cognitive-services
author: yulin-li
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 09/29/2020
ms.author: yulili
ms.custom: references_regions
zone_pivot_groups: programming-languages-set-nineteen
ms.openlocfilehash: 245a00acb07d1c0e769a243413fccdf64d544f5a
ms.sourcegitcommit: 857859267e0820d0c555f5438dc415fc861d9a6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93135471"
---
# <a name="pronunciation-assessment"></a>Evaluación de la pronunciación

La evaluación de la pronunciación evalúa la pronunciación de la voz y ofrece a los oradores información sobre la precisión y la fluidez del audio hablado.
Con la evaluación de la pronunciación, los estudiantes de idiomas pueden practicar, obtener comentarios instantáneos y mejorar su pronunciación para poder hablar y realizar presentaciones con confianza.
Los educadores pueden utilizar la funcionalidad para evaluar la pronunciación de varios hablantes en tiempo real.

En este artículo, aprenderá a configurar `PronunciationAssessmentConfig` y a recuperar `PronunciationAssessmentResult` mediante el SDK de voz.

> [!NOTE]
> La característica de evaluación de la pronunciación solo está disponible actualmente en las regiones `westus`, `eastasia` y `centralindia`, y solo admite el idioma `en-US`.

## <a name="pronunciation-assessment-with-the-speech-sdk"></a>Evaluación de la pronunciación con el SDK de voz

En los ejemplos siguientes, creará un elemento `PronunciationAssessmentConfig` y le aplicará `SpeechRecognizer`.

En los fragmentos de código siguientes se muestra cómo usar la detección automática de idioma en las aplicaciones:

::: zone pivot="programming-language-csharp"

```csharp
var pronunciationAssessmentConfig = new PronunciationAssessmentConfig(
    "reference text", GradingSystem.HundredMark, Granularity.Phoneme);

using (var recognizer = new SpeechRecognizer(
    speechConfig,
    audioConfig))
{
    // apply the pronunciation assessment configuration to the speech recognizer
    pronunciationAssessmentConfig.ApplyTo(recognizer);
    var speechRecognitionResult = await recognizer.RecognizeOnceAsync();
    var pronunciationAssessmentResult =
        PronunciationAssessmentResult.FromResult(speechRecognitionResult);
    var pronunciationScore = pronunciationAssessmentResult.PronunciationScore;
}
```

::: zone-end

::: zone pivot="programming-language-cpp"

```cpp
auto pronunciationAssessmentConfig =
    PronunciationAssessmentConfig::Create("reference text",
        PronunciationAssessmentGradingSystem::HundredMark,
        PronunciationAssessmentGranularity::Phoneme);

auto recognizer = SpeechRecognizer::FromConfig(
    speechConfig,
    audioConfig);

// apply the pronunciation assessment configuration to the speech recognizer
pronunciationAssessmentConfig->ApplyTo(recognizer);
speechRecognitionResult = recognizer->RecognizeOnceAsync().get();
auto pronunciationAssessmentResult =
    PronunciationAssessmentResult::FromResult(speechRecognitionResult);
auto pronunciationScore = pronunciationAssessmentResult->PronunciationScore;
```

::: zone-end

::: zone pivot="programming-language-java"

```java
PronunciationAssessmentConfig pronunciationAssessmentConfig =
    new PronunciationAssessmentConfig("reference text", 
        PronunciationAssessmentGradingSystem.HundredMark,
        PronunciationAssessmentGranularity.Phoneme);

SpeechRecognizer recognizer = new SpeechRecognizer(
    speechConfig,
    audioConfig);

// apply the pronunciation assessment configuration to the speech recognizer
pronunciationAssessmentConfig.applyTo(recognizer);
Future<SpeechRecognitionResult> future = recognizer.recognizeOnceAsync();
SpeechRecognitionResult result = future.get(30, TimeUnit.SECONDS);
PronunciationAssessmentResult pronunciationAssessmentResult =
    PronunciationAssessmentResult.fromResult(result);
Double pronunciationScore = pronunciationAssessmentResult.getPronunciationScore();

recognizer.close();
speechConfig.close();
audioConfig.close();
pronunciationAssessmentConfig.close();
result.close();
```

::: zone-end

::: zone pivot="programming-language-python"

```Python
pronunciation_assessment_config = \
        speechsdk.PronunciationAssessmentConfig(reference_text='reference text',
                grading_system=msspeech.PronunciationAssessmentGradingSystem.HundredMark,
                granularity=msspeech.PronunciationAssessmentGranularity.Phoneme)
speech_recognizer = speechsdk.SpeechRecognizer(
        speech_config=speech_config, \
        audio_config=audio_config)

# apply the pronunciation assessment configuration to the speech recognizer
pronunciation_assessment_config.apply_to(speech_recognizer)
result = speech_recognizer.recognize_once()
pronunciation_assessment_result = speechsdk.PronunciationAssessmentResult(result)
pronunciation_score = pronunciation_assessment_result.pronunciation_score
```

::: zone-end

::: zone pivot="programming-language-objectivec"

```Objective-C
SPXPronunciationAssessmentConfiguration* pronunciationAssessmentConfig =
    [[SPXPronunciationAssessmentConfiguration alloc]init:@"reference text"
                                           gradingSystem:SPXPronunciationAssessmentGradingSystem_HundredMark
                                             granularity:SPXPronunciationAssessmentGranularity_Phoneme];

SPXSpeechRecognizer* speechRecognizer = \
        [[SPXSpeechRecognizer alloc] initWithSpeechConfiguration:speechConfig
                                              audioConfiguration:audioConfig];

// apply the pronunciation assessment configuration to the speech recognizer
[pronunciationAssessmentConfig applyToRecognizer:speechRecognizer];

SPXSpeechRecognitionResult *result = [speechRecognizer recognizeOnce];
SPXPronunciationAssessmentResult* pronunciationAssessmentResult = [[SPXPronunciationAssessmentResult alloc] init:result];
double pronunciationScore = pronunciationAssessmentResult.pronunciationScore;
```

::: zone-end

### <a name="pronunciation-assessment-configuration-parameters"></a>Parámetros de configuración de evaluación de la pronunciación

En esta tabla se enumeran los parámetros de configuración para la evaluación de la pronunciación.

| Parámetro | Descripción | Obligatorio u opcional |
|-----------|-------------|---------------------|
| ReferenceText | Texto con el que se va a evaluar la pronunciación. | Obligatorio |
| GradingSystem | Sistema de puntos para la calibración de la puntuación. Los valores aceptados son: `FivePoint` y `HundredMark`. El valor predeterminado es `FivePoint`. | Opcional |
| Granularidad | Granularidad de la evaluación. Los valores aceptados son `Phoneme`, que muestra la puntuación en el nivel de todo el texto, la palabra y el fonema, `Word`, que muestra la puntuación en el nivel de todo el texto y la palabra, `FullText`, que muestra la puntuación solo en el nivel de todo el texto. El valor predeterminado es `Phoneme`. | Opcional |
| EnableMiscue | Habilita el cálculo de errores. Con esta opción habilitada, las palabras pronunciadas se comparan con el texto de referencia y se marcan con omisión/inserción en función de la comparación. Los valores aceptados son: `False` y `True`. El valor predeterminado es `False`. | Opcional |
| ScenarioId | GUID que indica un sistema de puntos personalizado. | Opcional |

### <a name="pronunciation-assessment-result-parameters"></a>Parámetros de resultados de evaluación de la pronunciación

En esta tabla se enumeran los parámetros de resultados de evaluación de la pronunciación.

| Parámetro | Description |
|-----------|-------------|
| `AccuracyScore` | Precisión de pronunciación de la voz. La precisión indica el grado de coincidencia de los fonemas con la pronunciación de un hablante nativo. La puntuación de precisión del nivel de texto completo y de las palabras individuales se agrega a partir de la puntuación de precisión del nivel de fonema. |
| `FluencyScore` | Fluidez del fragmento hablado en cuestión. La fluidez indica el grado de coincidencia de la voz con el uso que hace un hablante nativo de los silencios entre palabras. |
| `CompletenessScore` | Integridad de la voz, se determina mediante el cálculo de la proporción de palabras pronunciadas para hacer referencia a la entrada de texto. |
| `PronunciationScore` | Puntuación global que indica la calidad de la pronunciación del fragmento hablado en cuestión. Se agrega a partir de `AccuracyScore`, `FluencyScore` y `CompletenessScore` con ponderación. |
| `ErrorType` | Este valor indica si se ha omitido, se ha insertado o se ha pronunciado incorrectamente una palabra en comparación con `ReferenceText`. Los valores posibles son `None` (que significa que no hay ningún error en esta palabra), `Omission`, `Insertion` y `Mispronunciation`. |

## <a name="next-steps"></a>Pasos siguientes

<!-- TODO: update the sample links after release -->

<!-- ::: zone pivot="programming-language-csharp"
* See the [sample code](https://github.com/Azure-Samples/cognitive-services-speech-sdk/blob/master/samples/csharp/sharedcontent/console/speech_recognition_samples.cs#L741) on GitHub for automatic language detection
::: zone-end

::: zone pivot="programming-language-cpp"
* See the [sample code](https://github.com/Azure-Samples/cognitive-services-speech-sdk/blob/master/samples/cpp/windows/console/samples/speech_recognition_samples.cpp#L507) on GitHub for automatic language detection
::: zone-end

::: zone pivot="programming-language-java"
* See the [sample code](https://github.com/Azure-Samples/cognitive-services-speech-sdk/blob/master/samples/java/jre/console/src/com/microsoft/cognitiveservices/speech/samples/console/SpeechRecognitionSamples.java#L521) on GitHub for automatic language detection
::: zone-end

::: zone pivot="programming-language-python"
* See the [sample code](https://github.com/Azure-Samples/cognitive-services-speech-sdk/blob/master/samples/python/console/speech_synthesis_sample.py#L434) on GitHub for automatic language detection
::: zone-end

::: zone pivot="programming-language-objectivec"
* See the [sample code](https://github.com/Azure-Samples/cognitive-services-speech-sdk/blob/master/samples/objective-c/ios/speech-samples/speech-samples/ViewController.m#L494) on GitHub for automatic language detection
::: zone-end -->

* [Documentación de referencia del SDK de voz](speech-sdk.md)
