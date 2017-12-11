---
title: Integrare Zimperium con Intune
titleSuffix: Intune on Azure
description: Integrare Intune con Zimperium
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 363fd280-1865-4a61-855b-eb75c3c62753
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b4adb2db14c2e1c83be8e7b3644944c1910cb97
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2017
---
# <a name="integrate-zimperium-with-intune"></a>Integrare Zimperium con Intune

È necessario attenersi alla procedura che segue per integrare la soluzione Zimperium Mobile Threat Defense (MTD) con Intune.

## <a name="before-you-begin"></a>Prima di iniziare

> [!NOTE]
> Le operazioni seguenti devono essere eseguite nella [console di Zimperium MTD](https://staging2-console.zimperium.com).

Prima di avviare il processo di integrazione di Zimperium con Intune, verificare che sia disponibile quanto segue:

-   Sottoscrizione di Microsoft Intune

-   Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:

    -   Accesso e lettura del profilo utente

    -   Accesso alla directory come utente connesso

    -   Lettura dati directory

    -   Invio di informazioni sul dispositivo a Intune

-   Credenziali di amministratore per accedere alla console di Zimperium MTD.

### <a name="zimperium-app-authorization"></a>Autorizzazione dell'app Zimperium

Il processo di autorizzazione dell'app Zimperium è costituito dai seguenti passaggi:

-   Consentire al servizio Zimperium di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.

-   Zimperium esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.

-   Consentire alla console di amministrazione di Zimperium di usare la funzionalità Single Sign-On (SSO) di Azure AD.

-   Consentire all'app Zimperium di accedere usando la funzionalità SSO di Azure AD.

## <a name="to-set-up-zimperium-integration"></a>Per configurare l'integrazione con Zimperium

1.  Passare alla [console di Zimperium MTD](https://staging2-console.zimperium.com) e accedere con le proprie credenziali.

2.  Scegliere **Management** (Gestione) nel menu a sinistra.

3.  Scegliere la scheda **MDM Settings** (Impostazioni MDM).

4.  Scegliere **Add MDM** (Aggiungi MDM), quindi selezionare **Microsoft Intune** dall'elenco **dei provider MDM**.

5.  Dopo aver impostato Microsoft Intune come servizio di gestione dei dispositivi mobili (MDM), nella finestra di **configurazione di Microsoft Intune** scegliere **Add Azure Active Directory** (Aggiungi Azure Active Directory) per ogni opzione: **Zimperium zConsole** e **app zIPS iOS e Android** per autorizzare Zimperium a comunicare con Intune e Azure AD usando la funzionalità Single Sign-On di Azure Active Directory.

    > [!IMPORTANT]
    > È necessario aggiungere Zimperium zConsole e le app zIPS iOS e Android per completare il processo di integrazione con Intune.

6.  Scegliere **Accept** (Accetta) per autorizzare l'app Zimperium a comunicare con Intune e Azure Active Directory.

7.  Dopo aver aggiunto **Zimperium zConsole** e le app **zIPS iOS e Android** ad Azure AD, è necessario aggiungere i gruppi di sicurezza di Azure AD per consentire a Zimperium di sincronizzare il gruppo di sicurezza di Azure AD con il proprio servizio.

8.  Scegliere **Finish** (Fine) per salvare la configurazione e avviare la sincronizzazione del primo gruppo di sicurezza di Azure AD.

## <a name="next-steps"></a>Passaggi successivi

-   [Configurare le app di Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)