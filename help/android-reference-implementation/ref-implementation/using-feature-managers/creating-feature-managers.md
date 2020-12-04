---
description: TVSDK-Funktionen werden durch die Konfiguration gesteuert und über den MediaPlayer implementiert.
seo-description: TVSDK-Funktionen werden durch die Konfiguration gesteuert und über den MediaPlayer implementiert.
seo-title: Erstellen von Funktionsmanagern durch Weiterleiten von Konfigurationsinformationen an den MediaPlayer
title: Erstellen von Funktionsmanagern durch Weiterleiten von Konfigurationsinformationen an den MediaPlayer
uuid: 106ececd-a670-4360-b000-a31fec65233c
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# Erstellen von Funktionsmanagern durch Weiterleiten von Konfigurationsinformationen an den MediaPlayer {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

TVSDK-Funktionen werden durch die Konfiguration gesteuert und über den MediaPlayer implementiert.

* Die Konfiguration ist die Liste bestimmter Einstellungen für die Funktion, z. B. die anfängliche Bitrate der ABR-Steuerung und die standardmäßige Sichtbarkeit von Untertiteln.

   Funktionsmanager müssen die Konfigurationen abrufen, um das Funktionsverhalten zu bestimmen.

   In der Primetime-Referenzimplementierung wird die Konfiguration in freigegebenen Voreinstellungen gespeichert. Sie können die Konfiguration jedoch auf jede für Ihre Umgebung sinnvolle Weise speichern.

* `MediaPlayer` ist das TVSDK-Medienplayer-Objekt, das die Videoressource enthält.

   Funktionsmanager registrieren TVSDK-Ereignis-Listener für dieses Player-Objekt, rufen Daten aus der Wiedergabesitzung ab und lösen TVSDK-Funktionen für die Wiedergabesitzung aus.

Jede Funktion verfügt über eine entsprechende Konfigurationsoberfläche. `CCManager` verwendet beispielsweise `ICCConfig`, um die Konfiguration abzurufen. `ICCConfig` enthält Methoden zum Abrufen der Konfigurationsinformationen, die sich ausschließlich auf die Untertitelung beziehen.

Das folgende Beispiel zeigt die Datei [!DNL ICCConfig.java], die für den Empfang von Informationen zur Sichtbarkeit der Bildunterschrift, zum Schriftstil und zur Schriftartkante von `MediaPlayer` konfiguriert wurde:

```java
// Constructor of CCManager 
 
<b>public CCManager(ICCConfig ccConfig, MediaPlayer mediaPlayer) {...}</b> 
  
// ICCConfig methods 
 
<b>public interface ICCConfig {</b> 
  
    /** 
     * Get the closed captioning visibility config 
     * 
     * @return true if visibility is set to true, false otherwise 
     */ 
    
<b> public boolean getCCVisibility();</b> 
  
    /** 
     * Get the closed captioning font style 
     * 
     * @return TextFormat.Font object represents font style 
     */ 
     
<b>public TextFormat.Font getCCFont();</b>

    /** 
     * Get the closed captioning font edge 
     * 
     * @return TextFormat.FontEdge represents of font edge 
     */ 
     
<b>public TextFormat.FontEdge getCCFontEdge();</b> 
... 
}
```

Eine Anwendung, die eine TVSDK-Funktion verwendet, kann ihren Funktionsmanager mit einem Konfigurationsanbieter und einem `MediaPlayer`-Objekt erstellen. Beispiel:

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

API-Dokumente zur Konfiguration von Feature Manager: [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)