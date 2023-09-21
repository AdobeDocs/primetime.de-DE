---
description: TVSDK-Funktionen werden durch die Konfiguration gesteuert und über den MediaPlayer implementiert.
title: Erstellen von Funktionsmanagern durch Übergabe von Konfigurationsinformationen an den MediaPlayer
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Erstellen von Funktionsmanagern durch Übergabe von Konfigurationsinformationen an den MediaPlayer {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}

TVSDK-Funktionen werden durch die Konfiguration gesteuert und über den MediaPlayer implementiert.

* Konfiguration ist die Liste spezifischer Einstellungen für die Funktion, z. B. die anfängliche Bitrate der ABR-Steuerung und die standardmäßige Sichtbarkeit der verdeckten Untertitel.

  Feature Manager müssen die Konfigurationen abrufen, um das Verhalten der Funktionen zu bestimmen.

  In der Primetime-Referenzimplementierung wird die Konfiguration in freigegebenen Voreinstellungen gespeichert. Sie können die Konfiguration jedoch auf jede für Ihre Umgebung sinnvolle Weise speichern.

* `MediaPlayer` ist das TVSDK-Medienplayer-Objekt, das die Videoressource enthält.

  Feature Manager registrieren TVSDK-Ereignis-Listener für dieses Player-Objekt, rufen Daten aus der Wiedergabesitzung ab und Trigger TVSDK-Funktionen für die Wiedergabesitzung.

Jede Funktion verfügt über eine entsprechende Konfigurationsoberfläche. Beispiel: `CCManager` uses `ICCConfig` , um die Konfiguration abzurufen. `ICCConfig` enthält Methoden, um die Konfigurationsinformationen abzurufen, die sich nur auf die Untertitelung beziehen.

Das folgende Beispiel zeigt die [!DNL ICCConfig.java] -Datei, die für den Empfang von Informationen über Sichtbarkeit, Schriftschnitt und Schriftrand der geschlossenen Beschriftung konfiguriert ist. `MediaPlayer`:

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

Eine Anwendung, die eine TVSDK-Funktion verwendet, kann ihren Feature Manager mit einem Konfigurationsanbieter und einem `MediaPlayer` -Objekt. Beispiel:

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

API-Dokumente zur Konfiguration von Feature Manager: [Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)
