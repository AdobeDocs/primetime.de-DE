---
description: Informationen über die Verpackung und den Schutz von Inhalten ermöglichen Ihnen den Schutz Ihrer Inhalte.
title: Verpacken und Schützen von Inhalten
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Verpacken und Schützen von Inhalt {#packaging-protecting-content}

Informationen über die Verpackung und den Schutz von Inhalten ermöglichen Ihnen den Schutz Ihrer Inhalte.

## Sichern des Servers {#securing-the-server}

Sie müssen den Computer, auf dem Richtlinienverwaltung und Inhaltsverpackung stattfinden, physisch sichern.

Weitere Informationen finden Sie unter [Physische Sicherheit und Zugriff](../../secure-deployment-guidelines/physical-sec-and-access.md).

Wenn für die Implementierung der Inhaltspaketerstellung eine Netzwerkverbindung erforderlich ist, müssen Sie Ihr Betriebssystem härter einsetzen und eine entsprechende Firewall-Lösung implementieren. Weitere Informationen finden Sie unter [Netzwerktopologie](../../secure-deployment-guidelines/overview/network-topology.md).

## Sicheres Verpacken von Inhalt {#securely-packaging-content}

Die Konfigurationsdatei für das Befehlszeilenwerkzeug des Adobe Primetime DRM Media Packager erfordert eine PKCS12-Berechtigung, die beim Verpacken verwendet wird.

In den Befehlszeilenwerkzeugen zur Referenzimplementierung wird das Kennwort für die PKCS12-Berechtigungsdatei in der Datei `flashaccess.properties` in unverschlüsseltem Text gespeichert. Achten Sie daher besonders darauf, dass Sie den Computer, der diese Datei hostet, sichern und sicherstellen, dass der Computer in einer sicheren Umgebung ist. Weitere Informationen finden Sie unter [Physische Sicherheit und Zugriff](../../secure-deployment-guidelines/physical-sec-and-access.md).

Der Packager verwendet auch die Transportzertifikate License Server und License Server und die Integrität und Vertraulichkeit dieser Informationen müssen geschützt werden. Nur autorisierte Stellen sollten den Packager verwenden dürfen. Wenn Ihre privaten Schlüssel beschädigt sind, informieren Sie Adobe Systems Incorporated sofort, damit das Zertifikat widerrufen werden kann.

>[!NOTE]
>
>Mit der API können Sie denselben Schlüssel für mehrere Inhaltselemente verwenden. Um ein Höchstmaß an Sicherheit zu gewährleisten, sollten Sie diese Funktion nur für FMS-Inhalte mit mehreren Bitraten verwenden. Verwenden Sie nicht denselben Schlüssel für mehrere Dateien, die unterschiedliche Inhalte darstellen.

Die Primetime DRM Packaging API gibt unter bestimmten Bedingungen Warnungen aus. Überprüfen Sie diese Warnungen, um festzustellen, ob Ihre Dateien erfolgreich verschlüsselt wurden. Die Warnmeldungen können wie folgt lauten:

* Die Richtlinie ist abgelaufen und ein nicht erkanntes Tag oder Track kann nicht verschlüsselt werden.
* Filmfragmente können nicht verschlüsselt werden und Verweise innerhalb dieser Fragmente sind möglicherweise gültig.
* Metadaten können nicht verschlüsselt werden.

Wenn Inhalte mithilfe einer Richtlinie mit falschen Attributen gepackt werden, muss die Richtlinie aktualisiert werden. Die aktualisierte Richtlinie muss dem Lizenzserver über eine Liste zur Richtlinienaktualisierung oder einen anderen Mechanismus zum Versand zur Verfügung gestellt werden. Einige Richtlinienattribute können nach der Erstellung der Richtlinie nicht mehr geändert werden. Wenn diese Attribute nicht korrekt sind, ziehen Sie den Inhalt von den Distribution-Sites zurück, widerrufen Sie die Richtlinie, sodass keine zukünftigen Lizenzen erteilt werden können, und verschlüsseln Sie den Inhalt erneut.

Wenn die Verpackung abgeschlossen ist, wird der Verpackungsschlüssel vom Garbage Collection erfasst und nicht explizit zerstört. Daher bleibt der Verpackungsschlüssel noch einige Zeit im Speicher. Sie müssen sich vor unbefugtem Zugriff auf den Computer schützen und sicherstellen, dass keine Dateien, wie z. B. Kernauslagerungen, offen gelegt werden, die diese Informationen offen legen könnten.

## Sicheres Speichern von Richtlinien {#securely-storing-policies}

Mit dem Adobe Primetime DRM SDK können Sie Anwendungen entwickeln, die in der Inhaltspakete und bei der Richtlinienerstellung verwendet werden können.

Wenn Sie diese Anwendungen erstellen, können Sie einigen Benutzern erlauben, Richtlinien zu erstellen und zu ändern, und andere Benutzer darauf beschränken, nur vorhandene Richtlinien auf den Inhalt anzuwenden. Sie müssen die erforderlichen Zugriffskontrollen implementieren und Benutzerkonten mit unterschiedlichen Berechtigungen für die Richtlinienerstellung und Richtlinienanwendung erstellen.

Richtlinien werden erst dann unterzeichnet oder vor Änderungen geschützt, wenn sie in der Verpackung verwendet werden. Wenn Sie befürchten, dass Benutzer von Verpackungstools Richtlinien ändern könnten, signieren Sie die Richtlinien, um sicherzustellen, dass die Richtlinien nicht geändert werden können.

Weitere Informationen zum Erstellen von Anwendungen mit dem SDK finden Sie in den Primetime-DRM-APIs unter [API Primetime-API-Verweise](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).

## Asymmetrische Schlüsselverschlüsselung {#asymmetric-key-encryption}

Die asymmetrische Schlüsselverschlüsselung, auch als Verschlüsselung öffentlicher Schlüssel bezeichnet, verwendet Schlüssel-Paare. Ein Schlüssel ist für die Verschlüsselung, der andere für die Entschlüsselung.

Der Entschlüsselungsschlüssel oder der *`private key`* wird geheim gehalten. der Verschlüsselungsschlüssel oder das *`public key`* wird allen Personen zur Verfügung gestellt, die zum Verschlüsseln von Inhalten berechtigt sind. Jeder mit Zugriff auf den öffentlichen Schlüssel kann Inhalte verschlüsseln. Der Inhalt kann jedoch nur von jemandem entschlüsselt werden, der Zugriff auf den privaten Schlüssel hat. Der private Schlüssel kann nicht aus dem öffentlichen Schlüssel rekonstruiert werden.

Wenn Sie Inhalte verpacken, wird der öffentliche Schlüssel des Lizenzservers zum Verschlüsseln des Inhaltsverschlüsselungsschlüssels (CEK) in den DRM-Metadaten verwendet. Sie müssen sicherstellen, dass nur der Lizenzserver Zugriff auf den privaten Schlüssel des Lizenzservers hat. Wenn jemand anderes den Schlüssel hat, kann er den Inhalt entschlüsseln und Ansicht geben.

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie das Zertifikat des Lizenzservers mit dem öffentlichen Schlüssel von einer vertrauenswürdigen Quelle abrufen. Auf diese Weise können Sie sicherstellen, dass es sich um den Schlüssel des Lizenzservers und nicht um einen Schurkenschlüssel handelt. Wenn Angreifer ihren öffentlichen Schlüssel durch den Lizenzserver-Schlüssel ersetzen würden, könnten sie Ihren Inhalt entschlüsseln.

Weitere Informationen zum Verpacken von Inhalten finden Sie unter [Verwenden des Adobe Primetime DRM SDK zum Schützen von Inhalten](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_protecting_content.pdf).