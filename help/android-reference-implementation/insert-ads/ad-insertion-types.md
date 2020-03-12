---
description: Das TVSDK bietet derzeit integrierte Metadatenunterstützung für Anzeigen-Provider für TVSDK-Anzeigen, direkte Werbeunterbrechungen und benutzerdefinierte Anzeigenmarken.
seo-description: Das TVSDK bietet derzeit integrierte Metadatenunterstützung für Anzeigen-Provider für TVSDK-Anzeigen, direkte Werbeunterbrechungen und benutzerdefinierte Anzeigenmarken.
seo-title: Anzeigeneinfügetypen
title: Anzeigeneinfügetypen
uuid: 6b5c3555-1ddd-4215-8bb2-03d16bb818c5
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Anzeigeneinfügetypen {#ad-insertion-types}

Das TVSDK bietet derzeit integrierte Metadatenunterstützung für Anzeigen-Provider für TVSDK-Anzeigen, direkte Werbeunterbrechungen und benutzerdefinierte Anzeigenmarken.

Es unterstützt die folgenden Typen von Workflows für die Anzeigeneinfügung für VOD und Live/Lineare Inhalte.

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Einfügetyp </th> 
   <th colname="col2" class="entry"> Unterstützt in... </th> 
   <th colname="col3" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Adobe Primetime-Werbeanzeigen </td> 
   <td colname="col2">VOD <p>Live </p> <p>Linear </p> </td> 
   <td colname="col3">Die Referenzimplementierung stellt <span class="codeph"> AuditudeMetadaten</span> -Informationen bereit, die für Primetime-Anzeigenentscheidungen (früher Auditude genannt) mit dem Server verbunden werden, basierend auf den Informationen, die im Abschnitt</a> Primetime-Anzeigen der JSON-Konfigurationsdatei</a>bereitgestellt werden. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Direkte Werbeunterbrechungen </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Sie müssen Anzeigen-URLs in der JSON-Eingabedatei angeben. Wenn das TVSDK versucht, eine Anzeige aufzulösen, ruft es den Auflöser für den direkten Werbeunterbrechungsaufruf auf und löst die Anzeigen auf der Grundlage der Informationen über den Umbruch in der JSON-Konfigurationsdatei</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Benutzerspezifische Anzeigenmarken </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Benutzerspezifische Anzeigenmarkierungen sind nützlich, wenn der Videostream sowohl Hauptinhalt als auch Anzeigen enthält, jedoch keine Informationen zu den Anzeigenpositionen und -zeitpunkten enthält. Wenn die Positionierungsinformationen der Anzeige auf andere Weise abgerufen werden, z. B. über ein externes CMS, können Sie benutzerdefinierte Anzeigenmarken definieren und an die Player-Zeitleiste weiterleiten. <p>Um einen Player für das Einfügen von Anzeigen einzurichten, müssen Sie Anzeigenmetadaten im Abschnitt "Benutzerspezifische Anzeigenmetadaten"der JSON-Konfigurationsdatei</a>übergeben, die über eine unterstützende Ad-Provider-Implementierung in der Referenz-Implementierung verfügt. </p> </td>
  </tr>
 </tbody>
</table>