---
description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.
seo-description: Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.
seo-title: Widevine DRM
title: Widevine DRM
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: ddcdf38fb7a77b7609a21bbdf6b32188b917e22c

---


# Widevine DRM {#widevine-drm}

Sie können die Funktionen des Primetime Digital Rights Management (DRM)-Systems verwenden, um sicheren Zugriff auf Ihre Videoinhalte zu bieten. Alternativ können Sie DRM-Lösungen von Drittanbietern als Alternative zur integrierten Lösung von Adobe verwenden.

Wenden Sie sich an Ihren Adobe-Kundenbetreuer, um aktuelle Informationen zur Verfügbarkeit von DRM-Lösungen von Drittanbietern zu erhalten.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

Sie können das native Widevine DRM von Android mit HLS CMAF-Streams verwenden.

>[!NOTE]
>
> Für Widevine CENC CTR Scheme ist eine Android-Version 4.4 (API Level 19) erforderlich.
>
> Für Widevine CBCS Scheme ist eine Android-Version 7.1 (API-Ebene 25) erforderlich.

## Details zum Lizenzserver festlegen {#license-server-details}

Rufen Sie vor dem Laden der MediaPlayer-Ressource die folgende `com.adobe.mediacore.drm.DRMManager` API auf:

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### Argumente {#arguments-license-server}

* `drm` - `"com.widevine.alpha"` für Widevine.

* `licenseServerURL` - Die URL des Widevine-Lizenzservers, der Lizenzanforderungen erhält.

* `requestProperties` - Enthält zusätzliche Header, die in die ausgehende Lizenzanforderung aufgenommen werden sollen.

Verwenden Sie beispielsweise bei der Verwendung von für Expressplay DRM verpackten Inhalten den folgenden Code vor der Wiedergabe:

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## Benutzerdefinierten Rückruf bereitstellen {#custom-callback}

Rufen Sie vor dem Laden der MediaPlayer-Ressource die folgende `com.adobe.mediacore.drm.DRMManager` API auf.

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### Argumente {#arguments-custom-callback}

* `callback` - die benutzerdefinierte Implementierung von MediaDRMCallback anstelle der Standardimplementierung `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

Weitere Informationen finden Sie unter 3.11 API-Referenz.

## PSSH-Feld der aktuell geladenen MediaPlayer-Ressource abrufen {#pssh-box-mediaplayer-resoource}

Rufen Sie die folgende `com.adobe.mediacore.drm.DRMManager` API auf, vorzugsweise in der benutzerdefinierten Callback-Implementierung.

```java
public static byte[] getPSSH()
```

API gibt das Schutzsystem-spezifische Header-Feld zurück, das mit der geladenen Widevine-Medienressource verknüpft ist.

Ein gültiges Feld ist für kurze Dauer verfügbar (zwischen der Erstellung der DRM-Instanz und dem Laden der Schlüssel). `MediaDrmCallback callback executeKeyRequest()` kann es zum Anpassen von Lizenzschlüsseln verwenden.

>[!NOTE]
>
> `getPSSH()` Die API wird nur mit einer einzelnen Player-Instanz unterstützt. Mehrere Player oder Instant On-Funktion sollten seriell initialisiert werden, um das richtige Feld zu erhalten.
