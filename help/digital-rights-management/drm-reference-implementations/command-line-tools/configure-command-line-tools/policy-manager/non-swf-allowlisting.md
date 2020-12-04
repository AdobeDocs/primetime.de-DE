---
seo-title: Liste mit Nicht-SWF-Anwendungen zulassen
title: Liste mit Nicht-SWF-Anwendungen zulassen
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# Nicht-SWF-Anwendung Listen zulassen {#non-swf-application-isting}

AIR war die erste Plattform, auf der spezielle Anwendungen die Auflistung zulassen, und der Name der Eigenschaft, die Sie zur Zulassungsliste von Nicht-SWF-Anwendungen verwenden (Adobe AIR, iOS, Android usw.) behält seinen ursprünglichen Namen bei: `policy.allowedAIRApplication.n`. Auf diese Weise können die Inhalte von allen Nicht-Flash-Anwendungen wiedergegeben werden, die vor der Veröffentlichung mit einem Signaturzertifikat signiert wurden. Dies wird als *Anwendungs-ID* bezeichnet. Sie können die Anwendungs-ID mithilfe des Tools [!DNL AdobePublisherIDUtility.jar] extrahieren. Diese Zulässigkeitsliste wird auf jedem Client erzwungen, der Primetime DRM unterstützt.

Die Anwendungs-ID wird aus dem öffentlichen Schlüssel des Signaturzertifikats abgeleitet, mit dem eine bestimmte Anwendung signiert wird. Wenn der öffentliche Schlüssel im Zertifikat jemals abläuft, ist es zulässig, dass alle zuvor aufgelisteten Inhalte nur in Apps wiedergegeben werden, die mit dem alten Zertifikat signiert wurden, nicht in der neuen App (mit dem neuen Zertifikat signiert).

Wenn Sie sich in einer Situation befinden, in der eine Inhaltsbibliothek für Anwendungen, die mit einem bestimmten Unterschriftszertifikat signiert wurden, zugelassen ist und dieses Zertifikat abläuft und Sie ein neues Zertifikat erhalten (mit einem anderen öffentlichen/privaten Schlüssel), wird Ihr alter Inhalt nicht auf Ihrer neuen App *abgespielt, es sei denn,* Sie führen einen der folgenden Schritte aus:

* Verwenden Sie einen `PolicyUpdateList` auf Ihrem Lizenzserver, um die eingehende Zulassungsliste zu überschreiben und einen neuen Anwendungseintrag mit dem Digest Ihres neuen Signaturzertifikats einzufügen.
* Aktualisieren Sie die Logik des Lizenzservers, um die eingehende Richtlinie zu überschreiben und einen neuen Eintrag für die Zulassungsliste einzufügen.
* Fordern Sie an, dass der Aussteller des Unterschriftszertifikats Ihnen ein neues Zertifikat ausstellt, das denselben öffentlichen/privaten Schlüssel verwendet wie das vorherige Zertifikat.
* Wenn Sie HDS-/HLS-Inhalte bereitstellen, die auf einen URL-Endpunkt verweisen, um das `DRMMetadata` abzurufen, können Sie das `DRMMetadata` (mit dem Primetime DRM Java SDK) neu generieren, um eine neue DRM-Richtlinie einzufügen, die einen aktualisierten Eintrag für die Application Zulassungsliste enthält.

* Komprimieren Sie alle alten Inhalte mit einer neuen DRM-Richtlinie, die den Digest Ihres neuen Signaturzertifikats enthält.

Weitere Informationen finden Sie unter `policy.allowedAIRApplication.n` in *Konfigurationseigenschaften*.

>[!NOTE]
>
>Für das Auflisten einer iOS-Anwendung ist ein besonderer Ansatz erforderlich. Siehe [Zulassungsliste Ihrer iOS-Anwendung](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) im *TVSDK für iOS-Programmierhandbuch*.
