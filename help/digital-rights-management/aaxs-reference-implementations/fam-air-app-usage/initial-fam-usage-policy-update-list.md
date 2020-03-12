---
seo-title: Liste der Richtlinienaktualisierung
title: Liste der Richtlinienaktualisierung
uuid: ecc74b66-5b53-4ec3-9641-8b78929e2932
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Liste der Richtlinienaktualisierung {#policy-update-list}

Sie können Listen zur Richtlinienaktualisierung verwenden, um Richtlinienänderungen an einem Lizenzserver zu kommunizieren. Wenn eine Richtlinie geändert wird, nachdem sie zum Verpacken von Inhalten verwendet wurde, sollte der Lizenzserver über die neueste Version der Richtlinie informiert werden, damit eine Lizenz mit der Version ausgegeben werden kann.

Um zum ersten Mal eine Liste zur Richtlinienaktualisierung zu erstellen, klicken Sie auf **[!UICONTROL Add policies]** , um alle auf dem Server verfügbaren Richtlinien Ansicht. Wählen Sie für Richtlinien, die aktualisiert wurden, seit sie zum Verpacken von Inhalten verwendet wurden, das **[!UICONTROL update]** Optionsfeld aus.

Wenn Sie zum Ausstellen von Lizenzen keine Richtlinie mehr verwenden möchten und die Richtlinie bereits zum Verpacken von Inhalten verwendet wurde, sollten Sie die Richtlinie möglicherweise widerrufen. Wählen Sie dazu das **[!UICONTROL revoke]** Optionsfeld aus. Wählen Sie nach Auswahl der gewünschten Richtlinien **[!UICONTROL Create Policy Update List]**. Eine aufgerufene Datei [!DNL PolicyUpdateList.dat] wird im [!DNL Resources] Verzeichnis gespeichert.

Um eine vorhandene Liste zur Richtlinienaktualisierung zu ändern, klicken Sie auf , **[!UICONTROL Add policies]** um alle auf dem Server verfügbaren Richtlinien Ansicht. Wählen Sie die zusätzlichen Richtlinien aus, die hinzugefügt oder widerrufen werden sollen. Vorhandene Einträge in der Liste &quot;Richtlinienaktualisierung&quot;können im oberen Bildschirmbereich geändert werden. Richtlinien, die markiert sind, **[!UICONTROL updated]** können in **[!UICONTROL revoked]** geändert werden, aber sobald eine Richtlinie **[!UICONTROL revoked]** vorliegt, kann sie nicht wieder in **[!UICONTROL updated]** geändert werden.

Wenn die gewünschten Änderungen vorgenommen wurden, wählen Sie &quot; **[!UICONTROL Create Policy Update List]** und die [!DNL PolicyUpdateList.dat] Datei wird neu generiert&quot;. Wenn sich eine Richtlinie bereits in der Liste zur Richtlinienaktualisierung befindet und sie seit der letzten Generierung der Liste aktualisiert wurde, wird beim erneuten Generieren der Liste zur Richtlinienaktualisierung die neueste Richtlinienversion verwendet.
