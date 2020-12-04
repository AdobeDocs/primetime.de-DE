---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.
seo-title: Implementieren benutzerdefinierter Zeitaktualisierungen
title: Implementieren benutzerdefinierter Zeitaktualisierungen
uuid: 174937ca-3c26-4385-a298-8a01fc93ea20
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%

---


# Implementieren benutzerdefinierter Zeitaktualisierungen {#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die Position angeben, die vom localTime-Wert des TVSDK gemeldet wird. Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine Abspielposition festlegen möchten, die sich von der Standardposition unterscheidet.

So überschreiben Sie die Standardposition der Abspielleiste:

```
vaTrackingMetadata.currentTimeUpdateBlock = ^CMTime () { 
    NSInteger random = arc4random() % 500;  
    return CMTimeMakeWithSeconds(random, 1); 
};
```

>[!IMPORTANT]
>
>In diesem Codebeispiel ist 500 nur ein Beispielwert. Sie müssen einen anderen Wert für Ihre benutzerdefinierte Abspielposition verwenden.