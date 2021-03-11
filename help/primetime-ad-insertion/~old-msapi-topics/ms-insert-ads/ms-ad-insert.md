---
description: Alle Anforderungen zum Einfügen von Anzeigen verwenden dieselbe URL-Struktur und dieselben grundlegenden Parameter für die Abfrage. Zusätzliche Parameter für die Abfrage ermöglichen es dem Manifestserver, mit einer Vielzahl von Clients und Situationen zu arbeiten.
title: Anfragen zum Einfügen von Werbeanzeigen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---


# Anfragen zur Anzeigeneinfügung {#requests-for-ad-insertion}

Alle Anforderungen zum Einfügen von Anzeigen verwenden dieselbe URL-Struktur und dieselben grundlegenden Parameter für die Abfrage. Zusätzliche Parameter für die Abfrage ermöglichen es dem Manifestserver, mit einer Vielzahl von Clients und Situationen zu arbeiten.

| Parameter | Beschreibung |
|--- |--- |
| u | Die Asset-ID ist ein MD5-Hash der Ad_request_id aus den Adobe Primetime-Metadaten zur Anzeigenentscheidung. Wird von Ihrem technischen Kundenbetreuer für Adobe bereitgestellt. |
| z | Die Zonen-ID für das Asset, das für Auditude bereitgestellt werden muss. Wird von Ihrem technischen Kundenbetreuer für Adobe bereitgestellt. |
| `__sid__` | Eine eindeutige ID, die vom Manifestserver zum Generieren der Sitzungs-ID verwendet wird. |

>[!NOTE]
>
>Der Parameter `__sid__` ist von Unterstrich-Zeichen der Dublette umgeben.

Der Manifestserver unterhält Sitzungen für einzelne Clients oder Gruppen von Clients, um sicherzustellen, dass die Sequenzen der API-Interaktionen für verschiedene Clients getrennt bleiben. Das `__sid__`, das der Client in der Bootstrap-URL an den Manifestserver sendet, sollte innerhalb seiner Umgebung eindeutig sein. Der Manifestserver verwendet ihn, um eine global eindeutige ID zu erstellen, die er an den Client zurückgibt.

Die verbleibenden Parameter für die Abfrage beziehen sich auf verschiedene Clients und Situationen.