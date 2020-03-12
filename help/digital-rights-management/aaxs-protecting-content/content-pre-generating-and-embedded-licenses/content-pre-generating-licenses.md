---
seo-title: Vorgenerieren von Lizenzen
title: Vorgenerieren von Lizenzen
uuid: 31430753-11f1-4ce5-b402-cf4279119a05
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Vorgenerieren von Lizenzen{#pre-generating-licenses}

Um Lizenzen vorab zu generieren, verwenden Sie `com.adobe.flashaccess.sdk.license.pregen.LicenseFactory.getInstance()` zum Abrufen einer Instanz von `LicenseFactory`. Eine Lizenzserver-Berechtigung muss angegeben werden, um die von dieser Factory generierten Lizenzen zu signieren. Diese Klasse unterstützt das Generieren von Leaf-Lizenzen ohne Lizenzketten und Leaf- und Root-Lizenzen mit der [erweiterten Lizenzketten](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-other-policy-options/content-enhanced-license-chaining.md).

Beim Generieren einer Leaf-Lizenz müssen die Inhaltsmetadaten mit `initContentInfo()`angegeben werden. Wenn die Metadaten mehrere Richtlinien enthalten oder Sie eine Richtlinie verwenden möchten, die nicht in den Metadaten enthalten ist, geben Sie `setSelectedPolicy()` die Richtlinie an, die zum Generieren der Lizenz verwendet werden soll. Wenn Sie eine Liste zur Richtlinienaktualisierung verwenden, um Aktualisierungen von Richtlinien zu verfolgen, können Sie die Liste zur Richtlinienaktualisierung der Lizenzfabrik bereitstellen, bevor Sie die Metadaten mit `setPolicyUpdateList()`initialisieren.

Beim Generieren einer Stammlizenz können die Inhaltsmetadaten wie oben beschrieben angegeben werden. Alternativ kann eine Root-Lizenz auch mithilfe einer Richtlinie ( `setSelectedPolicy()`) und einer Lizenzserver-URL ( `setLicenseServerURL()`) anstelle der Metadaten generiert werden.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Eine Lizenzserver-URL ist erforderlich, auch wenn es keinen Adobe Access License Server gibt, über den die Clients eine Lizenz anfordern können. In diesem Fall sollte die URL des Lizenzservers eine URL angeben, die den Lizenzaussteller identifiziert.

Wenn die Richtlinie die erweiterte Lizenzketten verwendet, muss eine Lizenzserver-Berechtigung angegeben werden, um den Root Encryption Key in der Richtlinie ( `setRootKeyRetrievalInfo()`) zu entschlüsseln.

Wenn für die Richtlinie eine domänengebundene Lizenz erforderlich ist, geben Sie die Domänenaussteller an, von denen aus der Lizenzserver Domänentoken akzeptieren kann. `setDomainCAs()` Ein oder mehrere CA-Domänenzertifikate müssen bereitgestellt werden, um den Empfänger der Lizenz zu validieren.

Wenn für die Richtlinie ein Remote-Key-Versand für iOS-Geräte erforderlich ist, muss das Key-Server-Zertifikat mit bereitgestellt werden, `setKeyServerCertificate()`es sei denn, ein verkettetes Leaf wird generiert.

Um eine Lizenz zu generieren, rufen Sie den Lizenztyp (Leaf- oder Stammordner) und ein oder mehrere Empfänger-Zertifikate auf `generateLicense()` und geben Sie diese an. Je nach den in der Richtlinie angegebenen Anforderungen handelt es sich bei dem Empfänger-Zertifikat entweder um ein Computerzertifikat oder ein Domänenzertifikat. Wenn Sie ein verkettetes Leaf generieren, ist kein Empfänger erforderlich. Nachdem die Lizenz generiert wurde, können die in der Richtlinie angegebenen Nutzungsregeln überschrieben werden. Rufen Sie schließlich auf, `signLicense()` um die Lizenz zu signieren und eine Instanz von zu erhalten `PreGeneratedLicense`. Die Lizenz kann jetzt in einer Datei gespeichert (zum Abrufen der serialisierten Lizenz) oder in verschlüsselten Inhalt eingebettet werden. `getBytes()` Siehe [Einbetten von Lizenzen](../../aaxs-protecting-content/content-pre-generating-and-embedded-licenses/content-embedding-licenses.md).

Beispiel-Code, der vorab generierte Lizenzen demonstriert, finden Sie `com.adobe.flashaccess.samples.licensegen.GenerateLicense` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.
