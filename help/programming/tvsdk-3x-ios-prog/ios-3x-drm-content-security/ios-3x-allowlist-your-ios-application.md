---
description: Sie können Ihre iOS-Apps mit dem Werkzeugwerkzeug der Adobe Zulassungslisten durchführen.
seo-description: Sie können Ihre iOS-Apps mit dem Werkzeugwerkzeug der Adobe Zulassungslisten durchführen.
seo-title: Zulassungsliste der iOS-Anwendung
title: Zulassungsliste der iOS-Anwendung
uuid: bc558f5f-d4e6-4c1c-81eb-f8bd61c63016
translation-type: tm+mt
source-git-commit: eb9f0a2f6d2118b953c711dfdc0402d1d923b016
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---


# Zulassungsliste der iOS-Anwendung {#allowlist-your-ios-application}

Sie können Ihre iOS-Apps mit dem Werkzeugwerkzeug der Adobe Zulassungslisten durchführen.

Im Allgemeinen können Sie beim Abschluss einer TVSDK-Anwendung Adobe Primetime DRM-Befehlszeilenwerkzeuge verwenden, um Ihre App Zulassungsliste.

>[!TIP]
>
>Sie können diese Werkzeuge auch verwenden, um DRM-Richtlinien zu erstellen und Inhalte zu verschlüsseln.

Durch Zulassen der App-Auflistung wird sichergestellt, dass geschützter Inhalt nur im Videoplayer wiedergegeben werden kann. Wenn Sie jedoch zulassen, dass eine iOS-Anwendung aufgelistet wird, müssen Sie ein spezielles Verfahren durchführen, das mit den Richtlinien für die Antragseinsendung von Apple funktioniert.

Bevor Sie eine iOS-App senden, müssen Sie sie signieren und bei Apple veröffentlichen.

>[!NOTE]
>
>Apple schneidet die Signatur Ihres Entwicklers ab und signiert die Anwendung erneut mit einem eigenen Zertifikat.

Aufgrund der erneuten Unterzeichnung sind die Listen zulassen-Informationen, die Sie vor der Übermittlung an den Apple App Store erstellt haben, nicht verwendbar.

Um mit dieser Übermittlungsrichtlinie zu arbeiten, hat Adobe ein `machotools`-Tool erstellt, das Ihre iOS-Anwendung per Fingerabdruck abdruckt, um einen Digest-Wert zu erstellen, diesen Wert zu signieren und diesen Wert in Ihre iOS-Anwendung einzufügen. Nach dem Fingerabdruck Ihrer iOS-App können Sie die App an den Apple App Store übermitteln. Wenn ein Benutzer Ihre App aus dem App Store ausführt, berechnet Primetime DRM zur Laufzeit den Fingerabdruck der Anwendung und bestätigt ihn mit dem Digest-Wert, der zuvor in die Anwendung injiziert wurde. Wenn der Fingerabdruck übereinstimmt, wird bestätigt, dass die App als aufgelistet zulässig gilt und geschützte Inhalte wiedergegeben werden dürfen.

Die Adobe `machotools` ist im iOS TVSDK SDK enthalten, in der [!DNL [...]/tools/DRM]-Ordner.

So verwenden Sie `machotools`:

1. Generieren Sie ein Schlüsselpaar.

   Um ein Dienstprogramm wie OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Geben Sie bei Aufforderung ein Kennwort zum Schutz des privaten Schlüssels ein.

   Kennwörter sollten mindestens 12 Zeichen enthalten, und die Zeichen sollten eine Mischung aus Groß- und Kleinbuchstaben-ASCII-Zeichen und -Zahlen enthalten.
1. Um mit OpenSSL ein sicheres Kennwort zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl rand -base64 8
   ```

1. Erstellen einer Zertifikatsignaturanforderung (CSR).

   Um mit OpenSSL eine CSR zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Unterschreiben Sie das Zertifikat selbst und geben Sie eine beliebige Dauer ein.

   Im folgenden Beispiel wird ein Ablauf von 20 Jahren angegeben:

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Konvertieren Sie das selbst signierte Zertifikat in eine PKCS#12-Datei:

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   Sie können das selbst signierte Zertifikat verwenden, um Ihre iOS-App zu signieren.

1. Aktualisieren Sie den Speicherort der PFX-Datei und des Kennworts.
1. Bevor Sie Ihre Anwendung in Xcode erstellen, gehen Sie zu **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** und fügen Sie dem Ausführungsskript den folgenden Befehl hinzu:

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Führen Sie [!DNL machotools] aus, um den Hashwert für die App-Herausgeber-ID zu generieren.

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Erstellen Sie eine neue DRM-Richtlinie oder aktualisieren Sie Ihre vorhandene Richtlinie, um den zurückgegebenen Hashwert für die Herausgeber-ID einzuschließen.
1. Erstellen Sie mithilfe von [!DNL AdobePolicyManager.jar] eine neue DRM-Richtlinie (aktualisieren Sie Ihre vorhandene Richtlinie), um den zurückgegebenen Hash-Wert für die Herausgeber-ID, eine optionale App-ID sowie die Attribute für die min- und max. Version in die enthaltene Datei einzuschließen.[!DNL flashaccess-tools.properties]

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. Verpacken Sie den Inhalt mit der neuen DRM-Richtlinie und bestätigen Sie die Wiedergabe des Inhalts, der in der iOS-App zugelassen ist.
