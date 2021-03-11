---
description: Flash Media Rights Management Server 1.x und Adobe Primetime DRM verwenden verschiedene Metadaten, um Inhalte zu verpacken und Lizenzen anzufordern. Damit Primetime DRM den Inhalt von FMRMS Version 1.x verwenden kann, müssen die Metadaten konvertiert werden.
title: Kompatibilität mit Flash Media Rights Management Server 1.x sicherstellen
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# Gewährleistung der Kompatibilität mit Flash Media Rights Management Server 1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x und Adobe Primetime DRM verwenden verschiedene Metadaten, um Inhalte zu verpacken und Lizenzen anzufordern. Damit Primetime DRM den Inhalt von FMRMS Version 1.x verwenden kann, müssen die Metadaten konvertiert werden.

Das Primetime-DRM-SDK unterstützt die folgenden Optionen zur Konvertierung von Metadaten:

* Offline (empfohlen)

   Generieren Sie die Primetime-DRM-Metadaten in einem Offlineprozess und speichern Sie die Metadaten, bis sie von einem Client angefordert werden. Wenn Metadaten offline generiert werden, benötigt der Lizenzserver keinen Zugriff auf die 1.x-CEKs oder die Paketberechtigung. Die Konvertierung von Offline-Angeboten ist leistungsfähiger, da der Lizenzserver die Metadaten nicht in Echtzeit generieren muss.
* On-Demand

   Die Primetime-DRM-Metadaten werden generiert, wenn die Metadaten von einem Client angefordert werden. Wenn ein Primetime-DRM-Client Inhalte der Version 1.x herunterlädt, sendet der Client die DRM-Metadaten an das Primetime-DRM-SDK. Das SDK konvertiert die DRM-Metadaten in das aktuelle Format, verschlüsselt und bettet den Inhaltsverschlüsselungsschlüssel (CEK) in die Metadaten ein und sendet den Inhalt zurück an den Primetime DRM-Client.

   >[!NOTE]
   >
   >Die Primetime DRM 1.x-Metadaten enthalten nicht den CEK.

   Um die Metadaten zu konvertieren, benötigt Primetime DRM Zugriff auf die Primetime DRM 1.x-Inhaltsverschlüsselungsschlüssel. Wenn Sie von Flash Media Rights Management Server 1.x migrieren, können Sie die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank speichern oder eine benutzerdefinierte Lösung implementieren, um die Schlüssel zur Inhaltsverschlüsselung sicher an einem anderen Speicherort zu speichern. Wenn Sie die Schlüssel zur Inhaltsverschlüsselung in der LiveCycle ES-Datenbank speichern möchten, befolgen Sie die Anweisungen unter *Schutz des Zugriffs auf vertrauliche Inhalte in der Datenbank* in **Härtung und Sicherheit für LiveCycle® ES2**.

Weitere Informationen zum Sicherstellen der Kompatibilität mit Inhalten, die mit Flash Media Rights Management Server 1.x verpackt wurden, finden Sie in den Adobe Primetime DRM-APIs unter [Adobe Primetime API References](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).
