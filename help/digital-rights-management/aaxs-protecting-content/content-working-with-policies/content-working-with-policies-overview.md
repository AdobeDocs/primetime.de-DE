---
seo-title: Übersicht
title: Übersicht
uuid: 7363d241-6947-4a9c-80e5-e50be71066b9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Übersicht {#overview}

Mithilfe von Adobe® Access™ können Inhaltsanbieter Richtlinien auf Mediendateien anwenden. Mithilfe der Policy-Management-APIs können Administratoren Ansichten erstellen, Details zu Richtlinien erstellen und aktualisieren.

Eine *policy* definiert, wie Ansichten von Inhalten durchgeführt werden können. Es handelt sich um eine Sammlung von Informationen, die Sicherheitseinstellungen, Authentifizierungsanforderungen und Verwendungsrechte enthalten. Wenn Richtlinien angewendet werden, ermöglichen die Verschlüsselung und Unterzeichnung Anbietern von Inhalten, die Kontrolle über ihren Inhalt zu behalten, unabhängig davon, wie weit er verteilt wird. Geschützte Dateien können mit Adobe® Flash® Media Server oder einem HTTP-Server bereitgestellt werden. Sie können in benutzerdefinierten Playern heruntergeladen und abgespielt werden, die mit Adobe® AIR®, Adobe® Flash® Player und Adobe® Primetime SDK für iOS erstellt wurden. Die Richtlinie ist eine Vorlage, die der Lizenzserver beim Generieren einer Lizenz verwenden kann. Der Client kann auch auf die Richtlinie verweisen, bevor er eine Lizenz anfordert, um festzustellen, ob er den Benutzer zur Authentifizierung auffordern muss, bevor er eine Lizenzanforderung an den Server ausstellt.

Eine Richtlinie gibt eine oder mehrere Rechte an, die dem Kunden gewährt werden. In der Regel enthält eine Richtlinie mindestens die Option &quot;Recht abspielen&quot;. Es ist auch möglich, mehrere Wiedergaberechte mit jeweils unterschiedlichen Einschränkungen anzugeben. Wenn der Client auf eine Lizenz mit mehreren Abspielrechten stößt, verwendet er die erste, für die er alle Einschränkungen erfüllt. Diese Funktion kann beispielsweise verwendet werden, um verschiedene Ausgabeschutzeinstellungen auf verschiedenen Plattformen zu erzwingen. Beispiel-Code, der dieses Beispiel illustriert, finden Sie unter `CreatePolicyWithOutputProtection.java` im Verzeichnis &quot;samples&quot;der Referenzimplementierungs-Befehlszeilenwerkzeuge.

Sie können die folgenden Aufgaben mithilfe der Richtlinienverwaltungs-APIs ausführen:

* Richtlinien erstellen und aktualisieren
* Details zur Ansicht
* Listen zur Richtlinienaktualisierung verwalten

Weitere Informationen zur Java-API, die in diesem Kapitel behandelt werden, finden Sie unter *API-Referenz für den Zugriff auf Adoben*.

Informationen zur Implementierung der Policy Manager-Referenz finden Sie unter *Verwenden der Adobe Access Reference Implementierungen*.
