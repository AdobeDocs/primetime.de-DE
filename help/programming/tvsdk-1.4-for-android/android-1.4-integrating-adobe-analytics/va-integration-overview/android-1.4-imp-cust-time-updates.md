---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom TVSDK localTime-Wert gemeldete Position angeben. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
title: Implementieren benutzerdefinierter Zeitaktualisierungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Implementieren benutzerdefinierter Zeitaktualisierungen {#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom TVSDK localTime-Wert gemeldete Position angeben. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine andere Abspielposition als die Standardposition festlegen möchten.

So überschreiben Sie die Standardposition der Abspielleiste:

```java
vaMetadata.setCurrentTimeUpdateBlock(new VideoAnalyticsMetadata.CurrentTimeUpdateBlock() { 
    @Override 
    public long call() { 
        long range = 500L; 
        Random r = new Random() 
        return (long)(r.nextDouble()*range); 
    } 
});
```

>[!IMPORTANT]
>
>Die Werte in diesem Codefragment sind nur Beispiele. Sie müssen unterschiedliche Werte für Ihre benutzerdefinierte Abspielposition verwenden.