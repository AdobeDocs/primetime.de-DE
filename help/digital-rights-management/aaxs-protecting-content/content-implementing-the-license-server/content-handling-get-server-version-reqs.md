---
title: Verarbeitung von Get Server-Versionsanforderungen
description: Verarbeitung von Get Server-Versionsanforderungen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '102'
ht-degree: 0%

---


# Verarbeitung von Get Server-Versionsanforderungen{#handling-get-server-version-requests}

Adobe Access Client 3.0 und höher senden eine Serverversion-Anforderung, um die Serverfunktionen zu bestimmen. Alle Server, die Adobe Access SDK 3.0 oder höher verwenden, müssen Unterstützung für Get Server-Versionsanforderungen implementieren.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* Die Anforderungs-URL muss &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/getServerVersion/v3&quot; lauten.

Bei Adobe Access SDK 4.0 und höher zeigt die Antwort auf eine Anfrage zur Serverversion an, dass der Server die Versionen 3 und 4 des Adobe Access-Protokolls unterstützt.
