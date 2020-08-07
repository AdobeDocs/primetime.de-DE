---
seo-title: Remote- und lokaler iOS-Key-Versand
title: Remote- und lokaler iOS-Key-Versand
uuid: 90f672e7-9301-4e14-adca-db2a8f951a83
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---


# Remote- und lokaler iOS-Key-Versand {#remote-and-local-ios-key-delivery}

Adobe Primetime unterstützt die folgenden Optionen für wichtigen Versand von iOS-Clients:

* **Remote** - Führt die in der Spezifikation für HTTP Live Streaming (HLS) angegebenen Vorgänge aus; Das M3U8-Manifest gibt einen HTTPS-Pfad an, der einen AES-Schlüssel enthält, der zum Entschlüsseln der folgenden verschlüsselten Segmente im Stream verwendet werden sollte. Wenn Sie `Remote` in der Primetime-DRM-Richtlinie angeben, muss das Clientgerät eine Verbindung zu einem Remote-HTTPS-Server herstellen, um einen AES-Schlüssel abrufen zu können.

* **Lokal** : Wenn Sie für den AES-Schlüssel `Local` im Primetime-DRM angeben, anstatt eine Verbindung zum Internet/Netzwerk herzustellen, wird ein lokaler HTTPS-Server in die iOS-Anwendung eingebettet, der dann alle AES-Schlüsselanforderungen verwaltet. Der eingebettete HTTPS-Server wird automatisch in der P-Anwendung eingerichtet und konfiguriert. Der Anwendungsentwickler benötigt keine Intervention.

Der Remote-Key-Versand wird über die Primetime-DRM-Richtlinie aktiviert, die zum Verpacken von Inhalten verwendet wird. Wenn Sie diese Einstellung ändern möchten, müssen Sie den Inhalt neu verpacken. Wenn Sie Remote-Key-Versand aktivieren, müssen Sie einen Primetime-DRM-Key-Server bereitstellen, der wichtige Anfragen von iOS-Clients verwalten kann. Der Arbeitsablauf für Clients auf anderen Plattformen wird jedoch nicht geändert.

>[!NOTE]
>
>Die Auswahl der wichtigen Versand betrifft nur iOS-Clients. All other devices that use HLS content , such as Android and Primetime on Desktop (Flash Player), always use `Local` key delivery, even if `Remote` has been specified.

