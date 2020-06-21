---
seo-title: Wichtigste Funktionen
title: Wichtigste Funktionen
uuid: b1bded0f-4e45-4ff8-a7ce-dac3d3ec0ab0
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1146'
ht-degree: 0%

---


# Wichtigste Funktionen {#key-features}

Adobe Access bietet folgende wichtige Funktionen:

* **HLS-Streaming-Unterstützung (Adobe Primetime erforderlich):** Verwenden Sie Adobe Access DRM mit HLS-Inhalten, die auf jede Plattform gestreamt werden können, die von Flash oder Adobe Primetime unterstützt wird (z. B. Desktop, iOS und Android).
* **Native iOS-Anwendungsunterstützung (Adobe Primetime erforderlich):** Verwenden Sie Adobe Access DRM, um Videos in Ihren iOS-Anwendungen zu schützen.
* **Native Unterstützung von Android-Anwendungen (Adobe Primetime erforderlich):** Verwenden Sie Adobe Access DRM, um Videos in Ihren Android-Anwendungen zu schützen.
* **Geschütztes Streaming auf Xbox (Adobe Primetime erforderlich)**.
* **Remote-Versand mit iOS-Schlüssel (Adobe Primetime erforderlich):** Unterstützung für die Bereitstellung von Remote-iOS-Schlüsseln über einen Server mit mehreren Mandanten, den so genannten Adobe Access Key Server.
* **Persistenter Inhaltsschutz:** Inhalte bleiben über die gesamte Vertriebskette geschützt. Sobald der Inhalt verpackt ist, bleibt er jederzeit geschützt, und Teile davon werden nur zum Zeitpunkt der Wiedergabe und gemäß den Nutzungsregeln entschlüsselt.
* Da der Inhalt mit Nutzungsregeln und Lizenzinformationen gepackt wird, wird der Schutz immer mit dem Inhalt weitergeleitet. Wenn nicht lizenzierte Verbraucher versuchen, den Inhalt abzuspielen, leitet die in den Inhalt eingebettete Richtlinie sie weiter, damit sie eine gültige Lizenz für den Inhalt erwerben können.
* **Sichere Wiedergabe geschützter Inhalte: **Bewährte Verschlüsselungsschemata werden verwendet, um Inhalte vor nicht autorisierter Wiedergabe zu schützen.
* **Flexible Nutzungsregeln:** Nutzungsregeln bestimmen, wie Benutzer geschützte Inhalte verwenden können. Die von Adobe Access unterstützten Nutzungsregeln ermöglichen verschiedene Geschäftsmodelle, einschließlich Pay-per-Ansicht, Filmverleih, Abonnements oder werbefinanzierte Dienste. Die Nutzungsregeln werden von der Richtlinie festgelegt, die Sie während der Verpackung in den Inhalt einbetten, oder können vom Lizenzserver während der Lizenzerwerbung angegeben werden.
* **Ausgabeschutz:** Mit Output Protection-Kontrollen können Schutzsysteme wie HDCP, CGMS-A oder Rovi (ehemals Macrovision) ACP aktiviert werden. Dies kann dazu beitragen, die Inhaltsausgabe über digitale (z. B. HDMI, DVI und UDI) und analoge (z. B. S-Video- und Component-Video) Ausgaben zu schützen.

   Sie können in der Richtlinie, die Sie für Ihren Inhalt erstellen, Ausgabeschutzoptionen festlegen, die den Zugriff auf Inhalte auf Grundlage der Ausgabeschutzfunktionen des Geräts ermöglichen oder verweigern. Sie können beispielsweise angeben, dass für bestimmte Inhalte kein Ausgabeschutz erforderlich ist, jedoch Ausgabeschutz für Premium-Videoinhalte erforderlich ist, wodurch verhindert wird, dass Inhalte auf Betriebssystemen ohne diese Funktion ausgegeben werden.

   Während diese Regeln durchgängig auf allen Plattformen durchgesetzt werden, ist es derzeit nur möglich, den Ausgabeschutz auf Windows-Plattformen sicher zu aktivieren.

* **Unterstützung für dynamisches Streaming: **Verwenden Sie die dynamische Streaming-Funktion von Flash Media Server oder Adobe HTTP Dynamic Streaming, um Inhalte mit mehreren Bitraten zu schützen. Beim dynamischen Streaming wird ein Videostream verwendet, mit dem die Bitrate und die Wiedergabequalität je nach verfügbarer Bandbreite dynamisch angepasst werden, was eine verbesserte Benutzererfahrung ermöglicht. Adobe Access ermöglicht die Verwendung desselben Inhaltsverschlüsselungsschlüssels und derselben Lizenz für die verschiedenen Kodierungen desselben Assets.
* **Offline-Ansicht:** Der Adobe AIR-Laufzeitclient ermöglicht es Verbrauchern, Inhalte für die spätere Anzeige herunterzuladen und zu speichern, unabhängig davon, ob der Computer mit dem Internet verbunden bleibt oder nicht.
* **Identitätsbasierte Lizenzierung:** Verknüpfen Sie Berechtigungen mit Benutzeridentitäten, wobei die Verbraucher sich authentifizieren müssen (indem sie eine Benutzer-ID und ein Kennwort angeben), um Zugriff auf Inhalte zu erhalten. Bei der Identitätslizenzierung muss der Entwickler der Clientanwendung die Benutzerauthentifizierung im Rahmen des Lizenzakquise-Arbeitsablaufs implementieren.
* **Lizenzverkettung:** Ermöglicht es Verbrauchern, die Lebensdauer ihres gesamten Inhalts zu verlängern, indem sie eine einzige Root-Lizenz erneuern. Eine der Hauptverwendungen der Lizenzketten sind Abonnement-basierte Geschäftsmodelle, bei denen nach Ablauf eines Abonnements Lizenzen für eine große Anzahl von Inhaltsdateien erneuert werden können, indem die Root-Lizenz einfach erneuert wird.

   Sowohl Root- als auch Laublizenzen sind an den Computer des Verbrauchers gebunden. Die Blattlizenz enthält den CEK und einen Verweis auf die Root-Lizenz. Die Root-Lizenz kann die in der Laublizenz gewährten Rechte erweitern. So kann ein Verbraucher z. B. Laublizenzen für 50 Inhaltselemente haben, die nach Ablauf eines bestimmten Abonnements ablaufen. Wenn der Kunde eine neue Root-Lizenz mit einem neuen Ablaufdatum herunterlädt, können alle 50 Inhaltselemente bis zum Ablauf der aktualisierten Lizenz wiedergegeben werden.

   Adobe Access 2.0 hat eine Lizenzverkettung eingeführt, bei der sowohl die Blatt- als auch die Root-Lizenzen an einen bestimmten Computer gebunden sind. Adobe Access 3.0 bietet eine erweiterte Form der Lizenzverkettung, bei der ein Blatt an eine Root-Lizenz gebunden ist und nur die Root-Lizenz an einen bestimmten Computer oder eine bestimmte Domäne gebunden ist. Lesen Sie *Verbesserte Lizenzketten* in *Verwenden des Adobe Access SDK zum Schutz von Inhalten*.

* **Schlüsselrotation:** Während der typischen Verpackung wird der Inhalt mit dem Content Encryption Key (CEK) verschlüsselt, und der Client erhält eine Lizenz, die das CEK enthält, um den Inhalt zu konsumieren. Wenn die Schlüsselrotation aktiviert ist, kann der Schlüssel zum Verschlüsseln des Inhalts geändert werden, sodass der Schlüssel nur zum Verschlüsseln eines Teils des Inhalts verwendet wird. Lesen Sie die *Schlüsseldrehung* in *Verwenden des Adobe Access-SDK zum Schutz von Inhalten*.

* **Out-of-Band-Lizenzen:** Mit Adobe Access ist es möglich, einen Arbeitsablauf zu implementieren, in dem Clients vorab generierte Lizenzen nicht mehr über das Band verfügen, wodurch die Bereitstellung eines Lizenzservers entfällt.
* **Domänenunterstützung:** Als Alternative zur Bindung einer Lizenz an ein bestimmtes Gerät unterstützt Adobe Access die Bindung von Lizenzen an eine Domäne. Mehrere Geräte können einer Domäne beitreten und ein Domänentoken erhalten, sodass Lizenzen zwischen Geräten in der Domäne verschoben werden können. Lesen Sie *Domänenregistrierung* unter *Verwenden des Adobe Access SDK zum Schutz von Inhalten*.

* **Partielle Verschlüsselung:** Gibt an, ob alle Frames oder nur eine Teilmenge von Frames verschlüsselt werden sollen. Es gibt drei Verschlüsselungsstufen: niedrig, mittel und hoch. Durch die Reduzierung des Verschlüsselungsgrads kann sich der CPU-Aufwand auf Geräten mit niedrigerem Ende verringern.
* **Getrennte Inhaltsverpackung:** Für die Inhaltsverpackung ist keine Netzwerkverbindung mit dem Lizenzserver erforderlich. Dies ermöglicht sichere Back-End-Vorgänge, indem die Belichtung komprimierter Inhalte, die noch nicht geschützt sind, begrenzt wird.
* **Kontrolle über Zeitrücklauf: **Adobe Access bietet eine sichere und genaue Berechnung der Zeit, um die Zeitrücknahme auf dem Clientcomputer zu erkennen. Dadurch werden Rechte im Zusammenhang mit dem Zugriff auf Inhalte für einen bestimmten Zeitraum erzwungen, und die Verbraucher werden daran gehindert, Zugangsrechte zu untergraben, indem die Zeit auf ihrem Computer verändert wird.
* **Individualisierung**: Ermöglicht das Binden von Inhalten an einen bestimmten Computer.
* **zulassungsliste:** Ermöglicht der Client-Laufzeit sicherzustellen, dass geschützter Inhalt nur in einer autorisierten SWF- oder AIR-Anwendung wiedergegeben wird.
* **Widerruf beschädigter Clients: **Kompromisslose Client-Software kann gesperrt werden. Wenn festgestellt wird, dass die Flash Player- oder Adobe AIR-Laufzeitumgebung beeinträchtigt wurde, kann diesen Clients der Dienst verweigert werden, bis sie auf eine neuere und sicherere Version der Clientsoftware aktualisieren.
* **Mehrere Richtlinien für dieselbe Videodatei: **Ein Videoinhalt kann mehrere Richtlinien während der Verpackung enthalten. Bei der Erteilung einer Lizenz kann der Lizenzserver entscheiden, welche der Richtlinien verwendet werden sollen, damit ein Content-Distributor dieselbe geschützte Datei für verschiedene Geschäftsmodelle (z. B. Vermietung und elektronischer Durchverkauf) verwenden kann.

