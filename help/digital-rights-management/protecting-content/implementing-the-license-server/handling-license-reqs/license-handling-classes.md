---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 0%

---


# Übersicht {#overview}

Um eine Lizenz zu erhalten, erstellen Clients eine Anforderung aus den in den gepackten Inhalt eingebetteten Metadaten und senden diese Anforderung dann an den Lizenzserver. Der Lizenzserver verwendet Informationen, die aus den Inhaltsmetadaten extrahiert wurden, um eine Lizenz zu generieren.

Wenn Client und Server beide Protokoll Version 5 unterstützen, lautet die Anforderungs-URL &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/license/v4]&quot;. Wenn Protokollversion 3 das Maximum ist, das vom Client oder Server unterstützt wird, senden Primetime DRM-Clients dann Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/license/v3]&quot;. Andernfalls werden Authentifizierungsanforderungen an &quot;URL des Lizenzservers in Metadaten&quot; + &quot; [!DNL /flashaccess/license/v1]&quot; gesendet

Ein Gerät kann über mehrere Lizenzen für denselben Inhalt verfügen (gleiche Lizenz-ID), jedoch nur eine Lizenz für eine bestimmte Lizenz-ID und DRM-Richtlinie-ID besitzen. Wenn eine Lizenz mit einer LicenseID/PolicyID des Duplikats erteilt wird, ersetzt die neue Lizenz die alte nur, wenn das Ausgabedatum der neuen Lizenz nach dem Ausgabedatum der vorhandenen Lizenz liegt. Diese Logik wird verwendet, um in Inhalt eingebettete Lizenzen zu verarbeiten. Es wird daher nicht empfohlen, mehr als eine Lizenz mit derselben DRM-Richtlinien-ID in einen Inhaltsabschnitt einzubetten. Die gleiche Logik gilt für Lizenzen, die über die `DRMManager.storeVoucher()` ActionScript3-API an den Client weitergeleitet werden. Wenn der Kunde bereits über eine Lizenz mit einem späteren Ausgabedatum verfügt, kann die bereitgestellte Lizenz ignoriert werden.

## Lizenzanforderungsbearbeitungsklassen {#section_190E3BEF316C4B09ACC21E4C2BAC5C75}

* `com.adobe.flashaccess.sdk.protocol.license.LicenseHandler` - Dies ist die Klasse des Lizenzanforderungshandlers. Er liest und analysiert Lizenzanforderungen. Die `getRequests()`-Methode gibt eine Liste von `LicenseRequestMessage`-Objekten zurück.
* `com.adobe.flashaccess.sdk.protocol.license.LicenseRequestMessage` - Dies ist die Anforderungsmeldungsklasse. Der Aufrufer sollte die `LicenseRequestMessage`-Liste durchlaufen, die von `getRequests()` zurückgegeben wird, und für jede Anforderung entweder eine Lizenz generieren oder einen Fehlercode festlegen. Rufen Sie `LicenseRequestMessage.getContentInfo()` auf, um Informationen aus den Inhaltsmetadaten abzurufen, einschließlich der Inhalts-ID-, Lizenz-ID- und DRM-Richtlinien.

Lizenzen und Fehler werden gleichzeitig gesendet, wenn die `LicenseHandler.close()`-Methode aufgerufen wird.

Weitere Informationen finden Sie in der Referenzdokumentation zur DRM-Server-API](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/overview-summary.html).[
