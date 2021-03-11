---
title: Vorhandene DRM-Inhalte für die Verwendung von Cloud DRM aktualisieren (Optional)
description: Vorhandene DRM-Inhalte für die Verwendung von Cloud DRM aktualisieren (Optional)
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Vorhandenen DRM-Inhalt für die Verwendung von Cloud DRM aktualisieren (Optional) {#update-existing-drm-content-to-use-cloud-drm-optional}

Wenn Sie über eine vorhandene, durch Primetime DRM geschützte Inhaltsbibliothek verfügen, ist es möglich, die vorhandenen Inhalte zu &quot;reheader&quot;zu machen, um den Primetime Cloud DRM-Dienst zu verwenden, anstatt die ursprünglichen Quelldateien erneut verpacken/verschlüsseln zu müssen. Beim erneuten Headern des Inhalts werden einfach die DRM-Metadaten des Inhalts im HLS-Manifest aktualisiert. Es wird keine Entschlüsselung/erneute Verschlüsselung des Originalassets durchgeführt. Diese Option kann nützlich sein, wenn der ursprüngliche Quellinhalt nicht verfügbar ist oder wenn Bedenken hinsichtlich der erforderlichen Ressourcen zum erneuten Verpacken einer großen Bibliothek bestehen.

Sie können das Primetime DRM Java SDK verwenden, um die Metadaten programmgesteuert zu aktualisieren. Darüber hinaus kann das in diesem Schutzkit enthaltene Befehlszeilenwerkzeug [!DNL OfflinePackager.jar] diese Aufgabe auch mit der Option `-drm_refresh` durchführen.

## Details der neuen Kopfzeile {#section_3F3980D8E775450588C64E02A8448189}

Beim erneuten Bearbeiten von Headern müssen die folgenden Felder aktualisiert werden, um CloudDRM verwenden zu können:

* Lizenzserver-URL (zu [!DNL ht<span></span>tps://access.adobeprimetime.com/flashaccessserver/axs_prod])
* Lizenzserverzertifikat (in das CloudDRM-Lizenzserverzertifikat)
* Transportbescheinigung (in das CloudDRM-Transportzertifikat)
* Packager-Berechtigung (für die Paketberechtigung, die Sie für die Verwendung mit CloudDRM aktiviert haben)

## Suchen der DRM-Metadaten {#section_28721CB7966F40708AEC8637F2E9BB72}

Bei Inhalten, die HTTP-Technologie verwenden (z. B. HDS oder HLS), wird ein Manifest verwendet, das auf die DRM-Metadaten für den Zugriff auf die Adobe verweist. In HDS werden die Metadaten vom `<drmmeta>`-Tag referenziert und in HLS vom `#EXT-X-FAXS-CM`-Tag. In beiden Szenarien können die Metadaten als Base-64-kodierter Block im Manifest oder extern als Binärdatei referenziert werden. Wenn die Metadaten im Manifest eingebettet/eingebettet sind, müssen Sie die Metadaten zunächst base64-dekodieren, bevor Sie diese Daten zur Instanziierung der DRM-Metadaten verwenden.

## Verwenden der im Lieferumfang enthaltenen Datei OfflinePacger.jar {#section_37C2091856E44AA380D742C72B4DD1A7}

Geben Sie `-drm_refresh option` an die Befehlszeile an. Eine neue Manifestdatei wird mit aktualisierten DRM-Metadaten erstellt, während der Inhalt nicht erneut verschlüsselt wird.

## Verwenden des Primetime DRM Java SDK to Re-Header {#section_7EDBAC4C78DF4CD5BE8410EEAD8437A2}

Die Aktualisierung vorhandener DRM-Metadaten kann mithilfe des Primetime DRM (früher Adobe Access DRM) Java SDK für einen programmatischen Ansatz durchgeführt werden. Weitere Informationen finden Sie im Codebeispiel [!DNL RegenerateMetadata.java] im [!DNL /Reference Implmentation/Command Line Tools/samples/]-Paket des SDK. Das Java-SDK für Adobe Access ist nicht Bestandteil dieses CloudDRM-Schutzkits und muss direkt von der Adobe erworben werden. Für weitere Informationen wenden Sie sich bitte an Ihren Ansprechpartner bei der Adobe.