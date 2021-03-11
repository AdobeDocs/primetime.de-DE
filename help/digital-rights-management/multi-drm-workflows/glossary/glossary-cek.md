---
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
translation-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Glossar {#glossary}

Häufig verwendete Begriffe, die eine besondere Definition erfordern.

## Content Encryption Key {#content-encryption-key}

Der Inhaltsverschlüsselungsschlüssel (CEK), der von einem Dienstprogramm erzeugt wird, wird anschließend von einem Inhaltspackager bei der Vorbereitung von Inhalten verwendet, die geschützt werden müssen.
Das Dienstprogramm generiert den Schlüssel in Hex mit einer Länge von 16 Byte.
Dieses Handbuch zeigt in Notizen und Fehlermeldungen, Datei- und Befehlsbeispielen die folgenden Varianten von Parameternamen und Wertnamen für das CEK:

* content-Schlüssel
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

Dateinamen für ein CEK werden wie folgt angezeigt:

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

Das CEK selbst kann in einem Schlüsselmanagementsystem gespeichert und verschlüsselt werden. Dieser Leitfaden bezieht sich auf den Index der Datenspeicherung als CEK-Datenspeicherung-ID CEKSID. Der Begriff Schlüssel-Verschlüsselungsschlüssel (KEK) bezieht sich auf den Schlüssel der zweiten Ebene und der Begriff `ek` bezieht sich auf den Wert dieser Verschlüsselung.
Einige Aufrufe verwenden sowohl die CEK- als auch die CEK-Datenspeicherung-ID CEKSID, und der aus der Datenspeicherung abgerufene CEK muss mit dem im Aufruf angegebenen CEK übereinstimmen.
Für HLS Offline mit FairPlay gibt es auch ein `persistentContentKey`, das ablaufen kann.

## Datenspeicherung-ID für den Inhaltsverschlüsselungsschlüssel {#content-encryption-key-storage-id}

Die Content Encryption Key Datenspeicherung ID (CEKSID) ist eine ID zum Abrufen eines Content Encryption Key aus einem Schlüsselmanagementsystem.

Die CEKSID wird auch als
* Schlüssel-ID
* Inhalts-ID
* `&kid`

## Kundenauthentifizierung {#customer-authenticator}

Ein Schlüssel für die Authentifizierung bei Anforderungen an die API von Expressplay. Anforderungen können Anforderungen für Token enthalten.