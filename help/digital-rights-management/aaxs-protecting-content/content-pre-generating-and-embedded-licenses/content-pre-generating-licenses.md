---
title: Vorausgenerierung von Lizenzen
description: Vorausgenerierung von Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Vorausgenerierung von Lizenzen{#pre-generating-licenses}

Verwenden Sie zum Vorgenerieren von Lizenzen die `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` , um eine Instanz von `LicenseFactory`. Um die von dieser Factory generierten Lizenzen zu signieren, muss eine Lizenz für License Server angegeben werden. Diese Klasse unterstützt das Generieren von Leaf-Lizenzen ohne Lizenzketten sowie von Leaf- und Root-Lizenzen mit der [Verbesserte Lizenzverkettung](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen die Inhaltsmetadaten mit `initContentInfo()`. Wenn die Metadaten mehrere Richtlinien enthalten oder Sie eine Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, verwenden Sie `setSelectedPolicy()` um die Richtlinie anzugeben, die zum Generieren der Lizenz verwendet werden soll. Wenn Sie eine Liste mit Richtlinienaktualisierungen verwenden, um Aktualisierungen von Richtlinien zu verfolgen, können Sie die Liste für Richtlinienaktualisierungen vor der Initialisierung der Metadaten mit `setPolicyUpdateList()`.

Beim Generieren einer Root-Lizenz können die Inhaltsmetadaten wie oben beschrieben angegeben werden. Alternativ kann eine Root-Lizenz mithilfe einer Richtlinie ( `setSelectedPolicy()`) und der Lizenzserver-URL ( `setLicenseServerURL()`) anstelle der Metadaten.

>[!NOTE]
>
>Eine Lizenzserver-URL ist auch dann erforderlich, wenn kein Adobe Access License Server vorhanden ist, von dem aus die Clients eine Lizenz anfordern können. In diesem Fall sollte die Lizenzserver-URL eine URL angeben, die den Lizenzgeber identifiziert.

Wenn die Richtlinie die erweiterte Lizenzketten verwendet, muss eine Lizenzserver-Berechtigung angegeben werden, damit der Root Encryption Key in der Richtlinie ( `setRootKeyRetrievalInfo()`).

Wenn die Richtlinie eine domänengebundene Lizenz erfordert, verwenden Sie `setDomainCAs()` , um die Domänenautoren anzugeben, von denen der Lizenzserver Domänen-Token akzeptiert. Zur Validierung des Lizenzempfängers müssen ein oder mehrere Zertifizierungszertifikate der Domain CA bereitgestellt werden.

Wenn die Richtlinie die Bereitstellung von Remote-Schlüsseln für iOS-Geräte erfordert, muss das Schlüsselserverzertifikat mit `setKeyServerCertificate()`, es sei denn, ein verkettetes Leaf wird generiert.

Um eine Lizenz zu generieren, rufen Sie auf `generateLicense()` und geben Sie den Lizenztyp (Leaf oder Root) sowie ein oder mehrere Empfängerzertifikate an. Das Empfängerzertifikat ist je nach den in der Richtlinie angegebenen Anforderungen entweder ein maschinelles Zertifikat oder ein Domänenzertifikat. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können die in der Richtlinie angegebenen Nutzungsregeln überschrieben werden. Abschließend aufrufen `signLicense()` zum Signieren der Lizenz und zum Abrufen einer Instanz von `PreGeneratedLicense`. Die Lizenz kann jetzt in einer Datei gespeichert werden (verwenden Sie `getBytes()` um die serialisierte Lizenz abzurufen) oder in verschlüsselten Inhalt eingebettet. Siehe [Einbetten von Lizenzen](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Beispielcode für vorgenerierte Lizenzen finden Sie unter `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
