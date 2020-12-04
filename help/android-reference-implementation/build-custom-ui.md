---
description: Sie können auf einfache Weise eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenz-Implementierungsframework basiert.
seo-description: Sie können auf einfache Weise eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenz-Implementierungsframework basiert.
seo-title: Benutzerdefinierte Benutzeroberfläche erstellen
title: Benutzerdefinierte Benutzeroberfläche erstellen
uuid: b785f6a4-3ef8-4f7a-a087-0d6551da9750
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---


# Erstellen einer benutzerdefinierten Benutzeroberfläche {#build-a-custom-user-interface}

Sie können eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenz-Implementierungsframework basiert.

Die UI-Komponenten der folgenden Funktionen sind bereits integriert:

* Klickbare Anzeigen
* Anzeigenüberlagerungen
* Spätbindendes Audio
* Untertitel
* Listener für alle oben genannten Komponenten

1. Bearbeiten Sie die Datei [!DNL PlayerFragment.java], um die Komponenten der Benutzeroberfläche zu initialisieren, die Sie im Player verwenden möchten.

1. Bearbeiten Sie die Datei [!DNL res/player/player_fragment.xml], um die Benutzeroberfläche anzupassen.
1. Erstellen Sie das Projekt.

>[!NOTE]
>
>Um Änderungen an der Suchleiste der Benutzeroberfläche vorzunehmen, können Sie die MarkableSeekBar-Klasse bearbeiten. Die [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html)-Klasse verarbeitet den Schieberegler, den Schieberegler, den Anzeigenmarkenhalter, Cue-Marker, den Pufferbereich und den Suchbereich-Hintergrund.