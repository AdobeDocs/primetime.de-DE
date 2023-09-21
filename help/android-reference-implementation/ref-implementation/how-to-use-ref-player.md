---
title: Verwendung der Primetime-Referenzimplementierung
description: Verwendung der Primetime-Referenzimplementierung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Verwendung der Primetime-Referenzimplementierung {#how-to-use-the-primetime-reference-implementation}

Die Primetime-Referenzimplementierung ist ein modularer Player, der in einzelne Funktionen unterteilt wurde, die Sie über spezialisierte Feature Manager einfach ändern können. Diese Funktions-Manager werden als Brücke verwendet, um die Anwendung und die TVSDK-Bibliothek zu verbinden.

Sie können die Referenzimplementierung wie folgt verwenden:

* Verwenden Sie sie unverändert, ohne den Code zu ändern (alle Funktionen sind mit Standardwerten aktiviert).
* Verwenden Sie es als Referenz, um zu verstehen, wie die TVSDK-Bibliothek verwendet wird.
* Wählen Sie die Funktionen aus, die für Ihre Anwendung gelten, indem Sie die nicht verwendeten Funktionen deaktivieren.
* Passen Sie die Komponenten der Benutzeroberfläche an, ohne Änderungen an den Funktionen vorzunehmen.

Wir stellen die Primetime-Referenzimplementierung bereit, die Ihnen dabei hilft, das TVSDK zu verstehen und die Feature Manager einfach zu ändern, um Ihren Player anzupassen. Lesen Sie jedoch auch den Abschnitt [TVSDK 1.4 für Android-Programmierhandbuch](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android.pdf) für detaillierte Informationen zur TVSDK-Bibliothek.

Um den einfachen Zugriff auf die Referenzimplementierungs-API-Dokumentation im Javadoc-Format zu erhalten, klicken Sie auf [here](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/index.html).
