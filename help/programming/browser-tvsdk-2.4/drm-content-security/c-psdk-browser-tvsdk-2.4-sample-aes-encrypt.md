---
description: Während die Verschlüsselungsmethode AES-128 den gesamten Transport-Stream (TS)-Container einschließlich Kopfzeilen verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Teile der Videodaten.
title: Beispiel-AES-verschlüsselte HLS-Streams
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Beispiel-AES-verschlüsselte HLS-Streams{#sample-aes-encrypted-hls-streams}

Während die Verschlüsselungsmethode AES-128 den gesamten Transport-Stream (TS)-Container einschließlich Kopfzeilen verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Teile der Videodaten.

In verschlüsselten Streams wird ein geschützter Block identifiziert, über den der Schutz abgeschlossen ist. H.264-Video-geschützte Blöcke sind der Hauptteil der Typen 1 und 5 der NAL-Einheiten (Network Adaption Layer). Ein geschützter Block von Audio ist ein Audio-Frame und Audio muss im AAC-Format vorliegen.

>[!IMPORTANT]
>
>Sie müssen über den Schlüssel und den Initialisierungsvektor (IV) verfügen. Browser TVSDK verwendet den Schlüssel und IV, um den Stream vor der Wiedergabe zu entschlüsseln.

Jeder geschützte Block enthält eine Ganzzahl von 16-Byte-Blöcken, die mit dem CBC-Modus (CBC-Verschlüsselung) des Typs AES-128 ohne Abstand verschlüsselt werden. CBC tritt in jedem geschützten Block auf, und zu Beginn jedes neuen geschützten Blocks muss der IV auf den ursprünglichen Wert zurückgesetzt werden.

Die folgenden Codecs werden unterstützt:

* Für Videos wird H.264 unterstützt.
* Für Audio wird sample-AES nur für AAC unterstützt.
