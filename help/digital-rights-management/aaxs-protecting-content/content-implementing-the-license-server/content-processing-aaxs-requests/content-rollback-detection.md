---
title: Rollenerkennung
description: Rollenerkennung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Rollenerkennung{#rollback-detection}

Für die Rollback-Erkennung müssen einige Nutzungsregeln vorsehen, dass der Client Statusinformationen für die Durchsetzung der Rechte aufbewahrt. Um beispielsweise die Nutzungsregel für das Wiedergabefenster durchzusetzen, speichert der Client das Datum und die Uhrzeit, zu der der Benutzer mit der Anzeige des Inhalts begonnen hat. Dieses Ereignis Trigger den Start des Wiedergabefensters. Um das Wiedergabefenster sicher durchzusetzen, muss der Server sicherstellen, dass der Benutzer keine Sicherung durchführt und den Clientstatus wiederherstellt, um die auf dem Client gespeicherte Startzeit des Wiedergabefensters zu entfernen. Der Server verfolgt dies, indem er den Wert des Rollback-Zählers des Clients verfolgt. Für jede Anfrage ruft der Server den Wert des Zählers ab, indem er `RequestMessageBase.getClientState()` um die `ClientState` -Objekt, dann aufrufen `ClientState.getCounter()` , um den aktuellen Wert des Kundenstatuszählers abzurufen. Der Server sollte diesen Wert für jeden Client speichern (verwenden Sie `MachineId.getUniqueId()` , um den mit dem Rollback-Zählerwert verknüpften Client zu identifizieren), und rufen Sie dann `ClientState.incrementCounter()` , um den Zählerwert um 1 zu erhöhen. Wenn der Server erkennt, dass der Zählerwert kleiner als der vom Server zuletzt angezeigte Wert ist, wurde der Clientstatus möglicherweise zurückgesetzt. Weitere Informationen zur Fehlererkennung für Client-Status finden Sie in der `ClientState` API-Referenzdokumentation.
