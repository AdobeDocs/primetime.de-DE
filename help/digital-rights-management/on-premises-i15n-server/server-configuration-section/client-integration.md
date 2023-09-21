---
title: Client-Integration
description: Client-Integration
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '76'
ht-degree: 0%

---

# Client-Integration{#client-integration}

Um den Client zur Individualisierung an den On-Premises-Individualisierungsserver (im Gegensatz zum Adobe gehosteten globalen Individualisierungsserver) zu leiten, sollte der Client die zuvor erstellten DRM-Metadaten für Premises verwenden. Wenn ein nicht individualisierter Client eine Lizenzakquise durchführt oder DRM mithilfe der speziellen Metadaten initialisiert, führt dies dazu, dass der Client eine Verbindung zur benutzerdefinierten URL des Individualization Server herstellt.

Ein Codebeispiel ist im [!DNL client_sample] Ordner.
