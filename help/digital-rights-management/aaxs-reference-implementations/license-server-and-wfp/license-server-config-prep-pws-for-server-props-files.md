---
seo-title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
uuid: 2d876eb0-b1a5-4c30-ae96-0a22f6a03910
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften {#preparing-passwords-for-the-server-properties-files}

Um die Sicherheit des Passworts Ihrer Berechtigung sicherzustellen, wird ein Tool zum Verschlüsseln des Passworts bereitgestellt, bevor es in die [!DNL flashaccess-refimpl.properties] Datei oder [!DNL flashaccess-refimpl-packager.properties] -Datei eingegeben wird.

So führen Sie das Tool mit dem bereitgestellten ANT-Skript aus:

* Zu *`<Reference Implementation Server Path>`*[!DNL \refimpl]

* Stellen Sie sicher, dass die `sdkdir` Eigenschaft in [!DNL build-refimpl.xml] verweist auf den Ordner, der das Adobe Access SDK enthält.
* Führen Sie den folgenden Befehl mit ANT aus:

   ```
       ant -f build-refimpl.xml
   ```

* Geben Sie bei Aufforderung das Kennwort Ihrer Berechtigung ein

So führen Sie das Tool mit Java aus:

* Zu *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

* Geben Sie an der Eingabeaufforderung den Befehl ein:

* Windows:

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
>Kennwörter, die mit dem mit der Referenz-Implementierung bereitgestellten Dienstprogramm zum Abwracken von Kennwörtern kodiert wurden, funktionieren nicht mit dem Adobe Access Server für geschütztes Streaming.
