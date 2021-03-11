---
description: Sie können einen benutzerdefinierten Ausgangspunkt für die Eingabe eines DVR-Streams festlegen, anstatt dass standardmäßig der DVR-Stream zu Beginn über die ConfigProvider-Klasse eingegeben wird.
title: Auswählen eines benutzerdefinierten Startpunkts für DVR
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Auswählen eines benutzerdefinierten Startpunkts für DVR {#choosing-a-custom-starting-point-for-dvr}

Sie können einen benutzerdefinierten Ausgangspunkt für die Eingabe eines DVR-Streams festlegen, anstatt dass standardmäßig der DVR-Stream zu Beginn über die ConfigProvider-Klasse eingegeben wird.

So legen Sie die Beginn-Zeit mithilfe der Klasse [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) fest:

1. Aktivieren Sie [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. Legen Sie die Beginn-Zeit in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()) fest.
1. Überprüfen Sie, ob die Position des benutzerdefinierten Beginns aktiviert ist.
