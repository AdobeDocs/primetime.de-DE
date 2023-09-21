---
title: Lokal generierte Zertifikatsperrlisten verwenden
description: Lokal generierte Zertifikatsperrlisten verwenden
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---

# Lokal generierte Zertifikatsperrlisten verwenden{#consume-locally-generated-crls}

Um lokal generierte Zertifikatsperrlisten (CRLs) und Richtlinien-Aktualisierungslisten zu verwenden, verwenden Sie Adobe Access-APIs, um die Signatur zu überprüfen. Die APIs überprüfen, ob die Listen nicht manipuliert wurden und ob sie vom richtigen Lizenzserver signiert wurden.

* Aufruf `RevocationList.verifySignature` , um die Signatur zu überprüfen, bevor Sie die RevocationList für beliebige APIs bereitstellen.

  Weitere Informationen finden Sie unter `RevocationListFactory` im *Adobe Access API-Referenz*.

* Aufruf `PolicyUpdateList.verifySignature`, um die Signatur vor der Bereitstellung der `PolicyUpdateList` auf alle APIs zugreifen.

  Weitere Informationen finden Sie unter `PolicyUpdateList` im *Adobe Access API-Referenz*.
