---
description: Die TVSDK-Primetime-Referenz ist eine Android-Anwendung, die um die TVSDK- und AVE-Frameworks aufgebaut ist.
title: Erstellen der Primetime-Referenzimplementierung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Erstellen der Primetime-Referenzimplementierung {#build-the-primetime-reference-implementation}

Die TVSDK-Primetime-Referenz ist eine Android-Anwendung, die um die TVSDK- und AVE-Frameworks aufgebaut ist.

So richten Sie das Primetime Reference-Projekt in Eclipse ein und erstellen es:

1. Laden Sie die Zip-Datei für TVSDK Android herunter und entpacken Sie sie in ein Verzeichnis an einem Speicherort, den Sie sich merken werden.
1. Starten Sie Eclipse.
1. Auswählen **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Auswählen **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Klicks **[!UICONTROL Next]**.
1. Verwenden Sie die **[!UICONTROL Browse]** -Schaltfläche zum Ausfüllen der **[!UICONTROL Root Directory]** -Feld mit dem Verzeichnis unter [!DNL samples/PrimetimeReference/src] an die Sie die TVSDK Android-ZIP-Datei entpackt haben.
1. Wählen Sie die folgenden zu importierenden Projekte aus: **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. Klicks **[!UICONTROL Finish]**.
1. Auswählen  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** , um das Projekt zu erstellen.

   Dieser Schritt ist nicht erforderlich, wenn das Projekt für die automatische Erstellung eingerichtet ist.
1. Wenn Sie das Testprojekt in den Arbeitsbereich einbeziehen möchten, verknüpfen Sie das Testprojekt mit dem PrimetimeReference-Projekt:
   1. Wiederholen Sie die Schritte 3. bis 6.
   1. Wählen Sie das folgende zu importierende Projekt aus: `PrimetimeReference\tests`.
   1. Klicks **[!UICONTROL Finish]**.

      Das Testprojekt ist vom CatalogActivity-Projekt abhängig. Daher müssen Sie das Testprojekt mit dem CatalogActivity-Projekt verknüpfen.
   1. Rechtsklick **[!UICONTROL tests]** und wählen **[!UICONTROL Properties]**.
   1. Wählen Sie die **[!UICONTROL Projects]** Registerkarte unter Java Build-Pfad.
   1. Klicks **[!UICONTROL Add...]**
   1. Wählen Sie CatalogActivity aus.
   1. Klicks **[!UICONTROL OK]** , um das Projekt hinzuzufügen.
   1. Klicks **[!UICONTROL OK]** , um die Seite Eigenschaften zu verlassen.
   1. Auswählen  **[!UICONTROL Project]** > **[!UICONTROL Build Project]** , um das Projekt zu erstellen.

      Dieser Schritt ist nicht erforderlich, wenn das Projekt für die automatische Erstellung eingerichtet ist.
