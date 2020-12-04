---
description: Für diejenigen, die mit der Primetime Access DRM-Lösung von Adobe vertraut sind, gibt es einige grundlegende architektonische Unterschiede zwischen Access und der Primetime Cloud DRM, powered by ExpressPlay.
seo-description: Für diejenigen, die mit der Primetime Access DRM-Lösung von Adobe vertraut sind, gibt es einige grundlegende architektonische Unterschiede zwischen Access und der Primetime Cloud DRM, powered by ExpressPlay.
seo-title: Migration vom Zugriff auf mehrere DRM
title: Migration vom Zugriff auf mehrere DRM
uuid: 3e33ca9a-867e-46b8-bf88-8dbfe14ff786
translation-type: tm+mt
source-git-commit: ffb993889a78ee068b9028cb2bd896003c5d4d4c
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---


# Migration von Access zu Multi-DRM {#migrating-from-access-to-multi-drm}

Für diejenigen, die mit der Primetime Access DRM-Lösung von Adobe vertraut sind, gibt es einige grundlegende architektonische Unterschiede zwischen Access und der Primetime Cloud DRM, powered by ExpressPlay.

## Architektonische Unterschiede zwischen Zugriff und Multi-DRM

|  | Zugriff | Multi-DRM |
|---|---|---|
| **Verpackung** | Der Packager ist an einen Lizenzserver gebunden. Der Packager muss den öffentlichen Schlüssel des Lizenzservers kennen, wenn Inhalte verpackt werden. | Der Packager ist nicht an einen Lizenzserver gebunden. |
|  | Sobald der Inhalt verpackt ist, ist er an einen bestimmten Lizenzserver gebunden. | Inhalte sind nicht an einen bestimmten Lizenzserver gebunden. Eine Folge davon ist, dass Sie alle Inhalte verpacken können, bevor Sie Ihre Produktionslizenz erhalten. |
|  | Der Packager muss nicht mit einer wichtigen Datenspeicherung kommunizieren, da die Schlüssel nach der Verschlüsselung sicher in den Inhalt selbst (in Metadaten) eingebettet werden. Sie können nur vom entsprechenden Lizenzserver gelesen werden. | Schlüssel müssen von einem wichtigen Datenspeicherung-System an *Packager gesendet oder* von *einem Packager an ein Datenspeicherung-Schlüsselsystem gesendet werden.* Ein Schlüsselsystem für die Datenspeicherung kann entweder das eigene System eines Kunden sein oder die Key-Datenspeicherung von ExpressPlay sein. |
| **Berechtigung** | Der Client stellt eine Inhaltsanfrage an den Access Cloud-Dienst. Der Access Cloud-Dienst stellt dann eine Anforderung an das Berechtigungssystem des Kunden. Das Berechtigungssystem des Kunden reagiert mit Berechtigungen für den Kunden zurück. (Der Kunde hat wahrscheinlich ein Cookie für die Anmeldung von den Servern des Kunden erhalten, bevor er die Lizenzanforderung gestellt hat.) | Der Client stellt eine Anforderung für ein Token aus dem Store des Kunden auf (dies ist wahrscheinlich der gleiche Arbeitsablauf, in dem der Kunde zuvor ein Authentifizierungs-Cookie erhalten hat). Derzeit führt der Kunde eine Berechtigungsprüfung durch. Wenn die Berechtigungsprüfung erfolgreich ist, sendet der Kunde eine Anforderung an die ExpressPlay-Server, um ein Token für den Kunden zu generieren. Dieses Token ist immer an ein bestimmtes Inhaltselement gebunden und *kann* an ein bestimmtes Gerät gebunden sein. Der Store des Kunden sendet das Token zurück an den Client. Wenn der Client eine DRM-Wiedergabeanforderung ausführt, wird das Token in der Anforderung enthalten (die Methode hierfür ist gerätespezifisch), und der DRM-Server von ExpressPlay validiert das Token, ohne den Server des Kunden aufzurufen. |