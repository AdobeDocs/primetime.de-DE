---
title: Glossar
description: Häufig verwendete Begriffe, die eine spezielle Definition erfordern.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Glossar {#glossary}

Häufig verwendete Begriffe, die eine spezielle Definition erfordern.

## Inhaltsverschlüsselungsschlüssel {#content-encryption-key}

Der von einem Dienstprogramm generierte Content-Verschlüsselungsschlüssel (CEK) wird anschließend von einem Inhaltspaket bei der Vorbereitung von zu schützenden Inhalten verwendet.
Das Dienstprogramm generiert den Schlüssel in Hex mit einer Länge von 16 Byte.
In diesem Handbuch werden in Notizen und Fehlermeldungen, Datei- und Befehlsbeispielen die folgenden Varianten von Parameternamen und Wertnamen für das CEK angezeigt:

* Content-Schlüssel
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

Dateinamen für ein CEK werden wie folgt angezeigt:

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

Das CEK selbst kann sowohl in einem Schlüsselverwaltungssystem als auch verschlüsselt gespeichert werden. Dieses Handbuch bezieht sich auf den Speicherindex als CEK Storage ID CEKSID. Der Begriff Schlüssel-Verschlüsselungsschlüssel (KEK) bezieht sich auf den Verschlüsselungsschlüssel der zweiten Ebene und den Begriff `ek` bezieht sich auf den Wert dieser Verschlüsselung.
Einige Aufrufe verwenden sowohl die CEK- als auch die CEK-Speicher-ID CEKSID, und der aus dem Speicher abgerufene CEK muss mit dem im Aufruf angegebenen CEK übereinstimmen.
Für HLS Offline mit FairPlay gibt es auch eine `persistentContentKey` die auf ablaufen eingestellt werden kann.

## Speicherkennung des Inhaltsverschlüsselungsschlüssels {#content-encryption-key-storage-id}

Die Kennung des Schlüsselspeichers für die Inhaltsverschlüsselung (Content Encryption Key Storage ID, CEKSID) ist eine ID zum Abrufen eines Inhaltsverschlüsselungsschlüssels aus einem Schlüsselverwaltungssystem.

Die CEKSID wird auch als
* Schlüssel-ID
* Inhalts-ID
* `&kid`

## Kundenauthentifizierung {#customer-authenticator}

Ein Schlüssel für die Authentifizierung bei Anfragen an die API von &quot;Expressplay&quot;. Anfragen können Anforderungen für Token enthalten.
