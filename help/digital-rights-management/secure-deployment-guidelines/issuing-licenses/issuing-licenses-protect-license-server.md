---
description: Sie müssen sicherstellen, dass Sie sicher Lizenzen ausstellen. Beachten Sie diese Best Practices zum Schutz des Lizenzservers .
title: Schutz des Lizenzservers
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 0%

---

# Schutz des Lizenzservers {#protecting-the-license-server}

Sie müssen sicherstellen, dass Sie sicher Lizenzen ausstellen. Beachten Sie folgende Best Practices zum Schutz des Lizenzservers:

## Lokal generierte Zertifikatsperrlisten verwenden {#consuming-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Richtlinien-Aktualisierungslisten zu verwenden, verwenden Sie Adobe Primetime DRM-APIs, um die Signatur zu überprüfen.

Die folgenden APIs überprüfen, ob die Listen nicht bearbeitet wurden und ob die Listen vom richtigen Lizenzserver signiert wurden:

* Aufruf [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) , um die Signatur zu überprüfen, bevor Sie die [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) auf alle APIs zugreifen.

  Weitere Informationen finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* Aufruf [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) , um die Signatur vor der Bereitstellung der `PolicyUpdateList` auf alle APIs zugreifen.

  Weitere Informationen finden Sie unter [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Verarbeiten von durch Adobe veröffentlichten Zertifikatsperrlisten{#consuming-crls-published-by-adobe}

Das SDK lädt regelmäßig von Adobe veröffentlichte Zertifikatsperrlisten herunter. Sie müssen sicherstellen, dass der Zugriff auf diese Dateien nicht blockiert wird oder die Durchsetzung dieser Zertifikatsperrlisten nicht verhindert wird.

Das SDK verfügt über eine Konfigurationsoption, mit der Fehler beim Abrufen von Adobe-Zertifikatsperrlisten ignoriert werden können. Sie können diese Option nur in Entwicklungsumgebungen anwenden. In Produktionsumgebungen muss der Lizenzserver die Zertifikatsperrlisten von Adobe abrufen. Wenn der Lizenzserver keine gültige Zertifikatsperrliste abrufen kann, ist ein Fehler aufgetreten.

## Generieren von Zertifikatsperrlisten als Ergänzung zu den von Adobe veröffentlichten{#generating-crls-to-supplement-those-published-by-adobe}

Sie können Adobe Primetime DRM verwenden, um Zertifikatsperrlisten zu erstellen, die die von Adobe veröffentlichte Zertifikatsperrliste für Rechner ergänzen.

Das Primetime DRM SDK überprüft und erzwingt die Adobe-Zertifikatsperrlisten. Sie können jedoch zusätzliche Clientcomputer deaktivieren, indem Sie eine Zertifikatsperrliste erstellen, die zusätzliche Maschinenanmeldeinformationen widerruft, indem Sie die Zertifikatsperrliste an das Primetime DRM SDK übergeben. Wenn Sie eine Lizenz erteilen, überprüft das SDK die Adobe-Zertifikatsperrliste und Ihre Zertifikatsperrliste.

Informationen zum Generieren von Zertifikatsperrlisten finden Sie unter [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## Rollenerkennung {#rollback-detection}

Wenn Ihre Adobe Primetime DRM-Implementierung Geschäftsregeln verwendet, nach denen der Client den Status beibehalten muss (z. B. das Wiedergabefenster), empfiehlt Adobe, dass der Server den Rollback-Zähler verfolgt und AIR- oder SWF-Zulassungsauflistungen verwendet.

Der Rollback-Zähler wird in den meisten Anforderungen des Clients an den Server gesendet. Wenn für Ihre Implementierung von Primetime DRM der Rollback-Zähler nicht erforderlich ist, kann er ignoriert werden. Andernfalls empfiehlt Adobe, dass der Server die zufällige Computer-ID speichert, die mithilfe von abgerufen wird. [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())und den aktuellen Zählerwert in einer Datenbank.

Weitere Informationen zum Erhöhen und Verfolgen des Rollback-Zählers finden Sie unter [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) und Rollback-Erkennung.

## Maschinenzahl bei Erteilung der Lizenzen {#machine-count-when-issuing-licenses}

Wenn die Geschäftsregeln erfordern, dass die Anzahl der Computer für einen Benutzer verfolgt wird, muss der Lizenzserver oder der Domänenserver die Computer-IDs speichern, die dem Benutzer zugeordnet sind.

Die zuverlässigste Methode zur Verfolgung von Computer-IDs besteht darin, den Wert zu speichern, der von der [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) -Methode in einer Datenbank. Wenn eine neue Anforderung empfangen wird, vergleichen Sie die Computer-ID in der Anfrage mit den bekannten Computer-IDs, indem Sie [MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) führt einen Vergleich von IDs durch, um zu ermitteln, ob die IDs denselben Computer repräsentieren. Dieser Vergleich ist nur praktisch, wenn eine kleine Anzahl von Computer-IDs vorhanden ist. Wenn Benutzer beispielsweise fünf Computer in ihrer Domäne haben, können Sie in der Datenbank nach den Computer-IDs suchen, die mit dem Benutzernamen des Benutzers verknüpft sind, und einen kleinen Datensatz zum Vergleich abrufen.

Dieser Vergleich ist bei Implementierungen, die einen anonymen Zugriff zulassen, nicht praktikabel. In diesem Fall [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) verwendet werden. Diese ID kann jedoch nicht identisch sein, wenn der Benutzer über Flash und Adobe AIR® Laufzeitumgebungen auf Inhalte zugreift.

>[!NOTE]
>
>Die ID überlebt nicht, wenn der Benutzer die Festplatte umformatiert.

## Wiederholungsschutz {#replay-protection}

Der Schutz der Wiederholung verhindert, dass ein Angreifer eine Lizenzanforderungsnachricht wiederholt und möglicherweise einen DoS-Angriff (Denial-of-Service) gegen den Client auslöst.

Ein DoS-Angriff ist ein Versuch von Angreifern, zu verhindern, dass legitime Benutzer eines Dienstes diesen Dienst verwenden. Beispielsweise könnte ein Wiedergabeangriff, der den Rollback-Zähler verwendet, dazu verwendet werden, den Lizenzserver in der Annahme zu &quot;tricken&quot;, dass der DRM-Client seinen Status zurückgesetzt hat, was zu einer Aussetzung des Kontos führt.

Weitere Informationen zum Wiederholungsschutz finden Sie unter [AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## Zulassungsliste vertrauenswürdiger Inhaltspakete verwalten {#maintain-a-allowlist-of-trusted-content-packagers}

Eine Zulassungsliste ist eine Liste vertrauenswürdiger Entitäten.

Bei Inhaltspaketen handelt es sich bei den Entitäten um Organisationen, denen der Inhaltseigentümer vertraut, um die Videodateien zu verpacken (oder zu verschlüsseln) und DRM-geschützte Inhalte zu erstellen. Bei der Bereitstellung von Adobe Primetime DRM sollten Sie eine Zulassungsliste vertrauenswürdiger Inhaltspakete verwalten. Vor der Lizenzerteilung müssen Sie außerdem die Identität des Inhaltspakets in den DRM-Metadaten einer DRM-geschützten Datei überprüfen.

Informationen zum Abrufen von Informationen über die Entität, die den Inhalt verpackt hat, finden Sie unter [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## Zeitüberschreitung für Authentifizierungstoken{#timeout-for-authentication-tokens}

Alle Authentifizierungstoken, die vom Adobe Primetime DRM SDK generiert werden, haben ein Timeout-Intervall, um die Anwendungssicherheit zu schützen.

Der Ablauf für das Authentifizierungstoken wird bei der Bearbeitung einer Authentifizierungsanforderung mit dem Primetime DRM SDK angegeben. Nach Ablauf ist das Token nicht mehr gültig und der Benutzer muss sich erneut beim Lizenzserver authentifizieren.

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## Überschreiben von Richtlinienoptionen {#overriding-policy-options}

Wenn Sie eine Lizenz ausstellen, kann der Lizenzserver die in der Richtlinie angegebenen Nutzungsregeln überschreiben.

Wenn die Richtlinie ein Startdatum angibt, wird vor diesem Startdatum keine Lizenz generiert. Sie können jedoch ein künftiges Startdatum in der Lizenz festlegen, nachdem die Lizenz generiert wurde. Diese Option sollte mit Vorsicht verwendet werden, da der Client nicht verhindern kann, dass der Benutzer die Systemzeit vorwärts bewegt, um das Startdatum zu umgehen.
