---
description: Um weiterhin Lizenzen für Inhalte auszustellen, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 gepackt wurden, müssen Sie Lizenz- und DRM-Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migrieren, der auf dem Adobe Primetime DRM SDK basiert.
title: Migration von FMRMS 1.0 oder 1.5 zu Adobe Primetime DRM 2.0 oder höher
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Migration von FMRMS 1.0 oder 1.5 zu Adobe Primetime DRM 2.0 oder höher{#migrate-from-fmrms-or-to-adobe-primetime-drm-or-later}

Um weiterhin Lizenzen für Inhalte auszustellen, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 gepackt wurden, müssen Sie Lizenz- und DRM-Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migrieren, der auf dem Adobe Primetime DRM SDK basiert.

Führen Sie zum Migrieren die folgenden Aufgaben aus:

1. Einfuhrlizenzinformationen:

   1. Informationen zum Importieren von Lizenzinformationen von LiveCycle ES in Ihren Primetime DRM-basierten Server finden Sie in den Beispieldatenbankskripten im Abschnitt [!DNL Reference Implementation\Server\migration\db] Ordner.
   1. Führen Sie die Beispielskripte aus, um relevante Daten aus einer MySQL-, Oracle- oder SQL Server-Datenbank in ein CSV-Dateiformat zu exportieren.
   1. Importieren Sie die Daten nach dem Export der Daten aus LiveCycle ES in Ihre Datenbank.

      Die exportierten Lizenzinformationen umfassen Folgendes:

      * Lizenz-ID
      * Eine Inhalts-ID, die zur Paketierungszeit zugewiesen wird
      * Die Kennung der angewandten DRM-Richtlinie
      * Der Zeitpunkt, zu dem der Inhalt gepackt wurde
      * Der Schlüssel zur Inhaltsverschlüsselung

      Diese Informationen sind erforderlich, bevor Sie die 1.x-Inhaltsmetadaten in das Primetime-DRM-Metadatenformat konvertieren können. In der Referenzimplementierung werden diese Daten in der Tabelle der Lizenzdatenbank gespeichert und von `RefImplMetadataConvReqHandler`. Weitere Informationen finden Sie unter `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`.

1. Konvertieren Sie FMRMS-Richtlinien in das Primetime-DRM-Format:

   1. Bevor Sie die DRM-Richtlinien anwenden können, um Metadaten zu konvertieren und Lizenzen für Inhalte der Version 1.0 oder 1.5 auszustellen, konvertieren Sie die vorhandenen DRM-Richtlinien in das Primetime-DRM-Format.

      Die `Reference Implementation\Server\migration` enthält Beispielcode zum Erstellen einer Primetime-DRM-Richtlinie, die auf älteren DRM-Richtlinien basiert. Informationen zum Migrieren von FMRMS 1.0 zu Primetime DRM finden Sie in der `V1_0PolicyConverter.java` Beispiel.
   1. Kompilieren des Beispielcodes durch Ausführen `ant-f build-migration.xml build-1.0-converter` -Skript, das nach den DRM-Bibliotheken 1.0 und Primetime in der [!DNL libs/1.0] und [!DNL libs/flashaccess] Verzeichnissen.

   1. Bearbeiten Sie die [!DNL converter.properties] -Datei auf Ihren LiveCycle ES-Server verweisen.
   1. Ausführen `ant -f build-migration.xml migrate-all-1.0-policies` zur Konvertierung aller DRM-Richtlinien von FMRMS 1.0 in das Primetime-DRM-Format.

      Informationen zur Migration von FMRMS 1.5 zu Primetime DRM finden Sie in der `V1_5PolicyConverter.java` Beispiel.

   1. Kompilieren des Beispielcodes durch Ausführen `ant-f build-migration.xml build-1.5-converter` -Skript, das erwartet, dass sich die 1.5- und 3.0-Bibliotheken in der [!DNL libs/1.5] und [!DNL libs/flashaccess] Verzeichnissen.

   1. Bearbeiten Sie die [!DNL converter.properties] -Datei auf Ihren LiveCycle ES-Server verweisen.
   1. Ausführen `ant -f build-migration.xml migrate-all-1.5-policies` zur Konvertierung aller DRM-Richtlinien von FMRMS 1.5 in das Primetime-DRM-Format.

      Die konvertierten DRM-Richtlinien werden als Dateisatz gespeichert. Die `DRM PolicyConverter` generiert eine CSV-formatierte Datei, die die Zuordnung der alten DRM-Richtlinien-IDs zu den neuen DRM-Richtlinien-IDs enthält. Sie können diese Datei in die [!DNL PolicyConversion] in der Referenzimplementierungsdatenbank, wo sie von `RefImplMetadataConvReqHandler`.

1. Unterstützen Sie 1.x-Kompatibilitätsanfragen mit der `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler` properties:

   1. Nachdem die relevanten Daten auf einen Primetime-DRM-basierten Server migriert wurden, implementieren Sie die Unterstützung für 1.x-Kompatibilitätsanfragen.

      Beispiele zur Verarbeitung dieser Anforderungstypen finden Sie unter `RefImplUpgradeV1ClientHandler` und `RefImplMetadataConvReqHandler` in der Referenzimplementierung.
