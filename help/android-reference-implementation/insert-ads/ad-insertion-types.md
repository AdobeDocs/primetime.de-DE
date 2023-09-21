---
description: Das TVSDK bietet derzeit integrierte Metadatenunterstützung für Anzeigen-Anbieter für TVSDK-Anzeigen, Werbeunterbrechungen und benutzerdefinierte Anzeigenmarken.
title: Anzeigeneinfügetypen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Anzeigeneinfügetypen {#ad-insertion-types}

Das TVSDK bietet derzeit integrierte Metadatenunterstützung für Anzeigen-Anbieter für TVSDK-Anzeigen, Werbeunterbrechungen und benutzerdefinierte Anzeigenmarken.

Es unterstützt die folgenden Arten von Workflows zum Einfügen von Anzeigen für VOD und Live-/Lineare Inhalte.

<table id="table_1C3A659BDDB7453CA953A103045FCA01"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Einfügetyp </th> 
   <th colname="col2" class="entry"> Unterstützt in ... </th> 
   <th colname="col3" class="entry"> Beschreibung </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Adobe Primetime-Anzeigen-Entscheidungsfindungs-Anzeigen </td> 
   <td colname="col2">VOD <p>Live </p> <p>Linear </p> </td> 
   <td colname="col3">Die Referenzimplementierung bietet <span class="codeph"> AuditudeMetadata</span> Informationen, die basierend auf den Informationen im Abschnitt "Primetime-Anzeigen"für die Primetime-Anzeigenentscheidung (früher als Auditude bezeichnet) mit dem Server verbunden werden sollen.</a> der JSON-Konfigurationsdatei</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Direkte Werbeunterbrechungen </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Sie müssen Anzeigen-URLs in der JSON-Eingabedatei angeben. Wenn das TVSDK versucht, eine Anzeige aufzulösen, ruft es den Resolver für die direkte Werbeunterbrechung auf und löst die Anzeigen auf der Grundlage der direkten Anzeige auf Informationen auf, die in der JSON-Konfigurationsdatei bereitgestellt werden</a>. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Benutzerdefinierte Anzeigenmarken </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3">Benutzerdefinierte Anzeigenmarkierungen sind nützlich, wenn der Video-Stream sowohl Hauptinhalte als auch Anzeigen enthält, jedoch keine Informationen zu den Anzeigenpositionen und der Anzeigenzeit enthält. Wenn die Anzeigenpositionsinformationen auf andere Weise abgerufen werden, z. B. über ein externes CMS, können Sie benutzerdefinierte Anzeigenmarkierungen definieren und an die Player-Timeline übergeben. <p>Um einen Player für das Einfügen von Anzeigen einzurichten, müssen Sie Anzeigenmetadaten im Abschnitt für benutzerdefinierte Anzeigenmetadaten der JSON-Konfigurationsdatei übergeben.</a>, die eine unterstützende Implementierung des Anzeigenanbieters in der Referenzimplementierung enthält. </p> </td>
  </tr>
 </tbody>
</table>
