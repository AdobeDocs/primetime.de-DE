---
title: Aktivieren von Primetime-Berechtigungsdiensten für ein Programm in Xbox 360 und XboxOne Clientless
description: Aktivieren von Primetime-Berechtigungsdiensten für ein Programm in Xbox 360 und XboxOne Clientless
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Aktivieren von Primetime-Berechtigungsdiensten für ein Programm in Xbox 360 und XboxOne Clientless {#enabling-primetime-entitlement-services-for-a-programer-on-xbox-360-and-xboxone-clientless}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.




1. Der Programmierer erstellt ein Zendesk-Ticket zur Aktivierung der clientlosen Xbox 360/One-Lösung für die Primetime-Authentifizierung, indem er die folgenden Informationen bereitstellt:

   1. Plattform: z. B. Xbox 360, Xbox One

   1. Anforderer-ID: z. B. netgeo, CNN etc.

1. Adobe erstellt X509-Zertifikate und konfiguriert den privaten Schlüssel und das Kennwort am Ende.

1. Adobe stellt dem Programer das öffentliche Zertifikat (des X509-Zertifikats) im Ticket oder per E-Mail zur Verfügung.

1. Der Programmierer muss dieses öffentliche Zertifikat dann im GDNP-Portal für die bei Microsoft registrierte App installieren.

1. Der Programmierer fordert dann das JWT-Token (Java Web Token) bzw. STS-Token für XboxOne bzw. 360 vom Microsoft Xbox Live-Dienst an, der mit dem in Schritt 3 bereitgestellten öffentlichen X509-Zertifikat verschlüsselt wird.

1. Dies sind die Token, die die eindeutige deviceId für Xbox-Geräte enthalten. Fügen Sie das Token (JWT oder STS) mithilfe eines &quot;x&quot;-Parameters in die Autorisierungskopfzeile ein (wie unten gezeigt):

   1. Für Xbox 360 muss das XSTS-Token Base64-kodiert sein, bevor es an die Primetime-Pay-TV-Authentifizierung gesendet wird.
   1. Bei Xbox One ist das JWT bereits korrekt kodiert, sodass keine zusätzliche Kodierung erfolgen sollte.

1. Alle API-Aufrufe des Xbox-Geräts sollten die Autorisierungskopfzeile mit dem oben genannten Token im x-Parameter enthalten.



>[!NOTE]
>
>Insbesondere die Xbox weist einige eindeutige Anforderungen im Zusammenhang mit digitalem Signieren auf. Die Geräte-ID der XBox-Konsole ist im XSTS-Token enthalten.  Für Xbox 360 ist dies eine verschlüsselte SAML-Assertion. Für Xbox One ist dies ein verschlüsseltes JWT. Die XBox-Konsolenanwendung sendet das gesamte XSTS-Token an die Primetime-Pay-TV-Authentifizierung. Die Pay-TV-Authentifizierung von Primetime entschlüsselt das Token mit seinem öffentlichen Schlüssel, analysiert das Token und extrahiert die deviceId daraus.

>[!NOTE]
>
>Aufgrund der großen Länge des XSTS-Tokens hat die XBox-Konsole eine technische Einschränkung: Sie kann das Token nicht als HTTP-GET-Parameter an die Primetime-Pay-TV-Authentifizierungs-APIs senden. Um dies zu beheben, ermöglicht die Pay-TV-Authentifizierung von Primetime das Senden des XSTS-Tokens als Teil des HTTP-Headers &quot;Authorization&quot;beim Aufrufen der APIs. Das XSTS-Token muss mit dem öffentlichen Schlüssel aus dem X.509-Zertifikat verschlüsselt werden, das dem Programmierer von der Primetime-Pay-TV-Authentifizierung ausgestellt wurde. Die Pay-TV-Authentifizierung von Primetime speichert den zugehörigen privaten Schlüssel und verwendet ihn zum Entschlüsseln des XSTS-Tokens und zum Extrahieren der deviceId.
