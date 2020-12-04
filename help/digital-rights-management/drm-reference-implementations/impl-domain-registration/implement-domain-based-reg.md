---
seo-title: Identitätsbasierte Domänenregistrierung implementieren
title: Identitätsbasierte Domänenregistrierung implementieren
uuid: 4a71b2e0-d1a2-4d63-9cbd-980a292774ab
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f
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
