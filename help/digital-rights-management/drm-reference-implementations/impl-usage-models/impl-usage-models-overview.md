---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Übersicht{#overview}

Die Referenzimplementierung enthält eine Demomodusoption, die zeigt, wie verschiedene Nutzungsmodelle für ein Segment mit gepackten Inhalten implementiert werden. Der Demomodus bietet Geschäftslogik für diese Nutzungsmodelle:

* **Download-To-Own (DTO)** - Benutzer können den Inhalt online oder offline herunterladen und erhalten eine permanente Lizenz für den Inhalt.
* **Miete/Video-On-Demand (VOD)** - Der verfügbare Inhalt umfasst zeitbasierte Einschränkungen. Beispielsweise können Benutzer Inhalte für einen Zeitraum von 30 Tagen abspielen. Sobald die Wiedergabe beginnt, hat der Benutzer bis zu 48 Stunden Zeit, um die Wiedergabe des Inhalts abzuschließen. Der Inhalt muss in 30 Tagen angezeigt werden.
* **Anmeldung (alles, was Sie essen können)** - Einige Dienste bieten bezahlte Abonnements an, die den Nutzern unbegrenzten Zugang zu einer großen Inhaltsbibliothek bieten, solange sie weiterhin eine monatliche Gebühr zahlen. Der Lizenzserver erteilt für jedes Inhaltssegment eine eindeutige Lizenz und erteilt außerdem eine Stammlizenz, die am Ende des Abonnementzeitraums abläuft. Wenn Benutzer ihr Abonnement jeden Monat verlängern, muss auch die Root-Lizenz erneuert werden.

  >[!NOTE]
  >
  >Für die vorhergehenden Nutzungsmodelle müssen Benutzer nach dem Erwerb einer Lizenz ihre Anmeldeinformationen eingeben, damit der Server überprüfen kann, ob die Benutzer über ein Mietkonto verfügen.

* **Anzeigenfinanziert** - Inhalte werden monetarisiert, indem Werbung als Teil des Erlebnisses einbezogen wird. Mit diesem Modell können Inhalte verteilt werden und erfordern keine Benutzerauthentifizierung.

Im Demomodus des Nutzungsmodells steuert die Geschäftslogik auf dem Server die Attribute für generierte Lizenzen. Bei der Verpackung muss Ihre DRM-Richtlinie nur angeben, ob eine Authentifizierung erforderlich ist.

Um alle vier Nutzungsmodelle zu aktivieren, müssen Sie nur zwei DRM-Richtlinien einbeziehen:

* Eine DRM-Richtlinie, die einen anonymen Zugriff für das Ad-based-Modell ermöglicht
* Eine DRM-Richtlinie, die eine Authentifizierung mit Benutzername/Kennwort für die anderen drei Nutzungsmodelle erfordert.

Wenn ein Benutzer eine Lizenz anfordert, kann eine Client-Anwendung anhand der Authentifizierungsinformationen in den DRM-Richtlinien bestimmen, ob der Benutzer zur Authentifizierung aufgefordert werden soll.
