---
title: WKWebView-Unterstützung für iOS SDK 3.1+
description: WKWebView-Unterstützung für iOS SDK 3.1+
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# WKWebView-Unterstützung für iOS SDK 3.1+ {#wkwebview-support-on-ios-sdk-3.1}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

</br>

**Da Apple UIWebView auf iOS nicht mehr unterstützt, haben wir iOS SDK 3.1 mit Unterstützung für WKWebView aktualisiert.**

## Kompatibilität {#compatibility}

Ab iOS SDK-Version 3.1 können Implementoren jetzt WKWebView oder UIWebView austauschbar verwenden. Da UIWebView von Apple nicht mehr unterstützt wird, sollten Apps zu WKWebView migrieren, um Probleme mit zukünftigen iOS-Versionen zu vermeiden.

Beachten Sie, dass bei der Migration lediglich der Umstieg auf die UIWebView-Klasse auf WKWebView erforderlich ist. In Bezug auf AccessEnabler von Adobe ist keine spezifische Arbeit erforderlich.

## Bekannte Probleme {#known-issues}

AccessEnabler von Adobe verwendete eine verborgene interne UIWebView-Instanz, um &quot;[passive Authentifizierung](/help/authentication/sso-passive-authn.md)&quot;für bestimmte MVPDs. Der &quot;passive&quot;Fluss war für MVPDs nützlich, die Authentifizierung für jede Anfragende-ID erfordern. Von diesem Fluss profitierten jene Programmierer, die dieselbe Team-ID über mehrere iOS-Anwendungen hinweg verwendeten, um ein SSO-Erlebnis (Adobe SSO) zu simulieren. Diese Funktion wird derzeit von einer begrenzten Anzahl von MVPDs verwendet.

Die Funktion nutzte ein UIWebView-Verhalten, das es der Adobe ermöglichte, die Authentifizierungs-Cookies zu erfassen und sie während des &quot;passiven&quot;Flusses erneut wiederzugeben. WKWebView bietet eine höhere Sicherheit, die die Adobe verhindert, die bei der Anmeldung eingestellten Cookies zu erfassen und sie mithilfe einer verborgenen Instanz von WKWebView erneut wiederzugeben. Aufgrund dieser Sicherheitsverbesserung und angesichts der Tatsache, dass der &quot;passive&quot;Fluss nur einer sehr begrenzten Anzahl von MVPDs in einem sehr spezifischen Implementierungsszenario zugute kam (mehrere Anwendungen mit derselben Team-ID), hat Adobe die &quot;passive Authentifizierungsfunktion&quot;für MVPDs entfernt, die zur Authentifizierung Webansichten verwenden.

Die Funktion ist weiterhin für MVPDs vorhanden, die für die Verwendung von SFSafariViewController konfiguriert sind. Beachten Sie jedoch, dass in diesem Fall die &quot;passive&quot;Authentifizierung für den Benutzer sichtbar ist, da SFSafariViewController nicht auf &quot;verborgene&quot;Weise verwendet werden kann.
