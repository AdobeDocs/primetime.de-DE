---
description: Sie können Ihren Player so einrichten, dass die Wiedergabe- und Gerätestatistiken des QoSProviders beliebig oft gelesen werden.
title: Anzeigen von QoS-Wiedergabe und Gerätestatistiken
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Anzeigen von QoS-Wiedergabe und Gerätestatistiken {#display-qos-playback-and-device-statistics}

Sie können Ihren Player so einrichten, dass die Wiedergabe- und Gerätestatistiken des QoSProviders beliebig oft gelesen werden.

Die `QoSProvider` -Klasse stellt verschiedene Statistiken bereit, darunter die Framerate, die Profil-Bitrate, die Gesamtzeit, die mit der Pufferung verbracht wurde, die Anzahl der Pufferversuche, die Zeit, die zum Abrufen des ersten Bytes vom ersten Videofragment erforderlich war, die Zeit, die zum Rendern des ersten Frames benötigt wurde, die derzeit gepufferte Länge und die Pufferzeit.

Die Referenzimplementierung bietet eine `QoSManager` -Klasse, in der Sie die Anzeige der QoS-Überlagerung aktivieren können. Sie können die QoS-Sichtbarkeit auch in der Benutzeroberfläche &quot;Einstellungen&quot;aktivieren:

![](assets/qos-configuration.jpg)

Die `QoSManager` verfolgt QoS-Statistiken, indem Geräteinformationen abgerufen, an den Medienplayer angehängt und mit den neuesten QoS-Informationen aktualisiert werden.

**Aktivieren oder Deaktivieren der Berichterstellung für QoS-Statistiken**

1. Erstellen Sie einen QoManager oder aktivieren Sie die QoS-Berichterstellung mithilfe von ManagerFactory.

   * So erstellen Sie einen QosManager:
      * Diese Anwendung muss die Werbe-Workflow-Funktion verwenden

   QoSManager qosManager = new QosManagerOn();

   * So verwenden Sie eine ManagerFactory, um die Anzeige von QoS-Statistiken zu ermöglichen:

   qosManager = ManagerFactory.getQosManager(
   <b>true</b>, config, mediaPlayer);

   >[!NOTE]
   >
   >Ändern des booleschen Werts in `false` deaktiviert QoS-Berichte.

2. Hinzufügen von Ereignis-Listenern:

   `qosManager.addEventListener(qosManagerEventListener);`

3. Erstellen Sie den QoS-Provider und hängen Sie ihn an den Kontext der Player-Aktivität an:

   `qosManager.createQOSProvider(getActivity());`

   >[!NOTE]
   >
   >Wenn die Player-Aktivität zerstört werden soll, rufen Sie [qosManager.killQOSProvider](https://help.adobe.com/en_US/primetime/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html#destroyQOSProvider()) , um den QOS-Provider zu bereinigen, indem er ihn vom Medienplayer trennt.

**Verwandte API-Dokumentation**

* [Klasse QosManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.html)
* [Klasse QosManagerOn](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManagerOn.html)
* [QosManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosManagerEventListener.html)
* [QosItem](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/QosManager.QosItem.html)
