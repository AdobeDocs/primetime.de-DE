---
description: Für die ersten Schritte mit der Primetime DRM Cloud, powered by ExpressPlay, müssen Sie mithilfe Ihres Adobe-Kundenbetreuers Adobe Cert- und ExpressPlay-Konten einrichten.
title: Bereitstellung (Konten usw.)
exl-id: 2543d997-3495-4545-9395-072c07431aba
source-git-commit: a0917e128862184ce18050792c2ee2ac265050d2
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Bereitstellung (Konten usw.) {#get-provisioned-accounts-etc}

Für die ersten Schritte mit der Primetime DRM Cloud, powered by ExpressPlay, müssen Sie mithilfe Ihres Adobe-Kundenbetreuers Adobe Cert- und ExpressPlay-Konten einrichten.

1. Wenden Sie sich an Ihren Kundenbetreuer und fordern Sie die Adobe Cert- und ExpressPlay-Konten an, die Sie für die Implementierung von Multi-DRM mit TVSDK benötigen.

   Geben Sie Ihrem Ansprechpartner für die Adobe die E-Mail-Adresse an, die Sie als Kontaktstelle verwenden werden. Adobe erstellt dann zwei Konten für Sie:

   * ***Certificate Portal-Konto*** - ( https://certportal.primetime.adobe.com) : Die *Adobe Access/Primetime DRM Certificate Enrollment Management Team* sendet eine E-Mail an die von Ihnen angegebenen Adressen. Die E-Mail enthält die URL für das Adobe-Zertifikatsportal sowie einen Link zur Dokumentation zur Zertifikatregistrierung der Adobe (aktuelle Dokumente finden Sie hier: [Handbuch zur Zertifikatregistrierung](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***ExpressPlay-Konto*** - Adobe sendet Ihnen eine E-Mail mit einem Link, den Sie zur Registrierung für Ihr ExpressPlay Admin-Konto verwenden.

1. Melden Sie sich mit Ihrer Adobe ID beim Adobe-Zertifikatportal an (verwenden Sie dieselbe E-Mail-Adresse wie bei Ihrem Kundenbetreuer). Wenn Sie noch keine Adobe ID haben, können Sie schnell eine erstellen, indem Sie der *Adobe ID abrufen* Link vom cert portal:

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Fordern Sie im Adobe Cert-Portal eine *Testversion* cert.

   Im Rahmen der Multi-DRM-Studie wird eine einzige Testausstellung alle Aspekte des Inhaltsschutzes abdecken: Verpackung, Lizenzierung und Transport. Sie müssen Ihre eigenen [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) , um eine Anforderung für ein Zertifikat zu stellen:
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe sendet Ihnen eine E-Mail, die die Annahme oder Ablehnung Ihrer Ausstellungsanfrage anzeigt. Sie können den Status Ihrer Cert-Anforderung(en) auf der *Anforderungsverlauf* im cert portal:
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Erstellen Sie Ihr ExpressPlay Admin-Konto.

   Folgen Sie dem Link zu ExpressPlay dieser Adobe. Dadurch wird die *Konto erstellen* Seite bei ExpressPlay. Füllen Sie die erforderlichen Informationen aus und senden Sie das Formular. Sie erhalten eine E-Mail von `operations@expressplay.com` enthält einen Aktivierungslink, der eine Woche lang gültig ist. Richten Sie nach der Aktivierung Ihren ExpressPlay-Dienst ein:
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Wenn Sie Ihren Dienst erstellt haben, erhalten Sie Ihre eigene Admin-Seite. Neben einigen Aktivitäten-Tracking-Feldern sehen Sie Ihre Produktion und Ihren Test *Kundenauthentifikatoren* (API-Schlüssel) und Ihre Produktions- und Testdienst-URLs:

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Wenn Sie FairPlay verwenden, sind (auf der Apple-Entwicklersite) zusätzliche Schritte erforderlich, um ExpressPlay einzurichten. Siehe [ExpressPlay-Dienst für FairPlay aktivieren](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) für Anweisungen.
