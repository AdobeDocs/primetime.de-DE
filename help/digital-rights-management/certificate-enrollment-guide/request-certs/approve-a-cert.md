---
title: Zertifikat genehmigen (Konto oder Sekundärer Administrator)
description: Zertifikat genehmigen (Konto oder Sekundärer Administrator)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Zertifikat genehmigen (Konto oder Sekundärer Administrator){#approve-a-certificate-account-or-secondary-administrator}

1. Melden Sie sich bei der Zertifikatregistrierungs-Site an.
1. Wählen Sie die **[!UICONTROL Certificates]** Registerkarte.
1. Überprüfen Sie die Anfrage, um sicherzustellen, dass die Anfrage gültig ist.
1. Wenn die Anfrage gültig ist, klicken Sie auf **[!UICONTROL Approve]**.

   Sie können auch einen Kommentar hinzufügen. Eine E-Mail wird an den Anforderer gesendet, in der angegeben wird, dass die Anfrage von einem der Administratoren des Unternehmens genehmigt wurde. Eine Kopie dieser E-Mail wird an das Unternehmen und die Adobe-Administratoren gesendet.

1. Wenn die Anforderung nicht gültig ist, klicken Sie auf **[!UICONTROL Reject]** und geben Sie im Bestätigungsdialogfeld einen Kommentar ein.

   Dem Antragsteller wird eine E-Mail gesendet, in der er feststellt, dass der Antrag von einem der Administratoren des Unternehmens abgelehnt wurde. Eine Kopie dieser E-Mail wird an die Administratoren des Unternehmens gesendet.

Wenn ein Administrator eine Zertifikatanforderung genehmigt, überprüft Adobe die Identität des Anforderers. Adobe kontaktiert den Antragsteller unter der in seinem Profil angegebenen Telefonnummer.

Der Adobe-Administrator versucht, den Antragsteller innerhalb von drei Tagen zweimal zu kontaktieren. Wenn der Adobe-Administrator den Anforderer nicht kontaktieren kann, hinterlässt er eine Nachricht, die einen Rückruf anfordert, oder er gibt eine Zeit an, zu der er erneut aufruft. Wenn der Adobe-Administrator den Anforderer nicht erreichen kann, wird eine E-Mail an die Administratoren gesendet.

>[!NOTE]
>
>Nur die Account- und Sekundären Administratoren können die Telefonnummer des Unternehmens und die Challenge-Phrase des Anforderers ändern.

Wenn die Identität des Anforderers überprüft wird, erhält der Anforderer eine E-Mail mit der PKCS#7-Datei ( [!DNL p7b]).

Der Anforderer kann den PKCS#7-Inhalt aus dem E-Mail-Textkörper kopieren und in eine Datei speichern oder die an die E-Mail angehängte Datei verwenden. Adobe empfiehlt, dass Sie beim Speichern der PKSC#7-Datei den Basisnamen verwenden, den Sie zum Generieren des privaten Schlüssels und der CSR-Datei verwendet haben.

>[!NOTE]
>
>Die an den Anforderer gesendete Datei enthält nur das Zertifikat. Die Datei enthält keine Informationen zum privaten Schlüssel.
