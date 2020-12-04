---
description: In bestimmten Analytics-Implementierungen sollte die Client-Anwendung möglicherweise eine andere Abspielposition als die des TVSDK localTime-Werts angeben. Beispielsweise kann während der Wiedergabe eines LINEAR-Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-description: In bestimmten Analytics-Implementierungen sollte die Client-Anwendung möglicherweise eine andere Abspielposition als die des TVSDK localTime-Werts angeben. Beispielsweise kann während der Wiedergabe eines LINEAR-Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-title: Implementieren benutzerdefinierter Zeitaktualisierungen
title: Implementieren benutzerdefinierter Zeitaktualisierungen
uuid: 2b46eca9-3815-4c44-ab5e-21678c35f410
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Implementieren von benutzerdefinierten Zeitaktualisierungen{#implement-custom-time-updates}

In bestimmten Analytics-Implementierungen sollte die Client-Anwendung möglicherweise eine andere Abspielposition als die des TVSDK localTime-Werts angeben. Beispielsweise kann während der Wiedergabe eines LINEAR-Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine andere Abspielposition als die Standardposition festlegen möchten.

1. So überschreiben Sie die Standardposition der Abspielleiste:

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
   >Die Werte in diesem Codefragment sind nur Beispiele. Sie müssen unterschiedliche Werte für Ihre benutzerdefinierte Abspielposition verwenden.

