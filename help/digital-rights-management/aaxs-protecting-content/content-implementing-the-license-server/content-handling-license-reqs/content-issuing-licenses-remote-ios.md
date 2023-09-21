---
title: Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich)
description: Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Erteilung von Lizenzen für die Bereitstellung von Remote-Schlüsseln an iOS-Clients (Adobe Primetime erforderlich){#issuing-licenses-for-remote-key-delivery-to-ios-clients-requires-adobe-primetime}

Um Lizenzen für Inhalte zu erteilen, für die Remote Key-Bereitstellung für iOS-Geräte erforderlich ist, muss das Lizenzserver-Zertifikat des Schlüsselservers in `HandlerConfiguration.setKeyServerCertificate()`.
