---
title: Verarbeiten von Server-Versionsanfragen
description: Verarbeiten von Server-Versionsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Verarbeiten von Server-Versionsanfragen {#handle-get-server-version-requests}

Adobe Primetime DRM Client 3.0 oder höher sendet eine Anfrage zum Abrufen der Server-Version , um die Funktionen des Servers zu ermitteln. Alle Server, die das Primetime DRM SDK 3.0 oder höher verwenden, müssen Unterstützung für Get Server Version-Anfragen implementieren.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* Die Anforderungs-URL muss &quot;Lizenzserver-URL in Metadaten&quot;lauten + &quot; [!DNL /flashaccess/getServerVersion/v3]&quot;

Bei Primetime DRM SDK 4.0 oder höher zeigt die Antwort auf eine Anfrage zur Server-Version des Servers an Clients, dass der Server die Versionen 3 und 4 des Primetime DRM-Protokolls unterstützt.
