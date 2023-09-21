---
description: In der Regel sind alle Primetime-DRM-Lizenzen zum Zeitpunkt der Erstellung an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen auf verschiedenen Geräten ohne Autorisierung freigeben. Zusätzlich zur geräteübergreifenden Bindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder eine Gerätegruppe zu binden.
title: Verschlüsselten Inhalt mit Domain-Unterstützung abspielen
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Unterstützung der Gerätedomäne {#device-domain-support}

In der Regel sind alle Primetime-DRM-Lizenzen zum Zeitpunkt der Erstellung an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen auf verschiedenen Geräten ohne Autorisierung freigeben. Zusätzlich zur geräteübergreifenden Bindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder eine Gerätegruppe zu binden.

Wenn die Inhaltsmetadaten angeben, dass die Registrierung der Gerätedomäne erforderlich ist, kann die Anwendung eine API aufrufen, um einer Gerätegruppe beizutreten. Diese Aktion Trigger die Anforderung einer Domänenregistrierung, die an den Domänenserver gesendet werden soll. Sobald eine Lizenz für eine Gerätegruppe erteilt wurde, kann die Lizenz exportiert und für andere Geräte freigegeben werden, die der Gerätegruppe beigetreten sind.

Die Gerätegruppeninformationen werden dann in der `DRMContentData` `VoucherAccessInfo` -Objekt, das dann verwendet wird, um die Informationen darzustellen, die zum erfolgreichen Abrufen und Verwenden einer Lizenz erforderlich sind.

## Verschlüsselten Inhalt mit Domain-Unterstützung abspielen {#play-encrypted-content-using-domain-support}

Um verschlüsselten Inhalt mit Primetime DRM wiederzugeben, führen Sie die folgenden Schritte aus:

1. Verwenden `VoucherAccessInfo.deviceGroup`, überprüfen Sie, ob die Gerätegruppenregistrierung erforderlich ist.
1. Wenn eine Authentifizierung erforderlich ist:
   1. Verwenden Sie die `DeviceGroupInfo.authenticationMethod` -Eigenschaft ermitteln, ob eine Authentifizierung erforderlich ist.
   1. Wenn eine Authentifizierung erforderlich ist, authentifizieren Sie den Benutzer, indem Sie einen der folgenden Schritte ausführen:

      * Benutzernamen und Kennwort des Benutzers abrufen und aufrufen `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)`.
      * Abrufen eines zwischengespeicherten/vorgenerierten Authentifizierungstokens und Aufrufen `DRMManager.setAuthenticationToken()`.

   1. Aufrufen `DRMManager.addToDeviceGroup()`
1. Rufen Sie die Lizenz für den Inhalt ab, indem Sie eine der folgenden Aufgaben ausführen:
   1. Verwenden Sie die `DRMManager.loadVoucher()` -Methode.
   1. Beziehen Sie die Lizenz von einem anderen Gerät, das in derselben Gerätegruppe registriert ist, und stellen Sie die Lizenz für die `DRMManager` durch die `DRMManager.storeVoucher()` -Methode.
1. Abspielen des verschlüsselten Inhalts mit dem `Primetime.play()` -Methode.
Um die Lizenz für den Inhalt zu exportieren, kann jedes Gerät die rohen Bytes der Lizenz mithilfe der `DRMVoucher.toByteArray()` -Methode, nachdem Sie die Lizenz vom Primetime DRM-Lizenzserver erhalten haben. Inhaltsanbieter beschränken normalerweise die Anzahl der Geräte in einer Gerätegruppe. Wenn das Limit erreicht ist, müssen Sie möglicherweise die `DRMManager.removeFromDeviceGroup()` -Methode auf einem nicht verwendeten Gerät, bevor das aktuelle Gerät registriert wird.
