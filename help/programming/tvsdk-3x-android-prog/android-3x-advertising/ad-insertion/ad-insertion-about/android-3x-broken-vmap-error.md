---
description: Wenn TVSDK in einer Werbeserver-Antwort auf einen beschädigten VMAP stößt, wird ein Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.
keywords: 1109;NETWORK_AD_URL_FAILED;broken VMAP
seo-description: Wenn TVSDK in einer Werbeserver-Antwort auf einen beschädigten VMAP stößt, wird ein Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.
seo-title: Behandlung von Clientfehlern bei beschädigtem VMAP
title: Behandlung von Clientfehlern bei beschädigtem VMAP
uuid: ab2c567d-d945-4ebe-b65a-c1f13518a576
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Behandlung von Clientfehlern bei beschädigtem VMAP {#client-error-handling-for-broken-vmap}

Wenn TVSDK in einer Werbeserver-Antwort auf einen beschädigten VMAP stößt, wird ein Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.

Abhängig von der Art der Antwort auf den Anzeigen-Server und Ihren Einstellungen zum Laden der Anzeige kann Ihr Player eine unterschiedliche Anzahl von 1109 Fehlern erhalten, wenn TVSDK in einer Antwort auf einen ungültigen VMAP auf dem Anzeigen-Server auftritt.

Betrachten wir ein Szenario, bei dem die Antwort des Anzeigenservers auf die VMAP-XML verweist. Nehmen wir auch an, dass die Antwort des Werbeservers vier verfügbare Anzeigenplätze hat, von denen jeder auf denselben VMAP verweist. Lassen Sie uns abschließend sagen, dass dieser VMAP kaputt ist.

In diesem Szenario löst TVSDK zwei 1109 Fehler aus, wenn verzögertes Auflösen aktiviert ist (verzögertes Auflösen[aktivieren](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/t-enable-lazy-ad-resolving.md)): bei jedem Parsing-Pass über der Zeitleiste wird ein Fehler ausgelöst. Dies liegt daran, dass TVSDK bei Aktivierung der verzögerten Anzeigenauflösung die Anzeigen in 2 Durchgängen analysiert: der erste Durchlauf erfolgt unmittelbar vor den Beginn für die Inhaltswiedergabe für Pre-Roll-Anzeigen und der zweite Durchlauf nach Wiedergabe-Beginn für Mid-Roll- und Post-Roll-Anzeigen.

>[!NOTE]
>
>Wenn Sie in diesem Szenario die verzögerte Anzeigenauflösung deaktivieren, löst TVSDK nur einen 1109-Fehler aus (nur einen Parsing-Pass).