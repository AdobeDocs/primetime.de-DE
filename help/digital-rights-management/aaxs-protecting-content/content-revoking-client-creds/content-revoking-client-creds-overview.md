---
seo-title: Widerrufen von Clientberechtigungen
title: Widerrufen von Clientberechtigungen
uuid: 47f1ec1a-bd8f-4f8c-bee3-bfbf6d9902e7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Widerrufen von Clientberechtigungen{#revoking-client-credentials}

Unter bestimmten Bedingungen ist es erforderlich, die Anmeldeinformationen eines Kunden zu sperren oder zu prüfen, ob ein bestimmter Satz von Anmeldeinformationen bereits gesperrt wurde. Berechtigungen können widerrufen werden, wenn die Anmeldeinformationen beschädigt werden. In diesem Fall werden Lizenzen nicht mehr an kompromittierte Kunden vergeben.

Adobe unterhält Zertifikatsperrlisten (Certificate Revocation Listen, CRLs) zum Sperren von angegriffenen Clients. Diese Zertifikatsperrlisten werden automatisch vom SDK erzwungen. Lizenzserver können Clients weiter einschränken, indem sie bestimmte Computerberechtigungen oder bestimmte Versionen von DRM- und Laufzeitberechtigungen deaktivieren. Es `RevocationList` kann ein SDK erstellt und an das SDK übergeben werden, um die Anmeldeinformationen des Computers zu sperren. Bestimmte DRM-/Laufzeitversionen können entweder auf Richtlinienebene (durch Festlegen von Modulbeschränkungen im play right) oder global (durch Festlegen von Modulbeschränkungen im `HandlerConfiguration`) gesperrt werden.

Die Diskussion in diesem Kapitel konzentriert sich auf das Widerrufen von Client-Anmeldeinformationen.
