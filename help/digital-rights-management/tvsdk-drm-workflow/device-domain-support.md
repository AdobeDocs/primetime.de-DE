---
description: In der Regel sind alle Primetime-DRM-Lizenzen zum Zeitpunkt der Erstellung an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen auf verschiedenen Geräten ohne Autorisierung freigeben. Zusätzlich zur geräteübergreifenden Bindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder eine Gerätegruppe zu binden.
title: Verschlüsselten Inhalt mit Domain-Unterstützung abspielen
exl-id: 3c9badfc-046b-4c56-bde1-7b3b708bfaa2
source-git-commit: 59f7f8aa82be59c4012ee80648032600590bc4e1
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Unterstützung von Gerätedomänen {#device-domain-support}

In der Regel sind alle Primetime-DRM-Lizenzen zum Zeitpunkt der Erstellung an ein eindeutiges Gerät gebunden. Diese Bindung verhindert, dass Benutzer Lizenzen auf verschiedenen Geräten ohne Autorisierung freigeben. Zusätzlich zur geräteübergreifenden Bindung bietet Primetime DRM die Möglichkeit, Lizenzen an eine Gerätedomäne oder eine Gerätegruppe zu binden.

Wenn die Inhaltsmetadaten angeben, dass die Registrierung der Gerätedomäne erforderlich ist, kann die Anwendung eine API aufrufen, um einer Gerätegruppe beizutreten. Diese Aktion Trigger die Anforderung einer Domänenregistrierung, die an den Domänenserver gesendet werden soll. Sobald eine Lizenz für eine Gerätegruppe erteilt wurde, kann die Lizenz exportiert und für andere Geräte freigegeben werden, die der Gerätegruppe beigetreten sind.

Die Gerätegruppeninformationen werden dann im `DRMContentData` `VoucherAccessInfo` -Objekt verwendet, das dann verwendet wird, um die Informationen darzustellen, die zum erfolgreichen Abrufen und Verwenden einer Lizenz erforderlich sind.

## Verschlüsselten Inhalt mit Domain-Unterstützung abspielen {#play-encrypted-content-using-domain-support}

Um verschlüsselten Inhalt mit Primetime DRM wiederzugeben, führen Sie die folgenden Schritte aus:

1. Überprüfen Sie mithilfe von `VoucherAccessInfo.deviceGroup`, ob die Gerätegruppenregistrierung erforderlich ist.
1. Wenn eine Authentifizierung erforderlich ist:
   1. Verwenden Sie die `DeviceGroupInfo.authenticationMethod`-Eigenschaft, um herauszufinden, ob eine Authentifizierung erforderlich ist.
   1. Wenn eine Authentifizierung erforderlich ist, authentifizieren Sie den Benutzer, indem Sie einen der folgenden Schritte ausführen:

      * Rufen Sie den Benutzernamen und das Kennwort des Benutzers ab und rufen Sie `DRMManager.authenticate(deviceGroup.serverURL, deviceGroup.domain, username, password)` auf.
      * Rufen Sie ein zwischengespeichertes/vorgeneriertes Authentifizierungstoken ab und rufen Sie `DRMManager.setAuthenticationToken()` auf.
   1. Aufrufen von `DRMManager.addToDeviceGroup()`
1. Rufen Sie die Lizenz für den Inhalt ab, indem Sie eine der folgenden Aufgaben ausführen:
   1. Verwenden Sie die `DRMManager.loadVoucher()` -Methode.
   1. Rufen Sie die Lizenz von einem anderen Gerät ab, das in derselben Gerätegruppe registriert ist, und stellen Sie die Lizenz für `DRMManager` über die `DRMManager.storeVoucher()`-Methode bereit.
1. Geben Sie den verschlüsselten Inhalt mit der `Primetime.play()`-Methode wieder.
Um die Lizenz für den Inhalt zu exportieren, kann jedes Gerät die rohen Bytes der Lizenz mithilfe der `DRMVoucher.toByteArray()`-Methode bereitstellen, nachdem es die Lizenz vom Primetime DRM-Lizenzserver erhalten hat. Inhaltsanbieter beschränken normalerweise die Anzahl der Geräte in einer Gerätegruppe. Wenn die Grenze erreicht ist, müssen Sie möglicherweise die `DRMManager.removeFromDeviceGroup()`-Methode auf einem nicht verwendeten Gerät aufrufen, bevor Sie das aktuelle Gerät registrieren.
