---
title: Wichtigste Funktionen
description: Wichtigste Funktionen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Wichtigste Funktionen{#key-features}

Adobe Primetime DRM bietet die folgenden wichtigen Funktionen:

* **HLS-Streaming-Unterstützung (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM mit HLS-Inhalten, die an jede von Flash oder Adobe Primetime unterstützte Plattform (wie Desktop, iOS und Android) gestreamt werden können.
* **Native iOS-Anwendungsunterstützung (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM, um Videos in Ihren iOS-Anwendungen zu schützen.
* **Native Android-Anwendungsunterstützung (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM, um Videos in Ihren Android-Anwendungen zu schützen.
* **Geschütztes Streaming in Xbox (Adobe Primetime erforderlich)**.
* **Remote iOS-Schlüsselbereitstellung (Adobe Primetime erforderlich):** Unterstützung für die Bereitstellung von Remote-iOS-Schlüsseln über einen Multi-Mandanten-Schlüsselserver, den so genannten Primetime DRM Key Server.
* **Persistenter Inhaltsschutz:** Inhalte bleiben in der gesamten Verteilungskette geschützt. Sobald der Inhalt verpackt ist, bleibt er jederzeit geschützt und Teile davon werden nur zum Zeitpunkt der Wiedergabe und gemäß den Nutzungsregeln entschlüsselt.
* Da der Inhalt mit Nutzungsregeln und Lizenzinformationen gepackt wird, wird der Schutz immer mit dem Inhalt durchlaufen. Wenn nicht lizenzierte Benutzer versuchen, den Inhalt wiederzugeben, leitet die in den Inhalt eingebettete Richtlinie sie so um, dass sie eine gültige Lizenz für den Inhalt erwerben können.
* **Sichere Wiedergabe geschützter Inhalte:** Es werden bewährte Verschlüsselungsschemata verwendet, um Inhalte vor nicht autorisierter Wiedergabe zu schützen.
* **Flexible Nutzungsregeln:** Nutzungsregeln bestimmen, wie Verbraucher geschützte Inhalte verwenden können. Die von Primetime DRM unterstützten Nutzungsregeln ermöglichen verschiedene Geschäftsmodelle, darunter Pay-per-View, Vermietung von Filmen, Abonnements oder Ad-finanziert-Dienste. Die Nutzungsregeln werden durch die Richtlinie angegeben, die Sie während der Verpackung in den Inhalt einbetten, oder können vom Lizenzserver während der Lizenzakquise angegeben werden.
* **Output Protection:** Mit Output Protection-Kontrollen können Schutzsysteme wie HDCP, CGMS-A oder Rovi (ehemals Macrovision) AKP aktiviert werden. Dies kann dazu beitragen, die Inhaltsausgabe über digitale (z. B. HDMI, DVI und UDI) und analoge (z. B. S-Video- und Komponenten-Video-) Ausgaben zu schützen.

  Sie können in der Richtlinie, die Sie für Ihren Inhalt erstellen, Ausgabeschutzoptionen festlegen, die den Zugriff auf Inhalte auf der Grundlage der Ausgabeschutzfunktionen eines Geräts ermöglichen oder verweigern. Sie können beispielsweise angeben, dass für bestimmte Inhalte kein Ausgabeschutz erforderlich ist, aber Ausgabeschutz für Premium-Videoinhalte erforderlich ist, wodurch verhindert wird, dass Inhalte auf Betriebssystemen ohne diese Funktion ausgegeben werden.

  Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren.

* **Unterstützung für dynamisches Streaming:** Verwenden Sie die Dynamic Streaming-Funktion von Flash Media Server oder Adobe HTTP Dynamic Streaming, um Inhalte zu schützen, die mit mehreren Bitraten kodiert wurden. Dynamic Streaming verwendet einen Videostream, der die Bitrate und Wiedergabequalität dynamisch an die verfügbare Bandbreite anpasst und so ein verbessertes Benutzererlebnis bietet. Mit Primetime DRM können Sie denselben Inhaltsverschlüsselungsschlüssel und dieselbe Lizenz für die verschiedenen Kodierungen desselben Assets verwenden.
* **Offline-Anzeige:** Mit dem Adobe AIR-Laufzeitclient können Verbraucher Inhalte herunterladen und für die spätere Anzeige speichern, unabhängig davon, ob der Computer mit dem Internet verbunden bleibt oder nicht.
* **Identitätsbasierte Lizenzierung:** Verknüpfen Sie Berechtigungen mit Benutzeridentitäten, sodass Verbraucher sich authentifizieren müssen (indem sie eine Benutzer-ID und ein Kennwort angeben), um Zugriff auf Inhalte zu erhalten. Identitätsbasierte Lizenzierung erfordert, dass die Partei, die die Clientanwendung entwickelt, die Benutzerauthentifizierung als Teil des Workflows für die Lizenzakquise implementiert.
* **Lizenzverkettung:** Ermöglicht es Verbrauchern, die Lebensdauer ihres gesamten Inhalts zu verlängern, indem sie eine einzige Root-Lizenz erneuern. Eine der Hauptverwendungen der Lizenzketten sind Abonnement-basierte Geschäftsmodelle, bei denen am Ende einer Abonnementlaufzeit Lizenzen für eine große Anzahl von Inhaltsdateien durch die bloße Verlängerung der Root-Lizenz erneuert werden können.

  Sowohl Root- als auch Laublizenzen sind an den Computer des Verbrauchers gebunden. Die Laublizenz enthält das CEK und einen Verweis auf die Root-Lizenz. Die Root-Lizenz kann die in der Leaf-Lizenz gewährten Rechte erweitern. Beispielsweise kann ein Verbraucher Laublizenzen für 50 Inhaltselemente haben, die am Ende einer bestimmten Abonnementdauer ablaufen. Wenn der Kunde eine neue Root-Lizenz mit einem neuen Ablaufdatum herunterlädt, können alle 50 Inhalte bis zum Ablauf der aktualisierten Lizenz wiedergegeben werden.

  Primetime DRM 2.0 führte Lizenzketten ein, in denen sowohl die Leaf- als auch die Root-Lizenzen an einen bestimmten Computer gebunden sind. Primetime DRM 3.0 bietet eine verbesserte Form der Lizenzketten, in der ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Lesen *Verbesserte Lizenzketten* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Schlüsselrotation:** Während der typischen Verpackung wird der Inhalt mit dem Content Encryption Key (CEK) verschlüsselt und der Client erhält eine Lizenz mit dem CEK, um den Inhalt zu nutzen. Wenn die Schlüsselrotation aktiviert ist, kann der Schlüssel zum Verschlüsseln des Inhalts so geändert werden, dass der Schlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Lesen *Hauptrolle* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Out-of-Band-Lizenzen:** Mit Primetime DRM ist es möglich, einen Workflow zu implementieren, in dem Clients vorgenerierte Lizenzen außerhalb des Bandbereichs erhalten, sodass Lizenzserver nicht mehr bereitgestellt werden müssen.
* **Domänenunterstützung:** Als Alternative zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Primetime DRM die Bindung von Lizenzen an eine Domäne. Mehrere Geräte können einer Domäne beitreten und ein Domänen-Token erhalten, über das Lizenzen zwischen Geräten in der Domäne verschoben werden können. Lesen *Domänenregistrierung* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Partielle Verschlüsselung:** Gibt an, ob alle Frames oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch. Die Verringerung der Verschlüsselungsstufe kann den CPU-Overhead auf Geräten mit niedrigerem Endergebnis verringern.
* **Getrennte Inhaltspakete:** Inhaltspakete erfordern keine Netzwerkverbindung zum Lizenzserver. Dies ermöglicht sichere Backend-Vorgänge, indem die Belichtung komprimierter Inhalte, die noch nicht geschützt sind, eingeschränkt wird.
* **Kontrolle über das Cursor-Rollback: **Primetime DRM ermöglicht die sichere und genaue Berechnung der Zeit, um das Cursor-Rollback auf dem Clientcomputer zu erkennen. Dadurch werden Rechte im Zusammenhang mit dem Zugriff auf Inhalte für einen bestimmten Zeitraum erzwungen und Verbraucher daran gehindert, Zugriffsrechte durch Änderung der Zeit auf ihrem Computer zu untergraben.
* **Individualisierung**: Ermöglicht das Binden von Inhalten an eine bestimmte Maschine.
* **Anwendungs-Zulassungsliste:** Ermöglicht es der Client-Laufzeitumgebung sicherzustellen, dass geschützter Inhalt nur in einer autorisierten SWF- oder AIR-Anwendung wiedergegeben wird.
* **Sperrung kompromittierter Clients:** Kompromittierte Client-Software kann widerrufen werden. Wenn festgestellt wird, dass die Flash Player- oder Adobe AIR-Laufzeitumgebung gefährdet ist, kann der Dienst diesen Clients bis zum Upgrade auf eine neuere und sicherere Clientsoftware verweigert werden.
* **Mehrere Richtlinien für dieselbe Videodatei:** Ein einzelnes Videoinhalt kann mehrere Richtlinien enthalten, die während der Verpackung eingebettet werden. Bei der Erteilung einer Lizenz kann der Lizenzserver entscheiden, welche der Richtlinien verwendet werden sollen, und es einem Inhaltsanbieter ermöglichen, dieselbe geschützte Datei für verschiedene Geschäftsmodelle (z. B. Vermietung und elektronischer Verkauf) zu verwenden.
