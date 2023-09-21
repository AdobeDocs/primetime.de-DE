---
description: Um die benutzerdefinierten Skins zu verwenden, müssen Sie die Anpassung ähnlich wie default-video-control.css schreiben und auf diese neue Anpassung im Player verweisen.
title: Benutzerdefinierte Skins
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Benutzerdefinierte Skins{#custom-skins}

Um die benutzerdefinierten Skins zu verwenden, müssen Sie die Anpassung ähnlich wie default-video-control.css schreiben und auf diese neue Anpassung im Player verweisen.

Sie können beispielsweise eine der folgenden Optionen verwenden:

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

Sie können die folgenden Arten von Änderungen vornehmen:

* Vordergrundfarbe von Schaltflächen und Text

  Alle Steuerelemente mit einem Vordergrund verwenden die `vid-skin-fgcolor` -Klasse. Um den Vordergrund aller Steuerelemente zu ändern, navigieren Sie durch alle Elemente mit der `vid-skin-fgcolor` und geben Sie die gewünschte Farbe an.
* Hintergrundfarbe von Schaltflächen und Text

  Alle Steuerelemente mit einem Vordergrund verwenden die `vid-skin-bgcolor` -Klasse. Um den Vordergrund aller Steuerelemente zu ändern, navigieren Sie durch alle Elemente mit `vid-skin-bgcolor` und geben Sie die gewünschte Farbe an.
* Form des Abspielkopfes

  Der Abspielkopf kann quadratisch oder rund sein. Um den Abspielkopf zu ändern, fügen Sie `square` oder `round` -Klasse zu `playhead` -Element.
* Stil der Pufferung

  Der Referenz-Player bietet die folgenden Arten von Spinnern, die angezeigt werden können, wenn der Player Inhalte puffert:

   * Überlagerungstext ( `overlay-text`)
   * Rechteckige Verdrehung ( `spinner`)
   * Signal ( `signal`)
   * Vertikale Balken ( `vertical`)

     >[!TIP]
     >
     >Um einen der Pufferspinner zu verwenden, müssen Sie die Klasse im Element &quot;Buffering-overlay&quot;hinzufügen. Verwenden Sie zum Beispiel `overlay-text`, fügen Sie die folgenden Zeilen in der `BufferOverlay.js` Datei:
     >
     >```js
     >var overlay = document.getElementById("buffering-overlay"); 
     >overlay.classList.add ("spinner");
     >```
     >
