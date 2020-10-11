---
title: Anzeigen-Server integrieren
description: Integration des Anzeigen-Servers
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Anzeigen-Server integrieren {#integrate-ad-server}

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

<!--For technical information regarding specific ad servers or ad macros, see [Supported ad servers and macros](supported-ad-servers-and-macros.md).-->

Falls weitere Makros erforderlich sind, wenden Sie sich an Ihren Adobe Primetime Support-Mitarbeiter.

## Erweiterte Funktionen {#advanced-features}

Primetime Ad Insertion bietet außerdem regelbasierte Entscheidungsfunktionen, die erweiterte Funktionen ermöglichen. Dies kann wichtig sein, wenn Sie Anzeigen basierend auf Lagerbestandsrechten an verschiedene Werbeserver weiterleiten oder die Frequenzgrenze für einzelne Anzeigen aktivieren möchten. <!--For more information, see [Advanced Features](route-ads-based-on-rules.md).-->
