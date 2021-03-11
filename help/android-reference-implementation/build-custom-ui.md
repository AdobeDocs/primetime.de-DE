---
description: Sie können auf einfache Weise eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenz-Implementierungsframework basiert.
title: Benutzerdefinierte Benutzeroberfläche erstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
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