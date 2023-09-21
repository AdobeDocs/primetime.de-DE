---
description: Das Kryptomodul der Adobe-Video-Engine gibt diese Benachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.
title: NATIVE_ERROR Crypto-Werte
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 8%

---

# NATIVE_ERROR: Crypto-Werte{#native-error-crypto-values}

Das Kryptomodul der Adobe-Video-Engine gibt diese Benachrichtigungen im Metadatenobjekt NATIVE_ERROR zurück.

| Wert für RUNTIME_CODE-Metadatenschlüssel | Wert für den Metadatenschlüssel RUNTIME_CODE_MESSAGE | Bedeutung |
|---|---|---|
| 300 | `CRYPTO_ALGORITHM_NOT_SUPPORTED` | Der verwendete Algorithmus wird nicht unterstützt. |
| 301 | `CRYPTO_ERROR_CORRUPTED_DATA` | Daten sind beschädigt. |
| 302 | `CRYPTO_ERROR_BUFFER_TOO_SMALL` | Puffer zu klein. |
| 303 | `CRYPTO_ERROR_BAD_CERTIFICATE` | Ungültiges Zertifikat. |
| 304 | `CRYPTO_ERROR_DIGEST_UPDATE` | Digest Update. |
| 305 | `CRYPTO_ERROR_DIGEST_FINISH` | Digest Finish. |
| 306 | `CRYPTO_ERROR_BAD_PARAMETER` | Unangemessener Parameter. |
