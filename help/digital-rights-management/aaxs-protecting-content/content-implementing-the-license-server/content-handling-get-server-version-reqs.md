---
seo-title: Verarbeitung von Get Server-Versionsanforderungen
title: Verarbeitung von Get Server-Versionsanforderungen
uuid: a3084faa-cf3d-45cc-a244-298308c4cf15
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Verarbeitung von Get Server-Versionsanforderungen{#handling-get-server-version-requests}

Adobe Access Client 3.0 und höher senden eine Get Server Version-Anforderung, um die Funktionen des Servers zu bestimmen. Alle Server, die Adobe Access SDK 3.0 oder höher verwenden, müssen Unterstützung für Get Server-Versionsanforderungen implementieren.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionHandler`
* Die Anforderungsmeldungsklasse lautet `com.adobe.flashaccess.sdk.protocol.getversion.GetServerVersionRequestMessage`
* Die Anforderungs-URL muss &quot;Lizenzserver-URL in Metadaten&quot; + &quot;/flashaccess/getServerVersion/v3&quot; lauten.

Bei Adobe Access SDK 4.0 und höher zeigt die Antwort auf eine Anfrage zur Serverversion an, dass der Server die Versionen 3 und 4 des Adobe Access-Protokolls unterstützt.
