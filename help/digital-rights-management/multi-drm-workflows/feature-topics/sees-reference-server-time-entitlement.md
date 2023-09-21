---
description: Arbeiten Sie mit dem SEES zusammen, um zu sehen, wie Sie einen zeitbasierten Berechtigungsdienst mit ExpressPlay aktivieren.
title: Zeitbasierte Berechtigung für Referenz-Service
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Referenz-Dienst: Zeitbasierte Berechtigung {#reference-service-time-based-entitlement}

Arbeiten Sie mit dem SEES zusammen, um zu sehen, wie Sie einen zeitbasierten Berechtigungsdienst mit ExpressPlay aktivieren.

Der SEES erhält vom Client eine Berechtigungsanfrage (siehe Abschnitt Öffentliche API ). Der SEES-Server sucht nach dem CEK und IV basierend auf dem `contentID`, fügt die `expirationTime`und leitet die Anfrage an den ExpressPlay-Server weiter. Das endgültige ExpressPlay-Token ist zeitgebunden. Siehe Diagramm zur zeitbasierten Entitätssequenz unten. ![](assets/fees-time-based.png)

**Tabelle 1: Lizenzparameter, die vom Client gesendet werden**

| Abfrageparameter | Beschreibung | Erforderlich |
|---|---|---|
| `contentKey` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels | Ja |
| `iv` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung der Inhaltsverschlüsselung IV | Ja |
| `rentalDuration` | Mietdauer in Sekunden (Standard = 0) | Nein |

**Tabelle 2: Vom SEES-Server hinzugefügte Token-Einschränkungsparameter**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> Abfrageparameter </th> 
   <th class="entry"> Beschreibung </th> 
   <th class="entry"> Erforderlich? </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>Ablaufzeit dieses Tokens. Dieser Wert muss eine Zeichenfolge in <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> Datums-/Uhrzeitformat im ZZ-Zonenbezeichner ("Zulu-Zeit") oder eine Ganzzahl, der ein "+"-Zeichen vorangestellt ist. Ein Beispiel für eine RFC 3339-Datums-/Uhrzeitangabe ist <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Wenn der Wert eine Zeichenfolge im Datums-/Uhrzeitformat von RFC 339 ist, stellt er ein absolutes Ablaufdatum/eine absolute Ablaufzeit für das Token dar. Wenn der Wert eine Ganzzahl ist, der ein "+"-Zeichen vorangestellt ist, wird er als relative Anzahl von Sekunden ab Ausgabe interpretiert, dass das Token gültig ist. Beispiel: <span class="codeph"> +60</span> gibt eine Minute an. Die maximale (und standardmäßige, falls nicht angegeben) Token-Lebensdauer beträgt 30 Tage. Verwenden Sie das kodierte Formular "%2B", wenn Sie das "+"-Zeichen angeben. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>
