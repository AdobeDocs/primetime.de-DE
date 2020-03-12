---
seo-title: Aktualisieren von Metadaten
title: Aktualisieren von Metadaten
uuid: 769483e6-a2d1-46cb-afcf-557aa807037c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Aktualisieren von Metadaten{#upgrading-metadata}

Wenn ein Adobe Primetime-DRM-Client auf Inhalte stößt, die mit Flash Media Rights Management Server 1.x verpackt wurden, extrahiert er die Verschlüsselungsmetadaten aus dem Inhalt und sendet sie an den Server. Der Server konvertiert dann die FMRMS 1.x-Metadaten in das Primetime-DRM-Format und sendet sie an den Client. Der Client sendet dann die aktualisierten Metadaten in einer standardmäßigen Primetime DRM-Lizenzanforderung.

* Die Anforderungs-Handler-Klasse ist `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1MetadataHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL von 1.x-Inhalt*&quot; +&quot; [!DNL /flashaccess/headerconversion/v1].

Die Metadaten-Konvertierung kann sofort erfolgen, wenn der Server die alten Metadaten vom Client erhält. Alternativ kann der Server den alten Inhalt vorverarbeiten und die konvertierten Metadaten speichern; In diesem Fall muss der Server, wenn der Client neue Metadaten anfordert, die neuen Metadaten abrufen, die mit der Lizenzkennung der alten Metadaten übereinstimmen.

Zum Konvertieren von Metadaten muss der Server die folgenden Schritte ausführen:

* Geh `LiveCycleKeyMetaData`. Um die Metadaten vorab zu konvertieren, können Sie `LiveCycleKeyMetaData` sie aus einer 1.x-gepackten Datei mit `MediaEncrypter.examineEncryptedContent()`abrufen. Die Metadaten sind auch in der Metadaten-Konvertierungsanforderung enthalten ( `FMRMSv1MetadataHandler.getOriginalMetadata()`).

* Rufen Sie die Lizenzkennung aus den alten Metadaten ab und suchen Sie nach den Verschlüsselungsschlüssel- und DRM-Richtlinien (diese Informationen waren ursprünglich in der Adobe LiveCycle ES-Datenbank enthalten). Die LiveCycle ES DRM-Richtlinien müssen in DRM 2.0-DRM-Richtlinien von Primetime konvertiert werden.) Die Referenzimplementierung enthält Skripten und Beispielcode zum Konvertieren der DRM-Richtlinien und Exportieren von Lizenzinformationen aus LiveCycle ES.
* Füllen Sie das `V2KeyParameters` Objekt aus (das Sie durch Aufruf abrufen `MediaEncrypter.getKeyParameters()`).

* Laden Sie die Datei `SigningCredential`, bei der es sich um die von Adobe ausgestellte Paketberechtigung handelt, mit der Verschlüsselungsmetadaten signiert werden. Rufen Sie das `SignatureParameters` Objekt ab, indem Sie die Unterschriftsberechtigung aufrufen `MediaEncrypter.getSignatureParameters()` und ausfüllen.

* Rufen Sie `MetaDataConverter.convertMetadata()` an, um die `V2ContentMetaData`.

* Rufen Sie `V2ContentMetaData.getBytes()` und speichern Sie für die zukünftige Verwendung oder rufen Sie an `FMRMSv1MetadataHandler.setUpdatedMetadata()`.

