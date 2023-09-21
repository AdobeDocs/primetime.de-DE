---
title: HSM-Voreinstellungen
description: HSM-Voreinstellungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# HSM-Voreinstellungen {#hsm-preferences}

Die Voreinstellungen in dieser Registerkarte müssen nur angegeben werden, wenn die Variable **[!UICONTROL Enable HSM]** auf der Registerkarte Packager aktiviert ist. In der folgenden Tabelle werden diese Voreinstellungen beschrieben:

| Präferenz | Beschreibung |
|---|---|
| Sun PKCS#11 Konfigurationsdateiname | Der vollständige Pfad zur Konfigurationsdatei des Sun PKCS#11-Anbieters. Weitere Informationen zum Inhalt dieser Konfigurationsdatei finden Sie im Java PKCS#11 Reference Guide auf der Sun-Website. |
| Partitionenkennwort | Das Kennwort für die in der Konfigurationsdatei PKCS#11 angegebene HSM-Partition. |
| Lizenzserver-Zertifikatalias | Alias für das auf HSM gespeicherte Zertifikat des Adobe-erteilten Lizenzservers. Dieses Zertifikat wird zum Verschlüsseln des CEK während der Verpackung verwendet. Geben Sie anstelle von *Lizenzserver-Zertifikat* auf der Registerkarte &quot;Packager&quot;. |
| Lizenzserver-Transport-Zertifikatalias | Alias für auf HSM gespeicherte, von Adobe ausgestellte Server-Transportzertifikate. Dieses Zertifikat dient zur Sicherung der Kommunikation zwischen dem Client und dem Lizenzserver. Geben Sie anstelle von *Lizenzserver-Transportzertifikat* auf der Registerkarte &quot;Packager&quot;. |
| Package Credential Alias | Alias für Adobe-ausgestellte Paketberechtigungen (Zertifikat und privater Schlüssel), die auf HSM gespeichert sind. Damit werden die Metadaten während der Verpackung signiert. Geben Sie anstelle von *Packager Credential* auf der Registerkarte &quot;Packager&quot;. |
| Berechtigungsalias für Lizenzserver | Alias für auf HSM gespeicherte Adobe-erteilte Lizenzserverberechtigungen (Zertifikat und privater Schlüssel). Diese Berechtigung wird zum Signieren von Listen für Richtlinienaktualisierungen verwendet. Geben Sie anstelle von *Lizenzserver-Berechtigungen* auf der Registerkarte Liste der Richtlinienaktualisierungen . (Dieser Alias entspricht wahrscheinlich dem *Lizenzserver-Zertifikatalias*. |
