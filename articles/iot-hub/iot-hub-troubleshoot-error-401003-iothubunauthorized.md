---
title: Solución de problemas del error 401003 de Azure IoT Hub IoTHubUnauthorized
description: Corrección del error 401003 IoTHubUnauthorized
author: jlian
manager: briz
ms.service: iot-hub
services: iot-hub
ms.topic: troubleshooting
ms.date: 01/30/2020
ms.author: jlian
ms.custom:
- amqp
- mqtt
ms.openlocfilehash: af057750e81086bf691b87057da97af3de19cd3b
ms.sourcegitcommit: d76108b476259fe3f5f20a91ed2c237c1577df14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2020
ms.locfileid: "92909648"
---
# <a name="401003-iothubunauthorized"></a>401003 IoTHubUnauthorized

En este artículo se describen las causas y las soluciones de los errores **401003 IoTHubUnauthorized**.

## <a name="symptoms"></a>Síntomas

### <a name="symptom-1"></a>Síntoma 1

En los registros, verá un patrón de dispositivos que se están desconectando con el error **401003 IoTHubUnauthorized** , seguido de **404104 DeviceConnectionClosedRemotely** y que se conectan correctamente poco después.

### <a name="symptom-2"></a>Síntoma 2

Las solicitudes a IoT Hub producen un error con uno de los siguientes mensajes de error:

* Authorization header missing (Falta el encabezado de autorización)
* IotHub '\*' does not contain the specified device '\*' ("*" en IotHub no contiene el dispositivo "*" especificado)
* Authorization rule '\*' does not allow access for '\*' (La regla de autorización "*" no permite el acceso a "*")
* Authentication failed for this device, renew token or certificate and reconnect (Error de autenticación para este dispositivo, renueve el token o el certificado y vuelva a realizar la conexión)
* Thumbprint does not match configuration: Thumbprint: SHA1Hash=\*, SHA2Hash=\*; Configuration: PrimaryThumbprint=\*, SecondaryThumbprint=\* (La huella digital no coincide con la configuración: Thumbprint: SHA1Hash=<1>, SHA2Hash=<2>; Configuration: PrimaryThumbprint=<3>, SecondaryThumbprint=<4>)

## <a name="cause"></a>Causa

### <a name="cause-1"></a>Causa 1

Con el protocolo MQTT, algunos SDK se basan en IoT Hub para emitir la desconexión cuando el token de SAS expira para saber cuándo actualizarlo. Por lo tanto, 

1. el token de SAS expira,
1. IoT Hub lo reconoce y desconecta el dispositivo con **401003 IoTHubUnauthorized** ,
1. el dispositivo completa la desconexión con **404104 DeviceConnectionClosedRemotely** ,
1. el SDK de IoT genera un nuevo token de SAS y
1. el dispositivo se vuelve a conectar con IoT Hub correctamente.

### <a name="cause-2"></a>Causa 2

IoT Hub no ha podido autenticar el encabezado de autenticación, la regla o la clave. Esto puede deberse a cualquiera de los motivos citados en los síntomas.

## <a name="solution"></a>Solución

### <a name="solution-1"></a>Solución 1

Si se usa el SDK de IoT para la conexión mediante la cadena de conexión del dispositivo, no es necesario realizar ninguna acción. El SDK de IoT regenera el token nuevo para volver a realizar la conexión tras la expiración del token de SAS. 

Si el volumen de errores es un problema, cambie al SDK de C, que renueva el token de SAS antes de la expiración. Además, con el protocolo AMQP, el token de SAS puede actualizarse sin desconexión.

### <a name="solution-2"></a>Solución 2

En general, el mensaje de error presentado debe explicar cómo corregir el error. Si por alguna razón no tiene acceso a los detalles del mensaje de error, asegúrese de lo siguiente:

- Que la firma de acceso compartido u otro token de seguridad que use no haya expirado.
- En cuanto a la autenticación de certificados X.509, el certificado de dispositivo o el certificado de CA asociado al dispositivo no han expirado. Para obtener información sobre cómo registrar certificados de CA de X.509 con IoT Hub, consulte [Configuración de la seguridad de X.509 en Azure IoT Hub](iot-hub-security-x509-get-started.md).
- Para realizar la autenticación de la huella digital del certificado X.509, la huella digital del certificado del dispositivo se registra con IoT Hub.
- Que la credencial de autorización tiene el formato correcto para el protocolo utilizado. Para obtener más información, consulte [Control del acceso a IoT Hub](iot-hub-devguide-security.md).
- La regla de autorización empleada tiene permiso para la operación solicitada.

## <a name="next-steps"></a>Pasos siguientes

- Para facilitar la autenticación en IoT Hub, se recomiendan los [SDK de IoT de Azure](iot-hub-devguide-sdks.md).
- Para obtener más detalles sobre la autenticación con IoT Hub, consulte [Control del acceso a IoT Hub](iot-hub-devguide-security.md).
