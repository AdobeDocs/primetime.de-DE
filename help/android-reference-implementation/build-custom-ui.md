---
description: Sie können einfach eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenzimplementierungs-Framework basiert.
title: Benutzerdefinierte Benutzeroberfläche erstellen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Benutzerdefinierte Benutzeroberfläche erstellen {#build-a-custom-user-interface}

Sie können eine benutzerdefinierte Benutzeroberfläche erstellen, die auf dem Referenzimplementierungs-Framework basiert.

Die UI-Komponenten der folgenden Funktionen sind bereits integriert:

* Klickbare Anzeigen
* Anzeigenüberlagerungen
* Spätbindende Audiowiedergabe
* Geschlossene Untertitel
* Listener für alle oben genannten Komponenten

1. Bearbeiten Sie die [!DNL PlayerFragment.java] -Datei, um die UI-Komponenten zu initialisieren, die Sie im Player verwenden möchten.

1. Bearbeiten Sie die [!DNL res/player/player_fragment.xml] -Datei, um die Benutzeroberfläche anzupassen.
1. Erstellen Sie das Projekt.

>[!NOTE]
>
>Um UI-Änderungen an der Suchleiste vorzunehmen, können Sie die MarkableSeekBar-Klasse bearbeiten. Die [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) -Klasse verarbeitet den Schieberegler, den Daumen des Reglers, den Anzeigenmarkierungshalter, Cue-Markierungen, den Pufferbereich und die Suchbereich-Hintergründe.
