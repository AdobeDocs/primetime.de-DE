---
seo-title: Partielle Verschlüsselungsstufe
title: Partielle Verschlüsselungsstufe
uuid: 462ca2d0-0d37-43a8-b8a0-8a25ecf73ce1
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# Partielle Verschlüsselungsstufe{#partial-encryption-level}

Gibt an, ob alle Frames oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch.

>[!NOTE]
>
>Nur für Videospuren in F4V/H.264-Dateien.

Die teilweise Verschlüsselung ist so konzipiert, dass Inhaltsanbieter die Granularität erhalten, den Inhalt in Teilen zu kodieren. Durch die Verschlüsselung von Inhalten wird der CPU-Aufwand für das Gerät erhöht, das den Inhalt entschlüsselt und anzeigt. Verwenden Sie partielle Verschlüsselung, um den CPU-Aufwand zu reduzieren und gleichzeitig einen sehr starken Schutz des Inhalts zu gewährleisten. Ein motivierender Grund für die Verwendung dieser Funktion ist ein einzelner Inhalt, der auf Geräten mit niedriger, mittlerer und hoher Leistung abspielbar sein soll.

Aufgrund der Art der Videokodierung ist es nicht notwendig, 100 % des Videos zu verschlüsseln, damit es bei Diebstahl nicht wiedergegeben werden kann. Die teilweise Verschlüsselung hat drei Einstellungen: &quot;low&quot;, &quot;medium&quot;und &quot;high&quot;. Die zugehörigen prozentualen Verschlüsselungsraten hängen davon ab, wie das Video kodiert wird. Aufgrund dieser Kodierungsabhängigkeit liegt der Prozentsatz des verschlüsselten Inhalts in den folgenden Bereichen:

* Hoch: Verschlüsselt alle Beispiele.
* Mittel: Verschlüsselt eine Zielgruppe zu 50 % der Daten.
* Niedrig: Verschlüsselt eine Zielgruppe von 20 bis 30 % der Daten.

Diese Einstellungen wurden mit der folgenden Regel entwickelt: Alle Inhalte, die bei niedriger Einstellung verschlüsselt werden, werden auch bei der Einstellung Medium verschlüsselt. Dadurch wird sichergestellt, dass dasselbe Inhaltselement, das bei niedriger Verschlüsselung von einer Partei verteilt und bei mittlerer Verschlüsselung von einer anderen Partei verteilt wird, den Schutz des Inhalts nicht beeinträchtigt.

Example use case: Reducing the encryption level decreases the decryption overhead on the client and improves playback performance on low-end machines.
