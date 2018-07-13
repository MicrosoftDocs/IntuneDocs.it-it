---
title: Configurare l'integrazione di Pradeo con Intune
titleSuffix: Intune on Azure
description: Integrazione del connettore Pradeo con Intune
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 82872ba6-80f8-4cc9-adf4-0ccd8ff26dd2
ms.openlocfilehash: 223161bd12f40b3539ce2502599eb3324c7458ca
ms.sourcegitcommit: f70d6aaea59b52cd0d7bd3008afd243868967fd6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37067490"
---
# <a name="integrate-pradeo-with-intune"></a>Integrare Pradeo con Intune

Seguire questa procedura per integrare la soluzione Pradeo Mobile Threat Defense (MTD) con Intune.

## <a name="before-you-begin"></a>Prima di iniziare

> [!NOTE]
> I passaggi seguenti devono essere completati nella [console di Pradeo Security](https://www.apps-security.com).

Prima di avviare il processo di integrazione di Pradeo con Intune, verificare che sia disponibile quanto segue:

-   Sottoscrizione di Microsoft Intune

-   Credenziali di amministratore di Azure Active Directory per concedere le autorizzazioni seguenti:

    -   Accesso e lettura del profilo utente

    -   Accesso alla directory come utente connesso

    -   Lettura dati directory

    -   Invio di informazioni sul dispositivo a Intune

-   Credenziali di amministratore per accedere alla console di Pradeo Security.

### <a name="pradeo-app-authorization"></a>Autorizzazione dell'app Pradeo

Il processo di autorizzazione dell'app Pradeo è il seguente:

-   Consentire al servizio Pradeo di comunicare a Intune informazioni relative allo stato di integrità dei dispositivi.

-   Pradeo esegue la sincronizzazione con l'appartenenza al gruppo di registrazione di Azure AD per popolare il relativo database del dispositivo.

-   Consentire alla console di amministrazione di Pradeo di usare la funzionalità Single Sign-On (SSO) di Azure AD.

-   Consentire all'app Pradeo di accedere usando la funzionalità SSO di Azure AD.

## <a name="to-set-up-pradeo-integration"></a>Per configurare l'integrazione di Pradeo

1.  Passare alla [console di Pradeo Security](https://www.apps-security.com) e accedere con le proprie credenziali.

2.  Scegliere **Administration - Enterprise Mobility Management** (Amministrazione - Gestione mobilità aziendale) dal menu.

3.  Scegliere il **logo Intune**.

4.  Nella finestra **EMM (Enterprise Mobility Management - Intune)** (EMM - Gestione mobilità aziendale - Intune) in **Step 1** (Passaggio 1) scegliere il pulsante **Pradeo Connector** (Connettore Pradeo). 

    ![Finestra Pradeo EMM Intune](./media/pradeo_setup.png)

5. Nella finestra di connessione a Microsoft Intune, immettere le credenziali di Intune.

5.  Verrà riaperta la pagina Web di Pradeo. In **Step 2** (Passaggio 2) scegliere il pulsante **Pradeo Device Health** (Integrità dispositivo Pradeo).

7. Nella finestra Pradeo-Intune Connector (Connettore Pradeo-Intune) scegliere **Accept** (Accetto). 

8. Nella finestra del connettore API per dispositivi Pradeo selezionare **Accept** (Accept).

9. Verrà riaperta la pagina Web di Pradeo. In **Step 3** (Passaggio 3) scegliere il pulsante **Connect to Microsoft** (Connetti a Microsoft). 

10. Nella finestra di autenticazione di Microsoft Intune immettere le credenziali di Intune.

11. Quando viene visualizzato il messaggio **Successful Integration** (Integrazione riuscita), l'integrazione è completa.

## <a name="next-steps"></a>Passaggi successivi

-   [Configurare app Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)