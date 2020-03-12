---
seo-title: Migration von FMRMS 1.0 oder 1.5 auf Adobe Access 2.0 und höher
title: Migration von FMRMS 1.0 oder 1.5 auf Adobe Access 2.0 und höher
uuid: 05caeb39-0c62-4053-87a9-8e89030a188d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Migration von FMRMS 1.0 oder 1.5 auf Adobe Access 2.0 und höher {#migrating-from-fmrms-or-to-adobe-access-and-above}

Damit weiterhin Lizenzen für Inhalte ausgegeben werden können, die mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 verpackt wurden, müssen Lizenz- und Richtliniendaten vom LiveCycle ES-Server auf den neuen Server des Kunden migriert werden, der auf dem Adobe Access SDK basiert. Die wichtigsten Schritte sind:

1. Importieren von Lizenzinformationen
1. Konvertieren von FMRMS-Richtlinien in das Adobe Access-Format
1. Unterstützung der 1.x-Kompatibilitätsanfragen über die `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`

Informationen zum Importieren von Lizenzinformationen aus LiveCycle ES in Ihren Adobe Access-basierten Server finden Sie in den Beispieldatenbankskripten im [!DNL Reference Implementation\Server\migration\db] Ordner. Beispielskripte werden zum Exportieren der relevanten Daten aus einer MySQL-, Oracle- oder SQL Server-Datenbank in ein CSV-Dateiformat bereitgestellt. Nachdem die Daten exportiert wurden, können sie in die Datenbank Ihrer Wahl importiert werden. Zu den exportierten Lizenzinformationen gehören die Lizenz-ID, eine Inhalts-ID, die zum Zeitpunkt der Verpackung zugewiesen wurde, die ID der verwendeten Richtlinie, der Zeitpunkt, zu dem der Inhalt verpackt wurde, und der Inhaltsverschlüsselungsschlüssel. Für Adobe Access sind diese Informationen erforderlich, um die Metadaten des 1.x-Inhalts in das Adobe Access-Metadatenformat zu konvertieren (siehe `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`). In der Referenzimplementierung werden diese Daten in der Tabelle der Lizenzdatenbank gespeichert und von `RefImplMetadataConvReqHandler`der Firma verwendet.

Bestehende Richtlinien müssen in das Adobe Access-Format konvertiert werden, um diese Richtlinien beim Konvertieren von Metadaten und der Erteilung von Lizenzen für 1.0- oder 1.5-Inhalte verwenden zu können. Die Referenz Implementation\Server\migration folder contains sample code for creating an Adobe Access policy based on older policies.

Wenn Sie von FMRMS 1.0 auf Adobe Access migrieren, finden Sie weitere Informationen im Beispiel V1_0PolicyConverter.java. Kompilieren Sie den Beispielcode, indem Sie &quot; `ant-f build-migration.xml build-1.0-converter`&quot;ausführen (das Skript erwartet, dass die Bibliotheken 1.0 und Adobe Access sich jeweils in libs/flashaccess befinden [!DNL libs/1.0] ). Bearbeiten Sie die Datei &quot;converter.properties&quot;, um auf Ihren LiveCycle ES-Server zu verweisen. Führen Sie dann &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot;aus, um alle FMRMS 1.0-Richtlinien in das Adobe Access-Format zu konvertieren.

Wenn Sie von FMRMS 1.5 auf Adobe Access migrieren, finden Sie weitere Informationen im Beispiel V1_5PolicyConverter.java. Kompilieren Sie den Beispielcode mit &quot; `ant-f build-migration.xml build-1.5-converter`&quot; (das Skript erwartet, dass die Bibliotheken 1.5 und 3.0 in libs/1.5 bzw. libs/flashaccess enthalten sind). Bearbeiten Sie die Datei &quot;converter.properties&quot;, um auf Ihren LiveCycle ES-Server zu verweisen. Führen Sie dann &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot;aus, um alle FMRMS 1.5-Richtlinien in das Adobe Access-Format zu konvertieren.

Die konvertierten Richtlinien werden in eine Reihe von Dateien geschrieben. Darüber hinaus gibt PolicyConverter eine CSV-Datei aus, die die Zuordnung alter Richtlinien-IDs zu neuen Richtlinien-IDs enthält. Diese Datei kann in die Tabelle &quot;PolicyConversion&quot;in der Referenz-Implementierungsdatenbank importiert werden und wird von `RefImplMetadataConvReqHandler`dieser verwendet.

Sobald die relevanten Daten auf Ihren Adobe Access-basierten Server migriert wurden, können Sie Unterstützung für 1.x-Kompatibilitätsanfragen implementieren. Beispiele für die Verarbeitung dieser Anforderungstypen finden Sie unter `RefImplUpgradeV1ClientHandler` und `RefImplMetadataConvReqHandler` in der Referenz-Implementierung.
