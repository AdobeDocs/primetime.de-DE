---
title: Terminologie und Hauptkonzepte
description: Terminologie und Hauptkonzepte
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Terminologie und Hauptkonzepte{#terminology-and-core-concepts}

In diesem Dokument werden die folgenden Begriffe und Konzepte verwendet:

**Verbraucher**

Die *Verbraucher* ist der Endbenutzer, der Inhalte herunterlädt oder streamt.

**Inhalt**

*Inhalt* besteht aus digitalen Audio- oder Videodateien.

**Inhaltsverschlüsselungsschlüssel**

Die *Inhaltsverschlüsselungsschlüssel* (CEK) ist ein kryptografischer Schlüssel zum Verschlüsseln des Inhalts.

**Inhaltsverantwortliche**

*Inhaltsverantwortliche* sind die Unternehmen, die das Urheberrecht für den Inhalt besitzen. Dabei kann es sich um große Filmstudios oder kleinere, unabhängige Filmproduzenten oder andere audiovisuelle Inhalte handeln.

**Inhaltspakete**

*Inhaltspakete* sind Organisationen, die Inhalte für die Verwendung mit Adobe Primetime DRM verpacken. Eigentümer oder Distributoren von Inhalten können sich entscheiden, ihre eigenen Inhalte zu verpacken, oder sie können die Dienste eines Drittanbieters anfordern, ihre Inhalte zu verpacken und elektronisch über das Internet zu verteilen.

**Digitales Zertifikat**

*Digitale Zertifikate* (auch als *certificates*) eine Entität, z. B. eine Person, Organisation oder ein System, an ein bestimmtes Schlüsselpaar aus öffentlichem und privatem Schlüssel binden. Digitale Zertifikate können als elektronische Anmeldeinformationen betrachtet werden, die die Identität einer Person, eines Systems oder einer Organisation überprüfen.

**Digitale Signatur**

A *digitale Signatur* bindet die Identität des Herausgebers an den Inhalt, den er veröffentlicht hat, und bietet einen Mechanismus zur Erkennung von Manipulationen. Digitale Signaturalgorithmen verwenden kryptografische Hash-Funktionen und asymmetrische - oder öffentlich-private Schlüsselpaar - Verschlüsselungsalgorithmen. Einige digitale Signaturen nutzen auch digitale Zertifikate und PKI (Public Key Infrastructure), um öffentliche Schlüssel an die Identitäten von Inhaltsinhabern oder -verteilern zu binden.

**Distributor**

*Distributoren* (auch als *Content-Distributoren* oder* Einzelhändler*) sind Geschäftseinheiten, die die Vertriebsrechte von Inhaltseigentümern für die Veröffentlichung und Verbreitung von Inhalten an Verbraucher sichern. In einigen Fällen ist dieselbe Entität sowohl der Inhaltseigentümer als auch der Inhaltsanbieter.

**DRM-Metadaten**

Informationen, die der Client (d. h. Adobe® Flash® Player, Adobe® AIR® Runtime und Primetime-Client) sendet, um den angeforderten Inhalt zu identifizieren.

**Lizenz**

Eine *Lizenz *ist eine Datenstruktur, die einen verschlüsselten Schlüssel enthält, der zum Entschlüsseln von Inhalten verwendet wird, die mit einer Richtlinie verknüpft sind. Die Lizenz wird von Primetime DRM generiert, wenn der Verbraucher Inhalte anfordert, und ist an den Computer des Verbrauchers gebunden. Mithilfe einer Richtlinie als Referenz definiert die Lizenz die Rechte, die dem Verbraucher, der Inhalte herunterlädt, zur Verfügung stehen. Um Inhalte anzeigen zu können, muss der Verbraucher eine Lizenz erwerben.

**Lizenzakquise**

*Lizenzakquise* ist der Prozess des Erwerbs einer Lizenz, die es dem Verbraucher ermöglicht, geschützte Inhalte gemäß einer Reihe von Nutzungsregeln zu entschlüsseln und anzuzeigen. Die Lizenzakquise erfolgt, wenn ein Client Informationen sendet, die den angeforderten Inhalt identifizieren (die *DRM-Metadaten*) und das Maschinenzertifikat (zur Identifizierung des Computers des Verbrauchers) an den Lizenzserver (siehe unten).

**Lizenzserver**

Der* Lizenzserver *kann in die Abrechnungs- und Authentifizierungssysteme des Distributors oder Dienstleisters integriert sein und kann Geschäftslogik enthalten, um zu überprüfen, ob der Verbraucher, der geschützte Inhalte anfordert, berechtigt ist, den Inhalt anzuzeigen. Wenn der Benutzer berechtigt ist, auf den Inhalt zuzugreifen, gibt der Lizenzserver eine Lizenz heraus, die es dem Laufzeitclient ermöglicht, Inhalte basierend auf der Richtlinie und den Rechten des Kontos des Verbrauchers zu entschlüsseln und wiederzugeben.

Sie müssen einen Lizenzserver mit dem Primetime DRM SDK erstellen und bereitstellen.

**Politik**

A *policy* ist ein Container für die Nutzungsregeln, die bestimmen, wie Verbraucher geschützte Inhalte verwenden können. Richtlinien werden unabhängig vom geschützten Inhalt definiert. Eine Richtlinie erzwingt keine Rechte, bis sie über die Lizenz an den Inhalt gebunden ist. Eine Richtlinie listet den Satz von Nutzungsregeln auf, d. h. die Berechtigungen oder &quot;Rechte&quot;, die Verbraucher für den von ihnen erworbenen Inhalt haben. Beispielsweise können Inhaltseigentümer eine Richtlinie erstellen, die sicherstellt, dass geschützte Inhalte nur für einen bestimmten Zeitraum für Verbraucher zugänglich sind. Diese Richtlinie wird dann auf alle Inhalte angewendet, für die der Inhaltseigentümer diese Beschränkung erzwingen möchte.

Richtlinien werden mit dem Primetime DRM SDK erstellt.

**Geschützter Inhalt**

*Geschützter Inhalt* (auch als *verpackter Inhalt*) bezieht sich auf Videoinhalte, die mit dem Primetime DRM SDK oder anderen unterstützten Tools verschlüsselt wurden.

**Einzelhändler**

Siehe Eintrag für *Distributoren* weiter oben in diesem Abschnitt beschrieben.
