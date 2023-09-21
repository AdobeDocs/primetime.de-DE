---
title: Preflight-Funktion, Aktivierung, Fehlerbehebung oder Feststellung des Problems
description: Preflight-Funktion, Aktivierung, Fehlerbehebung oder Feststellung des Problems
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# Preflight-Funktion: Anleitung zum Aktivieren, Fehlerbehebung oder Bestimmen des Problems {#preflight-feature}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

Die Art und Weise, wie die Adobe Primetime-Authentifizierung preAuthorizeResources berechnet, wurde geändert. Die PreAuthorization-API verfügt über eine neue Implementierung. Diese Implementierung ersetzt die alte Lösung, die nur die Ausführung mehrerer Autorisierungsaufrufe umfasst.
Die externe Schnittstelle für die PreAuthorization-API ist unverändert. In der Programmeranwendung sind keine Aktualisierungen erforderlich.

Es gibt drei Möglichkeiten, die Preflight-Ressourcen zu berechnen:

* **Verzweigung und Verbindungsmethode zum MVPD**: Dazu müssen Adobe mehrere Autorisierungsaufrufe an den MVPD tätigen (der Client muss jedoch noch einen Preflight-Aufruf durchführen).
* **Kanalaufteilung**: Der MVPD stellt die Kanalverbindung für den angemeldeten Benutzer in der SAML-Authentifizierungsantwort bereit und Adobe gibt die darauf basierenden autorisierten Ressourcen zurück. Die SAML authN-Antwort im SAML-Tracker sollte diese Liste verfügbar machen.
* **Mehrkanalautorisierung**: Die Client- und Adobe-Authentifizierung führen beide einen einzigen Aufruf an den MVPD für eine Reihe von Ressourcen durch.

Unabhängig vom MVPD führt die Client-Anwendung einen einzelnen Aufruf an den Preflight-Endpunkt (checkPreauthorizedResources-API) durch und übergibt eine Reihe von resourceIDs. Basierend auf einer der oben genannten Methoden, die von MVPD unterstützt werden, gibt Adobe dann die vorab autorisierten resourceIDs zurück.

Wenn Preflight auf der Abspaltungs- und Join-Methode basiert, prüft das Adobe Primetime-Authentifizierungs-Backend in seiner Konfiguration einen für die &#39;max preauthorization calls&#39; festgelegten Wert. Dies wird durch Adobe konfiguriert.

Der Standardwert für die Konfiguration &quot;max preauthorization calls&quot;ist &quot;5&quot;, d. h., in Preflight können maximal 5 Ressourcen für die MVPDs &quot;fork &amp; join&quot;gesendet werden. Wenn Sie mehr als 5 Ressourcen übergeben, wird eine Ausnahme ausgegeben und eine Null-Liste zurückgegeben. Dies ist das erwartete Verhalten. Wir können dies auf einen beliebigen Wert konfigurieren, wenn das MVPD keine Channel-Lineup- oder Multi-Channel-Autorisierung unterstützt, aber erst nach Absprache mit ihnen, da mehrere Fork- und Join-Autorisierungsaufrufe ihre Ladezeiten erhöhen.

Daher sollten Sie nach diesen Dingen suchen, wenn Sie Preflight für einen MVPD aktivieren/beheben:

* Die Methode, die der MVPD unterstützt (Verzweigung und Verknüpfung, Kanalaufteilung oder Multi-Channel).
* Wenn nur Abspaltung und Join unterstützt wird, muss der Programmierer gefragt werden, wie viele resourceIDs er im Preflight-Aufruf senden wird.
* Der MVPD muss konsultiert werden und muss wissen, wie sich eine &quot;n&quot; Anzahl von Abspaltungs- und Join-Autorisierungsaufrufen auswirkt. Danach muss der Wert in config konfiguriert werden, wenn er größer als 5 ist.

**Einschränkung**

Bitte beachten Sie, dass wir keine resourceID aus dem Preflight-Aufruf für einige MVPDs wie AT&amp;T &amp; TWC erhalten, wenn eine der resourceIDs eine falsche ID oder eine nicht erkannte ID in der Liste der resourceIDs ist, die sie im Preflight-Aufruf senden, obwohl wir auch über gültige und autorisierte Ressourcen in dieser Liste verfügen.
