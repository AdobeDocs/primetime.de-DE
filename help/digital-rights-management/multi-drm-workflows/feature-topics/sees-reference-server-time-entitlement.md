---
description: Arbeiten Sie mit dem SEES zusammen, um zu sehen, wie ein zeitbasierter Berechtigungsdienst mit ExpressPlay aktiviert wird.
title: Zeitbasierte Berechtigung für Referenz-Dienst
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Referenz-Dienst: Zeitbasierte Berechtigung {#reference-service-time-based-entitlement}

Arbeiten Sie mit dem SEES zusammen, um zu sehen, wie ein zeitbasierter Berechtigungsdienst mit ExpressPlay aktiviert wird.

Die SEES erhält eine Berechtigungsanfrage (siehe Abschnitt Öffentliche API) vom Client. Der SEES-Server sucht die CEK und IV basierend auf dem `contentID`, fügt das `expirationTime` hinzu und leitet die Anforderung an den ExpressPlay-Server weiter. Das letzte ExpressPlay-Token ist zeitgebunden. Siehe das unten stehende Diagramm zur Sequenz der zeitbasierten Berechtigung. ![](assets/fees-time-based.png)

**Tabelle 1: Vom Client gesendete Lizenzparameter**

| Abfrage-Parameter | Beschreibung | Erforderlich |
|---|---|---|
| `contentKey` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung des Inhaltsverschlüsselungsschlüssels | Ja |
| `iv` | Eine hexadezimale 16-Byte-Zeichenfolgendarstellung der Inhaltsverschlüsselung IV | Ja |
| `rentalDuration` | Mietdauer in Sekunden (Standard = 0) | Nein |

**Tabelle 2: Vom SEES-Server hinzugefügte Token-Eingrenzungsparameter**

<table id="table_E979FAD7A61A4832A46667301939FAEB">  
 <thead> 
  <tr> 
   <th class="entry"> Abfrage-Parameter </th> 
   <th class="entry"> Beschreibung </th> 
   <th class="entry"> Erforderlich? </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> expirationTime</span> </td> 
   <td>Ablaufzeit dieses Tokens. Dieser Wert muss eine Zeichenfolge im Format <a href="https://www.ietf.org/rfc/rfc3339.txt" format="html" type="external"> RFC 3339</a> Datum/Uhrzeit im Z-Zonenbezeichner ("Zulu-Zeit") oder eine Ganzzahl mit vorangestelltem "+"-Zeichen sein. Ein Beispiel für eine RFC 3339-Datum/Uhrzeit ist <span class="codeph"> 2006-04-14T12:01:10Z</span>. <p>Wenn der Wert eine Zeichenfolge im Datums-/Uhrzeitformat von RFC 339 ist, stellt er ein absolutes Ablaufdatum/eine absolute Ablaufzeit für das Token dar. Wenn der Wert eine Ganzzahl ist, der ein "+"-Zeichen vorangestellt ist, wird er als relative Anzahl von Sekunden ab der Ausgabe interpretiert, dass das Token gültig ist. Beispiel: <span class="codeph"> +60</span> gibt eine Minute an. Die Gültigkeitsdauer des Tokens beträgt maximal 30 Tage (bzw. die Standardlebensdauer, falls nicht angegeben). Verwenden Sie das kodierte Formular "%2B", wenn Sie das "+"-Zeichen angeben. </p> </td> 
   <td> Nein </td> 
  </tr> 
 </tbody> 
</table>

