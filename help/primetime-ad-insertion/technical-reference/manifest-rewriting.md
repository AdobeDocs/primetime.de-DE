---
title: Manifest-Neuschreiben und Ad-Fetching-Regeln
description: Manifest-Neuschreiben und Ad-Fetching-Regeln
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Manifest-Neuschreiben und Ad-Fetching-Regeln {#manifest-rewriting}

Mit Primetime Ad Insertion können Fragmente neu geschrieben und Assets mithilfe einfacher Such-/Ersetzungsregeln abgerufen werden.  Dies kann verwendet werden, um https nach unten in HTTP-Anforderungen zu konvertieren, wodurch die Leistung durch Entfernen von TLS-Handshakes erhöht würde.  Dies kann auch verwendet werden, um Anzeigen-Assets und CDN-Assets aus demselben CDN bereitzustellen.

Regeln werden als Suche/Ersetzung für reguläre Ausdrücke definiert und können verwendet werden, um URLs vor dem Senden sowie nach dem Einfügen in ein Manifest umzuwandeln.

Diese Beispielregel konvertiert alle Anzeigenanforderungen von https in http nach domain.com herunter.

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

Die folgende Regel verwendet das Inhalts-CDN, um Anzeigen bereitzustellen, die sich auf dem Adobe und dem Speicher-CDN befinden.

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

Regeln können benannt und aktiviert/deaktiviert werden, indem die `ptprotoswitch` -Parameter in der Bootstrap-API, bei der es sich um eine kommagetrennte Liste der auszuführenden Regeln handelt.  Diese beiden Regeln können beispielsweise beide durch Festlegen von `ptprotoswitch=adfetch_rule1,adfetch_rule2`:

```
<ruleSet>
    <rule name="rule1">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
    <rule name="rule2">
        <find><![CDATA[...]]></find>
        <replace><![CDATA[...]]></replace>
    </rule>
</ruleSet>
```

Wenden Sie sich an Ihren technischen Support, um diese Regeln für Ihr Konto zu erstellen/zu aktivieren.
