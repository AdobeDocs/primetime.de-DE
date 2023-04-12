---
title: Übersicht für Programmierer
description: Übersicht für Programmierer
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '4272'
ht-degree: 0%

---


# Übersicht für Programmierer {#programmers-overview}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle -Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#introduction}

Diese Übersicht richtet sich an den Inhaltsanbieter (Programmierer), der plant, Adobe® Pass in seine Website oder Anwendung zu integrieren. Weitere Dokumentationen, einschließlich Schnellstart- und Integrationsleitfäden, finden Sie unten unter Verwandte Informationen .

Heute können Ihre Betrachter jederzeit und überall im Internet surfen und direkt von Ihnen, dem Programmierer, den Zugriff auf geschützte Inhalte anfordern. Sie möchten vielleicht eine einmalige Veranstaltung sehen, oder sie suchen nach Anzeigerechten für eine ganze Fernsehserie, die Sie ausstrahlen.

Bevor Sie jedoch den Zugriff auf Ihre geschützten Inhalte zulassen, müssen Sie festlegen, ob ein Kunde berechtigt ist, diese Inhalte anzuzeigen. Haben sie ein Abonnement mit einem Multichannel Video Programming Distributor (MVPD)? Wenn ja, beinhaltet dieses Abonnement Ihre Programmierung?

Die Bestimmung der Berechtigung eines Betrachters ist für einen Programmierer nicht immer einfach. Die MVPDs verfügen über die identifizierenden Daten und Zugriffsberechtigungen für ihre Kunden.  Fügen Sie hinzu, dass Betrachter, die versuchen, auf Ihren geschützten Inhalt zuzugreifen, sich für eine Vielzahl von MVPDs anmelden, von denen jede über verschiedene Systeme verfügt. Es ist einfach festzustellen, dass die Bestimmung des Anspruchs des Betrachters auf geschützte Inhalte schnell kompliziert und technisch schwierig werden kann:

![](assets/user-ent-by-progr.png)

*Abbildung: Benutzerberechtigungen, die direkt vom Programmierer bestimmt werden*

Adobe Primetime-Authentifizierung für TV Anywhere vermittelt diese Berechtigungstransaktionen zwischen Programmierern und MVPDs sicher. Die Adobe Primetime-Authentifizierung ermöglicht es Programmierern, geschützte Inhalte für gültige Kunden einfach, schnell und sicher bereitzustellen:

![](assets/user-ent-mediatedby-authn.png)

*Abbildung: Benutzerberechtigungen durch Adobe Primetime-Authentifizierung vermittelt*

Die Adobe Primetime-Authentifizierung fungiert als Proxy im Austausch mit teilnehmenden MVPDs, sodass Sie Ihre Viewer mit einer konsistenten siteübergreifenden Oberfläche präsentieren können. Mit der Adobe Primetime-Authentifizierung können Sie Ihren Viewern auch die Authentifizierung und Autorisierung per Single Sign-on (SSO) ermöglichen. Authentifizierung und Autorisierung werden für alle beteiligten Dienste verfolgt, sodass sich ein Abonnent nach seiner ersten Authentifizierung auf seinem eigenen System nicht mehr anmelden muss.

* **Authentifizierung** - Der Prozess, mit einem MVPD zu bestätigen, dass ein bestimmter Benutzer ein bekannter Kunde ist.
* **Genehmigung** - Der Prozess der Bestätigung mit einem MVPD, dass ein authentifizierter Benutzer über ein gültiges Abonnement für eine bestimmte Ressource verfügt.

### Funktionsweise der Adobe Primetime-Authentifizierung {#HowItWorks}

Die Content-Viewing-Anwendung des Programmierers interagiert mit der Adobe Primetime-Authentifizierung entweder über die Access Enabler-Client-Komponente oder die RESTful-Webdienste der Client-losen API (für nicht webfähige Geräte wie Smart TVs, Spielekonsolen, Set-Top-Boxen usw.). Der Access Enabler wird auf dem System des Benutzers ausgeführt, wodurch alle Berechtigungs-Workflows vereinfacht werden.  Die Komponente &quot;Access Enabler&quot;wird zur Adobe von ihrer Hosting-Website heruntergeladen, wenn Kunden auf Ihre Site zugreifen und geschützte Inhalte anfordern.  Adobe Primetime-Authentifizierungsserver hosten die RESTful-Webdienste, die in der Clientless-Lösung verwendet werden.

Die Adobe Primetime-Authentifizierung handhabt die tatsächlichen Berechtigungs-Workflows und stellt Primitive bereit, die Sie für Folgendes verwenden:

* Legen Sie Ihre Identität fest. (Der Programmierer ist der &quot;Anforderer&quot;im Berechtigungsfluss der Adobe Primetime-Authentifizierung.)
* Authentifizieren Sie einen Benutzer mit einem bestimmten MVPD.  (Der MVPD ist der &quot;Identitäts-Provider&quot;oder &quot;IdP&quot;im Berechtigungsfluss der Adobe Primetime-Authentifizierung.)
* Autorisieren Sie einen Benutzer mit dem MVPD für eine bestimmte Ressource.
* Melden Sie den Benutzer ab.

Der Programmierer ist für seine übergeordnete Web-Seite oder Player-Anwendung verantwortlich, die Folgendes durchführt:

* Implementiert die Benutzeroberfläche
* Interagiert mit den Web-Services Access Enabler oder ClientLess API

Ziel der Adobe Primetime-Authentifizierung ist es, eine einfache, modulare Methode zu erstellen, mit der sowohl Programmierer als auch MVPDs die Berechtigungsprüfung durchführen können.

## Grundlagen zu Token {#understanding-tokens}

Die Adobe Primetime-Authentifizierungsberechtigungslösung konzentriert sich auf die Generierung spezifischer Datenteile, die nach erfolgreichem Abschluss der Authentifizierungs- und Autorisierungs-Workflows erstellt werden. Diese Daten werden als Token bezeichnet. Token haben eine begrenzte Lebensdauer; Wenn sie ablaufen, müssen Token erneut ausgestellt werden, indem die Authentifizierungs- und Autorisierungs-Workflows neu gestartet werden.

Weitere Informationen zu Tokens finden Sie in den folgenden Abschnitten:

* [Typen von Token](#token-types)
* [Token-Speicher](#token-storage)
* [Token-Sicherheit](#token-security)
* [Token-Freigabe](#token-sharing)

### Token-Typen {#token-types}

Während der Authentifizierungs- und Autorisierungs-Workflows werden drei Typen von Token ausgegeben. Die AuthN- und AuthZ-Token sind &quot;langlebig&quot;, was Kontinuität im Anzeigeerlebnis des Benutzers bietet. Das Media Token ist ein kurzlebiges Token, das Best Practices der Branche zur Verhinderung von Betrug durch Stream-Ripping unterstützt. Programmierer geben die TTL-Werte (Time-to-Live) für jeden Token-Typ basierend auf Vereinbarungen mit MVPDs an. Programmierer entscheiden über einen TTL-Wert, der am besten für Ihr Unternehmen und Ihre Kunden geeignet ist.

* **AuthN-Token** (&quot;Lange Lebensdauer&quot;): Bei erfolgreicher Authentifizierung erstellt die Adobe Primetime-Authentifizierung ein AuthN-Token, das sowohl mit dem anfordernden Gerät als auch mit einer global eindeutigen Kennung (GUID) verknüpft ist.
   * Adobe Primetime-Authentifizierung sendet das AuthN-Token an den Access Enabler, der es sicher auf dem Client-System zwischenspeichert.  Während das AuthN-Token vorhanden und nicht abgelaufen ist, ist es für alle Anwendungen verfügbar, die die Adobe Primetime-Authentifizierung verwenden. Der Access Enabler verwendet das AuthN-Token für den Autorisierungsfluss.
   * Zu jedem Zeitpunkt wird nur ein AuthN-Token zwischengespeichert. Wenn ein neues AuthN-Token ausgegeben und bereits ein altes vorhanden ist, überschreibt die Adobe Primetime-Authentifizierung das zwischengespeicherte Token.
* **AuthZ-Token** (&quot;Lange Lebensdauer&quot;): Nach erfolgreicher Autorisierung erstellt die Adobe Primetime-Authentifizierung ein AuthZ-Token, das mit dem anfordernden Gerät verknüpft ist, und eine bestimmte geschützte Ressource.  Die geschützte Ressource wird durch eine eindeutige Ressourcen-ID identifiziert.
   * Adobe Primetime-Authentifizierung sendet das AuthZ-Token an den Access Enabler, der es sicher auf dem lokalen System zwischenspeichert. Der Access Enabler verwendet dann das AuthZ-Token, um das kurzlebige Medien-Token zu erstellen, das für den tatsächlichen Anzeigezugriff verwendet wird.
   * Zu jedem Zeitpunkt wird nur ein AuthZ-Token pro Ressource zwischengespeichert. Adobe Primetime-Authentifizierung kann mehrere AuthZ-Token zwischenspeichern, sofern sie mit verschiedenen Ressourcen verknüpft sind. Wenn ein neues AuthZ-Token ausgegeben wird und bereits ein altes für dieselbe Ressource existiert, überschreibt die Adobe Primetime-Authentifizierung das zwischengespeicherte Token.
* **Medien-Token** (&quot;kurzlebig&quot;): Der Access Enabler verwendet das AuthZ-Token, um eine kurzlebige (Standard: 7 Minuten) Medien-Token. Dies ist der Punkt, an dem eine erfolgreiche Wiedergabeanforderung als aufgetreten gilt.
   * Bevor Sie Zugriff auf die geschützte Ressource gewähren, muss Ihr Medienserver eine Adobe Primetime-Authentifizierungskomponente, den Media Token Verifier, verwenden, um das Medien-Token zu validieren.
   * Da das Medien-Token nicht an das Gerät gebunden ist, ist seine Lebensdauer erheblich kürzer (Standard: 7 Minuten) als die der langlebigen AuthN- und AuthZ-Token.
   * Das kurzlebige Medien-Token ist auf die einmalige Verwendung beschränkt und wird nie zwischengespeichert. Er wird jedes Mal, wenn eine Autorisierungs-API aufgerufen wird, vom Adobe Primetime-Authentifizierungsserver abgerufen.

### Token-Speicher {#token-storage}

Der Access Enabler speichert langlebige Token (AuthN und AuthZ) an Orten, die für die jeweilige Umgebung spezifisch sind:

* **Flash 10.1** (oder höher): Die langlebigen Token werden als lokale freigegebene Objekte gespeichert.
* **HTML5**: Die langlebigen Token werden sicher im lokalen Speicher des HTML5-Browsers aufbewahrt.
* **iOS**: Die langlebigen Token werden auf einer beständigen Zwischenablage gespeichert, auf der sie von anderen Adobe Primetime-Authentifizierungs-Client-Anwendungen aufgerufen werden können.
* **Android**: Die langlebigen Token werden in einer freigegebenen Datenbankdatei gespeichert, auf die andere Adobe Primetime-Authentifizierungs-Client-Anwendungen zugreifen können.
* **Clientlose API-Geräte**: Token werden auf den Primetime-Authentifizierungsservern gespeichert.

### Token-Sicherheit {#token-security}

Der Adobe Primetime-Authentifizierungsserver signiert alle langlebigen Token digital mit der Geräte-ID (abgeleitet aus den Hardwareeigenschaften des Geräts). Die digitale Signatur unterscheidet sich je nach Umgebung in ihrer Erstellung, ihrem Schutz und ihrer Validierung:

* **Flash 10.1** (oder höher) - Die Geräte-ID basiert auf der Geräteberechtigung, einem eindeutigen Zertifikat, das vom Adobe Individualization Server ausgestellt wurde. Diese Sicherheit entspricht der FAXS DRM-Technologie. Bei dieser serverseitigen Validierung wird die eindeutige Geräte-ID im Token mit der Geräteberechtigung verglichen (die sicher vom Flash Player an die Adobe Primetime-Authentifizierung übermittelt wird). Die Geräteberechtigung gibt auch die FAXS-Clientversion und die Flash Player- (oder AIR-) Version an, für die sie ausgestellt wurde. Die Gerätebindung ist stärker als bei HTML5, daher ist die Time-to-Live (TTL) für Token normalerweise länger mit Flash.
* **HTML5** - Das Gerät wird clientseitig individualisiert. Es verwendet über JavaScript verfügbare Eigenschaften, um eine Pseudo-Geräte-ID zu generieren, die Browser- und Betriebssystemversionen, eine IP-Adresse und eine GUID für Browsercookie (global eindeutige Kennung) enthält. Diese Token-Geräte-ID wird mit der aktuellen Pseudo-Geräte-ID für das Gerät verglichen. Da sich die IP-Adresse während der normalen Verwendung ändern kann, speichert die Adobe Primetime-Authentifizierung HTML5-Token an zwei Stellen: localStorage und sessionStorage. Wenn sich die IP ändert und das sessionStorage-Token ansonsten weiterhin gültig ist, wird die Sitzung beibehalten. Bei HTML5 ist die Gerätebindung nicht so stark, daher ist die TTL für Token in der Regel kleiner als für Flash.
* **Native Clients** (iOS und Android) - Die langlebigen Token enthalten native ID-Individualisierungsinformationen für Geräte und sind daher an das anfordernde Gerät gebunden. Die Authentifizierungs- und Autorisierungsanfragen werden über HTTPS gesendet und die Geräte-ID-Informationen werden digital von der Access Enabler-Bibliothek signiert, bevor sie an die Backend-Server gesendet werden. Auf der Serverseite werden die Geräte-ID-Informationen anhand der zugehörigen digitalen Signatur validiert.
* **Clientlose API-Clients** - Die ClientLess-API-Lösung verfügt über eine Reihe von Sicherheitsprotokollen, die das digitale Signieren aller API-Aufrufe beinhalten. Während der Berechtigungsflüsse generierte Token werden sicher auf den Adobe Primetime-Authentifizierungsservern gespeichert.

Die Adobe Primetime-Authentifizierung validiert jedes langlebige Token, um sicherzustellen, dass das Gerät, das auf den Inhalt zugreift, mit dem Gerät übereinstimmt, das das Token ausgegeben hat. Bei allen Token stellt eine clientseitige Validierung sicher, dass die digitale Signatur intakt ist und dass die Integrität des Tokens erhalten bleibt. Wenn die Überprüfung der Geräte-ID fehlschlägt, wird die Authentifizierungssitzung ungültig gemacht und der Benutzer wird aufgefordert, sich erneut anzumelden, wodurch die Token zurückgesetzt werden.

### Token-Freigabe {#token-sharing}

Anwendungen auf verschiedenen Plattformen verwenden keine Token. Hierfür gibt es eine Reihe von Gründen, darunter die folgenden:

* Wie unter [Token-Speicher](#token-storage)festgelegt ist, variiert die Methode zum Speichern von Token zwischen verschiedenen Plattformen (z. B. &quot;Lokale freigegebene Objekte für Flash&quot;, &quot;WebStorage für JavaScript&quot;).
* Der Grad der Token-Sicherheit unterscheidet sich zwischen Plattformen. Beispielsweise sind Flash-Token mit FAXS stark an ein Gerät gebunden. Token in einer reinen JavaScript-Umgebung verfügen nicht über die gleiche DRM-Unterstützung wie in Flash.  Die Freigabe von JS-Token für Flash-Anwendungen würde die Wahrscheinlichkeit verringern, dass weniger sichere Token eine sicherere Umgebung nutzen.

## Lebenszyklus der Programmierintegration {#prog-integ-lifecycle}

![](assets/progr-flow-int-lifecycle.png)

*Abbildung: Integrieren der Authentifizierung mit der Website und Anwendung des Programmierers*


## Logische Flüsse {#logical-flows}

### Entitäts-Flussdiagramm {#chart}

Das folgende Flussdiagramm zeigt den Gesamtprozess der Bestätigung der Berechtigung (mithilfe der Client-Komponente Adobe Primetime Authentication Access Enabler ):

![](assets/ent-flowchart.png)

*Abbildung: Verfahren zur Bestätigung der Berechtigung*

### Authentifizierungsschritte {#authn-steps}

Die folgenden Schritte zeigen ein Beispiel für den Authentifizierungsfluss der Adobe Primetime-Authentifizierung.  Dies ist der Teil des Berechtigungsprozesses, bei dem ein Programmierer feststellt, ob der Benutzer ein gültiger Kunde eines MVPD ist.  In diesem Szenario ist der Benutzer ein gültiger Abonnent eines MVPD.  Der Benutzer versucht, geschützte Inhalte mithilfe der Flash-Anwendung eines Programmierers anzuzeigen:

1. Der Benutzer besucht die Webseite des Programmierers, auf der die Flash-Applikation des Programmierers und die Adobe Primetime Authentication Access Enabler-Komponenten auf den Computer des Benutzers geladen werden. Die Flash-Anwendung verwendet Access Enabler, um die Identifizierung des Programmierers mit der Adobe Primetime-Authentifizierung festzulegen, und die Adobe Primetime-Authentifizierung nutzt den Access Enabler mit Konfigurations- und Statusdaten für diesen Programmierer (den &quot;Anforderer&quot;). Der Access Enabler muss diese Daten vom Server empfangen, bevor er andere API-Aufrufe durchführt. Technische Anmerkung: Der Programmierer legt seine Identität mit dem Access Enabler fest. `setRequestor()` Methode; Weitere Informationen finden Sie unter [Handbuch zur Programmierintegration](/help/authentication/programmer-integration-guide-overview.md).
1. Wenn der Benutzer versucht, den geschützten Inhalt des Programmierers anzuzeigen, zeigt die Programmer-Anwendung dem Benutzer eine Liste von MVPDs an, aus denen der Benutzer einen Anbieter auswählt.
1. Der Benutzer wird an einen Adobe Primetime-Authentifizierungsserver weitergeleitet, wo ein verschlüsselter [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) -Anfrage für den vom Benutzer ausgewählten MVPD erstellt. Diese Anfrage wird als Authentifizierungsanfrage im Namen des Programmierers an den MVPD gesendet. Je nach System des MVPD wird der Browser des Benutzers dann entweder zur MVPD-Site weitergeleitet, um sich anzumelden, oder ein Anmelde-iFrame wird in der App des Programmierers erstellt.
1. In beiden Fällen (Umleitung oder iFrame) akzeptiert der MVPD die Anfrage und zeigt die Anmeldeseite an.
1. Der Benutzer meldet sich mit dem MVPD an, der MVPD validiert den Status des Benutzers als zahlender Kunde und dann erstellt der MVPD seine eigene HTTP-Sitzung.
1. Wenn der Benutzer validiert wird, erstellt der MVPD eine Antwort (SAML und verschlüsselt), die der MVPD an die Adobe Primetime-Authentifizierung zurücksendet.
1. Die Adobe Primetime-Authentifizierung erhält die MVPD-Antwort, erkennt, dass eine Adobe Primetime-Authentifizierungs-HTTP-Sitzung geöffnet ist, validiert die SAML-Antwort vom MVPD und leitet zurück zur Programmer-Site.
1. Die Seite des Programmierers wird neu geladen, der Access Enabler wird neu geladen und der Programmierer ruft erneut setRequestor() auf.  Der zweite Aufruf von setRequestor() ist erforderlich, da die aktuelle Konfiguration geändert wurde. Es ist jetzt eine Markierung vorhanden, die den Access Enabler informiert, dass ein AuthN-Token auf dem Server auf die Generierung wartet.
1. Der Access Enabler erkennt, dass eine ausstehende Authentifizierung vorliegt, und fordert das Token vom Adobe Primetime-Authentifizierungsserver an. Das Token wird vom Server abgerufen, indem die DRM-Funktionen des Flash Players aufgerufen werden.
1. Das AuthN-Token wird im LSO-Cache des Flash Players des Programmierers gespeichert. Die Authentifizierung ist jetzt abgeschlossen und die Sitzung wird auf dem Adobe Primetime-Authentifizierungsserver zerstört.

### Autorisierungsschritte {#authz-steps}

Die folgenden Schritte werden von der [Authentifizierungsschritte](#authn-steps):

1. Wenn der Benutzer versucht, auf den geschützten Inhalt des Programmierers zuzugreifen, sucht die Anwendung des Programmierers zunächst auf dem lokalen Computer oder Gerät des Benutzers nach einem AuthN-Token.  Wenn dieses Token nicht vorhanden ist, wird die [Authentifizierungsschritte](#authn-steps) oben genannten Werte folgen.  Wenn das AuthN-Token vorhanden ist, wird der Autorisierungsfluss mit der Anwendung des Programmierers fortgesetzt, die einen Aufruf an den Access Enabler mit einer Anfrage zum Abrufen der Anzeigerechte des Benutzers für ein bestimmtes Element geschützter Inhalte initiiert.
1. Das spezifische Element geschützter Inhalte wird durch eine &quot;Ressourcen-ID&quot;dargestellt.  Dies kann eine einfache Zeichenfolge oder eine komplexere Struktur sein, aber in jedem Fall wird die Art der Ressourcenkennung im Voraus zwischen dem Programmierer und dem MVPD vereinbart.  Die Anwendung des Programmierers übergibt die Kennung der Ressource an den Access Enabler.  Der Access Enabler sucht auf dem lokalen Computer oder Gerät des Benutzers nach einem AuthZ-Token.  Wenn das AuthZ-Token nicht vorhanden ist, übergibt der Access Enabler die Anfrage an den Backend-Adobe Primetime-Authentifizierungsserver.
1. Der Adobe Primetime-Authentifizierungsserver kommuniziert mithilfe standardisierter Protokolle mit dem MVPDs-Autorisierungsendpunkt.  Wenn die Antwort des MVPD anzeigt, dass der Benutzer berechtigt ist, den geschützten Inhalt anzuzeigen, erstellt der Adobe Primetime-Authentifizierungsserver ein AuthZ-Token und gibt es an den Access Enabler weiter, der das AuthZ-Token auf dem Computer des Benutzers speichert.
1. Wenn ein AuthZ-Token auf dem Computer oder Gerät des Benutzers gespeichert ist, ruft die Anwendung des Programmierers den Access Enabler auf, um ein Media Token vom Adobe Primetime-Authentifizierungsserver abzurufen, und stellt dieses Token für die Anwendung des Programmierers bereit.
1. Schließlich verwendet die Anwendung des Programmierers die Komponente Media Token Verifier , um zu bestätigen, dass der richtige Benutzer den richtigen Inhalt anzeigt, und mit dem vorhandenen Media Token kann der Benutzer den geschützten Inhalt anzeigen.


## Registrierung und Initialisierung {#reg-and-init}

Der erste Schritt bei der Arbeit mit der Adobe Primetime-Authentifizierung besteht darin, sich bei Adobe oder einem für die Adobe Primetime-Authentifizierung autorisierten Partner zu registrieren.

Bei der Registrierung geben Sie eine Liste der Domänen an, von denen Sie mit der Adobe Primetime-Authentifizierung kommunizieren. Die Turner Broadcasting System-Domänen umfassen beispielsweise tbs.com und tnt.tv als Adobe Primetime-authentifizierungsregistrierte Domänen. Jede dieser Inhalts-Sites erhält Zugriff auf die Adobe Primetime-Authentifizierung und erhält eine eigene Anforderungs-ID (z. B. &quot;TBS&quot;und &quot;TNT&quot;). Wenn Sie sich dafür entscheiden, weitere Sites hinzuzufügen, müssen Sie die Adobe über die zusätzlichen Domänennamen informieren, damit sie in die Liste der zulässigen Domänen aufgenommen werden, und zusätzliche Anforderer-IDs erhalten.

>[!WARNING]
>
>Stellen Sie beim Testen Ihrer Integration sicher, dass sich Ihr Testserver in einer registrierten Domäne befindet, die Sie in der Produktion verwenden möchten. Anforderungen, auch Testanforderungen, die von Domänen stammen, die nicht auf der Whitelist stehen, werden ignoriert. Wenn Sie beispielsweise die Verwendung von domain.com in der Produktion angefordert haben, stellen Sie sicher, dass Sie Ihre Testintegration unter domain.com, test.domain.com und staging.domain.com bereitstellen.
>
>Anforderungen, die Benutzernamen und/oder Kennwort in der URL enthalten, werden ignoriert, selbst wenn Domänen auf der Whitelist stehen. Beispiel: `//username@registered-domain/`

Die Anforderer-ID identifiziert den Client des Programmierers in allen Kommunikationen mit der Client-Komponente Access Enabler der Adobe Primetime-Authentifizierung eindeutig. Alle statischen Adobe Primetime-Authentifizierungsdaten, die mit dem Programmierer verknüpft sind, werden dieser ID zugewiesen.

>[!TIP]
>
>Zusätzlich zu Ihrer Anforderer-ID erhalten Sie bei der Registrierung auch funktionale URLs für die Client-Komponente Access Enabler und den Media Token Verifier.

## Integrationsschritte {#integration-steps}

>[!TIP]
>
>Wenn Sie das Open Source Media Framework der Adobe (&quot;OSMF&quot;) für Ihre Medienplayer-Entwicklung verwenden, besteht die schnellste Möglichkeit zur Verwendung der Adobe Primetime-Authentifizierung darin, das OSMF-Plug-in zu integrieren *(Veraltet)* in den Code Ihres Spielers ein.
>
><!--For details, see [Adobe Primetime authentication Plugin For OSMF](https://tve.helpdocsonline.com/9-2-2) in the Programmer Integration Guide.-->

1. [Request-Einrichtung](#requestor)
1. [Umgang mit Authentifizierung und Autorisierung](#authn-authz)
1. [Unterstützende einmalige Abmeldung](#ssl)

### 1. Einrichtung des Anforderers {#requestor}

#### 1a. Registrieren bei der Adobe

Zunächst müssen Sie sich bei Adobe oder einem autorisierten Adobe Primetime-Authentifizierungspartner registrieren.  Bei der Registrierung erhalten Sie eine oder mehrere globale eindeutige Kennungen (GUIDs). Jede ausgestellte GUID ist mit einer Domäne verknüpft, von der aus der Zugriff auf die Adobe Primetime-Authentifizierung möglich ist. Sie übergeben eine GUID (die Anforderer-ID) für die anfordernde Domäne, um Ihre Identität für jede Sitzung zu registrieren, in der Sie mit dem Access Enabler interagieren. Weitere Informationen finden Sie unter [Registrierung und Initialisierung](#reg-and-init) im Integrationsleitfaden für Programmierer.

#### 1b. Integration von Initial Access Enabler

Der nächste Schritt besteht darin, den Access Enabler in Ihre vorhandene Medienplayer-App oder -Webseite zu integrieren:

* Sie können die Flash-Version einbetten, `AccessEnabler.swf`, in einen Flash-basierten Videoplayer einbetten, oder Sie können ihn direkt in die HTML Ihrer Web-Seite einbetten. Sie können mit dem Access Enabler-SWF entweder in ActionScript oder JavaScript kommunizieren. Die Basis-API ist ActionScript, aber wenn Sie es vorziehen, mit JavaScript zu arbeiten, steht eine vollständige Wrapper-Bibliothek zur Verfügung, die in Ihre Seiten aufgenommen werden kann.
* Bei Nicht-Flash-Umgebungen haben Sie folgende Möglichkeiten:
   * Verwenden Sie die HTML5/JavaScript-Version AccessEnabler.js und kommunizieren Sie mit ihr über die JavaScript-API.
   * Verwenden Sie die native AIR-Erweiterung für die Adobe Primetime-Authentifizierung, um nativen Code mit integrierten ActionScript-Klassen zu kombinieren.
   * Verwenden Sie eine der nativen Clientversionen der Access Enabler Library (iOS oder Android).

### 2. Umgang mit Authentifizierung und Autorisierung {#authn-authz}

#### 2a. Kommunikation mit dem Access Enabler

Die Kommunikation zwischen dem Access Enabler und Ihrer Web- oder Player-App ist asynchron. Ihre Anwendung ruft Access Enabler-Methoden auf und der Access Enabler antwortet über Callbacks, die Sie bei der Access Enabler-Bibliothek registrieren.

* Wenn Ihre Anwendung eine Autorisierungsanfrage stellt, initiiert der Access Enabler automatisch eine Authentifizierungsanfrage, wenn sich ein gültiges AuthN-Token noch nicht im lokalen System befindet. Wenn die Authentifizierung erfolgreich ist, wird das AuthN-Token des Benutzers lokal gespeichert, sodass er sich nicht erneut anmelden muss. Wenn sie sich erfolgreich über Adobe Primetime-Authentifizierung in einem anderen Kontext authentifiziert haben (z. B. über die MVPD-Website oder mit einem anderen Programmierer), hat der Access Enabler Zugriff auf das lokale AuthN-Token und eine zusätzliche Authentifizierung ist nicht erforderlich.
* Wenn ein Benutzer versucht, auf Ihren geschützten Inhalt zuzugreifen, senden Sie eine Autorisierungsanfrage an den Access Enabler. Nach der Überprüfung (oder Initiierung) der Authentifizierung kontaktiert der Access Enabler den MVPD (über den Adobe Primetime-Authentifizierungsserver), um festzustellen, ob der Kunde berechtigt ist, den geschützten Inhalt anzuzeigen. Ihre Anwendung muss nur die Anfrage an den Access Enabler senden und dann die Antwort verarbeiten (Autorisierungserfolg oder -fehler). Wenn die Autorisierung erfolgreich ist, wird ein AuthZ-Token auf dem Clientsystem gespeichert.  Schließlich erhält Ihre Anwendung ein kurzlebiges Medien-Token zur Verwendung in Ihrem eigenen Genehmigungsverfahren.

>[!NOTE]
>
>* Die Authentifizierung erfolgt als SAML-Austausch zwischen der Adobe Primetime-Authentifizierung als Service Provider (SP) und dem MVPD als Identitäts-Provider (IdP).
>
>* Die Autorisierung verwendet einen Back-Channel-Webdienstaustausch (Server-zu-Server) zwischen der Adobe Primetime-Authentifizierung (SP) und einem MVPD (IdP).



#### 2b. Bereitstellen einer Entitäts-Benutzeroberfläche {#entitlement-ui}

Sie stellen eine eigene Benutzeroberfläche für den Benutzerzugriff auf Ihre Inhalte bereit. Einige Elemente, wie der eigentliche Anmeldeprozess, werden vom MVPD bereitgestellt und einige Elemente sind optional als Teil der Adobe Primetime-Authentifizierung verfügbar. Führen Sie mindestens die folgenden Schritte aus:

* **Implementieren einer MVPD-Auswahlschnittstelle, über die ein neuer Benutzer seinen MVPD identifizieren und sich zum ersten Mal anmelden kann**. Für die Entwicklung bietet der Access Enabler eine einfache Benutzeroberfläche, über die der Kunde MVPDs auswählen und den Anmeldeprozess starten kann. Für die Produktion müssen Sie Ihr eigenes MVPD-Auswahldialogfeld implementieren. Einige MVPDs leiten zur Anmeldung zu ihrer eigenen Site um und einige verlangen, dass ihre Anmeldeseiten in einem iFrame angezeigt werden. Sie müssen einen Callback implementieren, der diesen iFrame erstellt, um die Fälle zu verarbeiten, in denen der MVPD des Benutzers seine Anmeldeseite in einem iFrame anzeigt.
* **Ermitteln geschützter Inhalte**. Für geschützten Inhalt ist eine Zugriffsberechtigung erforderlich. Auf Ihrer Benutzeroberfläche sollte angegeben werden, welcher Inhalt geschützt ist und welcher Inhalt autorisiert wurde.  Der Autorisierungsstatus wird häufig mit den Symbolen &quot;entsperrt&quot;und &quot;gesperrt&quot;angezeigt.
* **Anzeigen der Authentifizierung eines Benutzers**. Sie sollten den Authentifizierungsstatus eines Benutzers im Rahmen beliebiger Methoden zur Identifizierung geschützter Inhalte angeben. Sie können den Access Enabler abfragen, um festzustellen, ob der Kunde bereits authentifiziert wurde.

#### 2c. Integrieren des Medien-Token-Verifikators {#int-media-token-ver}

Sie müssen die Komponente Adobe Primetime Authentication Media Token Verifier in Ihren Medienserver integrieren.  Dadurch kann Ihr vorhandener Token-Prüfer die kurzlebigen Media-Token erkennen, die von der Adobe Primetime-Authentifizierung mit einer erfolgreichen Autorisierung bereitgestellt werden. Der Media Token Verifier überprüft die Medien-Token als letzten Sicherheitsschritt, bevor Sie dem Benutzer Zugriff auf geschützte Inhalte gewähren. Sie erhalten den Speicherort, von dem Sie den Media Token Verifier herunterladen können, wenn Sie sich bei Adobe registrieren.

### 3. Unterstützung der einmaligen Abmeldung {#ssl}

In den meisten Fällen ist Ihr Medienplayer für die Handhabung von Benutzerabfragen über eine einfache Access Enabler API verantwortlich. Wenn Sie logout() aufrufen, führt der Access Enabler Folgendes aus:

* Melden Sie den aktuellen Benutzer ab
* Löscht alle Authentifizierungs- und Autorisierungsinformationen für den abgemeldeten Benutzer
* Löscht alle AuthN- und AuthZ-Token aus dem lokalen System des Benutzers

Wenn der Benutzer seinen Computer so lange im Leerlauf lässt, dass seine Token ablaufen, kann der Benutzer dennoch zur Sitzung zurückkehren und die Abmeldung erfolgreich starten. Die Adobe Primetime-Authentifizierung stellt sicher, dass alle Token gelöscht werden, und benachrichtigt den MVPD, auch ihre Sitzung zu löschen.

Wenn die Abmeldung von einer Site initiiert wird, die nicht in die Adobe Primetime-Authentifizierung integriert ist, kann der MVPD den Adobe Primetime-Authentifizierungsdienst für die einmalige Abmeldung über einen Browser-Umleitung aufrufen.

## Grundlegendes zu Benutzer-IDs {#user-ids}

Grundsätzlich ist jeder Benutzer, der einen Berechtigungsfluss initiiert, einer einzelnen eindeutigen Benutzer-ID zugeordnet.  Im Zuge eines Berechtigungsflusses kann jedoch eine Benutzer-ID auf unterschiedliche Weise angezeigt werden, je nachdem, von welcher API Sie die ID erhalten.

Die sessionGUID im Short Media Token ist die sichere Form der UserID, die über den sendTrackingData() -Aufruf verfügbar ist.   In allen aktuellen Integrationen ist dies eine beständige GUID für den Benutzer über Zeit und Geräte hinweg, aber die Quelle der GUID beginnt mit der UserID in der SAML-Antwort vom MVPD.   Einige MVPDs könnten sich jedoch in Zukunft anders entscheiden und eine vorübergehende GUID senden.  Wenn ein Programmierer sicherstellen möchte, dass die MVPD-Quell-UserID in der AuthN-Antwort persistent ist, sollte er dies in seinen Vereinbarungen mit MVPDs anordnen.

Im Folgenden finden Sie die verschiedenen Möglichkeiten, wie die Benutzer-ID in den Adobe Primetime-Authentifizierungs-APIs dargestellt wird:

* `sendTrackingData()` GUID-Eigenschaft - Dies ist die Adobe-Hash-Version der MVPD UserID.  Es wird gehasht, sodass diese Benutzer-ID nicht von der MVPD an die Quelle zurückverfolgt werden kann.   Diese ID ist eindeutig und in der Regel persistent, kann jedoch nicht mit dem MVPD geteilt werden, um das spezifische Nutzungsverhalten mit dem zu vergleichen, was MVPDs auf ihrer Seite haben.   Es ist nicht digital unterzeichnet, daher nicht unbeschädigt für die Betrugsbekämpfung, aber es ist gut genug für Analysen.  Dieses Formular der Benutzer-ID wird clientseitig für alle Ereignisse bereitgestellt, die die Adobe Primetime-Authentifizierung im AuthN/AuthZ-Fluss generiert.
* Kurzmedien-Token `sessionGUID` property - Dies entspricht der UserID via `sendTrackingData()`, aber diese ist digital signiert, um ihre Integrität zu schützen.  Dadurch ist dieser Wert ausreichend für die Verfolgung von Betrug bei gleichzeitiger Nutzung. Er soll nach Verwendung unserer Validator-Bibliothek serverseitig verarbeitet werden und kann auf Betrugsmuster analysiert werden, bevor der Video-Stream an den Client freigegeben wird.  Die Durchführung dieser Aufgaben obliegt dem Programmierer.
* `getMetadata() userID `-Eigenschaft - Diese Eigenschaft ermöglicht es Adobe, die eigentliche MVPD UserID-Quell-ID für den Programmierer verfügbar zu machen. Sie wird mit dem öffentlichen Schlüssel aus dem Zertifikat, das wir vom Programmierer haben, verschlüsselt, sodass sie dem Client nicht im Klartext angezeigt wird. Dadurch erhält der Programmierer die eigentliche UserID aus dem MVPD, also kann sie direkt mit dem MVPD für die Kontoverknüpfung oder Betrugsuntersuchung verwendet werden.

**In der Schlussfolgerung**

* Die MVPD-Benutzer-ID ist eine allgemeine, aber nicht garantierte, beständige eindeutige ID, die **aus den MVPDs generiert und bei erfolgreicher Authentifizierung an Adobe übergeben werden**. Es ist im Allgemeinen in allen Netzwerken mit einigen Ausnahmen konsistent.
* Die MVPD-Benutzer-ID enthält keine personenbezogenen Daten und ist KEINE Kontonummer. Es muss nicht in verschlüsselter Form offen gelegt werden, da wir mit allen MVPDs überprüft haben, dass keine PII gesendet werden.


Wie Sie die Benutzer-ID verwenden, hängt vom Anwendungsfall ab:

* Wenn Sie es für Tracking/Analysen benötigen, ist es am praktischsten, es von `sendTrackingData()`.
* Wenn Sie es Server-seitig für Stream-Veröffentlichung, Betrug oder operative Daten benötigen, können Sie es vom Media Token Validator abrufen.
* Wenn Sie es für Kontoverknüpfung und tieferen Betrug benötigen, wenden Sie sich an Ihren Ansprechpartner bei der Adobe.

<!--
>[!RELATEDINFORMATION]
>
>* **Kickstart Guides** These guides explain the initial steps to take once you have decided to begin integrating with Adobe Primetime authentication.
>* **Programmer Integration Guide** This is a lower level technical guide for Programmers, directed primarily to the software engineers who code and test the applications and systems involved in the integration.
>* [Overview For MVPDs](/help/authentication/mvpd-overview.md) This provides a similar level of conceptual information as in this Programmer overview, but is directed toward MVPDs.
-->