---
title: Vorgenerieren von Lizenzen
description: Vorgenerieren von Lizenzen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Vorgenerierende Lizenzen{#pre-generating-licenses}

Um Lizenzen vorab zu generieren, verwenden Sie `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()`, um eine Instanz von `LicenseFactory` abzurufen. Eine Lizenzserver-Berechtigung muss angegeben werden, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt die Generierung von Leaf-Lizenzen ohne Lizenzketten sowie von Leaf- und Root-Lizenzen mit der [Verbesserte Lizenzketten](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen die Inhaltsmetadaten mit `initContentInfo()` angegeben werden. Wenn die Metadaten mehrere Richtlinien enthalten oder Sie eine Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, verwenden Sie `setSelectedPolicy()`, um die Richtlinie anzugeben, die zum Generieren der Lizenz verwendet werden soll. Wenn Sie eine Liste zur Richtlinienaktualisierung verwenden, um Aktualisierungen von Richtlinien zu verfolgen, können Sie die Liste zur Richtlinienaktualisierung der Lizenzfabrik bereitstellen, bevor Sie die Metadaten mit `setPolicyUpdateList()` initialisieren.

Beim Generieren einer Stammlizenz können die Inhaltsmetadaten wie oben beschrieben angegeben werden. Alternativ dazu kann eine Root-Lizenz mit einer Richtlinie ( `setSelectedPolicy()`) und einer Lizenzserver-URL ( `setLicenseServerURL()`) anstelle der Metadaten generiert werden.

>[!NOTE]
>
>Eine Lizenzserver-URL ist auch dann erforderlich, wenn keine Adobe Access License Server vorhanden ist, über die die Clients eine Lizenz anfordern können. In diesem Fall sollte die URL des Lizenzservers eine URL angeben, die den Lizenzaussteller identifiziert.

Wenn die Richtlinie die erweiterte Lizenzketten verwendet, muss eine Lizenzserver-Berechtigung angegeben werden, um den Root Encryption Key in der Richtlinie ( `setRootKeyRetrievalInfo()`) zu entschlüsseln.

Wenn für die Richtlinie eine domänengebundene Lizenz erforderlich ist, geben Sie mit `setDomainCAs()` die Domänenaussteller an, von denen der Lizenzserver Domänentoken akzeptiert. Ein oder mehrere CA-Domänenzertifikate müssen bereitgestellt werden, um den Empfänger der Lizenz zu validieren.

Wenn die Richtlinie einen Remote-Key-Versand für iOS-Geräte erfordert, muss das Key-Server-Zertifikat mit `setKeyServerCertificate()` bereitgestellt werden, es sei denn, ein verkettetes Leaf wird generiert.

Um eine Lizenz zu generieren, rufen Sie `generateLicense()` auf und geben Sie den Lizenztyp (Leaf oder Root) und ein oder mehrere Empfänger-Zertifikate an. Je nach den in der Richtlinie angegebenen Anforderungen handelt es sich bei dem Empfänger-Zertifikat entweder um ein Computerzertifikat oder ein Domänenzertifikat. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können die in der Richtlinie angegebenen Nutzungsregeln überschrieben werden. Rufen Sie schließlich `signLicense()` auf, um die Lizenz zu signieren und eine Instanz von `PreGeneratedLicense` abzurufen. Die Lizenz kann jetzt in einer Datei gespeichert werden (verwenden Sie `getBytes()`, um die serialisierte Lizenz abzurufen) oder in verschlüsselten Inhalt eingebettet werden. Siehe [Einbetten von Lizenzen](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Beispiel-Code, der vorab generierte Lizenzen demonstriert, finden Sie unter `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis der Referenzimplementierungs-Befehlszeilenwerkzeuge &quot;samples&quot;.
