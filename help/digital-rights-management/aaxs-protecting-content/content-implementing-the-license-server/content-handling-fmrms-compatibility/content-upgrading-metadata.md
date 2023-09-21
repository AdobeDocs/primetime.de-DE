---
title: Aktualisieren von Metadaten
description: Aktualisieren von Metadaten
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Aktualisieren von Metadaten{#upgrading-metadata}

Wenn ein Adobe Access-Client auf Inhalte trifft, die mit Flash Media Rights Management Server 1.x verpackt sind, extrahiert er die Verschlüsselungsmetadaten aus dem Inhalt und sendet sie an den Server. Der Server konvertiert die FMRMS 1.x-Metadaten in das Adobe Access-Format und sendet sie an den Client zurück. Der Client sendet dann die aktualisierten Metadaten in einer standardmäßigen Adobe-Zugriffslizenzanfrage.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL aus 1.x-Inhalt*&quot; +&quot;/flashaccess/headerconversion/v1&quot;.

Die Metadaten-Konvertierung kann sofort durchgeführt werden, wenn der Server die alten Metadaten vom Client erhält. Alternativ kann der Server den alten Inhalt vorab verarbeiten und die konvertierten Metadaten speichern. In diesem Fall muss der Server beim Anfordern neuer Metadaten nur die neuen Metadaten abrufen, die mit der Lizenzkennung der alten Metadaten übereinstimmen.

Um Metadaten zu konvertieren, muss der Server die folgenden Schritte ausführen:

* Get `LiveCycleKeyMetaData`. So konvertieren Sie die Metadaten vorab: `LiveCycleKeyMetaData` kann aus einer 1.x-gepackten Datei mit `MediaEncrypter.examineEncryptedContent()`. Die Metadaten sind auch in der Metadaten-Konvertierungsanforderung enthalten ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).
* Rufen Sie die Lizenzkennung aus den alten Metadaten ab und suchen Sie den Verschlüsselungsschlüssel und die Richtlinien (diese Informationen waren ursprünglich in der Adobe LiveCycle ES-Datenbank enthalten). Die LiveCycle ES-Richtlinien müssen in Adobe Access 2.0-Richtlinien konvertiert werden.) Die Referenzimplementierung enthält Skripte und Beispielcode zum Konvertieren der Richtlinien und Exportieren von Lizenzinformationen aus LiveCycle ES.
* Füllen Sie die `V2KeyParameters` -Objekt (das Sie durch Aufruf von abrufen `MediaEncrypter.getKeyParameters()`).
* Laden Sie die `SigningCredential`: die von Adobe ausgestellte Paketberechtigung zum Signieren von Verschlüsselungsmetadaten. Rufen Sie die `SignatureParameters` Objekt durch Aufruf von `MediaEncrypter.getSignatureParameters()` und geben Sie die Signaturberechtigung ein.
* Aufruf `MetaDataConverter.convertMetadata()` um die `V2ContentMetaData`.
* Aufruf `V2ContentMetaData.getBytes()` und zur zukünftigen Verwendung speichern oder aufrufen `FMRMSv1MetadataHandler.setUpdatedMetadata()`.
