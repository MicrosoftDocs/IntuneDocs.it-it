---
title: Risolvere i problemi di installazione delle app
titleSuffix: Microsoft Intune
description: Usare il riquadro Risoluzione dei problemi di Microsoft Intune per facilitare la risoluzione dei problemi di installazione delle app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3aadad0b185f72d9137ed0f2d807df6d035a9ba7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735337"
---
# <a name="troubleshoot-app-installation-issues"></a>Risolvere i problemi di installazione delle app

Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. Microsoft Intune offre dettagli sugli errori di installazione delle app che consentono agli operatori di help desk e agli amministratori di Intune di visualizzare informazioni sulle app in per rispondere alle richieste degli utenti. Il riquadro di risoluzione dei problemi all'interno di Intune fornisce dettagli sull'errore, incluse informazioni dettagliate sulle app gestite nel dispositivo dell'utente. Per ogni singolo dispositivo sono disponibili informazioni dettagliate sul ciclo di vita completo di un'app nel riquadro **App gestite**. È possibile visualizzare i problemi di installazione, ad esempio quando l'app è stato creata, modificata, assegnata e recapitata a un dispositivo. 

## <a name="app-troubleshooting-details"></a>Informazioni dettagliate per la risoluzione dei problemi delle app

Intune offre informazioni dettagliate per la risoluzione dei problemi delle app in base alle app installate nel dispositivo di un utente specifico.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** scegliere **Risoluzione dei problemi**.
4. Fare clic su **Seleziona utente** per selezionare un utente per risolvere i problemi. Verrà visualizzato il riquadro **Seleziona utenti**.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona** nella parte inferiore del riquadro. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel riquadro **Risoluzione dei problemi**. 
6. Selezionare il dispositivo per cui si vuole eseguire la risoluzione dei problemi nell'elenco **Dispositivi**.
    ![Riquadro Risoluzione dei problemi di Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Selezionare **App gestite** nel riquadro del dispositivo selezionato. Verrà visualizzato un elenco delle app gestite.
    ![Dettagli di un dispositivo specifico gestito da Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Selezionare un'app nell'elenco per cui **Stato dell'installazione** indica un errore.
    ![App selezionata che mostra informazioni dettagliate sull'errore di installazione.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > La stessa app potrebbe essere assegnata a più gruppi, ma con diverse azioni previste (finalità) per l'app. Ad esempio, la finalità risolta per un'app indicherà **esclusa** se l'app viene esclusa per un utente durante l'assegnazione di app. Per altre informazioni, vedere [Modalità di risoluzione dei conflitti tra finalità di app](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Se si verifica un errore di installazione per un'app obbligatoria, l'utente o il supporto tecnico sarà in grado di sincronizzare il dispositivo e ritentare l'installazione dell'app.

I dettagli dell'errore di installazione dell'app indicheranno il problema. È possibile usare questi dettagli per determinare l'azione migliore da intraprendere per risolvere il problema. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Errori di installazione delle app](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> È anche possibile accedere al riquadro **Risoluzione dei problemi** digitando nel browser l'indirizzo seguente: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>L'installazione dell'app di destinazione del gruppo di utenti non raggiunge il dispositivo
Quando si verificano problemi durante l'installazione delle app, è necessario prendere in considerazione le azioni seguenti:
- Se l'app non viene visualizzata nel Portale aziendale, assicurarsi che l'app venga distribuita con finalità **disponibili** e che l'utente acceda al portale aziendale con il tipo di dispositivo supportato dall'app.
- Per i dispositivi Windows BYOD, l'utente deve aggiungere un account aziendale al dispositivo.
- Controllare se l'utente ha superato il limite di dispositivi AAD:
  1. Passare a [Azure Active Directory impostazioni dispositivo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/DevicesMenuBlade/DeviceSettings/menuId).
  2. Prendere nota del valore impostato per il **numero massimo di dispositivi per utente**.
  3. Passare a [Azure Active Directory utenti](https://portal.azure.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade/AllUsers).
  4. Selezionare l'utente interessato e fare clic su **dispositivi**.
  5. Se l'utente supera il limite impostato, eliminare tutti i record obsoleti che non sono più necessari.
- Per i dispositivi DEP iOS, assicurarsi che l'utente sia elencato come **registrato dall'utente** nel pannello di panoramica del dispositivo Intune. Se viene visualizzato NA, distribuire un criterio di configurazione per il Portale aziendale Intune. Per altre informazioni, vedere [configurare l'app portale aziendale](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Risoluzione dei problemi di installazione delle app Win32

Selezionare l'app Win32 distribuita usando l'estensione di gestione di Intune. È possibile selezionare l'opzione **Raccogli i log** se l'installazione dell'app Win32 ha esito negativo. 

> [!IMPORTANT]
> L'opzione **Raccogli i log** non viene infatti attivata se l'app Win32 è stata installata nel dispositivo.<p>Per poter raccogliere i log dell'app Win32, è necessario che l'estensione di gestione di Intune sia stata installata nel client Windows. L'estensione di gestione di Intune viene installata quando uno script di PowerShell o un'app Win32 viene distribuita in un gruppo di sicurezza dispositivi o utente. Per altre informazioni, vedere i [Prerequisiti dell'estensione di gestione di Intune](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Raccogliere i file di log

Per raccogliere i log di installazione dell'app Win32, prima di tutto seguire le istruzioni riportate nella sezione [Informazioni dettagliate per la risoluzione dei problemi delle app](troubleshoot-app-install.md#app-troubleshooting-details). Quindi, continuare con la seguente procedura:

1. Fare clic sull'opzione **Raccogli i log** nel pannello **Dettagli installazione**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Specificare i percorsi dei file e i nomi di file dei log per iniziare il processo di raccolta, quindi fare clic su **OK**.

    > [!NOTE]
    > La raccolta dei log richiederà meno di due ore. Sono supportati i tipi di file con estensione *log, txt, dmp, cab, zip, xml, evtx ed evtl*. Sono consentiti fino a 25 percorsi di file.

3. Dopo aver raccolto i file di log, selezionare il collegamento **log** per scaricarli.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Verrà visualizzata una notifica per indicare l'esito positivo della raccolta dei log dell'app.

#### <a name="win32-log-collection-requirements"></a>Requisiti per la raccolta di log di Win32

Esistono regole specifiche da seguire per raccogliere i file di log:

- È necessario specificare il percorso completo dei file di log. 
- È possibile specificare variabili di ambiente per la raccolta dei log, ad esempio:<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Sono ammesse solo estensioni di file esatte, ad esempio:<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Il limite per il caricamento è 60 MB o 25 file, a seconda di quale condizione si verifica per prima. 
- La raccolta dei log di installazione dell'app Win32 è abilitata per le app che rispettano la finalità di assegnazione obbligatoria, disponibile e disinstallazione dell'app.
- I log archiviati sono crittografati per proteggere le informazioni personali contenute nei log.
- Quando si aprono dei ticket di supporto per gli errori che si verificano nelle app Win32, allegare i relativi log di errore usando la procedura riportata sopra.

## <a name="app-installation-errors"></a>Errori di installazione delle app

I seguenti messaggi di errore e descrizioni contengono dettagli sugli errori di installazione di Android e iOS. 

### <a name="android-errors"></a>Errori di Android

Questa sezione menziona sia l'amministratore del dispositivo che la registrazione di Samsung Knox. Per altre informazioni, vedere registrazione [amministratore dispositivi Android](../enrollment/android-enroll-device-administrator.md) e [registrare automaticamente i dispositivi Android usando la registrazione di Samsung Knox per dispositivi mobili](../enrollment/android-samsung-knox-mobile-enroll.md). 

| Messaggio di errore/codice | Descrizione |
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Non è stato possibile installare l'app. (0xC7D14FB5) | Questo messaggio di errore viene visualizzato quando Intune non determina la causa radice dell'errore di installazione dell'app Android. Non si ricevono informazioni da Android quando si verifica l'errore. Questo errore viene restituito quando il download del pacchetto dell'applicazione Android (APK) viene completato, ma l'installazione dell'app non riesce. Questo errore spesso può verificarsi a causa di un file APK non valido che non può essere installato nel dispositivo. Una causa possibile può essere il fatto che Google Play Protect blocca l'installazione dell'app come misura di sicurezza. L'errore si può verificare anche quando un dispositivo non supporta l'app, ad esempio se l'app richiede l'API versione 21 o successive e il dispositivo attualmente usa la versione 19 dell'API. Intune restituisce questo errore per i dispositivi DA e KNOX e benché gli utenti possano ricevere una notifica in cui si chiede di fare clic per riprovare, se si verifica un problema con il file APK, l'errore non continuerà a ripetersi. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. |
| L'installazione dell'app è stata annullata perché il file di installazione (APK) è stato eliminato dopo il download, ma prima dell'installazione. (0xC7D14FBA) | Il download del file APK è stato completato, ma il file è stato rimosso dal dispositivo prima che l'utente installasse l'app. Questo problema può verificarsi se trascorre molto tempo tra il download e l'installazione. Ad esempio l'utente ha annullato l'installazione originale, ha atteso e quindi ha fatto clic sulla notifica per riprovare. Questo messaggio di errore viene restituito solo per gli scenari DA. Gli scenari KNOX possono essere eseguiti automaticamente. Viene presentata una notifica che indica di riprovare in modo che l'utente possa accettare anziché annullare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. |
| L'installazione dell'app è stata annullata perché il processo è stato riavviato durante l'installazione. (0xC7D14FBB) | Il dispositivo è stato riavviato durante il processo di installazione del pacchetto dell'applicazione Android, quindi l'installazione è stata annullata. Questo messaggio di errore viene restituito per i dispositivi DA e KNOX. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. |
| Applicazione non rilevata dopo il completamento dell'installazione. (0x87D1041C) | L'utente ha disinstallato l'app in modo esplicito. Questo errore non viene restituito dal client. Si tratta di un errore generato quando l'app è già installata ma viene successivamente disinstallata dall'utente. Questo errore dovrebbe verificarsi solo per le applicazioni obbligatorie. Gli utenti possono disinstallare le app non obbligatorie. Questo errore si può verificare solo in DA. KNOX blocca la disinstallazione delle app gestite. Con la sincronizzazione successiva la notifica verrà ripubblicata nel dispositivo per indicare all'utente di eseguire l'installazione. L'utente può ignorare la notifica. Questo errore continuerà a essere segnalato finché l'utente non installa l'app. |
| Non è stato possibile eseguire il download a causa di un errore sconosciuto. (0xC7D14FB2) | Questo errore si verifica quando il download ha esito negativo. In genere, questo errore può verificarsi a causa di problemi di Wi-Fi o connessioni lente. Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. |
| Non è stato possibile eseguire il download a causa di un errore sconosciuto. Il criterio verrà ritentato alla successiva sincronizzazione del dispositivo. (0xC7D15078) | Questo errore si verifica quando il download ha esito negativo. In genere, questo errore può verificarsi a causa di problemi di Wi-Fi o connessioni lente. Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. |
| L'utente finale ha annullato l'installazione dell'app. (0xC7D14FB1) | L'utente ha disinstallato l'app in modo esplicito. Questo errore viene restituito quando l'attività di installazione del sistema operativo Android viene annullata dall'utente. L'utente ha premuto il pulsante Annulla quando era visualizzata la richiesta di installazione del sistema operativo oppure ha fatto clic in un altro punto. Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. Richiedere all'utente di non annullare l'installazione. |
| Il processo di download di file è stato arrestato in modo imprevisto. (0xC7D15015) | Il sistema operativo ha arrestato il processo di download prima del completamento. Questo errore può verificarsi quando il dispositivo ha la batteria in esaurimento o il download richiede troppo tempo. Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Intune visualizza una notifica per invitare gli utenti a fare clic per riprovare. Se l'app è un'app disponibile, la notifica può essere ignorata. Se invece l'app è obbligatoria, non può essere ignorata. Verificare che il dispositivo disponga di una connessione di rete affidabile.  |
| Il servizio di download di file è stato arrestato in modo imprevisto. Il criterio verrà ritentato alla successiva sincronizzazione del dispositivo. (0xC7D1507C) | Il sistema operativo ha terminato il processo di download prima del completamento. Questo errore può verificarsi quando il dispositivo ha la batteria in esaurimento o il download richiede troppo tempo. Questo errore viene restituito solo per gli scenari DA. Per gli scenari KNOX, all'utente non viene richiesto di eseguire l'installazione, che può essere eseguita automaticamente. Sincronizzare manualmente il dispositivo o attendere 24 ore e verificare lo stato. |
| Non è stato possibile disinstallare l'app. (0xc7d14fb8) | Si tratta di un errore di disinstallazione generico. Il sistema operativo non ha specificato perché la disinstallazione dell'app non è riuscita. Alcune app di amministrazione non possono semplicemente essere disinstallate. Verificare che l'app possa essere disinstallata manualmente e raccogliere i log Portale aziendale se la disinstallazione non riesce. |
| Il file APK di installazione app usato per l'aggiornamento non corrisponde alla firma per l'app corrente nel dispositivo. (0xc7d14fb7) | Il sistema operativo Android ha la limitazione di richiedere che il certificato di firma per la versione di aggiornamento sia esattamente lo stesso del certificato usato per firmare la versione esistente. Se lo sviluppatore non può usare lo stesso certificato per firmare la nuova versione, sarà necessario disinstallare l'app esistente e ridistribuire la nuova app anziché aggiornare l'app esistente. |
| L'utente finale ha annullato l'installazione dell'app. (0xc7d14fb9) | Informare l'utente di accettare l'app distribuita con Intune e installare l'app quando richiesto. |
| La disinstallazione dell'app è stata annullata perché il processo è stato riavviato durante l'installazione. (0xc7d14fbc) | Il processo di installazione dell'app è stato terminato dal sistema operativo o il dispositivo è stato riavviato. Se l'errore si verifica di nuovo, riprovare l'installazione e raccogliere i registri Portale aziendale. |
| Non è possibile installare il file APK di installazione dell'app perché non è firmato. (0xc7d14fb6) | Per impostazione predefinita, il sistema operativo Android richiede che le app siano firmate. Verificare che l'app sia firmata prima della distribuzione. |

### <a name="ios-errors"></a>Errori iOS

| Messaggio di errore/codice | Descrizione/Suggerimenti per la risoluzione dei problemi |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | L'agente MDM di Apple ha segnalato che il comando di installazione ha avuto esito negativo. |
| (0x87D1313C) | Si è persa la connessione di rete mentre l'URL aggiornato del servizio di download veniva inviato al dispositivo. In particolare, non è stato possibile trovare un server con il nome host specificato. |
| Il dispositivo iOS è attualmente occupato. (0x87D11388) | Il dispositivo iOS era occupato e ciò ha generato un errore. Il dispositivo è stato bloccato. L'utente deve sbloccare il dispositivo per installare l'app. |
| Installazione app non riuscita. (0x87D13B64) | Si è verificato un errore di installazione dell'app. Sono necessari i log della Console iOS per risolvere questo errore. |
| L'app è gestita, ma è scaduta o è stata rimossa dall'utente. (0x87D13B66) | L'utente ha disinstallato in modo esplicito l'app o l'app è scaduta ma non è stata scaricata o il rilevamento dell'app non corrisponde alla risposta del dispositivo. Inoltre, questo errore può verificarsi per un bug della piattaforma iOS 9.2.2. |
| L'app viene pianificata per l'installazione, ma è necessario un codice di riscatto per completare la transazione. (0x87D13B60) | Questo errore si verifica in genere con le app di iOS Store a pagamento. |
| Applicazione non rilevata dopo il completamento dell'installazione. (0x87D1041C) | Il processo di rilevamento dell'app non corrisponde alla risposta del dispositivo. |
| L'utente ha rifiutato l'offerta di installazione dell'app. (0x87D13B62) | Durante l'installazione iniziale dell'app, l'utente ha fatto clic su Annulla. Chiedere all'utente di accettare la richiesta di installazione la volta successiva. |
| L'utente ha rifiutato l'offerta di aggiornamento dell'app. (0x87D13B63) | L'utente finale ha fatto clic su Annulla durante il processo di aggiornamento. Distribuire come richiesto o informare l'utente di accettare la richiesta di aggiornamento. |
| Errore sconosciuto (0x87D103E8) | Si è verificato un errore sconosciuto durante l'installazione dell'app. Si tratta dell'errore che si verifica quando non si sono verificati altri errori. |
| È possibile installare le app VPP solo in modalità iPad condiviso (-2016330861). | È necessario ottenere le app tramite Volume Purchase Program di Apple per installare in un iPad condiviso. |
| Non è possibile installare le app quando l'App Store è disabilitato (-2016330860). | Affinché l'app possa essere installata, l'App Store deve essere abilitato. |
| Licenza VPP per l'app non trovata (-2016330859). | Provare a revocare la licenza dell'app e a riassegnarla. |
| Impossibile installare le app di sistema con il provider MDM (-2016330858). | L'installazione di app che vengono pre-installate dal sistema operativo iOS non è supportata. |
| Impossibile installare le app quando il dispositivo è in modalità di dispositivo perso (-2016330857). | In modalità di dispositivo perso, si blocca qualsiasi uso del dispositivo. Disabilitare la modalità di dispositivo perso per installare le app. |
| Impossibile installare le app quando il dispositivo è in modalità tutto schermo (-2016330856). | Provare ad aggiungere questo dispositivo a un gruppo di esclusione dei criteri di configurazione per la modalità tutto schermo per installare le app. |
| Impossibile installare app a 32 bit su questo dispositivo (-2016330852). | Il dispositivo non supporta l'installazione di app a 32 bit. Provare a distribuire la versione a 64 bit dell'app. |
| L'utente deve eseguire l'accesso all'App Store (-2016330855). | L'utente deve eseguire l'accesso all'App Store prima di poter installare l'app. |
| Processo sconosciuto. Riprovare (-2016330854). | L'installazione dell'app non è riuscita a causa di un motivo sconosciuto. Riprovare. |
| L'installazione dell'app non è riuscita. Intune proverà nuovamente alla successiva sincronizzazione del dispositivo (-2016330853). | L'installazione dell'app ha rilevato un errore di dispositivo. Sincronizzare il dispositivo per provare a installare nuovamente l'app. |
| L'assegnazione della licenza non è riuscita con errore Apple ' No VPP licenses rimanenti ' (0x87d13b7e) | Questo comportamento è da progettazione. Per risolvere questo problema, acquistare licenze VPP aggiuntive o recuperare licenze dagli utenti non più interessate. |
| Errore di installazione dell'app 12024: motivo sconosciuto. (0x87d13b6e) | Apple non ha fornito informazioni sufficienti per determinare il motivo per cui l'installazione non è riuscita. Nessun elemento da segnalare. |
| I criteri di configurazione delle app necessari non sono presenti, assicurarsi che i criteri siano assegnati agli stessi gruppi. (0x87d13b7f) | L'app richiede la configurazione dell'app, ma non è destinata alla configurazione dell'app. L'amministratore deve assicurarsi che i gruppi a cui è destinata l'app dispongano anche della configurazione dell'app necessaria indirizzata ai gruppi. |
| Le licenze VPP del dispositivo sono applicabili solo ai dispositivi iOS 9.0 +. (0x87d13b69) | Aggiornare i dispositivi iOS interessati a iOS 9.0 +. |
| L'applicazione è installata nel dispositivo, ma non è gestita. (0x87d13b8f) | Questo errore si verifica solo nelle app LOB. L'app è stata installata all'esterno di Intune. Per risolvere questo errore, disinstallare l'app dal dispositivo. Al successivo avvio della sincronizzazione del dispositivo, il dispositivo deve installare l'app da Intune. |
| Gestione app rifiutata dall'utente (0x87d13b68) | Richiedere all'utente di accettare la gestione delle app. |
| Errore sconosciuto. (0x87d1279d) | Questo errore si verifica nelle app dello store iOS, ma lo scenario di errore è sconosciuto. |
| Non è stato possibile aggiornare la versione più recente dell'app da una versione precedente. (0x87D13B9D) | Questo messaggio di errore viene visualizzato se l'app è installata e gestita ma con la versione non corretta del dispositivo. Questa situazione include quando un dispositivo ha ricevuto un comando per aggiornare un'app, ma la nuova versione non è ancora stata installata e restituita. Questo errore viene segnalato per la prima archiviazione di un dispositivo dopo la distribuzione dell'aggiornamento e si verificherà fino a quando il dispositivo non segnala che la nuova versione è installata o non riesce a causa di un errore diverso.  |


### <a name="other-installation-errors"></a>Altri errori di installazione

|  Messaggio di errore/codice  |  Descrizione  |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  0x80073CFF, 0x80CF201C (errore del client)  |  Per installare questa app, è necessario disporre di un sistema abilitato per il sideload. Verificare che il pacchetto dell'app sia firmato con una firma attendibile e installato in un dispositivo aggiunto al dominio per il quale sono abilitati i criteri **AllowAllTrustedApps** oppure in un dispositivo che dispone di una licenza per la funzionalità di sideload di Windows e per il quale sono abilitati i criteri **AllowAllTrustedApps**. Per altre informazioni, vedere [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Risoluzione dei problemi di creazione di pacchetti, distribuzione e query delle app di Windows Store).   |
|  0x80073CF0  |  Non è stato possibile aprire il pacchetto. Cause possibili:<ul><li> Il pacchetto non è firmato.</li><li> Il nome dell'autore non corrisponde al soggetto del certificato di firma.</li></ul> Per informazioni, controllare il registro eventi **AppxPackagingOM**. Per altre informazioni, vedere [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Risoluzione dei problemi di creazione di pacchetti, distribuzione e query delle app di Windows Store).  |
|  0x80073CF3  |  Non è stato possibile completare la convalida dell'aggiornamento, delle dipendenze o dei conflitti per il pacchetto. Cause possibili:<ul><li> Il pacchetto in arrivo è in conflitto con un pacchetto installato.</li><li> Non è possibile trovare una dipendenza pacchetto specificata.</li><li> Il pacchetto non supporta l'architettura del processore corretta.</li></ul> Per informazioni, controllare il registro eventi **AppXDeployment-Server**. Per altre informazioni, vedere [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Risoluzione dei problemi di creazione di pacchetti, distribuzione e query delle app di Windows Store).  |
|  0x80073CFB  |  Il pacchetto fornito è già installato, pertanto la reinstallazione del pacchetto è stata bloccata. Questo errore può verificarsi se si installa un pacchetto che non è identico al pacchetto già installato. Verificare che anche la firma digitale faccia parte del pacchetto. Quando un pacchetto viene ricompilato o firmato di nuovo, nel confronto bit per bit tale pacchetto non è più identico a quello installato in precedenza. Per questo problema sono disponibili due soluzioni:<ul><li> Incrementare il numero di versione dell'app, quindi ricompilare e firmare nuovamente il pacchetto.</li><li> Rimuovere il pacchetto precedente per ogni utente del sistema prima di installare quello nuovo.</li></ul> Per altre informazioni, vedere [Troubleshooting packaging, deployment, and query of Windows Store apps](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting) (Risoluzione dei problemi di creazione di pacchetti, distribuzione e query delle app di Windows Store).  |
|  0x87D1041C  |  L'installazione dell'applicazione è stata completata ma non viene rilevata l'applicazione. L'app è stata distribuita da Intune e successivamente disinstallata. I motivi per cui l'app è stata disinstallata includono:<ul><li> L'utente finale ha disinstallato l'app.</li><li> Le informazioni sull'identità nel pacchetto non corrispondono a quelle segnalate dal dispositivo per le app non valide.</li><li>Per le app MSI con aggiornamento automatico, la versione del prodotto non corrisponde alle informazioni dell'app dopo l'aggiornamento al di fuori di Intune.</li></ul> Chiedere all'utente di reinstallare l'app dal portale aziendale. Si noti che le app necessarie verranno reinstallate automaticamente al successivo accesso del dispositivo.  |
|  0x8000FFFF  |  Errore imprevisto durante l'installazione. Per ulteriori informazioni, controllare i registri di installazione.  |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Risoluzione dei problemi delle app da Microsoft Store

Le informazioni nell'argomento [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Risoluzione dei problemi relativi a pacchetti, distribuzioni e query delle app di Microsoft Store) consentono di risolvere i problemi comuni riscontrabili durante l'installazione di app da Microsoft Store, tramite Intune o altri mezzi.

## <a name="app-troubleshooting-resources"></a>Risorse per la risoluzione dei problemi delle app
- [Distribuzione di Visio e Project nell'ambito della distribuzione di Office Pro Plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Eseguire un'azione per assicurarsi che le app MSfB distribuite tramite Intune siano installate in Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Risoluzione dei problemi relativi alle distribuzioni di app MSI in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Procedure consigliate per la distribuzione del software a Intune classico agente PC Windows](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sulla risoluzione dei problemi di Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](../fundamentals/help-desk-operators.md). 
- È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per ulteriori informazioni, vedere la pagina relativa all' [esito positivo del cliente Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](../fundamentals/get-support.md).