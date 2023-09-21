---
description: Flash Media Rights Management Server 1.x und Adobe Primetime DRM verwenden unterschiedliche Metadaten, um Inhalte zu verpacken und Lizenzen anzufordern. Damit Primetime DRM Inhalte der FMRMS-Version 1.x verwendet, müssen die Metadaten konvertiert werden.
title: Gewährleistung der Kompatibilität mit Flash Media Rights Management Server 1.x
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# Gewährleistung der Kompatibilität mit Flash Media Rights Management Server 1.x {#ensuring-compatibility-with-flash-media-rights-management-server-x}

Flash Media Rights Management Server 1.x und Adobe Primetime DRM verwenden unterschiedliche Metadaten, um Inhalte zu verpacken und Lizenzen anzufordern. Damit Primetime DRM Inhalte der FMRMS-Version 1.x verwendet, müssen die Metadaten konvertiert werden.

Das Primetime DRM SDK unterstützt die folgenden Optionen zur Konvertierung von Metadaten:

* Offline (empfohlen)

  Generieren Sie die Primetime DRM-Metadaten in einem Offline-Prozess und speichern Sie die Metadaten, bis sie von einem Client angefordert werden. Wenn Metadaten offline generiert werden, benötigt der Lizenzserver keinen Zugriff auf die 1.x-CEKs oder die Paketberechtigung. Die Offline-Konvertierung bietet eine bessere Leistung, da der Lizenzserver die Metadaten nicht in Echtzeit generieren muss.
* On-Demand

  Die Primetime-DRM-Metadaten werden generiert, wenn die Metadaten von einem Client angefordert werden. Wenn ein Primetime-DRM-Client Inhalte der Version 1.x herunterlädt, sendet der Client die DRM-Metadaten an das Primetime-DRM-SDK. Das SDK konvertiert die DRM-Metadaten in das aktuelle Format, verschlüsselt und bettet den Inhaltsverschlüsselungsschlüssel (CECK) in die Metadaten ein und sendet den Inhalt zurück an den Primetime DRM-Client.

  >[!NOTE]
  >
  >Die Primetime DRM 1.x-Metadaten enthalten nicht den CEK.

  Um die Metadaten zu konvertieren, benötigt Primetime DRM Zugriff auf die Primetime DRM 1.x-Inhaltsverschlüsselungsschlüssel. Wenn Sie von Flash Media Rights Management Server 1.x migrieren, können Sie die Schlüssel zur Inhaltsverschlüsselung weiterhin in der LiveCycle ES-Datenbank speichern oder eine benutzerdefinierte Lösung implementieren, um die Schlüssel zur Inhaltsverschlüsselung sicher an einem anderen Speicherort zu speichern. Wenn Sie die Schlüssel zur Inhaltsverschlüsselung in der LiveCycle ES-Datenbank speichern möchten, befolgen Sie die Empfehlungen unter *Schutz des Zugriffs auf vertrauliche Inhalte in der Datenbank* in **Härtung und Sicherheit für LiveCycle® ES2**.

Weitere Informationen zur Sicherstellung der Kompatibilität mit Inhalten, die mit Flash Media Rights Management Server 1.x verpackt wurden, finden Sie in den DRM-APIs von Adobe Primetime unter [Adobe Primetime API-Referenzen](https://help.adobe.com/en_US/primetime/api/index.html#api-Adobe_Primetime_API_References).
