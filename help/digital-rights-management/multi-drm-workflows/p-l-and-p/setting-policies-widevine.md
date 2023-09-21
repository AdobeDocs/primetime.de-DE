---
title: Verwenden von Output Protection-Richtlinien
description: Verwenden von Output Protection-Richtlinien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Verwenden von Output Protection-Richtlinien{#using-output-protection-policies}

**Allgemeine Richtlinien zum Schutz der Ausgabe**

Widevine nativ unterstützt sowohl analoge als auch digitale Ausgabeschutzeinschränkungen. Informationen zum Anhängen dieser Richtlinien an generierte Lizenzen finden Sie in der Dokumentation Ihres Widevine Service Providers .

Wenn Sie Expressplay als Widevine Service Provider verwenden, fügen Sie Digital Output Protection-Richtlinien zum Zeitpunkt der Token-Generierung über das HdcpOutputControl-Flag hinzu: Zulässige Werte sind 0, 1, 2, wobei 0 = HDCP_NONE, 1 = HDCP_V1, 2 = HDCP_V2 ist. Sowohl HDCP_V1 als auch HDCP_V2 erzwingen HDCP-Versionen 1.X bzw. 2.X.

&quot;Expressplay&quot;unterstützt derzeit nicht das Anhängen analoger Ausgabebeschränkungen

**Ausgabeschutzrichtlinien für PlayReady**

PlayReady unterstützt auch nativ sowohl analoge als auch digitale Ausgabeschutzeinschränkungen. Die Werte der Ausgabeschutzstufe, die Sie festlegen können. Die Seite [Output Protection Levels](https://msdn.microsoft.com/en-us/library/dn468831.aspx) dokumentiert die Werte, die Sie festlegen können, sowie das erwartete Kundenverhalten.

Wenn Sie &quot;Expressplay&quot;verwenden, fügen Sie zum Zeitpunkt der Tokengenerierung Werte für die Ausgabeschutzstufe über die Kennzeichnungen &quot;compressionDigitalAudioOPL&quot;, &quot;unkomprimiertDigitalAudioOPL&quot;, &quot;compressionDigitalVideoOPL&quot;, &quot;unkomprimiertDigitalVideoOPL&quot;und &quot;unknownOutputBehavior&quot;hinzu. Diese werden dokumentiert unter [Anfrage zum PlayReady-Lizenz-Token](https://www.expressplay.com/developer/restapi/#playready-license-token-request)
