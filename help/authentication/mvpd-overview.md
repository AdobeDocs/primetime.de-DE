---
title: Übersicht über MVPDs
description: Übersicht über MVPDs
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2736'
ht-degree: 0%

---

# Überblick über MVPDs {#mvpd-overview}

>[!NOTE]
>
>Der Inhalt dieser Seite dient nur Informationszwecken. Für die Verwendung dieser API ist eine aktuelle Lizenz von Adobe erforderlich. Eine unbefugte Anwendung ist nicht zulässig.

## Einführung {#intro}

Diese Übersicht ist für Multi-Channel Video Programming Distributors (MVPDs) gedacht. Weitere Dokumentationen, einschließlich Schnellstart- und Integrationsleitfäden, finden Sie im Abschnitt &quot;Verwandte Informationen&quot;am Ende dieses Dokuments.



TV Anywhere (TVE) ist die inzwischen bekannte Branchenbewegung, die es Pay-TV-Abonnenten ermöglicht, auf den Inhalten zuzugreifen, für die sie bereits bezahlt haben, und zwar auf mehreren Geräten, sowohl zu Hause als auch außerhalb.  Für Pay TV-Anbieter schafft TVE neue Möglichkeiten, sowohl bestehende Kundenbeziehungen zu wahren als auch neue zu ermöglichen. Doch zusammen mit diesen Möglichkeiten ergeben sich Herausforderungen. In der TVE-Landschaft stellen Programmierer den Inhalt bereit, aber die MVPDs enthalten die Kundeninformationen, um zu überprüfen, ob potenzielle Betrachter gültige Abonnenten sind.



Die Koordination von Viewer-Authentifizierung und -Autorisierung mit einem Programmierer kann einfach sein, aber die Koordination mit Dutzenden oder Hunderten von verschiedenen Programmierern wird immer komplexer. Mit Adobe® Pass müssen MVPDs jedoch nur eine einzige, einfache Integration implementieren, um Zugriff auf das gesamte TVE-Ökosystem zu erhalten, einschließlich Programmierern wie NBCUniversal Media, Turner Broadcasting (TBS, TNT, CNN), Fox Broadcast Networks, Hulu usw.  Die Adobe Primetime-Authentifizierung bietet ein Integrations-Framework, mit dem sich die Benutzerberechtigungen einfach und sicher bestimmen lassen.



Unterste Zeile: Die Adobe Primetime-Authentifizierung vermittelt sicher Berechtigungstransaktionen zwischen Programmierern und MVPDs, wodurch der Viewer-Zugriff auf Abonnementinhalte erleichtert wird. Mit anderen Worten: Die Adobe Primetime-Authentifizierung erleichtert und erleichtert den richtigen Kunden den Zugriff auf die richtigen Inhalte.


Mit Adobe Primetime-Authentifizierung erhalten MVPDs:

Einfache Integration mit Programmierern.  Mit einer einzigen Integration können Sie sofort Konnektivität von mehreren Inhaltseigentümern bereitstellen.

Verbesserte Kundeninteraktion.  Unterstützung für ein reibungsloses Branding-Erlebnis, da Ihre Kunden Inhalte auf mehreren Plattformen und Geräten anzeigen.

Sichere Authentifizierung.  Stellen Sie sicher, dass nur autorisierte Benutzer und Geräte Zugriff auf Premium-Inhalte erhalten, und beschränken Sie (optional) die Anzahl der Geräte und gleichzeitigen Streams, die pro Haushaltskonto eine Verbindung herstellen können.

## FAQs {#faq}

Wie sicher ist die Adobe Primetime-Authentifizierung? Die oberste Priorität der Adobe Primetime-Authentifizierungsarchitektur besteht darin sicherzustellen, dass nur autorisierte Viewer authentifiziert werden und Zugriff auf Premium-Inhalte erhalten. Die Adobe Primetime-Authentifizierung bindet den Zugriff eng an Anzeigegeräte und kann dazu beitragen, Streams, Sitzungen und/oder Geräte für einen bestimmten Haushalt zu begrenzen.


Ist Flash Player erforderlich? Adobe Primetime-Authentifizierung für TV Anywhere ist Player- und plattformunabhängig und wird in beliebige Wiedergabeanwendungen integriert, einschließlich Silverlight und HTML5. Darüber hinaus bietet die Adobe Primetime-Authentifizierung native Unterstützung für Geräte wie Smartphones und Tablets mit iOS und Android.


Welche Geräte unterstützt die Adobe Primetime-Authentifizierung? Die Adobe Primetime-Authentifizierung wird von praktisch jedem Gerät mit dem HTML5-Webkit für die Anzeige im Browser unterstützt. Darüber hinaus werden bei der Adobe Primetime-Authentifizierung weiterhin native Software Development Kits (SDKs) für verschiedene gerätespezifische Plattformen eingeführt, darunter iOS-, Android™-, Xbox360- (nicht mehr unterstützt) und Adobe Air®-Anwendungen (nicht mehr unterstützt). Zuletzt wurde bei der Adobe Primetime-Authentifizierung eine clientlose Lösung für Geräte entwickelt, die keine Browser-Seiten rendern können (z. B. Smart-TVs, Set-Top-Boxen und Spielekonsolen).  Die Möglichkeit, Browserseiten zu rendern, ist eine Voraussetzung für die Authentifizierung von Benutzern mit MVPDs.


Unterstützt die Adobe Primetime-Authentifizierung die neuen Standards für Fernsehen überall? Die Adobe Primetime-Authentifizierung entspricht der Spezifikation CableLabs OLCA (Online Content Access), die technische Anforderungen und Architekturmerkmale für die Bereitstellung von Videos von Online-Quellen an einen Pay TV-Kunden bietet. Adobe nahm im Juni 2011 am gemeinsamen CableLabs-Interopt-Test-Projekt teil und hat den Testprozess für eine Service Provider-Implementierung bestanden. Die Adobe Primetime-Authentifizierung wird anhand der OLCA-Spezifikationen für die Authentifizierung überprüft (abgeschlossen und getestet). Die Autorisierungskomponente ist abgeschlossen, aber die Testprüfung wartet derzeit auf die Veröffentlichung der CableLabs-Testumgebung. Adobe ist auch ein aktives Mitglied des OATC (Open Authentication Technical Consortium) und nimmt an mehreren der von den Unterausschüssen im Rahmen dieses Gremiums durchgeführten Projekte zur Ausarbeitung von Spezifikationen teil.



Was ist Authentifizierung? Authentifizierung ist der Prozess, bei dem ein MVPD bestätigt, dass ein bestimmter Benutzer ein bekannter Kunde ist.



Was ist Autorisierung? Autorisierung ist der Prozess, bei dem ein MVPD bestätigt, dass ein authentifizierter Benutzer über ein gültiges Abonnement für eine bestimmte Ressource verfügt.



## Architektur {#architecture}

Die Adobe Primetime-Authentifizierung ist ein gehosteter Dienst, der eine schnelle Back-End-Integration (Server-zu-Server) ermöglicht, die auf den Geschäftsregeln basiert, die sowohl von MVPDs als auch von Programmierern benötigt werden. Dies bedeutet eine schnelle Markteinführung für alle Parteien, ein sichereres Umfeld zur Betrugsbekämpfung und eine bessere Kundenerfahrung, bei der mehr TV-Inhalte für mehr Menschen auf mehr Plattformen verfügbar sind.


Die Adobe Primetime-Authentifizierung erfolgt über das SaaS-Modell (Software as a Service) und ermöglicht eine sicherere Kommunikation zwischen Endbenutzern, MVPDs und Programmierern, um die Berechtigung für Inhalte zu überprüfen. Die Kernkomponenten des Dienstes umfassen Folgendes:

Server-seitig - Der gehostete Adobe Primetime-Authentifizierungsserver. Dies ist ein Anwendungsserver, der eine Back-Channel-Kommunikation (Server-zu-Server) mit den Authentifizierungssystemen von MVPDs durchführt.
Client-seitig: Der Client-seitige Access Enabler - Der Access Enabler ist eine kleine Datei, die in die Web-Seite oder Player-Anwendung eines Programmierers geladen wird. Es stellt Berechtigungs-APIs für die Inhaltsanzeigeanwendung des Programmierers bereit und kommuniziert mit dem Adobe Primetime-Authentifizierungsserver.
Clientlose Webdienste (für nicht webfähige Geräte) - RESTful-Webdienste, die Berechtigungs-APIs für Geräte wie Smart-TVs, Spielekonsolen und Set-Top-Boxen bereitstellen.

>[!NOTE]
>
>Als MVPD müssen Ihre Webdienste in der Lage sein, Authentifizierungs- und Autorisierungsanfragen von der Adobe Primetime-Authentifizierung zu erkennen und mit den erforderlichen Daten im erwarteten Format zu reagieren.
>

Mit der Adobe Primetime-Authentifizierung können Sie Kunden eine Federated Identity Management (SSO)-Authentifizierung und -Autorisierung bereitstellen. Mit der Adobe Primetime-Authentifizierung müssen sich Abonnenten nach ihrer ersten Authentifizierung nicht erneut anmelden, solange diese Authentifizierung vom MVPD beibehalten werden kann. (In der Regel 30 Tage.) Dazu bietet die Adobe Primetime-Authentifizierung eine gemeinsame Domäne für Authentifizierungstoken für unsere Kunden. Diese Authentifizierungsstatusinformationen stehen allen teilnehmenden Sites zur Verfügung, die in einen bestimmten MVPD integriert sind.


Derzeit verwenden die meisten Adobe Primetime-Authentifizierungsintegrationen mit MVPDs das SAML-Protokoll, eines der primären Authentifizierungsstandards. Die Adobe Primetime-Authentifizierung fungiert in der SAML-Architektur als Proxy Service Provider und behält die SAML-Authentifizierungsantwort als sicheres Token in der gemeinsamen Adobe-Domäne bei. Die Adobe Primetime-Authentifizierung ist SAML 2.0-kompatibel. Während die Adobe Primetime-Authentifizierung derzeit jedoch in der Regel mit SAML SSO-Lösungen verwendet wird, ist die Adobe Primetime-Authentifizierungsarchitektur an kein bestimmtes Protokoll gebunden. Daher kann die Unterstützung für neue Protokolle - z. B. auf Basis von OAuth 2.0 oder benutzerdefinierten Protokollen - im Laufe der Zeit hinzugefügt werden.


Adobe arbeitet mit dem technischen Team eines MVPD zusammen, um die Adobe Primetime-Authentifizierung so zu konfigurieren, dass die Anforderungen vorhandener Integrationen erfüllt werden. Die Integration von MVPDs ist kostenlos, vorausgesetzt, die Integration erfolgt standardmäßig und erfordert minimalen Support (Dokumentation und grundlegende E-Mail-Unterstützung). Wenn ein MVPD umfangreiche Unterstützung oder eine eskalierte Zeitleiste erfordert, kann eine Supportgebühr erhoben werden oder der Provider möchte mit einem Dritten zusammenarbeiten, der mit unserer Lösung wie Synacor vertraut ist.


Die Adobe Primetime-Authentifizierung unterstützt auch die effiziente Handhabung der MVPD-Geschäftslogik wie folgt:

Für eigenständige Geschäftslogik, die vom MVPD bei Erhalt einer Genehmigungsanfrage angewendet werden kann, stellt Adobe die erforderlichen Daten bereit, um die Durchsetzung der Geschäftslogik zu unterstützen, wenn der MVPD eine Genehmigungsanfrage erhält. Diese Daten können die eindeutige Geräte-ID des anfragenden Benutzers und die IP-Adresse des Geräts enthalten, sind jedoch nicht darauf beschränkt.

Für Geschäftslogik, die eine Benutzerinteraktion und/oder eine spezifische Handhabung durch die Adobe-Lösung erfordert, kann Adobe einige benutzerdefinierte Eigenschaften für jeden MVPD verwalten. Zu diesen MVPD-spezifischen Konfigurationen/Richtlinien gehört die Aktivierung vordefinierter Workflows, die an bestimmten Punkten des Arbeitsablaufs auf der obersten Ebene gestartet werden können. Weitere Informationen zur Unterstützung von benutzerdefinierten Properties erhalten Sie von Ihrem Adobe-Support-Mitarbeiter.

Das folgende Diagramm zeigt die Beziehung zwischen MVPD und Programmer mit diesen Adobe Primetime-Authentifizierungskomponenten:

![](assets/high-level-architecture-nflows.png)

*Abbildung: Allgemeine Architektur und Fluss*

## Adobe Primetime-Authentifizierungskomponenten {#components}

Im Folgenden finden Sie einen Überblick über einige der wichtigsten Komponenten des Authentifizierungs-Ökosystems der Adobe Primetime. Dazu gehören:

* [Zugriffsaktivierung/Clientlose Webdienste](#ae)
* [Adobe-gehosteter Backend-Server](#backend)
* [Token](#tokens)

### Zugreifen auf Enabler/Clientlose Webdienste {#ae}

Der Access Enabler erleichtert die Authentifizierung und Autorisierung aller Interaktionen mit dem Benutzer und wird lokal auf seinem System ausgeführt. Es ist der Access Enabler, der die tatsächlichen Berechtigungs-Workflows mit dem MVPD verarbeitet, während der Programmierer für die übergeordnete Web-Seite oder Player-Anwendung verantwortlich ist.

Clientlose Webdienste werden durch die Adobe Primetime-Authentifizierung für Geräte bereitgestellt, die keine Webseiten rendern können.  Für diese Geräte wird der Berechtigungsprozess initiiert und Inhalte auf dem intelligenten Gerät angezeigt, während die Authentifizierung mit einem MVPD auf einem webfähigen Gerät (PC, Smartphone und Tablet) stattfindet.

Access Enabler:

* Initiiert MVPD-spezifische Authentifizierungs- und Autorisierungsarbeitsabläufe.
* Zwischenspeichert die erfolgreichen Autorisierungsantworten pro Programmer-Ressource/-Kanal zwischen, um unnötigen Anforderungs-Traffic zu minimieren.
* Kann für vordefinierte, für jedes MVPD spezifische Workflows konfiguriert werden, z. B. für die explizite Geräteregistrierung.
* Es ist in folgenden Formularen verfügbar:
   * Eine SWF-Datei, die zur Flash Player-Laufzeit ausgeführt werden kann
   * Eine JS-Datei, die direkt vom Browser ausgeführt wird
   * Ein nativer Access Enabler für verschiedene Plattformen, einschließlich iOS, Android und Xbox.

### Adobe-gehosteter Backend-Server {#backend}

Der von Adobe gehostete Adobe Primetime-Authentifizierungs-Backend-Server:

* Stellt die Authentifizierungs- und Autorisierungs-Workflows mit den MVPDs bereit, die eine Server-zu-Server-Kommunikation zwischen der Adobe Primetime-Authentifizierung und dem Benutzer erfordern.
* Wartung der Konfiguration für Programmierer-Sites und -Anwendungen.
* Host die herunterladbaren Access Enabler-Komponentendateien.
* Erstellt Authentifizierungs- und Autorisierungstoken.

### Token {#tokens}

Die Adobe Primetime-Authentifizierungsberechtigungslösung konzentriert sich auf die Generierung bestimmter Datenteile, die nach erfolgreichem Abschluss von Authentifizierungs-/Autorisierungs-Workflows abgerufen werden. Diese Daten werden als Token bezeichnet. Sie haben eine begrenzte Lebensdauer und werden sicher an plattformabhängigen Standorten gespeichert. Nach Ablauf der Gültigkeit müssen Token erneut ausgestellt werden, indem die Authentifizierungs- und/oder Autorisierungs-Workflows neu gestartet werden.

Es gibt drei Arten von Token, die während der Authentifizierungs-/Autorisierungs-Workflows ausgegeben werden. Zwei davon sind &quot;langlebig&quot;, was Kontinuität im Anzeigeerlebnis des Benutzers gewährleistet. Das dritte, ein kurzlebiges Token, bietet Unterstützung für bewährte Verfahren der Industrie zur Eindämmung von Betrug durch Stream Ripping. Die TTL-Werte (Time-to-Live) für Token werden auf der Grundlage von Vereinbarungen zwischen MVPDs und Programmierern festgelegt. Sie entscheiden sich für einen TTL-Wert, der Ihrem Unternehmen und Ihren Kunden am besten zur Verfügung steht.

**Das langlebige Authentifizierungstoken**. Der Authentifizierungserfolg tritt auf, wenn ein Kunde die Adobe Primetime-Authentifizierung verwendet, um sich erfolgreich bei seinem MVPD-Konto anzumelden. Die Adobe Primetime-Authentifizierung erzeugt dann ein langlebiges Authentifizierungs-Token (&quot;authN&quot;), das an das anfordernde Gerät gebunden ist, und (je nach MVPD) eine global eindeutige Kennung (&quot;GUID&quot;), die den Benutzer anonym identifiziert.

**Das langlebige Autorisierungstoken**. Nach erfolgreicher Autorisierung erstellt die Adobe Primetime-Authentifizierung ein langlebiges Autorisierungs-Token (&quot;authZ&quot;). Dieses Token ist nicht portabel, da es an das anfordernde Gerät und eine bestimmte geschützte Ressource (z. B. einen Kanal, eine Reihe oder eine Folge) gebunden ist. Der Access Enabler verwendet das langlebige authZ-Token, um die kurzlebigen Medien-Token zu erstellen, die für den tatsächlichen Anzeigezugriff verwendet werden.

**Das kurzlebige Medien-Token**. Sobald der Benutzer autorisiert ist, generiert die Adobe Primetime-Authentifizierung ein authZ-Token und verwendet dieses Token zum Generieren eines einmaligen, kurzlebigen Medien-Tokens, das von Adobe signiert und verschlüsselt wird, um Manipulationen beim Austausch zu vermeiden. Da das Token mit kurzer Lebensdauer über die Access Enabler API oder Clientlose-Webdienste für die eingebettete Website verfügbar gemacht wird, muss der Medienserver des Programmierers vor der Bereitstellung des Zugriffs auf die geschützte Ressource eine Adobe Primetime-Authentifizierungskomponente (den Media Token Verifier) verwenden, um das Token zu validieren.

## Lebenszyklus der MVPD-Integration {#lifecycle}

Die folgende Abbildung zeigt den Lebenszyklus der Integration zwischen Adobe Primetime-Authentifizierung und einem MVPD.

![](assets/mvpd-int-lifecycle.png)

*Abbildung: Lebenszyklus der MVPD-Integration*

## Entitäts-Flussdiagramm {#chart}

Das folgende Flussdiagramm zeigt den Gesamtprozess der Bestätigung der Berechtigung mithilfe der Adobe Primetime-Authentifizierung:

![](assets/authn-authz-entitlmnt-flow.png)

*Abbildung: Berechtigungsverfahren mit Adobe Primetime-Authentifizierung*

## Authentifizierungsschritte {#authn-steps}

Die folgenden Schritte zeigen ein Beispiel für den Authentifizierungsfluss der Adobe Primetime-Authentifizierung.  Dies ist der Teil des Berechtigungsprozesses, bei dem ein Programmierer feststellt, ob der Benutzer ein gültiger Kunde eines MVPD ist.  In diesem Szenario ist der Benutzer ein gültiger Abonnent eines MVPD.  Der Benutzer versucht, geschützte Inhalte mithilfe der Flash-Anwendung eines Programmierers anzuzeigen:

1. Der Benutzer besucht die Webseite des Programmierers, auf der die Flash-Applikation des Programmierers und die Adobe Primetime-Authentifizierungszugriffs-Enabler-Komponenten auf den Computer des Benutzers geladen werden. Die Flash-Applikation verwendet Access Enabler, um die Identifikation des Programmierers mit der Adobe Primetime-Authentifizierung festzulegen, und die Adobe Primetime-Authentifizierung nutzt den Access Enabler mit Konfigurations- und Statusdaten für diesen Programmierer (den &quot;Anforderer&quot;). Der Access Enabler muss diese Daten vom Server empfangen, bevor er andere API-Aufrufe durchführt.  Technische Anmerkung: Der Programmierer legt seine Identität mit dem Access Enabler fest. `setRequestor()` -Methode; Einzelheiten finden Sie unter [Handbuch zur Programmierintegration](/help/authentication/programmer-integration-guide-overview.md).
1. Wenn der Benutzer versucht, den geschützten Inhalt des Programmierers anzuzeigen, zeigt die Programmer-Anwendung dem Benutzer eine Liste von MVPDs an, aus denen der Benutzer einen Anbieter auswählt.
1. Der Benutzer wird an einen Adobe Primetime-Authentifizierungsserver weitergeleitet, auf dem eine verschlüsselte SAML-Anfrage für den vom Benutzer ausgewählten MVPD erstellt wird. Diese Anfrage wird als Authentifizierungsanfrage im Namen des Programmierers an den MVPD gesendet. Je nach System des MVPD wird der Browser des Benutzers dann entweder zur MVPD-Site weitergeleitet, um sich anzumelden, oder ein Anmelde-iFrame wird in der App des Programmierers erstellt.
1. In beiden Fällen (Umleitung oder iFrame) akzeptiert der MVPD die Anfrage und zeigt die Anmeldeseite an.
1. Der Benutzer meldet sich mit dem MVPD an, der MVPD validiert den Status des Benutzers als zahlender Kunde und dann erstellt der MVPD seine eigene HTTP-Sitzung.
1. Wenn der Benutzer validiert wird, erstellt der MVPD eine Antwort (SAML und verschlüsselt), die der MVPD an die Adobe Primetime-Authentifizierung zurücksendet.
1. Die Adobe Primetime-Authentifizierung erhält die MVPD-Antwort, erkennt, dass eine Adobe Primetime-Authentifizierungs-HTTP-Sitzung geöffnet ist, validiert die [SAML](https://en.wikipedia.org/wiki/Security_Assertion_Markup_Language) Antwort vom MVPD und leitet zurück zur Seite des Programmierers.
1. Die Seite des Programmierers wird neu geladen, der Access Enabler wird neu geladen und der Programmierer ruft erneut setRequestor() auf.  Der zweite Aufruf von setRequestor() ist erforderlich, da die aktuelle Konfiguration geändert wurde. Es ist jetzt eine Markierung vorhanden, die den Access Enabler informiert, dass ein AuthN-Token auf dem Server auf die Generierung wartet.
1. Der Access Enabler erkennt, dass eine ausstehende Authentifizierung vorliegt, und fordert das Token vom Adobe Primetime-Authentifizierungsserver an. Das Token wird vom Server abgerufen, indem die Flash Player DRM-Funktionen aufgerufen werden.
1. Das AuthN-Token wird im Flash Player-LSO-Cache des Programmierers gespeichert. Die Authentifizierung ist jetzt abgeschlossen und die Sitzung wird auf dem Adobe Primetime-Authentifizierungsserver zerstört.

## Autorisierungsschritte {#authz-steps}

Die folgenden Schritte gehen über den vorherigen Abschnitt ([Authentifizierungsschritte](#authn-steps)):

1. Wenn der Benutzer versucht, auf den geschützten Inhalt des Programmierers zuzugreifen, sucht die Anwendung des Programmierers zunächst auf dem lokalen Computer oder Gerät des Benutzers nach einem AuthN-Token.  Wenn dieses Token nicht vorhanden ist, wird die [Authentifizierungsschritte](#authn-steps) oben genannten Werte folgen.  Wenn das AuthN-Token vorhanden ist, wird der Autorisierungsfluss mit der Anwendung des Programmierers fortgesetzt, die einen Aufruf an den Access Enabler mit einer Anfrage zum Abrufen der Anzeigerechte des Benutzers für ein bestimmtes Element geschützter Inhalte initiiert.
1. Das spezifische Element geschützter Inhalte wird durch eine &quot;Ressourcen-ID&quot;dargestellt.  Dies kann eine einfache Zeichenfolge oder eine komplexere Struktur sein, aber in jedem Fall wird die Art der Ressourcenkennung im Voraus zwischen dem Programmierer und dem MVPD vereinbart.  Die Anwendung des Programmierers übergibt die Kennung der Ressource an den Access Enabler.  Der Access Enabler sucht auf dem lokalen Computer oder Gerät des Benutzers nach einem AuthZ-Token.  Wenn das AuthZ-Token nicht vorhanden ist, übergibt der Access Enabler die Anfrage an den Backend-Adobe Primetime-Authentifizierungsserver.
1. Der Adobe Primetime-Authentifizierungsserver kommuniziert mithilfe standardisierter Protokolle mit dem MVPDs-Autorisierungsendpunkt.  Wenn die Antwort des MVPD anzeigt, dass der Benutzer berechtigt ist, den geschützten Inhalt anzuzeigen, erstellt der Adobe Primetime-Authentifizierungsserver ein AuthZ-Token und gibt es an den Access Enabler weiter, der das AuthZ-Token auf dem Computer des Benutzers speichert.
1. Wenn ein AuthZ-Token auf dem Computer oder Gerät des Benutzers gespeichert ist, ruft die Anwendung des Programmierers den Access Enabler auf, um ein Media Token vom Adobe Primetime-Authentifizierungsserver abzurufen, und stellt dieses Token für die Anwendung des Programmierers bereit.
1. Schließlich verwendet die Anwendung des Programmierers die Komponente Media Token Verifier , um zu bestätigen, dass der richtige Benutzer den richtigen Inhalt anzeigt, und mit dem vorhandenen Media Token kann der Benutzer den geschützten Inhalt anzeigen.

<!--
>![RELATEDINFORMATION]
>
>*   Kickstart Guides, [MVPD kickstart](/help/authentication/mvpd-kickstart-guide.md) and [programmer kickstart](/help/authentication/programmer-kickstart-guide.md). These guides explain the initial steps to take to begin integrating with Adobe Primetime authentication.
>
>*   [MVPD Integration Guide](/help/authentication/mvpd-kickstart-guide.md). This is a lower level technical guide for MVPDs, directed primarily to the software engineers who code and test the applications and systems involved in the integration.
>
>*   [Overview For Programmers](/help/authentication/programmer-overview.md). The same high level of conceptual information as in this MVPD overview, but directed toward the content providers (Programmers).
-->
