---
description: Um mit der Primetime DRM Cloud mit ExpressPlay zu beginnen, müssen Sie Adobe Cert- und ExpressPlay-Konten mithilfe Ihres Adobe-Kundenbetreuers einrichten.
seo-description: Um mit der Primetime DRM Cloud mit ExpressPlay zu beginnen, müssen Sie Adobe Cert- und ExpressPlay-Konten mithilfe Ihres Adobe-Kundenbetreuers einrichten.
seo-title: Bereitstellung (Konten usw.)
title: Bereitstellung (Konten usw.)
uuid: 51b95676-2121-4d8b-8756-9fd097185a13
translation-type: tm+mt
source-git-commit: 9792aff8586c46aabb5bfb70864cfe98c28e602d

---


# Bereitstellung (Konten usw.) {#get-provisioned-accounts-etc}

Um mit der Primetime DRM Cloud mit ExpressPlay zu beginnen, müssen Sie Adobe Cert- und ExpressPlay-Konten mithilfe Ihres Adobe-Kundenbetreuers einrichten.

1. Wenden Sie sich an Ihren Adobe-Kundenbetreuer und fordern Sie die Adobe Cert- und ExpressPlay-Konten an, die Sie für die Implementierung von Multi-DRM mit TVSDK benötigen.

       Geben Sie Ihrem Adobe-Kundenbetreuer die E-Mail-Adresse ein, die Sie als Kontaktstelle verwenden werden. Adobe erstellt dann zwei Konten für Sie:
   
   * ***Certificate Portal-Konto*** - (<span></span>https://certportal.primetime.adobe.com): Das *Adobe Access/Primetime-DRM-Zertifikatregistrierungsteam* sendet eine E-Mail an die angegebenen Adressen. Die E-Mail enthält die URL für das Adobe-Zertifikat-Portal sowie einen Link zur Adobe-Dokumentation zur Zertifikatregistrierung (die neuesten Dokumente finden Sie hier: Handbuch zur [Zertifikatregistrierung](../../../digital-rights-management/certificate-enrollment-guide/about-certs.md)).

   * ***ExpressPlay-Konto*** - Adobe sendet Ihnen eine E-Mail mit einem Link, den Sie zur Registrierung für Ihr ExpressPlay-Admin-Konto verwenden.

1. Melden Sie sich mit Ihrer Adobe-ID beim Adobe-Zertifikat-Portal an (verwenden Sie die gleiche E-Mail-Adresse wie Ihr Adobe-Vertreter). Wenn Sie noch keine Adobe-ID haben, können Sie eine schnell erstellen, indem Sie den Link &quot;Adobe ID ** abrufen&quot;im Zertifikat-Portal befolgen:

   <!--<a id="fig_mst_gtj_wv"></a>-->

   ![](assets/cert_portal_sign-in-page-web.png)

1. Fordern Sie im Adobe Cert-Portal ein *Trial* -Zertifikat an.

   Für die Multi-DRM-Testversion wird eine einzige Testausgabe alle folgenden Aspekte des Inhaltsschutzes abdecken: Verpackung, Lizenzierung und Transport. Sie müssen Ihre eigene [CSR](../../../digital-rights-management/certificate-enrollment-guide/request-certs/gen-cert-signing-req.md) angeben, um eine Anforderung für ein Zertifikat zu stellen:
   <!--<a id="fig_op1_xwj_wv"></a>-->

   ![](assets/cert_portal_trial_request-web.png)

   Adobe sendet Ihnen eine E-Mail, die auf die Annahme oder Ablehnung Ihrer Anforderung hinweist. Sie können den Status Ihrer Zertifikatsanforderung(en) auf der Registerkarte &quot; *Anforderungsverlauf* &quot;im cert-Portal anzeigen:
   <!--<a id="fig_gkl_myj_wv"></a>-->

   ![](assets/cert_portal_request_history-web.png)

1. Erstellen Sie Ihr ExpressPlay Admin-Konto.

   Folgen Sie dem Link zu ExpressPlay, den Adobe Ihnen bereitgestellt hat. Dadurch wird die Seite &quot;Konto ** erstellen&quot;bei ExpressPlay geöffnet. Füllen Sie die erforderlichen Informationen aus und senden Sie das Formular ab. Sie erhalten eine E-Mail von `operations@expressplay.com` einem Link zur Aktivierung, der eine Woche lang gültig ist. Richten Sie nach der Aktivierung Ihren ExpressPlay-Dienst ein:
   <!--<a id="fig_cjl_ztk_wv"></a>-->

   ![](assets/expressplay_create_service-web.png)

   Nachdem Sie Ihren Dienst erstellt haben, wird Ihnen Ihre eigene Admin-Seite angezeigt. Neben einigen Verfolgungsfeldern für Aktivitäten sehen Sie Ihre Produktions- und *Test-Kundenauthentifikatoren* (API-Schlüssel) und Ihre Produktions- und Test-Dienst-URLs:

   <!--<a id="fig_c5h_xdl_wv"></a>-->

   ![](assets/expressplay_admin_dashboard_2-web.png) ![](assets/expressplay_admin_dashboard-web.png)

1. Wenn Sie FairPlay verwenden, sind weitere Schritte erforderlich (auf der Apple Developer-Website), um ExpressPlay einzurichten. Anweisungen finden Sie unter [Aktivieren des ExpressPlay-Dienstes für FairPlay](../../multi-drm-workflows/p-l-and-p/fairplay-workflow.md#enable-expressplay-service-for-fairplay) .
