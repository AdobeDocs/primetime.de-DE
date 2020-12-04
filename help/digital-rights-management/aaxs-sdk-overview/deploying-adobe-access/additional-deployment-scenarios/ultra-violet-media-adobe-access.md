---
description: Adobe Access kann mit anderen Content-Streaming-Lösungen von Drittanbietern verwendet werden, um ein komplettes und sicheres DRM-basiertes Medienverteilungsnetzwerk einzurichten.
seo-description: Adobe Access kann mit anderen Content-Streaming-Lösungen von Drittanbietern verwendet werden, um ein komplettes und sicheres DRM-basiertes Medienverteilungsnetzwerk einzurichten.
seo-title: UltraViolet-Adobe-Zugriff
title: UltraViolet-Adobe-Zugriff
uuid: d287680f-02de-4cca-aeea-22b7fd8e67d2
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# UltraViolet Media- und Adobe-Access {#ultraviolet-media-and-adobe-access}

Adobe Access kann mit anderen Content-Streaming-Lösungen von Drittanbietern verwendet werden, um ein komplettes und sicheres DRM-basiertes Medienverteilungsnetzwerk einzurichten.

UltraViolet ( [](https://www.uvvu.com/)) ist ein Digital-Rights-Authentifizierungs- und Cloud-basiertes Distributionssystem, das es den Nutzern digitaler Home-Entertainment-Inhalte ermöglichen kann, erworbene Inhalte über mehrere Plattformen und Geräte zu streamen und herunterzuladen. UltraViolet-Inhalte werden mit Common Encryption (CENC) in einem Common File Format (CFF) heruntergeladen (oder gestreamt).

Es ist einfach, ein UltraViolet System zusammen mit Adobe Access einzurichten. Im folgenden Anwendungsfall wird das Verhalten des Inhaltsflusses dargestellt:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Der Inhaltsbesitzer kodiert und packt den Inhalt in CFF. Die verpackten Inhalte sind für den Vertrieb an einen Händler lizenziert.
1. Der Einzelhändler lädt die Inhalte auf einen digitalen Dienstleister wie CDN hoch. Der Inhalt kann jetzt heruntergeladen werden. Beachten Sie, dass einige dieser Rollen von einer oder mehreren Firmen wiedergegeben werden können.

   Der Endbenutzer verfügt über ein Gerät, das Adobe AIR unterstützt. Darüber hinaus muss der Benutzer eine UltraViolet-kompatible Anwendung installieren. Die Anwendung enthält den erforderlichen Code, um den CFF zu analysieren und ihn für den Verbrauch durch die Laufzeit darzustellen. Alle sensiblen kryptographischen Vorgänge werden in der sicheren Laufzeit verarbeitet.
1. Die Anwendung kann eine Domänenverbindung für das Gerät auslösen, die mit dem Koordinator interagiert. Der Koordinator unterhält einen Zugriffsschutz, eine Benutzerdatenbank und Domänen. Der Domänenmanager des Koordinators wird mithilfe des Adobe Access SDK erstellt, um Adobe Access-spezifische Vorgänge zum Verbinden/Verlassen von Domänen zu implementieren.
1. Der Benutzer kann dann mit der Anwendung ein Video auswählen, das er vom Händler erwerben möchte. Der Einzelhändler stellt in der Regel ein Webportal bereit und verarbeitet die gesamte Geschäftslogik.
1. Der Händler interagiert dann mit dem Koordinator, um ein Berechtigungstoken hinzuzufügen. Der Einzelhändler leitet die Anforderung für den eigentlichen Inhaltsdownload an den Dienstleister weiter.
1. Wenn das Gerät noch keine Lizenz für den Inhalt besitzt, löst es eine Lizenzanforderung mit dem CFF aus. Die Anforderung umfasst in der Regel ein Domänenzertifikat, Benutzeranmeldeinformationen und Informationen zur Anwendung. Der Dienstleister betreibt eine Adobe Access License Server (entwickelt mit dem Adobe Access SDK), die den UltraViolet Spezifikationen entspricht.
1. Die UltraViolet Geschäftslogik des Dienstleisters interagiert bei Bedarf mit dem Koordinator, um das entsprechende Berechtigungstoken abzurufen, um zu bestimmen, ob eine Inhaltslizenz erteilt werden soll.

   Die Inhaltslizenz ist an die Domäne gebunden. Die Clientanwendung kann die Lizenz in die CFF-Datei einfügen. Inhalte können jetzt in der Anwendung wiedergegeben werden, wobei alle Sicherheits- und Nutzungsregeln von der Adobe Access-Komponente in der Laufzeit verarbeitet werden.
1. Andere Geräte und Anwendungen, die demselben Endbenutzer gehören, können beim Koordinator registriert werden. Der Inhalt kann jetzt auf anderen Adobe Access-Geräten geladen werden, ohne dass eine externe Transaktion erforderlich ist.

