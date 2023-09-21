---
title: Voraussetzungen
description: Voraussetzungen
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Voraussetzungen {#prerequisites}

Vor dem Verpacken von Inhalten ist ein Primetime DRM Packager-Zertifikat erforderlich. Sie muss über den Primetime DRM Certificate Enrollment Process angefordert werden. Es ist nur ein Paketzertifikat erforderlich (kein Lizenzserver oder Transport). Geben Sie in der E-Mail mit der Zertifikatanfrage an, dass die Anforderung eines Zertifikats für die Verwendung mit dem DRM-Dienst lautet.

[Handbuch zur Zertifikatregistrierung](../../digital-rights-management/certificate-enrollment-guide/about-certs.md)

Es gibt zwei Stufen von Verpackungsbescheinigungen - PRODUKTION und TRIAL. Inhalte, die mit TRIAL-Zertifikaten gepackt werden, sind nur für die Entwicklungsverwendung vorgesehen und werden nach Ablauf des Zertifikats nicht wiedergegeben. Für alle Lizenzen, die für den TRIAL-Inhalt ausgestellt wurden, gilt ein hartcodiertes Richtlinienablaufdatum, das dem Ablaufdatum des Zertifikats entspricht (sofern nicht in der DRM-Richtlinie festgelegt).
