---
description: Wenn TVSDK in einer Werbeserver-Antwort auf einen beschädigten VMAP stößt, wird ein Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.
keywords: 1109;NETWORK_AD_URL_FAILED;unterbrochene VMAP
title: Behandlung von Clientfehlern bei beschädigtem VMAP
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Behandlung von Clientfehlern bei beschädigtem VMAP {#client-error-handling-for-broken-vmap}

Wenn TVSDK in einer Werbeserver-Antwort auf einen beschädigten VMAP stößt, wird ein Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.

Abhängig von der Art der Antwort auf den Anzeigen-Server und Ihren Einstellungen zum Laden der Anzeige kann Ihr Player eine unterschiedliche Anzahl von 1109 Fehlern erhalten, wenn TVSDK in einer Antwort auf einen ungültigen VMAP auf dem Anzeigen-Server auftritt.

Betrachten wir ein Szenario, bei dem die Antwort des Anzeigenservers auf die VMAP-XML verweist. Nehmen wir auch an, dass die Antwort des Werbeservers vier verfügbare Anzeigenplätze hat, von denen jeder auf denselben VMAP verweist. Lassen Sie uns abschließend sagen, dass dieser VMAP kaputt ist.

In diesem Szenario löst TVSDK zwei 1109 Fehler aus (nicht wie erwartet), wenn verzögertes Auflösen der Anzeige aktiviert ist ( [Verzögertes Auflösen aktivieren](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)): bei jedem Parsing-Pass über der Zeitleiste wird ein Fehler ausgelöst. Dies liegt daran, dass TVSDK bei Aktivierung der verzögerten Anzeigenauflösung die Anzeigen in 2 Durchgängen analysiert: der erste Durchlauf erfolgt unmittelbar vor den Beginn für die Inhaltswiedergabe für Pre-Roll-Anzeigen und der zweite Durchlauf nach Wiedergabe-Beginn für Mid-Roll- und Post-Roll-Anzeigen.

>[!NOTE]
>
>Wenn Sie in diesem Szenario die verzögerte Anzeigenauflösung deaktivieren, löst TVSDK nur einen 1109-Fehler aus (nur einen Parsing-Pass).

