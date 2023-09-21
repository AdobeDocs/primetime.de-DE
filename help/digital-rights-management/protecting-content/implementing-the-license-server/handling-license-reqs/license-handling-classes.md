---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---

# Übersicht {#overview}

Um eine Lizenz zu erhalten, stellen Clients eine Anfrage von den Metadaten, die in den gepackten Inhalt eingebettet sind, und senden diese Anfrage dann an den Lizenzserver. Der Lizenzserver verwendet Informationen, die aus den Inhaltsmetadaten extrahiert wurden, zum Generieren einer Lizenz.

Wenn Client und Server beide das Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;Lizenzserver-URL in Metadaten&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Wenn die Protokollversion 3 das Maximum ist, das entweder vom Client oder Server unterstützt wird, senden Primetime DRM-Clients dann Authentifizierungsanfragen an &quot;Lizenzserver-URL in Metadaten&quot;+ &quot; [!DNL /flashaccess/license/v3]&quot;. Andernfalls werden Authentifizierungsanfragen an &quot;Lizenzserver-URL in Metadaten&quot;und &quot;gesendet. [!DNL /flashaccess/license/v1]&quot;

Ein Gerät kann mehrere Lizenzen für denselben Inhalt (dieselbe Lizenzkennung) haben, jedoch nur eine Lizenz für eine bestimmte Lizenz-ID und DRM-Richtlinien-ID besitzen. Wenn eine Lizenz mit einer doppelten LicenseID/PolicyID empfangen wird, ersetzt die neue Lizenz die alte nur, wenn das Ausstellungsdatum der neuen Lizenz nach dem Ausstellungsdatum der bestehenden Lizenz liegt. Diese Logik wird verwendet, um in Inhalte eingebettete Lizenzen zu verarbeiten. Daher wird nicht empfohlen, mehr als eine Lizenz mit derselben DRM-Richtlinien-ID in einen Inhaltsbereich einzubetten. Dasselbe gilt für Lizenzen, die über die `DRMManager.storeVoucher()` ActionScript3-API; wenn der Client bereits über eine Lizenz mit einem späteren Ausstellungsdatum verfügt, kann die bereitgestellte Lizenz ignoriert werden.

## Handling von Lizenzanfragen {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Dies ist die Handler-Klasse für Lizenzanfragen. Er liest und analysiert Lizenzanfragen. Seine `getRequests()` -Methode gibt eine Liste von `LicenseRequestMessage` Objekte.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Dies ist die Anforderungsmeldungsklasse. Der Aufrufer sollte durch die `LicenseRequestMessage` Liste zurückgegeben von `getRequests()`und generieren Sie für jede Anfrage entweder eine Lizenz oder legen Sie einen Fehler-Code fest. Aufruf `LicenseRequestMessage.getContentInfo()` , um Informationen zu erhalten, die aus den Inhaltsmetadaten, einschließlich der Inhalts-ID, der Lizenzkennung und der DRM-Richtlinien, extrahiert wurden.

Lizenzen und Fehler werden gleichzeitig gesendet, wenn die Variable `LicenseHandler.close()` -Methode aufgerufen wird.

Siehe [Referenzdokumentation zur DRM-Server-API](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html) für Details.
