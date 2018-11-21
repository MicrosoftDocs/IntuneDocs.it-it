---
title: Esercitazione - Proteggere la posta elettronica di Exchange Online nei dispositivi gestiti con Intune
titlesuffix: Microsoft Intune
description: Informazioni su come proteggere Exchange Online con criteri di conformità di Intune iOS e l'accesso condizionale di Azure AD per richiedere dispositivi gestiti e l'app Outlook.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 09/19/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e88108d6c438bf2c192516be44908c4d76dfa9f
ms.sourcegitcommit: ba0699cc351954960b222223c60c4ecd50edc829
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49652122"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Esercitazione: Proteggere la posta elettronica di Exchange Online nei dispositivi gestiti
Informazioni sull'uso dei criteri di conformità dei dispositivi con accesso condizionale per assicurarsi che i dispositivi iOS possano accedere alla posta elettronica di Exchange Online solo se vengono gestiti da Intune e con un'app di posta elettronica approvata. 

In questa esercitazione si apprenderà come: 
> [!div class="checklist"]
> * Creare criteri di conformità per i dispositivi iOS di Intune per impostare le condizioni che deve soddisfare un dispositivo per essere considerato conforme.
> * Creare criteri di accesso condizionale di Azure Active Directory (Azure AD) che richiedono che i dispositivi iOS siano registrati in Intune, siano conformi ai criteri di Intune e usino l'app per dispositivi mobili Outlook approvata per accedere alla posta elettronica di Exchange Online.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
  - Per questa esercitazione sarà necessario un tenant di test con le sottoscrizioni seguenti:
    - Azure Active Directory Premium ([versione di valutazione gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Abbonamento a Office 365 Business che include Exchange ([versione di valutazione gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))
  - Prima di iniziare, creare un profilo di dispositivo di test per i dispositivi iOS, seguendo le procedure descritte in [Guida introduttiva: creare un profilo di posta elettronica del dispositivo per iOS](quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. Si accede a Intune nel portale di Azure scegliendo **Tutti i servizi** > **Intune**.

## <a name="create-the-ios-device-compliance-policy"></a>Creare i criteri di conformità del dispositivo per iOS
Configurare i criteri di conformità del dispositivo di Intune per impostare le condizioni che deve soddisfare un dispositivo per essere considerato conforme. Per questa esercitazione verranno creati criteri di conformità per i dispositivi iOS. I criteri di conformità sono specifici della piattaforma, pertanto sono necessari criteri di conformità separati per ogni piattaforma del dispositivo da valutare.

1.  In Intune selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2.  In **Nome** immettere **Test criteri di conformità iOS**. 
3.  In **Descrizione** immettere **Test criteri di conformità iOS**.
4.  In **Piattaforma** selezionare **iOS**. 
5.  Selezionare **Impostazioni** > **Posta elettronica**. 
     
    1.  Accanto a **Rendi obbligatorio un profilo di posta elettronica gestito nei dispositivi mobili** selezionare **Rendi obbligatorio**.
    2. Selezionare **OK**.

    ![Impostare i criteri di conformità per la posta elettronica per richiedere un profilo di posta elettronica gestito](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6.  Selezionare **Integrità del dispositivo**. Accanto a **Dispositivi Jailbroken** selezionare **Blocca** e quindi selezionare **OK**.
7.  Selezionare **Sicurezza del sistema** e immettere le impostazioni **Password**. Per questa esercitazione, selezionare le seguenti impostazioni consigliate:
     
    - Per **Richiedi una password per sbloccare i dispositivi mobili** selezionare **Rendi obbligatorio**.
    - Per **Password semplici** selezionare **Blocca**.
    - Per **Lunghezza minima password** immettere **4**.
    - Per **Tipo di password richiesto** scegliere **Alfanumerico**.
    - Per **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password** scegliere **Immediatamente**.
    - Per **Scadenza password (giorni)** immettere **41**.
    - Per **Numero di password precedenti di cui impedire il riutilizzo** immettere **5**.
 
    ![Configurare le impostazioni per la password per i criteri di conformità della posta elettronica](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8.  Selezionare **OK** e quindi di nuovo **OK**.
9.  Selezionare **Crea**.

## <a name="create-the-conditional-access-policy"></a>Creare i criteri di accesso condizionale
A questo punto si creeranno criteri di accesso condizionale che richiedono che tutte le piattaforme di dispositivi prevedano la registrazione in Intune e siano conformi ai criteri di conformità di Intune prima di poter accedere a Exchange Online. Verrà anche richiesto l'uso dell'app Outlook per l'accesso alla posta elettronica. I criteri di accesso condizionale sono configurabili nel portale di Azure AD o nel portale di Intune. Dato che finora è stato usato il portale di Intune, i criteri verranno creati in questo portale.
1.  In Intune selezionare **Accesso condizionale** > **Criteri** > **Nuovi criteri**.
1.  In **Nome** immettere **Criteri di test per posta elettronica Office 365**. 
3.  In **Assegnazioni** selezionare **Utenti e gruppi**. Nella scheda **Includi** selezionare **Tutti gli utenti** e quindi selezionare **Fine**.

4.  In **Assegnazioni** selezionare **App cloud**. Dato che si vuole proteggere la posta elettronica di Office 365 Exchange Online, si selezionerà questa app tramite la procedura seguente:
     
    1. Nella scheda **Includi** scegliere **Selezionare le app**.
    2. Scegliere **Seleziona**. 
    3. Nell'elenco delle applicazioni selezionare **Office 365 Exchange Online** e quindi scegliere **Seleziona**. 
    4. Seleziona **Chiudi**.
  
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5.  In **Assegnazioni** selezionare **Condizioni** > **Piattaforme del dispositivo**.
     
    1. In **Configura** selezionare **Sì**.
    2. Nella scheda **Includi** selezionare **Tutte le piattaforme (incluse quelle non supportate)** e quindi selezionare **Fine**. 
    3. Selezionare di nuovo **Fine**.
   
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6.  In **Assegnazioni** selezionare **Condizioni** > **App client**.
     
    1. In **Configura** selezionare **Sì**.
    2. Per questa esercitazione, selezionare **App per dispositivi mobili e client desktop** e **Client con autenticazione moderna** (che fa riferimento ad app come Outlook per iOS e Outlook per Android). Deselezionare tutte le altre caselle di controllo.
    3. Selezionare **Fine** e quindi di nuovo **Fine**.
    
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7.  In **Controlli di accesso** selezionare **Concedi**. 
     
    1. Nel riquadro **Concedi** selezionare **Concedi accesso**.
    2. Selezionare **Richiedi che i dispositivi siano contrassegnati come conformi**. 
    3. Selezionare **Richiedi app client approvata**.
    4. In **Per più controlli** selezionare **Richiedi tutti i controlli selezionati**. Questa impostazione garantisce che entrambi i requisiti selezionati vengano applicati quando un dispositivo tenta di accedere alla posta elettronica.
    5. Scegliere **Seleziona**.
     
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8.  In **Abilita criterio** selezionare **Sì**.
     
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9.  Selezionare **Crea**.

## <a name="try-it-out"></a>Procedura
Con i criteri creati, qualsiasi dispositivo iOS che tenta di accedere alla posta elettronica di Office 365 dovrà essere registrato in Intune e usare l'app per dispositivi mobili Outlook per iOS. Per testare questo scenario in un dispositivo iOS, provare ad accedere a Exchange Online usando le credenziali di un utente nel tenant di test. Verrà richiesto di registrare il dispositivo e installare l'app per dispositivi mobili Outlook.
1. Per testare in un iPhone, passare a **Impostazioni** > **Password e account** > **Aggiungi account** > **Exchange**.
2. Immettere l'indirizzo di posta elettronica per un utente nel tenant e quindi premere **Avanti**.
3. Premere **Accedi**.
4. Immettere la password dell'utente di test e premere **Accedi**.
5. Viene visualizzato un messaggio che indica che il dispositivo deve essere gestito per accedere alla risorsa, insieme a un'opzione per effettuare la registrazione. 

## <a name="clean-up-resources"></a>Pulizia delle risorse
Quando i criteri di test non sono più necessari, è possibile rimuoverli.
1. Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.
2. Selezionare **Conformità del dispositivo** > **Criteri**.
3. Nell'elenco **Nome criteri** selezionare il menu di scelta rapida (**...**) per i criteri di test e quindi selezionare **Elimina**. Selezionare **OK** per confermare.
4. Selezionare **Accesso condizionale** > **Criteri**.
5. Nell'elenco **Nome criteri** selezionare il menu di scelta rapida (**...**) per i criteri di test e quindi selezionare **Elimina**. Selezionare **Sì** per confermare.

 ## <a name="next-steps"></a>Passaggi successivi 
In questa esercitazione sono stati creati criteri che richiedono ai dispositivi iOS la registrazione in Intune e l'uso dell'app Outlook per accedere alla posta elettronica di Exchange Online. Per altre informazioni sull'uso di Intune con l'accesso condizionale per proteggere altri servizi e app, inclusi i client di Exchange ActiveSync per Office 365 Exchange Online, vedere [Configurare l'accesso condizionale](conditional-access.md).