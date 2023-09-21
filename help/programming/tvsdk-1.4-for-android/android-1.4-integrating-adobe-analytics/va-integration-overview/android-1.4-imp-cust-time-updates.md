---
description: In einigen Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die Position bereitstellen, die vom TVSDK localTime -Wert gemeldet wird. Beispielsweise kann während einer linearen Stream-Wiedergabe die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.
title: Benutzerdefinierte Zeitaktualisierungen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Benutzerdefinierte Zeitaktualisierungen implementieren {#implement-custom-time-updates}

In einigen Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die Position bereitstellen, die vom TVSDK localTime -Wert gemeldet wird. Beispielsweise kann während einer linearen Stream-Wiedergabe die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine andere Abspielposition als die Standardposition festlegen möchten.

So überschreiben Sie die standardmäßige Abspielposition:

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
>Die Werte in diesem Code-Snippet sind nur Beispiele. Sie müssen für Ihre benutzerdefinierte Abspielposition unterschiedliche Werte verwenden.
