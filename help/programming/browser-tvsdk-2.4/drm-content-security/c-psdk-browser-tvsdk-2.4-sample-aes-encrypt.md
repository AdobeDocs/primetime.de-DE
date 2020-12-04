---
description: Während die AES-128-Verschlüsselungsmethode den gesamten Transport Stream (TS)-Container einschließlich Header verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Videodaten.
seo-description: Während die AES-128-Verschlüsselungsmethode den gesamten Transport Stream (TS)-Container einschließlich Header verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Videodaten.
seo-title: Beispiel-AES-verschlüsselte HLS-Streams
title: Beispiel-AES-verschlüsselte HLS-Streams
uuid: 32c1f87b-eb81-4e1c-92ea-ec37260a7ecb
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Beispiel-AES-verschlüsselte HLS-Streams{#sample-aes-encrypted-hls-streams}

Während die AES-128-Verschlüsselungsmethode den gesamten Transport Stream (TS)-Container einschließlich Header verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Videodaten.

In verschlüsselten Streams wird ein geschützter Block identifiziert, über den der Schutz abgeschlossen ist. H.264-Videogeschützte Blöcke sind der Körper der Typen 1 und 5 der Netzwerkanpassungs-Layer (NAL)-Einheiten. Ein geschützter Audioblock ist ein Audiorahmen und Audio muss im AAC-Format vorliegen.

>[!IMPORTANT]
>
>Sie müssen über den Schlüssel und den Initialisierungsvektor (IV) verfügen. Browser TVSDK verwendet den Schlüssel und IV, um den Stream vor dem Abspielen zu entschlüsseln.

Jeder geschützte Block enthält eine Ganzzahl von 16-Byte-Blöcken, die mit dem AES-128 cipher Block-CBC-Modus ohne Auffüllung verschlüsselt werden. CBC tritt in jedem geschützten Block auf, und am Beginn jedes neuen geschützten Blocks muss das IV auf seinen ursprünglichen Wert zurückgesetzt werden.

Die folgenden Codecs werden unterstützt:

* Für Videos wird H.264 unterstützt.
* Für Audio wird sample-AES nur für AAC unterstützt.

