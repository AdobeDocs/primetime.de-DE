---
title: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
description: Vorbereiten von Kennwörtern für die Dateien mit den Servereigenschaften
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---


# Vorbereiten von Kennwörtern für die Server-Eigenschaftendateien {#preparing-passwords-for-the-server-properties-files}

Um die Sicherheit des Passworts Ihrer Berechtigung sicherzustellen, wird ein Tool zum Verschlüsseln des Kennworts bereitgestellt, bevor es in die Datei [!DNL flashaccess-refimpl.properties] oder [!DNL flashaccess-refimpl-packager.properties] eingegeben wird.

So führen Sie das Tool mit dem bereitgestellten ANT-Skript aus:

* Gehen Sie zu *`<Reference Implementation Server Path>`* [!DNL \refimpl]

* Stellen Sie sicher, dass die `sdkdir`-Eigenschaft in [!DNL build-refimpl.xml] auf den Ordner verweist, der das Adobe Access SDK enthält.
* Führen Sie den folgenden Befehl mit ANT aus:

   ```
       ant -f build-refimpl.xml
   ```

* Geben Sie bei Aufforderung das Kennwort Ihrer Berechtigung ein

So führen Sie das Tool mit Java aus:

* Gehen Sie zu *`<Reference Implementation Server Path>`*\ [!DNL scrambler]

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
>Kennwörter, die mit dem mit der Referenzimplementierung bereitgestellten Dienstprogramm zum Abwracken von Kennwörtern kodiert wurden, funktionieren nicht mit dem Adobe Access Server für geschütztes Streaming.
