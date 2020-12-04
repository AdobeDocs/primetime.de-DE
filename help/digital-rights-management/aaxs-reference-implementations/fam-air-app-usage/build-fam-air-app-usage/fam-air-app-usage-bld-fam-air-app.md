---
seo-title: Erstellen der AIR-Flash Access-Manager-Anwendung
title: Erstellen der AIR-Flash Access-Manager-Anwendung
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---


# Erstellen der AIR-Anwendung für Flash Access-Manager {#building-the-flash-access-manager-air-application}

Zum Erstellen der AIR-Flash Access-Manager-Datei aus dem Quellcode müssen Sie das Flex- und das AIR-SDK auf Ihrem Computer installieren. Bevor Sie die Anwendung verpacken und ausführen können, müssen Sie den MXML mit dem [!DNL amxmlc]-Compiler in eine SWF-Datei kompilieren. Der [!DNL amxmlc]-Compiler befindet sich im Ordner [!DNL bin] des Flex 4-SDK oder höher. Bei Bedarf können Sie die Variable &quot;path Umgebung&quot;so einstellen, dass sie den Ordner &quot;Flex SDK bin&quot;enthält, damit die Dienstprogramme in der Befehlszeile leichter ausgeführt werden können.

Führen Sie zum Erstellen der AIR-Datei &quot;Flash Access Manager&quot;das folgende Verfahren aus:

1. Öffnen Sie eine Befehlszeile oder ein Terminal und navigieren Sie zum Projektordner der AIR-Flash Access-Manager-Anwendung ( [!DNL UI Tools\Flash Access Manager] im Ordner &quot;Referenz-Implementierung&quot;).
1. Geben Sie den folgenden Befehl ein:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Wenn Sie [!DNL amxmlc] ausführen, wird [!DNL FlashAccessManager.swf] generiert, was den kompilierten Code der Anwendung enthält.

Das Adobe AIR SDK enthält das Dienstprogramm AIR Developer Tool (ADT), um AIR-Anwendungen zu verpacken und Zertifikate zu generieren. AIR-Anwendungen sollten digital signiert werden; Benutzern wird eine Warnung angezeigt, wenn Anwendungen installiert werden, die nicht ordnungsgemäß signiert oder gar nicht signiert sind. Um ein Zertifikat mit der Befehlszeile zu generieren, öffnen Sie ein Konsolenfenster im selben Ordner wie die AIR-Anwendung und geben Sie Folgendes ein:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Ersetzen Sie *some_password* durch ein Kennwort Ihrer Wahl. Nach einigen Sekunden muss ADT den Zertifikatsgenerierungsvorgang abschließen, und Sie sollten eine neue [!DNL testCert.pfx]-Datei im Anwendungsordner haben.

Verwenden Sie dann ADT, um die Anwendung mithilfe des Befehls in eine [!DNL .air]-Datei zu verpacken:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Mit diesem Befehl wird ADT angewiesen, Ihre Anwendung zu verpacken, indem die Schlüsseldatei in [!DNL testCert.pfx] verwendet wird. In der obigen Zeile konfigurieren Sie ADT, um die gesamte Anwendung in einer Datei mit dem Namen [!DNL FlashAccessManager.air] zu verpacken und die Dateien [!DNL FlashAccessManager-app.xml] und [!DNL FlashAccessManager.swf] sowie die Bilder aus dem Elementordner einzuschließen.

Während dieses Vorgangs werden Sie nach dem Kennwort aufgefordert, das Sie für die neue Zertifikatdatei festgelegt haben. Geben Sie es ein, warten Sie einen Moment, und eine [!DNL FlashAccessManager.air]-Datei sollte im selben Verzeichnis wie die Projektdateien angezeigt werden.
