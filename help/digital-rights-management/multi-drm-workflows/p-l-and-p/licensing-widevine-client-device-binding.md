---
description: In einigen Fällen können Sie Endbenutzer daran hindern, Inhalte auf mehreren Geräten wiederzugeben, wenn der Inhalt gekauft oder gemietet wird. Wenn der Kunde "Expressplay"verwendet, kann dies durch die Verwendung der Ausdrücke-APIs erfolgen, um das Ausdrücken-Token des Benutzers an den Computer des Benutzers zu binden.
title: Gerätebindung
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Gerätebindung{#device-binding}

In einigen Fällen können Sie Endbenutzer daran hindern, Inhalte auf mehreren Geräten wiederzugeben, wenn der Inhalt gekauft oder gemietet wird. Wenn der Kunde &quot;Expressplay&quot;verwendet, kann dies durch die Verwendung der Ausdrücke-APIs erfolgen, um das Ausdrücken-Token des Benutzers an den Computer des Benutzers zu binden.

Sie können die APIs wie folgt verwenden:

1. Generieren Sie ein Cookie.
1. Senden Sie eine Anfrage zur Generierung eines Platzhalter-Tokens mit dem generierten Cookie als Abfragezeichenfolge (cookie=)`<cookie>`) oder als Kopfzeilen.
1. Bitten Sie den Computer des Benutzers, mithilfe des oben genannten Tokens eine Lizenzanfrage an den Expression-Lizenzserver zu senden, z. B. durch Wiedergabe eines Platzhalterinhalts.

   Bei erfolgreicher Überprüfung der Platzhalterlizenz wird die device_id des Benutzers (berechnet oder von der DRM-Implementierung auf dem Gerät des Benutzers generiert) mit dem Cookie im Backend &quot;Ausdruck&quot;verknüpft. Dieses Cookie wird dann wie folgt verwendet:

   * Beim Kauf/Miete von Inhalten fragt der Code das Backend des Ausdrucks für die device_id des Benutzers ab, indem er das zugehörige Cookie ( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval))
   * Senden Sie eine Token-Generierungsanfrage mit dem Schlüssel (CEK), der keyID (CEKSID), den Richtlinien und anderen Informationen, wobei Sie das Cookie und die device_id oben als `cookie` Korrelationsparameter und `deviceid` Token-Einschränkungsparameter.

   * Geben Sie dieses Token für den Benutzer an.

     Dieser Prozess generiert ein Token für den Inhalt, der an die device_id des Benutzers gebunden ist. Wenn der Computer des Benutzers eine Lizenzanfrage mit diesem Token sendet, prüft das Backend des Ausdrucks die Geräte-ID des Tokens mit der Geräte-ID der Lizenzanfrage.

     Ein Beispiel für einen Berechtigungsserver für Ausdrücke implementiert diesen Workflow.
