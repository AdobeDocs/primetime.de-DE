---
description: MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen im Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Player-Status.
title: Benachrichtigungsinhalt
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---


# Benachrichtigungsinhalt {#notification-content}

MediaPlayerNotification-Objekte enthalten Informationen zu Änderungen im Player-Status, zu Warnungen und Fehlern. Fehler, die die Wiedergabe des Videos stoppen, führen auch zu einer Änderung des Player-Status.

Ihre Anwendung kann die Benachrichtigungen und Statusinformationen abrufen. Sie können mithilfe der Benachrichtigungsinformationen auch ein Protokollierungssystem für die Diagnose und Überprüfung erstellen.

Sie implementieren Ereignis-Listener, um Ereignis zu erfassen und darauf zu reagieren. In vielen Ereignissen werden Statusbenachrichtigungen für `MediaPlayerNotification` bereitgestellt.

`MediaPlayerNotification` enthält Informationen zum Status des Spielers.

TVSDK stellt eine chronologische Liste der `MediaPlayerNotification`-Benachrichtigungen bereit. Jede Benachrichtigung enthält die folgenden Informationen:

* Zeitstempel
* Diagnostische Metadaten, die aus den folgenden Elementen bestehen:

   * `type`: INFO, WARN oder FEHLER.
   * `code`: Eine numerische Darstellung der Benachrichtigung.
   * `name`: Eine für Menschen lesbare Beschreibung der Anmeldung, z. B. SEEK_ERROR
   * `metadata`: Schlüssel/Wert-Paare, die relevante Informationen zur Benachrichtigung enthalten. Beispielsweise stellt ein Schlüssel mit dem Namen `URL` einen Wert bereit, der eine URL im Zusammenhang mit der Benachrichtigung ist.

   * `innerNotification`: Ein Verweis auf ein anderes  `MediaPlayerNotification` Objekt, das sich direkt auf diese Benachrichtigung auswirkt.

Sie können diese Informationen zur späteren Analyse lokal speichern oder zur Protokollierung und grafischen Darstellung an einen Remote-Server senden.

## Einrichten des Benachrichtigungssystems {#set-up-your-notification-system}

Sie können auf Benachrichtigungen warten und eigene Benachrichtigungen zum Benachrichtigungsverlauf hinzufügen.

Der Kern des Primetime Player-Benachrichtigungssystems ist die `Notification`-Klasse, die eine eigenständige Benachrichtigung darstellt.

Die `NotificationHistory`-Klasse stellt einen Mechanismus zum Akkumulieren von Benachrichtigungen bereit. Es speichert ein Protokoll von Benachrichtigungsobjekten (NotificationHistoryItem), das eine Sammlung von Benachrichtigungen darstellt.

So empfangen Sie Benachrichtigungen:

* Benachrichtigungen abrufen
* hinzufügen Benachrichtigungen zum Benachrichtigungsverlauf

1. Suchen Sie nach Statusänderungen.
1. Implementieren Sie den Rückruf `MediaPlayer.PlaybackEventListener.onStateChanged`.
1. TVSDK übergibt zwei Parameter an den Rückruf:

   * Der neue Status ( `MediaPlayer.PlayerState`)
   * Ein `MediaPlayerNotification`-Objekt

## hinzufügen Echtzeit-Protokollierung und -Debugging {#add-real-time-logging-and-debugging}

Sie können Benachrichtigungen verwenden, um die Echtzeit-Anmeldung in Ihrer Videoanwendung zu implementieren.

Mit dem Benachrichtigungssystem können Sie Protokollierungs- und Debugging-Informationen für die Diagnose und Validierung erfassen, ohne das System übermäßig zu belasten.

>[!IMPORTANT]
>
>Das Back-End für die Protokollierung ist nicht Teil eines Produktions-Setups und wird voraussichtlich nicht mit hohem Traffic verarbeitet. Wenn Ihre Implementierung nicht vollständig sein muss, sollten Sie die Effizienz der Datenübertragung berücksichtigen, um eine Überlastung Ihres Systems zu vermeiden.

Im Folgenden finden Sie ein Beispiel zum Abrufen von Benachrichtigungen.

1. Erstellen Sie einen Timer-basierten Ausführungsthread für Ihre Videoanwendung, der die vom TVSDK-Benachrichtigungssystem erfassten Daten in regelmäßigen Abständen Abfrage.

1. Wenn das Zeitintervall zu groß ist und die Liste des Ereignisses zu klein ist, wird die Liste des Ereignisses für Benachrichtigungen überlaufen. Führen Sie einen der folgenden Schritte aus, um diesen Überlauf zu vermeiden:

   * Verringern Sie das Zeitintervall, das den Thread auslöst, der nach neuen Ereignissen fragt.
   * Vergrößern Sie die Benachrichtigungs-Liste.

1. Serialisieren Sie die neuesten Benachrichtigungs-Ereignis-Einträge im JSON-Format und senden Sie die Einträge zur Nachbearbeitung an einen Remoteserver.

   Der Remote-Server könnte dann die bereitgestellten Daten grafisch in Echtzeit anzeigen.
1. Um den Verlust von Benachrichtigungs-Ereignissen zu ermitteln, suchen Sie nach Lücken in der Sequenz von Ereignis-Indexwerten.

   Jedes Benachrichtigungs-Ereignis verfügt über einen Indexwert, der automatisch durch die `session.NotificationHistory`-Klasse inkrementiert wird.

## ID3-Tags {#id-tags}

ID3-Tags enthalten Informationen zu einer Audio- oder Videodatei, wie z. B. den Titel der Datei oder den Namen des Künstlers. TVSDK erkennt ID3-Tags auf der Segmentebene Transport Stream (TS) in HLS-Streams und sendet ein Ereignis. Die Anwendung kann Daten aus dem Tag extrahieren.

>[!IMPORTANT]
>
>TVSDK erkennt ID3-Metadaten (Version 2.3.0 oder 2.4.0) in Audio- (AAC) und Video-Streams (H.264) in allen möglichen Kodierungen (ASCII, UTF8, UTF16-BE oder UTF16-LE). Dabei werden ID3-Tags ignoriert, die sich nicht in einer der erkannten Versionen oder Formate befinden. Nicht angegebene Kodierung wird als UTF8 behandelt.

Wenn TVSDK ID3-Metadaten erkennt, wird eine Benachrichtigung mit den folgenden Daten ausgegeben:

* InfoCode = 303007
* TYPE = ID3
* NAME = nicht vorhanden
* ID = 0

1. Implementieren Sie einen Ereignis-Listener für `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` und registrieren Sie ihn beim `MediaPlayer`-Objekt.

   TVSDK ruft diesen Listener auf, wenn er ID3-Metadaten erkennt.

   >[!NOTE]
   >
   >Benutzerdefinierte Anzeigenbezeichnungen verwenden dasselbe `onTimedMetadata`-Ereignis, um die Erkennung eines neuen Tags anzuzeigen. Dies sollte keine Verwirrung stiften, da auf Manifestebene benutzerdefinierte Anzeigenbezeichnungen erkannt werden und ID3-Tags im Stream eingebettet werden. Weitere Informationen finden Sie unter custom-tags-configure .

1. Abrufen der Metadaten.

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
