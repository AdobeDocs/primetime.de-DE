---
seo-title: Terminologie und Kernkonzepte
title: Terminologie und Kernkonzepte
uuid: dc269873-7b63-4c18-bada-5338f4da0edd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Terminologie und Kernkonzepte{#terminology-and-core-concepts}

In diesem Dokument werden die folgenden Begriffe und Konzepte verwendet:

**Verbraucher**

Der *Verbraucher* ist der Endbenutzer, der Inhalte herunterlädt oder streamt.

**Inhalt**

*Der Inhalt* besteht aus digitalen Audio- oder Videodateien.

**Content Encryption Key**

Der *Content Encryption Key* (CEK) ist ein kryptografischer Schlüssel zum Verschlüsseln des Inhalts.

**Inhalteinhaber**

*Eigentümer* von Inhalten sind die Unternehmen, die Eigentümer des Urheberrechts an den Inhalten sind. Dabei kann es sich um große Filmstudios oder kleinere, unabhängige Produzenten von Filmen oder anderen audiovisuellen Inhalten handeln.

**Inhaltspakete**

*Content Packager* sind Organisationen, die Inhalte für die Verwendung mit Adobe Primetime DRM verpacken. Eigentümer oder Distributoren von Inhalten können sich entscheiden, ihre eigenen Inhalte zu verpacken, oder sie können die Dienste eines Drittanbieters zur Verpackung ihrer Inhalte einladen und diese elektronisch über das Internet verteilen.

**Digitales Zertifikat**

*Digitale Zertifikate* (auch als *Zertifikate* bezeichnet) binden eine Entität wie eine Einzelperson, Organisation oder ein System an ein bestimmtes öffentliches und privates Schlüsselpaar. Digitale Zertifikate können als elektronische Anmeldeinformationen betrachtet werden, die die Identität einer Person, eines Systems oder einer Organisation überprüfen.

**Digitale Signatur**

Eine *digitale Unterschrift* bindet die Identität des Herausgebers an den veröffentlichten Inhalt und bietet einen Mechanismus zum Erkennen von Manipulationen. Algorithmen für digitale Signaturen verwenden kryptografische Hash-Funktionen und asymmetrische - oder öffentliche/private Schlüsselpaare - Verschlüsselungsalgorithmen. Einige digitale Signaturen nutzen auch digitale Zertifikate und PKI (Public Key Infrastructure), um öffentliche Schlüssel an die Identitäten von Inhabern oder Distributoren von Inhalten zu binden.

**Distributor**

*Distributoren* (auch als *Content-Distributoren* oder* Einzelhändler* bezeichnet) sind Geschäftseinheiten, die das Distributionsrecht von den Inhabern von Inhalten für die Veröffentlichung und Verteilung von Inhalten an Verbraucher sicherstellen. In einigen Fällen handelt es sich bei derselben Entität sowohl um den Inhaltseigentümer als auch um den Inhaltsverteiler.

**DRM-Metadaten**

Informationen, die der Client (d. h. Adobe® Flash® Player, Adobe® AIR® Runtime und Primetime-Client) sendet, um den angeforderten Inhalt zu identifizieren.

**Lizenz**

Eine *Lizenz *ist eine Datenstruktur, die einen verschlüsselten Schlüssel enthält, der zum Entschlüsseln von Inhalten verwendet wird, die mit einer Richtlinie verknüpft sind. Die Lizenz wird von Primetime DRM generiert, wenn der Verbraucher Inhalte anfordert, und ist an den Computer des Verbrauchers gebunden. Mithilfe einer Richtlinie als Referenz definiert die Lizenz die Rechte, die dem Verbraucher, der Inhalte herunterlädt, zur Verfügung stehen. Zur Ansicht von Inhalten muss der Verbraucher eine Lizenz erwerben.

**Lizenzerwerb**

*Lizenzerwerb* ist der Erwerb einer Lizenz, die es dem Verbraucher ermöglicht, geschützte Inhalte gemäß einer Reihe von Nutzungsregeln zu entschlüsseln und zu Ansichten. Die Lizenzerfassung erfolgt, wenn ein Kunde Informationen zur Identifizierung des angeforderten Inhalts (die *DRM-Metadaten*) und das Computerzertifikat (zur Identifizierung des Computers des Verbrauchers) an den Lizenzserver sendet (siehe unten).

**Lizenzserver**

Der* Lizenzserver *kann in die Abrechnungs- und Authentifizierungssysteme des Distributors bzw. Dienstleisters integriert sein und kann Geschäftslogik enthalten, um zu überprüfen, ob der Kunde, der geschützten Inhalt anfordert, berechtigt ist, den Inhalt Ansicht. Wenn der Benutzer berechtigt ist, auf den Inhalt zuzugreifen, gibt der Lizenzserver eine Lizenz aus, die es dem Laufzeitclient ermöglicht, Inhalte zu entschlüsseln und wiederzugeben, basierend auf den mit dem Benutzerkonto verknüpften Richtlinien und Rechten.

Sie müssen einen License Server mit dem Primetime DRM SDK erstellen und bereitstellen.

**Politik**

Eine *Richtlinie* ist ein Container für die Nutzungsregeln, die bestimmen, wie Benutzer geschützte Inhalte verwenden können. Richtlinien werden unabhängig von den geschützten Inhalten definiert. Eine Richtlinie erzwingt erst dann Rechte, wenn sie durch die Lizenz an den Inhalt gebunden ist. Eine Richtlinie Liste den Satz von Nutzungsregeln, d. h. die Berechtigungen oder &quot;Rechte&quot;, die Verbraucher für die von ihnen erworbenen Inhalte haben. Beispielsweise können Inhalteinhaber eine Richtlinie erstellen, die sicherstellt, dass geschützte Inhalte nur für einen bestimmten Zeitraum für Verbraucher zugänglich sind. Diese Richtlinie wird dann auf alle Inhalte angewendet, für die der Inhaltseigentümer diese Beschränkung erzwingen möchte.

Richtlinien werden mit dem Primetime DRM SDK erstellt.

**Geschützte Inhalte**

*Geschützte Inhalte* (auch als *verpackte Inhalte* bezeichnet) beziehen sich auf Videoinhalte, die mit dem Primetime DRM SDK oder anderen unterstützten Werkzeugen verschlüsselt wurden.

**Einzelhändler**

Siehe den Eintrag für *Distributoren* weiter oben in diesem Abschnitt.
