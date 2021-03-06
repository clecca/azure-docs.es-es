---
title: 'Preguntas y respuestas sobre la aplicación Microsoft Authenticator: Azure AD'
description: Preguntas y respuestas frecuentes (P+F) relacionadas con la aplicación Microsoft Authentication y la comprobación en dos pasos.
services: active-directory
author: curtand
manager: daveba
ms.assetid: f04d5bce-e99e-4f75-82d1-ef6369be3402
ms.service: active-directory
ms.workload: identity
ms.subservice: user-help
ms.topic: end-user-help
ms.date: 10/20/2020
ms.author: curtand
ms.reviewer: olhaun
ms.openlocfilehash: 017898249f1ad32a37b7ccd6bce17fe3d32843f3
ms.sourcegitcommit: 3bcce2e26935f523226ea269f034e0d75aa6693a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2020
ms.locfileid: "92480316"
---
# <a name="frequently-asked-questions-faq-about-the-microsoft-authenticator-app"></a>Preguntas frecuentes (P+F) sobre la aplicación Microsoft Authenticator

En este artículo se proporcionan respuestas a preguntas habituales sobre la aplicación Microsoft Authenticator. Si no ve una respuesta a su pregunta, vaya al [foro de la aplicación Microsoft Authenticator](https://social.technet.microsoft.com/Forums/en-US/home?forum=MicrosoftAuthenticatorApp).

La aplicación Microsoft Authenticator reemplaza a la aplicación Azure Authenticator y es la aplicación recomendada cuando se utiliza Azure Multi-Factor Authentication. La aplicación Microsoft Authenticator está disponible para [Android](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator) e [iOS](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

### <a name="registering-a-device"></a>Registro de un dispositivo

**P.** : ¿Está registrando un dispositivo y acepta la concesión de acceso a dicho dispositivo para la empresa o el servicio?

**R.** : El registro de un dispositivo permite que el dispositivo acceda a los servicios de la organización, pero no que la organización acceda al dispositivo.

### <a name="legacy-apns-support-deprecated"></a>Compatibilidad con APNs heredado en desuso

**P.** : Dado que la interfaz binaria heredada para el servicio Apple Push Notification está en desuso a partir de noviembre de 2020, ¿cómo puedo seguir usando Microsoft Authenticator/Phone Factor para iniciar sesión?

**R.** : [Apple anunció la caída en desuso](https://developer.apple.com/news/?id=11042019a) de las notificaciones push que usan su interfaz binaria para dispositivos iOS, como las usadas por Phone Factor. Para seguir recibiendo notificaciones push, se recomienda que los usuarios actualicen su aplicación Authenticator a la versión más reciente. Mientras tanto, puede solucionarlo si comprueba manualmente las notificaciones en la aplicación Authenticator.

### <a name="app-lock-feature"></a>Característica Bloqueo de aplicación

**P.** : ¿Qué es Bloqueo de aplicación y cómo se puede usar para ayudar a mantenerme más seguro?

**R.** : Bloqueo de aplicación ayuda a mantener sus códigos de verificación de un solo uso, la información de aplicación y la configuración de la aplicación más seguros. Cuando la característica Bloqueo de aplicación está habilitada, se le pedirá que se autentique con el PIN del dispositivo o características biométricas cada vez que abra la aplicación Authenticator. Bloqueo de aplicación también ayuda a asegurarse de que es la única persona que puede aprobar notificaciones solicitando el PIN o características biométricas cada vez que aprueba una notificación de inicio de sesión. Puede activar o desactivar la característica Bloqueo de aplicación en la página de configuración de Authenticator. De forma predeterminada, la característica Bloqueo de aplicación se activa al configurar un PIN o características biométricas en el dispositivo.<br><br>Desafortunadamente, no hay ninguna garantía de que Bloqueo de aplicación vaya a impedir que alguien acceda a Authenticator. Esto se debe a que el registro del dispositivo puede realizarse en ubicaciones distintas de Authenticator, como en la configuración de la cuenta de Android o en la aplicación Portal de empresa.

### <a name="windows-mobile-retired"></a>Retiro de Windows Mobile

**P.** : Tengo un dispositivo Windows Mobile y Microsoft Authenticator está en desuso en Windows Mobile. ¿Puedo continuar autenticándome con la aplicación?

**R.** : Todas las autenticaciones que usen el Microsoft Authenticator en Windows Mobile se retirarán después del 15 de julio de 2020. Se recomienda encarecidamente que use un método de autenticación alternativo para evitar que no pueda entrar en sus cuentas.<br>Entre las opciones alternativas para los usuarios de empresa se incluyen:<br><ul><li>Configuración de Microsoft Authenticator para [Android](https://play.google.com/store/apps/details?id=com.azure.authenticator) o [iOS](https://apps.apple.com/app/microsoft-authenticator/id983156458).</li><li>[Configuración de SMS](multi-factor-authentication-setup-phone-number.md) para recibir códigos de verificación.</li><li>Configuración del número de teléfono para recibir [llamadas telefónicas para comprobar su identidad](multi-factor-authentication-setup-office-phone.md).</li></ul><br>Entre las opciones alternativas para los usuarios de la cuenta personal de Microsoft se incluyen:<br><ul><li>Configuración de Microsoft Authenticator para [Android](https://play.google.com/store/apps/details?id=com.azure.authenticator) o [iOS](https://apps.apple.com/app/microsoft-authenticator/id983156458).</li><li>Configuración de un método de inicio de sesión alternativo (SMS o correo electrónico) actualizando la información de seguridad de la [página de seguridad de la cuenta de Microsoft](https://account.microsoft.com/security/).</li></ul>

### <a name="android-screenshots"></a>Capturas de pantalla de Android

**P.** : ¿Puedo tomar capturas de pantalla de mis códigos de contraseña de un solo uso (OTP) en Android Authenticator?

**R.** : A partir de la versión 6.2003.1704 de Android Authenticator, todos los códigos OTP se ocultan de forma predeterminada siempre que se realiza una captura de pantalla de Authenticator. Si desea ver los códigos OTP en capturas de pantalla o permitir que otras aplicaciones capturen la pantalla de Authenticator, puede hacerlo. Solo tiene que activar la configuración **Captura de pantalla** en Authenticator y reiniciar la aplicación.

### <a name="delete-stored-data"></a>Eliminación de datos almacenados

**P.** : ¿Qué datos almacena Authenticator en mi nombre y cómo puedo eliminarlo?

**R.** : La aplicación Authenticator recopila tres tipos de información:<ul><li>Información de la cuenta que proporciona al momento de añadirla. Estos datos se pueden quitar mediante la eliminación de la cuenta.</li><li>Datos de registro de diagnóstico que solo están en la aplicación hasta que seleccione la opción **Enviar registros** a Microsoft a través del menú de **Ayuda** de la aplicación. Estos registros pueden contener datos personales, como direcciones de correo electrónico, direcciones de servidor o direcciones IP. También pueden contener datos de dispositivo, como el nombre del dispositivo y la versión del sistema operativo. Los datos personales recopilados se limitan a la información necesaria para ayudar a solucionar problemas de la aplicación. Puede examinar estos archivos de registro en la aplicación en cualquier momento para ver la información que se recopila. Si envía los archivos de registro, los ingenieros de la aplicación de autenticación los usarán solo para solucionar los problemas notificados por los clientes.</li><li>Datos de uso no personalmente identificables, como "se ha iniciado el flujo de adición de cuenta/la cuenta se ha añadido correctamente" o "notificación aprobada". Estos datos son una parte integral de nuestras decisiones de ingeniería. Su uso nos ayuda a determinar dónde podemos mejorar las aplicaciones de forma que sea importante para usted. Verá una notificación de esta recopilación de datos cuando use la aplicación por primera vez. Le informa de que se puede desactivar en la página **Configuración** de la aplicación. Puede activar o desactivar esta opción en cualquier momento.</li></ul>

### <a name="codes-in-the-app"></a>Códigos en la aplicación

**P.** : ¿Para qué sirven los códigos de la aplicación?

**R.** : Cuando abra Authenticator, podrá ver las cuentas que ha agregado como iconos. Las cuentas profesionales o educativas y las cuentas personales de Microsoft tendrán un número de seis u ocho dígitos visible en la vista de pantalla completa de la cuenta (a la que se accede pulsando el icono de la cuenta). Para otras cuentas, verá un número de seis u ocho dígitos en la página **Cuentas** de la aplicación.<br>Usará estos códigos como contraseña de un solo uso para verificar que usted es quien dice ser. Después de iniciar sesión con su nombre de usuario y contraseña, tendrá que escribir el código de verificación asociado a esa cuenta. Por ejemplo, si es Katy e inicia sesión en su cuenta de Contoso, pulsaría en el icono de la cuenta y usaría el código de verificación 895823. Para la cuenta de Outlook, debe seguir los mismos pasos.<br>Pulse en el icono de la cuenta de Contoso.<br>![Iconos de cuenta en la aplicación Authenticator](media/user-help-auth-app-faq/katy-signin.png)<br>Después de pulsar en el icono de la cuenta de Contoso, el código de verificación estará visible en pantalla completa.<br>![Código de verificación en el icono de cuenta de Authenticator](media/user-help-auth-app-faq/verification-code.png)

### <a name="countdown-timer"></a>Temporizador de cuenta regresiva

**P.** : ¿Por qué el número que se encuentra después del código es regresivo?

**R.** : Es posible que vea un temporizador de 30 segundos contando hacia atrás situado junto a su código de verificación activo. Este temporizador es para que nunca inicie sesión con el mismo código dos veces. A diferencia de una contraseña, no queremos que recuerde este número. La idea es que solo un usuario con acceso a su teléfono conozca el código.

### <a name="grayed-account-tile"></a>Icono de cuenta atenuado

**P.** : ¿Por qué es gris el icono de mi cuenta?

**R.** : Algunas organizaciones requieren que Authenticator funcione con el inicio de sesión único y que proteja los recursos de la organización. En esta situación, la cuenta no se usa para la verificación en dos pasos y se muestra en color gris o como inactiva. Este tipo de cuenta suele denominarse una cuenta de "agente".

### <a name="device-registration"></a>Registro de dispositivos

**P.** : ¿Qué es el registro de dispositivos?
**R.** : Es posible que su organización le exija que registre el dispositivo para realizar el seguimiento del acceso a los recursos protegidos, como archivos y aplicaciones. También podrían activar el acceso condicional para reducir el riesgo de acceso no deseado a esos recursos. Puede anular el registro de su dispositivo en **Configuración** , pero puede perder el acceso a los correos electrónicos en Outlook, los archivos en OneDrive y ya no podrá usar el inicio de sesión con el teléfono.

### <a name="verification-codes-when-connected"></a>Códigos de verificación cuando se está conectado

**P.** : ¿Es necesario estar conectado a Internet o a mi red para obtener y usar los códigos de verificación?

**R.** : Los códigos no requieren que esté conectado a Internet o a los datos, por lo que no necesita servicio telefónico para iniciar sesión. Además, dado que la aplicación deja de ejecutarse tan pronto como la cierra, no agotará la batería.

### <a name="no-notifications-when-app-is-closed"></a>No hay notificaciones cuando la aplicación está cerrada

**P.** : ¿Por qué solo recibo notificaciones cuando la aplicación está abierta? Cuando la aplicación está cerrada, no recibo notificaciones.

**R.** : Si está recibiendo notificaciones, pero no una alerta, incluso con el timbre activado, debe comprobar la configuración de la aplicación. Asegúrese de que la aplicación está activada para usar sonido o vibrar cuando se reciben notificaciones. Si no recibe notificaciones, debe comprobar las siguientes condiciones:<ul><li>¿El teléfono se encuentra en modo silencioso o no molestar? Estos modos pueden impedir que las aplicaciones envíen notificaciones.</li><li>¿Puede obtener notificaciones de otras aplicaciones? De lo contrario, puede haber un problema con las conexiones de red en su teléfono o el canal de notificaciones de Android o Apple. Puede intentar resolver las conexiones de red a través de la configuración del teléfono. Es posible que tenga que comunicarse con el proveedor de servicios para obtener ayuda con el canal de notificaciones de Android o Apple.</li><li>¿Puede obtener notificaciones para algunas cuentas en la aplicación, pero para otras? Si es así, quite la cuenta problemática de la aplicación, agréguela de nuevo permitiendo notificaciones y vea si esto soluciona el problema.</li></ul>Si ha probado todos estos pasos y sigue teniendo problemas, es recomendable que envíe todos los archivos de registro para su diagnóstico. Abra la aplicación, vaya a **Ayuda** y seleccione **Enviar registros**. Después, vaya al [foro de la aplicación Microsoft Authenticator](https://social.technet.microsoft.com/Forums/en-US/home?forum=MicrosoftAuthenticatorApp) e indíquenos cuál es el problema y qué pasos ha probado.

### <a name="switch-to-push-notifications"></a>Cambio a notificaciones push

**P.** : Estoy usando los códigos de verificación en la aplicación, pero ¿cómo cambio a las notificaciones push?

**R.** : Puede configurar notificaciones para su cuenta profesional o educativa (si se lo permite el administrador) o para su cuenta de Microsoft personal. Las notificaciones no funcionarán para cuentas de terceros, como Google o Facebook.<br>Para cambiar su cuenta personal a las notificaciones, tendrá que volver a registrar el dispositivo con la cuenta. Vaya a **Agregar cuenta** , seleccione **Cuenta personal de Microsoft** y, a continuación, inicie sesión con su nombre de usuario y contraseña.<br>Para una cuenta profesional o educativa, su organización decide si permite las notificaciones de un solo clic o no.

### <a name="notifications-for-other-accounts"></a>Notificaciones para otras cuentas

**P.** : ¿Funcionan las notificaciones con cuentas que no son de Microsoft?

**R.** : No, las notificaciones solo funcionan con cuentas de Microsoft y de Azure Active Directory. Si su trabajo o centro educativo usa cuentas de Azure AD, pueden desactivar esta característica.

### <a name="backup-and-recovery"></a>Copia de seguridad y recuperación

**P.** : Obtuve un dispositivo nuevo o restauré mi dispositivo desde una copia de seguridad. ¿Cómo configuro mis cuentas en Authenticator de nuevo?

**R.** : Si ha activado la **copia de seguridad en la nube** en su dispositivo antiguo, puede usar esa copia de seguridad antigua para recuperar las credenciales de la cuenta en el dispositivo iOS o Android nuevo. Para más información, consulte el artículo [Copia seguridad y recuperación de las credenciales de cuenta con Authenticator](user-help-auth-app-backup-recovery.md).

### <a name="lost-device"></a>Dispositivo perdido

**P.** : He perdido mi dispositivo o lo cambié por uno nuevo. ¿Cómo puedo asegurarme de que las notificaciones no siguen yendo a mi dispositivo antiguo?

**R.** : Al agregar Authenticator al nuevo dispositivo no se elimina automáticamente la aplicación del antiguo. Eliminar la aplicación del dispositivo antiguo no es suficiente. Debe eliminar la aplicación de dispositivo antiguo e indicar a Microsoft o a su organización que olvide y anule el registro del dispositivo antiguo.<ul><li>**Para eliminar la aplicación de un dispositivo con una cuenta Microsoft personal.** Vaya al área de verificación en dos pasos de la página de [seguridad de la cuenta](https://account.microsoft.com/security)  y elija desactivar la verificación del dispositivo antiguo.</li><li>**Para quitar la aplicación de un dispositivo con una cuenta Microsoft profesional o educativa.** Vaya al área de verificación en dos pasos de la [página MyApps](https://myapps.microsoft.com/) o el portal personalizado de la organización y desactive la verificación del dispositivo antiguo.</li></ul>

### <a name="remove-account-from-app"></a>Eliminación de la cuenta de la aplicación

**P.** : ¿Cómo se quita una cuenta de la aplicación?

**R.** : Pulse en el icono de la cuenta que desea quitar de la aplicación para ver la pantalla completa de la cuenta. Pulse en **Quitar cuenta** para quitar la cuenta de la aplicación.<br>Si tiene un dispositivo que está registrado en su organización, puede que necesite un paso más para quitar la cuenta. En estos dispositivos, Authenticator se registra automáticamente como administrador del dispositivo. Si quiere desinstalar totalmente la aplicación, primero debe anular el registro de la aplicación en la configuración de la aplicación.

### <a name="too-many-permissions"></a>Demasiados permisos

**P.** : ¿Por qué la aplicación solicita tantos permisos?

**R.** : Esta es una lista completa de permisos que se pueden solicitar y una explicación de cómo se utilizan en la aplicación. Los permisos específicos que aparezcan dependerán del tipo de teléfono que tenga.<ul><li>**Usar hardware biométrico.** Algunas cuentas profesionales o educativas requieran un PIN adicional cada vez que comprueba su identidad. La aplicación requiere su consentimiento para usar el reconocimiento biométrico o facial en lugar de escribir el PIN.</li><li>**Cámara.** Se usa para digitalizar códigos QR al agregar una cuenta Microsoft profesional, educativa o de otro tipo.</li><li>**Contactos y teléfono.** La aplicación requiere este permiso para buscar las cuentas profesionales o educativas de Microsoft en el teléfono y agregarlas a la aplicación.</li><li>**SMS.** Se utiliza para asegurarnos de que su número de teléfono coincide con el que tenemos en el registro cuando inicia sesión con su cuenta personal de Microsoft por primera vez. Enviamos un mensaje de texto al teléfono donde instaló la aplicación con un código de verificación de 6-8 caracteres. No es necesario que busque este código y lo especifique porque Authenticator lo encuentra automáticamente en el mensaje de texto.</li><li>**Extensión a otras aplicaciones.** La notificación que verifica su identidad también aparece en cualquier otra aplicación en ejecución.</li><li>**Recibir datos de internet.** Este permiso es necesario para enviar notificaciones.</li><li>**Impedir que el teléfono entre en modo de suspensión.** Si registra el dispositivo con su organización, dicha organización puede cambiar esta directiva en su teléfono.</li><li>**Controlar la vibración.** Puede elegir si quiere que el dispositivo vibre cada vez que se recibe una notificación para comprobar su identidad.</li><li>**Usar hardware de huella digital.** Algunas cuentas profesionales o educativas requieran un PIN adicional cada vez que comprueba su identidad. Para facilitar el proceso, se permite el uso de la huella digital en lugar de escribir el PIN.</li><li> **Ver conexiones de red.** Cuando se agrega una cuenta de Microsoft, la aplicación requiere conexión de red o a Internet.</li><li>**Leer el contenido del almacenamiento**. Este permiso solo se usa al notificar un problema técnico a través de la configuración de la aplicación. Parte de la información de su almacenamiento se recopila para diagnosticar el problema.</li><li>**Acceso completo a la red.** Este permiso es necesario para enviar notificaciones para comprobar su identidad.</li><li>**Ejecutar al inicio.** Si reinicia el teléfono, este permiso garantiza que continuará recibiendo notificaciones para comprobar su identidad.</li></ul>

### <a name="approve-requests-without-unlocking"></a>Aprobación de solicitudes sin desbloqueo

**P.** : ¿Por qué Authenticator permite aprobar una solicitud sin desbloquear el dispositivo?

**R.** : No tiene que desbloquear el dispositivo para aprobar solicitudes de comprobación porque todo lo que necesita demostrar es que lleva el teléfono encima. La verificación en dos pasos realiza dos comprobaciones: una comprobación de algo que sabe y una comprobación de algo que tiene. Lo que sabe es la contraseña. Lo que tiene es el teléfono (configurado con Authenticator y registrado como una prueba de autenticación multifactor). Por tanto, al tener el teléfono y aprobar la solicitud, se cumplen los criterios del segundo factor de la autenticación.

### <a name="activity-notifications"></a>Notificaciones de actividad

**P.** : ¿Por qué recibo notificaciones acerca de la actividad de mi cuenta?

**R.** : Las notificaciones de actividad se envían a Authenticator inmediatamente, cada vez que se realiza un cambio en las cuentas personales de Microsoft, lo que ayuda a que estén más protegidas. Antes, enviábamos estas notificaciones solo a través del correo electrónico y SMS. Para más información acerca de estas notificaciones de actividad, consulte [¿Qué sucede si se produce un inicio de sesión inusual en tu cuenta?](https://support.microsoft.com/help/13967/microsoft-account-unusual-sign-in). Para cambiar la ubicación donde recibe las notificaciones, inicie sesión en la página [¿Dónde podemos enviarle alertas no críticas de la cuenta?](https://account.live.com/SecurityNotifications/Update) de la cuenta.

### <a name="one-time-passcodes"></a>Códigos de acceso de un solo uso

**P.** : Los códigos de acceso de un solo uso no funcionan. ¿Cuál debo hacer?

**R.** : Asegúrese de que la fecha y la hora del dispositivo sean correctas y se estén sincronizando automáticamente. Si la fecha y la hora son incorrectas o no están sincronizadas, el código no funcionará.

### <a name="windows-10-mobile"></a>Windows 10 Mobile

**P.** : El sistema operativo Windows 10 Mobile quedó en desuso en diciembre de 2019. ¿Quedará en desuso también Microsoft Authenticator en sistemas operativos Windows Mobile?

**R.** : Authenticator dejará de admitirse en todos los sistemas operativos Windows Mobile después del 28 de febrero de 2020. Los usuarios no podrán recibir nuevas actualizaciones de la aplicación después de la fecha mencionada. Después del 28 de febrero de 2020, los servicios de Microsoft que actualmente admiten autenticaciones con Microsoft Authenticator en todos los sistemas operativos Windows Mobile comenzarán a retirar su soporte técnico. Para autenticarse en los servicios de Microsoft, se recomienda firmemente a todos los usuarios que cambien a un mecanismo de autenticación alternativo antes de esta fecha.

### <a name="default-mail-app"></a>Aplicación de correo predeterminada

**P.** : Al iniciar sesión en mi cuenta profesional o educativa con la aplicación predeterminada de correo electrónico que viene con iOS, Authenticator solicita la información de comprobación de seguridad. Después de escribir esa información y volver a la aplicación de correo, aparece un error. ¿Qué puedo hacer?

**R.** : Esto suele ocurrir porque el inicio de sesión y la aplicación de correo se producen en dos aplicaciones diferentes, lo que hace que el proceso de inicio de sesión en segundo plano inicial deje de funcionar y se produzca un error. Para intentar solucionar este error, se recomienda seleccionar el icono **Safari** en la parte inferior derecha de la pantalla mientras se inicia sesión en la aplicación de correo. Al pasar a Safari, todo el proceso de inicio de sesión se produce en una sola aplicación, lo que le permite iniciar sesión correctamente en la aplicación.

### <a name="apple-watch-watchos-7"></a>watchOS 7 en Apple Watch

**P.** : ¿Por qué tengo problemas con Apple Watch en watchOS 7?

**R.** : Hay un problema con la aprobación de notificaciones en watchOS 7 y estamos trabajando con Apple para solucionarlo. Mientras tanto, todas las notificaciones que requieran la aplicación watchOS de Microsoft Authenticator se deben autenticar en el teléfono.

### <a name="apple-watch-doesnt-show-accounts"></a>Apple Watch no muestra las cuentas

**P.** : ¿Por qué no aparecen todas mis cuentas al abrir Authenticator en mi Apple Watch?

**R.** : Authenticator admite solo el uso de cuentas Microsoft personales, o profesionales o educativas con notificaciones push en la aplicación complementaria de Apple Watch. Para otras cuentas, como Google o Facebook, tendrá que abrir la aplicación Authenticator en su teléfono para ver los códigos de verificación.

### <a name="apple-watch-notifications"></a>Notificaciones de Apple Watch

**P.** : ¿Por qué no puedo aprobar o denegar las notificaciones en mi Apple Watch?

**R.** : En primer lugar, asegúrese de que ha actualizado a Authenticator, versión 6.0.0 o una versión superior en su iPhone. Después, abra la aplicación complementaria de Microsoft Authenticator en su Apple Watch y busque las cuentas mediante el botón **Configurar** que aparece debajo de ellas. Complete el proceso de configuración para aprobar las notificaciones para esas cuentas.

### <a name="apple-watch-communication-error"></a>Error de comunicación de Apple Watch

**P.** : Recibo un error de comunicación entre Apple Watch y mi teléfono. ¿Qué puedo hacer para solucionar el problema?

**R.** : Este error se produce cuando la pantalla de Watch entra en suspensión antes de que finalice la comunicación con el teléfono.<br><b>Si el error se produce durante la instalación:</b><br>Intente volver a ejecutar el programa de instalación y asegúrese de mantener su dispositivo Watch activo hasta que termine el proceso. Al mismo tiempo, abra la aplicación en su teléfono y responda a las indicaciones que aparezcan.<br>Si el teléfono y el reloj aún no se comunican, puede probar las siguientes acciones:<ol><li>Obligue a la aplicación del teléfono Microsoft Authenticator a cerrarse y ábrala de nuevo en su iPhone.</li><li>Obligue a la aplicación complementaria a c errarse en su Apple Watch.<ol><li> Abra la aplicación complementaria Microsoft Authenticator en el reloj.</li><li>Mantenga presionado el botón lateral hasta que aparezca la pantalla **Apagar**.</li><li>Suelte el botón lateral y mantenga presionado Digital Crown para obligar a salir de la aplicación activa.</li></ol></li><li>Desactive las conexiones Bluetooth y Wi-Fi tanto en el teléfono como en el reloj y luego, vuelva a activarla.</li><li>Reinicie su iPhone y el reloj.</li></ol><b>Si el error se produce cuando intenta aprobar una notificación:</b><br>La próxima vez que intente aprobar una notificación en Apple Watch, mantenga la pantalla activa hasta que la solicitud se complete y oiga el sonido que indica que se realizó correctamente.

### <a name="apple-watch-companion-app-not-syncing"></a>La aplicación complementaria de Apple Watch no se sincroniza

**P.** : ¿Por qué la aplicación complementaria de Microsoft Authenticator para Apple Watch no se sincroniza con el reloj o aparece en este?

**R.** : Si la aplicación no aparece en el reloj, pruebe las siguientes acciones: <ol><li>Asegúrese de que el reloj ejecuta watchOS 4.0 o superior.</li><li>Sincronice el reloj de nuevo.</li></ol>

### <a name="apple-watch-companion-app-crashed"></a>La aplicación complementaria de Apple Watch se bloquea

**P.** : Mi aplicación complementaria de Apple Watch se ha bloqueado. ¿Puedo enviar mis registros de bloqueo para que pueda investigar?

**R.** : Primero debe asegurarse de que ha optado por compartir su análisis con nosotros. Si es un usuario de TestFlight, ya está registrado. En caso contrario, puede ir a **Configuración > Privacidad > Análisis** y seleccione las opciones **Share iPhone & Watch analytics** (Compartir análisis de iPhone y Watch) y **Share with App Developers** (Compartir con los desarrolladores de aplicaciones).<br>Después de registrarse, puede intentar reproducir el bloqueo para que los registros de bloqueo se nos envíen automáticamente para realizar la investigación. Pero, si no se puede reproducir el bloqueo, puede copiar manualmente los archivos de registro y enviárnoslos.<ol><li>Abra la aplicación Watch en su teléfono, vaya a **Configuración > General** y haga clic en **Copy Watch Analytics** (Copiar análisis de Watch).</li><li>Busque el bloqueo correspondiente en **Configuración > Privacidad > Análisis > Análisis de datos** y copie manualmente todo el texto.</li><li>Abra Authenticator en su teléfono y pegue el texto copiado en el cuadro de texto **Share with App Developers** (Compartir con los desarrolladores de aplicaciones) en la página **Enviar registros**.</li></ol>

## <a name="next-steps"></a>Pasos siguientes

- Si tiene dificultades para obtener el código de verificación de su cuenta Microsoft personal, consulte la sección **Solución de problemas de código de seguridad** del artículo [Información de seguridad y códigos de seguridad de la cuenta de Microsoft](https://support.microsoft.com/help/12428/microsoft-account-security-info-verification-codes).

- Si desea más información sobre la verificación en dos pasos, vea [Configuración de mi cuenta para la verificación en dos pasos](multi-factor-authentication-end-user-first-time.md).

- Para más información sobre seguridad, consulte [Introducción a la información de seguridad (versión preliminar)](./security-info-setup-signin.md).

- Si no encontró aquí la respuesta a su pregunta, nos gustaría ayudarle. Acceda al [foro de la aplicación Microsoft Authenticator](https://social.technet.microsoft.com/Forums/en-us/home?forum=MicrosoftAuthenticatorApp) para publicar la pregunta y obtener ayuda de la comunidad, para dejar un comentario en la página.
