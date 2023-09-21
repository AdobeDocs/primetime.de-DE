---
title: Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen
description: Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen{#ensure-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x und Adobe Access verwenden unterschiedliche Metadaten für das Verpacken von Inhalten und das Anfordern von Lizenzen. Damit Adobe Access FMRMS Version 1.x verwenden kann, müssen die Metadaten konvertiert werden.

Das Adobe Access SDK unterstützt zwei Optionen zum Konvertieren von Metadaten:

* Offline (empfohlen)

  Generieren Sie die Adobe Access-Metadaten in einem Offline-Prozess und speichern Sie sie für die Verwendung, wenn ein Client sie anfordert. Adobe empfiehlt diese Option. Wenn Metadaten offline generiert werden, benötigt der Lizenzserver keinen Zugriff auf die 1.x-CEKs oder die Paketberechtigung. Darüber hinaus bietet die Offline-Konvertierung eine bessere Leistung, da der Lizenzserver die Metadaten nicht in Echtzeit generieren muss.

* On-Demand

  Generieren Sie die Adobe Access-Metadaten bei Bedarf, wenn ein Client sie anfordert. Wenn ein Adobe Access-Client Inhalte der Version 1.x herunterlädt, werden die DRM-Metadaten (auch DRM-Header genannt) an das Adobe Access SDK gesendet. Das SDK konvertiert die DRM-Metadaten in das aktuelle Format. Das SDK verschlüsselt und bettet den Inhaltsverschlüsselungsschlüssel (CECK) in die Metadaten ein und sendet den Inhalt zurück an den Adobe Access-Client. (Die Adobe Access 1.x-Metadaten enthalten den CEK nicht.)

  Um die Metadaten zu konvertieren, erfordert Adobe Access Zugriff auf die Adobe Access 1.x-Inhaltsverschlüsselungsschlüssel. Wenn Sie von Flash Media Rights Management Server 1.x migrieren, können Sie die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank speichern oder eine benutzerdefinierte Lösung implementieren, um die Schlüssel zur Inhaltsverschlüsselung an einer anderen Stelle sicher zu speichern. Wenn Sie sich dafür entscheiden, die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank zu speichern, befolgen Sie die unter &quot;Schutz des Datenbankzugriffs auf vertrauliche Inhalte&quot;in *Härtung und Sicherheit für LiveCycle ES*.

Weitere Informationen zur Sicherstellung der Kompatibilität mit Inhalten, die mit Flash Media Rights Management Server 1.x gepackt werden, finden Sie in der *Adobe Access API-Referenz*.
