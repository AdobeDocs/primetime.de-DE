---
title: Aktualisieren der Referenzimplementierung DB
description: Aktualisieren der Referenzimplementierung DB
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Aktualisieren der Referenzimplementierung DB{#update-the-reference-implementation-db}

Fügen Sie der Referenzimplementierungsdatenbank Einträge hinzu, um Nutzungsmodelle zu steuern, unter denen eine Lizenz für einen bestimmten Benutzer ausgestellt wird.

1. Fügen Sie Einträge zu `Customer` Tabelle.

   Die `Customer` -Tabelle enthält Benutzernamen und Kennwörter, um Benutzer zu authentifizieren. Außerdem wird angegeben, ob ein Benutzer über ein Abonnement verfügt (eine Lizenz, die im Rahmen der *Abonnement* Nutzungsmodell).

1. Gewähren Sie einem Benutzer Zugriff über die Nutzungsmodelle Download-to-own oder Video-on-Demand.

       Fügen Sie der Tabelle &quot;CustomerAuthorization&quot;Einträge hinzu, um Folgendes anzugeben:
   
   * Das Nutzungsmodell
   * Jedes Inhaltssegment, auf das ein Benutzer zugreifen kann

Weitere Informationen zum Füllen der einzelnen Tabellen finden Sie unter [!DNL PopulateSampleDB.sql] Skript (auf Ihrer Primetime DRM-DVD im [!DNL Reference Implementation/Server/Reference Implementation Server/dbscript/] Verzeichnis).
