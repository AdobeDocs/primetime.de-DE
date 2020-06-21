---
description: Die Konfigurationsdatei "flashaccess-tenant.xml"enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten.
seo-description: Die Konfigurationsdatei "flashaccess-tenant.xml"enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten.
seo-title: Mandantenkonfigurationsdatei
title: Mandantenkonfigurationsdatei
uuid: bc9ee4a1-63b6-4362-9929-3e9fe8251075
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---


# Mandantenkonfigurationsdatei{#tenant-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-tenant.xml&quot;enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten.

Jeder Mandant unterstützt seine eigene Instanz dieser Konfigurationsdatei, die sich unter [!DNL &lt;LicenseServer.ConfigRoot>/flashAccessserver/tenants/ befindet<tenantname>]. Siehe [!DNL configs/flashaccessserver/tenants/sampletenant] Verzeichnis für eine Beispielkonfigurationsdatei für Mandanten.

Sie können alle Dateipfade in der Mandant-Konfigurationsdatei als absolute Pfade oder als Pfade angeben, die relativ zum Konfigurationsordner des Mandanten sind ( [!DNL &lt;LicenseServer.ConfigRoot>/flashAccessserver/tenants/<tenantname>]).

Die Mandant-Konfigurationsdatei enthält:

* *Verkehrsberechtigung* — Gibt eine oder mehrere von Adobe ausgestellte Transportberechtigungen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer [!DNL .pfx] Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Berechtigungen angegeben werden, entweder als Dateipfade oder als Schlüssel-Aliase oder beides.

   Weitere Informationen dazu, wann zusätzliche Anmeldeinformationen benötigt werden, finden Sie unter *Umgang mit Zertifikataktualisierungen* in *Verwenden des Adobe Primetime DRM SDK for Protection Content* .

* *Lizenzserver-Berechtigung* — Gibt eine oder mehrere Anmeldeinformationen des Lizenzservers (Zertifikat und privater Schlüssel) an, die von Adobe ausgestellt wurden. Sie können die Anmeldeinformationen des Lizenzservers als Pfad zu einer [!DNL .pfx] Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angeben. Hier können mehrere solcher Berechtigungen angegeben werden, entweder als Dateipfade oder als Schlüssel-Aliase oder beides.

   Weitere Informationen dazu, wann zusätzliche Anmeldeinformationen benötigt werden, finden Sie unter *Umgang mit Zertifikataktualisierungen* in *Verwenden des Adobe Primetime DRM SDK for Protection Content* .

* *Key Server Certificates* — Gibt optional das Lizenzserverzertifikat des Schlüsselservers an, das von Adobe ausgestellt wurde. Sie können das Lizenzserverzertifikat des Schlüsselservers als Pfad zu einer [!DNL .cer] Datei oder als Alias für ein Zertifikat angeben, das auf einem HSM gespeichert ist. Diese Option muss angegeben werden, um Lizenzen für Inhalte auszustellen, die mit einer DRM-Richtlinie verpackt sind, die Remote-Versand für iOS-Geräte erfordert.

* *Benutzerdefinierte Autorisierer* — Gibt optional benutzerdefinierte Autorisierungsklassen an, die für jede Lizenzanforderung aufgerufen werden sollen. Wenn mehrere Autorisierer angegeben sind, werden sie in der aufgeführten Reihenfolge aufgerufen.
* *Liste der zugelassenen Packstellen* — Gibt optional Zertifikate an, die Entitäten identifizieren, die zum Verpacken von Inhalten für diesen Lizenzserver berechtigt sind. Wenn keine Packager-Zertifikate angegeben sind, gibt der Server Lizenzen für Inhalte aus, die von einem Packager gepackt werden. Wenn der Server eine Lizenzanforderung von einem nicht autorisierten Packager erhält, wird die Anforderung verweigert.
* *Die Mindestversion* des unterstützten Clients finden Sie unter Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten.

* *Nutzungsregeln*

   * *Lizenzzwischenspeicherung* — Gibt optional an, wie lange die Lizenz auf dem Client gespeichert werden kann. Standardmäßig ist die Lizenzzwischenspeicherung deaktiviert. Wenn Sie die Lizenzzwischenspeicherung für einen begrenzten Zeitraum aktivieren möchten, müssen Sie das Enddatum oder die Anzahl der Sekunden festlegen, in denen die Lizenz gespeichert werden soll (beginnend mit dem Zeitpunkt der Lizenzerteilung). Wenn Sie die Anzahl der Sekunden auf 0 einstellen, wird die Lizenzzwischenspeicherung deaktiviert.

      >[!NOTE]
      >
      >Alle Lizenzen, die der Server für geschütztes Streaming erteilt hat, gelten für eine Gültigkeitsdauer von 24 Stunden (86400 Sekunden). Dieser Wert gilt implizit als Obergrenze, unabhängig davon, welches Enddatum oder welche Dauer für die Lizenzzwischenspeicherung festgelegt wurde, mit einem Maximalwert von 86400 Sekunden, auch wenn das Schema höhere Begrenzungen erzwingt.

   * *Recht* abspielen — Es muss mindestens ein Recht festgelegt werden. Wenn Sie mehrere Rechte angeben, verwendet der Client die erste Berechtigung, die alle Anforderungen erfüllt.

      * *Output Protection* — Steuert, ob die Ausgabe auf externen Wiedergabegeräten geschützt werden soll.
      * *AIR- und SWF-Anwendungsbeschränkungen* — Optionale zulassungsliste von SWF- und AIR-Anwendungen, die Inhalte wiedergeben können (z. B. sind nur die angegebenen Anwendungen zulässig). SWF-Anwendungen werden durch eine URL oder den Digest der SWF und die maximale Zeit für den Download und die Überprüfung der Zusammenfassung identifiziert.

         Informationen zur Berechnung der SWF-Zusammenfassung finden Sie unter *SWF-Hash-Rechner* .

         Eine Herausgeber-ID und eine optionale Anwendungs-ID, Mindest- und Höchstversion kennzeichnen AIR- und iOS-Anwendungen. Wenn Sie keine Anwendungseinschränkungen angeben, kann der Inhalt von jeder SWF- oder AIR-Anwendung wiedergegeben werden.

      * *DRM- und Laufzeitmodul-Einschränkungen* — Gibt die Mindestsicherheitsstufe an, die für das DRM/Runtime-Modul erforderlich ist. Enthält optional eine blockierungsliste von Versionen, für die die Wiedergabe des Inhalts nicht zulässig ist. Modulversionen werden durch Attribute wie Betriebssystem und/oder Versionsnummer identifiziert.

         Einschränkungen für DRM-Module und Einschränkungen für Laufzeitmodule unterstützen jetzt die folgenden zusätzlichen Attribute:

         * `oemVendor`
         * `model`
         * `screenType`
         Die folgenden Attribute sind jetzt optional:

         * `osVersion`
         * `version`
      * *Anforderungen* an die Gerätefähigkeit — Gibt optional die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind.
      * *Anforderungen* an die Erkennung von Järanlagen — Gibt optional an, dass die Wiedergabe auf Geräten, auf denen ein Jailbreak erkannt wird, nicht zulässig ist.



Weitere Informationen finden Sie in den Kommentaren in der Beispielkonfigurationsdatei des Mandanten.
