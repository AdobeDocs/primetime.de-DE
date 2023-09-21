---
title: Verschlüsselte Inhalte verpacken
description: Verschlüsselte Inhalte verpacken
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Verschlüsselte Inhalte verpacken{#package-encrypted-content}

1. Kopieren Sie die `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` in Ihr lokales Dateisystem.
1. In Ihrer lokalen `Command Line Tools\` Ordner, aktualisieren Sie die `flashaccesstools.properties` -Datei, um mit Ihrem Server zu arbeiten.

   Sie müssen mindestens die folgenden Eigenschaften ändern:

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Der Pfad zu Ihrem Lizenzserver-Zertifikat (normalerweise endet er mit [!DNL .cer], [!DNL .der] oder [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: Ihre Lizenzserver-URL, z. B.:    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: Der Pfad zu Ihrem Transportzertifikat (normalerweise endet er mit [!DNL .cer], [!DNL .der]oder [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Der Pfad zu Ihrem Packager-Zertifikat (dieser endet mit [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: Das Kennwort für Ihr Packager-Zertifikat.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie das Kennwort nicht verschlüsseln.

1. Erstellen Sie eine Richtlinie.

   In Ihrer lokalen `Command Line Tools\` Ordner, führen Sie den folgenden Befehl aus:

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Dieser Befehl erstellt eine Richtliniendatei mit dem Namen [!DNL examplepolicy.pol] die anonyme Authentifizierung des Lizenzservers verwendet (die `-x` -Option).
1. Kopieren Sie die MP4-, FLV- oder F4V-Videodatei, die Sie verschlüsseln möchten, in Ihre lokale `Command Line Tools\` Ordner.
1. Verpacken Sie den Inhalt.

   Angenommen, Ihre Quellvideodatei lautet [!DNL sample.mp4]. In Ihrer lokalen `Command Line Tools\` Ordner, führen Sie den folgenden Befehl aus:

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Wenn Sie HLS-, HDS- oder DASH-Inhalte verpacken möchten, müssen Sie ein anderes Pakettool verwenden, z. B. [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Kopieren Sie die verschlüsselten Dateiartefakte (in diesem Fall [!DNL sample_encrypted.mp4] und [!DNL sample_encrypted.mp4.metadata]) zu `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

An dieser Stelle haben Sie die Verpackungsphase des Prozesses abgeschlossen.

>[!NOTE]
>
>Weitere Informationen zu Befehlszeilen-Tools zum Verpacken von Inhalten, Erstellen von Richtlinien und mehr finden Sie unter [Adobe Primetime DRM-Befehlszeilenwerkzeuge](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
