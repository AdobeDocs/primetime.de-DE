---
title: Umgang mit Get Server-Versionsanfragen
description: Umgang mit Get Server-Versionsanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---

# Umgang mit Get Server-Versionsanfragen{#handling-get-server-version-requests}

Adobe Access Client 3.0 und höher sendet eine Anfrage &quot;Get Server Version&quot;, um die Serverfunktionen zu ermitteln. Alle Server, die Adobe Access SDK 3.0 und höher verwenden, müssen Unterstützung für Get Server Version-Anfragen implementieren.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* Die Anforderungs-URL muss &quot;Lizenzserver-URL in Metadaten&quot;+ &quot;/flashaccess/getServerVersion/v3&quot;lauten.

Bei Adobe Access SDK 4.0 und höher zeigt die Antwort auf eine Anfrage vom Typ &quot;Get Server Version&quot;den Clients an, dass der Server die Versionen 3 und 4 des Adobe Access-Protokolls unterstützt.
