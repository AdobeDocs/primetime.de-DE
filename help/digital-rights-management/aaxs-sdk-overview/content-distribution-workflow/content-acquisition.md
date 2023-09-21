---
title: Inhaltsakquise
description: Inhaltsakquise
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Inhaltsakquise {#content-acquisition}

Wenn ein Verbraucher eine geschützte Inhaltsdatei von einer Website oder einem CDN erhält, muss er auch eine Lizenz erwerben, die einen Schlüssel zum Entschlüsseln des Videos enthält, bevor es wiedergegeben werden kann. Die folgenden Schritte veranschaulichen einen gemeinsamen Arbeitsablauf für den Zugriff auf geschützte Inhalte durch einen Computer, auf dem Flash Player oder Adobe AIR ausgeführt wird:

1. Der Verbraucher besucht die Website des Einzelhändlers und wählt ein Video zum Ansehen aus. Der Verbraucher versucht, das geschützte Video herunterzuladen bzw. über eine Flash Player- oder Adobe AIR-Anwendung auf seinen Computer zu übertragen.

   Wenn der Benutzer zum ersten Mal versucht hat, mit diesem bestimmten Computer auf geschützte Inhalte zuzugreifen, muss die Flash Player- oder Adobe AIR-Laufzeitumgebung zuerst individualisiert werden, wie in Schritt 2 beschrieben. Wenn der Laufzeitclient bereits individualisiert wurde, erfolgt der Lizenzerwerb wie in Schritt 3 beschrieben.

1. Der Flash Player- oder Adobe AIR-Laufzeitclient erhält ein eindeutiges digitales Zertifikat (das als *Maschinenzertifikat*) von einem Adobe-gehosteten Server aus.

   Dieser Vorgang der Zuweisung eines eindeutigen Zertifikats wird als *Individualisierung*. Durch die Individualisierung werden der Computer und die Flash Player- oder Adobe AIR-Laufzeitumgebung für die Wiedergabe von Inhalten eindeutig identifiziert.

   Der Individualisierungsprozess ermöglicht es, die heruntergeladenen Lizenzen an einen bestimmten Computer zu binden, auf dem der Client installiert ist. Jeder Computer erhält eine eindeutige Maschinenberechtigung (maschineller privater Schlüssel und Maschinenzertifikat). Sollte ein bestimmter Kunde kompromittiert werden, kann er widerrufen und von der Beschaffung von Lizenzen für neue Inhalte ausgeschlossen werden.

1. Der Client analysiert den geschützten Inhalt, während er beginnt, ihn herunterzuladen oder auf den Computer des Verbrauchers zu streamen, und extrahiert die URL des Lizenzservers des Einzelhändlers aus den in die Datei eingebetteten DRM-Metadaten.

   Die DRM-Metadaten sind in der Regel separat vom Inhalt, z. B. eingebettet in eine zugehörige Manifestdatei oder als binärer Blob, können aber auch in die Inhaltsdatei eingebettet werden. Der Client kontaktiert den Lizenzserver unter der angegebenen URL und erwirbt eine Lizenz (wie unten in Schritt 4 beschrieben).
1. Der Kunde erhält eine Lizenz vom Lizenzserver des Einzelhändlers.

   Während der Lizenzakquise sendet der Client Informationen, die den angeforderten Inhalt identifizieren (die *DRM-Metadaten*) und das Maschinenzertifikat (mit dem der Computer des Verbrauchers identifiziert wird) an den Lizenzserver des Einzelhändlers. Die an den Server gesendete Lizenzanforderung wird mit dem öffentlichen Transportschlüssel verschlüsselt, der auch in den DRM-Metadaten enthalten ist.

   Der Lizenzserver, der in die Abrechnungs- und Authentifizierungsinfrastruktur des Einzelhändlers integriert werden kann, kann eine Prüfung der Geschäftsregeln durchführen, um zu überprüfen, ob der Benutzer berechtigt ist, die angeforderten Inhalte anzuzeigen. Wenn die Geschäftsregeln dies zulassen, gibt der Lizenzserver eine Lizenz mit dem Schlüssel zur Inhaltsverschlüsselung aus, um den Inhalt und die mit dem Konto des Benutzers verknüpften Nutzungsregeln zu entschlüsseln. Um eine Lizenzanfrage zu verarbeiten, entschlüsselt der Lizenzserver die Anfrage mit seinem privaten Transportschlüssel. Der CEK in den Metadaten wird mithilfe des privaten Lizenzserver-Schlüssels entschlüsselt und neu verschlüsselt, um die Lizenz an das Gerät zu binden, das die Anforderung ausführt. Die Lizenz wird mithilfe des privaten Schlüssels des Lizenzservers signiert. Die Lizenzantwort wird mit dem privaten Transportschlüssel signiert und verschlüsselt, bevor sie an den Client zurückgegeben wird.

   Sofern durch die Lizenz erlaubt, speichert der Client die Lizenz, um *Offline-Zugriff* der Lizenz. Lizenzzwischenspeicherung ermöglicht es dem Verbraucher, geschützte Inhalte anzuzeigen, ohne jedes Mal, wenn er Inhalte anzeigen möchte, eine Lizenz erneut zu erwerben.

1. Sobald der Flash Player- oder Adobe AIR-Laufzeitclient über eine Lizenz verfügt, extrahiert der Client das CEK aus der Lizenz und der Kunde kann den Inhalt anzeigen, auf den er zugreifen darf.

   <!--<a id="fig_s43_gc2_44"></a>-->

   ![](assets/FMRMS_fig01_web.png)

   Das vorstehende Beispiel zeigt nur einen möglichen Workflow. Alternativ können Sie einen Workflow mit einem proaktiven Download von Inhalten verwenden, bei dem die Lizenzakquise viel später erfolgt. Eine weitere Möglichkeit besteht darin, einen Workflow für die Vorab-Bestellung zu implementieren, bei dem die Lizenzakquise erfolgt, bevor auf den Inhalt zugegriffen wird.
