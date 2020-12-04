---
seo-title: BET-Fehlercodes
title: BET-Fehlercodes
uuid: 7b2d0dd1-9a43-47e3-b932-a4eaf784ae7a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---


# BEES-Fehlercodes {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

Wenn während einer BEES-Prüfung ein Fehler auftritt, wird ein `DRMErrorEvent` an den Client zurückgegeben. Sie können die Eigenschaften dieses Ereignisses analysieren, um Details zur Art des Fehlers zu finden. Nachfolgend sind einige mögliche Fehlercodes aufgeführt.

| Fehler | Beschreibung |
|---|---|
| `3304:305` | Allgemeiner Autorisierungsfehler von Primetime Cloud DRM, der versucht, eine Authentifizierungs-/Autorisierungsanfrage zu bearbeiten. Normalerweise nicht mit einem BEES-Problem verbunden. Wenn dieser Fehler immer wieder auftritt, sollten Sie eine Problemhilfe zusammen mit diagnostischen Informationen an das Primetime Cloud DRM-Team senden. |
| `3329:0` | Anwendungsspezifischer Fehler (vom BEES Authorizer). Wenn kein Unterfehlercode zurückgegeben wurde, zeigt der Fehlertext Details zum Problem an. Beispielsweise ist beim Analysieren der Antwort ein Fehler aufgetreten, oder der BEES-Server war unerreichbar. |
| `3329:<HTTP error code>` | Eine andere HTTP-Antwort als 200 wurde vom BEES-Server ausgegeben. Der HTTP-Fehlercode wird an den Client im Feld des Unterschriftscodes zurückgegeben. Dies könnte auf ein Konfigurationsproblem oder einen BEES-Serverausfall hindeuten. |
| `3329:<x>` | DER BEES-Server HAT DIE Lizenzanforderung DEALLOWIERT. Der Unterfehlercode und der Fehlertext werden vom BEES-Server in den Eigenschaften `error` und `errorText` der JSON-Antwort angegeben. Diese Art von Antwort sollte nicht als Fehler betrachtet werden, sondern als regelmäßige Ablehnung durch Ihren BEES-Server. |