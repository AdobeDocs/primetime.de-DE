---
description: 'null'
seo-description: 'null'
seo-title: Zertifikat genehmigen (Konto oder Sekundärer Administrator)
title: Zertifikat genehmigen (Konto oder Sekundärer Administrator)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# Zertifikat genehmigen (Konto oder Sekundärer Administrator){#approve-a-certificate-account-or-secondary-administrator}

1. Melden Sie sich bei der Zertifikatregistrierungssite an.
1. Wählen Sie die **[!UICONTROL Certificates]** Registerkarte.
1. Überprüfen Sie anhand der Anforderung, ob die Anforderung gültig ist.
1. Wenn die Anforderung gültig ist, klicken Sie auf **[!UICONTROL Approve]**.

   Sie können auch einen Kommentar hinzufügen. Eine E-Mail wird an den Anforderer gesendet, in der darauf hingewiesen wird, dass die Anfrage von einem der Administratoren der Firma genehmigt wurde. Eine Kopie dieser E-Mail wird an die Firma und an Adobe-Administratoren gesendet.

1. Wenn die Anforderung ungültig ist, klicken Sie auf **[!UICONTROL Reject]** und geben Sie im Bestätigungsdialogfeld einen Kommentar ein.

   Eine E-Mail wird an den Anforderer gesendet, in der darauf hingewiesen wird, dass der Antrag von einem der Administratoren der Firma abgelehnt wurde. Eine Kopie dieser E-Mail wird an die Administratoren der Firma gesendet.

Wenn ein Administrator eine Zertifikatanforderung genehmigt, prüft Adobe die Identität des Antragstellers. Adobe kontaktiert den Anforderer unter der Telefonnummer, die in seinem Profil aufgeführt ist.

Der Adobe-Administrator versucht, den Anforderer innerhalb von drei Tagen zweimal zu kontaktieren. Wenn der Adobe-Administrator den Anforderer nicht kontaktieren kann, hinterlässt er eine Meldung, in der er einen Rückruf anfordert, oder er gibt eine Zeit an, in der er erneut anrufen wird. Wenn der Adobe-Administrator den Anforderer nicht erreichen kann, wird eine E-Mail an die Administratoren gesendet.

>[!NOTE]
>
>Nur die Account- und Sekundaradministratoren können die Telefonnummer der Firma und die Wortgruppe des Anforderers ändern.

Wenn die Identität des Anforderers überprüft wird, erhält der Anforderer eine E-Mail mit der PKCS#7-Datei ( [!DNL p7b]).

Der Anforderer kann den PKCS#7-Inhalt aus dem E-Mail-Textkörper kopieren und in einer Datei speichern oder die Datei verwenden, die der E-Mail angehängt ist. Adobe empfiehlt, dass Sie beim Speichern der PKSC#7-Datei den Basisnamen verwenden, den Sie zum Generieren des privaten Schlüssels und der CSR-Datei verwendet haben.

>[!NOTE]
>
>Die an den Anforderer gesendete Datei enthält nur das Zertifikat. Die Datei enthält keine Informationen zum privaten Schlüssel.

