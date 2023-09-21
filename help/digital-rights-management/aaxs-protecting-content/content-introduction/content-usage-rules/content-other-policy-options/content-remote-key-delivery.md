---
title: Remote- und lokale iOS-Schlüsselbereitstellung
description: Remote- und lokale iOS-Schlüsselbereitstellung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Remote- und lokale iOS-Schlüsselbereitstellung{#remote-and-local-ios-key-delivery}

Adobe Primetime unterstützt zwei Optionen für die Schlüsselbereitstellung an iOS-Clients:

* Remote - Wie in der HLS-Spezifikation angegeben, gibt das M3U8-Manifest einen HTTPS-Pfad an, der einen AES-Schlüssel enthält, der zum Entschlüsseln der folgenden verschlüsselten Segmente im Stream verwendet werden soll. Wenn &quot;Remote&quot;angegeben ist, kontaktiert das Client-Gerät einen Remote-HTTPS-Server, um den AES-Schlüssel abzurufen.
* Lokal - Wenn &quot;Lokal&quot;angegeben ist, wird, anstatt über das Internet/Netzwerk für den AES-Schlüssel zu gelangen, ein lokaler HTTPS-Server in die iOS-Anwendung eingebettet, der alle AES-Schlüsselanforderungen verarbeitet. Der eingebettete HTTPS-Server wird automatisch in der Primetime-Anwendung eingerichtet und konfiguriert. Der Anwendungsentwickler benötigt keine Intervention.

Die Bereitstellung von Remote-Schlüsseln wird über die Richtlinie aktiviert, die zum Verpacken von Inhalten verwendet wird (eine Änderung dieser Einstellung erfordert eine Neuverpackung von Inhalten). Wenn die Bereitstellung von Remote-Schlüsseln aktiviert ist, muss ein Adobe Access Key Server bereitgestellt werden, um wichtige Anforderungen von iOS-Clients zu verarbeiten. Der Workflow für Clients auf anderen Plattformen wird jedoch nicht geändert.

>[!NOTE]
>
>Die Auswahl der wichtigsten Sendungen betrifft nur iOS-Clients. Alle anderen Geräte, die HLS-Inhalte verwenden, verwenden immer die &quot;Lokale&quot; Schlüsselbereitstellung, auch wenn &quot;Remote&quot; angegeben wurde.

Weitere Informationen finden Sie unter *Verwenden des Adobe Access Key Servers*.
