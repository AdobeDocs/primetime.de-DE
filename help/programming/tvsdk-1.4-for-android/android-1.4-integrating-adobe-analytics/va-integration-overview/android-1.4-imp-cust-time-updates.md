---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom TVSDK localTime-Wert gemeldete Position angeben. Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom TVSDK localTime-Wert gemeldete Position angeben. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-title: Implementieren benutzerdefinierter Zeitaktualisierungen
title: Implementieren benutzerdefinierter Zeitaktualisierungen
uuid: 7f5d46e5-eab6-4bdc-b015-ae27ddb609ce
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Implementieren benutzerdefinierter Zeitaktualisierungen {#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom TVSDK localTime-Wert gemeldete Position angeben. Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

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