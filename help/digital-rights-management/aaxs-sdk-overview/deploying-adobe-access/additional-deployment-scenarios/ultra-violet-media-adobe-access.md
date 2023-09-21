---
description: Adobe Access kann mit anderen Content-Streaming-Lösungen von Drittanbietern verwendet werden, um ein vollständiges und sicheres DRM-basiertes Medienverteilungs-Ökosystem einzurichten.
title: UltraViolet-Medien und Adobe-Zugriff
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# UltraViolet-Medien und Adobe-Zugriff {#ultraviolet-media-and-adobe-access}

Adobe Access kann mit anderen Content-Streaming-Lösungen von Drittanbietern verwendet werden, um ein vollständiges und sicheres DRM-basiertes Medienverteilungs-Ökosystem einzurichten.

UltraViolet ist ein Digital Rights Authentication- und Cloud-basiertes Distributionssystem, das es Verbrauchern von Digital Home Entertainment-Inhalten ermöglicht, erworbene Inhalte über mehrere Plattformen und Geräte zu streamen und herunterzuladen. UltraViolet-Inhalte werden in einem Common File Format (CFF) mit Common Encryption (CENC) heruntergeladen (oder gestreamt).

Es ist einfach, ein UltraViolet System zusammen mit Adobe Access einzurichten. Das folgende Nutzungsszenario zeigt das Verhalten des Inhaltsflusses:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Der Inhaltseigentümer kodiert und packt den Inhalt in CFF. Der gepackte Inhalt ist für einen Einzelhändler zum Vertrieb lizenziert.
1. Der Einzelhändler lädt den Inhalt auf einen digitalen Dienstleister hoch, z. B. CDN. Der Inhalt kann jetzt heruntergeladen werden. Beachten Sie, dass einige dieser Rollen von einem oder mehreren Unternehmen gespielt werden können.

   Der Endbenutzer verfügt über ein Gerät, das Adobe AIR unterstützt. Zusätzlich muss der Benutzer eine UltraViolet-kompatible Anwendung installieren. Die Anwendung enthält den erforderlichen Code, um den CFF zu analysieren und ihn zur Verwendung durch die Laufzeit darzustellen. Alle sensiblen kryptografischen Vorgänge werden in der sicheren Laufzeitumgebung verarbeitet.
1. Die Anwendung kann einen Domain-Join für das Gerät Trigger haben, der mit dem Koordinator interagiert. Der Koordinator unterhält einen Sperrer für Rechte, eine Benutzerdatenbank und Domänen. Der Domain-Manager des Koordinators wird mithilfe des Adobe Access SDK erstellt, um Adobe-Zugriffs-spezifische Domain-Join-/Urlaubsvorgänge zu implementieren.
1. Der Benutzer kann dann die Anwendung verwenden, um ein Video auszuwählen, das er vom Einzelhändler erwerben möchte. Der Einzelhändler stellt in der Regel ein Webportal bereit und übernimmt die gesamte Geschäftslogik.
1. Der Händler interagiert dann mit dem Koordinator, um ein Berechtigungstoken hinzuzufügen. Der Einzelhändler leitet die Anfrage dann an den Dienstleister für den tatsächlichen Download des Inhalts weiter.
1. Wenn das Gerät noch keine Lizenz für den Inhalt besitzt, wird eine Lizenzanforderung mit dem CFF Trigger. Die Anfrage umfasst in der Regel ein Domänenzertifikat, Benutzeranmeldeinformationen und Informationen zur Anwendung. Der Dienstleister betreibt einen Adobe Access License Server (entwickelt mit dem Adobe Access SDK), der den UltraViolet-Spezifikationen entspricht.
1. Die UltraViolet-Geschäftslogik des Dienstleisters interagiert bei Bedarf mit dem Koordinator, um das entsprechende Berechtigungstoken abzurufen und zu bestimmen, ob eine Inhaltslizenz ausgestellt werden soll.

   Die Inhaltslizenz ist an die Domäne gebunden. Die Client-Anwendung kann die Lizenz in die CFF-Datei einfügen. Inhalte können jetzt in der Anwendung wiedergegeben werden, wobei die gesamte Schutz- und Anwendungsregeldurchsetzung von der Adobe Access-Komponente zur Laufzeit verarbeitet wird.
1. Andere Geräte und Anwendungen, die demselben Endbenutzer gehören, können beim Koordinator registriert werden. Der Inhalt kann jetzt auf anderen Adobe Access-Geräten geladen werden, ohne dass eine externe Transaktion erforderlich ist.
