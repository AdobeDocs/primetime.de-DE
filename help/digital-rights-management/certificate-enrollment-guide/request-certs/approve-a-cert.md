---
description: 'null'
seo-description: 'null'
seo-title: Zertifikat genehmigen (Konto oder Sekundär)
title: Zertifikat genehmigen (Konto oder Sekundär)
uuid: 5b95e2e8-abe9-4aef-bcb4-9b98ba6604d1
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# Zertifikat genehmigen (Konto oder Sekundär Administrator){#approve-a-certificate-account-or-secondary-administrator}

1. Melden Sie sich bei der Zertifikatregistrierungssite an.
1. Wählen Sie die Registerkarte **[!UICONTROL Certificates]**.
1. Überprüfen Sie anhand der Anforderung, ob die Anforderung gültig ist.
1. Wenn die Anforderung gültig ist, klicken Sie auf **[!UICONTROL Approve]**.

   Sie können auch einen Kommentar hinzufügen. Eine E-Mail wird an den Anforderer gesendet, in der darauf hingewiesen wird, dass die Anfrage von einem der Administratoren der Firma genehmigt wurde. Eine Kopie dieser E-Mail wird an die Firma- und Adobe-Administratoren gesendet.

1. Wenn die Anforderung ungültig ist, klicken Sie auf **[!UICONTROL Reject]** und geben Sie im Bestätigungsdialogfeld einen Kommentar ein.

   Eine E-Mail wird an den Anforderer gesendet, in der darauf hingewiesen wird, dass der Antrag von einem der Administratoren der Firma abgelehnt wurde. Eine Kopie dieser E-Mail wird an die Administratoren der Firma gesendet.

Wenn ein Administrator eine Zertifikatanforderung genehmigt, überprüft die Adobe die Identität des Antragstellers. Die Adobe kontaktiert den Antragsteller unter der Telefonnummer, die in ihrem Profil angegeben ist.

Der Administrator der Adobe versucht, innerhalb von drei Tagen zweimal mit dem Antragsteller Kontakt aufzunehmen. Wenn der Administrator der Adobe den Anforderer nicht kontaktieren kann, hinterlässt er eine Meldung, in der er einen Rückruf anfordert, oder er gibt eine Uhrzeit an, zu der er erneut anrufen wird. Wenn der Administrator der Adobe nicht in der Lage ist, den Anforderer zu erreichen, wird eine E-Mail an die Administratoren gesendet.

>[!NOTE]
>
>Die Telefonnummer der Firma und die Wortgruppe des Anforderers können nur von den Kontoadministratoren und den Sekundär-Administratoren geändert werden.

Wenn die Identität des Anforderers überprüft wird, erhält der Anforderer eine E-Mail mit der PKCS#7-Datei ( [!DNL p7b]).

Der Anforderer kann den PKCS#7-Inhalt aus dem E-Mail-Textkörper kopieren und in einer Datei speichern oder die Datei verwenden, die der E-Mail angehängt ist. Adobe empfiehlt, dass Sie beim Speichern der PKSC#7-Datei den Basisnamen verwenden, mit dem Sie den privaten Schlüssel und die CSR-Datei generiert haben.

>[!NOTE]
>
>Die an den Anforderer gesendete Datei enthält nur das Zertifikat. Die Datei enthält keine Informationen zum privaten Schlüssel.

