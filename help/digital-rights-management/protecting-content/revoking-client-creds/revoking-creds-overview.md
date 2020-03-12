---
seo-title: Übersicht
title: Übersicht
uuid: c6f54867-d0a3-43fd-9493-6496f1b7831a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Übersicht{#overview}

Möglicherweise müssen Sie die Anmeldeinformationen eines Kunden sperren oder überprüfen, ob ein bestimmter Satz von Anmeldeinformationen unter bestimmten Bedingungen bereits gesperrt wurde. Berechtigungen können widerrufen werden, wenn sie beeinträchtigt werden. Wenn diese Probleme auftreten, werden Lizenzen nicht mehr an kompromittierte Kunden vergeben.

Adobe unterhält Zertifikatsperrlisten (Certificate Revocation Listen, CRLs) zum Sperren von angegriffenen Clients. Diese Zertifikatsperrlisten werden automatisch vom SDK erzwungen. Lizenzserver können Clients weiter einschränken, indem sie bestimmte Computerberechtigungen oder bestimmte Versionen von DRM- und Laufzeitberechtigungen deaktivieren. Es `RevocationList` kann ein SDK erstellt und an das SDK übergeben werden, um die Anmeldeinformationen des Computers zu sperren. Bestimmte DRM-/Laufzeitversionen können entweder auf DRM-Richtlinienebene widerrufen werden, indem Modulbeschränkungen im play-Recht oder global festgelegt werden, indem Modulbeschränkungen im `HandlerConfiguration`.

Die Diskussion konzentriert sich auf das Widerrufen von Client-Anmeldeinformationen.
