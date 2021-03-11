---
description: Sie können HTML-Überlagerungen mit StageVideo verwenden, um UI-Elemente in der Videoebene "Liste"des Flashs anzuzeigen. Diese Ebene befindet sich über der StageVideo-Ebene, sodass StageVideo immer hinter den Elementen der Display-Liste eines Flashs angezeigt wird.
title: StageVideo- und HTML-Überlagerungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# StageVideo- und HTML-Überlagerungen{#stagevideo-and-html-overlays}

Sie können HTML-Überlagerungen mit StageVideo verwenden, um UI-Elemente in der Videoebene &quot;Liste&quot;des Flashs anzuzeigen. Diese Ebene befindet sich über der StageVideo-Ebene, sodass StageVideo immer hinter den Elementen der Display-Liste eines Flashs angezeigt wird.

HTML-Überlagerungen sind Benutzeroberflächenelemente, die Sie in der Videoanzeigeebene des Flashs anzeigen können, die von `StageVideo` auf der eigenen Ebene wiedergegeben wird. Vor Flash 15 konnten Sie keine HTML-Überlagerungen verwenden, wenn keine Hardwarebeschleunigung verfügbar war. Ab Flash 15 werden HTML-Überlagerungen angezeigt, wenn `StageVideo` auf das Software-Rendering zurückfällt.

>[!IMPORTANT]
>
>Abhängig von den Systemfunktionen kann die Leistung bei der Verwendung von HTML-Überlagerungen um ein größeres oder geringeres Maß beeinträchtigt werden.

Berücksichtigen Sie die folgenden Informationen:

* Flash Player 15:

   * Sie können HTML-Überlagerungen unabhängig davon verwenden, ob Hardwarebeschleunigung verfügbar ist.
   * Um HTML-Überlagerungen zu verwenden, setzen Sie `wmode` auf `opaque`.

* Flash Player 14:

   * Wenn die Hardwarebeschleunigung verfügbar ist, befindet sich `StageVideo` unter der Display-Liste des Flashs, sodass Sie HTML-Überlagerungen verwenden können.
   * Wenn die Hardwarebeschleunigung nicht verfügbar ist, wird das Video über allen anderen Elementen im Browser wiedergegeben, wodurch die Verwendung von HTML-Überlagerungen verhindert wird.

Hier finden Sie die Mindestanforderungen für den Browser, um HTML-Überlagerungen mit `StageVideo` zu verwenden:

* Firefox Version 4 und höher
* Safari Version 4 und höher
* Internet Explorer:

   * Version 9+ unter Windows 7 und höher
   * Version 10+ unter Windows XP

* Chrome Version 26 und neuer

   >[!IMPORTANT]
   >
   >Chrome Pepper unter Windows XP und Windows Vista wird nicht unterstützt.

