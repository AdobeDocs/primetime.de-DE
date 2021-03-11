---
title: Übersicht über die DRMManager-Klasse
description: Übersicht über die DRMManager-Klasse
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# Verwenden der DRMManager-Klasse {#using-the-drmmanager-class}

Verwenden Sie die `DRMManager`-Klasse, um Lizenzen und Primetime DRM-Lizenzserversitzungen in Anwendungen zu verwalten.

**Lizenzverwaltung**

Wenn ein Gerät geschützten Inhalt wiedergibt, ruft die Laufzeitumgebung die für die Ansicht des Inhalts erforderliche Lizenz ab und speichert sie im Cache ab. Wenn die Anwendung den Inhalt lokal speichert und die Lizenz die Offline-Wiedergabe zulässt, kann der Benutzer den Inhalt in der Anwendung ohne Netzwerkverbindung Ansicht haben. Mit dem `DRMManager` können Sie die Lizenz vorab zwischenspeichern. Der Antrag muss nicht die zur Ansicht des Inhalts erforderliche Lizenz erhalten. Ihre Anwendung könnte beispielsweise die Mediendatei herunterladen und dann die Lizenz erwerben, solange der Benutzer noch online ist.

Verwenden Sie zum Vorausladen einer Lizenz ein `DRMContentData`-Objekt. Das `DRMContentData`-Objekt enthält die URL des Primetime DRM-Lizenzservers, der die Lizenz bereitstellen kann, und beschreibt, ob eine Benutzerauthentifizierung erforderlich ist. Mit diesen Informationen können Sie die `DRMManager` `loadVoucher()`-Methode aufrufen, um die Lizenz abzurufen und im Cache zu speichern. Der Arbeitsablauf für Vorausfüllen-Lizenzen wird ausführlicher unter *Vorausfüllen-Lizenzen für die Offline-Wiedergabe* beschrieben.

**Sitzungsverwaltung**

Sie können den `DRMManager` auch verwenden, um den Benutzer auf einem Primetime-DRM-Lizenzserver zu authentifizieren und persistente Sitzungen zu verwalten. Rufen Sie die `DRMManager` `authenticate()`-Methode auf, um eine Sitzung mit dem Primetime DRM-Lizenzserver einzurichten. Nach erfolgreichem Abschluss der Authentifizierung löst `DRMManager` ein `DRMAuthenticationCompleteEvent`-Objekt aus. Dieses Objekt enthält ein Sitzungstoken. Sie können dieses Token speichern, um zukünftige Sitzungen einzurichten, damit der Benutzer keine Kontoanmeldeinformationen angeben muss. Übergeben Sie das Token an die `setAuthenticationToken()`-Methode, um eine neue authentifizierte Sitzung einzurichten. (Die Einstellungen des Servers, der das Token generiert hat, bestimmen den Ablauf des Tokens und andere Attribute).

## Umgang mit DRMStatus-Ereignissen {#handling-drmstatus-events}

Das `DRMManager`-Objekt löst ein `DRMStatusEvent`-Objekt aus, nachdem ein Aufruf der `loadVoucher()`-Methode erfolgreich abgeschlossen wurde. Wenn eine Lizenz abgerufen wird, hat die detail-Eigenschaft des Ereignis-Objekts den Wert: `DRM.voucherObtained` und die voucher-Eigenschaft enthält das `DRMVoucher`-Objekt. Wenn keine Lizenz abgerufen wird, hat die detail-Eigenschaft immer noch den Wert: `DRM.voucherObtained`; Die Eigenschaft &quot;voucher&quot;ist jedoch null. Eine Lizenz kann nicht erworben werden, wenn Sie beispielsweise die `LoadVoucherSetting` von `localOnly` verwenden und keine lokal zwischengespeicherte Lizenz vorhanden ist. Wenn der Aufruf von `loadVoucher()` nicht erfolgreich abgeschlossen wird, möglicherweise aufgrund eines Authentifizierungs- oder Kommunikationsfehlers, löst `DRMManager` stattdessen ein `DRMErrorEvent`- oder `DRMAuthenticationErrorEvent`-Objekt aus.

## Handhabung von DRMAuthenticationComplete-Ereignissen{#handling-drmauthenticationcomplete-events}

Das `DRMManager`-Objekt löst ein `DRMAuthenticationCompleteEvent`-Objekt aus, wenn ein Benutzer durch einen Aufruf der `authenticate()`-Methode erfolgreich authentifiziert wurde. Das `DRMAuthenticationCompleteEvent`-Objekt enthält ein wiederverwendbares Token, mit dem die Benutzerauthentifizierung über Anwendungssitzungen hinweg aufrechterhalten werden kann. Übergeben Sie dieses Token an die `DRMManager` `setAuthenticationToken()`-Methode, um die Sitzung wiederherzustellen. (Der Token-Ersteller legt Tokenattribute wie Ablauf fest. Adobe stellt keine API zum Prüfen von Tokenattributen bereit.)

## Umgang mit DRMAuthenticationError-Ereignissen{#handling-drmauthenticationerror-events}

Das `DRMManager`-Objekt löst ein `DRMAuthenticationErrorEvent`-Objekt aus, wenn ein Benutzer nicht erfolgreich durch einen Aufruf der `authenticate()`- oder `setAuthenticationToken()`-Methoden authentifiziert werden kann.