---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
title: Implementieren benutzerdefinierter Zeitaktualisierungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---


# Implementieren von benutzerdefinierten Zeitaktualisierungen{#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

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

