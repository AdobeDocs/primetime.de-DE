---
description: Informationen über die Verpackung und den Schutz von Inhalten ermöglichen es Ihnen, Ihre Inhalte zu schützen.
title: Verpackung und Schutz von Inhalt
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---

# Verpacken und Schützen von Inhalten {#packaging-protecting-content}

Informationen über die Verpackung und den Schutz von Inhalten ermöglichen es Ihnen, Ihre Inhalte zu schützen.

## Sichern des Servers {#securing-the-server}

Sie müssen den Computer, auf dem Richtlinienmanagement und Inhaltspakete stattfinden, physisch sichern.

Weitere Informationen finden Sie unter [Physische Sicherheit und Zugang](../../secure-deployment-guidelines/physical-sec-and-access.md).

Wenn Ihre Implementierung der Inhaltspakettierung Netzwerkverbindungen erfordert, müssen Sie Ihr Betriebssystem härten und eine entsprechende Firewall-Lösung implementieren. Weitere Informationen finden Sie unter [Netzwerktopologie](../../secure-deployment-guidelines/overview/network-topology.md).

## Sichere Verpackung von Inhalten {#securely-packaging-content}

Für die Konfigurationsdatei für das Befehlszeilen-Tool des Adobe Primetime DRM Media Packager ist eine PKCS12-Berechtigung erforderlich, die beim Verpacken verwendet wird.

In den Befehlszeilenwerkzeugen für die Referenzimplementierung wird das Kennwort für die PKCS12-Anmeldeinformationen-Datei im Ordner `flashaccess.properties` Datei in unverschlüsseltem Text. Achten Sie daher besonders darauf, dass Sie den Computer, der diese Datei hostet, sichern und sicherstellen, dass sich der Computer in einer sicheren Umgebung befindet. Weitere Informationen finden Sie unter [Physische Sicherheit und Zugang](../../secure-deployment-guidelines/physical-sec-and-access.md).

Der Packager verwendet auch die Transportzertifikate License Server und License Server und die Integrität und Vertraulichkeit dieser Informationen müssen geschützt werden. Nur autorisierte Einheiten sollten die Verwendung des Packagers zulassen dürfen. Wenn Ihre privaten Schlüssel kompromittiert sind, informieren Sie Adobe Systems Incorporated unverzüglich, damit das Zertifikat widerrufen werden kann.

>[!NOTE]
>
>Mit der API können Sie denselben Schlüssel für mehrere Inhaltselemente verwenden. Um ein Höchstmaß an Sicherheit zu gewährleisten, sollten Sie diese Funktion nur für FMS-Inhalte mit mehreren Bitraten verwenden. Verwenden Sie nicht denselben Schlüssel für mehrere Dateien, die unterschiedliche Inhalte darstellen.

Die Primetime DRM Packaging API gibt unter bestimmten Bedingungen Warnungen aus. Überprüfen Sie diese Warnungen, um festzustellen, ob Ihre Dateien erfolgreich verschlüsselt wurden. Die Warnmeldungen können wie folgt lauten:

* Die Richtlinie ist abgelaufen und ein nicht erkanntes Tag oder Tracking kann nicht verschlüsselt werden.
* Filmfragmente können nicht verschlüsselt werden und Verweise in diesen Fragmenten sind möglicherweise gültig.
* Metadaten können nicht verschlüsselt werden.

Wenn Inhalte mithilfe einer Richtlinie mit falschen Attributen gepackt werden, muss die Richtlinie aktualisiert werden. Die aktualisierte Richtlinie muss dem Lizenzserver über eine Liste mit Richtlinienaktualisierungen oder einen anderen Bereitstellungsmechanismus zur Verfügung gestellt werden. Einige Richtlinienattribute können nach der Erstellung der Richtlinie nicht mehr geändert werden. Wenn diese Attribute falsch sind, rufen Sie den Inhalt von den Verteilungs-Sites zurück, widerrufen Sie die Richtlinie, damit keine zukünftigen Lizenzen erteilt werden können, und verschlüsseln Sie den Inhalt erneut.

Wenn die Verpackung abgeschlossen ist, wird der Verpackungsschlüssel abgebrannt und nicht explizit zerstört. Daher bleibt der Verpackungsschlüssel einige Zeit im Speicher. Sie müssen sich vor unbefugtem Zugriff auf den Computer schützen und sicherstellen, dass Sie keine Dateien, wie z. B. Core-Dumps, verfügbar machen, die diese Informationen offenlegen könnten.

## Sicheres Speichern von Richtlinien {#securely-storing-policies}

Mit dem Adobe Primetime DRM SDK können Sie Anwendungen entwickeln, die bei der Inhaltspakettierung und der Richtlinienerstellung verwendet werden können.

Wenn Sie diese Anwendungen erstellen, können Sie einigen Benutzern erlauben, Richtlinien zu erstellen und zu ändern, und andere Benutzer darauf beschränken, nur vorhandene Richtlinien auf den Inhalt anzuwenden. Sie müssen die erforderlichen Zugriffskontrollen implementieren und Benutzerkonten mit unterschiedlichen Berechtigungen für die Richtlinienerstellung und Richtlinienanwendung erstellen.

Richtlinien werden erst dann unterzeichnet oder vor Änderungen geschützt, wenn sie in der Verpackung verwendet werden. Wenn Sie befürchten, dass Benutzer von Verpackungs-Tools Richtlinien ändern könnten, unterschreiben Sie die Richtlinien, um sicherzustellen, dass die Richtlinien nicht geändert werden können.

Weitere Informationen zum Erstellen von Anwendungen mit dem SDK finden Sie in den Primetime DRM-APIs unter [API Primetime-API-Referenzen](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).

## Asymmetrische Schlüsselverschlüsselung {#asymmetric-key-encryption}

Die asymmetrische Schlüsselverschlüsselung, auch als Verschlüsselung mit öffentlichen Schlüsseln bezeichnet, verwendet Schlüsselpaare. Ein Schlüssel ist für die Verschlüsselung, der andere für die Entschlüsselung.

Der Entschlüsselungsschlüssel oder der *`private key`*, wird geheim gehalten; der Verschlüsselungsschlüssel oder der *`public key`*, wird jedem zur Verschlüsselung von Inhalten autorisiert. Jeder, der Zugriff auf den öffentlichen Schlüssel hat, kann Inhalte verschlüsseln. Allerdings kann nur jemand mit Zugriff auf den privaten Schlüssel den Inhalt entschlüsseln. Der private Schlüssel kann nicht aus dem öffentlichen Schlüssel rekonstruiert werden.

Wenn Sie Inhalte verpacken, wird der öffentliche Schlüssel des Lizenzservers verwendet, um den Inhalt-Verschlüsselungsschlüssel (CEK) in den DRM-Metadaten zu verschlüsseln. Sie müssen sicherstellen, dass nur der Lizenzserver Zugriff auf den privaten Schlüssel des Lizenzservers hat. Wenn jemand anderes über den Schlüssel verfügt, kann er den Inhalt entschlüsseln und anzeigen.

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie das Zertifikat des Lizenzservers mit dem öffentlichen Schlüssel von einer vertrauenswürdigen Quelle erhalten. Auf diese Weise können Sie sicherstellen, dass es sich um den Schlüssel des Lizenzservers und nicht um einen Schurkenschlüssel handelt. Wenn Angreifer ihren öffentlichen Schlüssel durch den Schlüssel des Lizenzservers ersetzen würden, könnten sie Ihren Inhalt entschlüsseln.

Weitere Informationen zum Verpacken von Inhalten finden Sie unter [Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_protecting_content.pdf).
