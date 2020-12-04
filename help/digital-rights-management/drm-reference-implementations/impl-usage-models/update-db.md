---
seo-title: Aktualisieren der Referenz-Implementierung DB
title: Aktualisieren der Referenz-Implementierung DB
uuid: 2883045e-ad62-466d-94a2-fc45ded2a4f5
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Aktualisieren Sie die Referenzimplementierung DB{#update-the-reference-implementation-db}

Fügen Sie der Referenz-Implementierungsdatenbank Einträge hinzu, um Nutzungsmodelle zu steuern, unter denen eine Lizenz für einen bestimmten Benutzer ausgestellt wird.

1. hinzufügen Einträge in die Tabelle `Customer`.

   Die Tabelle `Customer` enthält Benutzernamen und Kennwörter zur Authentifizierung von Benutzern. Es gibt auch an, ob ein Benutzer über ein Abonnement verfügt (eine Lizenz, die unter dem Gebrauchsmodell *Abonnement* erteilt wird).

1. Gewähren Sie einem Benutzer Zugriff auf die Nutzungsmodelle &quot;Download-to-Owned&quot;oder &quot;Video-on-Demand&quot;.

       hinzufügen Einträge in der Tabelle &quot;CustomerAuthorization&quot;, um Folgendes anzugeben:
   
   * Das Nutzungsmodell
   * Jedes Inhaltssegment, auf das ein Benutzer zugreifen kann

Weitere Informationen zum Füllen der einzelnen Tabellen finden Sie im Skript [!DNL PopulateSampleDB.sql] (auf Ihrer Primetime DRM-DVD im Ordner [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] enthalten).
