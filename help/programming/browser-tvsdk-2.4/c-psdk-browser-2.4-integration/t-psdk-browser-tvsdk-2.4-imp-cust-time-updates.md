---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom "Browser TVSDK localTime"-Wert gemeldete Position angeben.
title: Implementieren benutzerdefinierter Zeitaktualisierungen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Implementieren von benutzerdefinierten Zeitaktualisierungen{#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom &quot;Browser TVSDK localTime&quot;-Wert gemeldete Position angeben.

Beispielsweise kann bei einer linearen Stream-Wiedergabe der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

>[!TIP]
>
>Überschreiben Sie diese Methode nur, wenn Sie eine andere Abspielposition als die Standardposition festlegen möchten.

So überschreiben Sie die Standardposition der Abspielleiste:

```js
vaMetadata.currentTimeUpdateBlock = function() { 
       return playerPositionInSeconds; 
}; 
```

>[!IMPORTANT]
>
>Die Werte in diesem Codefragment sind nur Beispiele. Sie müssen unterschiedliche Werte für Ihre benutzerdefinierte Abspielposition verwenden.

