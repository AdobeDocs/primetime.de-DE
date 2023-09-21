---
description: Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste).
title: Anforderungen an Inhalt und Manifest
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Anforderungen an Inhalt und Manifest{#content-and-manifest-requirements}

Überprüfen Sie die Einschränkungen und Anforderungen für Streams und Wiedergabelisten (Manifeste).

<table id="table_D7C38CD3B4D24C3D9A3B55D8CEFE7366"> 
 <tbody> 
  <tr> 
   <td colname="col1"> Dauer des Inhaltssegments </td> 
   <td colname="col2"> Die Dauer eines Segments darf die in der Manifestdatei angegebene Zieldauer nicht überschreiten. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Inhaltsanforderung </td> 
   <td colname="col2"> Jedes TS-Segment sollte mit einem Schlüsselrahmen beginnen. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> HLS-Inhalt </td> 
   <td colname="col2"> <p>Beachten Sie Folgendes: 
     <ul id="ul_B226605345EA46F69DA1380E16826117"> 
      <li id="li_6564DC0E879544BB8513DD2D1CFBA8DE">AAC-SSR-Audio wird nicht unterstützt. </li> 
      <li id="li_B73CAEBE4347406EA4DB25551B444BDA">Audio-Codecs AC3 und Enhanced AC3 werden nicht unterstützt. </li> 
      <li id="li_5986DD33C0FE485D99D4C00E2E6012CA">HLS-Streams mit Diskontinuität, jedoch werden keine Diskontinuitätsmarkierungen unterstützt. </li> 
      <li id="li_FED8686372DF4A39BAABC531BA4EB137">HLS Live unterstützt das Rollover von Zeitstempeln nicht. </li> 
      <li id="li_565CFBEAD9874BA48F6E25B0893BF131">Anzeigen im DVR-Fenster von HLS Live Streams werden nicht aufgelöst. </li> 
      <li id="li_7D22EA32C94240D79EDDA96D9E72FE8F">Der Byte-Bereich wird mit verschlüsseltem AES-128-Inhalt nicht unterstützt. </li> 
     </ul></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> DASH-Inhalt </td> 
   <td colname="col2"> <p>Beachten Sie Folgendes: 
     <ul id="ul_9D33C2418F9F49DEAE0E642301726F89"> 
      <li id="li_74C69A21A7BD4831B92F0D57900E1CB1">Bei Live-Streams: Das Live-Profil mit dynamischem Typ wird unterstützt. </li> 
      <li id="li_0C8743DB152047819D23C9F180998AD7">Für VOD-Streams: Das Live-Profil mit statischem Typ wird unterstützt. </li> 
      <li id="li_FBC6828663FB413798A4BDAF0B9831AA">Für VOD-Streams: Das On-Demand-Profil ist nicht für Anzeigen-Workflows zertifiziert. </li> 
      <li id="li_4393B9B1F6144BDEAE484C879750ED23">Die Wiedergabe von DASH-Streams mit mehreren Zeiträumen wird nicht unterstützt. </li> 
      <li id="li_6A2CEC4E974C4D44A45F5503A1A9D8D0">Eingebettete Untertitel (608/708), die über das Tag "Ein-/Ausgabehilfe"signalisiert wurden, werden unterstützt. </li> 
      <li id="li_EDE93DF4F3A64A53BA80877F701A8F0D">Fragmentierte/segmentierte VTT-Dateien werden nicht unterstützt. </li> 
      <li id="li_8897F73611194030A490A4FF1178364C">Streams mit inband-benutzerdefinierten Tags sind nicht zertifiziert. </li> 
     </ul></p> </td> 
  </tr> 
 </tbody> 
</table>
