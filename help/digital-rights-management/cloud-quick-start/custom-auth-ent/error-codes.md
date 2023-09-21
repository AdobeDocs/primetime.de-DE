---
title: BEES-Fehlercodes
description: BEES-Fehlercodes
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# BEES-Fehlercodes {#bees-error-codes}

<!--<a id="section_81946679E1114DBA9FE173D0AA9E2F09"></a>-->

Wenn bei einer BEES-Prüfung ein Fehler auftritt, wird ein `DRMErrorEvent` wird an den Client zurückgegeben. Sie können die Eigenschaften dieses Ereignisses analysieren, um Details zur Art des Fehlschlagens zu erhalten. Unten finden Sie eine Untergruppe möglicher Fehlercodes.

| Fehler | Beschreibung |
|---|---|
| `3304:305` | Allgemeiner Autorisierungsfehler von Primetime Cloud DRM, der versucht, eine Authentifizierungs-/Autorisierungsanfrage zu verarbeiten. In der Regel nicht mit einem BEES-Problem verknüpft. Wenn dieser Fehler konsistent auftritt, sollten Sie dem Primetime Cloud DRM-Team ein Problemticket mit Diagnoseinformationen senden. |
| `3329:0` | Anwendungsspezifischer Fehler (vom BEES Authorizer). Wenn kein Unterfehlercode zurückgegeben wurde, zeigt der Fehlertext Details zum Problem an. Beispielsweise ist beim Analysieren der Antwort ein Fehler aufgetreten oder der BEES-Server war nicht erreichbar. |
| `3329:<HTTP error code>` | Eine andere HTTP-Antwort als 200 wurde vom BEES-Server ausgegeben. Der HTTP-Fehlercode wird im Feld &quot;Unterschriftscode&quot;an den Client zurückgegeben. Dies könnte auf ein Konfigurationsproblem oder einen BEES-Serverausfall hinweisen. |
| `3329:<x>` | DER BEES-Server HAT DIE Lizenzanforderung DEALLOWIERT. Der Unterfehlercode und der Fehlertext werden vom BEES-Server innerhalb der JSON-Antwort `error` und `errorText` Eigenschaften. Diese Art von Antwort sollte nicht als Fehler betrachtet werden, sondern als regelmäßige Abweisungsantwort von Ihrem BEES-Server. |
