---
description: Die TVSDK Primetime Reference ist eine Android-Anwendung, die auf den TVSDK- und AVE-Frameworks basiert.
seo-description: Die TVSDK Primetime Reference ist eine Android-Anwendung, die auf den TVSDK- und AVE-Frameworks basiert.
seo-title: Primetime-Referenzimplementierung erstellen
title: Primetime-Referenzimplementierung erstellen
uuid: ab12660a-1563-49a4-82d9-1ab13f8a92be
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Primetime-Referenzimplementierung erstellen {#build-the-primetime-reference-implementation}

Die TVSDK Primetime Reference ist eine Android-Anwendung, die auf den TVSDK- und AVE-Frameworks basiert.

So richten Sie das Primetime-Referenzprojekt in Eclipse ein und erstellen es:

1. Laden Sie die TVSDK Android-ZIP-Datei herunter und entpacken Sie sie in einen Ordner an einem Speicherort, den Sie sich merken werden.
1. Starten Sie Eclipse.
1. Wählen Sie **[!UICONTROL File]** > **[!UICONTROL Import]**.
1. Wählen Sie **[!UICONTROL Android]** > **[!UICONTROL Existing Android Code Into Workspace]**.
1. Klicken **[!UICONTROL Next]**.
1. Verwenden Sie die **[!UICONTROL Browse]** Schaltfläche, um das **[!UICONTROL Root Directory]** Feld mit dem Verzeichnis zu füllen, in dem Sie die TVSDK Android-ZIP-Datei entpackt [!DNL samples/PrimetimeReference/src] haben.
1. Wählen Sie die folgenden Projekte aus, die importiert werden sollen: **[!UICONTROL appcompat]**, **[!UICONTROL PrimetimeReference]**.
1. Klicken **[!UICONTROL Finish]**.
1. Wählen Sie **[!UICONTROL Project]** > **[!UICONTROL Build Project]** , um das Projekt zu erstellen.

   Dieser Schritt ist nicht erforderlich, wenn das Projekt so eingerichtet ist, dass es automatisch erstellt wird.
1. Wenn Sie das Testprojekt in den Arbeitsbereich einbeziehen möchten, verknüpfen Sie das Testprojekt mit dem PrimetimeReference-Projekt:
   1. Wiederholen Sie die Schritte 3. bis 6.
   1. Wählen Sie das folgende zu importierende Projekt aus: `PrimetimeReference\tests`.
   1. Klicken **[!UICONTROL Finish]**.

      Das Testprojekt hängt vom CatalogActivity-Projekt ab. Daher müssen Sie das Testprojekt mit dem CatalogActivity-Projekt verknüpfen.
   1. Klicken Sie mit der rechten Maustaste **[!UICONTROL tests]** und wählen Sie **[!UICONTROL Properties]**.
   1. Wählen Sie die **[!UICONTROL Projects]** Registerkarte unter Java Build Path.
   1. Klicken **[!UICONTROL Add...]**
   1. Wählen Sie CatalogActivity.
   1. Klicken Sie auf **[!UICONTROL OK]** , um das Projekt hinzuzufügen.
   1. Klicken Sie auf **[!UICONTROL OK]** , um die Seite Eigenschaften zu verlassen.
   1. Wählen Sie **[!UICONTROL Project]** > **[!UICONTROL Build Project]** , um das Projekt zu erstellen.

      Dieser Schritt ist nicht erforderlich, wenn das Projekt so eingerichtet ist, dass es automatisch erstellt wird.
