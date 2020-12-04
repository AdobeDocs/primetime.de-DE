---
description: Zur Wiedergabe des DASH-Inhalts, der aus der Inhaltsverpackung stammt, muss der TVSDK-Client den Inhaltsentschlüsselungsschlüssel abrufen, der während des Verpackungsprozesses im wichtigen Akquise-Arbeitsablauf übergeben wurde. Der Entschlüsselungsschlüssel für den Clientinhalt wird dem Client normalerweise von einem Widevine/PlayReady-Lizenzserver als Antwort auf einen oder mehrere HTTP/HTTPS-Beiträge vom Client bereitgestellt.
seo-description: Zur Wiedergabe des DASH-Inhalts, der aus der Inhaltsverpackung stammt, muss der TVSDK-Client den Inhaltsentschlüsselungsschlüssel abrufen, der während des Verpackungsprozesses im wichtigen Akquise-Arbeitsablauf übergeben wurde. Der Entschlüsselungsschlüssel für den Clientinhalt wird dem Client normalerweise von einem Widevine/PlayReady-Lizenzserver als Antwort auf einen oder mehrere HTTP/HTTPS-Beiträge vom Client bereitgestellt.
seo-title: Übersicht über den Arbeitsablauf für Client-wichtige Anforderungen
title: Übersicht über den Arbeitsablauf für Client-wichtige Anforderungen
uuid: 2f01f0ae-adbf-42fa-a908-4b5b9410a26d
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# Arbeitsablauf für Client-Schlüsselanforderungen {#client-key-request-workflow-overview}

Zur Wiedergabe des DASH-Inhalts, der aus der Inhaltsverpackung stammt, muss der TVSDK-Client den Inhaltsentschlüsselungsschlüssel abrufen, der während des Verpackungsprozesses im wichtigen Akquise-Arbeitsablauf übergeben wurde. Der Entschlüsselungsschlüssel für den Clientinhalt wird dem Client normalerweise von einem Widevine/PlayReady-Lizenzserver als Antwort auf einen oder mehrere HTTP/HTTPS-Beiträge vom Client bereitgestellt.

Um den Entschlüsselungsschlüssel für Inhalte zu erhalten, muss der PSDK-Client folgende Schritte ausführen

* Nehmen Sie die PSS-Box des Inhalts auf, geben Sie sie an die Plattform und erhalten Sie als Antwort eine wichtige Anforderung.
* Senden Sie die Schlüsselanforderung über eine HTTP-POST an den entsprechenden Widevine/PlayReady-Lizenzserver.
* Geben Sie die Antwort des Servers an die Plattform weiter, die den Entschlüsselungsschlüssel für den Clientinhalt aus der Antwort extrahiert und für die Entschlüsselung von Inhalten verwendet.

Um die HTTP-POST für die Schlüsselanforderung zu senden, muss der Code zusammen mit den zusätzlichen Daten, die an den Beitrag angehängt werden müssen, an den PSDK-Client die URL des Lizenzservers übergeben. Die Wahl der URL und der zu übergebenden Daten hängt vom Widevine/PlayReady-Dienstleister ab, mit dem Sie arbeiten. Wenn Sie beispielsweise ExpressPlay für die Bereitstellung des Dienstes verwenden, geben Sie die entsprechende ExpressPlay Widevine/PlayReady-Lizenzserver-URL ein und hängen Sie an die ausgehende Schlüsselanforderung das ExpressPlay-Token an, das mit dem Verschlüsselungsschlüssel des Inhalts verknüpft ist. Sie können die entsprechende URL des ExpressPlay-Servers für die Lizenz von ExpressPlay aus der Dokumentation abrufen.