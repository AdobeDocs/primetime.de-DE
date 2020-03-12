---
description: Eine Möglichkeit zur Koordinierung der Lizenzierung und Durchsetzung von Richtlinien besteht darin, diese Funktionen in einem Berechtigungsserver zu erstellen. Adobe stellt den SEES-Referenz-Berechtigungsserver bereit, mit dem Sie Ihren eigenen Server erstellen können.
seo-description: Eine Möglichkeit zur Koordinierung der Lizenzierung und Durchsetzung von Richtlinien besteht darin, diese Funktionen in einem Berechtigungsserver zu erstellen. Adobe stellt den SEES-Referenz-Berechtigungsserver bereit, mit dem Sie Ihren eigenen Server erstellen können.
seo-title: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES)
title: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES)
uuid: 99e42f76-7730-42fc-a9a9-f6396ac12c02
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Referenz-Server: Beispiel für einen ExpressPlay-Berechtigungsserver (SEES) {#reference-server-sample-expressplay-entitlement-server-sees}

Eine Möglichkeit zur Koordinierung der Lizenzierung und Durchsetzung von Richtlinien besteht darin, diese Funktionen in einem Berechtigungsserver zu erstellen. Adobe stellt den SEES-Referenz-Berechtigungsserver bereit, mit dem Sie Ihren eigenen Server erstellen können.

Der Referenz-Server SEES zeigt den ExpressPlay Entitlement Service an, der zwei Dienste anzeigt: Grundlegende zeitbasierte Berechtigung und Gerätebindungsberechtigung.

Das SEES basiert auf zwei ExpressPlay Fairplay Services:

1. Anforderungsdienst für Ausdrücken-Token
1. Dienst zum Abrufen von Ausdrucksdatensätzen

Das URL-Format für die ExpressPlay-Token-Anforderung besteht aus zwei Formularen: einem für die Produktion und einem für die Test-Umgebung:

**Produktion**:<span></span>https://fp-gen.{prod_domain}/hms/fp/token

**Test**:<span></span>https://fp-gen.test.expressplay.com/hms/fp/token

Das URL-Format für den ExpressPlay-Record-Abruf besteht aus zwei Formularen: einem für die Produktion und einem für die Test-Umgebung:

**Produktion**:<span></span>https://api.{prod_domain}/cmiapi/getrecord/

**Test**:<span></span>https://api.test.expressplay.com/cmiapi/getrecord/
