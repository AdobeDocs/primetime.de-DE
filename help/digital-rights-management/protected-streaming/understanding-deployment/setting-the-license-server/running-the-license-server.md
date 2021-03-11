---
title: Ausführen des DRM-Servers für geschütztes Streaming
description: Ausführen des DRM-Servers für geschütztes Streaming
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# Ausführen des DRM-Servers für geschütztes Streaming {#running-the-drm-server-for-protected-streaming}

Bevor Sie den Adobe Primetime DRM-Server für geschütztes Streaming Beginn haben, sollten Sie die Gültigkeit der Einstellungen in den Konfigurationsdateien überprüfen.

Sie können die Gültigkeit der Einstellungen mithilfe der Dienstprogramme überprüfen, die mit dem Lizenzserver bereitgestellt wurden. (Siehe *Configuration Validator* in diesem Handbuch.

Wenn Sie Tomcat und den Lizenzserver Beginn haben möchten, müssen Sie [!DNL catalina.bat start] oder [!DNL catalina.sh start] aus dem Tomcat-Ordner [!DNL bin] ausführen.

Nachdem der Server gestartet wurde, müssen Sie überprüfen, ob er korrekt konfiguriert wurde, indem Sie `https://<lic<span></span>ense-server-host:port>/flashaccessserver/<tenant-name>/flashaccess/license/v1` in einem Browserfenster öffnen. Wenn die Mandantenkonfiguration erfolgreich geladen wurde, wird eine Bestätigungsmeldung angezeigt.

## Protokolldateien {#log-files}

Die vom Adobe Primetime DRM-Server für die geschützte Streaming-Anwendung generierten Protokolldateien befinden sich in dem von LicenseServer.LogRoot angegebenen Ordner.

>[!NOTE]
>
>Wenn die aktuellen Protokolldateien während der Ausführung des Servers gelöscht oder verschoben werden, wird die Protokolldatei möglicherweise nicht erneut erstellt. Daher können einige Protokollinformationen gelöscht werden.

### Protokollordnerstruktur {#section_F490A483D60145ADBC21038914C39203}

Protokollordner sind für eine einfache Verwendung strukturiert. Der Protokollordner hat die folgende Struktur:

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

Die globale Protokolldatei [!DNL flashaccess-global.log] befindet sich unter *LicenseServer.LogRoot*. Das Protokoll kann Protokollmeldungen enthalten, die das Adobe Primetime DRM Java SDK oder Protokollmeldungen während der Zeit generiert haben, in der der Server initialisiert wurde.

### Partitionsprotokolldatei {#section_5660137CD6AA40519E72A4315534846B}

Die Partitionsprotokolldatei [!DNL flashaccess-partition.log] befindet sich im Ordner `<LicenseServer.LogRoot>/flashaccesserver`. Es enthält Protokollmeldungen, die während der Verarbeitung einer Lizenzanforderung generiert wurden.

### Mandanten-Protokolldatei {#section_F0257CC0831647F18A746B4F02E3E910}

Die Protokolldatei ([!DNL flashaccess-tenant.log]) jedes Mandanten befindet sich in `<LicenseServer.LogRoot>/flashaccesserver/tenants/<tenantname>`. Das Mandantenprotokoll enthält Informationen zum Audit, in denen jede für diesen Mandanten generierte Lizenz beschrieben wird.

## Konfigurationsdateien {#updating-configuration-files} aktualisieren

Sobald der Lizenzserver eine der Konfigurationsdateien des Lizenzservers liest (globale Konfiguration oder Mandantenkonfiguration), werden die Konfigurationsinformationen im Arbeitsspeicher zwischengespeichert. Daher müssen die Dateien nicht für jede Lizenzanforderung von der Festplatte gelesen werden. Der Server lässt jedoch auch zu, dass die meisten Werte in den Konfigurationsdateien geändert werden, ohne dass ein Neustart des Servers erforderlich ist, damit die Änderungen wirksam werden.

Wenn Sie die Konfigurationsdatei ändern, speichert der Lizenzserver den Zeitpunkt, zu dem die Datei zuletzt geändert wurde. In einem konfigurierbaren Intervall prüft der Server, ob sich die Dateiänderungszeit geändert hat. Wenn er geändert wurde, lädt der Server automatisch den Inhalt der Konfigurationsdatei neu.

Wenn Sie steuern möchten, wie oft der Server nach Updates sucht, müssen Sie das `refreshDelaySeconds`-Attribut im `Caching`-Element der globalen Konfigurationsdatei festlegen. Wenn `refreshDelaySeconds` beispielsweise auf 3600 Sekunden eingestellt ist, aktualisiert der Server die Konfiguration innerhalb von höchstens einer Stunde nach der Änderungszeit der Konfigurationsdatei. Ist `refreshDelaySeconds` auf 0 gesetzt, sucht der Server bei jeder Anforderung nach Konfigurationsaktualisierungen. Es wird nicht empfohlen, `refreshDelaySeconds` in einer beliebigen Produktions-Umgebung auf einen niedrigen Wert festzulegen, da dies die Leistung beeinträchtigen kann.

Das `Caching`-Element steuert auch, wie viele Mandantenkonfigurationen gleichzeitig zwischengespeichert werden. Sie können diesen Wert auf eine Zahl setzen, die kleiner als die Gesamtanzahl der Mieter ist, um die Menge des Speichers zu begrenzen, der zum Zwischenspeichern der Konfigurationsinformationen verwendet wird. Wenn eine Anforderung für einen Mandanten empfangen wird, der sich nicht im Cache befindet, wird die Konfiguration geladen, bevor die Anforderung verarbeitet werden kann. Wenn der Cache voll ist, wird der zuletzt verwendete Mandant aus dem Cache entfernt.

Die zwischengespeicherte Version der Konfiguration wird in folgenden Situationen weiterhin verwendet (bis zum nächsten Mal, wenn der Server nach Updates sucht):

* Wenn eine Änderung in einer Konfigurationsdatei oder einer der Zertifikatdateien gespeichert wird, auf die in der Datei [!DNL flashaccess-tenant.xml] verwiesen wird, während der Server versucht, die Datei zu lesen
* Wenn der Zeitstempel der Datei vor der aktuellen Zeit weniger als eine Sekunde liegt
* Wenn der Zeitstempel der Datei in der Zukunft liegt

Wenn keine zwischengespeicherte Version vorhanden ist, schlägt das Laden der Konfiguration fehl und ein Fehler wird an den Client zurückgegeben. Der Server versucht dann, die Datei erneut zu laden, wenn er das nächste Mal eine Anforderung für diesen Mandanten erhält.

### Aktualisieren der globalen Konfigurationsdatei {#section_AA546C72442646CFB8906AEEBDF50587}

Sie können das HSM-Kennwort jederzeit in [!DNL flashaccess-global.xml] ändern. Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Änderungen an den Elementen &quot;Protokollierung&quot;und &quot;Zwischenspeicherung&quot;werden jedoch nicht neu geladen. Sie müssen den Server neu starten, bevor Änderungen an diesen Elementen wirksam werden.

### Aktualisieren der Mandant-Konfigurationsdatei {#section_71624DB8DF28480F84F34F0FF7FD4365}

Sie können jederzeit alle Werte ändern, die in der Datei [!DNL flashaccess-tenant.xml] angegeben sind. Die Änderungen werden beim nächsten Laden der Konfigurationsdatei durch den Server wirksam. Der Server sucht außerdem nach allen Änderungen in allen Berechtigungsdateien ( [!DNL .pfx]) und Packager-Zulassungslisten-Zertifikatdateien, auf die in der Mietkonfigurationsdatei verwiesen wird.