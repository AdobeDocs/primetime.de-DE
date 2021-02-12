---
title: Anzeigen-Server integrieren
description: Integration des Anzeigen-Servers
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Anzeigen-Server {#integrate-ad-server} integrieren

Für den Beginn erhalten Sie eine Anmeldung für den Zugriff auf die Primetime Ad Insertion Console, in der Sie Regeln einrichten, die Primetime Ad Insertion verwendet, um Anzeigenanforderungen an den von Ihnen gewählten Anzeigen-Server zu senden. Primetime Ad Insertion unterstützt die meisten VAST- oder VMAP-kompatiblen Anzeigen-Server.

>[!NOTE]
>
>[IAB VAST-Seite](https://www.iab.com/guidelines/digital-video-ad-serving-template-vast)

## Makrounterstützung {#macro-support}

Primetime Ad Insertion aktiviert die folgenden Anzeigenservermakros für alle Streams:

* Cache-Busting
* Anwendungskontext oder Seiten-URL
* durchschnittliche Dauer
* Aktuelles Videoelement

Falls weitere Makros erforderlich sind, wenden Sie sich an Ihren Adobe Primetime Support-Mitarbeiter.

## Erweiterte Funktionen {#advanced-features}

Primetime Ad Insertion bietet außerdem regelbasierte Entscheidungsfunktionen, die erweiterte Funktionen ermöglichen. Dies kann wichtig sein, wenn Sie Anzeigen basierend auf Lagerbestandsrechten an verschiedene Werbeserver weiterleiten oder die Frequenzgrenze für einzelne Anzeigen aktivieren möchten. Weitere Informationen finden Sie unter [Erweiterte Funktionen](/help/primetime-ad-insertion/advanced-features/route-ads-based-on-rules.md).
