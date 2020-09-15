---
description: Um die benutzerdefinierten Skins zu verwenden, müssen Sie die Anpassung ähnlich wie default-video-control.css schreiben und auf diese neue Anpassung im Player verweisen.
seo-description: Um die benutzerdefinierten Skins zu verwenden, müssen Sie die Anpassung ähnlich wie default-video-control.css schreiben und auf diese neue Anpassung im Player verweisen.
seo-title: Benutzerdefinierte Skins
title: Benutzerdefinierte Skins
uuid: bc71926e-0dec-4628-8248-911224a7a6c2
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Benutzerdefinierte Skins{#custom-skins}

Um die benutzerdefinierten Skins zu verwenden, müssen Sie die Anpassung ähnlich wie default-video-control.css schreiben und auf diese neue Anpassung im Player verweisen.

Sie können beispielsweise eine der folgenden Optionen verwenden:

* `<link rel="stylesheet" href="css/common_style.css">`
* `<link rel="stylesheet" href="css/custom-video-controls1.css">`

Sie können die folgenden Arten von Änderungen vornehmen:

* Vordergrundfarbe von Schaltflächen und Text

   Alle Steuerelemente mit Vordergrund verwenden die `vid-skin-fgcolor` Klasse. Um den Vordergrund aller Steuerelemente zu ändern, durchlaufen Sie alle Elemente mit der `vid-skin-fgcolor` Klasse und geben Sie die gewünschte Farbe an.
* Hintergrundfarbe von Schaltflächen und Text

   Alle Steuerelemente mit Vordergrund verwenden die `vid-skin-bgcolor` Klasse. Um den Vordergrund aller Steuerelemente zu ändern, durchlaufen Sie alle Elemente mit `vid-skin-bgcolor` Klasse und geben Sie die gewünschte Farbe an.
* Form des Abspielkopfs

   Der Abspielkopf kann quadratisch oder rund sein. Um den Abspielkopf zu ändern, fügen Sie `square` oder `round` Klasse zu `playhead` Element hinzu.
* Stil der Pufferspinners

   Der Referenz-Player bietet die folgenden Stile von Spinnern können angezeigt werden, wenn der Player Inhalte puffert:

   * Überlagerungstext ( `overlay-text`)
   * Rechteckige Kreisel ( `spinner`)
   * Signal ( `signal`)
   * Vertikale Balken ( `vertical`)

      >[!TIP]
      >
      >Um einen der Pufferspiner zu verwenden, müssen Sie die Klasse im Puffer-Overlay-Element hinzufügen. Fügen Sie `overlay-text`der `BufferOverlay.js` Datei beispielsweise die folgenden Zeilen hinzu:
      >
      >
      ```js
      >var overlay = document.getElementById("buffering-overlay"); 
      >overlay.classList.add ("spinner");
      >```

