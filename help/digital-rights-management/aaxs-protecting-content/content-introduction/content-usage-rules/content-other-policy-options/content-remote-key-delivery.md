---
seo-title: Remote- und lokaler iOS-Key-Versand
title: Remote- und lokaler iOS-Key-Versand
uuid: 3c20b1d1-f842-438a-ae3a-4ec31da306ad
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Remote- und lokaler iOS-Key-Versand{#remote-and-local-ios-key-delivery}

Adobe Primetime unterstützt zwei Optionen für wichtigen Versand zu iOS-Clients:

* Remote - Wie in der HLS-Spezifikation angegeben, gibt das M3U8-Manifest einen HTTPS-Pfad an, der einen AES-Schlüssel enthält, der zum Entschlüsseln der folgenden verschlüsselten Segmente im Stream verwendet werden sollte. Wenn &quot;Remote&quot;angegeben ist, erreicht das Client-Gerät einen Remote-HTTPS-Server, um den AES-Schlüssel abzurufen.
* Lokal: Wenn &quot;Lokal&quot;angegeben ist, wird kein Verweis über das Internet/Netzwerk für den AES-Schlüssel gesendet, sondern ein lokaler HTTPS-Server in die iOS-Anwendung eingebettet, der alle AES-Schlüsselanforderungen verarbeitet. Der eingebettete HTTPS-Server wird automatisch in der Primetime-Anwendung eingerichtet und konfiguriert. Der Anwendungsentwickler benötigt keine Intervention.

Der Remote-Key-Versand wird über die Richtlinie aktiviert, die zum Verpacken von Inhalten verwendet wird (wenn diese Einstellung geändert wird, muss der Inhalt neu verpackt werden). Ist der Remote-Key-Versand aktiviert, muss ein Adobe Access-Key-Server bereitgestellt werden, um wichtige Anfragen von iOS-Clients zu bearbeiten. Der Arbeitsablauf für Clients auf anderen Plattformen wird jedoch nicht geändert.

>[!NOTE] {class=&quot;- topic/note &quot;
>
>Die Auswahl der wichtigen Versand betrifft nur iOS-Clients. Alle anderen Geräte, die HLS-Inhalte verwenden, verwenden immer den Versand &quot;Lokaler Schlüssel&quot;, auch wenn &quot;Remote&quot; angegeben wurde.

Weitere Informationen finden Sie unter *Verwenden des Adobe Access Key Servers*.
