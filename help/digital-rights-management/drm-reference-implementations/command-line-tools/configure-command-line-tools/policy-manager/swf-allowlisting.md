---
title: Zulassungsauflistung von SWF-Anwendungen
description: Zulassungsauflistung von SWF-Anwendungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Zulassungsauflistung von SWF-Anwendungen {#swf-application-allowlisting}

Um eine SWF-Anwendung Zulassungsliste, führen Sie eine der beiden folgenden Vorgehensweisen aus:

* Sie können eine URL zu einer SWF angeben. Dies ist ein sehr flexibler Ansatz, insbesondere in einer Entwicklungsumgebung, in der Sie Ihre SWF regelmäßig neu aufbauen.
* Sie können einen SWF-HASH angeben. Dies ist ein kryptografischer Digest-Wert Ihrer SWF. Dieser Ansatz ist weniger flexibel (aber viel strenger), da sich der SWF HASH ändert, wenn sich die Anwendung ändert und neu aufgebaut wird. In diesem Fall werden alle Inhalte, die an den vorherigen HASH gebunden sind, auf dem neuen Player nicht wiedergegeben und müssen neu verpackt werden. Die [!DNL PolicyManager.jar] berechnet den Hash automatisch, wenn Sie eine [!DNL .swf] -Datei.

  Wenn Sie hingegen Primetime DRM über Flash/Adobe Media Server (FMS/AMS) verwenden, können Sie den Pfad zu Ihren jeweiligen SWF angeben. FMS/AMS hasst die SWF automatisch, damit Sie ihn in die DRM-Richtlinie einfügen können, die zum Verpacken der von FMS/AMS gestreamten Inhalte verwendet wird.

Siehe `policy.allowedSWFApplication.n` in *Konfigurationseigenschaften* für Details.
