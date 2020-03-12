---
description: Mit den folgenden neuen APIs können Sie DRM-Rückrufe definieren.
seo-description: Mit den folgenden neuen APIs können Sie DRM-Rückrufe definieren.
seo-title: Implementierung von DRM-Rückrufen
title: Implementierung von DRM-Rückrufen
uuid: a54c5ec2-299f-47b0-b65b-eed5656ab6aa
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Implementierung von DRM-Rückrufen{#implementing-drm-callbacks}

Mit den folgenden neuen APIs können Sie DRM-Rückrufe definieren.

<!--<a id="section_1090BFDB2C1D4EA4AAC9F9A6EC9DCD51"></a>-->

Sie können eine Rückruffunktion definieren (z. B. `parseContentIdCallback`), um die Inhalts-ID zu analysieren und sie mithilfe der `drmManager` API auf &quot; `setParseContentIdCallback` API&quot;festzulegen.

```js
var arrayToString = function (array) { 
        var uint16array = new Uint16Array(array.buffer); 
        return String.fromCharCode.apply(null, uint16array); 
}, 
  
parseContentIdCallback = function (initData) { 
        var contentId = arrayToString(initData), 
            tokens = contentId?contentId.split('/'):[]; 
        if(tokens.length) { 
            return tokens[tokens.length-1]; 
        } else { 
            return ''; 
        } 
}; 
   
drmManager.setParseContentIdCallback(parseContentIdCallback);
```

<!--<a id="section_1E082B428EA74D9CA11C052158A83947"></a>-->

Sie können eine Rückruffunktion definieren (z. B. `onCertificateResponseCallback`), um eine Antwort auf ein Textzertifikat zu verarbeiten und die Funktion `drmManager` mithilfe der `setCertificateResponseCallback` API auf &quot;zurücksetzen&quot;festzulegen. Sie können das Standardverhalten `setCertificateResponseCallback` überschreiben. Wenn Sie beispielsweise eine andere `certificateResponseType` als `ArrayBuffer`verwenden, können Sie mit diesem Rückruf die Zertifikatantwort in den `ArrayBuffer` Typ konvertieren.

```js
var base64DecodeUint8Array = function (input) { 
        var raw = window.atob(input); 
        var rawLength = raw.length; 
        var array = new Uint8Array(new ArrayBuffer(rawLength)); 
 
        for (var i = 0; i < rawLength; i++) 
            array[i] = raw.charCodeAt(i); 
 
        return array; 
    }, 
  
onCertificateResponseCallback = function (certificateResponse) { 
    if(certificateResponse) { 
        var certText = certificateResponse.trim(); 
        certText = certText.replace(/^"(.+(?="$))"$/, '$1'); 
        return base64DecodeUint8Array(certText); 
    } 
}; 
  
drmManager.setCertificateResponseCallback(onCertificateResponseCallback);
```

<!--<a id="section_4DCC1B3ABCED484EB5340A558C9A770A"></a>-->

Sie können Rückruffunktionen definieren, um die Lizenzmeldung und die Lizenzantwort zu analysieren und sie in einem Aufruf an zu übergeben `drmManager.acquireLicense`. `onLicenseResponseCallback` ist ein neuer Parameter in der `acquireLicense` API.

```js
var base64EncodeUint8Array = function (input) { 
        var keyStr = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/="; 
        var output = ""; 
        var chr1, chr2, chr3, enc1, enc2, enc3, enc4; 
        var i = 0; 
        while (i < input.length) { 
            chr1 = input[i++]; 
            chr2 = i < input.length ? input[i++] : Number.NaN; // Not sure if the index 
            chr3 = i < input.length ? input[i++] : Number.NaN; // checks are needed here 
  
            enc1 = chr1 >> 2; 
            enc2 = ((chr1 & 3) << 4) | (chr2 >> 4); 
            enc3 = ((chr2 & 15) << 2) | (chr3 >> 6); 
            enc4 = chr3 & 63; 
  
            if (isNaN(chr2)) { 
                enc3 = enc4 = 64; 
            } else if (isNaN(chr3)) { 
                enc4 = 64; 
            } 
            output += keyStr.charAt(enc1) + keyStr.charAt(enc2) + 
                keyStr.charAt(enc3) + keyStr.charAt(enc4); 
        } 
        return output; 
    }, 
  
    base64DecodeUint8Array = function (input) { 
        var raw = window.atob(input); 
        var rawLength = raw.length; 
        var array = new Uint8Array(new ArrayBuffer(rawLength)); 
  
        for (var i = 0; i < rawLength; i++) 
            array[i] = raw.charCodeAt(i); 
  
        return array; 
    }, 
  
    onLicenseMessageCallback = function (drmLicenseRequest) { 
        var licenseMessage = drmLicenseRequest.licenseMessage, 
            base64Message = base64EncodeUint8Array(licenseMessage); 
        return base64Message; 
    }, 
  
    onLicenseResponseCallback = function (serverResponse) { 
        var keyText = serverResponse.licenseResponse.trim(); 
        keyText = keyText.replace(/^"(.+(?="$))"$/, '$1'); 
        return base64DecodeUint8Array(keyText); 
    };

drmManager.acquireLicense(drmMetadata, null, acquireLicenseListener, onLicenseMessageCallback, onLicenseResponseCallback);
```

In den Schutzdaten wird das neue **[!UICONTROL certificateResponseType]** Feld verwendet, um den Zertifikatantworttyp festzulegen. Hier ein Beispiel für Schutzdaten:

```js
{ 
     "com.apple.fps.1_0": { 
         "serverURL": "https://fairplay.license.istreamplanet.com/api/license/9d3ed760-3ba9-4042-b4a4-07e0d8069200", 
         "certificateURL":"https://fairplay-stage.license.istreamplanet.com/api/AppCert/9d3ed760-3ba9-4042-b4a4-07e0d8069200", 
         "licenseResponseType": "text", 
         "certificateResponseType": "text", 
         "httpRequestHeaders": { 
            "Content-type": "application/x-www-form-urlencoded" 
         } 
     } 
}
```

Die Verwendung des `certificateResponseType` Felds ist optional. Wird er nicht verwendet, wird der Wert als `ArrayBuffer`Wert angenommen.
