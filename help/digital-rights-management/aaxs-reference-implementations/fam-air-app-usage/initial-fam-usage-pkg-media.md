---
seo-title: Paketmedien
title: Paketmedien
uuid: f6e877be-d916-4766-bc44-99891a3df3a8
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Paketmedien {#package-media}

Verwenden Sie die Registerkarte &quot;Paketmedien&quot;, um Inhalte zu verpacken. Im Abschnitt &quot;Eigenschaften von Packager&quot;werden die Packager-Einstellungen angezeigt, die auf der Registerkarte &quot;Voreinstellungen&quot;eingegeben wurden. Um diese Einstellungen zu ändern, wechseln Sie zur Registerkarte &quot;Voreinstellungen&quot;, ändern Sie die Einstellungen und speichern Sie.

Wenn Sie eine einzelne FLV- oder F4V-Datei verpacken möchten, wählen Sie die **[!UICONTROL Select Single File]** Option und geben Sie den vollständigen Pfad zur Quelldatei und den vollständigen Pfad ein, in dem die verschlüsselte Datei gespeichert werden soll.

Wenn Sie alle Dateien in einem Ordner verpacken möchten, wählen Sie die **[!UICONTROL Select Single Folder]** Option. Geben Sie den Ordner mit den Quelldateien an. Nur Dateien im Eingabeordner, die den **[!UICONTROL Input Media File Selection]** Kriterien entsprechen, werden verpackt (Dateien in Unterordnern werden nicht gepackt). Sie können [!DNL .flv] Dateien und [!DNL .f4v] Dateien verschlüsseln oder einen benutzerdefinierten regulären Ausdruck eingeben (z. B. &quot;.*&quot; verschlüsselt alle Dateien im Ordner). Die verschlüsselten Dateien werden im angegebenen Ausgabeordner unter demselben Dateinamen wie die Originaldatei gespeichert.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Dateipfade müssen auf Dateien verweisen, die dem Verpackungsserver zur Verfügung stehen. Wenn Sie den Flash Access Manager auf einem anderen Computer als dem Verpackungsserver ausführen, müssen Sie einen Pfad angeben, auf den der Server zugreifen kann (entweder auf einem Netzlaufwerk oder auf dem Server selbst).

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

Klicken Sie nach Auswahl der Verpackungsoptionen auf die **[!UICONTROL Package Media]** Schaltfläche, um mit dem Verpacken der Dateien zu beginnen.
