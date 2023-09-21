---
title: Remote- und lokale iOS-Schlüsselbereitstellung
description: Remote- und lokale iOS-Schlüsselbereitstellung
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Remote- und lokale iOS-Schlüsselbereitstellung {#remote-and-local-ios-key-delivery}

Adobe Primetime unterstützt die folgenden Optionen für die Schlüsselbereitstellung an iOS-Clients:

* **Remote** - Führt gemäß der HTTP Live Streaming (HLS)-Spezifikation aus. Das M3U8-Manifest gibt einen HTTPS-Pfad an, der einen AES-Schlüssel enthält, der zum Entschlüsseln der folgenden verschlüsselten Segmente im Stream verwendet werden soll. Wenn Sie `Remote` in der Primetime-DRM-Richtlinie muss das Client-Gerät eine Verbindung zu einem Remote-HTTPS-Server herstellen, um einen AES-Schlüssel zu erhalten.

* **Lokal** - Wenn Sie `Local` im Primetime-DRM anstatt für den AES-Schlüssel eine Verbindung zum Internet/Netzwerk herzustellen, wird ein lokaler HTTPS-Server in die iOS-Anwendung eingebettet, der dann alle AES-Schlüsselanforderungen verwaltet. Der eingebettete HTTPS-Server wird automatisch in der P-Anwendung eingerichtet und konfiguriert. Der Anwendungsentwickler benötigt keine Intervention.

Die Bereitstellung von Remote-Schlüsseln wird über die Primetime-DRM-Richtlinie aktiviert, die zum Verpacken von Inhalten verwendet wird. Wenn Sie diese Einstellung ändern möchten, müssen Sie den Inhalt neu verpacken. Wenn Sie die Bereitstellung von Remote-Schlüsseln aktivieren, müssen Sie einen Primetime-DRM-Schlüsselserver bereitstellen, der wichtige Anforderungen von iOS-Clients verwalten kann. Es gibt jedoch keine Änderung am Workflow für Clients auf anderen Plattformen.

>[!NOTE]
>
>Die Auswahl der wichtigsten Sendungen betrifft nur iOS-Clients. Alle anderen Geräte, die HLS-Inhalte verwenden, wie Android und Primetime auf dem Desktop (Flash Player), verwenden immer `Local` Schlüsselbereitstellung, auch wenn `Remote` wurde angegeben.
