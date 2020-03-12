---
description: CRS bietet Just-in-time- (JIT) und asynchrone Umverpackungen und HLS-in-HLS-Konvertierungen. Das Ergebnis der Neuverpackung ist eine HLS-formatierte Version des Originals der Werbeanzeige. CRS platziert die im HLS-Format formatierte Version auf dem Content Versand-Netzwerk (CDN), um sie bei Bedarf zu verwenden.
seo-description: CRS bietet Just-in-time- (JIT) und asynchrone Umverpackungen und HLS-in-HLS-Konvertierungen. Das Ergebnis der Neuverpackung ist eine HLS-formatierte Version des Originals der Werbeanzeige. CRS platziert die im HLS-Format formatierte Version auf dem Content Versand-Netzwerk (CDN), um sie bei Bedarf zu verwenden.
seo-title: Hauptverwendung von CRS
title: Hauptverwendung von CRS
uuid: df2caa67-bc94-4146-9b93-14edc060c3d5
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Hauptverwendung von CRS {#main-uses-of-crs}

CRS bietet Just-in-time- (JIT) und asynchrone Umverpackungen und HLS-in-HLS-Konvertierungen. Das Ergebnis der Neuverpackung ist eine HLS-formatierte Version des Originals der Werbeanzeige. CRS platziert die im HLS-Format formatierte Version auf dem Content Versand-Netzwerk (CDN), um sie bei Bedarf zu verwenden.

In JIT beginnt die Neuverpackung der Adobe Primetime-Anzeige mit dem Einsetzen des Pakets, wenn erstmals ein Nicht-HLS-Anzeigenkreativ gefunden wird. Dies führt in der Regel zu verlorenen Möglichkeiten, die Anzeige während des Umpackvorgangs auszuführen.

Bei der asynchronen Neuverpackung wird das Werbekreativ transkodiert und gespeichert, bevor es benötigt wird, wodurch sich diese verlorenen Möglichkeiten beseitigen lassen.

Bei der HLS-zu-HLS-Konvertierung formatiert CRS ein HLS-Anzeigenkreativ in geeignete Blöcke, um eine einheitliche Wiedergabe zu gewährleisten.

## Just-in-time-Neuverpackung {#section_1BA344F2300B49F291865A7461EDFEAE}

Die JIT-Neuverpackungsreihenfolge lautet wie folgt:

1. Der Manifestserver ruft eine Anzeige ab.
1. Ist das Anzeigenformat HLS, fügt der Manifestserver die Anzeige in den Inhaltsstream ein.
1. Ist das Format nicht HLS (z. B. MP4, FLV oder WebM), sucht der Manifestserver auf dem CDN-Server nach einer transkodierten Version. Wenn eine Anzeige gefunden wird, wird die transkodierte Anzeige in den Inhaltsstream eingefügt.
1. Wenn das Format nicht HLS ist und der CDN-Server keine transkodierte Version hat, übergibt der Manifestserver die Anzeige an CRS, das die Anzeigenkreative transkodiert und das Ergebnis auf dem CDN-Server zur späteren Verwendung speichert.
1. Der Manifestserver gibt den Inhalt ohne Anzeige zurück.

## Asynchrone Neuverpackung {#section_ACDFB43FDA4B445CB9F2A107FEB4F2F7}

Sie können die unter [Umpackungs-API](../creative-repackaging-service/api-repackage.md) beschriebene API verwenden, um Nicht-HLS-Kreativelemente vorzukodieren, um den Verlust von Impressionen zu minimieren und die Monetarisierung zu maximieren.

## HLS-zu-HLS-Konvertierung {#section_877A0E7E8FAF4C2DB086A31C24D53435}

Um Pufferung und Verzögerung zu vermeiden, lädt ein Client ein Video in kleinen Teilen herunter. Wenn die Größe der Pakete inkonsistent ist, kann die Wiedergabe unscharf sein. Die HLS-zu-HLS-Konvertierung stellt sicher, dass Datenblöcke alle dieselbe Dauer haben (z. B. 6 Sekunden).

>[!NOTE]
>
>CRS erzeugt HLS Version 3, unabhängig davon, welche HLS-Version sie erhält.