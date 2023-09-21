---
title: Zugriff auf Adobe Pass und Adobe
description: Zugriff auf Adobe Pass und Adobe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Zugriff auf Adobe Pass und Adobe {#adobe-pass-and-adobe-access}

ADOBE PASS ( [](https://www.adobe.com/products/adobepass/)) bietet Benutzer-/Geräteauthentifizierung und -autorisierung für mehrere Inhaltsanbieter. Der Benutzer muss über ein gültiges Kabel-TV- oder Sat-TV-Abonnement verfügen.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kann zusammen mit Adobe Access zum Schutz von Medieninhalten verwendet werden. In diesem Szenario kann der Videoplayer (SWF) eine andere SWF laden, die als *Access Enabler*, das von Adobe Systems gehostet wird. Die *Access Enabler* wird verwendet, um eine Verbindung zum Adobe Pass-Dienst herzustellen und die SAML SSO-Integration mit den Identitäts-Provider-Systemen von MVPD (Multichannel Video Programming Distributor) zu erleichtern. Dazu gehört es, den Browser des Benutzers kurz zur MVPD-Anmeldeseite umzuleiten, dann ein AuthN-Token zu persistieren und schließlich mit einer zwischengespeicherten AuthN-Sitzung zur Inhalts-Website zurückzukehren.

Die *Access Enabler* kann dann Backend-Berechtigungen zwischen dem Adobe Pass-Dienst und dem MVPD erleichtern. Der MVPD verwaltet die Geschäftslogik und bestimmt, zu welchem Inhalt der Benutzer berechtigt ist. Die Berechtigung wird für diese Inhaltsressource in einem zusätzlichen AuthZ-Token beibehalten und an den Client zurückgesendet.

Die Authentifizierungs- und Autorisierungstoken werden mit der eindeutigen ID und dem privaten Schlüssel des Adobe Access-Clients signiert, um Manipulationen oder Spoofing zu vermeiden. Auf dieses Token kann nur über die *Access Enabler*.

Der Videoplayer kann den Prozess durch Aufruf von `getAuthorization` auf *Access Enabler*. Wenn gültige AuthN/AuthZ-Token vorhanden sind, wird die *AccessEnabler* gibt einen Rückruf an den Videoplayer aus, der ein kurzlebiges Medien-Token für die Wiedergabe des Videoinhalts enthält.

Adobe Pass stellt eine Java-Bibliothek für den Media Token-Validator bereit, die auf einem Server bereitgestellt werden kann. Wenn Sie den Flash Access-Server für den Inhaltsschutz verwenden, können Sie den Medien-Token-Validator in ein serverseitiges Adobe Access-Plug-in integrieren, um nach der erfolgreichen Validierung des Medien-Tokens automatisch eine generische Lizenz zu erteilen. Der Inhalt wird dann von den CDN-Servern an den Client gestreamt. Um eine Inhaltslizenz zu erhalten, kann das kurzlebige Medien-Token an den Adobe Access-Server gesendet werden, wo die Gültigkeit des Tokens verifiziert und eine Lizenz erteilt werden kann.

Das dauerhaft genutzte AuthN-Token wird im Allgemeinen von der *Access Enabler* für alle Inhaltsentwickler, um den AuthN für diesen MVPD-Abonnenten zu repräsentieren. Darüber hinaus können Adobe Access Server und Token Verifier vom CDN oder einem Dienstleister im Auftrag des Content Providers betrieben werden.
