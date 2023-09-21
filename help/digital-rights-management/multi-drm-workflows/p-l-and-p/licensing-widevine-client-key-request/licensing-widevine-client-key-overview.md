---
description: Um den aus der Inhaltspaketung resultierenden DASH-Inhalt wiederzugeben, muss der TVSDK-Client den Schlüssel für die Entschlüsselung des Inhalts abrufen, der während des Verpackungsprozesses im Workflow für die Schlüsselakquise übergeben wurde. Der Schlüssel zur Entschlüsselung des Clientinhalts wird normalerweise vom Widevine/PlayReady-Lizenzserver als Reaktion auf einen oder mehrere HTTP/HTTPS-Beiträge vom Client an den Client gesendet.
title: Übersicht über den Workflow für Client-Schlüsselanforderungen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Workflow für Client-Schlüsselanforderungen {#client-key-request-workflow-overview}

Um den aus der Inhaltspaketung resultierenden DASH-Inhalt wiederzugeben, muss der TVSDK-Client den Schlüssel für die Entschlüsselung des Inhalts abrufen, der während des Verpackungsprozesses im Workflow für die Schlüsselakquise übergeben wurde. Der Schlüssel zur Entschlüsselung des Clientinhalts wird normalerweise vom Widevine/PlayReady-Lizenzserver als Reaktion auf einen oder mehrere HTTP/HTTPS-Beiträge vom Client an den Client gesendet.

Um den Schlüssel zur Inhaltsentschlüsselung zu erhalten, muss der PSDK-Client die folgenden Schritte ausführen

* Erfassen Sie die Push-Box des Inhalts, geben Sie sie an die Plattform und erhalten Sie als Antwort eine wichtige Anfrage.
* Senden Sie die Schlüsselanfrage über eine HTTP-POST an den entsprechenden Widevine/PlayReady-Lizenzserver.
* Übergeben Sie die Antwort des Servers an die Plattform, die den Entschlüsselungsschlüssel für den Clientinhalt aus der Antwort extrahiert und zur Entschlüsselung des Inhalts verwendet.

Um die HTTP-POST für die Schlüsselanfrage zu senden, muss Ihr Code die Lizenzserver-URL zusammen mit zusätzlichen Daten, die an den Beitrag angehängt werden müssen, an den PSDK-Client übergeben. Die Auswahl der URL und der weiterzuleitenden Daten hängt vom Widevine/PlayReady Service Provider ab, mit dem Sie arbeiten. Wenn Sie beispielsweise ExpressPlay für die Bereitstellung des Dienstes verwenden, geben Sie die entsprechende URL des Lizenzservers ExpressPlay Widevine/PlayReady an und hängen Sie das ExpressPlay-Token an die Anfrage an den ausgehenden Schlüssel an, das mit dem Verschlüsselungsschlüssel des Inhalts verknüpft ist. Sie können die entsprechende ExpressPlay Widevine/PlayReady Lizenzserver-URL aus der ExpressPlay-Dokumentation abrufen.
