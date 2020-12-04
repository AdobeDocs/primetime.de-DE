---
seo-title: Asymmetrische Schlüsselverschlüsselung
title: Asymmetrische Schlüsselverschlüsselung
uuid: 0aae25f1-a609-4c73-9aef-13f8ae63f6e1
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# Asymmetrische Schlüsselverschlüsselung{#asymmetric-key-encryption}

Die asymmetrische Schlüsselverschlüsselung (auch als Verschlüsselung öffentlicher Schlüssel bezeichnet) verwendet Schlüssel-Paare. Ein Schlüssel wird für die Verschlüsselung verwendet. die andere für die Entschlüsselung. Der Entschlüsselungsschlüssel wird geheim gehalten und als *privater Schlüssel* bezeichnet. Der Verschlüsselungsschlüssel, der als *öffentlicher Schlüssel* bezeichnet wird, steht allen Personen zur Verfügung, die zum Verschlüsseln von Inhalten berechtigt sind. Jeder mit Zugriff auf den öffentlichen Schlüssel kann Inhalte verschlüsseln, aber nur jemand mit Zugriff auf den privaten Schlüssel kann den Inhalt entschlüsseln. Der private Schlüssel kann nicht aus dem öffentlichen Schlüssel rekonstruiert werden.

Beim Verpacken von Inhalten wird der öffentliche Schlüssel des Lizenzservers verwendet, um den Inhaltsverschlüsselungsschlüssel (CEK) in den DRM-Metadaten zu verschlüsseln. Sie müssen sicherstellen, dass nur der Lizenzserver Zugriff auf den privaten Schlüssel des Lizenzservers hat. wenn jemand anderes den Schlüssel hat, kann er den Inhalt entschlüsseln und Ansicht.

***Vorsicht:**Stellen Sie sicher, dass Sie das Zertifikat des Lizenzservers (mit dem öffentlichen Schlüssel) von einer vertrauenswürdigen Quelle erhalten, damit Sie sicher sein können, dass es sich um den Schlüssel des Lizenzservers und nicht um einen öffentlichen Schurkenschlüssel handelt. Wenn ein Angreifer seinen öffentlichen Schlüssel durch den Lizenzserver-Schlüssel ersetzen sollte, könnte er Ihren Inhalt entschlüsseln.*

Weitere Informationen zum Verpacken von Inhalten finden Sie unter *Verwenden des Adobe Access SDK for Protection Content*.
