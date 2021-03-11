---
title: Liste der Richtlinienaktualisierung
description: Liste der Richtlinienaktualisierung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Liste zur Richtlinienaktualisierung {#policy-update-list}

Sie können Listen zur Richtlinienaktualisierung verwenden, um Richtlinienänderungen an einem Lizenzserver zu kommunizieren. Wenn eine Richtlinie geändert wird, nachdem sie zum Verpacken von Inhalten verwendet wurde, sollte der Lizenzserver über die neueste Version der Richtlinie informiert werden, damit eine Lizenz mit der Version ausgegeben werden kann.

Um zum ersten Mal eine Liste zur Richtlinienaktualisierung zu erstellen, klicken Sie auf **[!UICONTROL Add policies]**, um alle auf dem Server verfügbaren Richtlinien Ansicht. Wählen Sie für Richtlinien, die aktualisiert wurden, seit sie zum Verpacken von Inhalten verwendet wurden, das Optionsfeld **[!UICONTROL update]**.

Wenn Sie zum Ausstellen von Lizenzen keine Richtlinie mehr verwenden möchten und die Richtlinie bereits zum Verpacken von Inhalten verwendet wurde, sollten Sie die Richtlinie möglicherweise widerrufen. Wählen Sie dazu das Optionsfeld **[!UICONTROL revoke]** aus. Wenn die gewünschten Richtlinien ausgewählt wurden, wählen Sie **[!UICONTROL Create Policy Update List]**. Eine Datei mit dem Namen [!DNL PolicyUpdateList.dat] wird im Ordner [!DNL Resources] gespeichert.

Um eine vorhandene Liste zur Richtlinienaktualisierung zu ändern, klicken Sie auf **[!UICONTROL Add policies]**, um alle auf dem Server verfügbaren Richtlinien Ansicht. Wählen Sie die zusätzlichen Richtlinien aus, die hinzugefügt oder widerrufen werden sollen. Vorhandene Einträge in der Liste &quot;Richtlinienaktualisierung&quot;können im oberen Bildschirmbereich geändert werden. Richtlinien, die mit **[!UICONTROL updated]** markiert sind, können in **[!UICONTROL revoked]** geändert werden. Ist eine Richtlinie jedoch **[!UICONTROL revoked]**, kann sie nicht mehr in **[!UICONTROL updated]** zurückgesetzt werden.

Wenn die gewünschten Änderungen vorgenommen wurden, wählen Sie **[!UICONTROL Create Policy Update List]** und die [!DNL PolicyUpdateList.dat]-Datei wird neu generiert. Wenn sich eine Richtlinie bereits in der Liste zur Richtlinienaktualisierung befindet und sie seit der letzten Generierung der Liste aktualisiert wurde, wird beim erneuten Generieren der Liste zur Richtlinienaktualisierung die neueste Richtlinienversion verwendet.
