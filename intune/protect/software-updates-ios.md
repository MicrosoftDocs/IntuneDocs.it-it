---
title: Configurare i criteri di aggiornamento software per iOS in Microsoft Intune - Azure | Microsoft Docs
description: In Microsoft Intune è possibile creare o aggiungere criteri di configurazione per limitare l'installazione automatica di aggiornamenti software nei dispositivi iOS gestiti da o sotto la supervisione di Intune. È possibile scegliere la data e ora in cui l'installazione degli aggiornamenti non verrà effettuata. È anche possibile assegnare questi criteri a gruppi, utenti o dispositivi e verificare la presenza di eventuali errori di installazione.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54e6cc0b3df95c74abf4b4ef1b827f8e121e3645
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726661"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Aggiungere criteri di aggiornamento software per iOS in Intune

I criteri di aggiornamento software consentono di forzare l'installazione automatica dell'aggiornamento del sistema operativo più recente disponibile nei dispositivi iOS con supervisione. Quando si configurano criteri, è possibile aggiungere i giorni e gli orari in cui si vuole che i dispositivi non installino aggiornamenti.

Questa funzionalità si applica a:

- iOS 10.3 e versioni successive (con supervisione)

Il dispositivo si collega a Intune ogni 8 ore. Se è disponibile un aggiornamento (al di fuori dell'orario sottoposto a restrizioni), il dispositivo scarica e installa l'aggiornamento più recente del sistema operativo. Non è necessario alcun intervento dell'utente per aggiornare il dispositivo. I criteri non impediscono a un utente di aggiornare manualmente il sistema operativo.

## <a name="configure-the-policy"></a>Configurare i criteri

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Aggiornamenti software** > **Criteri di aggiornamento per iOS** > **Crea**.
3. Immettere le impostazioni seguenti:

    - **Nome**: immettere un nome per il criterio di aggiornamento software. Immettere ad esempio `iOS restricted update times`.
    - **Description**: immettere una descrizione per il criterio. Questa impostazione è facoltativa ma consigliata.

4. Selezionare **Impostazioni > Configura**. Immettere le impostazioni seguenti:

    - **Selezionare gli orari per impedire le installazioni di aggiornamenti**: specificare un intervallo di tempo limitato durante il quale non deve essere forzata l'installazione degli aggiornamenti.
      - I blocchi nelle ore notturne non sono supportati e potrebbero non funzionare. Ad esempio, non configurare un criterio con *Ora di inizio* alle 20.00 e *Ora di fine* alle 6.00.
      - Un criterio che inizia a alle 00.00 e termina alle 00.00 viene valutato come 0 ore e non 24 ore, ovvero nessuna limitazione.

      Nell'impostare l'intervallo di tempo limitato, immettere i dettagli seguenti:

      - **Giorni**: scegliere il giorno o i giorni della settimana in cui gli aggiornamenti non vengono installati. Ad esempio, selezionare Lunedì, Mercoledì e Venerdì per impedire l'installazione degli aggiornamenti in questi giorni.
      - **Fuso orario**: scegliere un fuso orario.
      - **Ora di inizio**: scegliere l'ora di inizio dell'intervallo di tempo limitato. Ad esempio, immettere 5.00 in modo che gli aggiornamenti non vengano installati a partire dalle 5.00.
      - **Ora di fine**: scegliere l'ora di fine dell'intervallo di tempo limitato. Ad esempio, immettere 1.00 in modo che gli aggiornamenti possano essere installati a partire dall'1.00.

    - **Delay visibility of software updates to end users with no change to scheduled updates in the software update policy(days)** (Ritarda la visibilità degli aggiornamenti software per gli utenti finali senza modificare gli aggiornamenti pianificati nei criteri di aggiornamento software (giorni)): 

      **Se si vuole ritardare la visibilità degli aggiornamenti software per un periodo di tempo specifico nei dispositivi iOS con supervisione, configurare queste impostazioni in [Limitazioni del dispositivo](../configuration/device-restrictions-ios.md#general). I criteri di aggiornamento software sostituiscono tutte le restrizioni dei dispositivi. Se entrambe le impostazioni sono attive, i criteri di aggiornamento software avranno la priorità ogni volta.

      > [!IMPORTANT]  
      > Un criterio i cui valori per *Ora di inizio* e *Ora di fine* sono impostati sulle 00.00 viene valutato come 0 ore e non 24 ore. Questo significa nessuna limitazione.  

5. Selezionare **OK** > **Crea** per salvare le modifiche e creare il criterio.

I criteri vengono creati e visualizzati nell'elenco dei criteri.

Per indicazioni a cura del team di supporto di Intune, vedere [Ritardare la visibilità degli aggiornamenti software in Intune per i dispositivi con supervisione](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Il software MDM di Apple non consente di imporre a un dispositivo di installare gli aggiornamenti entro un'ora o data determinata.

## <a name="change-the-restricted-times-for-the-policy"></a>Modificare gli intervalli di tempo dotati di restrizioni per il criterio

1. In **Aggiornamenti software** selezionare **Criteri di aggiornamento per iOS**.
2. Scegliere dei criteri esistenti > **Proprietà**.
3. Aggiornare il periodo con limitazioni:

    1. Scegliere i giorni della settimana
    2. Scegliere il fuso orario nel quale verranno applicati i criteri
    3. Immettere l'ora di inizio e fine della disattivazione

    > [!NOTE]
    > Se i valori per **Ora di inizio** e **Ora di fine** sono entrambi impostati sulle 00.00, Intune non controlla le limitazioni riguardo a quando installare gli aggiornamenti. Questo significa che tutte le configurazioni per **Selezionare gli orari per impedire le installazioni di aggiornamenti** vengono ignorate e gli aggiornamenti possono essere installati in qualunque momento.  

## <a name="assign-the-policy-to-users"></a>Assegnare i criteri agli utenti

I criteri esistenti vengono assegnati a gruppi, utenti o dispositivi. Dopo l'assegnazione, i criteri vengono applicati.

1. In **Aggiornamenti software** selezionare **Criteri di aggiornamento per iOS**.
2. Scegliere dei criteri esistenti > **Assegnazioni**.
3. Selezionare gruppi, utenti o dispositivi Azure Active Directory da includere o escludere dai criteri.
4. Scegliere **Salva** per distribuire i criteri agli utenti.

I dispositivi usati dagli utenti a cui sono destinati i criteri vengono valutati per la conformità degli aggiornamenti. Questo criterio supporta anche i dispositivi senza utente.

## <a name="monitor-device-installation-failures"></a>Monitorare gli errori di installazione nei dispositivi
<!-- 1352223 -->
**Aggiornamenti software** > **Errori di installazione per dispositivi iOS** mostra un elenco di dispositivi con supervisione per cui è stato impostato un criterio di aggiornamento, è stato tentato un aggiornamento e non è stato possibile eseguirlo. Per ogni dispositivo, è possibile visualizzare il motivo per cui l'aggiornamento automatico non è riuscito. I dispositivi integri e aggiornati non vengono visualizzati nell'elenco. Un dispositivo è aggiornato se include l'ultimo aggiornamento supportato dal dispositivo stesso.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](../configuration/device-profile-assign.md) e [monitorarne lo stato](../configuration/device-profile-monitor.md).