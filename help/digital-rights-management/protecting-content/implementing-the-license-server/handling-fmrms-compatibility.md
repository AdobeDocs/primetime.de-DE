---
description: Umgang mit FMRMS-Kompatibilität
title: Aktualisieren von Clients
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Umgang mit FMRMS-Kompatibilität {#handling-fmrms-compatibility}

Es gibt zwei Arten von Anfragen im Zusammenhang mit der Flash Media Rights Management Server 1.x-Kompatibilität. Eine Art von Anfrage wird verwendet, um 1.x-Clients aufzufordern, auf eine Laufzeitumgebung zu aktualisieren, die Adobe Primetime DRM 2.0 oder höher unterstützt. Ein anderer wird verwendet, um 1.x-Metadaten auf das Primetime-DRM-Format zu aktualisieren, bevor eine Lizenz angefordert werden kann. Unterstützung für diese Anfragen ist nur erforderlich, wenn Sie zuvor Inhalte bereitgestellt haben, die FMRMS 1.0 oder 1.5 verwenden.

## Aktualisieren von Clients {#upgrading-clients}

Wenn ein FMRMS 1.x-Client einen Adobe Primetime DRM-Server kontaktiert, muss der Server den Client zur Aktualisierung auffordern.

* Die Anfrage-Handler-Klasse lautet `com.adobe.flashaccess.sdk.protocol.compatibility.FMRMSv1RequestHandler`.
* Die Anforderungs-URL lautet &quot;*Basis-URL aus 1.x-Inhalt*&quot; + &quot; [!DNL /edcws/services/urn:EDCLicenseService]&quot;

  Im Gegensatz zu anderen Adobe Primetime-Anfrage-Handlern bietet dieser Handler keinen Zugriff auf Anfrageinformationen oder erfordert die Festlegung von Antwortdaten. Erstellen Sie eine Instanz der `FMRMSv1RequestHandler`, und rufen Sie dann `close()`

## Aktualisieren von Metadaten {#upgrading-metadata}

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
