---
title: Remote- und lokaler iOS-Key-Versand
description: Remote- und lokaler iOS-Key-Versand
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Remote- und lokaler iOS-Key-Versand {#remote-and-local-ios-key-delivery}

Adobe Primetime unterstützt die folgenden Optionen für wichtigen Versand von iOS-Clients:

* **Remote**  - Führt die in der Spezifikation für HTTP Live Streaming (HLS) angegebenen Vorgänge aus; Das M3U8-Manifest gibt einen HTTPS-Pfad an, der einen AES-Schlüssel enthält, der zum Entschlüsseln der folgenden verschlüsselten Segmente im Stream verwendet werden sollte. Wenn Sie in der Primetime-DRM-Richtlinie `Remote` angeben, muss das Client-Gerät eine Verbindung zu einem Remote-HTTPS-Server herstellen, um einen AES-Schlüssel abrufen zu können.

* **Lokal** : Wenn Sie  `Local` im Primetime-DRM angeben, anstatt für den AES-Schlüssel eine Verbindung zum Internet/Netzwerk herzustellen, wird ein lokaler HTTPS-Server in die iOS-Anwendung eingebettet, der dann alle AES-Schlüsselanforderungen verwaltet. Der eingebettete HTTPS-Server wird automatisch in der P-Anwendung eingerichtet und konfiguriert. Der Anwendungsentwickler benötigt keine Intervention.

Der Remote-Key-Versand wird über die Primetime-DRM-Richtlinie aktiviert, die zum Verpacken von Inhalten verwendet wird. Wenn Sie diese Einstellung ändern möchten, müssen Sie den Inhalt neu verpacken. Wenn Sie Remote-Key-Versand aktivieren, müssen Sie einen Primetime-DRM-Key-Server bereitstellen, der wichtige Anfragen von iOS-Clients verwalten kann. Der Arbeitsablauf für Clients auf anderen Plattformen wird jedoch nicht geändert.

>[!NOTE]
>
>Die Auswahl der wichtigen Versand betrifft nur iOS-Clients. Alle anderen Geräte, die HLS-Inhalte verwenden, wie Android und Primetime auf dem Desktop (Flash Player), verwenden immer den Versand `Local`, selbst wenn `Remote` angegeben wurde.

