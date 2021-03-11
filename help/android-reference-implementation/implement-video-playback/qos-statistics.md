---
description: Sie können Ihren Player so einrichten, dass er die Wiedergabe- und Gerätestatistiken des QoSProviders so oft wie nötig liest.
title: Anzeigen von QoS-Wiedergabe und Gerätestatistiken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Anzeigen der QoS-Wiedergabe und Gerätestatistik {#display-qos-playback-and-device-statistics}

Sie können Ihren Player so einrichten, dass er die Wiedergabe- und Gerätestatistiken des QoSProviders so oft wie nötig liest.

Die `QoSProvider`-Klasse stellt verschiedene Statistiken bereit, darunter die Bildrate, die Bitrate des Profils, die Gesamtdauer der Pufferung, die Anzahl der Pufferung-Versuche, die Zeit bis zum Abrufen des ersten Bytes aus dem ersten Videofragment, die Zeit bis zum Rendern des ersten Bilds, die aktuell gepufferte Länge und die Pufferzeit.

Die Referenz-Implementierung stellt eine `QoSManager`-Klasse bereit, mit der Sie die Anzeige der QoS-Überlagerung aktivieren können. Sie können die QoS-Sichtbarkeit auch in der Benutzeroberfläche &quot;Einstellungen&quot;aktivieren:

![](assets/qos-configuration.jpg)

Die `QoSManager` verfolgt QoS-Statistiken, indem Geräteinformationen abgerufen, an den Medienplayer angehängt und mit den neuesten Servicequalitätsinformationen aktualisiert werden.

**QoS-Statistiken-Berichte aktivieren oder deaktivieren**

1. Erstellen Sie einen QoManager oder aktivieren Sie den QoS-Berichte mit ManagerFactory.

   * So erstellen Sie einen QosManager:
      * Diese Anwendung muss die Funktion für den Arbeitsablauf für Anzeigen verwenden

   QoSManager qosManager = new QosManagerOn();

   * So verwenden Sie eine ManagerFactory, um die Anzeige der QoS-Statistiken zu aktivieren:

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >Wenn Sie den booleschen Wert in `false` ändern, wird der QoS-Berichte deaktiviert.

2. hinzufügen Ereignis-Listener:

   `qosManager.addEventListener(qosManagerEventListener);`

3. Erstellen Sie den QoS-Anbieter und fügen Sie ihn dem Kontext der Player-Aktivität hinzu:

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Wenn die Player-Aktivität zerstört werden soll, stellen Sie sicher, dass Sie [qosManager.deleteQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) aufrufen, um den QOS-Provider durch Abtrennen vom Medienplayer zu bereinigen.

**Verwandte API-Dokumentation**

* [Klasse QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Klasse QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
