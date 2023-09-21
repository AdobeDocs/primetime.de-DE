---
title: Voraussetzungen für die Verwendung des Primetime DRM Key Servers
description: Voraussetzungen für die Verwendung des Primetime DRM Key Servers
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Einführung {#introduction}

Der Primetime-DRM-Schlüsselserver ist ein mehrmandantenfähiger Schlüsselserver für die Remote-iOS- und/oder Xbox 360-Schlüsselbereitstellung. Wenn die Remote-Schlüsselbereitstellung in einer Richtlinie für iOS aktiviert ist, muss ein Primetime-DRM-Schlüsselserver bereitgestellt werden, um die Wiedergabe von Inhalten auf iOS-Clients zu ermöglichen. Primetime DRM Key Server ist immer für Xbox 360 erforderlich.

## Voraussetzungen für die Verwendung des Primetime DRM Key Servers {#requirements-for-using-primetime-drm-key-server}

Die Mindestanforderungen für die Verwendung von Primetime DRM Key Server sind:

* [Java JRE 1.6](https://www.oracle.com/technetwork/java/javase/downloads/index.html) oder höher. (Um HSM unter Windows 64 Bit zu verwenden, ist JRE 8 erforderlich.)

  >[!NOTE]
  >
  >PKCS11 (64-Bit) wird jetzt in OpenJDK 8 unterstützt: [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131)und Oracle
* [Apache Tomcat 7](https://tomcat.apache.org)
* Von Adobe ausgestellte Anmeldeinformationen
* Von Microsoft ausgestellte Anmeldeinformationen (für Xbox 360-Clients)
