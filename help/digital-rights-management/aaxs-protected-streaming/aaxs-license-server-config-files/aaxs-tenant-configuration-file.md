---
title: Mandantenkonfigurationsdatei
description: Mandantenkonfigurationsdatei
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Mandantenkonfigurationsdatei {#tenant-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-tenant.xml&quot;enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten. Jeder Mandant verfügt über eine eigene Instanz dieser Konfigurationsdatei in *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*. Siehe [!DNL configs/flashaccessserver/tenants/sampletenant] -Verzeichnis für eine Beispiel-Mandantenkonfigurationsdatei.

Sie können alle Dateipfade in der Mandantenkonfigurationsdatei als absolute Pfade oder Pfade relativ zum Konfigurationsverzeichnis des Mandanten (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*).

Die Mandantenkonfigurationsdatei enthält:

* **Transportberechtigung** — Gibt eine oder mehrere von Adobe ausgestellte Transportberechtigungen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer .pfx-Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Anmeldeinformationen angegeben werden, entweder als Dateipfade, als Schlüssel-Alias oder beides. Siehe &quot;[Umgang mit Zertifikataktualisierungen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)&quot;in *Verwenden des Adobe Access SDK zum Schutz von Inhalten* für weitere Informationen darüber, wann zusätzliche Anmeldeinformationen benötigt werden.
* **Lizenzserver-Berechtigungen** — Gibt eine oder mehrere von Adobe ausgestellte Lizenzserver-Anmeldeinformationen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer .pfx-Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Anmeldeinformationen angegeben werden, entweder als Dateipfade, als Schlüssel-Alias oder beides. Weitere Informationen dazu, wann zusätzliche Anmeldeinformationen erforderlich sind, finden Sie unter Umgang mit Zertifikataktualisierungen unter Verwenden des Adobe Access SDK zum Schützen von Inhalten .
* **Wichtige Serverzertifikate** — Optional. Gibt das vom Adobe ausgestellte Lizenzserver-Zertifikat des Key Server an. Kann als Pfad zu einer .cer-Datei oder als Alias zu einem auf einem HSM gespeicherten Zertifikat angegeben werden. Diese Option muss angegeben werden, um Lizenzen für Inhalte zu erteilen, die mit einer Richtlinie gepackt sind, die die Bereitstellung von Remote-Schlüsseln für iOS-Geräte erfordert.
* **Benutzerdefinierte Autorisierer** — Optional. Gibt benutzerdefinierte Autorisierungsklassen an, die für jede Lizenzanforderung aufgerufen werden sollen. Wenn mehrere Autorisierer angegeben sind, werden sie in der aufgeführten Reihenfolge aufgerufen. Weitere Informationen finden Sie unter &quot;[Benutzerdefinierte Autorisierungserweiterungen](../../aaxs-protected-streaming/custom-authorization-extensions.md)&quot;.
* **Liste der zugelassenen Packager** — Optional. Gibt Zertifikate an, die Entitäten identifizieren, die zum Verpacken von Inhalten für diesen Lizenzserver berechtigt sind. Wenn keine Packager-Zertifikate angegeben sind, gibt der Server Lizenzen für Inhalte aus, die von einem beliebigen Packager gepackt wurden.
* **Unterstützte Mindestclientversion** (Siehe *Verwenden des Adobe Access SDK zum Schutz von Inhalten*).
* **Nutzungsregeln**

   * **Lizenzzwischenspeicherung** — Optional. Gibt an, wie lange die Lizenz auf dem Client gespeichert werden kann. Standardmäßig ist die Lizenzzwischenspeicherung deaktiviert. Um die Lizenzzwischenspeicherung für einen begrenzten Zeitraum zu aktivieren, legen Sie das Enddatum oder die Anzahl der Sekunden fest, für die die Lizenz gespeichert werden soll (beginnend mit der Lizenzerteilung). Wenn Sie die Anzahl der Sekunden auf 0 festlegen, wird das Lizenzzwischenspeichern deaktiviert.

     Beachten Sie, dass alle vom Server für geschütztes Streaming ausgestellten Lizenzen eine Gültigkeitsdauer von 24 Stunden haben (86400 Sekunden). Dieser Wert gilt daher implizit als Obergrenze für das Enddatum oder die Enddauer, das bzw. die für die Lizenzzwischenspeicherung festgelegt ist, mit einem Maximalwert von 86400 Sekunden, auch wenn das Schema höhere Grenzen erzwingt.

   * **Recht abspielen** — Es muss mindestens eine Berechtigung angegeben werden. Wenn mehrere Rechte angegeben sind, verwendet der Client die erste Berechtigung, für die er alle Anforderungen erfüllt.

      * **Output Protection** — Steuert, ob die Ausgabe auf externe Rendering-Geräte geschützt werden soll.
      * **AIR- und SWF-Anwendungsbeschränkungen** — Optionale Zulassungsliste von SWF- und AIR-Anwendungen, die Inhalte abspielen können (d. h. nur die angegebenen Anwendungen sind zulässig). SWF-Anwendungen werden durch eine URL oder den Digest der SWF und die maximale Zeit für den Download und die Verifizierung des Digest identifiziert. Informationen zur Berechnung der SWF-Digest finden Sie im Abschnitt &quot;SWF Hash Calculator&quot;. AIR- und iOS-Anwendungen werden durch eine Herausgeber-ID und eine optionale Anwendungs-ID, eine minimale Version und eine maximale Version identifiziert. Wenn keine Anwendungsbeschränkungen angegeben sind, kann jede SWF- oder AIR-Anwendung den Inhalt abspielen.
      * **DRM- und Laufzeitmodulbeschränkungen** — Gibt die Mindestsicherheitsstufe an, die für das DRM/Runtime-Modul erforderlich ist. Enthält optional eine Blockierungsliste von Versionen, die den Inhalt nicht abspielen dürfen. Modulversionen werden anhand von Attributen wie dem Betriebssystem und/oder einer Versionsnummer identifiziert. DRM-Modulbeschränkungen und Laufzeitmodulbeschränkungen unterstützen jetzt die folgenden zusätzlichen Attribute:

         * `oemVendor`
         * `model`
         * `screenType`

        Die folgenden Attribute sind jetzt optional:

         * `osVersion`
         * `version`

      * **Anforderungen an die Gerätefunktionen** — Gibt optional die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind.
      * **Anforderungen an die Jaille-Erkennung** - Gibt optional an, dass die Wiedergabe für Geräte, auf denen eine Unterbrechung erkannt wird, nicht zulässig ist.

Weitere Informationen finden Sie in den Kommentaren in der Beispielkonfigurationsdatei für Mandanten .
