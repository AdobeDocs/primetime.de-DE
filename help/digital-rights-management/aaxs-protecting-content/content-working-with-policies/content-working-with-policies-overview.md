---
title: Übersicht
description: Übersicht
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Übersicht  {#overview}

Mit Adobe® Access™ können Inhaltsanbieter Richtlinien auf Mediendateien anwenden. Mithilfe der APIs für die Richtlinienverwaltung können Administratoren Richtlinien erstellen, anzeigen und aktualisieren.

A *policy* definiert, wie Benutzer Inhalte anzeigen können. Es handelt sich dabei um eine Sammlung von Informationen, die Sicherheitseinstellungen, Authentifizierungsanforderungen und Verwendungsrechte enthalten. Wenn Richtlinien angewendet werden, ermöglichen Verschlüsselung und Signatur den Anbietern von Inhalten, die Kontrolle über ihren Inhalt zu behalten, unabhängig davon, wie weit er verteilt ist. Geschützte Dateien können über Adobe® Flash® Media Server oder einen HTTP-Server bereitgestellt werden. Sie können heruntergeladen und in benutzerdefinierten Playern wiedergegeben werden, die mit Adobe® AIR®, Adobe® Flash® Player und Adobe® Primetime SDK für iOS entwickelt wurden. Die Richtlinie ist eine Vorlage, die der Lizenzserver bei der Erstellung einer Lizenz verwenden kann. Der Client kann auch auf die Richtlinie verweisen, bevor er eine Lizenz anfordert, um festzustellen, ob er den Benutzer zur Authentifizierung auffordern muss, bevor er eine Lizenzanfrage an den Server sendet.

Eine Richtlinie gibt eine oder mehrere Rechte an, die dem Kunden gewährt werden. In der Regel enthält eine Richtlinie mindestens &quot;Recht abspielen&quot;. Es ist auch möglich, mehrere Wiedergabeberechtigungen mit jeweils unterschiedlichen Einschränkungen anzugeben. Wenn der Client auf eine Lizenz mit mehreren Wiedergabedregeln trifft, verwendet er die erste, für die er alle Einschränkungen erfüllt. Diese Funktion kann beispielsweise verwendet werden, um verschiedene Einstellungen für den Ausgabeschutz auf verschiedenen Plattformen durchzusetzen. Beispiel-Code, der dieses Beispiel veranschaulicht, finden Sie unter `CreatePolicyWithOutputProtection.java` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.

Mithilfe der Richtlinien-Management-APIs können Sie die folgenden Aufgaben ausführen:

* Richtlinien erstellen und aktualisieren
* Richtliniendetails anzeigen
* Listen zum Aktualisieren von Richtlinien verwalten

Weitere Informationen zur in diesem Kapitel behandelten Java-API finden Sie unter *Adobe Access API-Referenz*.

Informationen zur Referenzimplementierung von Policy Manager finden Sie unter *Verwenden der Adobe Access Reference-Implementierungen*.
