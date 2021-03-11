---
title: Verwendung der Primetime-Referenzimplementierung
description: Verwendung der Primetime-Referenzimplementierung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Verwendung der Primetime-Referenzimplementierung {#how-to-use-the-primetime-reference-implementation}

Die Primetime-Referenzimplementierung ist ein modularer Player, der in einzelne Funktionen unterteilt wurde, die Sie einfach über spezialisierte Funktionenmanager ändern können. Diese Funktionenmanager werden als Brücke zur Verbindung der Anwendung und der TVSDK-Bibliothek verwendet.

Sie können die Referenz-Implementierung wie folgt verwenden:

* Verwenden Sie es wie besehen, ohne den Code zu ändern (alle Funktionen sind mit den Standardwerten aktiviert).
* Verwenden Sie sie als Referenz, um zu verstehen, wie die TVSDK-Bibliothek verwendet wird.
* Wählen Sie die für Ihre Anwendung geltenden Funktionen aus, indem Sie die nicht verwendeten Funktionen deaktivieren.
* Passen Sie die Komponenten der Benutzeroberfläche an, ohne Änderungen an den Funktionen vorzunehmen.

Wir bieten die Primetime-Referenzimplementierung, um Ihnen zu helfen, das TVSDK zu verstehen und leicht ändern Sie die Funktion Manager, um Ihren Player anzupassen. Detaillierte Informationen zur TVSDK-Bibliothek finden Sie jedoch im Handbuch [TVSDK 1.4 für Android-Programmierer](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android.pdf).

Klicken Sie für einfachen Zugriff auf die Dokumentation zur Referenz-Implementierungs-API im JavaScript-Format [hier](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/index.html).
