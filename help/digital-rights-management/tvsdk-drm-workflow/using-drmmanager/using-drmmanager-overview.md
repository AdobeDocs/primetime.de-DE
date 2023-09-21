---
title: Übersicht über die DRMManager-Klasse
description: Übersicht über die DRMManager-Klasse
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Verwenden der DRMManager-Klasse {#using-the-drmmanager-class}

Verwenden Sie die `DRMManager` -Klasse zur Verwaltung von Lizenzen und Primetime DRM-Lizenzserver-Sitzungen in Anwendungen.

**Lizenzverwaltung**

Wenn ein Gerät geschützten Inhalt wiedergibt, erhält die Laufzeitumgebung die zum Anzeigen des Inhalts erforderliche Lizenz und speichert sie zwischen. Wenn die Anwendung den Inhalt lokal speichert und die Lizenz die Offline-Wiedergabe zulässt, kann der Benutzer den Inhalt in der Anwendung ohne Netzwerkverbindung anzeigen. Verwenden der `DRMManager`, können Sie die Lizenz vorab zwischenspeichern. Die Anwendung muss nicht die Lizenz erwerben, die zur Ansicht des Inhalts erforderlich ist. Beispielsweise könnte Ihre Anwendung die Mediendatei herunterladen und dann die Lizenz erwerben, solange der Benutzer noch online ist.

Verwenden Sie zum Vorausfüllen einer Lizenz eine `DRMContentData` -Objekt. Die `DRMContentData` -Objekt enthält die URL des Primetime DRM-Lizenzservers, der die Lizenz bereitstellen kann, und beschreibt, ob eine Benutzerauthentifizierung erforderlich ist. Mit diesen Informationen können Sie die `DRMManager` `loadVoucher()` -Methode, um die Lizenz zu erhalten und zwischenzuspeichern. Der Ablauf für das Vorausfüllen von Lizenzen wird im Abschnitt *Vorausfüllen von Lizenzen für die Offline-Wiedergabe*.

**Sitzungsverwaltung**

Sie können auch die `DRMManager` um den Benutzer für einen Primetime DRM-Lizenzserver zu authentifizieren und persistente Sitzungen zu verwalten. Rufen Sie die `DRMManager` `authenticate()` -Methode, um eine Sitzung mit dem Primetime-DRM-Lizenzserver einzurichten. Wenn die Authentifizierung erfolgreich abgeschlossen wurde, wird die `DRMManager` sendet einen `DRMAuthenticationCompleteEvent` -Objekt. Dieses Objekt enthält ein Sitzungstoken. Sie können dieses Token speichern, um zukünftige Sitzungen festzulegen, sodass der Benutzer seine Kontoanmeldeinformationen nicht angeben muss. Übergeben Sie das Token an die `setAuthenticationToken()` -Methode, um eine neue authentifizierte Sitzung einzurichten. (Die Einstellungen des Servers, der das Token generiert hat, bestimmen den Ablauf des Tokens und andere Attribute).

## Umgang mit DRMStatus-Ereignissen {#handling-drmstatus-events}

Die `DRMManager` sendet einen `DRMStatusEvent` -Objekt nach einem Aufruf von `loadVoucher()` -Methode erfolgreich abgeschlossen. Wenn eine Lizenz abgerufen wird, hat die Eigenschaft detail des Ereignisobjekts den Wert: `DRM.voucherObtained`, und die Gutscheineigenschaft enthält die `DRMVoucher` -Objekt. Wenn keine Lizenz abgerufen wird, hat die Detaileigenschaft weiterhin den Wert: `DRM.voucherObtained`Die Gutscheineigenschaft ist jedoch null. Eine Lizenz kann nicht erworben werden, wenn Sie beispielsweise die Variable `LoadVoucherSetting` von `localOnly` und es gibt keine lokal zwischengespeicherte Lizenz. Wenn die Variable `loadVoucher()` -Aufruf nicht erfolgreich abgeschlossen wurde, möglicherweise aufgrund eines Authentifizierungs- oder Kommunikationsfehlers, wird die `DRMManager` sendet einen `DRMErrorEvent` oder `DRMAuthenticationErrorEvent` -Objekt.

## Umgang mit DRMAuthenticationComplete-Ereignissen{#handling-drmauthenticationcomplete-events}

Die `DRMManager` sendet einen `DRMAuthenticationCompleteEvent` -Objekt, wenn ein Benutzer durch einen Aufruf der `authenticate()` -Methode. Die `DRMAuthenticationCompleteEvent` -Objekt enthält ein wiederverwendbares Token, mit dem die Benutzerauthentifizierung über Anwendungssitzungen hinweg beibehalten werden kann. Übergeben dieses Tokens an `DRMManager` `setAuthenticationToken()` Methode zur Wiederherstellung der Sitzung. (Der Token-Ersteller legt Tokenattribute wie Ablauf fest. Adobe stellt keine API zur Prüfung von Tokenattributen bereit.)

## Umgang mit DRMAuthenticationError-Ereignissen{#handling-drmauthenticationerror-events}

Die `DRMManager` sendet einen `DRMAuthenticationErrorEvent` -Objekt, wenn ein Benutzer nicht erfolgreich über einen Aufruf von `authenticate()` oder `setAuthenticationToken()` -Methoden.
