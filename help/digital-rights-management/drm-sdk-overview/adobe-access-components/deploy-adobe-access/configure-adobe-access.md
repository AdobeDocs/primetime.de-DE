---
seo-title: Adobe Primetime DRM bereitstellen
title: Adobe Primetime DRM bereitstellen
uuid: c14c2792-d207-4f39-b856-610520bdaa28
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime DRM bereitstellen {#configure-adobe-primetime-drm}

Ein wichtiger Vorteil des Adobe Primetime DRM SDK besteht darin, dass Sie es auf einem beliebigen Java™-Anwendungsserver oder Servlet-Container wie Tomcat installieren können. Sie benötigen auch JDK™ 1.5 oder höher. Weitere Informationen zu Softwareanforderungen finden Sie unter Primetime DRM SDK-Plattformanforderungen: [https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Die allgemeinen Schritte zur Bereitstellung von Primetime DRM sind:

1. Installieren und konfigurieren Sie Primetime DRM SDK.
1. Digitale Zertifikate von Adobe abrufen
1. Erstellen Sie einen License Server mit dem SDK oder stellen Sie Primetime DRM Server für das geschützte Streaming bereit.
1. Erstellen Sie Inhaltspakete und Richtlinienverwaltungstools, um Inhalte zu verpacken, die bereitgestellten Inhaltsbereitstellungswerkzeuge zu verwenden oder einen der Adobe HTTP Dynamic Streaming Packager zu lizenzieren.
1. Definieren Sie Nutzungsregeln für Ihren Inhalt und erstellen Sie Richtlinien, die diese Regeln unterstützen.
1. Verpacken Sie Ihre Inhalte mithilfe der Verpackungs- und Richtlinienverwaltungstools.
1. Entwickeln Sie Videoanwendungen, mit denen die Konsumenten Ihre geschützten Inhalte mit Flash Player oder Adobe AIR Ansicht oder eine etablierte OVP (Online Video Platform) verwenden können, die Primetime DRM unterstützt.
1. Stellen Sie eine SWF-Datei zur Verwendung mit Flash Player auf Ihrer Website bereit oder veröffentlichen Sie das Adobe AIR-Installationsprogramm zum Herunterladen.

Diese Schritte werden in den folgenden Abschnitten mit Verweisen auf andere Dokumente mit zusätzlichen Informationen erweitert.

## Bereitstellen unter einem 64-Bit-Betriebssystem{#deploying-on-a-bit-operating-system}

Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von RedHat oder Windows, bietet eine wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

## Adobe Primetime DRM SDK installieren {#install-adobe-primetime-drm-sdk}

Primetime DRM SDK wird als Java-Archivdatei (JAR) bereitgestellt. Weitere Informationen zum Installieren von Primetime DRM finden Sie unter Verwenden des Adobe Primetime DRM SDK für den Schutz von Inhalten und sichere Bereitstellungsrichtlinien.

## Lizenzserver implementieren {#implement-a-license-server}

Mit dem Adobe Primetime DRM SDK müssen Sie einen License Server erstellen. Wenn Inhalte mit Primetime DRM geschützt sind, können sie erst angezeigt werden, wenn dem Verbraucher eine Lizenz vom Lizenzserver erteilt wurde. Wenn identitätsbasierte Lizenzierung verwendet wird, stellt die kennwortbasierte Authentifizierung sicher, dass nur autorisierte Ansichten Inhalte öffnen und bereitstellen können.

Bei der Implementierung eines Lizenzservers müssen Sie die erforderlichen digitalen Zertifikate von Adobe abrufen. Detaillierte Anweisungen zum Anfordern von Zertifikaten finden Sie im Primetime DRM-Dokument für die Zertifikatregistrierung.

Weitere Informationen zum Implementieren eines Lizenzservers und zum Abrufen digitaler Zertifikate finden Sie unter **Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten.**

## Erstellen von Inhaltspaketwerkzeugen und Richtlinienverwaltungswerkzeugen{#create-content-packaging-and-policy-management-tools}

Mit dem Adobe Primetime DRM SDK können Sie Werkzeuge für die Inhaltspakete und Richtlinienverwaltung erstellen. Mit den Policy-Management-APIs können Administratoren Ansichten erstellen, Details zu Richtlinien erstellen und aktualisieren. Die Verpackungs-APIs betten die Richtlinie in eine Videodatei ein und verschlüsseln die Datei mit dem Inhaltsverschlüsselungsschlüssel.

Das Primetime-DRM-SDK enthält eine Referenz-Implementierung ( [!DNL AdobePackager.jar]), die Beispiele für Inhaltspakete und Richtlinienverwaltungstools ( [!DNL AdobePolicyManager.jar]) enthält.

Weitere Informationen zum Erstellen von Paketen für Inhalte und Richtlinienverwaltungstools finden Sie unter Adobe Primetime DRM SDK zum Schutz von Inhalten **verwenden.**

## Richtlinien und Paketinhalte erstellen {#create-policies-and-package-content}

Mithilfe der vom SDK unterstützten Nutzungsregeln müssen Sie Richtlinien zur Unterstützung des Geschäftsmodells Ihres Unternehmens definieren und erstellen und dann Ihre Inhalte mit diesen Richtlinien verpacken. Sobald Richtlinien auf Inhalte während der Verpackung angewendet werden, können Sie die Kontrolle über Ihre Inhalte behalten, unabhängig davon, wie weit sie verteilt werden.

Die Richtlinien in Adobe Primetime DRM unterstützen eine breite Palette verschiedener Nutzungsregeln, darunter:

* Die Angabe der Anzahl der Tage, an denen eine Lizenz gültig ist, sobald ein Benutzer beginnt, den Inhalt anzuzeigen.
* Zulassen der Lizenzzwischenspeicherung.
* Angabe von Client-Laufzeitumgebungen und -Versionen, die auf Inhalte zugreifen können (zum Beispiel müssen Benutzer über eine bestimmte Adobe AIR-Anwendung oder eine bestimmte Version von Flash Player verfügen).
* Es muss sichergestellt werden, dass sich Verbraucher vor dem Anzeigen geschützter Inhalte mit einem Benutzernamen und einem Kennwort authentifizieren oder anonymer Zugriff zugelassen wird.

Weitere Informationen zum Verpacken von Inhalten finden Sie unter *Schutz von Inhalten*. Weitere Informationen zu den Nutzungsregeln und den von ihnen unterstützten Geschäftsmodellen finden Sie unter *Nutzungsregeln*.

## Entwickeln von Anwendungen für die Videowiedergabe {#develop-applications-for-video-playback}

Um Benutzern den Zugriff auf Inhalte und die Ansicht zu ermöglichen, entwickeln Sie eine Videowiedergabeanwendung mit Flash Player oder Adobe AIR. Nachdem Sie eine Videowiedergabeanwendung entwickelt haben, müssen Sie sie für Endanwender bereitstellen. Wenn Sie eine Anwendung mit Flash Player entwickeln, hosten Sie sie auf der Website Ihres Unternehmens. Wenn Sie eine Anwendung mit Adobe® AIR® entwickeln, veröffentlichen Sie das Installationsprogramm der AIR-Anwendung, damit die Benutzer die Anwendung auf ihren Computer herunterladen und installieren können.

Weitere Informationen zum Entwickeln von benutzerdefinierten Videowiedergabeanwendungen für die Verwendung mit Adobe Primetime DRM finden Sie im Kapitel &quot;Arbeiten mit Video&quot;im [ActionScript 3.0 Entwicklerhandbuch](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html), im [Adobe Video Technology Center](https://www.adobe.com/devnet/video/)und im Open Source Media Framework.