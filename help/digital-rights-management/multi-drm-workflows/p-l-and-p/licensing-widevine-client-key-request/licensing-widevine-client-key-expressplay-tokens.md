---
description: Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anforderungen an den entsprechenden Ausdrucks-Token-Server senden.
title: Ausdruckstoken
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Ausdrucks-Token {#expressplay-tokens}

Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anforderungen an den entsprechenden Ausdrucks-Token-Server senden.

Ein Beispiel ist die folgende URL:

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

Die Content-Verschlüsselungsschlüssel-Datenspeicherung-ID oder die CEKSID, die dem `kid`-Parameter übergeben werden, und der Inhaltsverschlüsselungsschlüssel oder der CEK, der dem `contentKey`-Parameter übergeben wird, müssen mit der Datenspeicherung-ID des Inhaltsverschlüsselungsschlüssels und dem Inhaltsverschlüsselungsschlüssel für die Verpackung übereinstimmen. Der folgende Text ist ein Beispiel für die Token-Serverantwort:

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Anschließend können Sie

* die zurückgegebene URL und Abfrage als Lizenzserver-URL verwenden oder
* Entfernen Sie die Abfrage aus der URL und geben Sie das ExpressPlayToken separat als HTTP-POST-Header ein.