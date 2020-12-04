---
seo-title: Lokal generierte Zertifikatsperrlisten verwenden
title: Lokal generierte Zertifikatsperrlisten verwenden
uuid: 5a4519b8-6dbd-4921-9048-6c9f67aae18d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Lokal generierte Zertifikatsperrlisten verwenden{#consume-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Listen zur Richtlinienaktualisierung zu verwenden, verwenden Sie Adobe Access APIs, um die Signatur zu überprüfen. Die APIs überprüfen, ob die Listen nicht manipuliert wurden und ob sie vom richtigen License Server signiert wurden.

* Rufen Sie `RevocationList.verifySignature` auf, um die Signatur zu prüfen, bevor Sie die RevocationList für alle APIs bereitstellen.

   Weitere Informationen finden Sie unter `RevocationListFactory` in der *Adobe Access API Reference*.

* Rufen Sie `PolicyUpdateList.verifySignature`auf, um die Signatur zu überprüfen, bevor Sie `PolicyUpdateList` für APIs bereitstellen.

   Weitere Informationen finden Sie unter `PolicyUpdateList` in der *Adobe Access API Reference*.

