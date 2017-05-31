---
title: Usare i criteri per semplificare la gestione dei PC Windows | Documentazione Microsoft
description: Descrive i criteri di gestione dei PC Windows ed elenca le impostazioni per Microsoft Intune Center.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a2b956f8c999ec5489152a63a9af6e24da8ec536
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="use-policies-to-simplify-windows-pc-management"></a>Usare i criteri per semplificare la gestione dei PC

Per gestire i desktop di Windows come PC, eseguendo il client software di Intune su di essi, è possibile usare solo i criteri in **Gestione computer** nella console di amministrazione di Intune. Tutti gli altri criteri elencati nella console di amministrazione sono destinati solo ai dispositivi mobili. I criteri **Gestione computer** consentono di configurare le impostazioni in Microsoft Intune Center, controllare gli aggiornamenti dei PC e configurare Windows Firewall per i PC.

![Modello di criteri per PC Windows](../media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Gestire Microsoft Intune Center
Gli utenti visualizzano il client software di Intune come **Microsoft Intune Center**. Microsoft Intune Center consente agli utenti di:

-   Ottenere applicazioni dal portale aziendale.

-   Verificare la disponibilità di aggiornamenti.

-   Gestire Microsoft Intune Endpoint Protection.

-  Richiedere assistenza remota.

Microsoft Intune Center viene installato su tutti i computer gestiti. È possibile configurare le seguenti impostazioni in un criterio di Intune e visualizzarle in Microsoft Intune Center:

|Impostazione criterio|Dettagli|
|------------------|--------------------|
|**Nome**|Il nome dell'amministratore che gestisce il computer.<br />Lunghezza massima: 40 caratteri|
|**Numero di telefono**|Il numero di telefono dell'amministratore che gestisce il computer.<br />Lunghezza massima: 20 caratteri|
|**Indirizzo di posta elettronica**|L'indirizzo di posta elettronica dell'amministratore che gestisce il computer.<br />Lunghezza massima: 40 caratteri|
|**Nome sito Web**|Il nome del sito Web di supporto per gli utenti.<br />>Lunghezza massima: 40 caratteri|
|**URL sito Web**|L'URL del sito Web di supporto.<br />Lunghezza massima: 150 caratteri|
|**Note**|Una nota che viene visualizzata agli utenti.<br />Lunghezza massima: 120 caratteri|

Vedere le risorse seguenti per informazioni sui criteri e le impostazioni che è possibile configurare per i PC Windows:

- [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md). Questi criteri determinano che i computer gestiti cerchino e scarichino gli aggiornamenti software di Microsoft e di terze parti. Questi aggiornamenti non includono gli aggiornamenti del sistema operativo (ad esempio, l'aggiornamento da Windows 7 a Windows 10 o gli aggiornamenti da una versione di Windows 10 a una versione successiva).

- [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md). Queste impostazioni includono le analisi pianificate e le azioni da intraprendere quando viene rilevato il malware.

- [Proteggere i PC Windows con criteri di Windows Firewall in Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md). Questi criteri semplificano l'amministrazione delle impostazioni di Windows Firewall sui computer gestiti.


### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
