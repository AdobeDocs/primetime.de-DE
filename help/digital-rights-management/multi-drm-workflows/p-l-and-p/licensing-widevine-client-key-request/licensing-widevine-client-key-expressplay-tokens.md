---
description: Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anforderungen an den entsprechenden Ausdrucks-Token-Server senden.
seo-description: Sie können Ausdrucks-Token für ihren verschlüsselten Inhalt generieren, indem Sie Token-Anforderungen an den entsprechenden Ausdrucks-Token-Server senden.
seo-title: Ausdruckstoken
title: Ausdruckstoken
uuid: 6103e1b2-127d-4758-a589-15f0f3c73db1
translation-type: tm+mt
source-git-commit: d0ba1f98b16f6350ae842ca2ce1261bf49dd8a66

---


# Ausdruckstoken {#expressplay-tokens}

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

Die Datenspeicherung-ID oder die CEKSID für die Inhaltsverschlüsselung, die dem `kid` Parameter übergeben wird, und der Inhaltsverschlüsselungsschlüssel oder der CEK für den `contentKey` Parameter müssen mit der Datenspeicherung-ID des Inhaltsschlüssels und dem für die Verpackung verwendeten Verschlüsselungsschlüssel übereinstimmen. Der folgende Text ist ein Beispiel für die Token-Serverantwort:

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

Anschließend können Sie

* die zurückgegebene URL und Abfrage als Lizenzserver-URL verwenden oder
* Entfernen Sie die Abfrage aus der URL und geben Sie das ExpressPlayToken separat als HTTP POST-Header ein.