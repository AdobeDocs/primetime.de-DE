---
description: Sie können HTML-Überlagerungen mit StageVideo verwenden, um Benutzeroberflächen-Elemente in der Videoebene mit der Flash-Anzeigeliste anzuzeigen. Diese Ebene befindet sich über der StageVideo-Ebene, sodass StageVideo immer hinter allen Flash-Anzeigelistenelementen angezeigt wird.
title: StageVideo- und HTML-Überlagerungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# StageVideo- und HTML-Überlagerungen{#stagevideo-and-html-overlays}

Sie können HTML-Überlagerungen mit StageVideo verwenden, um Benutzeroberflächen-Elemente in der Videoebene mit der Flash-Anzeigeliste anzuzeigen. Diese Ebene befindet sich über der StageVideo-Ebene, sodass StageVideo immer hinter allen Flash-Anzeigelistenelementen angezeigt wird.

HTML-Überlagerungen sind Benutzeroberflächen-Elemente, die Sie in der Flash-Anzeigeebene in Videos anzeigen können, die von `StageVideo` auf dem eigenen Flugzeug. Vor Flash 15 konnten Sie keine HTML-Überlagerungen verwenden, wenn die Hardwarebeschleunigung nicht verfügbar war. Ab Flash 15 werden HTML-Überlagerungen bei `StageVideo` zurück auf das Software-Rendering.

>[!IMPORTANT]
>
>Abhängig von den Systemfunktionen kann sich die Leistung bei Verwendung von HTML-Überlagerungen bis zu einem größeren oder geringeren Grad verschlechtern.

Beachten Sie die folgenden Informationen:

* Flash Player 15:

   * Sie können HTML-Überlagerungen verwenden, unabhängig davon, ob die Hardwarebeschleunigung verfügbar ist.
   * Um HTML-Überlagerungen zu verwenden, legen Sie `wmode` nach `opaque`.

* Flash Player 14:

   * Wenn die Hardwarebeschleunigung verfügbar ist, `StageVideo` befindet sich unterhalb der Flash-Anzeigeliste, sodass Sie HTML-Überlagerungen verwenden können.
   * Wenn die Hardwarebeschleunigung nicht verfügbar ist, wird das Video über allen anderen Elementen im Browser gerendert, was die Verwendung von HTML-Überlagerungen verhindert.

Hier finden Sie die Mindestanforderungen an den Browser, um HTML-Überlagerungen mit `StageVideo`:

* Firefox Version 4 und höher
* Safari Version 4 und höher
* Internet Explorer:

   * Version 9+ unter Windows 7 und höher
   * Version 10+ unter Windows XP

* Chrome-Version 26 und höher

  >[!IMPORTANT]
  >
  >Chrome Pepper unter Windows XP und Windows Vista wird nicht unterstützt.
