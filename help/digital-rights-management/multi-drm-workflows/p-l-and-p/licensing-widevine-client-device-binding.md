---
description: In einigen Fällen sollten Sie Endbenutzer daran hindern, Inhalte auf mehreren Geräten abzuspielen, wenn der Inhalt gekauft oder gemietet wird. Wenn der Kunde Expressplay verwendet, kann dies mithilfe der Ausdrücken-APIs erfolgen, um das Ausdrücken-Token des Benutzers an den Computer des Benutzers zu binden.
title: Gerätebindung
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Gerätebindung{#device-binding}

In einigen Fällen sollten Sie Endbenutzer daran hindern, Inhalte auf mehreren Geräten abzuspielen, wenn der Inhalt gekauft oder gemietet wird. Wenn der Kunde Expressplay verwendet, kann dies mithilfe der Ausdrücken-APIs erfolgen, um das Ausdrücken-Token des Benutzers an den Computer des Benutzers zu binden.

Sie können die APIs wie folgt verwenden.

1. Erstellen Sie ein Cookie.
1. Senden Sie eine Anfrage zur Erstellung eines Platzhaltertokens mit dem generierten Cookie entweder als Abfrage-Zeichenfolge (cookie=`<cookie>`) oder als Kopfzeile.
1. Weisen Sie den Computer des Benutzers mit dem oben stehenden Token eine Lizenzanforderung an den Expression-Lizenzserver zu, z. B. durch Wiedergabe eines Platzhalterinhalts.

   Bei erfolgreicher Überprüfung dieser Platzhalterlizenzanforderung wird die vom Benutzer angegebene device_id (von der DRM-Implementierung auf dem Gerät des Benutzers berechnet oder generiert) mit dem Cookie im Expressplay-Back-End verknüpft. Dieses Cookie wird dann wie folgt verwendet:

   * Beim Kauf/der Miete von Inhalten wird das Expressplay-Back-End für die device_id des Benutzers durch Senden des zugehörigen Cookies ( [https://www.expressplay.com/developer/restapi/#record-retrieval](https://www.expressplay.com/developer/restapi/#record-retrieval)) Abfrage.
   * Senden Sie eine Token-Generierungsanfrage mit dem Schlüssel (CEK), der keyID (CEKSID), Richtlinien und anderen Informationen, wobei Sie den obigen Parameter cookie und device_id als den Parameter `cookie` für Korrelationseinschränkungen bzw. `deviceid` für Token anhängen.

   * Geben Sie dieses Token für den Benutzer ein.

      Bei diesem Vorgang wird ein Token für den Inhalt generiert, der an die device_id des Benutzers gebunden ist. Wenn der Computer des Benutzers eine Lizenzanforderung mit diesem Token sendet, prüft das Expressplay-Back-End die device_id des Tokens mit der device_id der Lizenzanforderung.

      Ein Beispielberechtigungsserver für Ausdrücke implementiert diesen Workflow.
