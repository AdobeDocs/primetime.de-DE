---
seo-title: Allow list for Adobe® Primetime applications allowed to play protected content
title: Zulassungsliste für Adobe® Primetime-Anwendungen, die geschützte Inhalte wiedergeben dürfen
uuid: 3b1f938c-5c76-459e-a918-dfbec0fc2ff9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Zulassungsliste für Adobe® Primetime-Anwendungen, die geschützte Inhalte wiedergeben dürfen {#allowlist-for-adobe-primetime-applications-allowed-to-play-protected-content}

Gibt die AIR/iOS-Anwendungen an, die Inhalte wiedergeben können. Specify the AIR/iOS application ID, minimum version, maximum version, and publisher ID.

Verwendungsbeispiel: Verwenden Sie diese Regel, um die Wiedergabe auf eine bestimmte AIR/iOS-Anwendung zu beschränken oder zu steuern, welche Version auf den Inhalt zugreifen kann.

>[!NOTE]
>
>If you are using Adobe Flash Builder to build protected applications, make sure that you do not deploy the application in ‘Debug&#39; mode. When deploying an application in ‘Debug&#39; mode, the Flash Builder will append “.debug” to the AIR application ID. This will cause the allow list functionality in Adobe Access to behave unexpectedly.

