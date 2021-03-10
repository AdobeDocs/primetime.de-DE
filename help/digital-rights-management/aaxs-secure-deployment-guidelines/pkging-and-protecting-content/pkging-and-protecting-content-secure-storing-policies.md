---
title: Sicheres Speichern von Richtlinien
description: Sicheres Speichern von Richtlinien
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Sicheres Speichern von Richtlinien{#securely-storing-policies}

Adobe Access SDK bietet eine große Flexibilität bei der Entwicklung von Applikationen für die Inhaltspakete und die Erstellung von Richtlinien. Beim Erstellen solcher Anwendungen möchten Sie möglicherweise einigen Benutzern erlauben, Richtlinien zu erstellen und zu ändern und andere Benutzer so zu beschränken, dass sie nur vorhandene Richtlinien auf Inhalte anwenden können. In diesem Fall müssen Sie die erforderlichen Zugriffskontrollen implementieren, um Benutzerkonten mit unterschiedlichen Berechtigungen für die Richtlinienerstellung und die Anwendung von Richtlinien auf Inhalte zu erstellen.

Richtlinien werden erst dann unterzeichnet oder anderweitig vor Änderungen geschützt, wenn sie in der Verpackung verwendet werden. Wenn Sie Bedenken haben, dass Benutzer Ihrer Verpackungswerkzeuge Richtlinien ändern, sollten Sie die Richtlinien unterschreiben, um sicherzustellen, dass sie nicht geändert werden können.

Weitere Informationen zum Erstellen von Anwendungen mit dem SDK finden Sie in der *API-Referenz für den Zugriff auf Adoben*.
