---
title: Paketmedien
description: Paketmedien
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# Paketmedien {#package-media}

Verwenden Sie die Registerkarte &quot;Paketmedien&quot;, um Inhalte zu verpacken. Im Abschnitt &quot;Eigenschaften von Packager&quot;werden die Packager-Einstellungen angezeigt, die auf der Registerkarte &quot;Voreinstellungen&quot;eingegeben wurden. Um diese Einstellungen zu ändern, wechseln Sie zur Registerkarte &quot;Voreinstellungen&quot;, ändern Sie die Einstellungen und speichern Sie.

Wenn Sie eine einzelne FLV- oder F4V-Datei verpacken möchten, wählen Sie die Option **[!UICONTROL Select Single File]** und geben Sie den vollständigen Pfad zur Quelldatei und den vollständigen Pfad ein, in dem die verschlüsselte Datei gespeichert werden soll.

Wenn Sie alle Dateien in einem Ordner verpacken möchten, wählen Sie die Option **[!UICONTROL Select Single Folder]**. Geben Sie den Ordner mit den Quelldateien an. Es werden nur Dateien im Eingabeordner gepackt, die den Kriterien **[!UICONTROL Input Media File Selection]** entsprechen (Dateien in Unterordnern werden nicht gepackt). Sie können [!DNL .flv]-Dateien, [!DNL .f4v]-Dateien verschlüsseln oder einen benutzerdefinierten regulären Ausdruck eingeben (z. B. &quot;.*&quot; verschlüsselt alle Dateien im Ordner). Die verschlüsselten Dateien werden im angegebenen Ausgabeordner unter demselben Dateinamen wie die Originaldatei gespeichert.

>[!NOTE]
>
>Dateipfade müssen auf Dateien verweisen, die dem Verpackungsserver zur Verfügung stehen. Wenn Sie den Flash Access Manager auf einem anderen Rechner als dem Verpackungsserver ausführen, müssen Sie einen Pfad angeben, auf den der Server zugreifen kann (entweder auf einem Netzlaufwerk oder auf dem Server selbst).

Die folgende Tabelle beschreibt die Voreinstellungen für Paketmedien:

| Voreinstellung | Beschreibung |
|---|---|
| Richtliniendateinamen | Wählen Sie eine oder mehrere Richtlinien aus der Dropdown-Liste aus, die auf den Inhalt angewendet werden sollen. Um mehrere Richtlinien auszuwählen, halten Sie die STRG-Taste gedrückt, während Sie Richtlinien auswählen. |
| Sekunden unverschlüsselt | Gibt an, wie viele Sekunden Inhalt am Anfang der Datei unverschlüsselt bleiben soll. Geben Sie &quot;0&quot;ein, um die Verschlüsselung von Anfang an durchzuführen. |
| Video verschlüsseln | Aktivieren Sie dieses Kontrollkästchen, um Videodaten zu verschlüsseln |
| Verschlüsselungsstufe | Wenn die Videoverschlüsselung aktiviert ist, wählen Sie die Verschlüsselungsstufe für Videodaten aus. Hoch verschlüsselt alle Videodaten. Mittel- und Niedrig-Bereiche werden selektiv verschlüsselt. (Nur für F4V mit H.264-Video) |
| Audio verschlüsseln | Aktivieren Sie dieses Kontrollkästchen, um Audiodaten zu verschlüsseln |
| Verschlüsselungsskript | Aktivieren Sie dieses Kontrollkästchen, um Skriptdaten zu verschlüsseln (nur FLV) |
| Benutzerdefinierte Eigenschaften | Geben Sie benutzerdefinierte Eigenschaften an, die in den gepackten Inhalt aufgenommen werden sollen. Diese Eigenschaften stehen dem Lizenzserver bei der Lizenzerteilung zur Verfügung. (Optional) |

Klicken Sie nach Auswahl der Verpackungsoptionen auf die Schaltfläche **[!UICONTROL Package Media]**, um mit dem Verpacken der Dateien zu beginnen.
