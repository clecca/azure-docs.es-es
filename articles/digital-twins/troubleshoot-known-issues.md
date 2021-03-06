---
title: 'Problemas conocidos: Azure Digital Twins'
description: Obtenga ayuda para reconocer y mitigar los problemas conocidos de Azure Digital Twins.
author: baanders
ms.author: baanders
ms.topic: troubleshooting
ms.service: digital-twins
ms.date: 07/14/2020
ms.openlocfilehash: 549e1808a3b449f7d29b968cde76ef29391880b3
ms.sourcegitcommit: 3bdeb546890a740384a8ef383cf915e84bd7e91e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93100623"
---
# <a name="known-issues-in-azure-digital-twins"></a>Problemas conocidos en Azure Digital Twins

En este artículo se proporciona información sobre los problemas conocidos asociados a Azure Digital Twins.

## <a name="400-client-error-bad-request-in-cloud-shell"></a>"400 Error de cliente: Solicitud incorrecta" en Cloud Shell

Los comandos de Cloud Shell que se ejecutan en *https://shell.azure.com* pueden producir de forma intermitente el error "400 Error de cliente: Solicitud incorrecta de dirección URL: http://localhost:50342/oauth2/token", con seguimiento de la pila completa.

En el caso de Azure Digital Twins, concretamente, esto afecta a los siguientes grupos de comandos:
* `az dt route`
* `az dt model`
* `az dt twin`

### <a name="troubleshooting-steps"></a>Pasos para solucionar problemas

Esto puede resolverse si se vuelve a ejecutar el comando `az login` en Cloud Shell y se completan los pasos de inicio de sesión posteriores. Después de esto, debería poder ejecutar el comando nuevamente.

Como alternativa, puede abrir el panel de Cloud Shell en Azure Portal y completar desde aquí su trabajo de Cloud Shell:

:::image type="content" source="media/includes/portal-cloud-shell.png" alt-text="Vista del Azure Portal con el icono de &quot;Cloud Shell&quot; resaltado; y Cloud Shell aparece indicado en la parte inferior de la ventana del portal." lightbox="media/includes/portal-cloud-shell.png":::

Otra alternativa consiste en [instalar la CLI de Azure](/cli/azure/install-azure-cli?view=azure-cli-latest&preserve-view=true) en su máquina para poder ejecutar localmente comandos de la CLI de Azure. La CLI local no experimenta este problema.

### <a name="possible-causes"></a>Causas posibles

Este es el resultado de un problema conocido en Cloud Shell: [*Error intermitente al obtener el token de Cloud Shell con 400 Error de cliente: Solicitud incorrecta*](https://github.com/Azure/azure-cli/issues/11749).

Esto presenta un problema con los tokens de autenticación de la instancia de Azure Digital Twins y la autenticación basada en la [identidad administrada](../active-directory/managed-identities-azure-resources/overview.md) predeterminada del Cloud Shell. El paso de solución de problemas de ejecución de `az login` le deja fuera de la autenticación de identidad administrada, poniendo fin a este problema.

Esto no afecta a los comandos de Azure Digital Twins de los grupos de comandos `az dt` o `az dt endpoint`, ya que usan un tipo diferente de token de autenticación (basado en ARM), que no tiene ningún problema con la autenticación de identidad administrada de Cloud Shell.

## <a name="missing-role-assignment-after-scripted-setup"></a>Asignación de roles que faltan después de la instalación con script

Algunos usuarios pueden experimentar problemas con la parte de asignación de roles que se describe en el tutorial [*Procedimiento: Configuración de una instancia y autenticación (con scripts)*](how-to-set-up-instance-scripted.md). El script no indica un error, pero el rol *Propietario de datos de Azure Digital Twins* no se ha asignado correctamente al usuario, lo que afectará a la posibilidad de crear otros recursos más adelante.

[!INCLUDE [digital-twins-role-rename-note.md](../../includes/digital-twins-role-rename-note.md)]

Para determinar si la asignación de roles se configuró correctamente después de ejecutar el script, siga las instrucciones de la sección [*Comprobación de la asignación de roles de usuario*](how-to-set-up-instance-scripted.md#verify-user-role-assignment) del artículo de configuración. Si el usuario no se muestra con este rol, este problema le afecta.

### <a name="troubleshooting-steps"></a>Pasos para solucionar problemas

Para resolverlo, puede configurar la asignación de roles manualmente mediante la CLI o Azure Portal. 

Siga estas instrucciones:
* [CLI](how-to-set-up-instance-cli.md#set-up-user-access-permissions)
* [portal](how-to-set-up-instance-portal.md#set-up-user-access-permissions)

### <a name="possible-causes"></a>Causas posibles

En el caso de los usuarios que iniciaron sesión con una [cuenta Microsoft (MSA)](https://account.microsoft.com/account) personal, el identificador de entidad de seguridad del usuario que lo identifica en comandos de este tipo puede ser diferente del correo electrónico de inicio de sesión del usuario, lo que dificulta la detección y el uso de la asignación del rol correctamente por el script.

## <a name="issue-with-interactive-browser-authentication"></a>Problema con la autenticación interactiva del explorador

Al escribir código de autenticación en las aplicaciones de Azure Digital Twins con la versión **1.2.0** de la biblioteca **[Azure.Identity](/dotnet/api/azure.identity?view=azure-dotnet&preserve-view=true)** , puede experimentar problemas con el método [InteractiveBrowserCredential](/dotnet/api/azure.identity.interactivebrowsercredential?view=azure-dotnet&preserve-view=true).

Esta no es la versión más reciente de la biblioteca. La versión más reciente es **1.2.2**.

El método afectado se usa en los artículos siguientes: 
* [*Tutorial: Programación de una aplicación cliente*](tutorial-code.md)
* [*Procedimiento: Escritura de código de autenticación de aplicación*](how-to-authenticate-client.md)
* [*Procedimiento: Uso de las API y los SDK de Azure Digital Twins*](how-to-use-apis-sdks.md)

El problema incluye una respuesta de error de "Azure.Identity.AuthenticationFailedException" al intentar autenticarse en la ventana del explorador. Es posible que la ventana del explorador no se inicie por completo o que parezca que la autenticación del usuario se realiza correctamente, mientras que la aplicación cliente sigue generando el error.

### <a name="troubleshooting-steps"></a>Pasos para solucionar problemas

Para resolver el problema, actualice las aplicaciones de modo que usen la versión de `Azure.Identity` **1.2.2**. Con esta versión de la biblioteca, el explorador se cargará y autenticará según lo previsto.

### <a name="possible-causes"></a>Causas posibles

Está relacionado con un problema abierto de la versión más reciente de la biblioteca `Azure.Identity` (versión **1.2.0** ): [*No se puede autenticar cuando se usa InteractiveBrowserCredential*](https://github.com/Azure/azure-sdk-for-net/issues/13940).

Este problema se observa cuando se usa la versión **1.2.0** de la aplicación de Azure Digital Twins o si se agrega la biblioteca al proyecto sin especificar una versión (ya que, en este caso, también se toma como predeterminada esta versión más reciente).

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre la seguridad y los permisos de Azure Digital Twins:
* [*Conceptos: Seguridad para las soluciones de Azure Digital Twins*](concepts-security.md)