---
title: Umgang mit Fehlern bei Lizenzanfragen
description: Umgang mit Fehlern bei Lizenzanfragen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Umgang mit Fehlern bei Lizenzanfragen {#license-request-error-handling}

Wenn beim Analysieren von Anforderungen ein Fehler auftritt, wird eine `HandlerParsingException` auftritt. Diese Ausnahme umfasst Fehlerinformationen, die an den Client zurückgegeben werden. Wenn Sie die Fehlerinformationen abrufen müssen, müssen Sie `HandlerParsingException.getErrorData()`. Tritt während der Lizenzerstellung ein Fehler auf, weil die DRM-Richtlinienanforderungen nicht erfüllt wurden, wird ein `PolicyEvaluationException` auftritt. Diese Ausnahme umfasst auch `ErrorData` an den Client zurückgegeben.

Siehe API-Dokumentation für `LicenseRequestMessage.generateLicense()` für Details dazu, wie DRM-Richtlinien bei der Lizenzerstellung bewertet werden.
