---
title: Festlegen der Voreinstellungen - Übersicht
description: Festlegen der Voreinstellungen - Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Festlegen der Voreinstellungen - Übersicht {#setting-preferences-overview}

Mit Ausnahme der Paket-Server-URL werden alle unten angegebenen Voreinstellungen im [!DNL flashaccess-refimpl-packager.properties] -Datei auf dem Server. Alle Einstellungen können entweder direkt in der Eigenschaftendatei oder über die AIR-Anwendung geändert werden. Kennwörter werden verschlüsselt, wenn sie in der Eigenschaftendatei auf dem Server gespeichert werden. Geben Sie das unverschlüsselte Kennwort in die Benutzeroberfläche ein und es wird verschlüsselt, bevor es in der Datei gespeichert wird.

>[!NOTE]
>
>Alle Ordner und Pfade beziehen sich auf Ordner auf dem Paketserver, nicht auf den Client, auf dem die AIR-Anwendung ausgeführt wird.

Alle hier vorgenommenen Änderungen werden sofort wirksam, nachdem die Voreinstellungen gespeichert wurden. Es ist nicht erforderlich, den Server neu zu starten, es sei denn, der Packager-Thread wurde aufgrund von Konfigurationsproblemen beendet.

In den Beschreibungen der Voreinstellungen werden die folgenden Begriffe verwendet:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Präferenz </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Paket-Server-URL </td> 
   <td colname="2" class="- topic/entry "> Speicherort der Serverausführung <span class="filepath"> flashaccess-packager.war </span>; zum Beispiel <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Ressourcenverzeichnis </td> 
   <td colname="2" class="- topic/entry "> Verzeichnis, das Richtlinien, Zertifikate, Anmeldeinformationen und alle anderen für den Paketserver erforderlichen Ressourcen enthält </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Lizenzserver-URL </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL des Servers, von dem aus der Client eine Lizenz anfordern soll, beispielsweise <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>
