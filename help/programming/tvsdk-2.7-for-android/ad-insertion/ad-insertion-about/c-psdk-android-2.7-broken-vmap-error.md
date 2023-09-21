---
description: Wenn TVSDK in einer Werbeserver-Antwort auf einen defekten VMAP stößt, wird der Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.
keywords: 1109; NETWORK_AD_URL_FAILED; defektes VMAP
title: Umgang mit Client-Fehlern bei beschädigtem VMAP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Umgang mit Client-Fehlern bei beschädigtem VMAP {#client-error-handling-for-broken-vmap}

Wenn TVSDK in einer Werbeserver-Antwort auf einen defekten VMAP stößt, wird der Fehler 1109 (NETWORK_AD_URL_FAILED) ausgelöst.

Je nach der Art der Antwort des Werbeservers und Ihren Einstellungen zum Laden der Anzeige kann Ihr Player eine unterschiedliche Anzahl von 1109 Fehlern erhalten, wenn TVSDK in einer Antwort des Werbeservers auf ein defektes VMAP stößt.

Betrachten wir ein Szenario, in dem die Antwort des Werbeservers auf VMAP XML verweist. Nehmen wir auch an, dass die Antwort des Werbeservers über vier verfügbare Anzeigenplätze verfügt, von denen jeder auf dasselbe VMAP verweist. Lassen Sie uns abschließend sagen, dass dieses VMAP gebrochen ist.

In diesem Szenario ist die verzögerte Anzeigenauflösung aktiviert ( [Verzögertes Auflösen von Anzeigen aktivieren](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)), sendet TVSDK zwei 1109-Fehler (nicht den erwarteten): Bei jedem Parsing-Pass über die Timeline wird ein Fehler gesendet. Dies liegt daran, dass TVSDK bei aktivierter verzögerter Anzeigenauflösung die Anzeigen in 2 Durchgängen analysiert: Der erste Durchlauf erfolgt unmittelbar vor dem Start der Inhaltswiedergabe für Pre-Roll-Anzeigen und der zweite Durchlauf nach dem Start der Wiedergabe für Mid-Roll- und Post-Roll-Anzeigen.

>[!NOTE]
>
>In diesem Szenario löst TVSDK bei Deaktivierung der verzögerten Anzeigenauflösung nur einen 1109-Fehler aus (nur ein Parsing-Pass).
