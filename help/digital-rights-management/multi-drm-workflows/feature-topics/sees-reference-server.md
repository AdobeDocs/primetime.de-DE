---
description: Eine Möglichkeit, die Lizenzierung und Richtliniendurchsetzung zu koordinieren, besteht darin, diese Funktionen in einem Berechtigungsserver zu erstellen. Adobe stellt den SEES-Referenz-Berechtigungsserver bereit, mit dem Sie Ihren eigenen Server erstellen können.
title: 'Referenz-Server-Beispiel: ExpressPlay-Berechtigungsserver (SIES)'
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Referenz-Server: Beispiel für ExpressPlay Entitlement Server (SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

Eine Möglichkeit, die Lizenzierung und Richtliniendurchsetzung zu koordinieren, besteht darin, diese Funktionen in einem Berechtigungsserver zu erstellen. Adobe stellt den SEES-Referenz-Berechtigungsserver bereit, mit dem Sie Ihren eigenen Server erstellen können.

Der Referenz-Server SEES veranschaulicht den ExpressPlay-Berechtigungsdienst, der zwei Dienste anzeigt: grundlegende zeitbasierte Berechtigung und Gerätebindungsberechtigung.

Die SEES basiert auf zwei ExpressPlay Fairplay Services:

1. Request-Dienst für Expressions-Token
1. Abrufen von Ausdrucksdatensätzen

Das URL-Format für die Anfrage &quot;ExpressPlay Token&quot;akzeptiert zwei Formulare: eine für die Produktion und eine für die Testumgebung:

**Produktion**: ht<span></span>tps://fp-gen{prod_domain}/hms/fp/token

**Test**: ht<span></span>tps://fp-gen.test.expressplay.com/hms/fp/token

Das URL-Format für das Abrufen von ExpressPlay-Datensätzen nimmt zwei Formen an: eine für die Produktion und eine für die Testumgebung:

**Produktion**: ht<span></span>tps://api{prod_domain}/cmiapi/getrecord/

**Test**: ht<span></span>tps://api.test.expressplay.com/cmiapi/getrecord/
