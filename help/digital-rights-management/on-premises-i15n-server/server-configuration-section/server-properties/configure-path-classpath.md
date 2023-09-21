---
title: Pfad und Klassenpfad konfigurieren
description: Pfad und Klassenpfad konfigurieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# Pfad und Klassenpfad konfigurieren{#configure-the-path-and-classpath}

Die [!DNL flashaccess.war] contains [!DNL jsafeWithNative.jar], die Crypto-J-Bibliothek. Letztere erfordert eine zusätzliche native Bibliothek, um Kryptovorgänge durchzuführen.

1. Hinzufügen des nativen [!DNL jsafe] -Bibliothek zu Ihrem Pfad hinzu.

   * **Linux / [!DNL libjsafe.so] -** Der Ordner, der [!DNL libjsafe.so] muss sich auf dem Pfad befinden (native Crypto-J-Bibliotheken sind auch für andere Plattformen verfügbar). Legen Sie beispielsweise [!DNL libjsafe.so] on `LD_LIBRARY_PATH`.

   * **Windows / [!DNL jsafe.dll] -** Das Gegenstück unter Windows zu [!DNL libjsafe.so] angemessen ist [!DNL jsafe.dll].

   Diese Bibliotheken stehen Ihnen im Abschnitt [!DNL thirdparty] Bibliotheksordner.
1. Setzen Sie einen der [!DNL adobe-flashaccess-certs] JAR-Dateien im Klassenpfad.

       Diese JAR-Datei ist nicht in der WAR-Datei enthalten. Sie müssen sie explizit zum Klassenpfad hinzufügen.
   
   * Entwicklungsserver - sollte nur verwenden [!DNL adobe-flashaccess-certs-prerelease.jar].
   * Produktionsserver - sollte nur verwenden [!DNL adobe-flashaccess- certs.jar]

Die Verteilung umfasst eine [!DNL shared] Ordner, der sowohl die JAR-Datei als auch eine vorkonfigurierte [!DNL AdobeInitial.properties] -Datei. Adobe empfiehlt, diese Elemente zum `common.loader` über die [!DNL catalina.properties] -Datei. Beispiel:

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```
