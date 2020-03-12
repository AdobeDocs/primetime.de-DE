---
description: Die Hauptkomponenten von Primetime DRM bestehen aus einem Java SDK und den Umgebung Flash Player und Adobe AIR Client Runtime.
seo-description: Die Hauptkomponenten von Primetime DRM bestehen aus einem Java SDK und den Umgebung Flash Player und Adobe AIR Client Runtime.
seo-title: Java SDK, Flash Player und Adobe AIR-Client
title: Java SDK, Flash Player und Adobe AIR-Client
uuid: e6daed27-3803-4ef7-ba25-4a180af7502f
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Primetime DRM SDK {#section_522E57DFEEFF4794978FF2D366B83690}

Primetime DRM wird als Java-SDK bereitgestellt, das die Bausteine bereitstellt, aus denen Sie eine Serverimplementierung erstellen können. Mithilfe des SDK können Sie eine Primetime DRM-Lösung erstellen, die für das Geschäftsmodell Ihres Unternehmens geeignet ist.

Die im SDK bereitgestellten Java-APIs werden in den folgenden Unterabschnitten beschrieben.

## Java-APIs zum Verwalten von Gerätegruppendomänen{#java-apis-for-managing-device-group-domains}

Diese APIs ermöglichen es dem Server, Clientanforderungen zum Verbinden und Verlassen von Gerätegruppendomänen zu bearbeiten.

Eine Gerätegruppendomäne ist eine logische Sammlung von Geräten, die Lizenzen untereinander austauschen können. Damit dies geschieht, muss sich jedes Gerät zuerst bei derselben Domäne anmelden/registrieren. Das Primetime-DRM-SDK, das auf einem Server ausgeführt wird, muss die Anforderungen zum Verbinden der Gerätedomäne (Registrierung) sowie zum Deaktivieren der Gerätedomänenfreigabe (Deregistrierung) bearbeiten. Geräte, die nicht mit einer Domäne verbunden sind, erhalten Lizenzen, die an dieses Gerät gebunden sind, die nicht für andere Geräte freigegeben werden können.

## Java-APIs zum Schutz von Inhalten{#java-apis-for-protecting-content}

Mit diesen APIs werden Rechte definiert und Inhalte für die Verteilung vorbereitet. Die Content Protection-APIs sind:

* Politikmanagement

   Die Policy-Management-API wird zum Erstellen und Ändern von Richtlinien verwendet, die auf Inhalte angewendet werden sollen. Richtlinien können erstellt oder aktualisiert werden, einschließlich Abrufen/Einstellen aller Nutzungsregeln und Zulassen zusätzlicher Parameter in einem benutzerdefinierten Namensraum.

* Inhaltsverpackung

   Die API zur Inhaltspakete wird verwendet, um Inhalte zu verschlüsseln und Metadaten aus dem gepackten Inhalt abzurufen.

## Java-APIs für die Lizenzerteilung{#java-apis-for-issuing-licenses}

Diese APIs werden verwendet, wenn ein Client eine Lizenz vom Server anfordert. Das SDK unterstützt die folgenden Anforderungen vom Client:

* Authentifizierung

   Die Authentifizierungs-API kann verwendet werden, um Authentifizierungsanforderungen zu bearbeiten und Authentifizierungstoken zu generieren.

* Lizenzerstellung und -erwerb

   Die API zur Lizenzerstellung und Akquise wird verwendet, um eine Lizenz für den Benutzer zu generieren.

* Unterstützung für Adobe AIR-Clients und -Inhalte der Version 1.5

   Aus Gründen der Abwärtskompatibilität verfügt das SDK über APIs, um Anforderungen von AIR-Anwendungen zu bearbeiten, die für die Verwendung mit AIR-Clients der Version 1.5 und früher und geschützten Inhalten erstellt wurden.

## Referenzimplementierung {#reference-implementation}

Das SDK enthält eine Referenz-Implementierung, eine einfache Adobe Primetime DRM-Bereitstellung, die die Verwendung der Java-APIs demonstriert. Die Referenzimplementierung bietet eine License Server-, Watched Folder Packager-, Primetime DRM Manager AIR-Anwendung sowie Befehlszeilenwerkzeuge für die Inhaltspakete und Richtlinienverwaltung basierend auf den Java-APIs. Weitere Informationen zur Primetime DRM-Referenzimplementierung finden Sie unter Schutz von Inhalten.