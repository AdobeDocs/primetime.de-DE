---
title: Vorbereiten von Kennwörtern für die Servereigenschaftsdateien
description: Vorbereiten von Kennwörtern für die Servereigenschaftsdateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# Vorbereiten von Kennwörtern für die Servereigenschaftsdateien {#preparing-passwords-for-the-server-properties-files}

Um die Sicherheit des Passworts Ihrer Anmeldedaten sicherzustellen, wird ein Tool bereitgestellt, um das Kennwort zu verschlüsseln, bevor es in die [!DNL flashaccess-refimpl.properties] oder [!DNL flashaccess-refimpl-packager.properties] -Datei.

So führen Sie das Tool mit dem angegebenen ANT-Skript aus:

* Navigieren Sie zu *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Stellen Sie die `sdkdir` -Eigenschaft in [!DNL build-refimpl.xml] verweist auf den Ordner, der das Adobe Access SDK enthält
* Führen Sie den folgenden Befehl mit ANT aus:

  ```
      ant -f build-refimpl.xml
  ```

* Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort Ihrer Anmeldedaten ein

So führen Sie das Tool mit Java aus:

* Navigieren Sie zu *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

* Unter Windows:

  ```
  java -classpath path_to_adobe-flashaccess-sdk.jar;.  
  com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

* Unter Linux:

  ```
      java -classpath path_to_adobe-flashaccess-sdk.jar;.  
      com.adobe.flashaccess.refimpl.util.ScrambleUtil your_pfx_password
  ```

Das Dienstprogramm gibt das verschlüsselte Kennwort aus, das Sie in die .properties-Datei kopieren müssen.

>[!NOTE]
>
>Passwörter, die mit dem Kennwort-Scrambling-Dienstprogramm kodiert wurden, das mit der Referenzimplementierung bereitgestellt wird, funktionieren nicht mit der Adobe Access Server für geschütztes Streaming.
