---
title: SWF-Anwendung zur Listung zulassen
description: SWF-Anwendung zur Listung zulassen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# SWF-Anwendung erlaubt die Auflistung {#swf-application-allowlisting}

Zur Zulassungsliste einer SWF-Anwendung können Sie eine der beiden folgenden Strategien ausführen:

* Sie können eine URL zu einer SWF-Datei angeben. Dies ist ein sehr flexibler Ansatz, besonders in einer Entwicklungs-Umgebung, in der Sie Ihre SWF regelmäßig neu aufbauen.
* Sie können einen SWF-HASH angeben. Dies ist ein kryptografischer Digest-Wert Ihrer SWF. Dieser Ansatz ist weniger flexibel (aber viel strenger), da sich der SWF-HASH ändert, wenn sich die Anwendung ändert und neu aufgebaut wird. In diesem Fall werden alle Inhalte, die an den vorherigen HASH gebunden sind, nicht auf dem neuen Player abgespielt und müssen neu verpackt werden. Das [!DNL PolicyManager.jar]-Tool berechnet den Hash automatisch, wenn Sie eine [!DNL .swf]-Datei angeben.

   Wenn Sie hingegen Primetime DRM über den Flash/Adobe Mediums-Server (FMS/AMS) verwenden, können Sie den Pfad zu den jeweiligen SWFs angeben. FMS/AMS hash die SWFs automatisch, damit Sie sie in die DRM-Richtlinie einfügen können, die zum Verpacken der von FMS/AMS gestreamen Inhalte verwendet wird.

Weitere Informationen finden Sie unter `policy.allowedSWFApplication.n` in *Konfigurationseigenschaften*.
