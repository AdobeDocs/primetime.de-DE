---
description: Die Hauptkomponenten von Adobe Access bestehen aus einem Java-SDK und den Flash Player- und Adobe AIR-Client-Laufzeitumgebungen.
title: Java-SDK, Flash Player und Adobe AIR-Client
exl-id: 2df4da13-8df9-442b-8638-317c41d62fbe
source-git-commit: 8d7a4f69a6400b0c3242d4cb0c5daac81f27db3a
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Adobe-Access-Komponenten{#adobe-access-components}

Die Hauptkomponenten von Adobe Access bestehen aus einem Java-SDK und den Flash Player- und Adobe AIR-Client-Laufzeitumgebungen.

Weitere Informationen zum Einrichten des SDK finden Sie unter Einrichten des SDK in *Verwenden des Adobe Access SDK zum Schutz von Inhalten.*

Mit dem Adobe Access SDK können Sie eine Digital Rights Management-Lösung entwickeln, die in die bestehende Unternehmensinfrastruktur Ihres Unternehmens integriert wird, z. B. in Content Management, Abrechnung und Zugriffssteuerungssysteme für Benutzer. Mit Flash Player und Adobe AIR können Sie Anwendungen erstellen und einfach bereitstellen, über die Verbraucher auf große Bibliotheken digitaler Inhalte zugreifen und diese anzeigen können.

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access wird als Java-SDK bereitgestellt, das die Bausteine bereitstellt, aus denen Sie eine Serverimplementierung erstellen können. Mithilfe des SDK können Sie eine Adobe Access-Lösung erstellen, die dem Geschäftsmodell Ihres Unternehmens entspricht.

Die im SDK bereitgestellten Java-APIs werden in den folgenden Unterabschnitten beschrieben.

## Java-APIs zum Verwalten von Gerätegruppendomänen {#java-apis-for-managing-device-group-domains}

Mit diesen APIs kann der Server Clientanfragen zum Aufnehmen und Verlassen von Gerätegruppendomänen verarbeiten.

Eine Gerätegruppendomäne ist eine logische Sammlung von Geräten, die Lizenzen untereinander teilen können. Damit dies geschehen kann, muss sich jedes Gerät zuerst bei derselben Domäne anmelden/registrieren. Das Adobe Access SDK, das auf einem Server ausgeführt wird, muss die Anfragen zum Beitritt zur Gerätedomäne (Registrierung) sowie zum Austritt aus der Gerätedomäne (Aufhebung der Registrierung) verarbeiten. Geräte, die nicht mit einer Domäne verbunden sind, erhalten Lizenzen, die an dieses Gerät gebunden sind und nicht für andere Geräte freigegeben werden können.

## Java-APIs zum Schutz von Inhalten {#java-apis-for-protecting-content}

Mit diesen APIs können Sie Rechte definieren und Inhalte für die Verteilung vorbereiten. Die Content Protection-APIs sind:

* Richtlinienmanagement

  Die Policy Management-API wird verwendet, um Richtlinien zu erstellen und zu ändern, die auf Inhalte angewendet werden sollen. Richtlinien können erstellt oder aktualisiert werden, einschließlich Abrufen/Einstellen aller Nutzungsregeln und Ermöglichung zusätzlicher Parameter in einem benutzerdefinierten Namespace.

* Inhaltsverpackung

  Die Inhaltspaketungs-API wird verwendet, um Inhalte zu verschlüsseln und Metadaten aus dem gepackten Inhalt abzurufen.

## Java-APIs für die Lizenzerteilung {#java-apis-for-issuing-licenses}

Diese APIs werden verwendet, wenn ein Client eine Lizenz vom Server anfordert. Das SDK unterstützt die folgenden Anforderungen vom Client:

* Authentifizierung

  Die Authentifizierungs-API kann verwendet werden, um Authentifizierungsanfragen zu verarbeiten und Authentifizierungstoken zu generieren.

* Lizenzerstellung und -akquise

  Die API zur Lizenzerstellung und -akquise wird verwendet, um eine Lizenz für den Benutzer zu generieren.

* Unterstützung für Adobe AIR-Clients und -Inhalte der Version 1.5

  Aus Gründen der Abwärtskompatibilität verfügt das SDK über APIs zur Verarbeitung von Anfragen aus AIR-Anwendungen, die für die Verwendung mit AIR-Version 1.5 und früheren Clients sowie geschützten Inhalten erstellt wurden.

## Referenzimplementierung {#reference-implementation}

Das SDK enthält eine Referenzimplementierung, eine einfache Adobe Access-Bereitstellung, die die Verwendung der Java-APIs veranschaulicht. Die Referenzimplementierung bietet einen Lizenzserver, einen Watched Folder Packager, eine Adobe Access Manager AIR-Anwendung sowie Befehlszeilen-Tools für die Inhaltspaketung und Richtlinienverwaltung basierend auf den Java-APIs. Weitere Informationen zur Adobe Access-Referenzimplementierung finden Sie unter *Schutz von Inhalten*.

## Adobe Access Server für geschütztes Streaming {#adobe-access-server-for-protected-streaming}

Für Streaming-Anwendungsfälle, bei denen Inhalte mit Adobe Access geschützt sind, wie zum Beispiel für Adobe-HTTP Dynamic Streaming, umfasst die Software auch Adobe Access Server für geschütztes Streaming. Diese Lösung kann einfach in einem Servlet-Container wie Tomcat bereitgestellt werden und kann eine hohe Skalierbarkeit und Leistung erzielen, um die größten Anforderungen an die Inhaltsverteilung zu erfüllen.

## Adobe Flash Player {#adobe-flash-player}

Flash Player ist ein leichtes Browser-Plug-in und eine Laufzeitumgebung, das konsistente und ansprechende Benutzererlebnisse, atemberaubende Audio-/Videowiedergabe und weit reichende Reichweite bietet. Flash Player ermöglicht die Wiedergabe von gestreamten oder heruntergeladenen Videoinhalten in hoher Qualität. Für Herausgeber von Inhalten bietet Flash Player die Möglichkeit, die Wiedergabescreen, die Inhalte umgeben, anzupassen und so durch Werbung mit Bannern und Überlagerungen ein tieferes Branding-Erlebnis und Monetarisierung zu ermöglichen. Für Verbraucher bietet Flash Player eine intuitive und visuell ansprechende Möglichkeit, Videoinhalte anzuzeigen.

Weitere Informationen zum Flash Player finden Sie unter: [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR ist eine betriebssystemübergreifende Laufzeitumgebung, mit der Inhaltsersteller ihre bereits getätigten Investitionen im Web auf den Desktop ausweiten können, indem sie benutzerdefinierte Multimedia-Anwendungen entwerfen. Basierend auf bewährten, offenen Technologien bietet es eine zuverlässige, vereinfachte Möglichkeit für Unternehmen, benutzerdefinierte Anwendungen zu entwickeln und bereitzustellen, mit denen vertraut werden kann, dass sie eine sicherere und angenehmere Benutzererfahrung bieten. Adobe AIR ermöglicht Unternehmen die einfache Integration von Rich Media, um ein interaktiveres Benutzererlebnis zu schaffen. Damit können Entwickler bekannte Tools wie HTML, JavaScript, Flash oder Adobe® Flex® verwenden, um ihre einzigartige Kombination aus Rich-Internet-Anwendungen unter Windows, Macintosh oder Linux bereitzustellen.

Unternehmen haben die vollständige Kontrolle über die Benutzeroberfläche und können ein Benutzererlebnis gestalten, um ihre Marke widerzuspiegeln und zu stärken. Dank der integrierten Unterstützung für die Wiedergabe von mit dem Adobe Access SDK geschützten Inhalten hilft Adobe AIR bei der Erstellung benutzerdefinierter, durchgängiger Inhaltsverteilungsketten.

## Native iOS- und Android-Anwendungen {#native-ios-and-android-applications}

Native iOS- und Android-Anwendungen Nur für Adobe Primetime-Kunden verfügbar, Adobe-Zugriff DRM 4.0 und höher kann verwendet werden, um Videos zu schützen, die in nativen (Nicht-Flash-)Anwendungen auf Mobilgeräten verwendet werden. Damit eine Anwendung diesen geschützten Inhalt nutzen kann, muss sie mithilfe der Adobe Primetime Client-Bibliotheken implementiert werden.

Weitere Informationen zu Adobe Primetime finden Sie unter: [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)
