---
description: Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anfragen an den entsprechenden Ausdrucks-Token-Server senden.
title: Ausdrucks-Token
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Ausdrucks-Token {#expressplay-tokens}

Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anfragen an den entsprechenden Ausdrucks-Token-Server senden.

Ein Beispiel ist die folgende URL:

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

Die Speicherkennung des Inhaltsverschlüsselungsschlüssels oder die CEKSID, die der `kid` Parameter und der dem `contentKey` -Parameter muss mit der Speicherkennung des Schlüssels für die Inhaltsverschlüsselung und dem Schlüssel für die Inhaltsverschlüsselung übereinstimmen, der für die Verpackung verwendet wird. Der folgende Text ist ein Beispiel für die Token-Server-Antwort:

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Sie können dann

* die zurückgegebene URL und Abfrage als Lizenzserver-URL verwenden oder
* Entfernen Sie die Abfrage aus der URL und übergeben Sie den ExpressPlayToken separat als HTTP-POST-Header.
