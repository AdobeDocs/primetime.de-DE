---
title: Erforderliche Gerätefunktionen zum Abspielen geschützter Inhalte
description: Erforderliche Gerätefunktionen zum Abspielen geschützter Inhalte
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Erforderliche Gerätefunktionen zum Abspielen geschützter Inhalte {#device-capabilities-required-to-play-protected-content}

Gibt die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind. Informationen zu den Hardwarefunktionen sind für Geräte verfügbar, die das Portierungs-Kit verwenden.

Die Gerätefunktionen können anhand der in der folgenden Tabelle angegebenen Attribute identifiziert werden:

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>Attribut</b> </td> 
   <td><b>Unterstützte Werte</b> </td> 
   <td><b>Übereinstimmungskriterien</b> </td> 
   <td><b>Beschreibung</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Bus ohne Benutzerzugriff </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"oder "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exakte Übereinstimmung </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Wenn "true", darf das Gerät keinen für Benutzer zugänglichen Bus haben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Hardware-Stamm des Vertrauens </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"oder "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exakt Macth </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Wenn "true", muss das Gerät über einen Hardware-Stamm des Vertrauens verfügen. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Diese Nutzungsregel wird von Adobe Access-Clients ab Version 2.0.2 unterstützt. Das Verhalten bei älteren Clients hängt von der vom Lizenzserver unterstützten Mindestversion des Clients ab. Siehe [Minimale Client-Version](../../../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md).
