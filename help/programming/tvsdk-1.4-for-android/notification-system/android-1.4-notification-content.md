---
description: MediaPlayerNotification -Objekte liefern Informationen zu Änderungen des Player-Status, von Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Player-Status.
title: Benachrichtigungsinhalt
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# Benachrichtigungsinhalt {#notification-content}

MediaPlayerNotification -Objekte liefern Informationen zu Änderungen des Player-Status, von Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Player-Status.

Ihre Anwendung kann die Benachrichtigung und die Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für Diagnose und Validierung erstellen.

Sie implementieren Ereignis-Listener, um Ereignisse zu erfassen und darauf zu reagieren. Viele Ereignisse bieten `MediaPlayerNotification` Statusbenachrichtigungen.

`MediaPlayerNotification` enthält Informationen zum Status des Players.

TVSDK bietet eine chronologische Liste von `MediaPlayerNotification` Benachrichtigungen. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Benachrichtigung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel-Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispiel: ein Schlüssel mit dem Namen `URL` stellt einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf einen anderen `MediaPlayerNotification` -Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen lokal zur späteren Analyse speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Benachrichtigungssystem einrichten {#set-up-your-notification-system}

Sie können Benachrichtigungen überwachen und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime Player-Benachrichtigungssystems ist der `Notification` -Klasse, die eine eigenständige Benachrichtigung darstellt.

Die `NotificationHistory` -Klasse bietet einen Mechanismus zum Ansammeln von Benachrichtigungen. Es speichert ein Protokoll von Benachrichtigungsobjekten (NotificationHistoryItem), das eine Sammlung von Benachrichtigungen darstellt.

Benachrichtigungen erhalten:

* Benachrichtigungen abrufen
* Hinzufügen von Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren des `MediaPlayer.PlaybackEventListener.onStateChanged` Callback.
1. TVSDK übergibt zwei Parameter an den Rückruf:

   * Der neue Status ( `MediaPlayer.PlayerState`)
   * A `MediaPlayerNotification` Objekt

## Echtzeit-Protokollierung und -Debugging hinzufügen {#add-real-time-logging-and-debugging}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Protokollierung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für Diagnose und Validierung erfassen, ohne das System übermäßig zu belasten.

>[!IMPORTANT]
>
>Das Protokollierungs-Backend ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel für den Abruf von Benachrichtigungen.

1. Erstellen Sie einen Timer-basierten Ausführungs-Thread für Ihre Videoanwendung, der regelmäßig die vom TVSDK-Benachrichtigungssystem erfassten Daten abfragt.

1. Wenn das Intervall des Timers zu groß ist und die Größe der Ereignisliste zu klein ist, wird die Benachrichtigungsereignisliste überlaufen. Um diesen Überlauf zu vermeiden, führen Sie einen der folgenden Schritte aus:

   * Verringern Sie das Zeitintervall, das den Thread steuert, der nach neuen Ereignissen abfragt.
   * Vergrößern Sie die Benachrichtigungsliste.

1. Serialisieren Sie die neuesten Benachrichtigungsereigniseinträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remote-Server.

   Der Remote-Server könnte dann die bereitgestellten Daten grafisch in Echtzeit anzeigen.
1. Um den Verlust von Benachrichtigungsereignissen zu erkennen, suchen Sie nach Lücken in der Reihenfolge der Ereignisindexwerte.

   Jedes Benachrichtigungsereignis verfügt über einen Indexwert, der automatisch durch die Variable `session.NotificationHistory` -Klasse.

## ID3-Tags {#id-tags}

ID3-Tags bieten Informationen zu einer Audio- oder Videodatei, wie den Titel der Datei oder den Namen des Künstlers. TVSDK erkennt ID3-Tags auf der Segmentebene des Transport-Streams (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem -Tag extrahieren.

>[!IMPORTANT]
>
>TVSDK erkennt ID3-Metadaten (Version 2.3.0 oder 2.4.0) in Audio- (AAC) und Video-Streams (H.264) in jeder der möglichen Kodierungen (ASCII, UTF8, UTF16-BE oder UTF16-LE). Dabei werden ID3-Tags ignoriert, die sich nicht in einer der erkannten Versionen oder Formate befinden. Nicht angegebene Kodierung wird als UTF8 behandelt.

Wenn TVSDK ID3-Metadaten erkennt, wird eine Benachrichtigung mit den folgenden Daten ausgegeben:

* InfoCode = 303007
* TYPE = ID3
* NAME = nicht vorhanden
* ID = 0

1. Implementieren eines Ereignis-Listeners für `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` und registrieren Sie sie bei der `MediaPlayer` -Objekt.

   TVSDK ruft diesen Listener auf, wenn ID3-Metadaten erkannt werden.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigencodes verwenden dieselbe `onTimedMetadata` -Ereignis, um die Erkennung eines neuen Tags anzuzeigen. Dies sollte keine Verwirrung verursachen, da benutzerdefinierte Anzeigencodes auf Manifestebene erkannt und ID3-Tags in den Stream eingebettet werden. Weitere Informationen finden Sie unter custom-tags-configure .

1. Rufen Sie die Metadaten ab.

   ```java
   @Override 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```
