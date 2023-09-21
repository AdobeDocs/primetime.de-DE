---
title: Fehlerbehebung und Fehlerbehebung
description: Fehlerbehebung und Fehlerbehebung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 0%

---

# Fehlerbehebung und Fehlerbehebung {#troubleshooting-debugging}

Primetime Ad Insertion bietet Tools zur Identifizierung und Diagnose von Problemen, die in allen Phasen der Videobereitstellung auftreten können, z. B. CDN-Versandfehler, kreative Fehler oder Fehler bei der Clientverbindung.

Primetime Ad Insertion unterstützt die ausführliche Protokollierung über [Bootstrap-API-Parameter](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md) `ptdebug=true` oder `ptdebug=AdCall` zur Bootstrap-URL. Protokolle werden sowohl an HTTP-Antwortheader als auch an die Primetime-Ad Insertion-Konsole ausgegeben. Dieser Parameter ist nur für lokalisierte Tests vorgesehen, nicht für Produktions-Streams. Weitere Informationen zu Nachrichtentypen bei Aktivierung der ausführlichen Protokollierung finden Sie unter [Protokollierungsereignisse in ausführlicher Protokollierung debuggen](verbose-logging.md#ptdebug-logging-events).

Mit der X-ADBE-AI-X1-Kopfzeile bietet Primetime Ad Insertion außerdem Performance-Debugging für alle Anforderungen, mit dem die Leistung und Anzeigeneinfügungen bei jeder beliebigen Anfrage gemessen werden können. Dieser Anfrage-Header ist unabhängig davon verfügbar, ob die ausführliche Protokollierung aktiviert ist. Weitere Informationen finden Sie unter [Verbose-Header: X-ADBE-PTAI-X1](debugging-headers.md).
