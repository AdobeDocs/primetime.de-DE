---
seo-title: Verarbeitung von Lizenzanfragefehlern
title: Verarbeitung von Lizenzanfragefehlern
uuid: 4563f546-77fe-4fb9-9ad8-a0689fe6fb4d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---


# Verarbeitung von Lizenzanforderungsfehlern {#license-request-error-handling}

Tritt bei der Anforderungsanalyse ein Fehler auf, tritt ein `HandlerParsingException` auf. Diese Ausnahme enthält Fehlerinformationen, die an den Client zurückgegeben werden. Wenn Sie die Fehlerinformationen abrufen müssen, müssen Sie `HandlerParsingException.getErrorData()` aufrufen. Tritt während der Generierung einer Lizenz aufgrund von DRM-Richtlinienanforderungen, die nicht erfüllt wurden, ein Fehler auf, tritt ein `PolicyEvaluationException` auf. Diese Ausnahme umfasst auch `ErrorData`, die an den Client zurückgegeben werden.

Weitere Informationen dazu, wie DRM-Richtlinien während der Lizenzerstellung bewertet werden, finden Sie in der API-Dokumentation für `LicenseRequestMessage.generateLicense()`.
