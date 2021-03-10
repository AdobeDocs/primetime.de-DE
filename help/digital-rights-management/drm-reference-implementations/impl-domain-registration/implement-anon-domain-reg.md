---
title: Anonyme Domänenregistrierung implementieren
description: Anonyme Domänenregistrierung implementieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '37'
ht-degree: 0%

---


# Anonyme Domänenregistrierung implementieren{#implement-anonymous-domain-registration}

1. Erstellen Sie eine DRM-Richtlinie, die angibt, dass eine Domänenregistrierung erforderlich ist.
1. Geben Sie die URL des Domänenservers an als:

   ```
   https://[host:port]/flashaccess/domainserver/domainname/
   ```

1. Anonyme Authentifizierung erforderlich machen.

   Legen Sie in der Datei [!DNL .properties] Folgendes fest:

   ```
   policy.domain.anonymous=true 
   ```
