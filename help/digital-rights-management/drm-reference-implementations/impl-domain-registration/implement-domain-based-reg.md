---
title: Identitätsbasierte Domänenregistrierung implementieren
description: Identitätsbasierte Domänenregistrierung implementieren
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 0%

---


# Identitätsbasierte Domänenregistrierung implementieren{#implement-identity-based-domain-registration}

1. Erstellen Sie eine DRM-Richtlinie mit obligatorischer Domänenregistrierung.
1. Geben Sie den Host und Anschluss des Servers für die URL des Domänenservers an.

   Legen Sie in der Datei [!DNL .properties] Folgendes fest:

   ```
   policy.domain.url=https://[server:port] 
   ```

1. Die Authentifizierung mit Benutzername und Kennwort muss obligatorisch sein.

   Legen Sie in der Datei [!DNL .properties] Folgendes fest:

   ```
   policy.domain.anonymous=false 
   ```
