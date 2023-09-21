---
description: Die Konfigurationsdatei "flashaccess-tenant.xml"enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten.
title: Mandantenkonfigurationsdatei
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# Mandantenkonfigurationsdatei{#tenant-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-tenant.xml&quot;enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten.

Jeder Mandant unterstützt seine eigene Instanz dieser Konfigurationsdatei, die sich unter `<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`. Siehe `configs/flashaccessserver/tenants/sampletenant` -Verzeichnis für eine Beispiel-Mandantenkonfigurationsdatei.

Sie können alle Dateipfade in der Mandantenkonfigurationsdatei als absolute Pfade oder als Pfade angeben, die relativ zum Konfigurationsverzeichnis des Mandanten sind (`<LicenseServer.ConfigRoot>/flashaccessserver/tenants/<tenantname>`).

Die Mandantenkonfigurationsdatei enthält:

* *Transportberechtigung* — Gibt eine oder mehrere von Adobe ausgestellte Transportberechtigungen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einem [!DNL .pfx] und ein Kennwort oder einen Alias für eine auf einem HSM gespeicherte Berechtigung. Hier können mehrere solcher Anmeldeinformationen angegeben werden, entweder als Dateipfade, als Schlüssel-Alias oder beides.

  Siehe *Umgang mit Zertifikataktualisierungen* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten* für weitere Informationen darüber, wann zusätzliche Anmeldeinformationen benötigt werden.

* *Lizenzserver-Berechtigungen* — Gibt eine oder mehrere Lizenzserver-Anmeldeinformationen (Zertifikat und privater Schlüssel) an, die von Adobe ausgestellt wurden. Sie können die Anmeldeinformationen des Lizenzservers als Pfad zu einem [!DNL .pfx] und ein Kennwort oder einen Alias für eine auf einem HSM gespeicherte Berechtigung. Hier können mehrere solcher Anmeldeinformationen angegeben werden, entweder als Dateipfade, als Schlüssel-Alias oder beides.

  Siehe *Umgang mit Zertifikataktualisierungen* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten* für weitere Informationen darüber, wann zusätzliche Anmeldeinformationen benötigt werden.

* *Wichtige Serverzertifikate* — Gibt optional das Lizenzserverzertifikat des Key-Servers an, das von Adobe ausgestellt wurde. Sie können das Lizenzserverzertifikat des Schlüsselservers als Pfad zu einem [!DNL .cer] -Datei oder einem Alias für ein Zertifikat, das auf einem HSM gespeichert ist. Diese Option muss angegeben werden, um Lizenzen für Inhalte auszustellen, die mit einer DRM-Richtlinie verpackt sind, die die Bereitstellung von Remote-Schlüsseln für iOS-Geräte erfordert.

* *Benutzerdefinierte Autorisierer* — Gibt optional benutzerdefinierte Autorisierungsklassen an, die für jede Lizenzanforderung aufgerufen werden sollen. Wenn mehrere Autorisierer angegeben sind, werden sie in der aufgeführten Reihenfolge aufgerufen.
* *Liste der zugelassenen Packager* — Gibt optional Zertifikate an, die Entitäten identifizieren, die zum Verpacken von Inhalten für diesen Lizenzserver berechtigt sind. Wenn keine Packager-Zertifikate angegeben sind, gibt der Server Lizenzen für Inhalte aus, die von einem beliebigen Packager gepackt werden. Wenn der Server eine Lizenzanfrage von einem nicht autorisierten Packager erhält, wird die Anfrage verweigert.
* *Unterstützte Mindestclientversion* Siehe Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten .

* *Nutzungsregeln*

   * *Lizenzzwischenspeicherung* — Optional gibt an, wie lange Sie die Lizenz auf dem Client speichern können. Standardmäßig ist die Lizenzzwischenspeicherung deaktiviert. Wenn Sie die Lizenzzwischenspeicherung für einen begrenzten Zeitraum aktivieren möchten, müssen Sie das Enddatum oder die Anzahl der Sekunden festlegen, für die die Lizenz gespeichert werden soll (beginnend mit dem Zeitpunkt der Lizenzerteilung). Wenn Sie die Anzahl der Sekunden auf 0 festlegen, wird das Lizenzzwischenspeichern deaktiviert.

     >[!NOTE]
     >
     >Alle Lizenzen, die der Server für geschütztes Streaming ausgestellt hat, beinhalten eine Gültigkeitsdauer von 24 Stunden (86400 Sekunden). Dieser Wert gilt implizit als Obergrenze für das Enddatum bzw. die Enddauer, das bzw. die für die Lizenzzwischenspeicherung festgelegt ist, mit einem Maximalwert von 86400 Sekunden, auch wenn das Schema höhere Grenzen erzwingt.

   * *Recht abspielen* — Es muss mindestens ein Recht angegeben werden. Wenn Sie mehrere Berechtigungen angeben, verwendet der Client die erste Berechtigung, die alle Anforderungen erfüllt.

      * *Output Protection* — Steuert, ob die Ausgabe auf externe Rendering-Geräte geschützt werden soll.
      * *AIR- und SWF-Anwendungsbeschränkungen* — Optionale Zulassungsliste von SWF- und AIR-Anwendungen, die Inhalte wiedergeben können (z. B. sind nur die angegebenen Anwendungen zulässig). SWF-Anwendungen werden durch eine URL oder den Digest der SWF und die maximale Zeit für den Download und die Verifizierung des Digest identifiziert.

        Siehe *SWF Hash Calculator* für Informationen zur Berechnung der SWF-Digest.

        Eine Herausgeber-ID und eine optionale Anwendungs-ID, eine minimale Version und eine maximale Version identifizieren AIR- und iOS-Anwendungen. Wenn Sie keine Anwendungseinschränkungen angeben, können alle SWF- oder AIR-Anwendungen den Inhalt abspielen.

      * *DRM- und Laufzeitmodulbeschränkungen* — Gibt die Mindestsicherheitsstufe an, die für das DRM/Runtime-Modul erforderlich ist. Enthält optional eine Blockierungsliste von Versionen, die den Inhalt nicht abspielen dürfen. Modulversionen werden anhand von Attributen wie dem Betriebssystem und/oder einer Versionsnummer identifiziert.

        DRM-Modulbeschränkungen und Laufzeitmodulbeschränkungen unterstützen jetzt die folgenden zusätzlichen Attribute:

         * `oemVendor`
         * `model`
         * `screenType`

        Die folgenden Attribute sind jetzt optional:

         * `osVersion`
         * `version`

      * *Anforderungen an die Gerätefunktionen* — Gibt optional die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind.
      * *Anforderungen an die Jaille-Erkennung* - Gibt optional an, dass die Wiedergabe für Geräte, auf denen eine Unterbrechung erkannt wird, nicht zulässig ist.

Weitere Informationen finden Sie in den Kommentaren in der Beispielkonfigurationsdatei für Mandanten .
