---
title: Eseguire la migrazione dei criteri di accesso condizionale dal portale di Intune classico al nuovo portale di Azure.
titleSuffix: Intune on Azure
description: Eseguire la migrazione dei criteri di accesso condizionale dal portale di Intune classico al nuovo portale di Azure.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2450a878424d8c992a43e8028ba59b7136e1d530
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-new-azure-portal"></a>Riassegnare i criteri di accesso condizionale dal portale di Intune classico al nuovo portale di Azure.

Con il nuovo portale di Azure, l'accesso condizionale offre supporto per più criteri di applicazione insieme ad altre possibilità di personalizzazione.

## <a name="before-you-begin"></a>Prima di iniziare

Quando si è pronti per passare al nuovo portale di Azure, è sufficiente seguire la procedura seguente per riassegnare i criteri di accesso condizionale creati in precedenza nel portale di Intune classico:

- Raccogliere i criteri di accesso condizionale creati in precedenza nel portale di Intune classico per conoscere le impostazioni da riassegnare in un secondo momento.

- Seguire i passaggi illustrati in questo argomento per ricreare tali criteri nel nuovo portale di Azure.

- Disabilitare i criteri condizionali nella console classica di Intune dopo avere verificato che i nuovi criteri funzionino come previsto nel nuovo portale di Azure.
<br /><br />
    - **Prima di disabilitare** i criteri di accesso condizionale nel portale di Intune classico, pianificare come spostare gli utenti nei criteri nuovi. È possibile seguire due approcci:
<br /><br />
        - **Usare lo stesso gruppo di inclusione per applicare i criteri creati nel nuovo portale di Azure e creare un nuovo gruppo di esenzione da usare con i criteri applicati dal portale di Intune classico**.
            - Spostare progressivamente alcuni utenti nel gruppo di esenzione specificato nel portale classico.  Ciò impedisce che vengano applicati i criteri assegnati dal portale di Intune classico. Oltre ai criteri del portale di Intune classico, vengono anche applicati i criteri creati e assegnati allo stesso gruppo di utenti nel nuovo portale di Azure. 
<br /><br />
        - **Creare un nuovo gruppo a cui assegnare i criteri di accesso condizionale nel nuovo portale di Azure**. Se si sceglie questo approccio, è necessario eseguire le operazioni seguenti:
            - Rimuovere gradualmente gli utenti dai gruppi di sicurezza che hanno criteri di accesso condizionale assegnati nel portale di Intune classico.
            - Dopo aver verificato che i nuovi criteri funzionano per tali utenti, è possibile disabilitare i criteri nel portale di Intune classico. 
<br /><br />
- Se le impostazioni dei criteri di accesso condizionale erano state configurate per usare Exchange Active Sync (EAS) nel portale di Intune classico, vedere le [istruzioni in questo argomento](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients) per **riassegnare le impostazioni dei criteri di accesso condizionale EAS nel nuovo portale di Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Per verificare i criteri di accesso condizionale basati sui dispositivi nel portale di Intune classico

1.  Passare al [portale di Intune classico](https://manage.microsoft.com) e accedere con le proprie credenziali.

2.  Scegliere **Criteri** dal menu a sinistra.

3.  Scegliere **Accesso condizionale**, quindi selezionare il servizio cloud Microsoft (Exchange Online, SharePoint Online, e così via) per cui sono stati creati i criteri di accesso condizionale.

4.  Annotare le impostazioni di accesso condizionale e usare queste note come riferimento per creare gli stessi criteri di accesso condizionale nel nuovo portale di Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Interazione dei criteri di accesso condizionale basati sui dispositivi e sull'app

Il pannello **Protezione app di Intune**  nel nuovo portale di Azure consente agli amministratori di impostare regole condizionali basati su app in modo che solo le applicazioni che supportano i criteri di protezione di app di Intune possano accedere alle risorse aziendali. È possibile scegliere di sovrapporre questi criteri di accesso condizionale basati su app usando i criteri di accesso condizionale basati su dispositivi. A seconda se si vuole combinare i criteri condizionali basati su dispositivi e app (AND logico) oppure specificare un'opzione (OR logico). Se i requisiti dei criteri di accesso condizionale sono di:

- Richiedere un dispositivo conforme **E** usare l'app approvata.
    - È necessario impostare i criteri di accesso condizionale tramite il [pannello Accesso condizionale di Azure AD](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) e il [pannello Protezione app di Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Richiedere un dispositivo conforme **O** usare l'app approvata.
    - È necessario impostare i criteri di accesso condizionale tramite il [portale di Intune classico](https://manage.microsoft.com) e il [pannello Protezione app di Intune](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Questo argomento include schermate che confrontano l'esperienza utente con il portale di Intune classico e con il nuovo portale di Azure.

## <a name="to-re-assign-intune-device-based-conditional-access-policies"></a>Per riassegnare i criteri di accesso condizionale basati sui dispositivi

1. Passare a [Conditional access in the new Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) (Accesso condizionale nel nuovo portale di Azure) e accedere con le proprie credenziali.

2. Scegliere **Nuovo criterio**.

3. Specificare un nome per il criterio.

4. Scegliere **Utenti e gruppi** nella sezione **Assegnazioni** per assegnare i nuovi criteri di accesso condizionale.
    
    ![Confronto dell'interfaccia utente del gruppo utenti tra il portale di Intune classico e il portale nuovo di Azure](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Se sono selezionati tutti gli utenti nel portale di Intune classico, includere Tutti gli utenti. Lo stesso vale per i gruppi. Se sono selezionati gruppi, è necessario **selezionare i singoli utenti e i gruppi** per includerli. Inoltre, se è stata scelta l'opzione **Gruppi esenti** nel portale di Intune classico, è necessario escludere tali gruppi selezionati nel nuovo portale di Azure.

5. Dopo aver scelto il gruppo, fare clic su **Seleziona**, quindi su **Done** (Fine).

6. Scegliere **App cloud** nella sezione **Assegnazioni**.

7. Nel pannello **App cloud**, scegliere **Seleziona app**.

8. Scegliere l'app a cui si vuole applicare i nuovi criteri di accesso condizionale e fare clic su **Seleziona**.

9. Fare clic su **Fine**.

    ![Confronto dell'interfaccia utente dell'app cloud tra il portale di Intune classico e il portale nuovo di Azure](./media/reassign-ca-3.png)

    > [!TIP] 
    > Se si hanno più app con gli stessi criteri, è possibile consolidarli in un singolo set di criteri nel nuovo portale di Azure.

10. Scegliere **Condizioni** nella sezione **Assegnazioni**.

11. Nel pannello **Condizioni**, scegliere **Piattaforme dei dispositivi**, quindi selezionare le piattaforme dei dispositivi da applicare.

12. Dopo aver scelto le piattaforme dei dispositivi, fare clic su **Fine** due volte.

    ![Confronto dell'interfaccia utente della piattaforma dei dispositivi tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Se sono state scelte singole piattaforme nel portale di Intune classico, scegliere le singole piattaforme nel nuovo portale di Azure.

    > [!NOTE] 
    > È possibile specificare le opzioni di aggiunta al dominio o di conformità per Windows in un secondo momento.

13. Scegliere **Condizioni** nella sezione **Assegnazioni**.

14. Nel pannello **Condizioni**, scegliere **App client**, quindi scegliere l'app client a cui applicarle.

15. Dopo aver scelto l'app client, fare clic su **Done** (Fine) due volte.

    ![Confronto dell'interfaccia utente dell'app client tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-6.png)

16. Se sono state scelte le impostazioni del browser nel portale di Intune classico, selezionare **Browser** e **App per dispositivi mobili e client desktop** nel nuovo portale di Azure. Nel caso in cui non siano state scelte le impostazioni del browser nel portale di Intune classico, scegliere solo **App per dispositivi mobili e client desktop**. 

17. Scegliere **Concedi** nella sezione **Controlli di accesso**.

18. Scegliere **Richiedi che i dispositivi siano contrassegnati come conformi** in **Concedi controlli di accesso**, quindi fare clic su **Seleziona**.

19. Se si hanno criteri che richiedono che i dispositivi Windows siano aggiunti a un dominio e vengano anche consentiti i dispositivi Windows conformi e registrati con Intune, scegliere **Richiedi dispositivo aggiunto a un dominio** e **Richiedi che i dispositivi siano contrassegnati come conformi** insieme a **Richiedi uno dei controlli selezionati**.

20. Se non vengono consentiti i dispositivi Windows conformi e registrati con Intune, escludere i criteri Windows dai criteri correnti e quindi creare criteri separati con **Piattaforma dei dispositivi** impostata su **Windows**, includere le altre condizioni come specificato precedentemente e scegliere **Richiedi dispositivo aggiunto a un dominio** della sezione **Concedi controlli di accesso**.

21. Attivare l'opzione **Abilita criteri** nel pannello **Nuovo** dei criteri di accesso condizionale, quindi fare clic su **Crea**.

    ![Confronto dell'interfaccia utente dei criteri di accesso condizionale abilitati tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-11.png)

## <a name="to-reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Per riassegnare i criteri di accesso condizionale basati su dispositivo di Intune per i client EAS

Se sono state configurate le impostazioni di Exchange Active Sync (EAS) come parte dei criteri di Exchange Online nel portale di Intune classico, è necessario creare un secondo set di criteri di accesso condizionale nel nuovo portale di Azure.

1. Passare a [Conditional access in the new Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) (Accesso condizionale nel nuovo portale di Azure) e accedere con le proprie credenziali.

2. Scegliere **Nuovo criterio**.

3. Specificare un nome per il criterio.

4. Scegliere **Utenti e gruppi** nella sezione **Assegnazioni** per assegnare i nuovi criteri di accesso condizionale.

    ![Confronto dell'interfaccia utente del gruppo utenti tra il portale di Intune classico e il portale nuovo di Azure](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Se sono selezionati tutti gli utenti nel portale di Intune classico, includere Tutti gli utenti. Lo stesso vale per i gruppi. Se sono selezionati gruppi, è necessario **selezionare i singoli utenti e i gruppi** per includerli. Inoltre, se è stata scelta l'opzione **Gruppi esenti** nel portale di Intune classico, è necessario escludere tali gruppi selezionati nel nuovo portale di Azure.

5. Dopo aver scelto il gruppo, fare clic su **Seleziona**, quindi su **Done** (Fine).

6. Scegliere **App cloud** nella sezione **Assegnazioni**.

7. Nel pannello **App cloud**, fare clic su **App selezionate**, scegliere **Exchange Online**, fare clic su **Seleziona**, quindi fare clic su **Done** (Fine).

    ![Confronto dell'interfaccia utente delle app client tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > I criteri di accesso condizionale per i client EAS non possono includere altre app cloud.

8. Nel pannello **Condizioni**, scegliere **App client**, quindi scegliere l'app client a cui applicarle. Se si è scelto di bloccare i client che non sono supportati da Intune, usare l'opzione **Applica i criteri solo alle piattaforme supportate**.

    ![Confronto dell'interfaccia utente dell'app client tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-15.png)

9. Dopo aver scelto l'app client, fare clic su **Done** (Fine) due volte.

10. Scegliere **Concedi** nella sezione **Controlli di accesso**.

11. Scegliere **Richiedi che i dispositivi siano contrassegnati come conformi** in **Concedi controlli di accesso**, quindi fare clic su **Seleziona**.

    ![Confronto dell'interfaccia utente di Concedi accesso tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-16.png)

12. Attivare l'opzione **Abilita criteri** nel pannello **Nuovo** dei criteri di accesso condizionale, quindi fare clic su **Crea**.

    ![Confronto dell'interfaccia utente dei criteri di accesso condizionale abilitati tra il portale di Intune classico e il nuovo portale di Azure](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Disabilitare i criteri di accesso condizionale nel portale di Intune classico
### <a name="before-you-start"></a>Prima di iniziare

Quando si riassegnano i criteri di accesso condizionale nel nuovo portale di Azure, è importante disabilitare gradualmente i criteri di accesso condizionale creati in precedenza nel portale di Intune classico. Inoltre, potrebbe essere necessario usare lo stesso gruppo di sicurezza per applicare i criteri di accesso condizionale creati nel nuovo portale di Azure

- Vedere la sezione [Prima di iniziare](#before-you-begin) all'inizio di questo argomento prima di disabilitare i criteri di accesso condizionale nel portale di Intune classico.

### <a name="to-disable-the-conditional-access-policies"></a>Per disabilitare i criteri di accesso condizionale

1.  Passare al [portale di Intune classico](https://manage.microsoft.com) e accedere con le proprie credenziali.

2.  Scegliere **Criteri** dal menu a sinistra.

3.  Scegliere **Accesso condizionale**, quindi selezionare il servizio cloud Microsoft (Exchange Online, SharePoint Online, e così via) per cui sono stati creati i criteri di accesso condizionale.

4.  Deselezionare l'opzione **Abilita criteri di accesso condizionale**, quindi fare clic su **Salva**.

    ![Disabilitare i criteri di accesso condizionale nel portale di Intune classico](./media/reassign-ca-18.png)

## <a name="see-also"></a>Vedere anche

- [Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md)
- [Accesso condizionale basato su app con Intune](app-based-conditional-access-intune.md)
- [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)