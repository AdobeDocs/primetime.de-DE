---
seo-title: Rollenerkennung
title: Rollenerkennung
uuid: cc554194-2848-4104-85eb-f697a86c72f2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Rollenerkennung{#rollback-detection}

Für die Rollback-Erkennung müssen einige Verwendungsregeln vorsehen, dass der Client Statusinformationen zur Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer den Inhalt zum ersten Mal anzeigte. Dieses Ereignis löst den Beginn des Wiedergabefensters aus. Um das Wiedergabefenster sicher durchzusetzen, muss der Server sicherstellen, dass der Client nicht gesichert wird und der Clientstatus wiederhergestellt wird, damit die auf dem Client gespeicherte Wiedergabefenster-Beginn-Zeit entfernt wird. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt. Für jede Anforderung ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` aufruft, um das `ClientState`-Objekt abzurufen, und dann `ClientState.getCounter()` aufruft, um den aktuellen Wert des Clientstatuszählers abzurufen. Der Server sollte diesen Wert für jeden Client speichern (verwenden Sie `MachineId.getUniqueId()`, um den Client zu identifizieren, der mit dem Rollback-Zählerwert verknüpft ist), und dann `ClientState.incrementCounter()` aufrufen, um den Zählerwert um 1 zu erhöhen. Wenn der Server erkennt, dass der Zählerwert kleiner als der letzte vom Server angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgenommen. Weitere Informationen zur Fehlererkennung im Clientstatus finden Sie in der API-Referenzdokumentation.`ClientState`
