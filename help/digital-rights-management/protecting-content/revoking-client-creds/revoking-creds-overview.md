---
title: Übersicht
description: Übersicht
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Übersicht{#overview}

Möglicherweise müssen Sie die Anmeldeinformationen eines Kunden sperren oder überprüfen, ob ein bestimmter Satz von Anmeldeinformationen unter bestimmten Bedingungen bereits gesperrt wurde. Berechtigungen können widerrufen werden, wenn sie beeinträchtigt werden. Wenn diese Probleme auftreten, werden Lizenzen nicht mehr an kompromittierte Kunden vergeben.

Adobe unterhält Zertifikatsperrlisten (Certificate Revocation Listen, CRLs) zum Sperren von angegriffenen Clients. Diese Zertifikatsperrlisten werden automatisch vom SDK erzwungen. Lizenzserver können Clients weiter einschränken, indem sie bestimmte Computerberechtigungen oder bestimmte Versionen von DRM- und Laufzeitberechtigungen deaktivieren. Ein `RevocationList` kann erstellt und an das SDK übergeben werden, um die Anmeldeinformationen des Computers zu sperren. Bestimmte DRM-/Laufzeitversionen können entweder auf DRM-Richtlinienebene widerrufen werden, indem Modulbeschränkungen im play-Recht oder global festgelegt werden, indem Modulbeschränkungen im `HandlerConfiguration` festgelegt werden.

Die Diskussion konzentriert sich auf das Widerrufen von Client-Anmeldeinformationen.
