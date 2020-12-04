---
description: Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
seo-description: Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.
seo-title: Anzeigen bei vollständiger Wiedergabe im Ereignis aktivieren
title: Anzeigen bei vollständiger Wiedergabe im Ereignis aktivieren
uuid: 70e463bd-332c-4f91-ac05-03e79c0939a4
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# Anzeigen im Vollbildmodus aktivieren{#enable-ads-in-full-event-replay}

Full-Ereignis Replay (FER) ist ein VOD-Asset, das als Live-/DVR-Asset fungiert. Daher muss Ihre Anwendung Schritte unternehmen, um sicherzustellen, dass Anzeigen korrekt platziert werden.

Für Live-Inhalte verwendet TVSDK die Metadaten/Hinweise im Manifest, um zu bestimmen, wo Anzeigen platziert werden sollen. Manchmal ähneln Live-/Lineare Inhalte jedoch möglicherweise VOD-Inhalten. Wenn beispielsweise Live-Inhalte abgeschlossen sind, wird dem Live-Manifest ein `EXT-X-ENDLIST`-Tag angehängt. Bei HLS bedeutet das `EXT-X-ENDLIST`-Tag, dass der Stream ein VOD-Stream ist. TVSDK kann diesen Stream nicht automatisch von einem normalen VOD-Stream unterscheiden, um Anzeigen korrekt einzufügen.

Ihre Anwendung muss TVSDK mitteilen, ob der Inhalt live oder VOD ist, indem Sie `AdSignalingMode` angeben.

Bei einem FER-Stream sollte der Adobe Primetime-Ad-Entscheidungsserver nicht die Liste von Werbeunterbrechungen bereitstellen, die vor dem Starten der Wiedergabe in die Zeitleiste eingefügt werden müssen. Dies ist der typische Prozess für VOD-Inhalte. Stattdessen liest TVSDK durch Angabe eines anderen Signalisierungsmodus alle Cue-Points aus dem FER-Manifest und wechselt für jeden Cue-Point zum Anzeigen-Server, um eine Werbeunterbrechung anzufordern. Dieser Prozess ähnelt Live-/DVR-Inhalten.

Zusätzlich zu jeder Anforderung, die mit einem Cue-Point verknüpft ist, stellt TVSDK eine zusätzliche Anzeigenanforderung für Pre-Roll-Anzeigen auf.

1. Rufen Sie von einer externen Quelle wie vCMS den zu verwendenden Signalmodus ab.
1. Erstellen Sie die werbebezogenen Metadaten.
1. Wenn das Standardverhalten überschrieben werden muss, geben Sie das `AdSignalingMode` mit `AdvertisingMetadata.setSignalingMode` an.

   Die gültigen Werte sind `DEFAULT, SERVER_MAP` und `MANIFEST_CUES`.

   Sie müssen den Anzeigensignalisierungsmodus festlegen, bevor Sie `prepareToPlay` aufrufen. Nachdem TVSDK-Beginn Anzeigen auflösen und auf der Zeitleiste platzieren, werden Änderungen am Anzeigensignalisierungsmodus ignoriert. Legen Sie den Modus fest, wenn Sie das `AuditudeSettings`-Objekt erstellen.

1. Fahren Sie mit der Wiedergabe fort.

<!--<a id="example_3567B4A0D53E4DA99C10C13244454026"></a>-->

