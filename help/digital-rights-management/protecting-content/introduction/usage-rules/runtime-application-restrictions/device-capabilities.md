---
description: 'null'
seo-description: 'null'
seo-title: Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind
title: Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind
uuid: 1490711b-65d9-4716-8779-ae1da7d2c82c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Gerätefunktionen, die zum Abspielen geschützter Inhalte erforderlich sind {#device-capabilities-required-to-play-protected-content}

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

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Diese Nutzungsregel wird von Adobe Primetime DRM-Clients Version 2.0.2 und höher unterstützt. Das Verhalten älterer Clients hängt von der vom Lizenzserver unterstützten Clientversion ab.
>
>Siehe [Minimale Clientversion](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md).

