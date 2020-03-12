---
description: 'null'
seo-description: 'null'
seo-title: Übersicht
title: Übersicht
uuid: 5f82f603-6e2d-4c9d-a49f-7b07f30a29e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht{#overview}

Die Referenzimplementierung enthält eine Demomodusoption, die zeigt, wie verschiedene Nutzungsmodelle für ein Segment mit gepackten Inhalten implementiert werden. Der Demomodus enthält Geschäftslogik für diese Verwendungsmodelle:

* **Download-To-Own (DTO)** - Benutzer können die Inhalte online oder offline herunterladen und erhalten eine permanente Lizenz für die Inhalte.
* **Miete/Video-On-Demand (VOD)** - Der verfügbare Inhalt unterliegt zeitbedingten Einschränkungen. Beispielsweise können Benutzer Inhalte innerhalb von 30 Tagen abspielen. Sobald die Wiedergabe beginnt, hat der Benutzer bis zu 48 Stunden Zeit, um die Wiedergabe abzuschließen. Der Inhalt muss in 30 Tagen angezeigt werden.
* **Abonnement (all-you-can-eat)** - Manche Services Angebot kostenpflichtige Abonnement, die Benutzern unbegrenzten Zugriff auf eine umfangreiche Inhaltsbibliothek gewähren, solange sie weiterhin eine monatliche Gebühr zahlen. Der Lizenzserver stellt für jedes Inhaltssegment eine eindeutige Lizenz aus und gibt auch eine Stammlizenz aus, die am Ende des Abonnements abläuft. Wenn die Benutzer ihr Abonnement monatlich erneuern, muss die Root-Lizenz ebenfalls erneuert werden.

   >[!NOTE]
   >
   >Bei den vorherigen Verwendungsmodellen müssen Benutzer nach Erwerb einer Lizenz ihre Anmeldeinformationen eingeben, damit der Server überprüfen kann, ob die Benutzer über ein Mietkonto verfügen.

* **Werbemittel** - Inhalte werden monetarisiert, indem Werbung als Teil der Erfahrung einbezogen wird. Bei diesem Modell können Inhalte verteilt werden, ohne dass eine Benutzerauthentifizierung erforderlich ist.

Im Demomodulmodus steuert die Geschäftslogik auf dem Server die Attribute für generierte Lizenzen. Bei der Verpackung muss Ihre DRM-Richtlinie lediglich angeben, ob eine Authentifizierung erforderlich ist.

Um alle vier Nutzungsmodelle zu aktivieren, müssen Sie nur zwei DRM-Richtlinien einschließen:

* Eine DRM-Richtlinie, die einen anonymen Zugriff für das Ad-finanzierte Modell ermöglicht
* Eine DRM-Richtlinie, die die Authentifizierung des Benutzernamens/Kennworts für die anderen drei Verwendungsmodelle erfordert.

Wenn ein Benutzer eine Lizenz anfordert, kann eine Clientanwendung anhand der Authentifizierungsinformationen in den DRM-Richtlinien festlegen, ob der Benutzer zur Authentifizierung aufgefordert werden soll.
