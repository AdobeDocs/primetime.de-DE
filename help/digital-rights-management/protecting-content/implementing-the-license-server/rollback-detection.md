---
seo-title: Rollenerkennung
title: Rollenerkennung
uuid: ec124bac-a1d7-45be-bf09-a99d5eec5042
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Rollenerkennung {#rollback-detection}

Für die Rollback-Erkennung müssen einige Verwendungsregeln vorsehen, dass der Client Statusinformationen zur Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer den Inhalt zum ersten Mal anzeigte. Dieses Ereignis löst den Beginn des Wiedergabefensters aus. Um das Wiedergabefenster sicher durchzusetzen, muss der Server sicherstellen, dass der Beginn nicht gesichert wird, und den Clientstatus wiederherstellen, um die auf dem Client gespeicherte Wiedergabefenster-Zeit zu entfernen. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt.

Für jede Anforderung ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` zum Abrufen des `ClientState` Objekts aufruft und dann den aktuellen Wert des Clientstatuszählers abruft `ClientState.getCounter()` . Der Server sollte diesen Wert für jeden Client speichern ( `MachineId.getUniqueId()` um den Client zu identifizieren, der mit dem Rollback-Zählerwert verbunden ist) und dann aufrufen, den Zählerwert um 1 zu erhöhen `ClientState.incrementCounter()` . Wenn der Server erkennt, dass der Zählerwert kleiner als der letzte vom Server angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgenommen.

Weitere Informationen zur Fehlererkennung im Clientstatus finden Sie in der `ClientState` API-Referenzdokumentation.
