---
title: Asymmetrische Schlüsselverschlüsselung
description: Asymmetrische Schlüsselverschlüsselung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Asymmetrische Schlüsselverschlüsselung{#asymmetric-key-encryption}

Die Verschlüsselung des asymmetrischen Schlüssels (auch als Verschlüsselung des öffentlichen Schlüssels bezeichnet) verwendet Schlüsselpaare. Ein Schlüssel wird für die Verschlüsselung verwendet, der andere für die Entschlüsselung. Der Entschlüsselungsschlüssel wird geheim gehalten und als *privater Schlüssel*. Der Verschlüsselungsschlüssel, auch als *öffentlicher Schlüssel*, wird allen zur Verschlüsselung von Inhalten berechtigten zur Verfügung gestellt. Jeder, der Zugriff auf den öffentlichen Schlüssel hat, kann Inhalte verschlüsseln, aber nur jemand mit Zugriff auf den privaten Schlüssel kann den Inhalt entschlüsseln. Der private Schlüssel kann nicht aus dem öffentlichen Schlüssel rekonstruiert werden.

Beim Verpacken von Inhalten wird der öffentliche Schlüssel des Lizenzservers verwendet, um den Inhalt-Verschlüsselungsschlüssel (CEK) in den DRM-Metadaten zu verschlüsseln. Sie müssen sicherstellen, dass nur der Lizenzserver Zugriff auf den privaten Schlüssel des Lizenzservers hat. Wenn jemand anderes über den Schlüssel verfügt, kann er den Inhalt entschlüsseln und anzeigen.

***Vorsicht:**Stellen Sie sicher, dass Sie das Zertifikat des Lizenzservers (mit dem öffentlichen Schlüssel) von einer vertrauenswürdigen Quelle erhalten, damit Sie sicher sein können, dass es der Schlüssel des Lizenzservers und nicht ein öffentlicher Schlüssel von Schurken ist. Wenn ein Angreifer seinen öffentlichen Schlüssel durch den Schlüssel des Lizenzservers ersetzen würde, könnte er Ihren Inhalt entschlüsseln.*

Weitere Informationen zum Verpackungsinhalt finden Sie unter *Verwenden des Adobe Access SDK zum Schutz von Inhalten*.
