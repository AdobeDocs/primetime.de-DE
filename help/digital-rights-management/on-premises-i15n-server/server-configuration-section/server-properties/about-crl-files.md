---
title: Informationen zu CRL-Dateien
description: Informationen zu CRL-Dateien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Informationen zu CRL-Dateien {#about-crl-files}

Um ordnungsgemäß funktionieren zu können, müssen die Individualisierungs- und Lizenzserver über mehrere CRL-Dateien (Certificate Revocation List) verfügen, die auf dem laufenden Anwendungsserver (z. B. Tomcat) auf dem Datenträger zwischengespeichert werden. Neue CRL-Dateien müssen regelmäßig heruntergeladen und auf der Festplatte zwischengespeichert werden. Wenn die Gültigkeitsdauer von CRL-Dateien auf der Festplatte abgelaufen ist, verweigert der Individualization Server die Individualisierung von Clients und der License Server verweigert die Erteilung von Lizenzen.

Die auf der Festplatte zwischengespeicherten Zertifikatsperrlisten müssen Dateinamen haben, die den entsprechenden URLs entsprechen. Sonderzeichen wie die Doppelpunkte &#39;:&#39; und &#39;/&#39; werden in Dateinamen in Unterstriche &#39;_&#39; umgewandelt.

Im Folgenden finden Sie eine Liste von extern gehosteten Zertifikatsperrlisten, die sowohl von den Individualisierungs- als auch von Lizenzservern verwendet werden:

* **Intermediate CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessIntermediateCA.crl>]
   * Datei: [!DNL http___crl2.adobe.com_Adobe_FlashAccessIntermediateCA.crl]
   * Gültigkeit: Gut für ca. 12 Monate ab Erstellung

* **Root CRL:**

   * URL: [!DNL <ht<span></span>tps://crl2.adobe.com/Adobe/FlashAccessRootCA.crl>]
   * Datei: [!DNL http___crl2.adobe.com_Adobe_FlashAccessRootCA.crl]
   * Gültigkeit: Gut für ca. 5 Jahre ab Erstellung

* **Neueste Zertifikatsperrliste:**

   * URL: [!DNL <ht<span></span>tps://crl3.adobe.com/AdobeSystemsIncorporatedFlashAccessRuntime/LatestCRL.crl>]
   * Datei: [!DNL http___crl3.adobe.com_AdobeSystemsIncorporatedFlashAccessRuntime_LatestCRL.crl]
   * Gültigkeit: Gut für ca. 3 Monate ab Erstellung

Wenden Sie sich an den Adobe-Support, um mehr über die extern gehosteten Zertifikatsperrlisten zu erfahren, die von Lizenzservern verwendet werden können.

<!---

Commenting out because of a security vulnerability reported in Jira PSIRT-20689. 

The following are externally hosted CRLs that are used only by the License Servers:

* URL: `https://crl2.adobe.com/Adobe/FlashAccessIndividualizationCA.crl`

* File: `http___crl2.adobe.com_Adobe_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.primetime.adobe.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.primetime.adobe.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

* URL: `https://individualization-crl.s3-website-us-east-1.amazonaws.com/FlashAccessIndividualizationCA.crl`

* File: `http___individualization-crl.s3-website-us-east-1.amazonaws.com_FlashAccessIndividualizationCA.crl`

* Validity: Good for approximately 3 months from creation

--->

Zusätzlich zu den extern gehosteten Zertifikatsperrlisten können Sie eine zusätzliche Zertifikatsperrliste erstellen und verwalten. Dies ist die CRL für die Individualisierungs-Zertifizierungsstelle, wie in der [Erstellen einer CRL für individuelle Zertifizierungsstellen](../../../on-premises-i15n-server/server-configuration-section/server-properties/create-i15n-ca-crl.md) Abschnitt dieses Dokuments.

Zertifikatsperrlisten werden 45 Tage vor ihrem Ablauf aktualisiert. Dadurch sollten Sie ausreichend Zeit haben, neu generierte Zertifikatsperrlisten aus dem Internet zu erwerben und zu installieren. Sie müssen darauf achten, die CRL-Dateien zu aktualisieren, bevor sie abgelaufen sind.
