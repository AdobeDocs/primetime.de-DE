---
description: In bestimmten Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die vom lokalenTime-Wert des TVSDK gemeldete geben. Beispielsweise kann während der Wiedergabe eines LINEAR-Streams die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.
title: Benutzerdefinierte Zeitaktualisierungen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Benutzerdefinierte Zeitaktualisierungen implementieren{#implement-custom-time-updates}

In bestimmten Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die vom lokalenTime-Wert des TVSDK gemeldete geben. Beispielsweise kann während der Wiedergabe eines LINEAR-Streams die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine andere Abspielposition als die Standardposition festlegen möchten.

1. So überschreiben Sie die standardmäßige Abspielposition:

   ```
   vaMetadata.currentTimeUpdateBlock = function():Number { 
      if (currentTime == 0) { 
          currentTime = getTimer(); 
      } 
      return ((getTimer() - currentTime) / 1000 + 1000); 
   }
   ```

   >[!IMPORTANT]
   >
   >Die Werte in diesem Code-Snippet sind nur Beispiele. Sie müssen für Ihre benutzerdefinierte Abspielposition unterschiedliche Werte verwenden.
