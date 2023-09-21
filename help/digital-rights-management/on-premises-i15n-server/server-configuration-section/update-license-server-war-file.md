---
title: Aktualisieren der Lizenzserver-WAR-Datei
description: Aktualisieren der Lizenzserver-WAR-Datei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Aktualisieren der Lizenzserver-WAR-Datei{#update-the-license-server-war-file}

Um Clients zu unterstützen, die über einen On-Premises-Individualisierungsserver individualisiert wurden, müssen Sie den Zertifikatsstamm des Lizenzservers aktualisieren, um die neu erworbene Berechtigung für Individualization CA aufzunehmen. Ein Python-Skript ( [!DNL addIndivCert.py]) ist in der [!DNL update_license_server] Ordner.

Führen Sie folgende Schritte aus, um den Lizenzserver zu aktualisieren:

1. Erstellen Sie eine Kopie der zu aktualisierenden WAR-Dateien (Beispiele: [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Stellen Sie sicher, dass die WAR-Dateien entsperrt sind und ihre Berechtigungen festgelegt sind, damit sie geändert werden können.
1. Führen Sie die [!DNL addIndivCert.py] Python-Skript zum Aktualisieren der Lizenzserver-WAR-Dateien.

   Die Eingaben für das Skript lauten wie folgt:

   * `cert`: PKCS12-Datei, die das Zertifikat der Zertifizierungsstelle für Individualisierungen enthält
   * `war`: Zu aktualisierende WAR-Datei

   Die Ausgabedatei ist eine aktualisierte WAR-Datei.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

Die WAR-Dateien werden geändert. Bei Bedarf können Sie das Python-Skript entsprechend Ihren Anforderungen bearbeiten. Nachdem Sie die Aktualisierungen durchgeführt haben, können Sie die WAR-Dateien normal bereitstellen.
