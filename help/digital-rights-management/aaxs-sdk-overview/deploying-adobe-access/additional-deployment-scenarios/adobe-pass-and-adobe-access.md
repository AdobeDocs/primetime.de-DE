---
seo-title: Adobe Pass und Adobe Access
title: Adobe Pass und Adobe Access
uuid: 09e75cd7-00b3-4f0f-869e-43dc4d5c3bf7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Adobe Pass und Adobe Access {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) bietet Benutzer-/Geräteauthentifizierung und Autorisierung über mehrere Content-Provider hinweg. Der Benutzer muss über ein gültiges Kabel-TV- oder Satelliten-TV-Abonnement verfügen.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kann zusammen mit Adobe Access zum Schutz der Medieninhalte verwendet werden. In diesem Szenario kann der Videoplayer (SWF) eine weitere SWF-Datei mit dem Namen *Access Enabler* laden, die von Adobe Systems gehostet wird. Der *Access Enabler* wird verwendet, um eine Verbindung zum Adobe Pass-Dienst herzustellen und die SSO-Integration von SAML mit den Identitäts-Provider-Systemen von MVPD (Multichannel Video Programming Distributor) zu erleichtern. Dazu gehört die kurze Weiterleitung des Browsers des Benutzers zur MVPD-Anmeldeseite, dann die Beibehaltung eines AuthN-Tokens und schließlich die Rückkehr zur Content-Website mit einer zwischengespeicherten AuthN-Sitzung.

Der *Access Enabler* kann dann Backend-Autorisierungen zwischen dem Adobe Pass-Dienst und dem MVPD erleichtern. Die MVPD behält die Geschäftslogik bei und bestimmt, auf welche Inhalte der Benutzer Zugriff hat. Die Berechtigung wird in einem zusätzlichen AuthZ-Token für diese Inhaltsressource beibehalten und an den Client zurückgesendet.

Die Authentifizierungs- und Autorisierungstoken werden mit der eindeutigen ID und dem privaten Schlüssel des Adobe Access-Clients signiert, um Manipulationen oder Spoofing zu vermeiden. Auf dieses Token kann nur über den *Access Enabler* zugegriffen werden.

Der Videoplayer kann den Prozess auslösen, indem er `getAuthorization` den *Access Enabler* aufruft. Wenn gültige AuthN/AuthZ-Token vorhanden sind, gibt der *AccessEnabler* einen Rückruf an den Videoplayer aus, der ein kurzlebiges MedienToken für die Wiedergabe des Videoinhalts enthält.

Adobe Pass bietet eine Java-Bibliothek für den Validator von MedienToken, die auf einem Server bereitgestellt werden kann. Wenn Sie den Flash Access-Server zum Schutz von Inhalten verwenden, können Sie den MedienToken-Validator in ein serverseitiges Adobe Access-Plug-In integrieren, um nach erfolgreicher Überprüfung des Media-Tokens automatisch eine generische Lizenz auszustellen. Der Inhalt wird dann vom CDN-Server an den Client gestreamt. Um eine Inhaltslizenz zu erhalten, kann das Token für kurzlebige Medien an den Adobe Access-Server gesendet werden, wo die Gültigkeit des Tokens überprüft und eine Lizenz erteilt werden kann.

Das dauerhaft genutzte AuthN-Token wird im Allgemeinen vom *Access Enabler* für alle Inhaltsentwickler verwendet, um das AuthN für diesen MVPD-Abonnenten zu repräsentieren. Darüber hinaus können Adobe Access Server und Token Verifier vom CDN oder einem Dienstleister im Auftrag des Content Providers betrieben werden.
