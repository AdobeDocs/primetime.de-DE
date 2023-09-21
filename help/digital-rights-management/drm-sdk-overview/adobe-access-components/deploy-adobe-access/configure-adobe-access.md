---
title: Adobe Primetime DRM bereitstellen
description: Adobe Primetime DRM bereitstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Adobe Primetime DRM bereitstellen {#configure-adobe-primetime-drm}

Ein wichtiger Vorteil für das Adobe Primetime DRM SDK besteht darin, dass Sie es auf einem beliebigen Java™-Anwendungsserver oder Servlet-Container wie Tomcat installieren können. Außerdem benötigen Sie JDK™ 1.5 oder höher. Weitere Informationen zu Softwareanforderungen finden Sie unter Primetime DRM SDK-Plattformanforderungen: [https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Die allgemeinen Schritte zur Bereitstellung von Primetime DRM sind:

1. Installieren und konfigurieren Sie das Primetime DRM SDK.
1. Digitale Zertifikate von Adobe abrufen.
1. Erstellen Sie einen Lizenzserver mit dem SDK oder stellen Sie den Primetime DRM Server für geschütztes Streaming bereit.
1. Erstellen Sie Inhaltspakete und Richtlinien-Management-Tools, um Inhalte zu verpacken, verwenden Sie die bereitgestellten Inhaltsvorbereitungs-Tools oder lizenzieren Sie einen der Adobe HTTP Dynamic Streaming Packager.
1. Definieren Sie Nutzungsregeln für Ihren Inhalt und erstellen Sie Richtlinien zur Unterstützung dieser Regeln.
1. Verpacken Sie Ihre Inhalte mit den Tools für das Verpacken und Richtlinienmanagement.
1. Entwickeln Sie Videoanwendungen, mit denen Verbraucher Ihre geschützten Inhalte mithilfe von Flash Player oder Adobe AIR anzeigen können, oder verwenden Sie einen etablierten OVP (Online Video Platform), der Primetime DRM unterstützt.
1. Stellen Sie eine SWF-Datei zur Verwendung mit Flash Player auf Ihrer Website bereit oder posten Sie das Adobe AIR-Installationsprogramm zum Herunterladen.

Diese Schritte werden in den folgenden Abschnitten mit Verweisen auf andere Dokumente mit zusätzlichen Informationen erweitert.

## Bereitstellen unter einem 64-Bit-Betriebssystem{#deploying-on-a-bit-operating-system}

Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von Red Hat oder Windows, bietet deutlich bessere Leistung als ein 32-Bit-Betriebssystem.

## Installieren des Adobe Primetime DRM SDK {#install-adobe-primetime-drm-sdk}

Das Primetime DRM SDK wird als Java-Archivdatei (JAR) bereitgestellt. Weitere Informationen zur Installation von Primetime DRM finden Sie unter Verwenden des Adobe Primetime DRM SDK für den Schutz von Inhalten und sichere Bereitstellungsrichtlinien .

## Implementieren eines Lizenzservers {#implement-a-license-server}

Mit dem Adobe Primetime DRM SDK müssen Sie einen Lizenzserver erstellen. Wenn Inhalte mithilfe von Primetime DRM geschützt werden, können sie erst angezeigt werden, wenn der Lizenzserver dem Verbraucher eine Lizenz erteilt hat. Wenn identitätsbasierte Lizenzierung verwendet wird, stellt die passwortbasierte Authentifizierung sicher, dass nur autorisierte Benutzer Inhalte öffnen und anzeigen können.

Bei der Implementierung eines Lizenzservers müssen Sie die erforderlichen digitalen Zertifikate von Adobe abrufen. Detaillierte Anweisungen zum Anfordern von Zertifikaten finden Sie im Dokument Primetime DRM Certificate Enrollment .

Weitere Informationen zum Implementieren eines Lizenzservers und zum Abrufen digitaler Zertifikate finden Sie unter **Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten**

## Erstellen von Inhaltspaketen und Richtlinien-Management-Tools{#create-content-packaging-and-policy-management-tools}

Mit dem Adobe Primetime DRM SDK können Sie Tools für die Inhaltspakete und Richtlinienverwaltung erstellen. Mit den Policy Management-APIs können Administratoren Richtlinien erstellen, Details anzeigen und aktualisieren. Die Verpackungs-APIs betten die Richtlinie in eine Videodatei ein und verschlüsseln die Datei mit dem Schlüssel zur Inhaltsverschlüsselung.

Das Primetime DRM SDK enthält eine Referenzimplementierung ( [!DNL AdobePackager.jar]), die Beispiele für Inhaltspakete und Richtlinien-Management-Tools ( [!DNL AdobePolicyManager.jar]).

Weitere Informationen zum Erstellen von Inhaltspaketungs- und Richtlinienmanagement-Tools finden Sie unter **Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten**

## Erstellen von Richtlinien und Paketinhalten {#create-policies-and-package-content}

Mithilfe der vom SDK unterstützten Nutzungsregeln müssen Sie Richtlinien zur Unterstützung des Geschäftsmodells Ihres Unternehmens definieren und erstellen und dann Ihre Inhalte mithilfe dieser Richtlinien verpacken. Sobald Richtlinien auf Inhalte während der Verpackung angewendet werden, können Sie die Kontrolle über Ihren Inhalt behalten, unabhängig davon, wie weit er verteilt ist.

Die Richtlinien in Adobe Primetime DRM unterstützen eine Vielzahl verschiedener Nutzungsregeln, darunter:

* Die Angabe der Anzahl von Tagen, für die eine Lizenz gültig ist, sobald ein Verbraucher mit der Wiedergabe des Inhalts beginnt.
* Zulassen der Lizenzzwischenspeicherung.
* Angabe von Client-Laufzeiten und -Versionen, die auf Inhalte zugreifen können (z. B. müssen Benutzer über eine bestimmte Adobe AIR-Anwendung oder eine bestimmte Flash Player-Version verfügen).
* Anforderung, dass sich Verbraucher vor der Anzeige geschützter Inhalte mit einem Benutzernamen und einem Kennwort authentifizieren müssen oder anonymen Zugriff zulassen.

Weitere Informationen zum Verpacken von Inhalten finden Sie unter *Schutz von Inhalten*. Weitere Informationen zu den Nutzungsregeln und den von ihnen unterstützten Geschäftsmodellen finden Sie unter *Nutzungsregeln*.

## Anwendungen für die Videowiedergabe entwickeln {#develop-applications-for-video-playback}

Um Verbrauchern den Zugriff auf und die Anzeige von Inhalten zu ermöglichen, entwickeln Sie eine Videowiedergabeanwendung mit Flash Player oder Adobe AIR. Nachdem Sie eine Videowiedergabeanwendung entwickelt haben, müssen Sie sie für Verbraucher bereitstellen. Wenn Sie eine Anwendung mit Flash Player entwickeln, hosten Sie sie auf der Website Ihres Unternehmens. Wenn Sie eine Anwendung mit Adobe® AIR® entwickeln, posten Sie das Installationsprogramm für die AIR-Anwendung, damit Verbraucher die Anwendung herunterladen und auf ihrem Computer installieren können.

Weitere Informationen zum Entwickeln von benutzerdefinierten Videowiedergabeanwendungen für die Verwendung mit Adobe Primetime DRM finden Sie im Kapitel &quot;Arbeiten mit Videos&quot;in [Entwicklerhandbuch für ActionScript 3.0](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html), die [Adobe Video Technology Center](https://www.adobe.com/devnet/video/)und der Open Source Media Framework.
