---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-title: Implementieren benutzerdefinierter Zeitaktualisierungen
title: Implementieren benutzerdefinierter Zeitaktualisierungen
uuid: 303303eb-c371-4766-a1ee-806ba75b4e01
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Implementieren benutzerdefinierter Zeitaktualisierungen{#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine Abspielposition festlegen möchten, die sich von der Standardposition unterscheidet.

1. So überschreiben Sie die Standardposition der Abspielleiste:

   ```
   vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
       NSInteger random = arc4random() % 500;  
       return CMTimeMakeWithSeconds(random, 1); 
   };
   ```

   >[!IMPORTANT]
   >
   >In diesem Codebeispiel ist 500 nur ein Beispielwert. Sie müssen einen anderen Wert für Ihre benutzerdefinierte Abspielposition verwenden.

