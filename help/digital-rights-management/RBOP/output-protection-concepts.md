---
description: Dieser Abschnitt bietet einen konzeptionellen Überblick über die Konfiguration, Optionen und Bedeutungen im Zusammenhang mit dem Ausgabeschutz.
seo-description: Dieser Abschnitt bietet einen konzeptionellen Überblick über die Konfiguration, Optionen und Bedeutungen im Zusammenhang mit dem Ausgabeschutz.
seo-title: RBOP-Konzepte
title: RBOP-Konzepte
uuid: fc19c3c9-39a1-4b62-b763-101e5454a01f
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# RBOP-Konzepte {#rbop-concepts}

Dieser Abschnitt bietet einen konzeptionellen Überblick über die Konfiguration, Optionen und Bedeutungen im Zusammenhang mit dem Ausgabeschutz.

Sie legen Ihre auflösungsbasierten Ausgabeschutzanforderungen in einer hierarchischen JSON-Struktur fest. *Die Ausgabeanforderungen sind pixelbasiert.*

Auf der höchsten Ebene der JSON-Spezifikation können Sie maximale Pixelauflösung und Pixeleinschränkungen für bestimmte Auflösungen definieren:

* `maxPixel` - Die maximale Pixelauflösung definiert die maximale Auflösung für die Entschlüsselung.
* `pixelConstraints` - Pixeleinschränkungen definieren Ausgabeanforderungen, die für eine bestimmte Auflösung erzwungen werden müssen.

Sie verbinden Ausgabeanforderungen mit bestimmten Pixelbeschränkungen. Zu den Anforderungen, die Sie mit einer bestimmten Pixelbeschränkung verknüpfen können, zählen Einschränkungen für digitale, analoge und OTA-Verbindungen (Over-the-Air).

**Digitale Ausgabe**

Die Anforderung für die digitale Ausgabe kann restriktive Optionen festlegen, z. B. &quot;Digitalausgabeschutz erforderlich&quot;oder &quot;Wiedergabe ist nicht zulässig&quot;. In den Ausgabeanforderungen können auch weniger restriktive Optionen festgelegt werden, z. B. &quot;Es sollte kein Schutz angewendet werden&quot;oder &quot;Digitaler Schutz sollte verwendet werden, wenn er verfügbar ist&quot;.

**Analogausgabe**

Analoge Ausgangsverbindungen sind einfacher als die digitale Ausgabe. sie bestehen aus einer einzigen Ausgabeanforderung.
