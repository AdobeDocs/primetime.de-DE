---
description: Für diejenigen, die mit der Adobe Primetime Access DRM-Lösung vertraut sind, gibt es einige grundlegende Unterschiede zwischen Access und Primetime Cloud DRM, powered by ExpressPlay.
title: Migration vom Zugriff auf Multi-DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Migration vom Zugriff auf Multi-DRM {#migrating-from-access-to-multi-drm}

Für diejenigen, die mit der Adobe Primetime Access DRM-Lösung vertraut sind, gibt es einige grundlegende Unterschiede zwischen Access und Primetime Cloud DRM, powered by ExpressPlay.

## Architektonische Unterschiede zwischen Zugriff und Multi-DRM

|  | Zugriff | Multi-DRM |
|---|---|---|
| **Verpackung** | Der Packager ist an einen Lizenzserver gebunden. Der Packager muss den öffentlichen Schlüssel des Lizenzservers kennen, wenn Inhalte gepackt werden. | Der Packager ist nicht an einen Lizenzserver gebunden. |
|  | Sobald der Inhalt gepackt wurde, ist er an einen bestimmten Lizenzserver gebunden. | Der Inhalt ist nicht an einen bestimmten Lizenzserver gebunden. Dies führt dazu, dass Sie all Ihre Inhalte verpacken können, bevor Sie Ihre Produktionslizenz erhalten. |
|  | Der Packager muss nicht mit einer Form des Schlüsselspeichers kommunizieren, da die Schlüssel nach der Verschlüsselung sicher in den Inhalt selbst (in Metadaten) eingebettet werden. Nur der entsprechende Lizenzserver kann sie lesen. | Schlüssel müssen gesendet werden *nach* Packager aus einem Schlüsselspeichersystem oder versandt *von* einen Packager zu einem Schlüsselspeichersystem. Ein Schlüsselspeichersystem kann entweder das eigene System eines Kunden sein oder der Key Storage von ExpressPlay. |
| **Berechtigung** | Der Client sendet eine Anfrage nach Inhalten an den Access Cloud-Dienst. Der Access Cloud-Dienst sendet dann eine Anfrage an das Berechtigungssystem des Kunden. Das Berechtigungssystem des Kunden antwortet mit Berechtigungen für den Kunden. (Der Client hat wahrscheinlich ein Cookie für die Anmeldung von den Servern des Kunden erhalten, bevor er die Lizenzanfrage gestellt hat.) | Der Client sendet eine Anfrage nach einem Token aus der Storefront des Kunden (dies ist wahrscheinlich derselbe Workflow, in dem der Kunde zuvor ein Authentifizierungs-Cookie erhalten hat). Zu diesem Zeitpunkt führt der Kunde eine Berechtigungsprüfung durch. Wenn die Berechtigungsprüfung erfolgreich war, sendet der Kunde eine Anfrage an die ExpressPlay-Server, um ein Token für den Kunden zu generieren. Dieses Token ist immer an ein bestimmtes Inhaltselement gebunden und *kann* an ein bestimmtes Gerät gebunden sein. Die Storefront des Kunden sendet das Token zurück an den Client. Wenn der Client eine DRM-Wiedergabeanforderung sendet, ist das Token in der Anfrage enthalten (die Methode dafür ist gerätespezifisch) und der DRM-Server von ExpressPlay validiert das Token, ohne den Server des Kunden aufzurufen. |
