---
title: Sicheres Speichern von Richtlinien
description: Sicheres Speichern von Richtlinien
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Sicheres Speichern von Richtlinien{#securely-storing-policies}

Adobe Access SDK bietet eine große Flexibilität bei der Entwicklung von Anwendungen zur Verwendung bei der Inhaltspaketung und der Erstellung von Richtlinien. Bei der Erstellung solcher Anwendungen sollten Sie einigen Benutzern erlauben, Richtlinien zu erstellen und zu ändern und andere Benutzer so zu beschränken, dass sie nur vorhandene Richtlinien auf Inhalte anwenden können. In diesem Fall müssen Sie die erforderlichen Zugriffskontrollen implementieren, um Benutzerkonten mit unterschiedlichen Berechtigungen für die Richtlinienerstellung und die Anwendung von Richtlinien auf Inhalte zu erstellen.

Richtlinien werden erst dann unterzeichnet oder anderweitig vor Änderungen geschützt, wenn sie in der Verpackung verwendet werden. Wenn Sie sich wegen der Benutzer Ihrer Verpackungswerkzeuge, die Richtlinien ändern, Sorgen machen, sollten Sie die Richtlinien unterschreiben, um sicherzustellen, dass sie nicht geändert werden können.

Weitere Informationen zum Erstellen von Anwendungen mit dem SDK finden Sie unter *Adobe Access API-Referenz*.
