---
title: Zugriff auf Adobe Pass und Adobe
description: Zugriff auf Adobe Pass und Adobe
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---


# Zugriff auf Adobe Pass und Adobe {#adobe-pass-and-adobe-access}

Adobe Pass ( [](https://www.adobe.com/products/adobepass/)) bietet Benutzer-/Geräteauthentifizierung und Autorisierung für mehrere Content-Provider. Der Benutzer muss über ein gültiges Kabel-TV- oder Satelliten-TV-Abonnement verfügen.

<!--<a id="fig_cln_bc2_44"></a>-->

![](assets/AdobePass_web.png)

Adobe Pass kann zusammen mit Adobe Access zum Schutz der Medieninhalte verwendet werden. In diesem Szenario kann der Videoplayer (SWF) eine weitere SWF-Datei mit dem Namen *Access Enabler* laden, die von Adobe Systems gehostet wird. Der *Access Enabler* wird verwendet, um eine Verbindung zum Adobe Pass-Dienst herzustellen und die SSO-Integration von SAML mit den Identitäts-Provider-Systemen des MVPD (Multichannel Video Programming Distributor) zu erleichtern. Dazu gehört die kurze Weiterleitung des Browsers des Benutzers zur MVPD-Anmeldeseite, dann die Beibehaltung eines AuthN-Tokens und schließlich die Rückkehr zur Content-Website mit einer zwischengespeicherten AuthN-Sitzung.

Der *Access Enabler* kann dann Backend-Autorisierungen zwischen dem Adobe Pass-Dienst und dem MVPD erleichtern. Die MVPD behält die Geschäftslogik bei und bestimmt, auf welche Inhalte der Benutzer Zugriff hat. Die Berechtigung wird in einem zusätzlichen AuthZ-Token für diese Inhaltsressource beibehalten und an den Client zurückgesendet.

Die Authentifizierungs- und Autorisierungstoken werden mit der eindeutigen ID und dem privaten Schlüssel des Adobe Access-Clients signiert, um Manipulationen oder Spoofing zu vermeiden. Auf dieses Token kann nur über *Access Enabler* zugegriffen werden.

Der Videoplayer kann den Vorgang durch Aufruf von `getAuthorization` unter *Access Enabler* Trigger werden. Wenn gültige AuthN/AuthZ-Token vorhanden sind, gibt der *AccessEnabler* einen Rückruf an den Videoplayer aus, der ein Token für die Wiedergabe des Videoinhalts mit kurzer Lebensdauer enthält.

Adobe Pass stellt eine Java-Bibliothek für die Medienvalidierung zur Verfügung, die auf einem Server bereitgestellt werden kann. Wenn Sie den Flash Access-Server zum Schutz von Inhalten verwenden, können Sie den MedienToken-Validator mit einem serverseitigen Plug-In für den Zugriff auf die Adobe integrieren, um nach erfolgreicher Überprüfung des Medientokens automatisch eine generische Lizenz auszustellen. Der Inhalt wird dann vom CDN-Server an den Client gestreamt. Um eine Inhaltslizenz zu erwerben, kann das Token mit kurzer Lebensdauer an den Adobe Access-Server gesendet werden, auf dem die Gültigkeit des Tokens überprüft und eine Lizenz erteilt werden kann.

Das dauerhaft genutzte AuthN-Token wird im Allgemeinen von *Access Enabler* in allen Inhaltsentwicklern verwendet, um das AuthN für diesen MVPD-Abonnenten zu repräsentieren. Darüber hinaus können die Adobe Access Server- und Token-Prüfstelle vom CDN oder einem Dienstleister im Auftrag des Content Providers betrieben werden.
