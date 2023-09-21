---
title: Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich)
description: Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '63'
ht-degree: 0%

---

# Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich){#issuing-licenses-for-remote-key-delivery-to-ios-clients-requires-adobe-primetime}

Wenn Sie Lizenzen für Inhalte erteilen möchten, für die die Bereitstellung von Remote-Schlüssel für iOS-Geräte erforderlich ist, müssen Sie das Lizenzserverzertifikat des Schlüsselservers in `HandlerConfiguration.setKeyServerCertificate()`.
