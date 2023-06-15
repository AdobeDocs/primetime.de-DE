---
title: Versionshinweise zur Adobe Pass-Authentifizierung 2.65.1
description: Versionshinweise zur Adobe Pass-Authentifizierung 2.65.1
source-git-commit: c8259e3268556c20630fff92aa90b0f7f9c12617
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Versionshinweise zur Adobe Pass-Authentifizierung 2.65.1 {#authn-2651-rn}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Auf dieser Seite werden neue Funktionen, Änderungen und bekannte Probleme in dieser Version beschrieben:

## Server-seitige und Web-Clients {#server-side-web-clients-2651}

* [Build-Nummer](#build-number-2651)
* [Versionsübersicht](#release-overview-2651)

### Build-Nummer {#build-number-2651}

Adobe Pass-Authentifizierung: adobe-pass-**2,65,1**
Releasedatum: **20.6.2023 - 06.22.2023**

### Versionsübersicht {#release-overview-2651}

Diese Version fügt Folgendes hinzu:

Ab dieser Version bieten wir technischen Support für das Hinzufügen von Regeln zur Ratenbegrenzung für alle unsere APIs, um das gesamte Ökosystem vor falscher Nutzung zu schützen.

Das ursprüngliche Ziel besteht darin, das Verhalten der Anwendungen zu überwachen, um die richtigen Grenzwerte festzulegen, und im Rahmen dieser Version werden keine Beschränkungen angewendet. Für Fälle, in denen der durch eine bestimmte Anwendung generierte Traffic bestimmte Beschränkungen überschreitet, arbeiten wir mit jedem Kunden zusammen, um die Implementierung zu validieren.

Die Regeln zur Begrenzung der Rate werden Ende dieses Jahres angewendet, nachdem wir den aus allen Kundenanwendungen generierten Traffic validiert haben.
