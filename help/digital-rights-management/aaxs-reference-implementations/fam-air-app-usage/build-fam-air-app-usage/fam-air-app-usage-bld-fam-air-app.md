---
seo-title: Erstellen der Flash Access Manager-AIR-Anwendung
title: Erstellen der Flash Access Manager-AIR-Anwendung
uuid: 00927eb3-b8eb-4dd4-b528-91b70760c8cd
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Erstellen der Flash Access Manager-AIR-Anwendung {#building-the-flash-access-manager-air-application}

Um die Flash Access Manager-AIR-Datei aus dem Quellcode zu erstellen, müssen Sie das Flex- und AIR-SDK auf Ihrem Computer installieren. Bevor Sie die Anwendung verpacken und ausführen können, müssen Sie den MXML-Code mit dem [!DNL amxmlc] Compiler in eine SWF-Datei kompilieren. Der [!DNL amxmlc] Compiler befindet sich im [!DNL bin] Verzeichnis des Flex 4-SDK oder höher. Bei Bedarf können Sie die Variable &quot;path Umgebung&quot;so einstellen, dass sie den Flex SDK bin-Ordner enthält, damit die Dienstprogramme in der Befehlszeile leichter ausgeführt werden können.

Verwenden Sie das folgende Verfahren, um die AIR-Datei von Flash Access Manager zu erstellen:

1. Öffnen Sie eine Befehlszeile oder ein Terminal und navigieren Sie zum Projektordner der Flash Access Manager AIR-Anwendung ( [!DNL UI Tools\Flash Access Manager] im Ordner &quot;Referenz-Implementierung&quot;).
1. Geben Sie den folgenden Befehl ein:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Wird ausgeführt [!DNL amxmlc] generiert [!DNL FlashAccessManager.swf], was den kompilierten Code der Anwendung enthält.

Das Adobe AIR-SDK enthält das Dienstprogramm AIR Developer Tool (ADT), um AIR-Anwendungen zu verpacken und Zertifikate zu generieren. AIR-Anwendungen sollten digital signiert werden; Benutzern wird eine Warnung angezeigt, wenn Anwendungen installiert werden, die nicht ordnungsgemäß signiert oder gar nicht signiert sind. Um ein Zertifikat mit der Befehlszeile zu generieren, öffnen Sie ein Konsolenfenster im selben Ordner wie die AIR-Anwendung und geben Sie Folgendes ein:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Ersetzen Sie *some_password* durch ein Passwort Ihrer Wahl. Nach einigen Sekunden muss ADT den Zertifikatsgenerierungsvorgang abschließen, und Sie sollten eine neue [!DNL testCert.pfx] Datei im Anwendungsverzeichnis haben.

Verwenden Sie dann ADT, um die Anwendung mithilfe des Befehls in eine [!DNL .air] Datei zu verpacken:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Mit diesem Befehl wird ADT angewiesen, Ihre Anwendung zu verpacken, indem die Schlüsseldatei in verwendet [!DNL testCert.pfx]wird. In der obigen Zeile konfigurieren Sie ADT, um die gesamte Anwendung in eine Datei mit dem Namen [!DNL FlashAccessManager.air]zu verpacken und die Dateien [!DNL FlashAccessManager-app.xml] [!DNL FlashAccessManager.swf] und Bilder sowie die Bilder aus dem Asset-Ordner einzuschließen.

Während dieses Vorgangs werden Sie nach dem Kennwort aufgefordert, das Sie für die neue Zertifikatdatei festgelegt haben. Geben Sie es ein, warten Sie einen Moment und eine [!DNL FlashAccessManager.air] Datei sollte im selben Verzeichnis wie die Projektdateien angezeigt werden.
