---
seo-title: Ausgabenschutzkontrollen
title: Ausgabenschutzkontrollen
uuid: a0518392-cd33-4ef0-834c-f90145a9b421
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Ausgabenschutzkontrollen{#output-protection-controls}

Der Parameter für Ausgabeschutz steuert, ob die Ausgabe auf externen Renderinggeräten geschützt ist. Sie können Beschränkungen für analoge und digitale Ausgaben unabhängig voneinander festlegen.

Steuert, ob die Ausgabe auf externe Renderinggeräte eingeschränkt werden soll. Ein externes Gerät ist definiert als ein Video- oder Audiogerät, das nicht in den Computer eingebettet ist. Integrierte Displays, z. B. in Notebooks, werden im Szenario mit Ausgabeschutzsteuerelementen nicht als extern betrachtet.

Über die Luft (OTA) sind Verbindungstypen standardmäßig auf der Blacklist, können aber bei Bedarf explizit auf die Positivliste gesetzt werden. Zu den unterstützten OTA-Verbindungen zählen: Miracast, AirPlay, DLNA und WIDI.

**Auflösungsbasierter Ausgabeschutz: (Ab Version 5.3 verfügbar.) ** Dies bietet einen Ausgabeschutz, der auf der vertikalen Pixelanzahl des Inhalts basiert, sodass verschiedene Schutzanforderungen basierend auf der Anzahl der vertikalen Pixel festgelegt werden können.

Die folgenden Optionen/Ebenen der Durchsetzung stehen zur Verfügung:

| Option | In Analoggeräten unterstützt | In digitalen Geräten unterstützt |
|---|---|---|
| **Erforderlich** — Der Ausgabeschutz für Analog Copy Copy Protection (AKP) oder Copy Generation Management System - Analog (CGMS-A) muss aktiviert sein, damit Inhalte auf einem externen Gerät wiedergegeben werden können. Primetime-DRM-Clients müssen Ausgabeschutz mit AKP oder CGMS-A aktivieren. Auf Geräten, die beide unterstützen, versuchen die Primetime DRM 3.0-Clients beides zu aktivieren. Für die Wiedergabe des Inhalts muss jedoch nur einer aktiviert sein. | JA | JA |
| **AKP erforderlich** — Der Schutz der AKP-Produktion ist erforderlich. Die Wiedergabe ist auf CGMS-A nicht zulässig. Primetime-DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Primetime-DRM 2.0-Client so, als ob die Option &quot;Keine Wiedergabe&quot;angegeben wurde. | JA | - |
| **Gegebenenfalls** verwenden — Versuchen Sie, den Schutz der AKP- und CGMS-A-Ausgabe zu aktivieren, falls verfügbar, und lassen Sie die Wiedergabe zu, falls nicht verfügbar. Primetime-DRM 3.0-Clients versuchen, nach Möglichkeit sowohl AKP- als auch CGMS-A zu aktivieren. Primetime-DRM 2.0-Clients versuchen nur, AKP oder CGMS-A zu aktivieren. So wird beispielsweise vom Primetime DRM-Client versucht, entweder AKP oder CGMS-A zu aktivieren. Wenn der Versuch erfolgreich ist, kann die andere Option nicht aktiviert werden. Wenn der Versuch fehlschlägt, wird ein zweiter Versuch unternommen, die andere Option zu aktivieren. Auch wenn beide Versuche fehlschlagen, wird der Inhalt trotzdem wiedergegeben. | JA | JA |
| **AKP verwenden, falls verfügbar** — Versuchen Sie, den Schutz der AKP-Ausgabe zu aktivieren, wenn diese verfügbar ist, aber die Wiedergabe zu ermöglichen, wenn nicht verfügbar. Der Schutz ist auf CGMS-A nicht verfügbar. Primetime-DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Primetime DRM 2.0-Client so, als wäre die Option &quot;Kein Schutz&quot;angegeben worden. | JA | - |
| **Verwenden Sie CGMS-A, falls verfügbar **— Versuchen Sie, den Schutz der CGMS-A-Ausgabe zu aktivieren, wenn dieser verfügbar ist, lassen Sie die Wiedergabe jedoch zu, falls nicht verfügbar. Für AKP-Staaten ist kein Schutz verfügbar. Primetime-DRM 2.0-Clients unterstützen diese Option nicht. Wenn diese Einstellung aktiviert ist, verhält sich ein Primetime DRM 2.0-Client so, als wäre die Option &quot;Kein Schutz&quot;angegeben worden. | JA | - |
| **Kein Schutz** — Für analoge und digitale Ausgaben wird keine Ausgabeschutzaktivierung erzwungen. | JA | JA |
| **Keine Wiedergabe** — Die Wiedergabe auf einem externen Gerät für analoge und digitale Ausgaben nicht zulassen. | JA | JA |

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, können Sie den Ausgabeschutz nur auf Windows-Plattformen sicher aktivieren. Auf anderen Plattformen wie Macintosh und Linux stehen keine unterstützenden Betriebssystemfunktionen für Anwendungen von Drittanbietern zur Verfügung.

Verwendungsbeispiel: Manche Inhalte können Ausgabeschutzkontrollen durchsetzen, sodass der Content-Distributor das Schutzniveau festlegen kann. Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe auf einem Macintosh versucht wird, gibt der Client keine Inhalte auf externen Geräten wieder. Der Inhalt kann auf internen Monitoren wiedergegeben werden.

Wenn &quot;Erforderlich&quot;angegeben ist und die Wiedergabe unter Linux versucht wird, gibt der Client keine Inhalte auf Geräten wieder, da er nicht zwischen internen und externen Geräten unterscheiden kann.

Wenn Sie &quot;Falls verfügbar verwenden&quot;angeben, wird der Ausgabeschutz nach Möglichkeit aktiviert. Beispielsweise wird der Inhalt auf Windows-Systemen, die das zertifizierte Output Protection Protocol (COPP) unterstützen, mit Ausgabeschutz an eine externe Anzeige übergeben. Dieses Beispiel wird manchmal auch als *`selectable output control`*.
