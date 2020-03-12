---
description: Normalerweise sind alle Primetime-DRM-Lizenzen zur Erstellungszeit an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen ohne Autorisierung auf verschiedenen Geräten freigeben können. Neben der Gerätebindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder Gerätegruppe zu binden.
seo-description: Normalerweise sind alle Primetime-DRM-Lizenzen zur Erstellungszeit an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen ohne Autorisierung auf verschiedenen Geräten freigeben können. Neben der Gerätebindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder Gerätegruppe zu binden.
seo-title: Verschlüsselte Inhalte mithilfe der Domänenunterstützung wiedergeben
title: Verschlüsselte Inhalte mithilfe der Domänenunterstützung wiedergeben
uuid: 8854cc0f-9bfc-4833-82d7-a3f46ac88e06
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Unterstützung von Gerätedomänen {#device-domain-support}

Normalerweise sind alle Primetime-DRM-Lizenzen zur Erstellungszeit an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen ohne Autorisierung auf verschiedenen Geräten freigeben können. Neben der Gerätebindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder Gerätegruppe zu binden.

Wenn die Inhaltsmetadaten angeben, dass die Registrierung der Gerätedomäne erforderlich ist, kann die Anwendung eine API aufrufen, um einer Gerätegruppe beizutreten. Durch diese Aktion wird eine Domänenregistrierungsanfrage an den Domänenserver gesendet. Nachdem eine Lizenz für eine Gerätegruppe erteilt wurde, kann die Lizenz exportiert und für andere Geräte freigegeben werden, die der Gerätegruppe beigetreten sind.

Die Gerätegruppeninformationen werden dann im `DRMContentData` `VoucherAccessInfo` Objekt verwendet, das dann zur Darstellung der Informationen verwendet wird, die zum erfolgreichen Abrufen und Konsumieren einer Lizenz erforderlich sind.

## Verschlüsselte Inhalte mithilfe der Domänenunterstützung wiedergeben {#play-encrypted-content-using-domain-support}

So geben Sie verschlüsselte Inhalte mit Primetime DRM wieder:

1. Überprüfen Sie `VoucherAccessInfo.deviceGroup`mithilfe der Funktion, ob die Gerätegruppenregistrierung erforderlich ist.
1. Wenn Authentifizierung erforderlich ist:
   1. Verwenden Sie die `DeviceGroupInfo.authenticationMethod` Eigenschaft, um herauszufinden, ob eine Authentifizierung erforderlich ist.
   1. Wenn eine Authentifizierung erforderlich ist, authentifizieren Sie den Benutzer, indem Sie einen der folgenden Schritte ausführen:

      * Rufen Sie den Benutzernamen und das Kennwort des Benutzers ab und rufen Sie `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`auf.
      * Besorgen Sie sich ein zwischengespeichertes/vorab generiertes Authentifizierungstoken und rufen Sie `DRMManager.setAuthenticationToken()`auf.
   1. Aufrufen `DRMManager.addToDeviceGroup()`
1. Erwerben Sie die Inhaltslizenz, indem Sie eine der folgenden Aufgaben ausführen:
   1. Verwenden Sie die `DRMManager.loadVoucher()` Methode.
   1. Rufen Sie die Lizenz von einem anderen Gerät ab, das in derselben Gerätegruppe registriert ist, und stellen Sie die Lizenz ` DRMManager` nach der `DRMManager.storeVoucher()` Methode bereit.
1. Wiedergabe des verschlüsselten Inhalts mit der `Primetime.play()` Methode
Um die Lizenz für den Inhalt zu exportieren, kann jedes der Geräte die Rohdaten der Lizenz mit der `DRMVoucher.toByteArray()` Methode bereitstellen, nachdem die Lizenz vom Primetime DRM-Lizenzserver bezogen wurde. Content Provider beschränken in der Regel die Anzahl der Geräte in einer Gerätegruppe. Wenn der Grenzwert erreicht wird, müssen Sie die `DRMManager.removeFromDeviceGroup()` Methode möglicherweise auf einem nicht verwendeten Gerät aufrufen, bevor Sie das aktuelle Gerät registrieren.