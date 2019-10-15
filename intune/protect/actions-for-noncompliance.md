---
title: Messaggio e azioni per i dispositivi non conformi con Microsoft Intune - Azure | Microsoft Docs
description: Creare un messaggio di posta elettronica di notifica da inviare ai dispositivi non conformi. Se un dispositivo viene contrassegnato come non conforme, è possibile aggiungere azioni, ad esempio un periodo di tolleranza al termine del quale il dispositivo deve essere conforme, o creare una pianificazione per bloccare l'accesso finché il dispositivo non è conforme. Queste operazioni possono essere eseguite con Microsoft Intune in Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7fabc475e1ae05e6ef3fe70e8a507a15bee456cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727727"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi in Intune

Per i dispositivi che non soddisfano le regole o i criteri di conformità, è possibile aggiungere **Azioni per la non conformità**. Questa funzionalità consente di configurare una sequenza di azioni in ordine temporale, ad esempio l'invio di messaggi di posta elettronica all'utente finale o azioni di altro tipo.

## <a name="overview"></a>Panoramica

Per impostazione predefinita, quando Intune rileva un dispositivo che non è conforme, lo contrassegna immediatamente come non conforme. Quindi l'[accesso condizionale](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) di Azure Active Directory (AD) blocca il dispositivo. Quando un dispositivo non è conforme, la funzionalità **Azioni per la non conformità** consente inoltre di decidere cosa fare. Ad esempio, si può decidere di non bloccare immediatamente il dispositivo e di concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità.

Sono disponibili diversi tipi di azioni:

- **Invia un messaggio di posta elettronica all'utente finale**: è possibile personalizzare la notifica di posta elettronica prima di inviarla all'utente finale. È possibile personalizzare i destinatari, l'oggetto e il corpo del messaggio, inclusi il logo aziendale e le informazioni di contatto.

    Intune include inoltre le informazioni sul dispositivo non conforme nella notifica di posta elettronica.

- **Blocca in remoto il dispositivo non conforme**: per i dispositivi non conformi, è possibile impostare un blocco remoto. All'utente viene quindi richiesto un PIN o una password per sbloccare il dispositivo. Sono disponibili altre informazioni sulla funzionalità [Blocco remoto](../remote-actions/device-remote-lock.md). 

- **Contrassegna il dispositivo come non conforme**: è possibile creare una pianificazione (in numero di giorni) dopo la quale il dispositivo viene contrassegnato come non conforme. È possibile configurare l'azione in modo che venga applicata immediatamente oppure concedere all'utente un periodo di tolleranza entro il quale dovrà adeguarsi ai criteri di conformità.

Questo articolo illustra come:

- Creare un modello di notifica tramite messaggio
- Creare un'azione per la non conformità, ad esempio l'invio di un messaggio di posta elettronica o il blocco remoto di un dispositivo


## <a name="before-you-begin"></a>Prima di iniziare

- Per configurare le azioni per la mancata conformità è necessario aver creato almeno un criterio di conformità dei dispositivi. Per creare criteri di conformità dei dispositivi, vedere le piattaforme seguenti:

  - [Android](compliance-policy-create-android.md)
  - [Profili di lavoro Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Per usare i criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale di Azure AD. Vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) o [Modi comuni per usare l'accesso condizionale con Intune](conditional-access-intune-common-ways-use.md) per informazioni aggiuntive.

## <a name="create-a-notification-message-template"></a>Creare un modello di messaggio di notifica

Per inviare il messaggio di posta elettronica agli utenti, creare un modello di messaggio di notifica. Quando un dispositivo risulta non conforme, i dettagli immessi nel modello vengono visualizzati nel messaggio di posta elettronica inviato agli utenti.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Notifiche**.
3. Selezionare **Crea la notifica**. Immettere le informazioni seguenti:

   - **Nome**
   - **Oggetto**
   - **Message**
   - **Intestazione del messaggio di posta elettronica: includere il logo dell'azienda**
   - **Piè di pagina del messaggio di posta elettronica: includere il nome dell'azienda**
   - **Piè di pagina del messaggio di posta elettronica: includere le informazioni sul contatto**

   ![Esempio di messaggio di notifica di Intune relativo alla conformità](./media/actions-for-noncompliance/actionsfornoncompliance-1.PNG)

4. Dopo aver aggiunto le informazioni, scegliere **Crea**. Il modello di messaggio di notifica è pronto per l'uso. Il logo che si carica nell'ambito della personalizzazione del Portale aziendale viene usato per i modelli di posta elettronica. Per altre informazioni sulla personalizzazione del Portale aziendale, vedere [Personalizzazione dell'identità aziendale](../apps/company-portal-app.md#company-identity-branding-customization).

> [!NOTE]
> È anche possibile modificare o aggiornare un modello di notifica esistente creato in precedenza.

## <a name="add-actions-for-noncompliance"></a>Aggiungere azioni per la mancata conformità

Quando si crea un criterio di conformità del dispositivo, Intune crea automaticamente un'azione per la non conformità. Se un dispositivo non soddisfa i criteri di conformità, questa azione lo contrassegna come non conforme. È possibile personalizzare il periodo di tempo in cui il dispositivo rimane contrassegnato come non conforme. Questa azione non può essere rimossa.

È anche possibile aggiungere un'altra azione quando si crea un criterio di conformità o si aggiorna un criterio esistente. 

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e selezionare **Conformità del dispositivo**.
2. Selezionare **Criteri**, scegliere uno dei criteri e quindi selezionare **Proprietà**. 

    Non esiste ancora un criterio? Creare un criterio per [Android](compliance-policy-create-android.md), [iOS](compliance-policy-create-ios.md), [Windows](compliance-policy-create-windows.md) o un'altra piattaforma.
  
    > [!NOTE]
    > Attualmente i dispositivi JAMF e i dispositivi selezionati con i gruppi di dispositivi non possono ricevere le azioni di conformità.

3. Selezionare **Azioni per la mancata conformità** > **Aggiungi**.
4. Selezionare l'**azione**: 

    - **Invia un messaggio di posta elettronica all'utente finale**: quando il dispositivo non è conforme, scegliere di inviare un messaggio di posta elettronica all'utente. Inoltre: 
    
         - Scegliere il **modello di messaggio** creato in precedenza
         - Immettere eventuali **destinatari aggiuntivi** selezionando i gruppi
    
    - **Blocca in remoto il dispositivo non conforme**: quando il dispositivo non è conforme, bloccare il dispositivo. Questa azione obbliga l'utente a immettere un PIN o un passcode per sbloccare il dispositivo. 
    
5. Configurare i valori per l'opzione **Pianifica**: immettere il numero di giorni (da 0 a 365) dal rilevamento della non conformità, dopo cui attivare l'azione nei dispositivi degli utenti. Dopo questo periodo di tolleranza, è possibile applicare un criterio di [accesso condizionale](conditional-access-intune-common-ways-use.md). Se si immette **0** (zero) come numero di giorni, l'accesso condizionale viene applicato **immediatamente**. Ad esempio, se un dispositivo non è conforme, usare l'accesso condizionale per bloccare immediatamente l'accesso alla posta elettronica, a SharePoint e ad altre risorse dell'organizzazione.

    Quando si crea un criterio di conformità, viene creata automaticamente l'azione **Contrassegna il dispositivo come non conforme**, che viene impostata su **0** giorni (immediatamente). Con questa azione, durante l'archiviazione del dispositivo ne viene valutata immediatamente la conformità. Se si usa anche l'accesso condizionale, questo viene applicato immediatamente. Se si vuole consentire un periodo di tolleranza, modificare il valore di **Pianifica** nell'azione **Contrassegna il dispositivo come non conforme**.
    
    Nei criteri di conformità si vuole, ad esempio, anche inviare una notifica all'utente. A questo scopo, è possibile aggiungere l'azione **Invia un messaggio di posta elettronica all'utente finale**. In questa azione **Invia messaggio** si imposta **Pianifica** su 2 giorni. Se il dispositivo o l'utente finale viene ancora valutato come non conforme il giorno 2, il messaggio di posta elettronica viene inviato il giorno 2. Se si vuole inviare nuovamente il messaggio di posta elettronica all'utente il giorno 5 della mancata conformità, aggiungere un'altra azione e impostare **Pianifica** su 5 giorni.

    Per altre informazioni sulla conformità e sulle azioni predefinite, vedere la [panoramica della conformità](device-compliance-get-started.md).

6. Al termine, selezionare **Aggiungi** > **OK** per salvare le modifiche.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare i criteri](compliance-policy-monitor.md).