---
description: Häufige Probleme beim Testen betreffen häufig Ihre ExpressPlay-Authentifizierer, Transportprotokolle und die erforderlichen Dienstanforderungsparameter.
title: Fehlerbehebung für den Schnellstart
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# Fehlerbehebung für den Schnellstart{#troubleshooting-your-quick-start}

Häufige Probleme beim Testen betreffen häufig Ihre ExpressPlay-Authentifizierer, Transportprotokolle und die erforderlichen Dienstanforderungsparameter.

Wenn [!DNL curl] -Anfragen an ExpressPlay für die Token-Generierung fehlschlagen, enthält der Antworttext eine Fehlermeldung, die den Grund für das Fehlschlagen erklärt.

Wenn die Token-Generierung erfolgreich ist, der Inhalt jedoch trotzdem nicht wiedergegeben wird, überprüfen Sie die ExpressPlay-Token-Erlöserprotokolle auf Fehler wie &quot;Abgelaufenes Token&quot;.

Wenn die Token-Generierung erfolgreich war und die Rückgabe keinen Fehler aufwies, das Video jedoch immer noch nicht abgespielt wird, überprüfen Sie, ob das CEK mit dem Inhalt übereinstimmt und ob das Inhaltsformat mit den Funktionen des Zielgeräts übereinstimmt.

Zusätzlich:

* Vergewissern Sie sich, dass Sie in Ihren Serviceanfragen den richtigen Kundenauthentifizierer verwenden. Es ist einfach, versehentlich den Produktionsauthentifikator zu verwenden, wenn Sie den Testauthentifikator verwenden wollten. Stellen Sie außerdem sicher, dass Sie *Ihre* Authentifizierer. Während des Tests können Sie beispielsweise die `curl` und vergessen Sie, den Authentifizierer gegen die entsprechenden auszutauschen.

* Überprüfen Sie, ob Sie in Ihren Anfragen oder in Ihren Manifesten das richtige Transportprotokoll verwenden ( `https://` versus `https://`oder im Falle von FairPlay `skd://` versus `https://` versus `https://`.

* Stellen Sie sicher, dass Sie alle erforderlichen Abfrageparameter für die DRM-Lösung einschließen, mit der Sie arbeiten. Es ist zum Beispiel einfach, zwischen PlayReady und Widevine zu verwechseln, da beide mit DASH arbeiten, aber die erforderlichen Anforderungsparameter und Verpackungskonfigurationen unterschiedlich sind.
* Vergewissern Sie sich, dass Ihr ExpressPlay-Konto über genügend Token-Guthaben verfügt und noch nicht ausgeschöpft ist.
* Vergewissern Sie sich, dass das Triplet der DRM-Daten, die an das TVSDK gesendet werden, korrekt ist: ExpressPlay-Token, Lizenzserver-URL und DRM-Typ.
* Vergewissern Sie sich, dass alle Ihre Komponenten dieselbe Annahme darüber treffen, welche ExpressPlay-Umgebung verwendet wird, da es zwei Umgebungen gibt: Test und Produktion.
* Beachten Sie, dass verschiedene Browser normalerweise nur ein DRM für DASH-Inhalte unterstützen.
* Ab TVSDK 2.4 wird nur das DASH-LIVE-Verpackungsprofil unterstützt. (Die Unterstützung für DASH-OnDemand befindet sich auf der Roadmap.)
* AndroidTV PlayReady wird aufgrund von Einschränkungen des Geräteherstellers gelegentlich unterstützt. Beispiele:

   * Das Razer Forge-Gerät weist Probleme mit PlayReady-Inhalten auf
   * Amazon FireTV kann keine DASH-Inhalte mit verschlüsseltem Audio-Track verwenden

* Ab TVSDK 2.4 unterstützen nur AndroidTV-Geräte in der Regel sowohl PlayReady als auch Widevine DRMs. Alle anderen Android-Geräte unterstützen in der Regel nur Widevine.
* Ab TVSDK 2.4 muss sich das PSSH-Feld derzeit im .mpd-Manifest befinden. Dies widerspricht dem DASH-Standard, der angibt, dass das PSSH-Feld an einer beliebigen Stelle, wie im Inhalt selbst, und nicht nur in der .mpd-Datei stehen kann.
