---
seo-title: Verwenden von Output Protection-Richtlinien
title: Verwenden von Output Protection-Richtlinien
uuid: f00d2a97-0036-41a6-ab44-391cc40b146e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Verwenden von Output Protection-Richtlinien{#using-output-protection-policies}

**Allgemeine Ausgabenschutzrichtlinien**

Widevine nativ unterstützt sowohl analoge als auch digitale Ausgabeschutzbeschränkungen. In der Dokumentation Ihres Widevine-Dienstleisters erfahren Sie, wie Sie diese Richtlinien an generierte Lizenzen anhängen.

Wenn Sie Expressplay als Widevine-Dienstleister verwenden, fügen Sie über das hdcpOutputControl-Flag zum Zeitpunkt der Tokengenerierung digitale Ausgabeschutzrichtlinien hinzu:
Zulässige Werte sind 0, 1, 2, wobei 0 = HDCP_NONE, 1 = HDCP_V1, 2 = HDCP_V2. Sowohl HDCP_V1 als auch HDCP_V2 erzwingen HDCP-Versionen 1.X und 2.X.

Expressplay unterstützt derzeit nicht das Anschließen analoger Ausgabebeschränkungen

**PlayReady-Ausgabenschutzrichtlinien**

PlayReady unterstützt auch nativ sowohl analoge als auch digitale Ausgabeschränkungen. Die Werte für die Ausgabeschutzebene, die Sie festlegen können. Die Seite [Output Protection Levels](https://msdn.microsoft.com/en-us/library/dn468831.aspx) Dokumente die Werte, die Sie festlegen können, und das erwartete Kundenverhalten.

Wenn Sie &quot;Expressplay&quot;verwenden, fügen Sie Ausgabeschutzebenen zur Tokenerstellungszeit über das Flag &quot;compressionDigitalAudioOPL&quot;, &quot;uncompressionDigitalAudioOPL&quot;, &quot;compressionDigitalVideoOPL&quot;, &quot;uncompressionDigitalVideoOPL&quot;und das Flag &quot;unknownOutputBehavior&quot;an. Diese werden unter [PlayReady License Token Request](https://www.expressplay.com/developer/restapi/#playready-license-token-request) dokumentiert.
