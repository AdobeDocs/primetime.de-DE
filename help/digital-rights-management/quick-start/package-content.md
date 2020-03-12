---
seo-title: Verpacken von verschlüsseltem Inhalt
title: Verpacken von verschlüsseltem Inhalt
uuid: 1e271167-107d-41df-8a7c-3075cb3acc0c
translation-type: tm+mt
source-git-commit: 91cea7acb8127e02b82e5242b9ad6ab0d12ce0eb

---


# Verpacken von verschlüsseltem Inhalt{#package-encrypted-content}

1. Kopieren Sie den `<Primetime DRM DVD>\Reference Implementation\Command Line Tools\` Ordner in Ihr lokales Dateisystem.
1. Aktualisieren Sie die `Command Line Tools\` Datei im lokalen `flashaccesstools.properties` Ordner, damit sie mit Ihrem Server verwendet werden kann.

   Sie müssen mindestens die folgenden Eigenschaften ändern:

   * `encrypt.keys.asymmetric.certfile=[license-server-certificate.cer]`: Der Pfad zum Lizenzserver-Zertifikat (normalerweise endet es mit [!DNL .cer], [!DNL .der] oder [!DNL .pem]).

   * `encrypt.license.serverurl=[license-server-url]`: Ihre Lizenz-Server-URL, z. B.:    `https://<License Server Hostname>:8080/flashaccessserver/sampletenant`.

   * `encrypt.license.servercert=[transport-certificate.cer]`: Der Pfad zu Ihrem Transportzertifikat (normalerweise endet es mit [!DNL .cer], [!DNL .der]oder [!DNL .pem]).

   * `encrypt.sign.certfile=[packager-credentials.pfx]`: Der Pfad zum Packager-Zertifikat (endet mit [!DNL .pfx]).

   * `encrypt.sign.certpass=[password]`: Das Kennwort für Ihr Packager-Zertifikat.
   >[!NOTE]
   >
   >Stellen Sie sicher, dass das Kennwort nicht beschädigt wird.

1. Erstellen Sie eine Richtlinie.

   Führen Sie im lokalen `Command Line Tools\` Ordner den folgenden Befehl aus:

   ```
   java -jar libs/AdobePolicyManager.jar new examplepolicy.pol -n examplepolicy -x
   ```

   Mit diesem Befehl wird eine Richtliniendatei mit dem Namen [!DNL examplepolicy.pol] der anonymen Authentifizierung des Lizenzservers (die `-x` Option) erstellt.
1. Kopieren Sie die MP4-, FLV- oder F4V-Videodatei, die Sie in Ihren lokalen `Command Line Tools\` Ordner verschlüsseln möchten.
1. Verpacken Sie Ihren Inhalt.

   Nehmen wir einmal an, dass Ihre Quellvideodatei [!DNL sample.mp4]ist. Führen Sie im lokalen `Command Line Tools\` Ordner den folgenden Befehl aus:

   ```
   java -jar libs/AdobePackager.jar sample.mp4 sample_encrypted.mp4 -p examplepolicy.pol
   ```

   >[!NOTE]
   >
   >Wenn Sie HLS-, HDS- oder DASH-Inhalte verpacken möchten, müssen Sie ein anderes Packager-Tool verwenden, z. B. [Adobe Primetime Offline Packager](https://helpx.adobe.com/content/dam/help/en/primetime/guides/offline_packager_getting_started.pdf).

1. Kopieren Sie die verschlüsselten Dateiartefakte (in diesem Fall [!DNL sample_encrypted.mp4] und [!DNL sample_encrypted.mp4.metadata]) in `<Your Content Server - Tomcat Install Dir>\webapps\ROOT`.

An dieser Stelle haben Sie die Verpackungsphase des Prozesses abgeschlossen.

>[!NOTE]
>
>Weitere Informationen zu Befehlszeilenwerkzeugen zum Verpacken von Inhalten, Erstellen von Richtlinien und mehr finden Sie unter [Adobe Primetime DRM-Befehlszeilenwerkzeuge](../drm-reference-implementations/command-line-tools/command-line-tools-overview.md).
