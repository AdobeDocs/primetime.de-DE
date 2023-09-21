---
description: Dieser Abschnitt bietet einen konzeptionellen Überblick über die Konfiguration, Optionen und Bedeutungen im Zusammenhang mit dem Ausgabeschutz.
title: RBOP-Konzepte
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# RBOP-Konzepte {#rbop-concepts}

Dieser Abschnitt bietet einen konzeptionellen Überblick über die Konfiguration, Optionen und Bedeutungen im Zusammenhang mit dem Ausgabeschutz.

Sie legen Ihre auflösungsbasierten Ausgabeschutzanforderungen in einer hierarchischen JSON-Struktur fest. *Die Ausgabeanforderungen sind pixelbasiert.*

Auf der höchsten Ebene der JSON-Spezifikation können Sie die maximale Pixelauflösung und Pixelbegrenzungen für bestimmte Auflösungen definieren:

* `maxPixel` - Die maximale Pixelauflösung definiert die maximale Auflösung, für die eine Entschlüsselung vorgenommen wird.
* `pixelConstraints` - Pixelbeschränkungen definieren Ausgabeanforderungen, die für eine bestimmte Auflösung erzwungen werden müssen.

Sie verknüpfen Ausgabeanforderungen mit bestimmten Pixelbeschränkungen. Die Arten von Anforderungen, die Sie mit einer bestimmten Pixelbegrenzung verknüpfen können, umfassen Einschränkungen für digitale, analoge und OTA-Verbindungen (Over-the-Air).

**Digitale Ausgabe**

Die digitale Ausgabeanforderung kann restriktive Optionen festlegen, z. B. &quot;Digital Output Protection ist erforderlich&quot;oder &quot;Play-back ist nicht erlaubt&quot;. In den Ausgabeanforderungen können auch weniger restriktive Optionen festgelegt werden, z. B. &quot;kein Schutz sollte angewendet werden&quot;oder &quot;digitaler Schutz sollte verwendet werden, wenn er verfügbar ist&quot;.

**Analog Output**

Analog-Ausgabeverbindungen sind einfacher als die digitale Ausgabe; sie bestehen aus einer einzigen Ausgabeanforderung.
