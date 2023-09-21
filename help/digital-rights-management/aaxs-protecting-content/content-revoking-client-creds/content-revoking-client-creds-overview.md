---
title: Widerrufen von Client-Anmeldeinformationen
description: Widerrufen von Client-Anmeldeinformationen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---

# Widerrufen von Client-Anmeldeinformationen{#revoking-client-credentials}

Unter bestimmten Bedingungen ist es erforderlich, die Anmeldeinformationen eines Kunden zu widerrufen oder zu überprüfen, ob ein bestimmter Satz von Anmeldeinformationen bereits widerrufen wurde. Berechtigungen können widerrufen werden, wenn die Anmeldeinformationen nicht erfüllt werden. In diesem Fall werden Lizenzen nicht mehr an kompromittierte Kunden vergeben.

Adobe verwaltet Zertifikatsperrlisten (Certificate Revocation Lists, CRLs) zum Sperren kompromittierter Clients. Diese Zertifikatsperrlisten werden automatisch vom SDK erzwungen. Lizenzserver können Clients weiter einschränken, indem sie bestimmte Maschinenberechtigungen oder bestimmte Versionen von DRM und Laufzeitberechtigungen verbieten. A `RevocationList` kann erstellt und an das SDK übergeben werden, um die Anmeldeinformationen des Computers zu widerrufen. Bestimmte DRM-/Laufzeitversionen können entweder auf Richtlinienebene (durch Festlegen von Modulbeschränkungen in der Wiedergabequalität) oder global (durch Festlegen von Modulbeschränkungen im `HandlerConfiguration`).

Die Diskussion in diesem Kapitel konzentriert sich auf das Widerrufen von Client-Anmeldedaten.
