---
title: Lokal generierte Zertifikatsperrlisten verwenden
description: Lokal generierte Zertifikatsperrlisten verwenden
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

