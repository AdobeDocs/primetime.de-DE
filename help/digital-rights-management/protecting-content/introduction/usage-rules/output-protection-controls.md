---
title: Ausgabeschutzelemente
description: Ausgabeschutzelemente
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Ausgabeschutzelemente{#output-protection-controls}

Der Ausgabeschutzparameter steuert, ob die Ausgabe auf externe Rendering-Geräte geschützt ist. Sie können Einschränkungen für analoge und digitale Ausgaben unabhängig voneinander festlegen.

Steuert, ob die Ausgabe auf externe Rendering-Geräte beschränkt werden soll. Ein externes Gerät ist definiert als ein Video- oder Audiogerät, das nicht in den Computer eingebettet ist. Integrierte Anzeigen, wie z. B. in Notebook-Computern, werden im Szenario mit den Ausgabeschutzsteuerungen nicht als extern betrachtet.

Die Verbindungstypen über der Luft (OTA) sind standardmäßig alle blockiert, können jedoch bei Bedarf explizit aufgeführt werden. Zu den unterstützten OTA-Verbindungen gehören: Miracast, AirPlay, DLNA und WIDI.

**Auflösungsbasierter Ausgabeschutz: (ab Version 5.3 verfügbar.) ** Dies bietet einen Ausgabeschutz, der auf der vertikalen Pixelanzahl des Inhalts basiert und es ermöglicht, verschiedene Schutzanforderungen basierend auf vertikalen Pixelzahlen anzugeben.

Die folgenden Optionen/Durchsetzungsebenen sind verfügbar:

| Option | In Analoggeräten unterstützt | In digitalen Geräten unterstützt |
|---|---|---|
| **Erforderlich** — Der Ausgabeschutz für Analog Copy Copy Protection (AKP) oder Copy Generation Management System - Analog (CGMS-A) muss aktiviert sein, damit Inhalte auf einem externen Gerät wiedergegeben werden können. Primetime DRM-Clients müssen den Output Protection mithilfe von AKP oder CGMS-A aktivieren. Auf Geräten, die beide unterstützen, versuchen die Primetime DRM 3.0-Clients beide zu aktivieren. Die Wiedergabe des Inhalts darf jedoch nur von einer aktiviert sein. | JA | JA |
| **AKP erforderlich** — Der Schutz der AKP-Produktion ist erforderlich. Die Wiedergabe ist auf CGMS-A nicht zulässig. Primetime DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Primetime-DRM 2.0-Client so, als ob die Option &quot;Keine Wiedergabe&quot;angegeben wurde. | JA | - |
| **Verwendung, falls verfügbar** — Versuchen Sie, den Schutz der AKP- und CGMS-A-Ausgabe zu aktivieren, falls verfügbar, und die Wiedergabe zu ermöglichen, falls nicht verfügbar. Primetime DRM 3.0-Clients versuchen, nach Möglichkeit sowohl AKP als auch CGMS-A zu aktivieren. Primetime DRM 2.0-Clients versuchen nur, AKP oder CGMS-A zu aktivieren. Beispielsweise wird vom Primetime-DRM-Client versucht, entweder AKP oder CGMS-A zu aktivieren. Wenn der Versuch erfolgreich ist, kann die andere Option nicht aktiviert werden. Wenn der Versuch fehlschlägt, wird ein zweiter Versuch unternommen, die andere Option zu aktivieren. Selbst wenn beide Versuche fehlschlagen, wird der Inhalt trotzdem wiedergegeben. | JA | JA |
| **AKP verwenden, falls verfügbar** — Versuchen Sie, den Schutz der AKP-Ausgabe zu aktivieren, sofern verfügbar, aber die Wiedergabe zu ermöglichen, falls nicht verfügbar. Der Schutz ist bei CGMS-A nicht verfügbar. Primetime DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Primetime-DRM 2.0-Client so, als wäre die Option &quot;Kein Schutz&quot;angegeben. | JA | - |
| **Verwenden Sie CGMS-A, falls verfügbar **— Versuchen Sie, den CGMS-A-Ausgabeschutz zu aktivieren, sofern verfügbar, aber die Wiedergabe zu ermöglichen, wenn nicht verfügbar. Der Schutz der AKP-Staaten ist nicht möglich. Primetime DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Option festgelegt ist, verhält sich ein Primetime-DRM 2.0-Client so, als wäre die Option &quot;Kein Schutz&quot;angegeben. | JA | - |
| **Kein Schutz** — Für analoge und digitale Ausgaben wird keine Aktivierung zum Schutz der Ausgabe erzwungen. | JA | JA |
| **Keine Wiedergabe** — Die Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben nicht zulassen. | JA | JA |

>[!NOTE]
>
>Diese Regeln werden zwar durchgängig auf allen Plattformen durchgesetzt, Sie können jedoch den Ausgabeschutz nur auf Windows-Plattformen sicher aktivieren. Auf anderen Plattformen wie Macintosh und Linux stehen für Anwendungen von Drittanbietern keine unterstützenden Betriebssystemfunktionen zur Verfügung.

Anwendungsbeispiel: Manche Inhalte können Ausgabeschutzkontrollen durchsetzen und daher kann der Inhaltsanbieter das Schutzniveau festlegen. Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe auf einem Macintosh versucht wird, gibt der Client keine Inhalte auf externen Geräten wieder. Der Inhalt kann auf internen Monitoren wiedergegeben werden.

Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe unter Linux versucht wird, gibt der Client keine Inhalte auf Geräten wieder, da keine Unterscheidung zwischen internen und externen Geräten möglich ist.

Wenn Sie &quot;Wenn verfügbar verwenden&quot;angeben, wird der Ausgabeschutz nach Möglichkeit aktiviert. Auf Windows-Systemen, die das Certified Output Protection Protocol (COPP) unterstützen, wird der Inhalt beispielsweise mit Ausgabeschutz an eine externe Anzeige übergeben. Dieses Beispiel wird manchmal auch als *`selectable output control`*.
