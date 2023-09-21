---
description: Sie können Apps mit Ihrem Tool für iOS-Tools mit Adobe-Tools Zulassungsliste haben.
title: Zulassungsliste Ihrer iOS-Anwendung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Zulassungsliste Ihrer iOS-Anwendung {#allowlist-your-ios-application}

Sie können Apps mit Ihrem Tool für iOS-Tools mit Adobe-Tools Zulassungsliste haben.

Wenn Sie eine TVSDK-Anwendung abschließen, können Sie die Adobe Primetime DRM-Befehlszeilenwerkzeuge verwenden, um Ihre App Zulassungsliste.

>[!TIP]
>
>Sie können diese Tools auch verwenden, um DRM-Richtlinien zu erstellen und Inhalte zu verschlüsseln.

Mit der Zulassungsauflistung Ihrer App wird sichergestellt, dass geschützte Inhalte nur in Ihrem Videoplayer wiedergegeben werden können. Für die Zulassungsauflistung einer iOS-Anwendung müssen Sie jedoch ein besonderes Verfahren durchführen, das mit den Übermittlungsrichtlinien der Apple-Anwendung funktioniert.

Bevor Sie eine iOS-App senden, müssen Sie sie signieren und in Apple veröffentlichen.

>[!NOTE]
>
>Apple entfernt die Unterschrift Ihres Entwicklers und signiert die Anwendung mit einem eigenen Zertifikat erneut.

Aufgrund der erneuten Unterzeichnung können die Informationen zur Zulassungsauflistung, die Sie vor der Übermittlung an Apple App Store generiert haben, nicht verwendet werden.

Um mit dieser Übermittlungsrichtlinie zu arbeiten, hat Adobe eine `machotools` -Tool, mit dem Sie Ihre iOS-Anwendung abrufen und einen Digest-Wert erstellen, diesen Wert signieren und diesen Wert in Ihre iOS-Anwendung einfügen können. Nachdem Sie Ihre iOS-App per Fingerabdruck abgedruckt haben, können Sie die App an die Apple App Store senden. Wenn ein Benutzer Ihre App über App Store ausführt, führt Primetime DRM eine Laufzeitberechnung des Anwendungsfingerabdrucks durch und bestätigt sie mit dem Digest-Wert, der zuvor in die Anwendung eingefügt wurde. Wenn der Fingerabdruck übereinstimmt, wird bestätigt, dass die App auf die Zulassungsliste gesetzt ist und geschützter Inhalt wiedergegeben werden darf.

Die Adobe `machotools` ist im iOS TVSDK SDK in der [!DNL] enthalten [...]Ordner &quot;/tools/DRM&quot;.

Verwendung `machotools`:

1. Generieren Sie ein Schlüsselpaar.

   Um ein Dienstprogramm wie OpenSSL zu verwenden, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl genrsa -des3 -out selfsigncert-ios.key 1024
   ```

1. Geben Sie bei Aufforderung ein Kennwort zum Schutz des privaten Schlüssels ein.

   Passwörter sollten mindestens 12 Zeichen enthalten und die Zeichen sollten eine Mischung aus Groß- und Kleinbuchstaben ASCII-Zeichen und -Zahlen enthalten.
1. Um mithilfe von OpenSSL ein sicheres Kennwort zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl rand -base64 8
   ```

1. Generieren Sie eine Certificate Signing Request (CSR).

   Um mithilfe von OpenSSL eine CSR zu generieren, öffnen Sie ein Befehlsfenster und geben Sie Folgendes ein:

   ```shell
   openssl req -new -key selfsigncert-ios.key -out selfsigncert-ios.csr -batch
   ```

1. Unterschreiben Sie das Zertifikat selbst und geben Sie eine beliebige Dauer ein.

   Im folgenden Beispiel wird eine Gültigkeit von 20 Jahren festgelegt:

   ```shell
   openssl x509 -req -days 7300 -in selfsigncert-ios.csr  
     -signkey selfsigncert-ios.key -out selfsigncert-ios.crt
   ```

1. Konvertieren Sie das selbstsignierte Zertifikat in eine PKCS#12-Datei:

   ```shell
   openssl pkcs12 -export -out selfsigncert-ios.pfx  
     -inkey selfsigncert-ios.key -in selfsigncert-ios.crt
   ```

   Sie können das selbstsignierte Zertifikat verwenden, um Ihre iOS App zu signieren.

1. Aktualisieren Sie den Speicherort der PFX-Datei und des Kennworts.
1. Bevor Sie Ihre Anwendung in Xcode erstellen, gehen Sie zu  **[!UICONTROL Build Phases]** > **[!UICONTROL Run Script]** und fügen Sie dem Ausführungsskript den folgenden Befehl hinzu:

   ```shell
   mkdir -p "${PROJECT_DIR}/generatedRes" "${PROJECT_DIR}/machotools" sign  
     -in "${CODESIGNING_FOLDER_PATH}/${EXECUTABLE_NAME}"  
     -out "${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest"  
     -pfx "${PROJECT_DIR}/selfsigncert-ios.pfx"  
     -pass PASSWORD
   ```

1. Ausführen [!DNL machotools] , um den Hash-Wert Ihrer App-Herausgeber-ID zu generieren.

   ```shell
   ./machotools dumpMachoSignature -in ${PROJECT_DIR}/generatedRes/AAXSAppDigest.digest
   ```

1. Erstellen Sie eine neue DRM-Richtlinie oder aktualisieren Sie Ihre vorhandene Richtlinie, um den zurückgegebenen Herausgeber-ID-Hash-Wert einzuschließen.
1. Verwenden der [!DNL AdobePolicyManager.jar]erstellen Sie eine neue DRM-Richtlinie (aktualisieren Sie Ihre vorhandene Richtlinie), um den zurückgegebenen Publisher-ID-Hash-Wert, eine optionale App-ID sowie die minimalen und maximalen Versionsattribute in die eingeschlossenen einzuschließen. [!DNL flashaccess-tools.properties] -Datei.

   ```shell
   java -jar libs/AdobePolicyManager.jar new app_allowlist.pol
   ```

1. Verpacken Sie den Inhalt mithilfe der neuen DRM-Richtlinie und bestätigen Sie die Wiedergabe des auf der Zulassungsliste stehenden Inhalts in Ihrer iOS-App.
