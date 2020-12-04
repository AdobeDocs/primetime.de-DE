---
description: Die Hauptkomponenten von Adobe Access bestehen aus einem Java SDK und den Flash Player- und Adobe AIR Client-Laufzeitumgebungen.
seo-description: Die Hauptkomponenten von Adobe Access bestehen aus einem Java SDK und den Flash Player- und Adobe AIR Client-Laufzeitumgebungen.
seo-title: Java SDK-, Flash Player- und Adobe AIR-Client
title: Java SDK-, Flash Player- und Adobe AIR-Client
uuid: 6b6c5aa2-56ee-4476-a05b-dcbbe3b9001e
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 0%

---


# Komponenten für den Zugriff auf Adoben{#adobe-access-components}

Die Hauptkomponenten von Adobe Access bestehen aus einem Java SDK und den Flash Player- und Adobe AIR Client-Laufzeitumgebungen.

Weitere Informationen zum Einrichten des SDK finden Sie unter Einrichten des SDK in *Verwenden des Adobe Access SDK zum Schützen von Inhalten.*

Mit dem Adobe Access SDK können Sie eine Lösung zur Verwaltung digitaler Rechte entwickeln, die in die bestehende Unternehmensinfrastruktur Ihres Unternehmens integriert ist, z. B. in Content-Management-, Abrechnungs- und Benutzersysteme. Die Zugriffskontrolle erfolgt über das SDK. Mit Flash Player und Adobe AIR können Sie Anwendungen erstellen und einfach bereitstellen, mit denen Benutzer auf große Bibliotheken digitaler Inhalte zugreifen und diese Ansicht durchführen können.

## Adobe Access SDK {#section_6AA3DC7BAE354472AE179BBC9AF6BD27}

Adobe Access wird als Java-SDK bereitgestellt, das die Bausteine bereitstellt, aus denen Sie eine Serverimplementierung erstellen können. Mithilfe des SDK können Sie eine Adobe Access-Lösung erstellen, die dem Geschäftsmodell Ihres Unternehmens entspricht.

Die im SDK bereitgestellten Java-APIs werden in den folgenden Unterabschnitten beschrieben.

## Java-APIs zum Verwalten von Gerätegruppendomänen {#java-apis-for-managing-device-group-domains}

Diese APIs ermöglichen es dem Server, Clientanforderungen zum Verbinden und Verlassen von Gerätegruppendomänen zu bearbeiten.

Eine Gerätegruppendomäne ist eine logische Sammlung von Geräten, die Lizenzen untereinander austauschen können. Damit dies geschieht, muss sich jedes Gerät zuerst bei derselben Domäne anmelden/registrieren. Das Adobe Access SDK, das auf einem Server ausgeführt wird, muss die Verbindungsanfragen für die Gerätedomäne (Registrierung) sowie die Anforderung zum Erlöschen der Gerätedomäne (Entregistrierung) bearbeiten. Geräte, die nicht mit einer Domäne verbunden sind, erhalten Lizenzen, die an dieses Gerät gebunden sind, die nicht für andere Geräte freigegeben werden können.

## Java-APIs zum Schutz von Inhalten {#java-apis-for-protecting-content}

Mit diesen APIs werden Rechte definiert und Inhalte für die Verteilung vorbereitet. Die Content Protection-APIs sind:

* Politikmanagement

   Die Policy-Management-API wird zum Erstellen und Ändern von Richtlinien verwendet, die auf Inhalte angewendet werden sollen. Richtlinien können erstellt oder aktualisiert werden, einschließlich Abrufen/Einstellen aller Nutzungsregeln und Zulassen zusätzlicher Parameter in einem benutzerdefinierten Namensraum.

* Inhaltsverpackung

   Die API zur Inhaltspakete wird verwendet, um Inhalte zu verschlüsseln und Metadaten aus dem gepackten Inhalt abzurufen.

## Java-APIs für die Lizenzerteilung {#java-apis-for-issuing-licenses}

Diese APIs werden verwendet, wenn ein Client eine Lizenz vom Server anfordert. Das SDK unterstützt die folgenden Anforderungen vom Client:

* Authentifizierung

   Die Authentifizierungs-API kann verwendet werden, um Authentifizierungsanforderungen zu bearbeiten und Authentifizierungstoken zu generieren.

* Lizenzerstellung und -erwerb

   Die API zur Lizenzerstellung und Akquise wird verwendet, um eine Lizenz für den Benutzer zu generieren.

* Unterstützung von Clients und Inhalten der Adobe AIR Version 1.5

   Aus Gründen der Abwärtskompatibilität verfügt das SDK über APIs, um Anforderungen von AIR-Anwendungen zu bearbeiten, die für die Verwendung mit AIR-Clients der Version 1.5 und früher und geschützten Inhalten erstellt wurden.

## Referenz-Implementierung {#reference-implementation}

Das SDK enthält eine Referenzimplementierung, eine einfache Bereitstellung für den Zugriff auf Adoben, die die Verwendung der Java-APIs veranschaulicht. Die Referenzimplementierung bietet eine Lizenzserver-, Watched Folder Packager-, Adobe Access Manager AIR-Anwendung und Befehlszeilenwerkzeuge zum Verpacken und Verwalten von Inhalten basierend auf den Java-APIs. Weitere Informationen zur Implementierung der Adobe Access-Referenz finden Sie unter *Inhalte schützen*.

## Adobe Access Server für geschütztes Streaming {#adobe-access-server-for-protected-streaming}

Für Streaming-Anwendungen, bei denen Inhalte mit Adobe Access geschützt sind, z. B. für Adobe HTTP Dynamic Streaming, umfasst die Software auch Adobe Access Server für Protected Streaming. Diese Lösung kann einfach auf einem Servlet-Container wie Tomcat bereitgestellt werden und kann ein hohes Maß an Skalierbarkeit und Leistung erzielen, um den größten Inhaltsverteilungsbedarf zu decken.

## Adobe Flash Player {#adobe-flash-player}

Flash Player ist ein leichtes Browser-Plug-in und eine Laufzeitumgebung, mit denen Sie konsistente und ansprechende Benutzererfahrungen, eine beeindruckende Audio-/Videowiedergabe und eine durchgängige Reichweite erzielen können. Flash Player bietet eine hochwertige Wiedergabe von Streaming- oder heruntergeladenen Videoinhalten. Für Herausgeber von Inhalten bietet Flash Player die Möglichkeit, die Wiedergabebildschirme, die Inhalte umgeben, anzupassen, sodass Sie durch Anzeigen mit Bannern und Überlagerungen tiefere Branding-Erlebnisse und eine Monetarisierung erzielen können. Flash Player stellt eine intuitive und visuell ansprechende Methode zur Ansicht von Videoinhalten dar.

Weitere Informationen zu Flash Playern finden Sie unter: [www.adobe.com/go/flashplayer](https://www.adobe.com/go/flashplayer)

## Adobe AIR {#adobe-air}

Adobe AIR ist eine betriebssystemübergreifende Laufzeitumgebung, die es Inhaltsproduzenten ermöglicht, ihre bestehenden Investitionen im Web auf den Desktop auszudehnen, indem sie benutzerdefinierte Multimedia-Anwendungen entwickeln. Basierend auf bewährten, offenen Technologien bietet es Unternehmen eine zuverlässige, vereinfachte Möglichkeit, benutzerdefinierte Anwendungen zu entwickeln und bereitzustellen, die darauf vertrauen können, dass sie eine sicherere und angenehmere Benutzererfahrung bieten. Adobe AIR ermöglicht Unternehmen die einfache Integration von Rich-Media-Inhalten, um eine noch interaktivere Benutzererfahrung zu schaffen. Damit können Entwickler vertraute Tools wie HTML, JavaScript, Flash oder Adobe®-Flex® verwenden, um ihre einzigartige Kombination aus Rich-Internet-Anwendungen für Windows, Macintosh oder Linux bereitzustellen.

Unternehmen haben die vollständige Kontrolle über die Benutzeroberfläche und können eine Benutzererfahrung entwickeln, die ihre Marke widerspiegelt und stärkt. Dank der integrierten Unterstützung für die Wiedergabe von mit dem Adobe Access SDK geschützten Inhalten können Sie mit Adobe AIR benutzerspezifische, End-to-End-Verteilungsketten erstellen.

Weitere Informationen zu Adobe AIR finden Sie unter: [www.adobe.com/go/air](https://www.adobe.com/go/air)

## Native iOS- und Android-Anwendungen {#native-ios-and-android-applications}

Native iOS- und Android-Anwendungen Nur für Adobe Primetime-Kunden verfügbar. Adobe Access DRM 4.0 und höher kann zum Schutz von Videos verwendet werden, die in nativen Anwendungen (ohne Flash) auf Mobilgeräten verwendet werden. Damit eine Anwendung diese geschützten Inhalte nutzen kann, muss sie mithilfe der Adobe Primetime Client-Bibliotheken implementiert werden.

Weitere Informationen zu Adobe Primetime finden Sie unter: [https://www.adobe.com/solutions/primetime.html](https://www.adobe.com/solutions/primetime.html)