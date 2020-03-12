---
seo-title: Überblick über Out-of-Band-Lizenzen
title: Überblick über Out-of-Band-Lizenzen
uuid: 82e4529a-ee1b-4c0c-8885-e0e68319d1a0
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Out-of-Band-Lizenzen {#out-of-band-licenses}

Lizenzen können auch außerhalb des Bands erworben werden (ohne einen Primetime DRM License Server zu kontaktieren), indem die Lizenz auf der Festplatte und im Arbeitsspeicher mit der `storeVoucher()` Methode gespeichert wird.

Um verschlüsselte Videos in Primetime wiedergeben zu können, muss die jeweilige Laufzeitumgebung die Lizenz für dieses Video abrufen. Die Lizenz enthält den Entschlüsselungsschlüssel des Videos und wird vom Primetime DRM-Lizenzserver generiert, den der Kunde bereitgestellt hat.

Die Laufzeitumgebung erhält diese Lizenz in der Regel durch Senden einer Lizenzanforderung an den Primetime DRM-Lizenzserver, der in den DRM-Metadaten des Videos ( `DRMContentData` Klasse) angegeben ist. Die Anwendung kann diese Lizenzanforderung durch Aufruf der `DRMManager.loadVoucher()` Methode auslösen.

`DRMManager.storeVoucher()` ermöglicht dem Antrag, Lizenzen zu senden, die er außerhalb des Band erworben hat. Die Laufzeit kann dann den Lizenzanforderungsprozess überspringen und die weitergeleiteten Lizenzen für die Wiedergabe verschlüsselter Videos verwenden. Die Lizenz muss noch vom Primetime DRM-Lizenzserver generiert werden, bevor sie außerhalb des Bands erworben werden kann. Sie haben jedoch die Möglichkeit, die Lizenzen auf einem beliebigen HTTP-Server statt auf einem Primetime DRM-Lizenzserver zu hosten.

`DRMManager.storeVoucher()` wird auch zur Unterstützung der Lizenzfreigabe zwischen mehreren Geräten verwendet. Nach Primetime DRM 3.0 wird diese Funktion als &quot;Gerätedomänenunterstützung&quot;bezeichnet. Wenn Ihre Bereitstellung diesen Anwendungsfall unterstützt, können Sie mithilfe der `DRMManager.addToDeviceGroup()` Methode mehrere Computer für eine Gerätegruppe registrieren. Wenn es einen Computer mit einer gültigen domänengebundenen Lizenz für einen bestimmten Inhalt gibt, kann die Anwendung die serialisierte Lizenz mit der `DRMVoucher.toByteArray()` Methode extrahieren und auf Ihren anderen Computern können Sie die Lizenzen mit der `DRMManager.storeVoucher()` Methode importieren.

## Informationen zur Geräteregistrierung {#about-device-registration}

Alle Primetime-DRM-Lizenzen müssen zur Erstellungszeit an eine Endeinrichtung gebunden sein. Die Bindung ist der kryptografische Vorgang, bei dem nur einer bestimmten Entität die Möglichkeit gegeben wird, die Lizenz zu nutzen. Dies ist notwendig, um &quot;Floating-Lizenzen&quot; zu verhindern, die von beliebigen Geräten verwendet werden können. Damit Primetime DRM Lizenzen &quot;vorgenerieren&quot;kann, muss die &quot;Zielgruppe&quot;dieser vorab erstellten Lizenzen bereits bekannt sein. Primetime DRM bezeichnet dies als &quot;Geräteregistrierung&quot;.

## Gerät registrieren {#register-a-device}

Nehmen wir an, Sie haben die folgenden Aufgaben durchgeführt:

* Sie haben das Primetime DRM Server SDK eingerichtet.
* Sie haben einen HTTP-Server für die Ausgabe vorab generierter Lizenzen eingerichtet.
* Sie haben eine Primetime-Anwendung zur Ansicht des geschützten Inhalts erstellt.

 Die Geräteregistrierung umfasst die folgenden Aktionen:

1. Die Anwendung erstellt eine zufällig generierte ID.
1. Die Anwendung ruft die `DRMManager.authenticate()` Methode auf. Die Anwendung muss die zufällig generierte ID in die Authentifizierungsanforderung aufnehmen. Fügen Sie beispielsweise die ID in das Feld &quot;Benutzername&quot;ein.
1. Die in Schritt 2 erwähnte Aktion führt dazu, dass Primetime DRM eine Authentifizierungsanfrage an den Server des Kunden sendet. Diese Anforderung umfasst das Gerätezertifikat:
   1. Der Server extrahiert das Gerätezertifikat und die generierte ID aus der Anforderung und speichert sie.
   1. Das Teilsystem &quot;Kunde&quot;erstellt Lizenzen für dieses Gerätezertifikat vorab, speichert sie und gewährt Zugriff darauf in einer Weise, die sie mit der generierten ID verknüpft. .
1. Der Server antwortet auf die Anforderung mit einer Erfolgsmeldung.
1. Die Anwendung speichert die generierte ID.

Nach der Geräteregistrierung verwendet die Anwendung die generierte ID auf dieselbe Weise wie die Geräte-ID im vorherigen Schema:
1. Die Anwendung versucht, die generierte ID zu finden.
1. Wenn die generierte ID gefunden wird, verwendet die Anwendung beim Herunterladen der vorab erstellten Lizenzen die generierte ID. Der Antrag sendet die Lizenzen an den Primetime DRM-Client, um sie nach der `DRMManager.storeVoucher()` Methode zu verwenden. .
1. Wenn die generierte ID nicht gefunden wird, durchläuft die Anwendung das Geräteregistrierungsverfahren.

## DRM-Werkseinstellung {#drm-factory-reset}

Wenn der Benutzer des Geräts die Option zum Zurücksetzen der DRM-Factory aufruft, wird das Gerätezertifikat bereinigt. Um den geschützten Inhalt weiter abspielen zu können, muss die Anwendung erneut das Geräteregistrierungsverfahren durchlaufen. Wenn die Anwendung eine veraltete vorab generierte Lizenz sendet, lehnt der Primetime DRM-Client sie ab, da die Lizenz für eine ältere Geräte-ID verschlüsselt wurde.

* Flash-API: [DRMManager.resetDRMVouchers()](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html#resetDRMVouchers()) - (Kann nur als Reaktion auf bestimmte nicht wiederherstellbare DRM-Fehlercodes aufgerufen werden.)
* iOS-API: [DRMManager resetDRM](https://help.adobe.com/en_US/primetime/api/drm-apis/client/ios/interface_d_r_m_manager.html#a0dd6c9662428583196e0419d3ea69446)
* Android-API: [DRMManager.resetDRM()](https://help.adobe.com/en_US/primetime/api/drm-apis/client/android/com/adobe/ave/drm/DRMManager.html#resetDRM(com.adobe.ave.drm.DRMOperationErrorCallback,%20com.adobe.ave.drm.DRMOperationCompleteCallback))