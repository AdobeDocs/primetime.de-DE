---
title: Übersicht über Out-of-Band-Lizenzen
description: Übersicht über Out-of-Band-Lizenzen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Out-of-Band-Lizenzen {#out-of-band-licenses}

Lizenzen können auch außerhalb des Bands erworben werden (ohne einen Primetime DRM-Lizenzserver zu kontaktieren), indem die Lizenz auf der Festplatte und im Speicher unter Verwendung der `storeVoucher()` -Methode.

Um verschlüsselte Videos in Primetime abzuspielen, muss die jeweilige Laufzeitumgebung die Lizenz für dieses Video erhalten. Die Lizenz enthält den Entschlüsselungsschlüssel des Videos und wird vom Primetime DRM-Lizenzserver generiert, den der Kunde bereitgestellt hat.

Die Laufzeitumgebung erhält diese Lizenz im Allgemeinen, indem sie eine Lizenzanfrage an den Primetime DRM-Lizenzserver sendet, der in den DRM-Metadaten des Videos angegeben ist ( `DRMContentData` -Klasse). Die Anwendung kann diese Lizenzanfrage durch Aufruf des Triggers `DRMManager.loadVoucher()` -Methode.

`DRMManager.storeVoucher()` ermöglicht dem Antrag den Versand von Lizenzen, die er außerhalb des Band erworben hat. Die Laufzeitumgebung kann dann den Lizenzanforderungsprozess überspringen und die weitergeleiteten Lizenzen für die Wiedergabe verschlüsselter Videos verwenden. Die Lizenz muss weiterhin vom Primetime DRM-Lizenzserver generiert werden, bevor sie außerhalb des Band erworben werden kann. Sie haben jedoch die Möglichkeit, die Lizenzen auf einem beliebigen HTTP-Server anstatt auf einem Primetime DRM-Lizenzserver zu hosten.

`DRMManager.storeVoucher()` wird auch verwendet, um die Lizenzfreigabe zwischen mehreren Geräten zu unterstützen. Nach Primetime DRM 3.0 wird diese Funktion als &quot;Device Domain Support&quot;bezeichnet. Wenn Ihre Implementierung diesen Anwendungsfall unterstützt, können Sie mehrere Computer mit der `DRMManager.addToDeviceGroup()` -Methode. Wenn es einen Computer mit einer gültigen domänengebundenen Lizenz für einen bestimmten Inhalt gibt, kann die Anwendung die serialisierte Lizenz mithilfe der `DRMVoucher.toByteArray()` -Methode und auf Ihren anderen Computern können Sie die Lizenzen mit der `DRMManager.storeVoucher()` -Methode.

## Über die Geräteregistrierung {#about-device-registration}

Alle Primetime-DRM-Lizenzen müssen zum Zeitpunkt der Erstellung an eine Endentität gebunden sein. Die Bindung ist der kryptografische Prozess, bei dem nur einer bestimmten Entität die Möglichkeit gegeben wird, die Lizenz zu nutzen. Dies ist notwendig, um &quot;Floating-Lizenzen&quot; zu verhindern, die von beliebigen Geräten verwendet werden können. Damit Primetime DRM Lizenzen &quot;vorgenerieren&quot;kann, muss die &quot;Zielgruppe&quot;dieser vorgenerierten Lizenzen bereits im Voraus bekannt sein. Primetime DRM bezeichnet dies als &quot;Geräteregistrierung&quot;.

## Gerät registrieren {#register-a-device}

Nehmen wir an, Sie haben die folgenden Aufgaben ausgeführt:

* Sie haben das Primetime DRM Server SDK eingerichtet.
* Sie haben einen HTTP-Server für die Ausgabe von vorgenerierten Lizenzen eingerichtet.
* Sie haben eine Primetime-Anwendung erstellt, um den geschützten Inhalt anzuzeigen.

 Die Phase der Geräteregistrierung umfasst die folgenden Aktionen:

1. Die Anwendung erstellt eine zufällig generierte ID.
1. Die Anwendung ruft die `DRMManager.authenticate()` -Methode. Die Anwendung muss die zufällig generierte ID in die Authentifizierungsanforderung aufnehmen. Schließen Sie beispielsweise die ID in das Feld &quot;Benutzername&quot;ein.
1. Die in Schritt 2 erwähnte Aktion führt dazu, dass Primetime DRM eine Authentifizierungsanfrage an den Server des Kunden sendet. Diese Anfrage enthält das Gerätezertifikat:
   1. Der Server extrahiert das Gerätezertifikat und die generierte ID aus der Anforderung und speichert sie.
   1. Das Kundenuntersystem generiert Lizenzen für dieses Gerätezertifikat im Voraus, speichert es und gewährt ihm Zugriff auf diese so, dass sie mit der generierten ID verknüpft werden. .
1. Der Server antwortet auf die Anfrage mit der Meldung &quot;Erfolg&quot;.
1. Die Anwendung speichert die generierte ID.

Nach der Geräteregistrierung verwendet die Anwendung die generierte ID auf dieselbe Weise wie die Geräte-ID im vorherigen Schema:
1. Die Anwendung versucht, die generierte ID zu finden.
1. Wenn die generierte ID gefunden wird, verwendet die Anwendung die generierte ID beim Herunterladen der vorgenerierten Lizenzen. Der Antrag sendet die Lizenzen zur Verwendung der `DRMManager.storeVoucher()` -Methode. .
1. Wenn die generierte ID nicht gefunden wird, durchläuft die Anwendung das Verfahren zur Geräteregistrierung.

## DRM-Werkseinstellung zurücksetzen {#drm-factory-reset}

Wenn der Benutzer des Geräts die Option zum Zurücksetzen der DRM-Factory aufruft, wird das Gerätezertifikat gelöscht. Um den geschützten Inhalt weiterhin wiederzugeben, muss die Anwendung das Verfahren zur Geräteregistrierung erneut durchlaufen. Wenn die Anwendung eine veraltete vorgenerierte Lizenz sendet, lehnt der Primetime DRM-Client sie ab, da die Lizenz für eine ältere Geräte-ID verschlüsselt wurde.

* Flash-API: [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Kann nur als Antwort auf bestimmte nicht wiederherstellbare DRM-Fehlercodes aufgerufen werden.)
* iOS-API: [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android-API: [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))
