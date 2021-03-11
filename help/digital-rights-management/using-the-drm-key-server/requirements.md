---
title: Anforderungen für die Verwendung des Primetime DRM Key-Servers
description: Anforderungen für die Verwendung des Primetime DRM Key-Servers
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Einführung {#introduction}

Primetime DRM Key Server ist ein Multi-Mandant Key Server für Remote iOS- und/oder Xbox 360-Versand. Wenn Remote Key Versand in einer Richtlinie für iOS aktiviert ist, muss ein Primetime-DRM-Key-Server bereitgestellt werden, um die Wiedergabe von Inhalten auf iOS-Clients zu aktivieren. Primetime DRM Key Server ist immer für Xbox 360 erforderlich.

## Voraussetzungen für die Verwendung des Primetime-DRM-Schlüsselservers {#requirements-for-using-primetime-drm-key-server}

Die Mindestanforderungen für die Verwendung von Primetime DRM Key Server sind:

* [Java JRE 1.6 ](https://www.oracle.com/technetwork/java/javase/downloads/index.html) oder höher. (Um HSM auf Windows 64 Bit zu verwenden, ist JRE 8 erforderlich.)

   >[!NOTE]
   >
   >64-Bit PKCS11 wird jetzt in OpenJDK 8 unterstützt: [https://openjdk.java.net/jeps/131](https://openjdk.java.net/jeps/131) und Oracle JDK: [https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559](https://bugs.java.com/bugdatabase/view_bug.do?bug_id=6880559).

* [Apache Tomcat 7](https://tomcat.apache.org)
* Von der Adobe ausgestellte Berechtigungen
* Von Microsoft ausgestellte Anmeldeinformationen (für Xbox 360-Clients)