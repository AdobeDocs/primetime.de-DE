---
seo-title: Mandantenkonfigurationsdatei
title: Mandantenkonfigurationsdatei
uuid: 6e5c82c9-b8f5-4fca-8325-a884b2c779f7
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---


# Mandantenkonfigurationsdatei {#tenant-configuration-file}

Die Konfigurationsdatei &quot;flashaccess-tenant.xml&quot;enthält Einstellungen, die für einen bestimmten Mandanten des Lizenzservers gelten. Jeder Mandant hat seine eigene Instanz dieser Konfigurationsdatei unter *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*. Eine Beispielkonfigurationsdatei für Mandanten finden Sie im Ordner [!DNL configs/flashaccessserver/tenants/sampletenant].

Sie können alle Dateipfade in der Mietkonfigurationsdatei als absolute Pfade oder Pfade relativ zum Konfigurationsverzeichnis des Mandanten (*LicenseServer.ConfigRoot* [!DNL /flashaccessserver/tenants/]*tenantname*) angeben.

Die Mandant-Konfigurationsdatei enthält:

* **Verkehrsberechtigung** — Gibt eine oder mehrere von der Adobe ausgestellte Transportberechtigungen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer .pfx-Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Berechtigungen angegeben werden, entweder als Dateipfade oder als Schlüssel-Aliase oder beides. Weitere Informationen dazu, wann zusätzliche Anmeldeinformationen benötigt werden, finden Sie unter &quot;[Verarbeiten von Zertifikataktualisierungen](../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-cert-updates.md)&quot;in *Verwenden des Adobe Access SDK für den Inhaltsschutz*.
* **Lizenzserver-Berechtigung** — Gibt eine oder mehrere von der Adobe ausgestellte Lizenzserver-Anmeldeinformationen (Zertifikat und privater Schlüssel) an. Kann als Pfad zu einer .pfx-Datei und einem Kennwort oder als Alias für eine auf einem HSM gespeicherte Berechtigung angegeben werden. Hier können mehrere solcher Berechtigungen angegeben werden, entweder als Dateipfade oder als Schlüssel-Aliase oder beides. Weitere Informationen dazu, wann weitere Anmeldeinformationen benötigt werden, finden Sie unter Umgang mit Zertifikataktualisierungen in *Verwenden des Adobe Access SDK für den Inhaltsschutz *.
* **Key Server Certificates** — Optional. Gibt das von der Adobe ausgestellte Lizenzserverzertifikat des Schlüsselservers an. Kann als Pfad zu einer .cer-Datei oder als Alias zu einem auf einem HSM gespeicherten Zertifikat angegeben werden. Diese Option muss angegeben werden, um Lizenzen für Inhalte auszustellen, die mit einer Richtlinie verpackt wurden, die Remote-Versand für iOS-Geräte erfordert.
* **Benutzerdefinierte Autorisierer** — Optional. Gibt benutzerdefinierte Autorisierungsklassen an, die für jede Lizenzanforderung aufgerufen werden sollen. Wenn mehrere Autorisierer angegeben sind, werden sie in der aufgeführten Reihenfolge aufgerufen. Weitere Informationen finden Sie unter &quot;[Benutzerdefinierte Autorisierungs-Erweiterungen](../../aaxs-protected-streaming/custom-authorization-extensions.md)&quot;.
* **Liste der zugelassenen Packstellen** — Optional. Gibt Zertifikate an, die Entitäten identifizieren, die zum Verpacken von Inhalten für diesen Lizenzserver berechtigt sind. Wenn keine Packager-Zertifikate angegeben sind, gibt der Server Lizenzen für Inhalte aus, die von einem Packager verpackt wurden.
* **Mindestunterstützte Clientversion**  (siehe  *Verwenden des Adobe Access SDK zum Schützen von Inhalten*).
* **Nutzungsregeln**

   * **Lizenzzwischenspeicherung** — Optional. Gibt an, wie lange die Lizenz auf dem Client gespeichert werden kann. Standardmäßig ist die Lizenzzwischenspeicherung deaktiviert. Um die Lizenzzwischenspeicherung für einen begrenzten Zeitraum zu aktivieren, legen Sie das Enddatum oder die Anzahl der Sekunden fest, in denen die Lizenz gespeichert werden soll (beginnend mit dem Zeitpunkt der Lizenzerteilung). Wenn Sie die Anzahl der Sekunden auf 0 einstellen, wird die Lizenzzwischenspeicherung deaktiviert.

      Beachten Sie, dass alle vom Server für das geschützte Streaming ausgegebenen Lizenzen eine Gültigkeitsdauer von 24 Stunden haben (86400 Sekunden). Dieser Wert gilt daher implizit als Obergrenze für das Enddatum oder die Dauer, die für die Lizenzzwischenspeicherung festgelegt wird, mit einem Höchstwert von 86400 Sekunden, auch wenn das Schema höhere Begrenzungen erzwingt.

   * **Recht**  abspielen— Es muss mindestens ein Recht angegeben werden. Wenn mehrere Rechte angegeben sind, verwendet der Kunde das erste Recht, für das er alle Anforderungen erfüllt.

      * **Output Protection** — Steuert, ob die Ausgabe auf externen Wiedergabegeräten geschützt werden soll.
      * **AIR- und SWF-Anwendungsbeschränkungen** — Optionale Zulassungsliste von SWF- und AIR-Anwendungen, die Inhalte wiedergeben können (d. h., nur die angegebenen Anwendungen sind zulässig). SWF-Anwendungen werden durch eine URL oder den Digest der SWF und die maximale Zeit für den Download und die Überprüfung der Zusammenfassung identifiziert. Informationen zur Berechnung der SWF-Zusammenfassung finden Sie im Abschnitt &quot;SWF-Hash-Rechner&quot;. AIR- und iOS-Anwendungen werden durch eine Herausgeber-ID und eine optionale Anwendungs-ID, Mindest- und Höchstversion gekennzeichnet. Wenn keine Anwendungseinschränkungen angegeben sind, kann der Inhalt von jeder SWF- oder AIR-Anwendung wiedergegeben werden.
      * **DRM- und Laufzeitmodul-Einschränkungen** — Gibt die Mindestsicherheitsstufe an, die für das DRM/Runtime-Modul erforderlich ist. Enthält optional eine Blockierungsliste von Versionen, für die die Wiedergabe des Inhalts nicht zulässig ist. Modulversionen werden durch Attribute wie Betriebssystem und/oder Versionsnummer identifiziert. Einschränkungen für DRM-Module und Einschränkungen für Laufzeitmodule unterstützen jetzt die folgenden zusätzlichen Attribute:

         * `oemVendor`
         * `model`
         * `screenType`

         Die folgenden Attribute sind jetzt optional:

         * `osVersion`
         * `version`
      * **Anforderungen an die Gerätefähigkeit** — Gibt optional die Hardwarefunktionen an, die für den Zugriff auf Inhalte erforderlich sind.
      * **Anforderungen an die**  Erkennung von Jägerspaltungen— Gibt optional an, dass die Wiedergabe auf Geräten, auf denen ein Jailbreak erkannt wird, nicht zulässig ist.



Weitere Informationen finden Sie in den Kommentaren in der Beispielkonfigurationsdatei des Mandanten.
