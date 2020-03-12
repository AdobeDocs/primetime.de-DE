---
seo-title: Übersicht über die DRMManager-Klasse
title: Übersicht über die DRMManager-Klasse
uuid: 71ce061b-75b6-4ab5-8bbd-cafe7c3e4592
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Verwenden der DRMManager-Klasse {#using-the-drmmanager-class}

Verwenden Sie die `DRMManager` Klasse zum Verwalten von Lizenzen und Primetime DRM-Lizenzserversitzungen in Anwendungen.

**Lizenzverwaltung**

Wenn ein Gerät geschützten Inhalt wiedergibt, ruft die Laufzeitumgebung die für die Ansicht des Inhalts erforderliche Lizenz ab und speichert sie im Cache ab. Wenn die Anwendung den Inhalt lokal speichert und die Lizenz die Offline-Wiedergabe zulässt, kann der Benutzer den Inhalt in der Anwendung ohne Netzwerkverbindung Ansicht haben. Mit der `DRMManager`können Sie die Lizenz vorab zwischenspeichern. Der Antrag muss nicht die zur Ansicht des Inhalts erforderliche Lizenz erhalten. Ihre Anwendung könnte beispielsweise die Mediendatei herunterladen und dann die Lizenz erwerben, solange der Benutzer noch online ist.

Verwenden Sie zum Vorausladen einer Lizenz ein `DRMContentData` Objekt. Das `DRMContentData` Objekt enthält die URL des Primetime DRM-Lizenzservers, der die Lizenz bereitstellen kann, und beschreibt, ob eine Benutzerauthentifizierung erforderlich ist. Mit diesen Informationen können Sie die `DRMManager` Methode aufrufen, um die Lizenz abzurufen und `loadVoucher()` zu zwischenspeichern. Der Arbeitsablauf für Vorausfüllen-Lizenzen wird in den *Vorausfüllen-Lizenzen für die Offline-Wiedergabe* ausführlicher beschrieben.

**Sitzungsverwaltung**

Sie können auch die verwenden, `DRMManager` um den Benutzer auf einem Primetime DRM-Lizenzserver zu authentifizieren und persistente Sitzungen zu verwalten. Rufen Sie die `DRMManager` `authenticate()` Methode auf, um eine Sitzung mit dem Primetime DRM-Lizenzserver einzurichten. Nach erfolgreichem Abschluss der Authentifizierung `DRMManager` wird ein `DRMAuthenticationCompleteEvent` Objekt ausgelöst. Dieses Objekt enthält ein Sitzungstoken. Sie können dieses Token speichern, um zukünftige Sitzungen einzurichten, damit der Benutzer keine Kontoanmeldeinformationen angeben muss. Übergeben Sie das Token an die `setAuthenticationToken()` Methode, um eine neue authentifizierte Sitzung einzurichten. (Die Einstellungen des Servers, der das Token generiert hat, bestimmen den Ablauf des Tokens und andere Attribute).

## Umgang mit DRMStatus-Ereignissen {#handling-drmstatus-events}

Das `DRMManager` sendet ein `DRMStatusEvent` Objekt, nachdem ein Aufruf der `loadVoucher()` Methode erfolgreich abgeschlossen wurde. Wenn eine Lizenz abgerufen wird, hat die detail-Eigenschaft des Ereignis-Objekts den Wert: `DRM.voucherObtained`und die Eigenschaft &quot;voucher&quot;enthält das `DRMVoucher` Objekt. Wenn keine Lizenz abgerufen wird, hat die detail-Eigenschaft immer noch den Wert: `DRM.voucherObtained`; Die Eigenschaft &quot;voucher&quot;ist jedoch null. Eine Lizenz kann nicht erworben werden, wenn Sie z. B. die `LoadVoucherSetting` von verwenden `localOnly` und keine lokal zwischengespeicherte Lizenz vorhanden ist. Wenn der `loadVoucher()` Aufruf nicht erfolgreich abgeschlossen wird, möglicherweise aufgrund eines Authentifizierungs- oder Kommunikationsfehlers, sendet der `DRMManager` Aufruf stattdessen ein `DRMErrorEvent` oder `DRMAuthenticationErrorEvent` -Objekt.

## Handhabung von DRMAuthenticationComplete-Ereignissen{#handling-drmauthenticationcomplete-events}

Das `DRMManager` sendet ein `DRMAuthenticationCompleteEvent` Objekt, wenn ein Benutzer durch einen Aufruf der `authenticate()` Methode erfolgreich authentifiziert wurde. Das `DRMAuthenticationCompleteEvent` Objekt enthält ein wiederverwendbares Token, mit dem die Benutzerauthentifizierung über Anwendungssitzungen hinweg aufrechterhalten werden kann. Übergeben Sie dieses Token an die `DRMManager` `setAuthenticationToken()` Methode, um die Sitzung wiederherzustellen. (Der Token-Ersteller legt Tokenattribute wie Ablauf fest. Adobe stellt keine API zum Prüfen von Tokenattributen bereit.)

## Handhabung von DRMAuthenticationError-Ereignissen{#handling-drmauthenticationerror-events}

Das `DRMManager` sendet ein `DRMAuthenticationErrorEvent` Objekt, wenn ein Benutzer nicht erfolgreich durch einen Aufruf der `authenticate()` oder `setAuthenticationToken()` Methoden authentifiziert werden kann.