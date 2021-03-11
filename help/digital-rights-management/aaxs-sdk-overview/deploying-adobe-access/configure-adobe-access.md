---
title: Zugriff auf Adobe bereitstellen
description: Zugriff auf Adobe bereitstellen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Adobe-Zugriff {#deploy-adobe-access} bereitstellen

Ein wichtiger Vorteil des Adobe Access SDK besteht darin, dass Sie es auf einem beliebigen Java™-Anwendungsserver oder Servlet-Container wie Tomcat installieren können. Sie benötigen auch JDK™ 1.5 oder höher. Weitere Informationen zu Softwareanforderungen finden Sie unter Plattformanforderungen für Adobe Access SDK: [: https://www.adobe.com/products/flashaccess/systemreqs/](https://www.adobe.com/products/flashaccess/systemreqs/).

Die Schritte zur Bereitstellung von Adobe Access auf hoher Ebene sind:

1. Installieren und konfigurieren Sie das Adobe Access SDK.
1. Digitale Zertifikate aus der Adobe abrufen
1. Erstellen Sie einen Lizenzserver mit dem SDK oder stellen Sie Adobe Access Server für das geschützte Streaming bereit.
1. Erstellen Sie Inhaltsverpackungs- und Richtlinienverwaltungstools, um Inhalte zu verpacken, die bereitgestellten Inhaltsbereitstellungswerkzeuge zu verwenden oder einen der Adobe HTTP Dynamic Streaming Packager zu lizenzieren.
1. Definieren Sie Nutzungsregeln für Ihren Inhalt und erstellen Sie Richtlinien, die diese Regeln unterstützen.
1. Verpacken Sie Ihre Inhalte mithilfe der Verpackungs- und Richtlinienverwaltungstools.
1. Entwickeln Sie Videoanwendungen, mit denen die Konsumenten Ihre geschützten Inhalte mit Flash Player oder Adobe AIR oder mit einer etablierten OVP (Online-Videoplattform), die den Zugriff auf Adoben unterstützt, Ansichten durchführen können.
1. Stellen Sie eine SWF-Datei zur Verwendung mit Flash Player auf Ihrer Website bereit oder veröffentlichen Sie das Adobe AIR-Installationsprogramm zum Herunterladen.

Diese Schritte werden in den folgenden Abschnitten mit Verweisen auf andere Dokumente mit zusätzlichen Informationen erweitert.

## Bereitstellen unter einem 64-Bit-Betriebssystem {#deploying-on-a-bit-operating-system}

Ein 64-Bit-Betriebssystem, wie die 64-Bit-Version von RedHat oder Windows, bietet eine wesentlich bessere Leistung als ein 32-Bit-Betriebssystem.

## Adobe Access SDK {#install-adobe-access-sdk} installieren

Adobe Access SDK wird als Java-Archivdatei (JAR) bereitgestellt. Weitere Informationen zum Installieren von Adobe Access finden Sie unter *Verwenden des Adobe Access SDK zum Schützen von Inhalten* und *Richtlinien für die sichere Bereitstellung*.

## Implementieren eines Lizenzservers {#implement-a-license-server}

Mit dem Adobe Access SDK müssen Sie einen License Server erstellen. Wenn Inhalte mithilfe von Adobe Access geschützt werden, können sie erst angezeigt werden, wenn der Lizenzserver eine  erteilt hat. Wenn identitätsbasierte Lizenzierung verwendet wird, stellt die kennwortbasierte Authentifizierung sicher, dass nur autorisierte Ansichten Inhalte öffnen und bereitstellen können.

Bei der Implementierung eines Lizenzservers müssen Sie die erforderlichen digitalen Zertifikate von der Adobe abrufen. Detaillierte Anweisungen zum Anfordern von Zertifikaten finden Sie im Dokument Adobe Access Certificate Enrollment.

Weitere Informationen zum Implementieren eines Lizenzservers und zum Abrufen digitaler Zertifikate finden Sie unter Verwenden von Adobe Access SDK zum Schützen von Inhalten.*

## Erstellen Sie Inhaltspakete und Richtlinienverwaltungs-Tools {#create-content-packaging-and-policy-management-tools}

Mit dem Adobe Access SDK können Sie Inhaltspakete und Richtlinienverwaltungstools erstellen. Mit den Policy-Management-APIs können Administratoren Ansichten erstellen, Details zu Richtlinien erstellen und aktualisieren. Die Verpackungs-APIs betten die Richtlinie in die FLV- oder F4V-Datei ein und verschlüsseln die Datei mit dem Inhaltsverschlüsselungsschlüssel.

Das Adobe Access SDK enthält eine Referenz-Implementierung ( [!DNL AdobePackager.jar]), die Beispiele für Inhaltspakete und Richtlinienverwaltungstools ( [!DNL AdobePolicyManager.jar]) enthält.

Weitere Informationen zum Erstellen von Inhaltspaketen und Richtlinienverwaltungstools finden Sie unter *Verwenden des Adobe Access-SDK zum Schützen von Inhalten*.

## Richtlinien und Paketinhalt erstellen {#create-policies-and-package-content}

Mithilfe der vom SDK unterstützten Nutzungsregeln müssen Sie Richtlinien zur Unterstützung des Geschäftsmodells Ihres Unternehmens definieren und erstellen und dann Ihre Inhalte mit diesen Richtlinien verpacken. Sobald Richtlinien auf Inhalte während der Verpackung angewendet werden, können Sie die Kontrolle über Ihre Inhalte behalten, unabhängig davon, wie weit sie verteilt werden.

Die Richtlinien in Adobe Access unterstützen eine breite Palette verschiedener Nutzungsregeln, darunter:

* Die Angabe der Anzahl der Tage, an denen eine Lizenz gültig ist, sobald ein Benutzer beginnt, den Inhalt anzuzeigen.
* Zulassen der Lizenzzwischenspeicherung.
* Angabe von Client-Laufzeitumgebungen und -Versionen, die auf Inhalte zugreifen können (z. B. müssen Benutzer über eine bestimmte Adobe AIR-Anwendung oder eine bestimmte Version von Flash Player verfügen).
* Es muss sichergestellt werden, dass sich Verbraucher vor dem Anzeigen geschützter Inhalte mit einem Benutzernamen und einem Kennwort authentifizieren oder anonymer Zugriff zugelassen wird.

Weitere Informationen zum Verpacken von Inhalten finden Sie unter *Schutz von Inhalten*. Weitere Informationen zu den Nutzungsregeln und den von ihnen unterstützten Geschäftsmodellen finden Sie unter *Gebrauchsregeln*.

## Entwickeln von Anwendungen für die Videowiedergabe {#develop-applications-for-video-playback}

Um Benutzern den Zugriff auf und die Ansicht von Inhalten zu ermöglichen, entwickeln Sie eine Videowiedergabeanwendung mit Flash Player oder Adobe AIR. Nachdem Sie eine Videowiedergabeanwendung entwickelt haben, müssen Sie sie für Endanwender bereitstellen. Wenn Sie eine Anwendung mit Flash Player entwickeln, hosten Sie sie auf der Website Ihres Unternehmens. Wenn Sie eine Anwendung mit Adobe® AIR® entwickeln, veröffentlichen Sie das Installationsprogramm der AIR-Anwendung, damit die Benutzer die Anwendung auf ihren Computer herunterladen und installieren können.

Weitere Informationen zum Entwickeln von benutzerdefinierten Videowiedergabeanwendungen für Adobe Access finden Sie im Kapitel &quot;Arbeiten mit &quot;im [ActionScript 3.0 Entwicklerhandbuch](https://help.adobe.com/en_US/as3/dev/WS9936fa0d5984e93b3f4f38ec1272a447844-8000.html)*, *im [Adobe Video Technology Center](https://www.adobe.com/devnet/video/) und im Open Source Media Framework.