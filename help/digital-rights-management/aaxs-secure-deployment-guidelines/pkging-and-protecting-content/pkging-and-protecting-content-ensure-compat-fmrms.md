---
seo-title: Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen
title: Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen
uuid: 0160ca02-ebe6-4090-bf32-1d1a46088844
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Kompatibilität mit Flash Media Rights Management Server 1.x{#ensure-compatibility-with-flash-media-rights-management-server-x} sicherstellen

Flash Media Rights Management Server 1.x und Adobe Access verwenden unterschiedliche Metadaten zum Verpacken von Inhalten und Anfordern von Lizenzen. Damit Adobe Access den FMRMS-Inhalt der Version 1.x verwenden kann, müssen die Metadaten konvertiert werden.

Das Adobe Access SDK unterstützt zwei Optionen zum Konvertieren von Metadaten:

* Offline (empfohlen)

   Generieren Sie die Metadaten für den Zugriff auf Adoben in einem Offlineprozess und speichern Sie sie zur Verwendung, wenn ein Client sie anfordert. Adobe empfiehlt diese Option. Wenn Metadaten offline generiert werden, benötigt der Lizenzserver keinen Zugriff auf die 1.x-CEKs oder die Paketberechtigung. Darüber hinaus ist die Konvertierung von Offline-Angeboten leistungsfähiger, da der Lizenzserver die Metadaten nicht in Echtzeit generieren muss.

* On-Demand

   Generieren Sie die Adobe Access-Metadaten auf Anforderung, wenn ein Client sie anfordert. Wenn ein Adobe Access-Client Inhalte der Version 1.x herunterlädt, werden die DRM-Metadaten (auch DRM-Header genannt) an das Adobe Access SDK gesendet. Das SDK konvertiert die DRM-Metadaten in das aktuelle Format. Das SDK verschlüsselt und bettet den Inhaltsverschlüsselungsschlüssel (CEK) in die Metadaten ein und sendet den Inhalt zurück an den Adobe Access Client. (Die Metadaten von Adobe Access 1.x enthalten nicht den CEK.)

   Für die Konvertierung der Metadaten ist für den Zugriff auf Adoben der Zugriff auf die Inhaltsverschlüsselungsschlüssel der Adobe Access 1.x erforderlich. Wenn Sie von Flash Media Rights Management Server 1.x migrieren, können Sie die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank speichern oder eine benutzerdefinierte Lösung implementieren, um die Schlüssel zur Inhaltsverschlüsselung an einer anderen Stelle sicher zu speichern. Wenn Sie sich dafür entscheiden, die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank zu speichern, befolgen Sie die Empfehlungen unter &quot;Schutz des Zugriffs auf vertrauliche Inhalte in der Datenbank&quot;in *Härtung und Sicherheit für LiveCycle ES*.

Weitere Informationen zum Sicherstellen der Kompatibilität mit Inhalten, die mit Flash Media Rights Management Server 1.x verpackt wurden, finden Sie in der *API-Referenz für den Zugriff auf Adoben*.
