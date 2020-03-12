---
seo-title: WAR-Datei des Lizenzservers aktualisieren
title: WAR-Datei des Lizenzservers aktualisieren
uuid: 0cde53d6-185d-4bf2-84fc-0c31d17904a8
translation-type: tm+mt
source-git-commit: 1547eb3dd220fafc08df923f40504736c16a866c

---


# WAR-Datei des Lizenzservers aktualisieren{#update-the-license-server-war-file}

Um Clients zu unterstützen, die über einen On Premises Individualization Server individualisiert wurden, müssen Sie den Zertifikatsstamm des Lizenzservers aktualisieren, um die neu erworbene CA-Berechtigung für die Individualisierung einzuschließen. Ein Python-Skript ( [!DNL addIndivCert.py]) ist im [!DNL update_license_server] Ordner enthalten.

Führen Sie die folgenden Schritte aus, um den Lizenzserver zu aktualisieren:

1. Erstellen Sie eine Kopie der zu aktualisierenden WAR-Dateien (Beispiele: [!DNL flashaccess.war], [!DNL faxsks.war]).
1. Stellen Sie sicher, dass die WAR-Dateien entsperrt sind und ihre Berechtigungen festgelegt sind, damit sie geändert werden können.
1. Führen Sie das [!DNL addIndivCert.py] Python-Skript aus, um die WAR-Dateien des Lizenzservers zu aktualisieren.

   Die Eingaben für das Skript lauten wie folgt:

   * `cert`: PKCS12-Datei, die das CA-Zertifikat für die Individualisierung enthält
   * `war`: Zu aktualisierende WAR-Datei
   Die Ausgabedatei ist eine aktualisierte WAR-Datei.

   ```
   ./addIndivCert.py -cert NEW_IndivCA.cer -war flashaccess.war
   ```

Die WAR-Dateien werden geändert. Sie können das Python-Skript bei Bedarf bearbeiten. Nachdem Sie die Aktualisierungen durchgeführt haben, können Sie die WAR-Dateien normal bereitstellen.
