---
title: Identitätsbasierte Domänenregistrierung implementieren
description: Identitätsbasierte Domänenregistrierung implementieren
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---

# Identitätsbasierte Domänenregistrierung implementieren{#implement-identity-based-domain-registration}

1. Erstellen Sie eine DRM-Richtlinie mit einer obligatorischen Domänenregistrierung.
1. Geben Sie den Host und Port des Servers für die URL des Domänenservers an.

   In der [!DNL .properties] -Datei, festlegen:

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Machen Sie die Authentifizierung mit einem Benutzernamen und einem Kennwort obligatorisch.

   In der [!DNL .properties] -Datei, festlegen:

   ```
   policy.domain.anonymous=false 
   ```
