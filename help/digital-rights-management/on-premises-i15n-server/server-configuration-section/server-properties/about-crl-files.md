---
title: Informationen zu CRL-Dateien
description: Informationen zu CRL-Dateien
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# Informationen zu CRL-Dateien {#about-crl-files}

Um ordnungsgemäß funktionieren zu können, müssen auf den Individualisierungs- und Lizenzservern mehrere CRL-Listen (Certificate Revocation ) zwischengespeichert werden, die auf dem laufenden Anwendungsserver (z. B. Tomcat) gespeichert sind. Neue CRL-Dateien müssen regelmäßig heruntergeladen und auf der Festplatte zwischengespeichert werden. Wenn die Gültigkeitsdauer von CRL-Dateien auf der Festplatte abgelaufen ist, verweigert der Individualization Server die Individualisierung von Clients und der License Server verweigert die Erteilung von Lizenzen.

Die auf der Festplatte zwischengespeicherten Zertifikatsperrlisten müssen Dateinamen haben, die mit den entsprechenden URLs übereinstimmen. Sonderzeichen wie Doppelpunkte &#39;:&#39; und &#39;/&#39; werden in den Dateinamen in Unterstriche &#39;_&#39; umgewandelt.

Im Folgenden finden Sie eine Liste extern gehosteter Zertifikatsperrlisten, die sowohl von den Individualisierungs- als auch von den Lizenzservern verwendet werden:

* **Intermediate CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * Datei: [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * Gültigkeit: Gut ca. 12 Monate nach der Erstellung

* **Stammzertifikat:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * Datei: [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * Gültigkeit: Gut seit etwa 5 Jahren

* **Letzte Zertifikatsperrliste:**

   * URL: [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * Datei: [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * Gültigkeit: Gut für ca. 3 Monate nach der Erstellung

Bei den folgenden CRLs handelt es sich um extern gehostete Zertifikatsperrlisten, die nur von Lizenzservern verwendet werden:

* URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl>]
* Datei: [!DNL http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl]
* Gültigkeit: Gut für ca. 3 Monate nach der Erstellung

* URL: [!DNL <ht<span></span>tps://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl>]
* Datei: [!DNL http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl]
* Gültigkeit: Gut für ca. 3 Monate nach der Erstellung

* URL: [!DNL <ht<span></span>tps://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl]
* Datei: [!DNL http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl]
* Gültigkeit: Gut für ca. 3 Monate nach der Erstellung

Zusätzlich zu den oben genannten Zertifikatsperrlisten müssen Sie eine zusätzliche Zertifikatsperrliste erstellen und verwalten. Dies ist die CRL für die Zertifizierungsstelle für Individualisierungen, wie im Abschnitt [Zertifizierungsstelle für Individualisierung erstellen ](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) dieses Dokuments angegeben.

Zertifikatsperrlisten werden 45 Tage vor Ablauf aktualisiert. Auf diese Weise sollten Sie ausreichend Zeit haben, neu generierte Zertifikatsperrlisten aus dem Internet zu erwerben und zu installieren. Sie müssen darauf achten, dass die Zertifikatsperrlisten aktualisiert werden, bevor sie abgelaufen sind.
