---
description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-description: Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.
seo-title: Qualität der Dienstleistungsstatistiken
title: Qualität der Dienstleistungsstatistiken
uuid: c08c1031-616a-4776-92e2-1c405467689b
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Qualität der Dienststatistiken {#quality-of-service-statistics}

Die Servicequalität (QoS) Angebot eine detaillierte Ansicht der Leistung der Video-Engine. TVSDK bietet detaillierte Statistiken über Wiedergabe, Pufferung und Geräte.

## Lesen Sie die QOS-Wiedergabe-, Puffer- und Gerätestatistik {#section_9996406E2D814FA382B77E3041CB02BC}

Sie können die Statistiken zu Wiedergabe, Pufferung und Gerät aus der `PTQOSProvider`-Klasse lesen.

Die `PTQOSProvider`-Klasse stellt verschiedene Statistiken bereit, einschließlich Informationen über Pufferung, Bitraten, Bildraten, Zeitdaten usw.

Er enthält außerdem Informationen zum Gerät, wie Modell, Betriebssystem und Geräte-ID des Herstellers.

>[!TIP]
>
>Sie können die Größe des Wiedergabepuffers nicht ändern, aber Sie können den Status der Puffergröße für das Debugging oder die Analyse überwachen. `PTPlaybackInformation` enthält Eigenschaften wie  `playbackBufferFull` und  `playbackLikelyToKeepUp`.

1. Instanziieren eines Medienplayers.
1. Erstellen Sie ein `PTQOSProvider`-Objekt und fügen Sie es an den Medienplayer an.

   Der Konstruktor `PTQOSProvider` nimmt einen Player-Kontext, damit er gerätespezifische Informationen abrufen kann.

   ```
   qosProvider = [[PTQOSProvider alloc]initWithPlayer:self.player]; 
   ```

1. (Optional) Lesen Sie die Wiedergabestatistik.

   Eine Lösung zum Lesen der Wiedergabestatistik besteht darin, einen Timer zu verwenden, z. B. einen `NSTimer`, der die neuen QoS-Werte regelmäßig von den `PTQOSProvider` abruft. Beispiel:

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
