---
title: Wichtigste Funktionen
description: Wichtigste Funktionen
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---


# Schlüsselfunktionen{#key-features}

Adobe Primetime DRM bietet folgende wichtige Funktionen:

* **Unterstützung für HLS-Streaming (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM mit HLS-Inhalten, die auf eine beliebige Plattform gestreamt werden können, die von Flash oder Adobe Primetime unterstützt wird (z. B. Desktop, iOS und Android).
* **Native Unterstützung für iOS-Anwendungen (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM, um Videos in Ihren iOS-Anwendungen zu schützen.
* **Native Unterstützung für Android-Anwendungen (Adobe Primetime erforderlich):** Verwenden Sie Primetime DRM, um Videos in Ihren Android-Anwendungen zu schützen.
* **Geschütztes Streaming auf Xbox (Adobe Primetime erforderlich)**.
* **Remote-iOS-Key-Versand (Adobe Primetime erforderlich):** Unterstützung für die Bereitstellung von Remote-iOS-Schlüsseln über einen Server mit mehreren Mandanten, den Primetime-DRM-Key-Server,
* **Dauerhafter Inhaltsschutz:** Inhalte bleiben über die gesamte Vertriebskette geschützt. Sobald der Inhalt verpackt ist, bleibt er jederzeit geschützt, und Teile davon werden nur zum Zeitpunkt der Wiedergabe und gemäß den Nutzungsregeln entschlüsselt.
* Da der Inhalt mit Nutzungsregeln und Lizenzinformationen gepackt wird, wird der Schutz immer mit dem Inhalt weitergeleitet. Wenn nicht lizenzierte Verbraucher versuchen, den Inhalt abzuspielen, leitet die in den Inhalt eingebettete Richtlinie sie weiter, damit sie eine gültige Lizenz für den Inhalt erwerben können.
* **Sichere Wiedergabe geschützter Inhalte:** Bewährte Verschlüsselungsschemata schützen Inhalte vor nicht autorisierter Wiedergabe.
* **Flexible Nutzungsregeln:** Nutzungsregeln bestimmen, wie Benutzer geschützte Inhalte verwenden können. Die von Primetime DRM unterstützten Nutzungsregeln ermöglichen verschiedene Geschäftsmodelle, einschließlich Pay-per-Ansicht, Filmverleih, Abonnements oder werbefinanzierte Dienstleistungen. Die Nutzungsregeln werden von der Richtlinie festgelegt, die Sie während der Verpackung in den Inhalt einbetten, oder können vom Lizenzserver während der Lizenzerwerbung angegeben werden.
* **Output Protection:** Output Protection-Steuerelemente können verwendet werden, um Schutzsysteme wie HDCP, CGMS-A oder Rovi (ehemals Macrovision) ACP einzubinden. Dies kann dazu beitragen, die Inhaltsausgabe über digitale (z. B. HDMI, DVI und UDI) und analoge (z. B. S-Video- und Component-Video) Ausgaben zu schützen.

   Sie können in der Richtlinie, die Sie für Ihren Inhalt erstellen, Ausgabeschutzoptionen festlegen, die den Zugriff auf Inhalte auf Grundlage der Ausgabeschutzfunktionen des Geräts ermöglichen oder verweigern. Sie können beispielsweise angeben, dass für bestimmte Inhalte kein Ausgabeschutz erforderlich ist, jedoch Ausgabeschutz für Premium-Videoinhalte erforderlich ist, wodurch verhindert wird, dass Inhalte auf Betriebssystemen ohne diese Funktion ausgegeben werden.

   Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren.

* **Unterstützung für dynamisches Streaming:** Verwenden Sie die dynamische Streaming-Funktion von Flash Media Server oder Adobe HTTP Dynamic Streaming, um Inhalte mit mehreren Bitraten zu schützen. Beim dynamischen Streaming wird ein Videostream verwendet, mit dem die Bitrate und die Wiedergabequalität je nach verfügbarer Bandbreite dynamisch angepasst werden, was eine verbesserte Benutzererfahrung ermöglicht. Primetime DRM ermöglicht die Verwendung desselben Inhaltsverschlüsselungsschlüssels und derselben Lizenz für die verschiedenen Kodierungen desselben Assets.
* **Offline-Anzeige:** Der Adobe AIR Runtime-Client ermöglicht es Verbrauchern, Inhalte für die spätere Anzeige herunterzuladen und zu speichern, unabhängig davon, ob der Computer mit dem Internet verbunden bleibt oder nicht.
* **Identitätsbasierte Lizenzierung:** Vergibt Berechtigungen zu Benutzeridentitäten, sodass sich Verbraucher authentifizieren müssen (Angabe einer Benutzer-ID und eines Kennworts), um Zugriff auf Inhalte zu erhalten. Bei der Identitätslizenzierung muss der Entwickler der Clientanwendung die Benutzerauthentifizierung im Rahmen des Lizenzakquise-Arbeitsablaufs implementieren.
* **Lizenzverkettung:** Ermöglicht es Verbrauchern, die Lebensdauer ihres gesamten Inhalts zu verlängern, indem sie eine einzige Root-Lizenz erneuern. Eine der Hauptverwendungen der Lizenzketten sind Abonnement-basierte Geschäftsmodelle, bei denen nach Ablauf eines Abonnements Lizenzen für eine große Anzahl von Inhaltsdateien erneuert werden können, indem die Root-Lizenz einfach erneuert wird.

   Sowohl Root- als auch Laublizenzen sind an den Computer des Verbrauchers gebunden. Die Blattlizenz enthält den CEK und einen Verweis auf die Root-Lizenz. Die Root-Lizenz kann die in der Laublizenz gewährten Rechte erweitern. So kann ein Verbraucher z. B. Laublizenzen für 50 Inhaltselemente haben, die nach Ablauf eines bestimmten Abonnements ablaufen. Wenn der Kunde eine neue Root-Lizenz mit einem neuen Ablaufdatum herunterlädt, können alle 50 Inhaltselemente bis zum Ablauf der aktualisierten Lizenz wiedergegeben werden.

   Primetime DRM 2.0 führte eine Lizenzketten ein, in denen sowohl die Blatt- als auch die Root-Lizenzen an einen bestimmten Rechner gebunden sind. Primetime DRM 3.0 bietet eine verbesserte Form der Lizenzverkettung, bei der ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Lesen Sie *Erweiterte Lizenzketten* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Schlüsselrotation:** Bei typischen Verpackungen wird der Inhalt mit dem Content Encryption Key (CEK) verschlüsselt und der Client erhält eine Lizenz, die das CEK enthält, um den Inhalt zu konsumieren. Wenn die Schlüsselrotation aktiviert ist, kann der Schlüssel zum Verschlüsseln des Inhalts geändert werden, sodass der Schlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Lesen Sie *Key Rotation* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Out-of-Band-Lizenzen:** Mit Primetime DRM ist es möglich, einen Arbeitsablauf zu implementieren, in dem Kunden vorab generierte Lizenzen erwerben, ohne dass ein Lizenzserver bereitgestellt werden muss.
* **Domänenunterstützung:** Als Alternative zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Primetime DRM die Bindung von Lizenzen an eine Domäne. Mehrere Geräte können einer Domäne beitreten und ein Domänentoken erhalten, sodass Lizenzen zwischen Geräten in der Domäne verschoben werden können. Lesen Sie *Domänenregistrierung* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.

* **Partielle Verschlüsselung:** Gibt an, ob alle Frames oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch. Durch die Reduzierung des Verschlüsselungsgrads kann sich der CPU-Aufwand auf Geräten mit niedrigerem Ende verringern.
* **Getrennte Inhaltsverpackung: Für die** Inhaltsverpackung ist keine Netzwerkverbindung mit dem Lizenzserver erforderlich. Dies ermöglicht sichere Back-End-Vorgänge, indem die Belichtung komprimierter Inhalte, die noch nicht geschützt sind, begrenzt wird.
* **Kontrolle über Zeitrücklauf: **Primetime DRM ermöglicht die sichere und genaue Berechnung der Zeit, um die Zeitrücklaufzeit auf dem Client-Computer zu erkennen. Dadurch werden Rechte im Zusammenhang mit dem Zugriff auf Inhalte für einen bestimmten Zeitraum erzwungen, und die Verbraucher werden daran gehindert, Zugangsrechte zu untergraben, indem die Zeit auf ihrem Computer verändert wird.
* **Individualisierung**: Ermöglicht das Binden von Inhalten an einen bestimmten Computer.
* **Anwendungs-Zulassungsliste:** Ermöglicht der Client-Laufzeit sicherzustellen, dass geschützter Inhalt nur in einer autorisierten SWF- oder AIR-Anwendung wiedergegeben wird.
* **Widerruf beschädigter Clients:** Kompromisslose Client-Software kann widerrufen werden. Wenn festgestellt wird, dass der Flash Player oder die Adobe AIR-Laufzeitumgebung gefährdet ist, kann der Dienst diesen Clients verweigert werden, bis sie auf eine neuere und sicherere Version der Clientsoftware aktualisieren.
* **Mehrere Richtlinien für dieselbe Videodatei:** Ein Videoinhalt kann mehrere Richtlinien während des Verpackens enthalten. Bei der Erteilung einer Lizenz kann der Lizenzserver entscheiden, welche der Richtlinien verwendet werden sollen, damit ein Content-Distributor dieselbe geschützte Datei für verschiedene Geschäftsmodelle (z. B. Vermietung und elektronischer Durchverkauf) verwenden kann.