---
title: Zulassungsliste für Nicht-SWF-Anwendungen
description: Zulassungsliste für Nicht-SWF-Anwendungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Zulassungsliste für Nicht-SWF-Anwendungen {#non-swf-application-isting}

AIR war die erste Plattform mit einer Zulassungsauflistung für Anwendungen und dem Namen der Eigenschaft, die Sie für die Zulassungsliste von Nicht-SWF-Anwendungen (Adobe AIR, iOS, Android usw.) verwenden. behält seinen ursprünglichen Namen bei: `policy.allowedAIRApplication.n`. Auf diese Weise können Inhalte von allen Nicht-Flash-Anwendungen wiedergegeben werden, die vor der Veröffentlichung mit einem Signaturzertifikat signiert wurden. Dies wird als *Bewerbungs-ID*. Sie können die Anwendungs-ID mithilfe der [!DNL AdobePublisherIDUtility.jar] -Tool. Diese Zulassungsauflistung wird auf jedem Client erzwungen, der Primetime DRM unterstützt.

Die Anwendungs-ID wird aus dem öffentlichen Schlüssel des Signaturzertifikats abgeleitet, das zum Signieren einer bestimmten Anwendung verwendet wird. Wenn der öffentliche Schlüssel im Zertifikat jemals abläuft, dann dürfen alle vorherigen Inhalte, die aufgeführt sind, nur in Apps wiedergegeben werden, die mit dem alten Zertifikat signiert sind, nicht in der neuen App (mit dem neuen Zertifikat signiert).

Wenn Sie sich in einer Situation befinden, in der eine Inhaltsbibliothek für Anwendungen aufgelistet ist, die mit einem bestimmten Signaturzertifikat signiert wurden, dieses Zertifikat abläuft und Sie ein neues Zertifikat erhalten (mit einem anderen öffentlichen/privaten Keypair), wird Ihr alter Inhalt nicht in Ihrer neuen App wiedergegeben *es* Sie führen einen der folgenden Schritte aus:

* Verwenden Sie eine `PolicyUpdateList` auf Ihrem Lizenzserver verwenden, um die eingehende Richtlinie zu überschreiben und einen neuen Eintrag für die Zulassungsliste der Anwendung mit dem Digest Ihres neuen Signaturzertifikats einzufügen.
* Aktualisieren Sie die Logik Ihres Lizenzservers, um die eingehende Richtlinie zu überschreiben und einen neuen Eintrag für die Anwendungs-Zulassungsliste einzufügen.
* Fordern Sie an, dass der Aussteller des Signaturzertifikats Ihnen ein neues Zertifikat ausstellt, das dasselbe öffentliche/private Schlüsselpaar verwendet, das auch Ihr vorheriges Zertifikat verwendet hat.
* Wenn Sie HDS-/HLS-Inhalte bereitstellen, die auf einen URL-Endpunkt verweisen, um die `DRMMetadata`, können Sie die `DRMMetadata` (unter Verwendung des Primetime DRM Java SDK) zum Einfügen einer neuen DRM-Richtlinie, die einen aktualisierten Eintrag für die Zulassungsliste von Anwendungen enthält.

* Komprimieren Sie alle alten Inhalte mit einer neuen DRM-Richtlinie, die den Digest Ihres neuen Signaturzertifikats enthält.

Siehe `policy.allowedAIRApplication.n` in *Konfigurationseigenschaften* für Details.

>[!NOTE]
>
>Für das Zulassen der Auflistung einer iOS-Anwendung ist ein spezieller Ansatz erforderlich. Siehe [Zulassungsliste Ihrer iOS-Anwendung](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) im *TVSDK für iOS-Programmierhandbuch*.
