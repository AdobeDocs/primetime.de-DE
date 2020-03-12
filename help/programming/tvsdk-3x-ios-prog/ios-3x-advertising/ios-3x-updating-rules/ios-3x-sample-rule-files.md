---
description: In der Datei AdobeTVSDKConfig.json können Sie sowohl Standardregeln als auch Regeln für bestimmte Zonen angeben.
seo-description: In der Datei AdobeTVSDKConfig.json können Sie sowohl Standardregeln als auch Regeln für bestimmte Zonen angeben.
seo-title: Beispiele für kreative Auswahlregeln
title: Beispiele für kreative Auswahlregeln
uuid: 0342de7e-b9cd-48e3-8bd1-e463bd6d0495
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Beispiele für kreative Auswahlregeln {#sample-creative-selection-rules}

In der Datei AdobeTVSDKConfig.json können Sie sowohl Standardregeln als auch Regeln für bestimmte Zonen angeben.

## Beispielstandardregeln {#section_xy4_3fx_hz}

Im Folgenden finden Sie ein Beispiel für eine [!DNL AdobeTVSDKConfig.json] Datei, die nur Standardregeln definiert:

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ]
        }
    }
}
```

## Beispielstandardregeln mit zusätzlichen Zonenregeln {#section_ocv_3fx_hz}

Im Folgenden finden Sie ein Beispiel für eine [!DNL AdobeTVSDKConfig.json] Datei, die Standardregeln sowie zusätzliche Regeln für eine bestimmte Zonen-ID definiert (in diesem Fall Zone **&quot;1234&quot;**):

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ],
            
<b>"1234"</b>: [
                {
                    "type": "priority",
                    "matches": "nc",
                    "item": "host",
                    "values": [
                        "my.domain.com",
                        "a.bcd.com"
                    ],
                    "priority": [
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/x-flv",
                        "video/quicktime",
                        "video/webm",
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/javascript"
                    ]
                }
            ]
        }
    }
}
```
