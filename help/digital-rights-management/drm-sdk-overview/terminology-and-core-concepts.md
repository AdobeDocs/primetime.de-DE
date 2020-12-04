---
seo-title: Terminologie und Kernkonzepte
title: Terminologie und Kernkonzepte
uuid: dc269873-7b63-4c18-bada-5338f4da0edd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# Terminologie und Kernkonzepte{#terminology-and-core-concepts}

In diesem Dokument werden die folgenden Begriffe und Konzepte verwendet:

**Verbraucher**

Der *Consumer* ist der Endbenutzer, der Inhalte herunterlädt oder streamt.

**Inhalt**

*Inhalt* besteht aus digitalen Audio- oder Videodateien.

**Content Encryption Key**

Der *Content Encryption Key* (CEK) ist ein kryptografischer Schlüssel zum Verschlüsseln des Inhalts.

**Inhalteinhaber**

*Die* Eigentümer von Inhalten sind die Unternehmen, die Eigentümer des Urheberrechts an den Inhalten sind. Dabei kann es sich um große Filmstudios oder kleinere, unabhängige Produzenten von Filmen oder anderen audiovisuellen Inhalten handeln.

**Inhaltspakete**

*Content* Packager sind Organisationen, die Inhalte für die Verwendung mit Adobe Primetime DRM verpacken. Eigentümer oder Distributoren von Inhalten können sich entscheiden, ihre eigenen Inhalte zu verpacken, oder sie können die Dienste eines Drittanbieters zur Verpackung ihrer Inhalte einladen und diese elektronisch über das Internet verteilen.

**Digitales Zertifikat**

*Digitale Zertifikate*  (auch als  *Zertifikate* bezeichnet) binden eine Entität wie eine Einzelperson, Organisation oder ein System an ein bestimmtes öffentliches und privates Schlüsselpaar. Digitale Zertifikate können als elektronische Anmeldeinformationen betrachtet werden, die die Identität einer Person, eines Systems oder einer Organisation überprüfen.

**Digitale Signatur**

Eine *digitale Signatur* bindet die Identität des Herausgebers an den veröffentlichten Inhalt und stellt einen Mechanismus zur Erkennung von Manipulationen bereit. Algorithmen für digitale Signaturen verwenden kryptografische Hash-Funktionen und asymmetrische - oder öffentliche/private Schlüsselpaare - Verschlüsselungsalgorithmen. Einige digitale Signaturen nutzen auch digitale Zertifikate und PKI (Public Key Infrastructure), um öffentliche Schlüssel an die Identitäten von Inhabern oder Distributoren von Inhalten zu binden.

**Distributor**

*Distributoren*  (auch als  *Content* Distributor* Einzelhändler* bezeichnet) sind Unternehmen, die die Vertriebsrechte von Inhaltseigentümern für die Veröffentlichung und Verbreitung von Inhalten an Verbraucher sichern. In einigen Fällen handelt es sich bei derselben Entität sowohl um den Inhaltseigentümer als auch um den Inhaltsverteiler.

**DRM-Metadaten**

Informationen, die der Client (d. h. Adobe® Flash® Player, Adobe® AIR® Runtime und Primetime-Client) sendet, um die angeforderten Inhalte zu identifizieren.

**Lizenz**

Eine *Lizenz *ist eine Datenstruktur, die einen verschlüsselten Schlüssel enthält, der zum Entschlüsseln von Inhalten verwendet wird, die mit einer Richtlinie verknüpft sind. Die Lizenz wird von Primetime DRM generiert, wenn der Verbraucher Inhalte anfordert, und ist an den Computer des Verbrauchers gebunden. Mithilfe einer Richtlinie als Referenz definiert die Lizenz die Rechte, die dem Verbraucher, der Inhalte herunterlädt, zur Verfügung stehen. Zur Ansicht von Inhalten muss der Verbraucher eine Lizenz erwerben.

**Lizenzerwerb**

*Der* Erwerb von Lizenzen ist der Erwerb einer Lizenz, die es dem Verbraucher ermöglicht, geschützte Inhalte gemäß einer Reihe von Nutzungsregeln zu entschlüsseln und zu Ansichten. Der Lizenzerwerb erfolgt, wenn ein Client Informationen zur Identifizierung des angeforderten Inhalts (die *DRM-Metadaten*) und des Computerzertifikats (zur Identifizierung des Computers des Verbrauchers) an den Lizenzserver sendet (siehe unten).

**Lizenzserver**

Der* Lizenzserver *kann in die Abrechnungs- und Authentifizierungssysteme des Distributors bzw. Dienstleisters integriert sein und kann Geschäftslogik enthalten, um zu überprüfen, ob der Kunde, der geschützten Inhalt anfordert, berechtigt ist, den Inhalt Ansicht. Wenn der Benutzer berechtigt ist, auf den Inhalt zuzugreifen, gibt der Lizenzserver eine Lizenz aus, die es dem Laufzeitclient ermöglicht, Inhalte zu entschlüsseln und wiederzugeben, basierend auf den mit dem Benutzerkonto verknüpften Richtlinien und Rechten.

Sie müssen einen License Server mit dem Primetime DRM SDK erstellen und bereitstellen.

**Politik**

Eine *Richtlinie* ist ein Container für die Nutzungsregeln, die bestimmen, wie Benutzer geschützte Inhalte verwenden können. Richtlinien werden unabhängig von den geschützten Inhalten definiert. Eine Richtlinie erzwingt erst dann Rechte, wenn sie durch die Lizenz an den Inhalt gebunden ist. Eine Richtlinie Liste den Satz von Nutzungsregeln, d. h. die Berechtigungen oder &quot;Rechte&quot;, die Verbraucher für die von ihnen erworbenen Inhalte haben. Beispielsweise können Inhaltsinhaber eine Richtlinie erstellen, die sicherstellt, dass geschützte Inhalte nur für einen bestimmten Zeitraum für Verbraucher zugänglich sind. Diese Richtlinie wird dann auf alle Inhalte angewendet, für die der Inhaltseigentümer diese Beschränkung erzwingen möchte.

Richtlinien werden mit dem Primetime DRM SDK erstellt.

**Geschützte Inhalte**

*Geschützte Inhalte*  (auch als  *verpackte Inhalte* bezeichnet) beziehen sich auf Videoinhalte, die mit dem Primetime DRM SDK oder anderen unterstützten Werkzeugen verschlüsselt wurden.

**Einzelhändler**

Siehe den Eintrag für *Distributoren* weiter oben in diesem Abschnitt.
