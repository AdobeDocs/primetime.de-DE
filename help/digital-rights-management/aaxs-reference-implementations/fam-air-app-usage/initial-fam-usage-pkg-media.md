---
title: Paketmedien
description: Paketmedien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Paketmedien {#package-media}

Verwenden Sie die Registerkarte Paketmedien , um Inhalte zu verpacken. Im Abschnitt Eigenschaften von Packager werden die auf der Registerkarte Voreinstellungen eingegebenen Paketeinstellungen angezeigt. Um diese Einstellungen zu ändern, wechseln Sie zur Registerkarte Voreinstellungen , ändern Sie die Einstellungen und speichern Sie.

Wenn Sie eine einzelne FLV- oder F4V-Datei verpacken möchten, wählen Sie die **[!UICONTROL Select Single File]** und geben Sie den vollständigen Pfad zur Quelldatei und den vollständigen Pfad ein, in dem die verschlüsselte Datei gespeichert werden soll.

Wenn Sie alle Dateien in einem Ordner verpacken möchten, wählen Sie die **[!UICONTROL Select Single Folder]** -Option. Geben Sie den Ordner an, der die Quelldateien enthält. Nur Dateien im Eingabeordner, die mit dem **[!UICONTROL Input Media File Selection]** Kriterien werden gepackt (Dateien in Unterordnern werden nicht gepackt). Verschlüsselung auswählen [!DNL .flv] Dateien, [!DNL .f4v] oder geben Sie einen benutzerdefinierten regulären Ausdruck ein (z. B. &quot;.&#42;&quot; verschlüsselt alle Dateien im Ordner). Die verschlüsselten Dateien werden im angegebenen Ausgabeordner unter Verwendung des gleichen Dateinamens wie die Originaldatei gespeichert.

>[!NOTE]
>
>Dateipfade müssen sich auf Dateien beziehen, die dem Paketserver zur Verfügung stehen. Wenn Sie den Flash Access Manager auf einem anderen Computer als dem Paketserver ausführen, müssen Sie einen Pfad angeben, auf den der Server zugreifen kann (entweder auf einem Netzlaufwerk oder auf dem Server selbst).

In der folgenden Tabelle werden die Package Media-Voreinstellungen beschrieben:

| Präferenz | Beschreibung |
|---|---|
| Policy File Name(s) | Wählen Sie eine oder mehrere Richtlinien aus der Dropdownliste aus, die auf den Inhalt angewendet werden sollen. Um mehrere Richtlinien auszuwählen, halten Sie die Strg-Taste gedrückt, während Sie Richtlinien auswählen. |
| Unverschlüsselte Sekunden | Gibt die Anzahl der Sekunden an Inhalt an, der am Anfang der Datei unverschlüsselt bleiben soll. Geben Sie &quot;0&quot;ein, um die Verschlüsselung von Anfang an durchzuführen. |
| Video verschlüsseln | Aktivieren Sie dieses Kontrollkästchen, um Videodaten zu verschlüsseln |
| Verschlüsselungsstufe | Wenn die Videoverschlüsselung aktiviert ist, wählen Sie die Verschlüsselungsstufe für Videodaten aus. Hoch verschlüsselt alle Videodaten. Mittel und Niedrig verschlüsseln selektiv Teile des Videos. (Nur für F4V mit H.264-Video) |
| Audio verschlüsseln | Aktivieren Sie dieses Kontrollkästchen zum Verschlüsseln von Audiodaten |
| Verschlüsselungsskript | Aktivieren Sie dieses Kontrollkästchen, um Skriptdaten zu verschlüsseln (nur FLV). |
| Benutzerdefinierte Eigenschaften | Geben Sie benutzerdefinierte Eigenschaften an, die in den gepackten Inhalt eingefügt werden sollen. Diese Eigenschaften stehen dem Lizenzserver bei der Lizenzerteilung zur Verfügung. (Optional) |

Nachdem Sie die Verpackungsoptionen ausgewählt haben, klicken Sie auf das **[!UICONTROL Package Media]** -Schaltfläche, um mit der Verpackung der Dateien zu beginnen.
