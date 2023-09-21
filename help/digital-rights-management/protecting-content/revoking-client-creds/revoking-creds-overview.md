---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Übersicht{#overview}

Möglicherweise müssen Sie die Anmeldeinformationen eines Kunden widerrufen oder überprüfen, ob ein bestimmter Berechtigungssatz bereits unter bestimmten Bedingungen widerrufen wurde. Berechtigungen können widerrufen werden, wenn sie kompromittiert sind. Wenn diese Probleme auftreten, werden keine Lizenzen mehr an kompromittierte Kunden vergeben.

Adobe verwaltet Zertifikatsperrlisten (Certificate Revocation Lists, CRLs) zum Sperren kompromittierter Clients. Diese Zertifikatsperrlisten werden automatisch vom SDK erzwungen. Lizenzserver können Clients weiter einschränken, indem sie bestimmte Maschinenberechtigungen oder bestimmte Versionen von DRM und Laufzeitberechtigungen verbieten. A `RevocationList` kann erstellt und an das SDK übergeben werden, um die Anmeldeinformationen des Computers zu widerrufen. Bestimmte DRM-/Laufzeitversionen können entweder auf DRM-Richtlinienebene widerrufen werden, indem Modulbeschränkungen in der Wiedergabequalität festgelegt werden oder global, indem Modulbeschränkungen in der `HandlerConfiguration`.

Im Mittelpunkt der Diskussion steht das Widerrufen von Client-Anmeldedaten.
