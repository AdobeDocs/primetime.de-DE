---
description: In einigen Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die Position bereitstellen, die durch den localTime -Wert des TVSDK gemeldet wird. Beispielsweise kann während einer linearen Stream-Wiedergabe die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.
title: Benutzerdefinierte Zeitaktualisierungen implementieren
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Benutzerdefinierte Zeitaktualisierungen implementieren {#implement-custom-time-updates}

In einigen Analytics-Implementierungen möchte die Client-Anwendung möglicherweise eine andere Abspielposition als die Position bereitstellen, die durch den localTime -Wert des TVSDK gemeldet wird. Beispielsweise kann während einer linearen Stream-Wiedergabe die Abspielleiste jedes Programms relativ zur Startzeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine Abspielposition festlegen möchten, die sich von der Standardposition unterscheidet.

So überschreiben Sie die standardmäßige Abspielposition:

```
vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
    NSInteger random = arc4random() % 500;  
    return CMTimeMakeWithSeconds(random, 1); 
};
```

>[!IMPORTANT]
>
>In diesem Codebeispiel ist 500 nur ein Beispielwert. Sie müssen einen anderen Wert für Ihre benutzerdefinierte Abspielposition verwenden.
