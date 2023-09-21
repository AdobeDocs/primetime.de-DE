---
title: Erstellen der Flash Access Manager AIR-Anwendung
description: Erstellen der Flash Access Manager AIR-Anwendung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Erstellen der Flash Access Manager AIR-Anwendung {#building-the-flash-access-manager-air-application}

Um die AIR-Datei des Flash Access-Managers aus dem Quellcode zu erstellen, müssen Sie das Flex- und das AIR-SDK auf Ihrem Computer installiert haben. Bevor Sie die Anwendung verpacken und ausführen können, müssen Sie den MXML-Code mithilfe der [!DNL amxmlc] Compiler. Die [!DNL amxmlc] Compiler finden Sie im [!DNL bin] Verzeichnis des Flex SDK 4 oder höher. Bei Bedarf können Sie Ihre Pfadumgebungsvariable so einstellen, dass sie das bin-Verzeichnis des Flex SDK enthält, damit die Dienstprogramme einfacher über die Befehlszeile ausgeführt werden können.

Führen Sie die folgenden Schritte aus, um die AIR-Datei von Flash Access Manager zu erstellen:

1. Öffnen Sie eine Befehlszeile oder ein Terminal und navigieren Sie zum Projektordner der Flash Access Manager AIR-Anwendung ( [!DNL UI Tools\Flash Access Manager] im Verzeichnis &quot;Referenzimplementierung&quot;).
1. Geben Sie den folgenden Befehl ein:

   ```
   amxmlc src\FlashAccessmanager.mxml
   ```

   Läuft [!DNL amxmlc] herstellt [!DNL FlashAccessManager.swf], der den kompilierten Code der Anwendung enthält.

Das Adobe AIR SDK enthält das Dienstprogramm AIR Developer Tool (ADT) zum Packen von AIR-Anwendungen und Generieren von Zertifikaten. AIR-Anwendungen sollten digital signiert werden. Benutzer erhalten eine Warnung, wenn sie Anwendungen installieren, die nicht ordnungsgemäß signiert sind oder überhaupt nicht signiert sind. Um mithilfe der Befehlszeile ein Zertifikat zu generieren, öffnen Sie ein Konsolenfenster im selben Ordner wie Ihre AIR-Anwendung und geben Sie Folgendes ein:

```
adt -certificate -cn SelfSigned 1024-RSA testCert.pfx  
<i class="+ topic ph hi-d="" i "="">
  some_password 
</i class="+ topic>
```

Substitute *some_password* mit einem Kennwort Ihrer Wahl. Nach einigen Sekunden sollte ADT seinen Zertifikatgenerierungsprozess abschließen. Sie sollten über eine neue [!DNL testCert.pfx] -Datei in Ihrem Anwendungsverzeichnis.

Verwenden Sie als Nächstes ADT , um die Anwendung in ein [!DNL .air] -Datei mithilfe des Befehls:

```
adt -package -storetype pkcs12 -keystore testCert.pfx FlashAccessManager.air src\FlashAccessManager-app.xml . -C src assets
```

Dieser Befehl weist ADT an, Ihre Anwendung mithilfe der Schlüsseldatei in [!DNL testCert.pfx]. In der obigen Zeile konfigurieren Sie ADT, um Ihre gesamte Anwendung in einer Datei mit dem Namen zu verpacken. [!DNL FlashAccessManager.air], und um die Dateien einzuschließen [!DNL FlashAccessManager-app.xml] und [!DNL FlashAccessManager.swf] und die Bilder aus dem Asset-Verzeichnis.

Im Rahmen dieses Prozesses werden Sie nach dem Kennwort gefragt, das Sie für Ihre neue Zertifikatdatei festgelegt haben. Geben Sie es ein, warten Sie einen Moment und [!DNL FlashAccessManager.air] sollte sich im selben Verzeichnis befinden wie Ihre Projektdateien.
