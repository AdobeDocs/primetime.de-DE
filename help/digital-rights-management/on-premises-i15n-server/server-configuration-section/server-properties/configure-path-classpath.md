---
title: Pfad und Klassenpfad konfigurieren
description: Pfad und Klassenpfad konfigurieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---


# Pfad und Klassenpfad konfigurieren{#configure-the-path-and-classpath}

Das [!DNL flashaccess.war] enthält [!DNL jsafeWithNative.jar], die Crypto-J-Bibliothek. Letztere benötigt eine zusätzliche native Bibliothek, um Kryptovorgänge durchzuführen.

1. hinzufügen Sie die native Bibliothek [!DNL jsafe] in Ihren Pfad.

   * **Linux /  [!DNL libjsafe.so] -** Das Verzeichnis, das enthält,  [!DNL libjsafe.so] muss auf dem Pfad (native Crypto-J-Bibliotheken sind auch für andere Plattformen verfügbar). Legen Sie beispielsweise [!DNL libjsafe.so] auf `LD_LIBRARY_PATH` fest.

   * **Windows /  [!DNL jsafe.dll] -** Das Gegenstück auf Windows zu  [!DNL libjsafe.so] ist die entsprechende  [!DNL jsafe.dll].
   Diese Bibliotheken stehen Ihnen im Bibliotheksordner [!DNL thirdparty] zur Verfügung.
1. Legen Sie eine der [!DNL adobe-flashaccess-certs]-JAR-Dateien in den Klassenpfad.

       Diese JAR-Datei ist nicht in der WAR-Datei enthalten. müssen Sie sie explizit dem Klassenpfad hinzufügen.
   
   * Entwicklungsserver - Sollte nur [!DNL adobe-flashaccess-certs-prerelease.jar] verwenden.
   * Produktionsserver - nur [!DNL adobe-flashaccess- certs.jar] verwenden

Die Distribution enthält einen Ordner [!DNL shared], der sowohl die JAR-Datei als auch eine vorkonfigurierte [!DNL AdobeInitial.properties]-Datei enthält. Adobe empfiehlt, dass Sie diese Elemente der Datei `common.loader` über die Datei [!DNL catalina.properties] hinzufügen. Beispiel:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


