---
description: 'Wenn ein Verbraucher eine geschützte Inhaltsdatei von einer Website oder einem CDN erwirbt, muss er auch eine Lizenz erwerben, die einen Schlüssel zum Entschlüsseln des Videos enthält, bevor es wiedergegeben werden kann. Die folgenden Schritte illustrieren einen gemeinsamen Arbeitsablauf für den Zugriff auf geschützte Inhalte durch einen Computer, auf dem Flash Player oder Adobe AIR ausgeführt wird '
seo-description: 'Wenn ein Verbraucher eine geschützte Inhaltsdatei von einer Website oder einem CDN erwirbt, muss er auch eine Lizenz erwerben, die einen Schlüssel zum Entschlüsseln des Videos enthält, bevor es wiedergegeben werden kann. Die folgenden Schritte illustrieren einen gemeinsamen Arbeitsablauf für den Zugriff auf geschützte Inhalte durch einen Computer, auf dem Flash Player oder Adobe AIR ausgeführt wird '
seo-title: Inhaltsakquise
title: Inhaltsakquise
uuid: 80253746-bc31-43f0-b28b-7a1aa7fe34a7
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---


# Inhaltsakquise{#content-acquisition}

Wenn ein Verbraucher eine geschützte Inhaltsdatei von einer Website oder einem CDN erwirbt, muss er auch eine Lizenz erwerben, die einen Schlüssel zum Entschlüsseln des Videos enthält, bevor es wiedergegeben werden kann. Die folgenden Schritte illustrieren einen gemeinsamen Arbeitsablauf für den Zugriff auf geschützte Inhalte auf einem Computer, auf dem Flash Player oder Adobe AIR ausgeführt wird:

1. Der Verbraucher besucht die Website des Einzelhändlers und wählt ein Video aus, das er sehen möchte. Der Kunde versucht, das geschützte Video mit einem Flash Player oder einer Adobe AIR-Anwendung herunterzuladen oder auf seinen Computer zu übertragen.

   Ist dies das erste Mal, dass der Kunde versucht hat, auf geschützten Inhalt mit diesem bestimmten Computer zuzugreifen, muss der Flash Player oder die Adobe AIR-Laufzeit zuerst individualisiert werden, wie in Schritt 2 beschrieben. Wenn der Laufzeitclient bereits individualisiert wurde, erfolgt der Erwerb einer Lizenz wie in Schritt 3 beschrieben.

1. Der Flash Player- oder Adobe AIR-Laufzeitclient erhält ein eindeutiges digitales Zertifikat (das als *Computerzertifikat* bezeichnet wird) von einem Adobe-gehosteten Server.

   Dieser Prozess der Zuweisung eines eindeutigen Zertifikats wird als *Individualisierung* bezeichnet. Die Individualisierung identifiziert eindeutig sowohl den Computer als auch die Flash Player- oder Adobe AIR-Laufzeitumgebung, mit der Inhalte wiedergegeben werden.

   Durch den Individualisierungsprozess können die heruntergeladenen Lizenzen an einen bestimmten Computer gebunden werden, auf dem der Client installiert ist. Jeder Computer erhält eine eindeutige Maschinenberechtigung (maschineller privater Schlüssel und Computerzertifikat). Sollte ein bestimmter Client gefährdet werden, kann er widerrufen und vom Erwerb von Lizenzen für neue Inhalte ausgeschlossen werden.

1. Der Client analysiert den geschützten Inhalt, während er beginnt, ihn auf den Computer des Verbrauchers herunterzuladen oder zu streamen, und extrahiert die URL des Lizenzservers des Einzelhändlers aus den in die Datei eingebetteten Primetime-DRM-Metadaten.

   Die Primetime-DRM-Metadaten sind in der Regel vom Inhalt getrennt, z. B. eingebettet in eine begleitende Manifestdatei oder als binärer Block, können aber auch in die Inhaltsdatei eingebettet werden. Der Client kontaktiert den Lizenzserver unter der angegebenen URL und erwirbt eine Lizenz (wie in Schritt 4 beschrieben).
1. Der Kunde erhält eine Lizenz vom Lizenzserver des Einzelhändlers.

   Während der Lizenzerwerbung sendet der Kunde Informationen zur Identifizierung des angeforderten Inhalts (die DRM-Primetime-Metadaten *) und das Computerzertifikat (zur Identifizierung des Computers des Verbrauchers) an den Lizenzserver des Händlers.* Die an den Server gesendete Lizenzanforderung wird mit dem öffentlichen Transportschlüssel verschlüsselt, der auch in den Primetime DRM-Metadaten enthalten ist.

   Lizenzserver — die in die Abrechnungs- und Authentifizierungs-Infrastruktur des Einzelhändlers integriert werden können — kann eine Geschäftsregelprüfung durchführen, um zu überprüfen, ob der Benutzer zur Ansicht des angeforderten Inhalts berechtigt ist. Wenn die Geschäftsregeln dies zulassen, gibt der Lizenzserver eine Lizenz mit dem Schlüssel für die Inhaltsverschlüsselung aus, um den Inhalt und die mit dem Konto dieses Benutzers verknüpften Nutzungsregeln zu entschlüsseln. Zur Verarbeitung einer Lizenzanforderung entschlüsselt der Lizenzserver die Anforderung mit seinem privaten Transportschlüssel. Das CEK in den Metadaten wird mithilfe des privaten Schlüssels für License Server entschlüsselt und erneut verschlüsselt, um die Lizenz an das Gerät zu binden, auf dem die Anforderung ausgeführt wird. Die Lizenz wird mit dem privaten Lizenzserver-Schlüssel signiert. Die Lizenzantwort wird mit dem privaten Transportschlüssel signiert und verschlüsselt, bevor sie an den Client zurückgegeben wird.

   Sofern die Lizenz dies zulässt, speichert der Client die Lizenz, um *Offline-Zugriff* für die Lizenz zu aktivieren. Die Lizenzzwischenspeicherung ermöglicht es dem Kunden, geschützte Inhalte Ansicht, ohne jedes Mal, wenn er Inhalte Ansicht, eine neue Lizenz zu erwerben.

1. Sobald der Flash Player- oder Adobe AIR-Laufzeitclient über eine Lizenz verfügt, extrahiert der Client das CEK aus der Lizenz und der Kunde kann die Inhalte, auf die er zugreifen darf, Ansicht vornehmen.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   Das vorstehende Beispiel zeigt nur einen möglichen Arbeitsablauf. Alternativ können Sie einen Workflow mit einem proaktiven Download von Inhalten verwenden, bei dem die Lizenzerfassung viel später erfolgt. Eine andere Möglichkeit besteht darin, einen Workflow für die Vorabbestellung zu implementieren, bei dem die Lizenzerfassung stattfindet, bevor auf den Inhalt zugegriffen wird.

