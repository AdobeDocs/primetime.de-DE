---
title: Store-Schlüssel
description: Store-Schlüssel
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Store-Schlüssel{#store-keys}

Adobe empfiehlt, dass Herausgeber von Inhalten kryptografische private Schlüssel zum Signieren und zur Verschlüsselung auf einem sicheren, manipulationssicheren Hardwaregerät speichern. Schlüssel, die in Software gespeichert sind, sind anfälliger für Kompromisse als Schlüssel, die in Hardware gespeichert sind. Wenn beispielsweise ein Softwareschlüssel durchgesickert wird, wird der Schlüssel oder die Datei, der/die den Schlüssel enthält, in der Regel kopiert, was die Erkennung des Verstoßes erschwert. Schlüssel, die auf Hardware gespeichert sind, sind weniger anfällig für nicht erkannte Kompromisse.

Hardware-Sicherheitsmodule (HSMs) sind dedizierte Hardwaregeräte, die kryptografische Schlüssel speichern und schützen. Weitere Informationen finden Sie unter *Speichern von Anmeldeinformationen* in *Verwenden des Adobe Primetime DRM SDK zum Schutz von Inhalten*.
