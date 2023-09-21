---
description: Die Hauptkomponenten von Primetime DRM bestehen aus einem Java-SDK und den Client-Laufzeitumgebungen Flash Player und Adobe AIR .
title: Java-SDK, Flash Player und Adobe AIR-Client
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ADOBE PRIMETIME DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM wird als Java-SDK bereitgestellt, das die Bausteine bereitstellt, aus denen Sie eine Serverimplementierung erstellen können. Mithilfe des SDK können Sie eine Primetime DRM-Lösung erstellen, die dem Geschäftsmodell Ihres Unternehmens entspricht.

Die im SDK bereitgestellten Java-APIs werden in den folgenden Unterabschnitten beschrieben.

## Java-APIs zum Verwalten von Gerätegruppendomänen{#java-apis-for-managing-device-group-domains}

Mit diesen APIs kann der Server Clientanfragen zum Aufnehmen und Verlassen von Gerätegruppendomänen verarbeiten.

Eine Gerätegruppendomäne ist eine logische Sammlung von Geräten, die Lizenzen untereinander teilen können. Damit dies geschehen kann, muss sich jedes Gerät zuerst bei derselben Domäne anmelden/registrieren. Das auf einem Server ausgeführte Primetime-DRM-SDK muss die Anfragen zum Beitritt zur Gerätedomäne (Registrierung) sowie zum Austritt aus der Gerätedomäne (Aufhebung der Registrierung) verarbeiten. Geräte, die nicht mit einer Domäne verbunden sind, erhalten Lizenzen, die an dieses Gerät gebunden sind und nicht für andere Geräte freigegeben werden können.

## Java-APIs zum Schutz von Inhalten{#java-apis-for-protecting-content}

Mit diesen APIs können Sie Rechte definieren und Inhalte für die Verteilung vorbereiten. Die Content Protection-APIs sind:

* Richtlinienmanagement

  Die Policy Management-API wird verwendet, um Richtlinien zu erstellen und zu ändern, die auf Inhalte angewendet werden sollen. Richtlinien können erstellt oder aktualisiert werden, einschließlich Abrufen/Einstellen aller Nutzungsregeln und Ermöglichung zusätzlicher Parameter in einem benutzerdefinierten Namespace.

* Inhaltsverpackung

  Die Inhaltspaketungs-API wird verwendet, um Inhalte zu verschlüsseln und Metadaten aus dem gepackten Inhalt abzurufen.

## Java-APIs für die Lizenzerteilung{#java-apis-for-issuing-licenses}

Diese APIs werden verwendet, wenn ein Client eine Lizenz vom Server anfordert. Das SDK unterstützt die folgenden Anforderungen vom Client:

* Authentifizierung

  Die Authentifizierungs-API kann verwendet werden, um Authentifizierungsanfragen zu verarbeiten und Authentifizierungstoken zu generieren.

* Lizenzerstellung und -akquise

  Die API zur Lizenzerstellung und -akquise wird verwendet, um eine Lizenz für den Benutzer zu generieren.

* Unterstützung für Adobe AIR-Clients und -Inhalte der Version 1.5

  Aus Gründen der Abwärtskompatibilität verfügt das SDK über APIs zur Verarbeitung von Anfragen aus AIR-Anwendungen, die für die Verwendung mit AIR-Version 1.5 und früheren Clients sowie geschützten Inhalten erstellt wurden.

## Referenzimplementierung {#reference-implementation}

Das SDK enthält eine Referenzimplementierung, eine einfache Adobe Primetime DRM-Bereitstellung, die die Verwendung der Java-APIs veranschaulicht. Die Referenzimplementierung bietet einen Lizenzserver, einen Watched Folder Packager, eine Primetime DRM Manager AIR-Anwendung sowie Befehlszeilen-Tools für die Inhaltspaketung und Richtlinienverwaltung basierend auf den Java-APIs. Weitere Informationen zur Primetime DRM-Referenzimplementierung finden Sie unter Schutz von Inhalten.
