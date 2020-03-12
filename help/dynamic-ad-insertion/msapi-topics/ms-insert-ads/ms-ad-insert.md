---
description: Alle Anforderungen zum Einfügen von Anzeigen verwenden dieselbe URL-Struktur und dieselben grundlegenden Parameter für die Abfrage. Zusätzliche Parameter für die Abfrage ermöglichen es dem Manifestserver, mit einer Vielzahl von Clients und Situationen zu arbeiten.
seo-description: Alle Anforderungen zum Einfügen von Anzeigen verwenden dieselbe URL-Struktur und dieselben grundlegenden Parameter für die Abfrage. Zusätzliche Parameter für die Abfrage ermöglichen es dem Manifestserver, mit einer Vielzahl von Clients und Situationen zu arbeiten.
seo-title: Anfragen zum Einfügen von Werbeanzeigen
title: Anfragen zum Einfügen von Werbeanzeigen
uuid: e42b3228-bff7-4202-86ed-7f631f3016ae
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Anfragen zum Einfügen von Werbeanzeigen {#requests-for-ad-insertion}

Alle Anforderungen zum Einfügen von Anzeigen verwenden dieselbe URL-Struktur und dieselben grundlegenden Parameter für die Abfrage. Zusätzliche Parameter für die Abfrage ermöglichen es dem Manifestserver, mit einer Vielzahl von Clients und Situationen zu arbeiten.

| Parameter | Beschreibung |
|--- |--- |
| u | Die Asset-ID ist ein MD5-Hash der Metadaten ad_request_id aus den Adobe Primetime-Anzeigenentscheidungsmetadaten. Wird von Ihrem Adobe Technical Account Manager bereitgestellt. |
| z | Die Zonen-ID für das Asset, das für Auditude bereitgestellt werden muss. Wird von Ihrem Adobe Technical Account Manager bereitgestellt. |
| `__sid__` | Eine eindeutige ID, die vom Manifestserver zum Generieren der Sitzungs-ID verwendet wird. |

>[!NOTE]
>
>Der `__sid__` Parameter ist von Unterstrich-Zeichen der Dublette umgeben.

Der Manifestserver unterhält Sitzungen für einzelne Clients oder Gruppen von Clients, um sicherzustellen, dass die Sequenzen der API-Interaktionen für verschiedene Clients getrennt bleiben. Der `__sid__` vom Client in der Bootstrap-URL an den Manifestserver gesendete Wert sollte innerhalb seiner Umgebung eindeutig sein. Der Manifestserver verwendet ihn, um eine global eindeutige ID zu erstellen, die er an den Client zurückgibt.

Die verbleibenden Parameter für die Abfrage beziehen sich auf verschiedene Clients und Situationen.