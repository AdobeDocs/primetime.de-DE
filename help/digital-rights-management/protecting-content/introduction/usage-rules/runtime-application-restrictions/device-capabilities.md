---
title: Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind
description: Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind{#device-capabilities-required-to-play-protected-content}

Die erforderlichen Gerätefunktionen geben die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind. Informationen zu den Hardwarefunktionen stehen für Geräte zur Verfügung, die das Portierungs-Kit verwenden.

Die folgenden Attribute können die Gerätefunktionen identifizieren:

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>Attribut</b> </td> 
   <td><b>Unterstützte Werte</b> </td> 
   <td><b>Übereinstimmungskriterien</b> </td> 
   <td><b>Beschreibung</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Benutzerfreundlicher Bus </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"oder "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exakte Übereinstimmung </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Wenn "true", darf das Gerät keinen benutzerfreundlichen Bus haben. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Hardwarestamm von Trust </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true"oder "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Exakte Übereinstimmung </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Wenn "true", muss das Gerät über einen Hardware-Stammordner für die Vertrauenswürdigkeit verfügen. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Diese Nutzungsregel wird von Adobe Primetime DRM-Clients ab Version 2.0.2 unterstützt. Das Verhalten älterer Clients hängt von der vom Lizenzserver unterstützten Clientversion ab.
>
>Siehe [Minimale Client-Version](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md).

