---
seo-title: Abrufen von Serverversionsanforderungen
title: Abrufen von Serverversionsanforderungen
uuid: 6e287f58-2ad2-428a-a76a-6847d06b0fd8
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# Verarbeiten von Serverversionsanforderungen {#handle-get-server-version-requests}

Adobe Primetime DRM Client 3.0 oder höher sendet eine Get Server Version-Anforderung, um die Funktionen des Servers zu bestimmen. Alle Server, die Primetime DRM SDK 3.0 oder höher verwenden, müssen die Unterstützung für Anfragen zur Get-Server-Version implementieren.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* Die Anforderungsmeldungsklasse ist `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* Die Anforderungs-URL muss &quot;Lizenzserver-URL in Metadaten&quot; + &quot; [!DNL /flashaccess/getServerVersion/v3]&quot;lauten.

Bei Primetime DRM SDK 4.0 oder höher zeigt die Antwort auf eine Anfrage zur Serverversion an, dass der Server die Versionen 3 und 4 des Primetime DRM-Protokolls unterstützt.
