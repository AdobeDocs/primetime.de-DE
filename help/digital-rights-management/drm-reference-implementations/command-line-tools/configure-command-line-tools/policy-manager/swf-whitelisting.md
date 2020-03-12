---
seo-title: Whitelist für SWF-Anwendungen
title: Whitelist für SWF-Anwendungen
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Whitelist für SWF-Anwendungen{#swf-application-whitelisting}

Zur Whitelist einer SWF-Anwendung können Sie eine der beiden folgenden Strategien befolgen:

* Sie können eine URL zu einer SWF-Datei angeben. Dies ist ein sehr flexibler Ansatz, besonders in einer Entwicklungs-Umgebung, in der Sie Ihre SWF regelmäßig neu aufbauen.
* Sie können einen SWF-HASH angeben. Dies ist ein kryptografischer Digest-Wert Ihrer SWF. Dieser Ansatz ist weniger flexibel (aber viel strenger), da sich der SWF-HASH ändert, wenn sich die Anwendung ändert und neu aufgebaut wird. In diesem Fall werden alle Inhalte, die an den vorherigen HASH gebunden sind, nicht auf dem neuen Player abgespielt und müssen neu verpackt werden. Das [!DNL PolicyManager.jar] Tool berechnet den Hash automatisch, wenn Sie eine [!DNL .swf] Datei angeben.

   Wenn Sie hingegen Primetime DRM über Flash/Adobe Media Server (FMS/AMS) verwenden, können Sie den Pfad zu den jeweiligen SWFs angeben. FMS/AMS hash die SWFs automatisch, damit Sie sie in die DRM-Richtlinie einfügen können, die zum Verpacken der von FMS/AMS gestreamen Inhalte verwendet wird.

Weitere Informationen finden Sie `policy.allowedSWFApplication.n` unter *Konfigurationseigenschaften* .
