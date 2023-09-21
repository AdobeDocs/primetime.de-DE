---
description: Die Wiederholung eines vollständigen Ereignisses (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Maßnahmen ergreifen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
title: Aktivieren von Anzeigen bei vollständiger Ereigniswiedergabe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Aktivieren von Anzeigen bei vollständiger Ereigniswiedergabe{#enable-ads-in-full-event-replay}

Die Wiederholung eines vollständigen Ereignisses (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Maßnahmen ergreifen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird ein `EXT-X-ENDLIST` -Tag an das Live-Manifest angehängt. Bei HLS muss die Variable `EXT-X-ENDLIST` -Tag bedeutet, dass der Stream ein VOD-Stream ist. TVSDK kann diesen Stream nicht automatisch von einem normalen VOD-Stream unterscheiden, um Anzeigen korrekt einzufügen.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie die `AdSignalingMode`.

Bei einem FER-Stream sollte der Adobe Primetime-Ad Decisioning-Server nicht die Liste der Werbeunterbrechungen bereitstellen, die in die Timeline eingefügt werden müssen, bevor die Wiedergabe gestartet wird. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalmodus alle Cue-Punkte aus dem FER-Manifest und geht für jeden Cue-Punkt zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anfrage, die mit einem Cue-Punkt verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen vor.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie die `AdSignalingMode` mithilfe von `AdvertisingMetadata.setSignalingMode`.

   Die gültigen Werte sind `DEFAULT, SERVER_MAP`, und `MANIFEST_CUES`.

   Sie müssen den Anzeigenanzeigemodus festlegen, bevor Sie `prepareToPlay`. Wenn TVSDK beginnt, Anzeigen aufzulösen und auf der Timeline zu platzieren, werden Änderungen am Anzeigenanzeigemodus ignoriert. Legen Sie den Modus fest, wenn Sie die `AuditudeSettings` -Objekt.

1. Wiedergabe fortsetzen.

<!--<a id="example_3567B4A0D53E4DA99C10C13244454026"></a>-->
