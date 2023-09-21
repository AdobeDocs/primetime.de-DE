---
title: Partielle Verschlüsselungsstufe
description: Partielle Verschlüsselungsstufe
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Partielle Verschlüsselungsstufe {#partial-encryption-level}

Diese Verpackungsoption gibt an, ob alle Frames oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch.

>[!NOTE]
>
>Die partielle Verschlüsselung gilt nur für die Videospur in F4V-/MP4-Dateien.

Die partielle Verschlüsselung soll den Anbietern von Inhalten die Granularität verleihen, den Inhalt in Teilen zu kodieren. Durch die Verschlüsselung von Inhalten entsteht CPU-Mehraufwand für das Gerät, das den Inhalt entschlüsselt und anzeigt. Verwenden Sie partielle Verschlüsselung, um den CPU-Overhead zu reduzieren und gleichzeitig einen sehr starken Schutz des Inhalts zu gewährleisten. Ein motivierender Grund für die Verwendung dieser Funktion ist ein einzelnes Inhaltselement, das auf Geräten mit niedriger, mittlerer und hoher Leistung wiedergegeben werden kann.

Aufgrund der Art der Videokodierung ist es nicht erforderlich, 100 % des Videos zu verschlüsseln, damit es bei Diebstahl nicht wiedergegeben werden kann. Die partielle Verschlüsselung hat drei Einstellungen: &quot;Niedrig&quot;, &quot;Mittel&quot;und &quot;Hoch&quot;. Die zugehörigen Prozentsätze der Verschlüsselung hängen davon ab, wie das Video kodiert wird. Aufgrund dieser Kodierungsabhängigkeit liegt der Prozentsatz des verschlüsselten Inhalts in den folgenden Bereichen:

* Hoch: Verschlüsselt alle Beispiele.
* Mittel: Verschlüsselt eine Zielgruppe zu 50 % der Daten.
* Niedrig: Verschlüsselt eine Zielgruppe von 20 bis 30 % der Daten.

Diese Einstellungen wurden mit der folgenden Regel erstellt: Alle Inhalte, die mit der niedrigen Einstellung verschlüsselt werden, werden auch mit der mittleren Einstellung verschlüsselt. Dadurch wird sichergestellt, dass derselbe Inhalt, der bei niedriger Verschlüsselung von einer Partei verteilt und bei mittlerer Verschlüsselung von einer anderen Partei verteilt wird, den Schutz des Inhalts nicht beeinträchtigt.

Anwendungsbeispiel: Durch die Reduzierung des Verschlüsselungsgrads wird der Mehraufwand für die Entschlüsselung auf dem Client verringert und die Wiedergabeleistung auf Geräten mit geringer Auslastung verbessert.
