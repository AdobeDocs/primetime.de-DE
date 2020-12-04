---
description: Um weiterhin Lizenzen für Inhalte auszustellen, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 gepackt wurden, müssen Sie Lizenz- und DRM-Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migrieren, der auf dem Adobe Primetime DRM SDK basiert.
seo-description: Um weiterhin Lizenzen für Inhalte auszustellen, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 gepackt wurden, müssen Sie Lizenz- und DRM-Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migrieren, der auf dem Adobe Primetime DRM SDK basiert.
seo-title: Migrieren von FMRMS 1.0 oder 1.5 zu Adobe Primetime DRM 2.0 oder höher
title: Migrieren von FMRMS 1.0 oder 1.5 zu Adobe Primetime DRM 2.0 oder höher
uuid: 49ecbbd2-d83b-4bf2-841e-c3f9e5d5e141
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---


# Migrieren von FMRMS 1.0 oder 1.5 zu Adobe Primetime DRM 2.0 oder höher{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Um weiterhin Lizenzen für Inhalte auszustellen, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 gepackt wurden, müssen Sie Lizenz- und DRM-Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migrieren, der auf dem Adobe Primetime DRM SDK basiert.

Führen Sie zum Migrieren die folgenden Aufgaben aus:

1. Einfuhrlizenzinformationen:

   1. Informationen zum Importieren von Lizenzinformationen aus LiveCycle ES in Ihren Primetime DRM-basierten Server finden Sie in den Beispieldatenbankskripten im Ordner [!DNL Reference Implementation\Server\migration\db].
   1. Führen Sie die Beispielskripten aus, um relevante Daten aus einer MySQL-, Oracle- oder SQL Server-Datenbank in ein CSV-Dateiformat zu exportieren.
   1. Importieren Sie die Daten nach dem Exportieren der Daten aus LiveCycle ES in Ihre Datenbank.

      Die Informationen zur exportierten Lizenz umfassen Folgendes:

      * Eine Lizenz-ID
      * Eine Inhalts-ID, die zum Zeitpunkt der Verpackung zugewiesen wird
      * Die ID der DRM-Richtlinie, die angewendet wird
      * Der Zeitpunkt, zu dem der Inhalt verpackt wurde
      * Der Schlüssel zur Inhaltsverschlüsselung

      Diese Informationen sind erforderlich, bevor Sie die Metadaten des 1.x-Inhalts in das Primetime-DRM-Metadatenformat konvertieren können. In der Referenzimplementierung werden diese Daten in der Tabelle der Lizenzdatenbank gespeichert und von `RefImplMetadataConvReqHandler` verwendet. Weitere Informationen finden Sie unter `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`.


1. Konvertieren von FMRMS-Richtlinien in das Primetime-DRM-Format:

   1. Bevor Sie die DRM-Richtlinien anwenden können, um Metadaten zu konvertieren und Lizenzen für Inhalte der Version 1.0 oder 1.5 auszustellen, konvertieren Sie die vorhandenen DRM-Richtlinien in das Primetime-DRM-Format.

      Der Ordner `Reference Implementation\Server\migration` enthält Beispielcode zum Erstellen einer Primetime-DRM-Richtlinie, die auf älteren DRM-Richtlinien basiert. Informationen zum Migrieren von FMRMS 1.0 zu Primetime DRM finden Sie im Beispiel `V1_0PolicyConverter.java`.
   1. Kompilieren Sie den Beispielcode mit dem Skript `ant-f build-migration.xml build-1.0-converter`, das nach den Bibliotheken 1.0 und Primetime DRM in den Ordnern [!DNL libs/1.0] und [!DNL libs/flashaccess] sucht.

   1. Bearbeiten Sie die Datei [!DNL converter.properties], um auf Ihren LiveCycle ES-Server zu verweisen.
   1. Führen Sie `ant -f build-migration.xml migrate-all-1.0-policies` aus, um alle DRM-Richtlinien von FMRMS 1.0 in das Primetime-DRM-Format zu konvertieren.

      Informationen zum Migrieren von FMRMS 1.5 zu Primetime DRM finden Sie im Beispiel `V1_5PolicyConverter.java`.

   1. Kompilieren Sie den Beispielcode, indem Sie das Skript `ant-f build-migration.xml build-1.5-converter` ausführen, das erwartet, dass sich die Bibliotheken 1.5 und 3.0 in den Ordnern [!DNL libs/1.5] und [!DNL libs/flashaccess] befinden.

   1. Bearbeiten Sie die Datei [!DNL converter.properties], um auf Ihren LiveCycle ES-Server zu verweisen.
   1. Führen Sie `ant -f build-migration.xml migrate-all-1.5-policies` aus, um alle DRM-Richtlinien von FMRMS 1.5 in das Primetime-DRM-Format zu konvertieren.

      Die konvertierten DRM-Richtlinien werden als Dateisatz gespeichert. Das `DRM PolicyConverter` generiert eine CSV-formatierte Datei, die die Zuordnung der alten DRM-Richtlinien-IDs zu den neuen DRM-Richtlinien-IDs enthält. Sie können diese Datei in die Tabelle [!DNL PolicyConversion] in der Referenz-Implementierungsdatenbank importieren, in der sie von `RefImplMetadataConvReqHandler` verwendet wird.

1. Unterstützen Sie die 1.x-Kompatibilitätsanfragen mit den Eigenschaften `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`:

   1. Nachdem die relevanten Daten auf einen Primetime DRM-basierten Server migriert wurden, implementieren Sie Unterstützung für 1.x-Kompatibilitätsanfragen.

      Beispiele zur Verarbeitung dieser Anforderungstypen finden Sie unter `RefImplUpgradeV1ClientHandler` und `RefImplMetadataConvReqHandler` in der Referenz-Implementierung.

