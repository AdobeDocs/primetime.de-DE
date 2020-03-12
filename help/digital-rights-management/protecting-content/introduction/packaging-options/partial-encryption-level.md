---
seo-title: Partielle Verschlüsselungsstufe
title: Partielle Verschlüsselungsstufe
uuid: dbd9ce92-c829-4cad-9ac4-c57bd4f70345
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Partielle Verschlüsselungsstufe {#partial-encryption-level}

Diese Verpackungsoption gibt an, ob alle oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die teilweise Verschlüsselung gilt nur für die Videospur in F4V-/MP4-Dateien.

Die teilweise Verschlüsselung ist so konzipiert, dass Inhaltsanbieter die Granularität erhalten, den Inhalt in Teilen zu kodieren. Durch die Verschlüsselung von Inhalten wird der CPU-Aufwand für das Gerät erhöht, das den Inhalt entschlüsselt und anzeigt. Verwenden Sie partielle Verschlüsselung, um den CPU-Aufwand zu reduzieren und gleichzeitig einen sehr starken Schutz des Inhalts zu gewährleisten. Ein motivierender Grund für die Verwendung dieser Funktion ist ein einzelner Inhalt, der auf Geräten mit niedriger, mittlerer und hoher Leistung abspielbar sein soll.

Aufgrund der Art der Videokodierung ist es nicht notwendig, 100 % des Videos zu verschlüsseln, damit es bei Diebstahl nicht wiedergegeben werden kann. Die teilweise Verschlüsselung hat drei Einstellungen: &quot;low&quot;, &quot;medium&quot;und &quot;high&quot;. Die zugehörigen prozentualen Verschlüsselungsraten hängen davon ab, wie das Video kodiert wird. Aufgrund dieser Kodierungsabhängigkeit liegt der Prozentsatz des verschlüsselten Inhalts in den folgenden Bereichen:

* Hoch: Verschlüsselt alle Beispiele.
* Mittel: Verschlüsselt eine Zielgruppe zu 50 % der Daten.
* Niedrig: Verschlüsselt eine Zielgruppe von 20 bis 30 % der Daten.

Diese Einstellungen wurden mit der folgenden Regel entwickelt: Alle Inhalte, die bei niedriger Einstellung verschlüsselt werden, werden auch bei der Einstellung Medium verschlüsselt. Dadurch wird sichergestellt, dass dasselbe Inhaltselement, das bei niedriger Verschlüsselung von einer Partei verteilt und bei mittlerer Verschlüsselung von einer anderen Partei verteilt wird, den Schutz des Inhalts nicht beeinträchtigt.

Verwendungsbeispiel: Durch die Reduzierung des Verschlüsselungsgrads wird der Overhead bei der Entschlüsselung auf dem Client verringert und die Wiedergabeleistung auf Low-End-Computern verbessert.
