---
description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Adobe-Lösung verwenden.
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu ermöglichen. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Adobe-Lösung verwenden.

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen über die Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

Sie können das native Widevine DRM von Android mit HLS CMAF-Streams verwenden.

>[!NOTE]
>
> Für das Weitläufige CENC-CTR-System ist die Android-Version 4.4 (API Level 19) erforderlich.
>
> Für das umfassende CBCS-Schema ist die Android-Version 7.1 (API Level 25) erforderlich.

## Details zum Lizenzserver festlegen {#license-server-details}

Rufen Sie Folgendes auf `com.adobe.mediacore.drm.DRMManager` API vor dem Laden der MediaPlayer-Ressource:

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### Argumente {#arguments-license-server}

* `drm` - `"com.widevine.alpha"` für Widevine.

* `licenseServerURL` - Die URL des Widevine-Lizenzservers, der Lizenzanfragen erhält.

* `requestProperties` - Enthält zusätzliche Header, die in die ausgehende Lizenzanfrage aufgenommen werden sollen.

Wenn Sie beispielsweise Inhalte verwenden, die für Expression DRM verpackt sind, verwenden Sie vor der Wiedergabe den folgenden Code:

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## Bereitstellen eines benutzerdefinierten Rückrufs {#custom-callback}

Rufen Sie Folgendes auf `com.adobe.mediacore.drm.DRMManager` API vor dem Laden der MediaPlayer-Ressource.

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### Argumente {#arguments-custom-callback}

* `callback` - benutzerdefinierte Implementierung von MediaDRMCallback zur Verwendung anstelle der standardmäßigen `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

Weitere Informationen finden Sie unter [Android TVSDK 3.11 API-Dokumentation](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.11/index.html).

## PSSH-Feld der aktuell geladenen MediaPlayer-Ressource abrufen {#pssh-box-mediaplayer-resoource}

Rufen Sie Folgendes auf `com.adobe.mediacore.drm.DRMManager` API, vorzugsweise in der benutzerdefinierten Callback-Implementierung.

```java
public static byte[] getPSSH()
```

Die API gibt das spezifische Header-Feld für das Schutzsystem zurück, das mit der geladenen Widevine-Medienressource verknüpft ist.

Ein gültiges Feld ist für kurze Dauer verfügbar (zwischen der Erstellung der DRM-Instanz und dem Laden von Schlüsseln). `MediaDrmCallback callback executeKeyRequest()` kann es verwenden, um das Abrufen von Lizenzschlüsseln anzupassen.

>[!NOTE]
>
> `getPSSH()` API wird nur bei einer einzelnen Player-Instanz unterstützt. Mehrere Player oder Instant On-Funktion sollten seriell initialisiert werden, um das richtige Feld zu erhalten.
