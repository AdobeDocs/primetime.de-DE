---
seo-title: Pfad und Klassenpfad konfigurieren
title: Pfad und Klassenpfad konfigurieren
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# Pfad und Klassenpfad konfigurieren{#configure-the-path-and-classpath}

Die [!DNL flashaccess.war] enthält [!DNL jsafeWithNative.jar]die Crypto-J-Bibliothek. Letztere benötigt eine zusätzliche native Bibliothek, um Kryptovorgänge durchzuführen.

1. Hinzufügen Sie die native [!DNL jsafe] Bibliothek an Ihren Pfad.

   * **Linux /[!DNL libjsafe.so]-** Das Verzeichnis mit [!DNL libjsafe.so] muss auf dem Pfad (native Crypto-J-Bibliotheken sind auch für andere Plattformen verfügbar). Legen Sie beispielsweise [!DNL libjsafe.so] auf `LD_LIBRARY_PATH`.

   * **Windows /[!DNL jsafe.dll]-** Das Gegenstück auf Windows zu [!DNL libjsafe.so] ist die entsprechende [!DNL jsafe.dll].
   Diese Bibliotheken stehen Ihnen im [!DNL thirdparty] Bibliotheksordner zur Verfügung.
1. Legen Sie eine der [!DNL adobe-flashaccess-certs] JAR-Dateien in den Klassenpfad.

       Diese JAR-Datei ist nicht in der WAR-Datei enthalten. müssen Sie sie explizit dem Klassenpfad hinzufügen.
   
   * Entwicklungsserver - sollte nur verwendet [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Produktionsserver - nur verwenden [!DNL adobe-flashaccess- certs.jar]

Die Distribution enthält einen [!DNL shared] Ordner, der sowohl die JAR-Datei als auch eine vorkonfigurierte [!DNL AdobeInitial.properties] Datei enthält. Adobe empfiehlt, diese Elemente der Datei `common.loader` über die [!DNL catalina.properties] Datei hinzuzufügen. Beispiel:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


