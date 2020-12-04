---
seo-title: UltraViolet-Medien und Adobe Primetime DRM
title: UltraViolet-Medien und Adobe Primetime DRM
uuid: 7076c0f9-e092-48e4-9118-8a414bd03c7a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# UltraViolet-Medien und Adobe Primetime DRM {#ultraviolet-media-and-adobe-primetime-drm}

Adobe Primetime DRM kann mit anderen Streaming-Lösungen von Drittanbietern verwendet werden, um ein komplettes und sicheres DRM-basiertes Medienverteilungsnetzwerk einzurichten.

UltraViolet ( [https://www.myuv.com/](https://www.uvvu.com/)) ist ein Digital-Rights-Authentifizierungs- und Cloud-basiertes Distributionssystem, das es den Nutzern digitaler Home-Entertainment-Inhalte ermöglichen kann, erworbene Inhalte über mehrere Plattformen und Geräte zu streamen und herunterzuladen. UltraViolet-Inhalte werden mit Common Encryption (CENC) in einem Common File Format (CFF) heruntergeladen (oder gestreamt).

Es ist einfach, ein UltraViolet-System zusammen mit Adobe Primetime DRM einzurichten. Im folgenden Anwendungsfall wird das Verhalten des Inhaltsflusses dargestellt:

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Der Inhaltsbesitzer kodiert und packt den Inhalt in CFF. Die verpackten Inhalte sind für den Vertrieb an einen Händler lizenziert.
1. Der Einzelhändler lädt die Inhalte auf einen digitalen Dienstleister wie CDN hoch. Der Inhalt kann jetzt heruntergeladen werden. Beachten Sie, dass einige dieser Rollen von einer oder mehreren Firmen wiedergegeben werden können.

   Der Endbenutzer verfügt über ein Gerät, das Adobe AIR unterstützt. Darüber hinaus muss der Benutzer eine UltraViolet-kompatible Anwendung installieren. Die Anwendung enthält den erforderlichen Code, um den CFF zu analysieren und ihn für den Verbrauch durch die Laufzeit darzustellen. Alle sensiblen kryptographischen Vorgänge werden in der sicheren Laufzeit verarbeitet.
1. Die Anwendung kann eine Domänenverbindung für das Gerät auslösen, die mit dem Koordinator interagiert. Der Koordinator unterhält einen Zugriffsschutz, eine Benutzerdatenbank und Domänen. Der Domänenmanager des Koordinators wird mithilfe des Primetime DRM SDK erstellt, um Primetime DRM-spezifische Vorgänge zum Verbinden/Verlassen von Domänen zu implementieren.
1. Der Benutzer kann dann mit der Anwendung ein Video auswählen, das er vom Händler erwerben möchte. Der Einzelhändler stellt in der Regel ein Webportal bereit und verarbeitet die gesamte Geschäftslogik.
1. Der Händler interagiert dann mit dem Koordinator, um ein Berechtigungstoken hinzuzufügen. Der Einzelhändler leitet die Anforderung für den eigentlichen Inhaltsdownload an den Dienstleister weiter.
1. Wenn das Gerät noch keine Lizenz für den Inhalt besitzt, löst es eine Lizenzanforderung mit dem CFF aus. Die Anforderung umfasst in der Regel ein Domänenzertifikat, Benutzeranmeldeinformationen und Informationen zur Anwendung. Der Dienstleister betreibt einen Primetime DRM License Server (entwickelt mit dem Primetime DRM SDK), der den UltraViolet Spezifikationen entspricht.
1. Die UltraViolet Geschäftslogik des Dienstleisters interagiert bei Bedarf mit dem Koordinator, um das entsprechende Berechtigungstoken abzurufen, um zu bestimmen, ob eine Inhaltslizenz erteilt werden soll.

   Die Inhaltslizenz ist an die Domäne gebunden. Die Clientanwendung kann die Lizenz in die CFF-Datei einfügen. Inhalte können jetzt in der Anwendung wiedergegeben werden, wobei alle Schutz- und Nutzungsregeln von der Primetime DRM-Komponente in der Laufzeit verarbeitet werden.
1. Andere Geräte und Anwendungen, die demselben Endbenutzer gehören, können beim Koordinator registriert werden. Der Inhalt kann jetzt auf anderen Primetime-DRM-Geräten geladen werden, ohne dass eine externe Transaktion erforderlich ist.