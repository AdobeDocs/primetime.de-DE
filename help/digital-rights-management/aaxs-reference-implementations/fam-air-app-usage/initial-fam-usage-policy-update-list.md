---
title: Liste der Richtlinienaktualisierungen
description: Liste der Richtlinienaktualisierungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Liste der Richtlinienaktualisierungen {#policy-update-list}

Sie können mithilfe von Listen für Richtlinienaktualisierungen Richtlinienänderungen an einen Lizenzserver weiterleiten. Wenn eine Richtlinie geändert wird, nachdem sie zum Verpacken von Inhalten verwendet wurde, ist es wünschenswert, den Lizenzserver über die neueste Version der Richtlinie zu informieren, damit die Version zur Lizenzerteilung verwendet werden kann.

Um zum ersten Mal eine Liste mit Richtlinienaktualisierungen zu erstellen, klicken Sie auf **[!UICONTROL Add policies]** , um alle auf dem Server verfügbaren Richtlinien anzuzeigen. Wählen Sie für Richtlinien, die seit ihrer Verwendung für das Verpacken von Inhalten aktualisiert wurden, die **[!UICONTROL update]** Optionsfeld.

Wenn Sie keine Richtlinie mehr zur Lizenzerteilung verwenden möchten und die Richtlinie bereits zum Verpacken von Inhalten verwendet wurde, können Sie die Richtlinie widerrufen. Wählen Sie dazu die **[!UICONTROL revoke]** Optionsfeld. Wenn die gewünschten Richtlinien ausgewählt wurden, wählen Sie **[!UICONTROL Create Policy Update List]**. Eine Datei namens [!DNL PolicyUpdateList.dat] wird im [!DNL Resources] Verzeichnis.

Um eine vorhandene Liste für Richtlinienaktualisierungen zu ändern, klicken Sie auf **[!UICONTROL Add policies]** , um alle auf dem Server verfügbaren Richtlinien anzuzeigen. Wählen Sie die zusätzlichen Richtlinien zum Hinzufügen oder Sperren aus. Vorhandene Einträge in der Liste für Richtlinienaktualisierungen können im oberen Bereich des Bildschirms geändert werden. Richtlinien, die markiert sind **[!UICONTROL updated]** kann geändert werden in **[!UICONTROL revoked]**, aber sobald eine Richtlinie **[!UICONTROL revoked]** festgelegt ist, kann nicht zurück zu **[!UICONTROL updated]**.

Wenn die gewünschten Änderungen vorgenommen wurden, wählen Sie **[!UICONTROL Create Policy Update List]** und die [!DNL PolicyUpdateList.dat] -Datei neu generiert. Wenn eine Richtlinie bereits in der Liste der Richtlinienaktualisierungen enthalten ist und seit der letzten Erstellung der Liste aktualisiert wurde, wird die neueste Version der Richtlinie verwendet, wenn die Liste für Richtlinienaktualisierungen erneut generiert wird.
