---
seo-title: HSM-Voreinstellungen
title: HSM-Voreinstellungen
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# HSM-Voreinstellungen {#hsm-preferences}

Die Voreinstellungen in dieser Registerkarte müssen nur angegeben werden, wenn das **[!UICONTROL Enable HSM]** Kontrollkästchen auf der Registerkarte &quot;Packager&quot;aktiviert ist. In der folgenden Tabelle werden die folgenden Voreinstellungen beschrieben:

| Voreinstellung | Beschreibung |
|---|---|
| Sun PKCS#11 Konfigurationsdateiname | Der vollständige Pfad zur Konfigurationsdatei des Sun PKCS#11-Anbieters. Einzelheiten zum Inhalt dieser Konfigurationsdatei finden Sie im Java PKCS#11-Referenzhandbuch auf der Sun-Website. |
| Partitionskennwort | Das in der PKCS#11-Konfigurationsdatei angegebene Kennwort für die HSM-Partition. |
| Lizenzserver-Zertifikatalias | Alias für von Adobe ausgegebenes Lizenzserverzertifikat, das auf HSM gespeichert ist. Dieses Zertifikat wird zum Verschlüsseln des CEK während der Verpackung verwendet. Geben Sie dies anstelle des *Lizenzserverzertifikats* auf der Registerkarte &quot;Packager&quot;an. |
| Lizenzserver-Transportzertifikatalias | Alias für von Adobe ausgegebenes Servertransportzertifikat, das auf HSM gespeichert ist. Dieses Zertifikat dient zum Schützen der Kommunikation zwischen dem Client und dem Lizenzserver. Geben Sie dies anstelle des *Lizenzserver-Transportzertifikats* auf der Registerkarte &quot;Packager&quot;an. |
| Alias für Packager-Berechtigungen | Alias für von Adobe ausgestellte Paketberechtigung (Zertifikat und privater Schlüssel), die auf HSM gespeichert ist. Dadurch werden die Metadaten beim Verpacken signiert. Geben Sie dies anstelle von *Packager Credential* auf der Registerkarte Packager an. |
| Berechtigungsalias für Lizenzserver | Alias für von Adobe ausgestellte Lizenzserver-Berechtigungen (Zertifikat und privater Schlüssel), die auf HSM gespeichert sind. Mit dieser Berechtigung werden Listen zur Richtlinienaktualisierung signiert. Geben Sie dies anstelle der *Lizenzserverberechtigung* auf der Registerkarte Liste für Richtlinienaktualisierung an. (Dieser Alias entspricht wahrscheinlich dem Alias für das *Lizenzserver-Zertifikat*.) |

