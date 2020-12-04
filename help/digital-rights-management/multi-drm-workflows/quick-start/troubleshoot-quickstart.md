---
description: Häufige Probleme beim Testen betreffen häufig die ExpressPlay-Authentifizierer, Transportprotokolle und erforderlichen Dienstanforderungsparameter.
seo-description: Häufige Probleme beim Testen betreffen häufig die ExpressPlay-Authentifizierer, Transportprotokolle und erforderlichen Dienstanforderungsparameter.
seo-title: Fehlerbehebung für Ihren QuickBeginn
title: Fehlerbehebung für Ihren QuickBeginn
uuid: 42256aa0-2efc-4602-aefc-3bab2dc58ec0
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Fehlerbehebung für Ihren QuickBeginn{#troubleshooting-your-quick-start}

Häufige Probleme beim Testen betreffen häufig die ExpressPlay-Authentifizierer, Transportprotokolle und erforderlichen Dienstanforderungsparameter.

Wenn Ihre [!DNL curl]-Anforderungen für die Token-Generierung fehlschlagen, enthält der Antworttext eine Fehlermeldung, die den Grund für das Fehlschlagen erklärt.

Wenn die Token-Generierung erfolgreich war, der Inhalt aber trotzdem nicht abgespielt wird, überprüfen Sie die ExpressPlay-Token-Rücknahmeprotokolle auf Fehler wie &quot;Abgelaufenes Token&quot;.

Wenn die Token-Generierung erfolgreich war und bei der Auszahlung kein Fehler aufgetreten ist, das Video jedoch immer noch nicht abgespielt wird, prüfen Sie, ob das CEK mit dem Inhalt übereinstimmt und ob das Inhaltsformat mit den Funktionen des Zielgruppe-Geräts übereinstimmt.

Zusätzlich:

* Vergewissern Sie sich, dass Sie in Ihren Serviceanforderungen den richtigen Kundenauthentifizierer verwenden. Es ist einfach, den Produktionsauthentifizierer versehentlich zu verwenden, wenn Sie den Testauthentifizierer verwenden möchten. Vergewissern Sie sich auch, dass Sie *Ihren*-Authentifizierer verwenden. Beispielsweise könnten Sie beim Testen den Befehl `curl` eines anderen ausleihen und vergessen, den Authentifizierer gegen diesen auszutauschen.

* Vergewissern Sie sich, dass Sie das richtige Transportprotokoll in Ihren Anforderungen oder in Ihren Manifesten ( `https://` versus `https://` oder im Falle von FairPlay `skd://` versus `https://` versus `https://` verwenden.

* Stellen Sie sicher, dass alle erforderlichen Parameter für die Abfrage der DRM-Lösung, mit der Sie arbeiten, vorhanden sind. Es ist zum Beispiel einfach, zwischen PlayReady und Widevine zu verwechseln, da beide mit DASH arbeiten, aber die erforderlichen Anforderungsparameter und Verpackungskonfigurationen unterscheiden sich.
* Vergewissern Sie sich, dass Ihr ExpressPlay-Konto über genügend Token-Guthaben verfügt und nicht ausgeschöpft wurde.
* Vergewissern Sie sich, dass das an das TVSDK gesendete Triplet DRM-Daten korrekt ist: ExpressPlay-Token, Lizenzserver-URL und DRM-Typ.
* Vergewissern Sie sich, dass alle Komponenten dieselbe Annahme darüber treffen, welche ExpressPlay-Umgebung verwendet wird, da es zwei Umgebung gibt: Test and Production.
* Beachten Sie, dass verschiedene Browser normalerweise nur ein DRM für DASH-Inhalte unterstützen.
* Ab TVSDK 2.4 wird nur das DASH-LIVE-Verpackungs-Profil unterstützt. (Der DASH-OnDemand-Support befindet sich auf der Roadmap.)
* Aufgrund der Einschränkungen des Geräteherstellers wird AndroidTV PlayReady nur vorübergehend unterstützt. Beispiele:

   * das Razer Forge-Gerät Probleme mit PlayReady-Inhalten hat
   * Amazon FireTV kann DASH-Inhalte, die die Audiospur verschlüsselt haben, nicht verarbeiten

* Ab TVSDK 2.4 unterstützen nur AndroidTV-Geräte in der Regel sowohl PlayReady- als auch Widevine-DRMs. Alle anderen Android-Geräte unterstützen in der Regel nur Widevine.
* Ab TVSDK 2.4 erfordert das Android TVSDK derzeit, dass sich das Feld PSSH im .mpd-Manifest befindet. Dies steht im Gegensatz zum DASH-Standard, der festlegt, dass das PSSH-Feld an jeder beliebigen Stelle, wie im Inhalt selbst, und nicht nur in der .mpd-Datei stehen kann.

