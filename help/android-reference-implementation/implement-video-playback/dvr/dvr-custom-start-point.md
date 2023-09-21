---
description: Sie können einen benutzerdefinierten Ausgangspunkt für die Eingabe eines DVR-Streams wählen, anstatt das Standardverhalten, den DVR-Stream zu Beginn mit der ConfigProvider-Klasse aufzurufen.
title: Auswählen eines benutzerdefinierten Startpunkts für DVR
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---

# Auswählen eines benutzerdefinierten Startpunkts für DVR {#choosing-a-custom-starting-point-for-dvr}

Sie können einen benutzerdefinierten Ausgangspunkt für die Eingabe eines DVR-Streams wählen, anstatt das Standardverhalten, den DVR-Stream zu Beginn mit der ConfigProvider-Klasse aufzurufen.

So legen Sie die Startzeit bis zum [ConfigProvider](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html) -Klasse:

1. Aktivieren [isCustomPositionPrefEnabled()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/ConfigProvider.html#isCustomPositionPrefEnabled()).
1. Festlegen der Startzeit in [retrieveStartTimePref()](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/IPlaybackConfig.html#iretrieveStartTimePref()).
1. Überprüfen Sie, ob die benutzerdefinierte Startposition aktiviert ist.
