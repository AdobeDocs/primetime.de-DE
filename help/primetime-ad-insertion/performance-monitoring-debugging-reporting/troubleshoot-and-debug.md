---
title: Fehlerbehebung und Debugging
description: null
translation-type: tm+mt
source-git-commit: 242b5a2875ebc0e0020296ce9489dd54438b5ad0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Fehlerbehebung und Debugging {#troubleshooting-debugging}

Primetime-Ad Insertion-Angebot-Tools zur Erkennung und Diagnose von Problemen, die in allen Phasen des Video-Versands auftreten können, z. B. CDN-Versand-Fehler, Kreativfehler oder Clientverbindungsfehler.

Primetime Ad Insertion unterstützt die ausführliche Protokollierung über den [Bootstrap-API-Parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` oder `ptdebug=AdCall` zur Bootstrap-URL. Protokolle werden sowohl an HTTP-Antwort-Kopfzeilen als auch an die Primetime Ad Insertion-Konsole ausgegeben. Dieser Parameter ist nur für lokalisierte Tests gedacht, nicht für Produktionsströme. Weitere Informationen zu Meldungstypen, wenn die ausführliche Protokollierung aktiviert ist, finden Sie unter [ptdebug-Protokollierungs-Ereignis in der ausführlichen Protokollierung](verbose-logging.md#ptdebug-logging-events).

Primetime Ad Insertion bietet auch Performance-Debugging für alle Anforderungen mit dem X-ADBE-AI-X1 Header, der zur Messung der Performance und Anzeigeneinfügungen bei jeder Anforderung verwendet werden kann. Dieser Anforderungsheader ist unabhängig davon verfügbar, ob die ausführliche Protokollierung aktiviert ist. Weitere Informationen finden Sie unter [Ausführliche Kopfzeilen: X-ADBE-PTAI-X1](debugging-headers.md).
