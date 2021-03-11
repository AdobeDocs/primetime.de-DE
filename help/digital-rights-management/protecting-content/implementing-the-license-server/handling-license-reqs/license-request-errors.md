---
title: Verarbeitung von Lizenzanfragefehlern
description: Verarbeitung von Lizenzanfragefehlern
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Verarbeitung von Lizenzanforderungsfehlern {#license-request-error-handling}

Tritt bei der Anforderungsanalyse ein Fehler auf, tritt ein `HandlerParsingException` auf. Diese Ausnahme enthält Fehlerinformationen, die an den Client zurückgegeben werden. Wenn Sie die Fehlerinformationen abrufen müssen, müssen Sie `HandlerParsingException.getErrorData()` aufrufen. Tritt während der Generierung einer Lizenz aufgrund von DRM-Richtlinienanforderungen, die nicht erfüllt wurden, ein Fehler auf, tritt ein `PolicyEvaluationException` auf. Diese Ausnahme umfasst auch `ErrorData`, die an den Client zurückgegeben werden.

Weitere Informationen dazu, wie DRM-Richtlinien während der Lizenzerstellung bewertet werden, finden Sie in der API-Dokumentation für `LicenseRequestMessage.generateLicense()`.
