---
title: Configurare la sottoscrizione con Lookout | Microsoft Docs
description: Questo argomento include informazioni dettagliate su come configurare la protezione dalle minacce per il dispositivo di Lookout.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8477a2f1-2e1d-4d42-8bcb-e1181cc900bb
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3c777d8857fd177e5a27840ab8a97c8a137aa189
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="set-up-your-lookout-mobile-threat-defense-subscription"></a>Configurare la sottoscrizione di Lookout Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per configurare Lookout Mobile Threat Defense sono necessari i passaggi seguenti:

| #        |Passaggio  |
| ------------- |:-------------|
| 1 | [Raccogliere le informazioni di Azure AD](#collect-azure-ad-information) |
| 2 | [Configurare la sottoscrizione](#configure-your-subscription) |
| 3 | [Configurare i gruppi di registrazione](#configure-enrollment-groups) |
| 4 | [Configurare la sincronizzazione dello stato](#configure-state-sync) |
| 5 | [Configurare le informazioni per il destinatario dei report sugli errori tramite posta elettronica](#configure-error-report-email-recipient-information) |
| 6 | [Configurare le impostazioni di registrazione](#configure-enrollment-settings) |
| 7 | [Configurare le notifiche tramite posta elettronica](#configure-email-notifications) |
| 8 | [Configurare la classificazione delle minacce](#configure-threat-classification) |
| 1 | [Monitoraggio della registrazione](#watching-enrollment) |


> [!IMPORTANT]
> Un tenant esistente di Lookout Mobile Endpoint Security non ancora associato al tenant di Azure AD non può essere usato per l'integrazione con Azure AD e Intune. Contattare il supporto di Lookout per creare un nuovo tenant di Lookout Mobile Endpoint Security. Usare il nuovo tenant per caricare gli utenti di Azure AD.

## <a name="collect-azure-ad-information"></a>Raccogliere le informazioni di Azure AD
Il tenant di Lookout Mobility Endpoint Security verrà associato alla sottoscrizione di Azure AD per l'integrazione di Lookout con Intune. Per abilitare la sottoscrizione per il servizio Lookout Mobile Threat Defense, il supporto tecnico di Lookout (enterprisesupport@lookout.com) ha bisogno delle informazioni seguenti:  

* **ID tenant di Azure AD**
* **ID oggetto gruppo di Azure AD** per l'accesso **completo** alla console di Lookout
* **ID oggetto gruppo di Azure AD** per l'accesso **limitato** alla console di Lookout (facoltativo)

Usare la procedura seguente per raccogliere le informazioni che dovranno essere fornite al team di supporto tecnico di Lookout.

1. Accedere al [portale di gestione di Azure AD](https://manage.windowsazure.com) e selezionare la propria sottoscrizione. 
  ![screenshot della pagina di Azure AD con il nome del tenant](../media/mtp/aad_tenant_name.png)
2. Quando si sceglie il nome della sottoscrizione, l'URL risultante include l'ID sottoscrizione.  Se risulta problematico trovare l'ID sottoscrizione, questo [articolo del supporto tecnico Microsoft](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b) include suggerimenti per trovare l'ID sottoscrizione. 
3. Trovare l'ID gruppo di Azure AD. La console di Lookout supporta 2 livelli di accesso:  
  * **Accesso completo:** l'amministratore di Azure AD può creare un gruppo per gli utenti che avranno accesso completo e, facoltativamente, creare un gruppo per gli utenti che avranno accesso limitato.  Solo gli utenti di questi gruppi saranno in grado di accedere alla **console di Lookout**.
  * **Accesso limitato:** gli utenti in questo gruppo non avranno alcun accesso a diversi moduli correlati alla configurazione e alla registrazione della console di Lookout e avranno accesso in sola lettura al modulo **Security Policy** (Criteri di sicurezza) della console di Lookout.  

  Per altri dettagli sulle autorizzazioni, leggere [questo articolo](https://personal.support.lookout.com/hc/articles/114094105653) nel sito Web di Lookout.

  L'**ID oggetto gruppo** è reperibile nella pagina **Proprietà** del gruppo nella **console di gestione di Azure AD**.

  ![screenshot della pagina delle proprietà con il campo ID evidenziato](../media/mtp/aad_group_object_id.png)

4. Dopo aver raccolto le informazioni, contattare il supporto di Lookout all'indirizzo di posta elettronica enterprisesupport@lookout.com. Il servizio di supporto tecnico di Lookout collaborerà con il contatto principale dell'utente per il caricamento della sottoscrizione e per creare l'account aziendale per Lookout, usando le informazioni raccolte.

## <a name="configure-your-subscription"></a>Configurare la sottoscrizione
1. Quando il servizio di supporto tecnico di Lookout ha creato l'account aziendale per Lookout, viene inviato un messaggio di posta elettronica da Lookout al contatto principale per l'azienda con un collegamento all'URL di accesso: https://aad.lookout.com/les?action=consent.

2.  Al primo accesso alla console di Lookout è necessario usare un account utente con il ruolo di amministratore globale di Azure AD per la registrazione del tenant di Azure AD. In seguito, per l'accesso non è necessario questo livello di privilegi di Azure AD. Viene visualizzata una pagina per richiedere il consenso. Scegliere **Accept** (Accetto) per completare la registrazione.

  ![screenshot della pagina per il primo accesso alla console di Lookout](../media/mtp/lookout_mtp_initial_login.png) Dopo aver accettato e fornito il consenso, si verrà reindirizzati alla console di Lookout.

  Vedere [Risolvere i problemi di integrazione di Lookout](/intune-classic/troubleshoot/troubleshooting-lookout-integration) per assistenza per i problemi di accesso.

3.  Nella [console di Lookout](https://aad.lookout.com), nel modulo **System** (Sistema), scegliere la scheda **Connectors** (Connettori) e quindi selezionare **Intune**.

  ![screeenshot della console di Lookout con la scheda Connectors (Connettori) aperta e l'opzione Intune evidenziata](../media/mtp/lookout_mtp_setup-intune-connector.png)

4.  Passare a **Connectors** > **Connection Settings** (Connettori, Impostazioni di connessione) e specificare la frequenza di heartbeat in **Heartbeat Frequency** in minuti.

  ![screenshot della scheda delle impostazioni di connessione che mostra la frequenza di heartbeat configurata](../media/mtp/lookout-mtp-connection-settings.png)

## <a name="configure-enrollment-groups"></a>Configurare i gruppi di registrazione
1. Come procedura consigliata, creare un gruppo di sicurezza di Azure AD nel [portale di gestione di Azure AD](https://manage.windowsazure.com) con un numero limitato di utenti per verificare l'integrazione di Lookout.

  Tutti i dispositivi supportati da Lookout e registrati in Intune degli utenti in un gruppo di registrazione in Azure AD che vengono identificati e sono supportati, vengono registrati e sono idonei per l'attivazione nella protezione dalle minacce per il dispositivo di Lookout.

2. Nella [console di Lookout](https://aad.lookout.com), nel modulo **System** (Sistema), scegliere la scheda **Connectors** (Connettori) e selezionare **Enrollment Management** (Gestione registrazione) per definire il set di utenti i cui dispositivi devono essere registrati in Lookout. Aggiungere il nome visualizzato (**Display Name**) del gruppo di sicurezza di Azure AD per la registrazione.

  ![screenshot della pagina di registrazione di Intune Connector](../media/mtp/lookout-mtp-enrollment.png)

  >[!IMPORTANT]
  > Per il **Display Name** (Nome visualizzato) viene fatta distinzione tra maiuscole e minuscole, come indicato nella pagina **Proprietà** del gruppo di sicurezza nel portale di Azure. Come illustrato nell'immagine seguente, il nome indicato in **Display Name** (Nome visualizzato) per il gruppo di sicurezza ha iniziali maiuscole, mentre il titolo è tutto in lettere minuscole. Nella console di Lookout usare la combinazione di maiuscole/minuscole di **Display Name** (Nome visualizzato) per il gruppo di sicurezza.
  >![screenshot del portale di Azure, servizio Azure Active Directory, pagina delle proprietà](../media/mtp/aad-group-display-name.png)

  La procedura consigliata prevede l'uso dell'incremento predefinito (5 minuti) per verificare la presenza di nuovi dispositivi.

  **Limitazioni attuali:**
  * Lookout non può convalidare i nomi visualizzati dei gruppi.  Assicurarsi che il valore indicato nel campo **NOME VISUALIZZATO** nel portale di Azure sia identico al nome del gruppo di sicurezza di Azure AD.
  * La creazione di gruppi annidati non è supportata.  I gruppi di sicurezza di Azure AD usati in Lookout devono contenere solo utenti e non possono contenere altri gruppi.

3.  Dopo aver aggiunto un gruppo, alla successiva apertura dell'app Lookout for Work nel dispositivo supportato, il dispositivo viene attivato in Lookout.

4.  Quando si è soddisfatti dei risultati, è possibile estendere la registrazione ad altri gruppi di utenti.

## <a name="configure-state-sync"></a>Configurare la sincronizzazione dello stato
Nell'opzione **State Sync** (Sincronizzazione stato) specificare il tipo di dati che deve essere inviato a Intune.  Per il corretto funzionamento dell'integrazione di Lookout e Intune sono necessari sia lo stato del dispositivo che lo stato delle minacce.  Queste opzioni sono abilitate per impostazione predefinita.

## <a name="configure-error-report-email-recipient-information"></a>Configurare le informazioni per il destinatario dei report sugli errori tramite posta elettronica
Nella sezione **Error Management** (Gestione degli errori) immettere l'indirizzo di posta elettronica del destinatario dei report sugli errori.

![screenshot della pagina di gestione degli errori di Intune Connector](../media/mtp/lookout-mtp-connector-error-notifications.png)

## <a name="configure-enrollment-settings"></a>Configurare le impostazioni di registrazione
Nel modulo **System** (Sistema), nella pagina **Connectors** (Connettori), specificare il numero di giorni dopo i quali un dispositivo deve essere considerato disconnesso.  I dispositivi disconnessi sono considerati non conformi. L'accesso alle applicazioni aziendali tramite questi dispositivi in base ai criteri di accesso condizionale di Intune è bloccato. È possibile specificare un valore compreso tra 1 e 90 giorni.

![](../media/mtp/lookout-console-enrollment-settings.png)

## <a name="configure-email-notifications"></a>Configurare le notifiche tramite posta elettronica
Per ricevere avvisi relativi alle minacce tramite posta elettronica, accedere alla [console di Lookout](https://aad.lookout.com) con l'account utente che deve ricevere le notifiche. Nella scheda **Preferences** (Preferenze) del modulo **System** (Sistema) scegliere il livello delle minacce per cui generare le notifiche e impostarle su **ON** (Attivato). Salvare le modifiche.

![screenshot della pagina delle preferenze con l'account utente visualizzato](../media/mtp/lookout-mtp-email-notifications.png) Se non si vogliono più ricevere notifiche tramite posta elettronica, impostare le notifiche su **OFF** (Disattivato) e salvare le modifiche.

### <a name="configure-threat-classification"></a>Configurare la classificazione delle minacce
Lookout Mobile Threat Defense usa vari tipi di classificazione per le minacce ai dispositivi mobili. Alle [classificazioni delle minacce di Lookout](http://personal.support.lookout.com/hc/articles/114094130693) sono associati livelli di rischio predefiniti. Questi livelli possono essere modificati in qualsiasi momento per adattarli ai requisiti aziendali.

![screenshot della pagina dei criteri con minacce e classificazioni](../media/mtp/lookout-mtp-threat-classification.png)

>[!IMPORTANT]
> I livelli di rischio rappresentano un aspetto importante di Mobile Threat Defense perché l'integrazione con Intune calcola la conformità dei dispositivi in base a questi livelli di rischio in fase di esecuzione. In altre parole, l'amministratore di Intune imposta una regola nei criteri per identificare un dispositivo come non conforme se presenta una minaccia attiva con un livello minimo di rischio: **alto**, **medio** o **basso**. Il calcolo di conformità dei dispositivi in Intune dipende direttamente dai criteri di classificazione delle minacce in Lookout Mobile Threat Defense.

## <a name="watching-enrollment"></a>Monitoraggio della registrazione
Al termine della configurazione, Lookout Mobile Threat Defense inizia a eseguire il polling di Azure AD per i dispositivi corrispondenti ai gruppi di registrazione specificati.  Le informazioni sui dispositivi registrati sono disponibili nel modulo Devices (Dispositivi).  Per i dispositivi viene visualizzato lo stato iniziale in sospeso.  Lo stato del dispositivo cambia dopo l'installazione, l'apertura e l'attivazione nel dispositivo dell'app Lookout for Work.  Per informazioni dettagliate su come ottenere l'app Lookout for Work nel dispositivo, vedere l'argomento [Configurare e distribuire l'app Lookout for Work](configure-deploy-lookout-for-work-app.md).
## <a name="next-steps"></a>Passaggi successivi
[Abilitare la connessione a Lookout MTP in Intune](/intune-classic/deploy-use/enable-lookout-mtd-connection)
