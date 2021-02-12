---
title: Manifestumschreibungs- und Anzeigenabruf-Regeln
description: 'Manifestumschreibungs- und Anzeigenabruf-Regeln '
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Manifestumschreibung und Ad-Fetching-Regeln {#manifest-rewriting}

Primetime Ad Insertion ermöglicht das Umschreiben von Fragmenten und das Abrufen von Assets mithilfe einfacher Such-/Ersetzungsregeln.  Auf diese Weise können Sie HTTPS in HTTP-Anforderungen nach unten konvertieren, wodurch die Leistung durch Entfernen von TLS-Handshakes erhöht wird.  Dies kann auch verwendet werden, um Anzeigen- und CDN-Assets von demselben CDN bereitzustellen.

Regeln werden als reguläre Suche/Ersetzung von Ausdrücken definiert und können verwendet werden, um URLs vor dem Senden sowie nach dem Einfügen in ein Manifest umzuformen.

Diese Beispielregel konvertiert alle Anzeigenanforderungen von HTTPS zu http in domain.com.

```
find: "https://domain.com/(.*)"
replace: "http://domain.com/$1"
```

Die folgende Regel verwendet das Content-CDN zur Bereitstellung von Anzeigen, die sich im CDN der Adobe und Datenspeicherung befinden.

```
find: "https?://primetime-a.akamaihd.net/(.*)"
replace: "http://mycdn.com/ad-mapping-pathname/$1"
```

Regeln können benannt und aktiviert/deaktiviert werden, indem Sie den Parameter `ptprotoswitch` in der Bootstrap-API ändern. Hierbei handelt es sich um eine kommagetrennte Liste von auszuführenden Regeln.  Diese beiden Regeln können beispielsweise beide durch Festlegen von `ptprotoswitch=adfetch_rule1,adfetch_rule2` ausgeführt werden:

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