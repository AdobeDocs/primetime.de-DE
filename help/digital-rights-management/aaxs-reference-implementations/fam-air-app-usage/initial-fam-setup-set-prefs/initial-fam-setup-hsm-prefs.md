---
seo-title: HSM-Voreinstellungen
title: HSM-Voreinstellungen
uuid: 1b97d582-d4b6-48cd-9c24-2d13493571e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---


# HSM-Voreinstellungen {#hsm-preferences}

Die Voreinstellungen in dieser Registerkarte müssen nur angegeben werden, wenn auf der Registerkarte &quot;Packager&quot;das Kontrollkästchen **[!UICONTROL Enable HSM]** aktiviert ist. In der folgenden Tabelle werden die folgenden Voreinstellungen beschrieben:

| Voreinstellung | Beschreibung |
|---|---|
| Sun PKCS#11 Konfigurationsdateiname | Der vollständige Pfad zur Konfigurationsdatei des Sun PKCS#11-Anbieters. Einzelheiten zum Inhalt dieser Konfigurationsdatei finden Sie im Java PKCS#11-Referenzhandbuch auf der Sun-Website. |
| Partitionskennwort | Das in der PKCS#11-Konfigurationsdatei angegebene Kennwort für die HSM-Partition. |
| Lizenzserver-Zertifikatalias | Alias für das von der Adobe ausgestellte Lizenzserverzertifikat, das auf dem HSM gespeichert ist. Dieses Zertifikat wird zum Verschlüsseln des CEK während der Verpackung verwendet. Geben Sie dies anstelle von *Lizenzserverzertifikat* auf der Registerkarte &quot;Packager&quot;an. |
| Lizenzserver-Transportzertifikatalias | Alias für auf HSM gespeicherte, von der Adobe ausgestellte Servertransportzertifikate. Dieses Zertifikat dient zum Schützen der Kommunikation zwischen dem Client und dem Lizenzserver. Geben Sie dies anstelle von *License Server Transport Certificate* auf der Registerkarte Packager an. |
| Alias für Packager-Berechtigungen | Alias für von der Adobe ausgestellte Paketberechtigung (Zertifikat und privater Schlüssel), die auf dem HSM gespeichert ist. Dadurch werden die Metadaten beim Verpacken signiert. Geben Sie dies anstelle von *Packager Credential* auf der Registerkarte &quot;Packager&quot;an. |
| Berechtigungsalias für Lizenzserver | Alias für von der Adobe ausgestellte Lizenzserver-Berechtigungen (Zertifikat und privater Schlüssel), die auf dem HSM gespeichert sind. Mit dieser Berechtigung werden Listen zur Richtlinienaktualisierung signiert. Geben Sie dies anstelle von *Lizenzserverberechtigung* auf der Registerkarte Liste für Richtlinienaktualisierung an. (Dieser Alias ist wahrscheinlich mit *Lizenzserver-Zertifikatalias* identisch.) |

