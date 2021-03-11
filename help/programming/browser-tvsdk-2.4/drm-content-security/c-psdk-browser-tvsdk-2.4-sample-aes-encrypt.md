---
description: Während die AES-128-Verschlüsselungsmethode den gesamten Transport-Stream-Container (TS) einschließlich Header verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Videodaten.
title: Beispiel-AES-verschlüsselte HLS-Streams
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---


# Beispiel-AES-verschlüsselte HLS-Streams{#sample-aes-encrypted-hls-streams}

Während die AES-128-Verschlüsselungsmethode den gesamten Transport-Stream-Container (TS) einschließlich Header verschlüsselt, verschlüsselt die SAMPLE-AES-Verschlüsselung nur die Audio- und Videodaten.

In verschlüsselten Streams wird ein geschützter Block identifiziert, über den der Schutz abgeschlossen ist. H.264-Videogeschützte Blöcke sind der Körper der Typen 1 und 5 der Netzwerkanpassungs-Layer (NAL)-Einheiten. Ein geschützter Audioblock ist ein Audiorahmen und Audio muss im AAC-Format vorliegen.

>[!IMPORTANT]
>
>Sie müssen über den Schlüssel und den Initialisierungsvektor (IV) verfügen. Browser TVSDK verwendet den Schlüssel und IV, um den Stream vor dem Abspielen zu entschlüsseln.

Jeder geschützte Block enthält eine Ganzzahl von 16-Byte-Blöcken, die mit dem AES-128 cipher Block-CBC-Modus ohne Auffüllung verschlüsselt werden. CBC tritt in jedem geschützten Block auf, und am Beginn jedes neuen geschützten Blocks muss das IV auf seinen ursprünglichen Wert zurückgesetzt werden.

Die folgenden Codecs werden unterstützt:

* Für Videos wird H.264 unterstützt.
* Für Audio wird sample-AES nur für AAC unterstützt.

