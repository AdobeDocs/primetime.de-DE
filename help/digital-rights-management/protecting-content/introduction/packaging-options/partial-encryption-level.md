---
seo-title: Partielle Verschlüsselungsstufe
title: Partielle Verschlüsselungsstufe
uuid: dbd9ce92-c829-4cad-9ac4-c57bd4f70345
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# Partielle Verschlüsselungsstufe {#partial-encryption-level}

Diese Verpackungsoption gibt an, ob alle oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch.

>[!NOTE]
>
>Die teilweise Verschlüsselung gilt nur für die Videospur in F4V-/MP4-Dateien.

Die teilweise Verschlüsselung ist so konzipiert, dass Inhaltsanbieter die Granularität erhalten, den Inhalt in Teilen zu kodieren. Encryption of content adds CPU overhead to the device that is decrypting and viewing the content. Verwenden Sie partielle Verschlüsselung, um den CPU-Aufwand zu reduzieren und gleichzeitig einen sehr starken Schutz des Inhalts zu gewährleisten. Ein motivierender Grund für die Verwendung dieser Funktion ist ein einzelner Inhalt, der auf Geräten mit niedriger, mittlerer und hoher Leistung abspielbar sein soll.

Due to the nature of video encoding, it is not necessary to encrypt 100% of video to make it unplayable if it is stolen. Partial encryption has three settings, low, medium, and high, and the associated percentages of encryption are dependent upon how the video is encoded. Because of this encoding dependency, the percentage of your content that is encrypted falls within the following ranges:

* High: Encrypts all samples.
* Medium: Encrypts a target 50% of the data.
* Low: Encrypts a target 20 to 30% of the data.

Diese Einstellungen wurden mit der folgenden Regel entwickelt: Alle Inhalte, die bei niedriger Einstellung verschlüsselt werden, werden auch bei der Einstellung Medium verschlüsselt. This ensures that the same piece of content distributed at low encryption by one party and distributed at medium encryption by another party does not compromise the protection of the content.

Example use case: Reducing the encryption level decreases the decryption overhead on the client and improves playback performance on low-end machines.
