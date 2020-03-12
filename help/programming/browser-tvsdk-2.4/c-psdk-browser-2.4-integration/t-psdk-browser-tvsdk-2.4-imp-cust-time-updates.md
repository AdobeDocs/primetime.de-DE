---
description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom "Browser TVSDK localTime"-Wert gemeldete Position angeben.
seo-description: In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom "Browser TVSDK localTime"-Wert gemeldete Position angeben.
seo-title: Implementieren benutzerdefinierter Zeitaktualisierungen
title: Implementieren benutzerdefinierter Zeitaktualisierungen
uuid: 26a0592c-a47b-4d65-b984-5e51533dcddc
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Implementieren benutzerdefinierter Zeitaktualisierungen{#implement-custom-time-updates}

In einigen Analytics-Implementierungen sollte die Clientanwendung möglicherweise eine andere Abspielposition als die vom &quot;Browser TVSDK localTime&quot;-Wert gemeldete Position angeben.

Beispielsweise kann während der Wiedergabe eines linearen Streams der Abspielkopf jedes Programms relativ zur Beginn-Zeit angegeben werden.

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

