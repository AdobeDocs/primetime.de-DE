---
title: UltraViolet-Medien und Adobe Primetime DRM
description: UltraViolet-Medien und Adobe Primetime DRM
copied-description: true
exl-id: 03b01a29-e8e0-4fb5-a685-63a745a6417c
source-git-commit: d49042b559ce6083eca0738517d04c490755a033
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# UltraViolet-Medien und Adobe Primetime DRM {#ultraviolet-media-and-adobe-primetime-drm}

Adobe Primetime DRM kann mit anderen Content Streaming-Lösungen von Drittanbietern verwendet werden, um ein vollständiges und sicheres DRM-basiertes Medienverteilungs-Ökosystem einzurichten.

UltraViolet ist ein Digital Rights Authentication- und Cloud-basiertes Distributionssystem, das es Verbrauchern von Digital Home Entertainment-Inhalten ermöglicht, erworbene Inhalte über mehrere Plattformen und Geräte zu streamen und herunterzuladen. UltraViolet-Inhalte werden in einem Common File Format (CFF) mit Common Encryption (CENC) heruntergeladen (oder gestreamt).

Es ist einfach, ein UltraViolet-System zusammen mit Adobe Primetime DRM einzurichten. Das folgende Nutzungsszenario zeigt das Verhalten des Inhaltsflusses:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Der Inhaltseigentümer kodiert und packt den Inhalt in CFF. Der gepackte Inhalt ist für einen Einzelhändler zum Vertrieb lizenziert.
1. Der Einzelhändler lädt den Inhalt auf einen digitalen Dienstleister hoch, z. B. CDN. Der Inhalt kann jetzt heruntergeladen werden. Einige dieser Rollen können von einem oder mehreren Unternehmen gespielt werden.

   Der Endbenutzer verfügt über ein Gerät, das Adobe AIR unterstützt. Außerdem muss der Benutzer eine UltraViolet-kompatible Anwendung installieren. Die Anwendung enthält den erforderlichen Code, um den CFF zu analysieren und ihn zur Verwendung durch die Laufzeit darzustellen. Alle sensiblen kryptografischen Vorgänge werden in der sicheren Laufzeitumgebung verarbeitet.
1. Die Anwendung kann einen Domain-Join für das Gerät Trigger haben, der mit dem Koordinator interagiert. Der Koordinator unterhält einen Sperrer für Rechte, eine Benutzerdatenbank und Domänen. Der Domain-Manager des Koordinators wird mithilfe des Primetime DRM SDK erstellt, um Primetime-DRM-spezifische Domain-Join-/Urlaubsvorgänge zu implementieren.
1. Der Benutzer kann dann die Anwendung verwenden, um ein Video auszuwählen, das er vom Einzelhändler erwerben möchte. Der Einzelhändler stellt in der Regel ein Webportal bereit und übernimmt die gesamte Geschäftslogik.
1. Der Händler interagiert dann mit dem Koordinator, um ein Berechtigungstoken hinzuzufügen. Der Einzelhändler leitet die Anfrage dann an den Dienstleister für den tatsächlichen Download des Inhalts weiter.
1. Wenn das Gerät noch keine Lizenz für den Inhalt besitzt, wird eine Lizenzanforderung mit dem CFF Trigger. Die Anfrage umfasst in der Regel ein Domänenzertifikat, Benutzeranmeldeinformationen und Informationen zur Anwendung. Der Dienstleister betreibt einen Primetime DRM License Server (entwickelt mit dem Primetime DRM SDK), der den UltraViolet-Spezifikationen entspricht.
1. Die UltraViolet-Geschäftslogik des Dienstleisters interagiert bei Bedarf mit dem Koordinator, um das entsprechende Berechtigungstoken abzurufen und zu bestimmen, ob eine Inhaltslizenz ausgestellt werden soll.

   Die Inhaltslizenz ist an die Domäne gebunden. Die Client-Anwendung kann die Lizenz in die CFF-Datei einfügen. Inhalte können jetzt in der Anwendung wiedergegeben werden, wobei die gesamte Schutz- und Anwendungsregeldurchsetzung von der Primetime DRM-Komponente zur Laufzeit verarbeitet wird.
1. Andere Geräte und Anwendungen, die demselben Endbenutzer gehören, können beim Koordinator registriert werden. Der Inhalt kann jetzt auf anderen Primetime-DRM-Geräten geladen werden, ohne dass eine externe Transaktion erforderlich ist.
