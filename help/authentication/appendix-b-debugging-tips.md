---
title: Anhang B "Tipps zum Debuggen"
description: Anhang B "Tipps zum Debuggen"
exl-id: ea024797-315e-47c0-99ea-1ac49c8c9697
source-git-commit: 84a16ce775a0aab96ad954997c008b5265e69283
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Anhang B: Tipps zum Debugging {#appendix-b-debugging-tips}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.


## Löschen temporärer Daten {#clearing-temporary-data}

Die Adobe Primetime-Authentifizierung speichert temporäre Daten wie Browsercache, LSO-Cache und Cookies. Das Löschen temporärer Daten ist wichtig, um sicherzustellen, dass Sie beim Testen eine saubere Verzögerung erhalten.

- [Löschen des Browser-Caches und der Cookies](#clearing-the-browser-cache-and-cookies)
- [Löschen des LSO-Cache](#clearing-lsos-cache)


## Löschen des Browser-Caches und der Cookies {#clearing-the-browser-cache-and-cookies}

Es ist browserabhängig, aber in Firefox: &quot;Tools&quot;-\> &quot;Letzten Verlauf löschen...&quot;-\> In &quot;Zeitbereich zum Löschen:&quot;wählen Sie &quot;Alles&quot;; und auf &quot;Details&quot;: &quot;Cookies&quot;und &quot;Cache&quot;-\> Klicken Sie auf &quot;Jetzt löschen&quot;.


## Löschen des LSO-Cache {#clearing-lsos-cache}

Zugriff auf [Flash Player-Hilfe](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html).

Wählen Sie die ```entitlement.\*``` (je nachdem, was getestet wird) und klicken Sie auf &quot;Website löschen&quot;.


## Debugging-Tools {#tools}

Adobe Primetime-Authentifizierungstechniken verwenden die folgenden Debugging-Tools:

- Firebug - <http://www.getfirebug.com/>
- Flashbug (funktioniert mit der Debug-Version des Flash-Players)
- Fiddler - <http://www.fiddler2.com/fiddler2/>
- Charles - <http://www.charlesproxy.com/>
- Wireshark - <http://www.wireshark.org/>


<!--
## Related Information

- [Programmer Integration Guide](/help/authentication/programmer-integration-guide-overview.md)

- [Using Charles Proxy (Tech Note)](https://tve.zendesk.com/hc/en-us/articles/204962849-Using-Charles-Proxy)
-->
