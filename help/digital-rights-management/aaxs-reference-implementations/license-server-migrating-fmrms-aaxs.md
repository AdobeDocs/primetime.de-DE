---
title: Migration von FMRMS 1.0 oder 1.5 zu Adobe Access 2.0 und höher
description: Migration von FMRMS 1.0 oder 1.5 zu Adobe Access 2.0 und höher
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Migration von FMRMS 1.0 oder 1.5 zu Adobe Access 2.0 und höher {#migrating-from-fmrms-or-to-adobe-access-and-above}

Um weiterhin Lizenzen für mit Flash Media Rights Management Server (FMRMS) 1.0 oder 1.5 verpackte Inhalte zu erteilen, müssen Lizenz- und Richtliniendaten basierend auf dem Adobe Access SDK vom LiveCycle ES-Server auf den neuen Server des Kunden migriert werden. Die wichtigsten Schritte sind:

1. Lizenzinformationen importieren
1. Konvertieren von FMRMS-Richtlinien in das Adobe Access-Format
1. Unterstützen der 1.x-Kompatibilitätsanfragen über die `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`

Informationen zum Importieren von Lizenzinformationen von LiveCycle ES in Ihren Adobe Access-basierten Server finden Sie in den Beispieldatenbankskripten, die im Abschnitt [!DNL Reference Implementation\Server\migration\db] Ordner. Beispielskripte werden zum Exportieren der relevanten Daten aus einer MySQL-, Oracle- oder SQL Server-Datenbank in ein CSV-Dateiformat bereitgestellt. Nach dem Export können die Daten in die Datenbank Ihrer Wahl importiert werden. Die exportierten Lizenzinformationen enthalten die Lizenzkennung, eine Inhalts-ID, die zum Zeitpunkt der Verpackung zugewiesen wird, die Kennung der verwendeten Richtlinie, den Zeitpunkt der Inhaltspaketung und den Schlüssel zur Inhaltsverschlüsselung. Für den Adobe-Zugriff sind diese Informationen erforderlich, um die 1.x-Inhaltsmetadaten in das Metadatenformat Adobe-Zugriff zu konvertieren (siehe `FMRMSv1RequestHandler` und `FMRMSv1MetadataHandler`). In der Referenzimplementierung werden diese Daten in der Tabelle der Lizenzdatenbank gespeichert und von `RefImplMetadataConvReqHandler`.

Bestehende Richtlinien müssen in das Adobe Access-Format konvertiert werden, um diese Richtlinien bei der Konvertierung von Metadaten und der Erteilung von Lizenzen für 1.0- oder 1.5-Inhalte verwenden zu können. Der Ordner Referenzimplementierung\Server\Migration enthält Beispielcode zum Erstellen einer Adobe-Zugriffsrichtlinie basierend auf älteren Richtlinien.

Wenn Sie von FMRMS 1.0 auf Adobe Access migrieren, finden Sie weitere Informationen im Beispiel V1_0PolicyConverter.java . Kompilieren Sie den Beispielcode, indem Sie &quot; `ant-f build-migration.xml build-1.0-converter`&quot;(Das Skript erwartet, dass sich die 1.0- und Adobe Access-Bibliotheken in [!DNL libs/1.0] und libs/flashaccess). Bearbeiten Sie die Datei &quot;Converter.properties&quot;, um auf Ihren LiveCycle ES-Server zu verweisen. Führen Sie dann &quot; `ant -f build-migration.xml migrate-all-1.0-policies`&quot;, um alle FMRMS 1.0-Richtlinien in das Adobe Access-Format zu konvertieren.

Wenn Sie von FMRMS 1.5 auf Adobe Access migrieren, finden Sie weitere Informationen im Beispiel V1_5PolicyConverter.java . Kompilieren Sie den Beispielcode, indem Sie &quot; `ant-f build-migration.xml build-1.5-converter`&quot;(Das Skript erwartet, dass sich die Bibliotheken 1.5 und 3.0 in libs/1.5 bzw. libs/flashaccess befinden). Bearbeiten Sie die Datei &quot;Converter.properties&quot;, um auf Ihren LiveCycle ES-Server zu verweisen. Führen Sie dann &quot; `ant -f build-migration.xml migrate-all-1.5-policies`&quot;, um alle FMRMS 1.5-Richtlinien in das Adobe Access-Format zu konvertieren.

Die konvertierten Richtlinien werden in eine Reihe von Dateien geschrieben. Darüber hinaus gibt PolicyConverter eine CSV-Datei aus, die die Zuordnung alter Richtlinien-IDs zu neuen Richtlinien-IDs enthält. Diese Datei kann in die Tabelle &quot;PolicyConversion&quot;in der Referenzimplementierungsdatenbank importiert werden und wird von `RefImplMetadataConvReqHandler`.

Sobald die entsprechenden Daten auf Ihren Adobe Access-basierten Server migriert wurden, können Sie die Unterstützung für 1.x-Kompatibilitätsanfragen implementieren. Siehe `RefImplUpgradeV1ClientHandler` und `RefImplMetadataConvReqHandler` in der Referenzimplementierung für Beispiele zur Verarbeitung dieser Anforderungstypen.
