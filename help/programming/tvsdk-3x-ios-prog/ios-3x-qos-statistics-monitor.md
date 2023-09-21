---
description: Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
title: Qualitätsstatistiken der Dienstleistung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Qualitätsstatistiken der Dienstleistung {#quality-of-service-statistics}

Die Servicequalität (QoS) bietet einen detaillierten Überblick über die Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

## Lesen von QOS-Wiedergabe, -Pufferung und Gerätestatistiken {#section_9996406E2D814FA382B77E3041CB02BC}

Sie können die Wiedergabe-, Pufferungs- und Gerätestatistiken aus dem `PTQOSProvider` -Klasse.

Die `PTQOSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter Informationen zur Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Es enthält auch Informationen zum Gerät, wie Modell, Betriebssystem und Geräte-ID des Herstellers.

>[!TIP]
>
>Sie können die Puffergröße der Wiedergabe nicht ändern, aber Sie können den Status der Puffergröße für das Debuggen oder die Analyse überwachen. `PTPlaybackInformation` enthält Eigenschaften wie `playbackBufferFull` und `playbackLikelyToKeepUp`.

1. Instanziieren eines Medienplayers
1. Erstellen Sie eine `PTQOSProvider` -Objekt und fügen Sie es an den Medienplayer an.

   Die `PTQOSProvider` -Konstruktor verwendet einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Optional) Lesen Sie die Wiedergabestatistiken.

   Eine Lösung zum Lesen der Wiedergabestatistiken besteht darin, einen Timer zu verwenden, z. B. eine `NSTimer`, der die neuen QoS-Werte regelmäßig aus der `PTQOSProvider`. Beispiel:

   ```
   - (void)printPlaybackInfoLog { 
       PTPlaybackInformation *playbackInfo = qosProvider.playbackInformation;  
       if (playbackInfo) { 
           // For example: 
           NSString *infoLog = [NSString stringWithFormat:@"observedBitrate :  
                                  %f\n",playbackInfo.observedBitrate]; 
           [consoleView logMessage:@"====%@\n\n",infoLog]; 
       } 
   }
   ```

1. (Optional) Lesen Sie die gerätespezifischen Informationen.

   ```
    PTDeviceInformation *devInfo = qosProvider.deviceInformation; 
   if (devInfo) { 
       [consoleView logMessage:@"=== qosDeviceInfo:==\n os =%@\n model =  
          %@\n id =%@\n\n", devInfo.os, devInfo.model, devInfo.id]; 
   } 
   [NSTimer scheduledTimerWithTimeInterval:2.0 target:self  
      selector:@selector(printPlaybackInfoLog) userInfo:nil repeats:YES];
   ```
