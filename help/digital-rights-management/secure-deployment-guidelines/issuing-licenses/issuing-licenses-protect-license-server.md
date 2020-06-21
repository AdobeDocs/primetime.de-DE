---
description: 'Sie müssen sicherstellen, dass Sie Lizenzen sicher ausstellen. Beachten Sie die folgenden bewährten Verfahren zum Schutz des Lizenzservers. '
seo-description: 'Sie müssen sicherstellen, dass Sie Lizenzen sicher ausstellen. Beachten Sie die folgenden bewährten Verfahren zum Schutz des Lizenzservers. '
seo-title: Lizenzserver schützen
title: Lizenzserver schützen
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 0%

---


# Lizenzserver schützen {#protecting-the-license-server}

Sie müssen sicherstellen, dass Sie Lizenzen sicher ausstellen. Beachten Sie zum Schutz des Lizenzservers die folgenden bewährten Verfahren:

## Lokal generierte Zertifikatsperrlisten verwenden {#consuming-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.

Die folgenden APIs prüfen, ob die Listen nicht manipuliert wurden und ob die Listen vom richtigen Lizenzserver signiert wurden:

* Rufen Sie [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie die [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) für alle APIs bereitstellen.

   Weitere Informationen finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Rufen Sie [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) auf, um die Signatur zu überprüfen, bevor Sie sie für alle APIs bereitstellen `PolicyUpdateList` können.

   Weitere Informationen finden Sie unter [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Verwenden von von Adobe veröffentlichten Zertifikatsperrlisten{#consuming-crls-published-by-adobe}

Das SDK lädt regelmäßig Zertifikatsperrlisten herunter, die von Adobe veröffentlicht werden. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.

Das SDK verfügt über eine Konfigurationsoption, um Fehler beim Abrufen von Adobe-Zertifikatsperrlisten zu ignorieren. Sie können diese Option nur in Entwicklungs-Umgebung anwenden. In Produktions-Umgebung muss der Lizenzserver die Zertifikatsperrlisten von Adobe abrufen. Wenn der Lizenzserver keine gültige Zertifikatsperrliste abrufen kann, ist ein Fehler aufgetreten.

## Erstellen von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten{#generating-crls-to-supplement-those-published-by-adobe}

Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von Adobe veröffentlichte Computer-Zertifikatsperrliste ergänzen.

Das Primetime-DRM-SDK prüft und erzwingt die Adobe-Zertifikatsperrlisten. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Computeranmeldeinformationen widerruft, indem Sie die Zertifikatsperrliste an das Primetime-DRM-SDK übergeben. Wenn Sie eine Lizenz ausstellen, überprüft das SDK die Adobe-Zertifikatsperrliste und Ihre Zertifikatsperrliste.

Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Rollenerkennung {#rollback-detection}

Wenn Ihre Implementierung von Adobe Primetime DRM Geschäftsregeln verwendet, bei denen der Client den Status beibehalten muss (z. B. das Zeitintervall des Wiedergabefensters), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und AIR- oder SWF-Listen zulassen sollte.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Primetime DRM der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID, die mit [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())abgerufen wird, und den aktuellen Zählerwert in einer Datenbank speichert.

Weitere Informationen zum Inkrementieren und Verfolgen des Rollback-Zählers finden Sie unter [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) - und Rollback-Erkennung.

## Maschinenzahl bei Erteilung der Lizenzen {#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, müssen der Lizenzserver oder der Domänenserver die mit dem Benutzer verknüpften Computer-IDs speichern.

Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den von der [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) -Methode zurückgegebenen Wert in einer Datenbank zu speichern. Wenn eine neue Anforderung empfangen wird, vergleichen Sie die Computer-ID in der Anforderung mit den bekannten Computer-IDs, indem Sie [MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId))verwenden.

[MachineId.match()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) führt einen Vergleich der IDs durch, um zu ermitteln, ob die IDs für denselben Computer stehen. Dieser Vergleich ist nur sinnvoll, wenn eine kleine Anzahl von Computer-IDs vorhanden ist. Wenn Benutzer beispielsweise fünf Computer in ihrer Domäne zulassen, können Sie in der Datenbank nach den Computer-IDs suchen, die mit dem Benutzernamen des Benutzers verknüpft sind, und einen kleinen Datensatz zum Vergleich abrufen.

Dieser Vergleich ist bei Bereitstellungen, die anonymen Zugriff zulassen, nicht praktikabel. In diesem Fall kann [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) verwendet werden. Diese ID kann jedoch nicht identisch sein, wenn der Benutzer über Flash- und Adobe AIR®-Laufzeitumgebungen auf Inhalte zugreift.

>[!NOTE]
>
>Die ID überlebt nicht, wenn der Benutzer die Festplatte neu formatiert.

## Wiederholungsschutz {#replay-protection}

Der Schutz vor Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsmeldung wiedergibt und möglicherweise einen DoS-Angriff (Denial-of-Service) gegen den Client auslöst.

Ein DoS-Angriff ist ein Versuch von Angreifern, legitime Benutzer eines Dienstes daran zu hindern, diesen Dienst zu verwenden. Beispielsweise könnte ein Wiederholungsangriff, der den Rollback-Zähler verwendet, dazu verwendet werden, den License Server in die Annahme zu &quot;tricksen&quot;, dass der DRM-Client seinen Status zurückgenommen hat, was eine Aussetzung des Kontos verursacht.

Weitere Informationen zum Wiedergabeschutz finden Sie unter [ AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## zulassungsliste von Paketen mit vertrauenswürdigen Inhalten verwalten{#maintain-a-allowlist-of-trusted-content-packagers}

Eine zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.

Bei Content Packagern handelt es sich bei den Entitäten um Organisationen, denen der Eigentümer des Inhalts vertraut, die Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Primetime DRM sollten Sie eine zulassungsliste der Packager für vertrauenswürdige Inhalte verwalten. Sie müssen auch die Identität des Content Packager in den DRM-Metadaten einer DRM-geschützten Datei überprüfen, bevor Sie eine Lizenz ausstellen.

Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## Timeout für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Timeout-Intervall, um die Anwendungssicherheit zu schützen.

Der Ablauf für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanforderung mit dem Primetime DRM SDK angegeben. Nach Ablauf ist das Token nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Richtlinienoptionen überschreiben {#overriding-policy-options}

Wenn Sie eine Lizenz ausstellen, kann der Lizenzserver die in der Richtlinie angegebenen Nutzungsregeln außer Kraft setzen.

Wenn in der Richtlinie ein Beginn angegeben ist, wird vor diesem Beginn keine Lizenz generiert. Sie können jedoch ein späteres Lizenzdatum in der Lizenz festlegen, nachdem die Beginn generiert wurde. Diese Option sollte mit Vorsicht verwendet werden, da der Client den Benutzer nicht daran hindern kann, die Systemzeit vorwärts zu verschieben, um das Beginn zu umgehen.