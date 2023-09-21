---
title: Vorhandenen DRM-Inhalt für die Verwendung von Cloud DRM aktualisieren (optional)
description: Vorhandenen DRM-Inhalt für die Verwendung von Cloud DRM aktualisieren (optional)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Vorhandenen DRM-Inhalt für die Verwendung von Cloud DRM aktualisieren (optional) {#update-existing-drm-content-to-use-cloud-drm-optional}

Wenn Sie über eine vorhandene, durch Primetime DRM geschützte Inhaltsbibliothek verfügen, ist es möglich, den vorhandenen Inhalt für die Verwendung des Primetime Cloud DRM-Dienstes &quot;erneut zu komprimieren&quot;und die ursprünglichen Quelldateien nicht erneut zu verpacken/zu verschlüsseln. Beim erneuten Headern des Inhalts werden lediglich die DRM-Metadaten des Inhalts im HLS-Manifest aktualisiert. Es wird keine Entschlüsselung/erneute Verschlüsselung des ursprünglichen Assets durchgeführt. Dies kann eine nützliche Option sein, wenn der ursprüngliche Quellinhalt nicht verfügbar ist oder wenn Bedenken hinsichtlich der Menge der Ressourcen bestehen, die zum erneuten Verpacken einer großen Bibliothek erforderlich sind.

Es ist möglich, das Primetime DRM Java SDK zu verwenden, um die Metadaten programmgesteuert zu aktualisieren. Darüber hinaus wird die [!DNL OfflinePackager.jar] Das in diesem Schutzkit enthaltene Befehlszeilen-Tool kann diese Aufgabe auch mithilfe der `-drm_refresh` -Option.

## Details der Kopfzeile {#section_3F3980D8E775450588C64E02A8448189}

Bei der Neubearbeitung müssen die folgenden Felder aktualisiert werden, damit CloudDRM verwendet werden kann:

* Lizenzserver-URL (zu [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* Lizenzserver-Zertifikat (an das CloudDRM-Lizenzserverzertifikat)
* Transportbescheinigung (in das CloudDRM-Transportzertifikat)
* Paketberechtigung (an die Paketberechtigung, die Sie für die Verwendung mit CloudDRM aktiviert haben)

## Finden der DRM-Metadaten {#section_28721CB7966F40708AEC8637F2E9BB72}

Inhalte, die HTTP-Technologie verwenden (z. B. HDS oder HLS), verwenden ein Manifest, das auf die DRM-Metadaten des Adobe-Zugriffs verweist. In HDS werden die Metadaten durch die `<drmmeta>` und in HLS durch die Variable `#EXT-X-FAXS-CM` -Tag. In beiden Szenarien können die Metadaten inline im Manifest als base-64-kodierter Blob oder extern als Binärdatei referenziert werden. Wenn die Metadaten im Manifest eingebettet/inline sind, müssen Sie die Metadaten möglicherweise zuerst base64-dekodieren, bevor Sie diese Daten zur Instanziierung von DRM-Metadaten verwenden.

## Verwenden der im Lieferumfang enthaltenen Datei OfflinePlayer.jar {#section_37C2091856E44AA380D742C72B4DD1A7}

Lieferung der `-drm_refresh option` zur Befehlszeile. Eine neue Manifestdatei wird mit aktualisierten DRM-Metadaten erstellt, während der Inhalt nicht erneut verschlüsselt wird.

## Verwenden des Primetime DRM Java SDK zum erneuten Header {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

Die Aktualisierung vorhandener DRM-Metadaten kann mithilfe des Primetime DRM (ehemals Adobe Access DRM) Java SDK für einen programmatischen Ansatz durchgeführt werden. Weitere Informationen finden Sie im Abschnitt [!DNL RegenerateMetadata.java] Codebeispiel in [!DNL /Reference Implmentation/Command Line Tools/samples/] -Paket des SDK. Das Adobe Access Java SDK ist nicht Teil dieses CloudDRM Protection Kits und muss direkt von Adobe erworben werden. Für weitere Informationen wenden Sie sich bitte an Ihren Adobe-Ansprechpartner.
