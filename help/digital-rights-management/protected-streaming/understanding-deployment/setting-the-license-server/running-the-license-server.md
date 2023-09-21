---
title: Ausführen des DRM-Servers für geschütztes Streaming
description: Ausführen des DRM-Servers für geschütztes Streaming
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Ausführen des DRM-Servers für geschütztes Streaming {#running-the-drm-server-for-protected-streaming}

Bevor Sie den Adobe Primetime DRM-Server für geschütztes Streaming starten können, sollten Sie die Gültigkeit der Einstellungen in den Konfigurationsdateien überprüfen.

Sie können die Gültigkeit der Einstellungen mithilfe der Dienstprogramme überprüfen, die mit dem Lizenzserver bereitgestellt wurden. (Siehe *Konfigurationsprüfer* in diesem Handbuch.

Wenn Sie Tomcat und den Lizenzserver starten möchten, müssen Sie [!DNL catalina.bat start] oder [!DNL catalina.sh start] von Tomcat [!DNL bin] Verzeichnis.

Nachdem der Server gestartet wurde, müssen Sie überprüfen, ob er korrekt konfiguriert wurde, indem Sie `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` in einem Browserfenster. Wenn die Mandantenkonfiguration erfolgreich geladen wurde, wird eine Bestätigungsmeldung angezeigt.

## Protokolldateien {#log-files}

Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.

>[!NOTE]
>
>Wenn die aktuellen Protokolldateien gelöscht oder verschoben werden, während der Server ausgeführt wird, wird die Protokolldatei möglicherweise nicht erneut erstellt. Daher können einige Protokollinformationen gelöscht werden.

### Protokollordnerstruktur {#section_F490A483D60145ADBC21038914C39203}

Protokollverzeichnisse sind zur einfachen Verwendung strukturiert. Der Protokollordner hat die folgende Struktur:

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

### Globale Protokolldatei {#section_1CFA90748142439C9F3BE380969539DA}

die globale Protokolldatei, [!DNL flashaccess-global.log], befindet sich unter *LicenseServer.LogRoot*. Das Protokoll kann Protokollmeldungen enthalten, die vom Adobe Primetime DRM Java SDK oder Protokollmeldungen während der Zeit generiert wurden, als der Server initialisiert wurde.

### Protokolldatei der Partition {#section_5660137CD6AA40519E72A4315534846B}

die Partitionsprotokolldatei, [!DNL flashaccess-partition.log], befindet sich im `<LicenseServer.LogRoot>/flashaccesserver` Verzeichnis. Er enthält Protokollmeldungen, die während der Verarbeitung einer Lizenzanfrage generiert wurden.

### Mandantenprotokolldatei {#section_F0257CC0831647F18A746B4F02E3E910}

die Mandantenprotokolldatei jedes Mandanten, [!DNL flashaccess-tenant.log], befindet sich unter `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Das Mandantenprotokoll enthält Prüfinformationen, die die einzelnen für diesen Mandanten generierten Lizenzen beschreiben.

## Aktualisieren von Konfigurationsdateien {#updating-configuration-files}

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers (globale Konfiguration oder Mandantenkonfiguration) liest, werden die Konfigurationsinformationen im Speicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanfrage von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.

Bei jeder Änderung der Konfigurationsdatei speichert der Lizenzserver den Zeitpunkt, zu dem die Datei zuletzt geändert wurde. In einem konfigurierbaren Intervall überprüft der Server, ob sich die Zeit für die Dateiänderung geändert hat. Wenn er geändert wurde, lädt der Server automatisch den Inhalt der Konfigurationsdatei neu.

Wenn Sie steuern möchten, wie oft der Server nach Updates sucht, müssen Sie die Variable `refreshDelaySeconds` -Attribut im `Caching` -Element der globalen Konfigurationsdatei. Wenn beispielsweise `refreshDelaySeconds` auf 3600 Sekunden eingestellt ist, aktualisiert der Server die Konfiguration innerhalb von höchstens einer Stunde nach der Änderungszeit der Konfigurationsdatei. Wenn `refreshDelaySeconds` auf 0 gesetzt ist, überprüft der Server bei jeder Anfrage auf Konfigurationsaktualisierungen. Es wird nicht empfohlen, `refreshDelaySeconds` in Produktionsumgebungen auf einen niedrigen Wert zu setzen, da dies die Leistung beeinträchtigen kann.

Die `Caching` -Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl setzen, die kleiner als die Gesamtanzahl der Mandanten ist, um die zum Zwischenspeichern der Konfigurationsinformationen verwendete Speicherkapazität zu begrenzen. Wenn eine Anfrage für einen Mandanten empfangen wird, der sich nicht im Cache befindet, wird die Konfiguration geladen, bevor die Anfrage verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Die zwischengespeicherte Version der Konfiguration wird in den folgenden Situationen weiterhin verwendet (bis zum nächsten Mal, wenn der Server nach Aktualisierungen sucht):

* Wenn eine Änderung in einer Konfigurationsdatei oder in einer der Zertifikatdateien gespeichert wird, auf die im [!DNL flashaccess-tenant.xml] Datei, während der Server versucht, die Datei zu lesen
* Wenn der Zeitstempel der Datei vor der aktuellen Zeit weniger als eine Sekunde beträgt
* Wenn der Zeitstempel der Datei in der Zukunft liegt

Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht dann, die Datei erneut zu laden, wenn er das nächste Mal eine Anfrage für diesen Mandanten erhält.

### Aktualisieren der globalen Konfigurationsdatei {#section_AA546C72442646CFB8906AEEBDF50587}

Sie können das HSM-Kennwort in [!DNL flashaccess-global.xml] jederzeit verfügbar sein. Die Änderungen werden beim nächsten Neuladen der Konfigurationsdatei durch den Server wirksam. Änderungen an den Protokollierungs- und Caching-Elementen werden jedoch nicht neu geladen. Sie müssen den Server neu starten, bevor Änderungen für diese Elemente wirksam werden.

### Mandantenkonfigurationsdatei aktualisieren {#section_71624DB8DF28480F84F34F0FF7FD4365}

Sie können alle Werte ändern, die im [!DNL flashaccess-tenant.xml] -Datei zu einem beliebigen Zeitpunkt. Die Änderungen werden beim nächsten Neuladen der Konfigurationsdatei durch den Server wirksam. Außerdem überprüft der Server alle Änderungen an den Anmeldedaten ( [!DNL .pfx]) Dateien und Packager-Zulassungsliste-Zertifikatdateien, auf die in der Mandantenkonfigurationsdatei verwiesen wird.
