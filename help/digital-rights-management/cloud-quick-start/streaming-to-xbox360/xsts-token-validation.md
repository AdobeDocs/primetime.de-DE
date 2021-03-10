---
title: Xbox Live XSTS-Token-Überprüfung
description: Xbox Live XSTS-Token-Überprüfung
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---


# Xbox Live XSTS Token Validierung{#xbox-live-xsts-token-validation}

Bei XSTS-Anforderungen enthält das Feld `customerSpecificAuthToken` das Base64-kodierte XSTS-Token. Der Code `XSTSValidator` untersucht das dekodierte Base64-Token auf das Vorhandensein des Elements `EncryptedAssertion`; Sie können jedoch andere Methoden verwenden, um zwischen diesen Anforderungen und Nicht-Xbox-Anforderungen zu unterscheiden. Sie können beispielsweise eine andere URL verwenden.

Die in der Antwortmeldung zurückgegebene Richtlinie setzt die ursprüngliche Richtlinie in den DRM-Metadaten außer Kraft, die mit der Xbox-Schlüsselanforderung bereitgestellt werden. Nur eine Untergruppe von Richtlinienfunktionen wird vom Xbox-Client unterstützt. Diese Felder sind die einzigen Felder, die die ursprüngliche Richtlinie außer Kraft setzen.

Es sind weitere Setup-Schritte erforderlich, um die Entschlüsselung und Überprüfung von Token zu unterstützen. Sie müssen die Berechtigungen [!DNL xsts_partner_cert.pfx] und [!DNL x_secure_token_service.part.xboxlive.com.cer] in einen JKS-Format-Keystore laden, den Sie dann als Systemeigenschaft `xsts-keystore` für Ihren Back-End-Berechtigungsserver angeben. Standardmäßig hat der Partner [!DNL .pfx] den Alias `xsts` und das Token-Überprüfungszertifikat hat den Alias `xsts-verify-cert`. Sie können diese auch mithilfe der Systemeigenschaften überschreiben. Schließlich gibt es eine Systemeigenschaft `xsts-keystore-password`, die keine Standardeinstellung hat und das Keystore-Kennwort enthält. Die vom `XSTSValidator`-Code gelesenen Systemeigenschaften sind nachfolgend zusammengefasst:

| Systemeigenschaft | Standardwert | Kommentar |
|---|---|---|
| `xsts-keystore` | `xsts.jks` | Der vom Validator verwendete JKS-Format-Keystore. |
| `xsts-keystore-password` |  | Kennwort für den Keystore |
| `xsts-alias` | `xsts` | Alias zum Abrufen des Entschlüsselungsschlüssels aus dem Keystore |
| `xsts-verify-cert-alias` | `xsts-verify-cert` | Alias zum Abrufen des Überprüfungszertifikats aus dem Keystore |

