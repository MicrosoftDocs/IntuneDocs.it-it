---
title: Assegnare le licenze di Intune | Microsoft Docs
description: Assegnare licenze agli utenti per la sottoscrizione di Intune
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 03/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb4314ea-88b5-44d3-92ce-4c6aff0587a4
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 793df9f3734b84c74ecac9b8192d0b06306607e8
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="assign-intune-licenses-to-your-user-accounts"></a>Assegnare le licenze di Intune agli account utente

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Indipendentemente dal fatto che si decida di aggiungere gli utenti manualmente o di sincronizzarli da Active Directory locale, è necessario assegnare una licenza di Intune a ogni utente prima che gli utenti possano registrare i propri dispositivi in Intune.

## <a name="assign-an-intune-license-in-the-office-365-admin-center"></a>Assegnare una licenza di Intune nell'interfaccia di amministrazione di Office 365

È possibile usare il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) per aggiungere manualmente gli utenti basati su cloud e assegnare licenze sia ad account utente basati su cloud che ad account sincronizzati con Azure AD da Active Directory locale.

1.  Accedere al [portale di gestione di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) usando le credenziali di amministratore tenant e quindi scegliere **Utenti** > **Utenti attivi**.

2.  Selezionare l'account utente a cui si vuole assegnare una licenza utente di Intune e quindi scegliere **Licenze di prodotto** > **Modifica**.

3.  Impostare sulla posizione **Attivato** l'interruttore per **Intune** o **Enterprise Mobility + Security** e scegliere **Salva**.

4. L'account utente dispone ora delle autorizzazioni necessarie per usare il servizio e registrare dispositivi nella gestione.

> [!NOTE]
> Gli utenti verranno visualizzati nella console di amministrazione solo dopo aver registrato un dispositivo. È anche possibile selezionare un gruppo di utenti per modificare le licenze contemporaneamente, selezionando le opzioni per aggiungere o sostituire una licenza per tutti gli utenti selezionati.

## <a name="use-school-data-sync-to-assign-licenses-to-users-in-intune-for-education"></a>Usare School Data Sync per assegnare licenze Education agli utenti di Intune
Le organizzazioni che operano nel settore dell'istruzione possono usare School Data Sync (SDS) per assegnare licenze Intune per Education agli utenti sincronizzati. È sufficiente selezionare la casella di controllo Intune per Education durante la configurazione del profilo SDS.  

![Immagine dell'impostazione del profilo SDS](./media/i4e-sds-profile-setup-setting.png)

Quando si assegna una licenza Intune per Education, assicurarsi di assegnare anche una licenza di Intune A Direct.

![Immagine della configurazione della licenza del prodotto](./media/i4e-set-licenses.png)

Per altre informazioni su SDS, vedere questa [panoramica di School Data Sync](https://support.office.com/en-us/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91?ui=en-US&rs=en-US&ad=US).

## <a name="use-powershell-to-selectively-manage-ems-user-licenses"></a>Usare PowerShell per gestire in modo selettivo le licenze utente di EMS
Le organizzazioni che usano Microsoft Enterprise Mobility Suite + Security (precedentemente noto come Enterprise Mobility Suite) possono contenere utenti che necessitano solo di Azure Active Directory Premium o dei servizi di Intune nel pacchetto EMS. È possibile assegnare un servizio o un sottoinsieme di servizi tramite i [cmdlet di PowerShell per Azure Active Directory](https://msdn.microsoft.com/library/jj151815.aspx).

Per assegnare in modo selettivo le licenze utente per i servizi EMS, aprire PowerShell come amministratore su un computer dotato del [Modulo di Azure Active Directory per Windows PowerShell](https://msdn.microsoft.com/library/jj151815.aspx#bkmk_installmodule). È possibile installare PowerShell su un computer locale o su un server ADFS.

È necessario creare una nuova definizione dello SKU della licenza da applicare solo ai piani del servizio desiderati. A tale scopo, disabilitare i piani a cui non si desidera applicare la nuova definizione. Ad esempio, è possibile creare una definizione dello SKU che non assegna una licenza di Intune. Per visualizzare un elenco dei servizi disponibili, digitare:

    (Get-MsolAccountSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus

È possibile eseguire il comando seguente per escludere il piano di servizio di Intune. È possibile usare lo stesso metodo per espandere un intero gruppo di sicurezza o usare filtri più granulari.

**Esempio 1**<br>
Creare un nuovo utente nella riga di comando e assegnare una licenza di EMS senza abilitare la parte di Intune della licenza:

    Connect-MsolService

    New-MsolUser -DisplayName “Test User” -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS


Verificare con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

**Esempio 2**<br>
Disabilitare la parte di Intune della licenza EMS per un utente a cui è già stata assegnata una licenza:

    Connect-MsolService

    $CustomEMS = New-MsolLicenseOptions -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
    Set-MsolUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS

Verificare con:

    (Get-MsolUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus

![PoSH-AddLic-Verify](./media/posh-addlic-verify.png)

>[!div class="step-by-step"]

>[&larr; **Sync users to Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md) (Sincronizzare utenti su Intune) [**Organize users and devices** (Organizzare utenti e dispositivi) &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)  
