---
seo-title: Übersicht über Voreinstellungen
title: Übersicht über Voreinstellungen
uuid: d1c067b1-6c2b-460e-8d00-5a5bfee0789c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht über Voreinstellungen {#setting-preferences-overview}

Mit Ausnahme der Packager Server-URL werden alle unten angegebenen Voreinstellungen in der [!DNL flashaccess-refimpl-packager.properties] Datei auf dem Server gespeichert. Alle Einstellungen können entweder direkt in der Eigenschaftendatei oder über die AIR-Anwendung geändert werden. Kennwörter werden verschlüsselt, wenn sie in der Eigenschaftendatei auf dem Server gespeichert werden. Geben Sie das unverschlüsselte Kennwort in die Benutzeroberfläche ein, und es wird verschlüsselt, bevor es in der Datei gespeichert wird.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Alle Ordner und Pfade beziehen sich auf Ordner auf dem Packager-Server, nicht auf dem Client, auf dem die AIR-Anwendung ausgeführt wird.

Alle hier vorgenommenen Änderungen werden sofort nach dem Speichern der Voreinstellungen wirksam. Der Server muss erst neu gestartet werden, wenn der Packager Thread aufgrund von Konfigurationsproblemen beendet wurde.

Die Voreinstellungsbeschreibungen verwenden die folgenden Begriffe:

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_tj5_hcz_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> Voreinstellung </th> 
   <th colname="2" class="- topic/entry entry"> Beschreibung </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> URL des Packager-Servers </td> 
   <td colname="2" class="- topic/entry "> Speicherort des Servers, auf dem <span class="filepath"> flashaccess-packager.war ausgeführt wird </span>; Beispiel: <span class="filepath"> https://localhost:8080 </span> </td> 
  </tr> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Ressourcenverzeichnis </td> 
   <td colname="2" class="- topic/entry "> Ordner mit Richtlinien, Zertifikaten, Berechtigungen und anderen für den Packager-Server erforderlichen Ressourcen </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "> Lizenzserver-URL </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">URL des Servers, von dem der Client eine Lizenz anfordern soll; Beispiel: <span class="filepath"> https://mylicenseserver.com:8080 </span> </p> </td> 
  </tr> 
 </tbody> 
</table>

