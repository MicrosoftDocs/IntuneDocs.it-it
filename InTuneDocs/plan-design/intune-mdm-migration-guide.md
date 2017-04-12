---
title: Guida alla migrazione alla gestione dei dispositivi mobili (MDM) di Intune | Microsoft Docs
description: "Lo scopo di questa guida è presentare ai clienti i vari dettagli correlati alla migrazione da un provider MDM di terze parti a Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 444cb61ea57b92924a681c564a1a913f4204ea89
ms.lasthandoff: 03/28/2017


---

# <a name="intune-migration-guide"></a>Guida alla migrazione a Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

![Grafica della migrazione all'ambiente MDM di Intune](../media/MDM-migration-guide-art.PNG)

Il successo della migrazione a Intune dipende, per iniziare, da un piano ben articolato che tenga conto dell'ambiente MDM corrente, degli obiettivi aziendali e dei requisiti tecnici. È inoltre necessario l'appoggio delle principali parti interessate, ovvero colore che supporteranno il piano di migrazione e collaboreranno alla sua messa in opera.

Lo scopo di questa guida è presentare i vari dettagli correlati alla migrazione da un provider MDM di terze parti a Intune.

## <a name="whats-included-in-this-guide"></a>Contenuti della guida

La guida è suddivisa in due fasi, che includono entrambe attività, strategie e indicazioni tattiche utili per eseguire passo-passo il processo completo per la migrazione all'ambiente MDM di Intune.

-   [Fase 1: Preparare Intune per la gestione dei dispositivi mobili (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)

    -   [Valutare i requisiti per la gestione dei dispositivi mobili](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)

    -   [Configurazione di base](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

    -   [Configurare i criteri di gestione di dispositivi e app](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

    -   [Configurare i criteri di protezione delle app (facoltativo)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

    -   [Considerazioni speciali sulla migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

-   [Fase 2: Campagna di migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

    -   [Piano di comunicazione](https://docs.microsoft.com/intune/plan-design/migration-phase2-communication-plan)

    -   [Promuovere l'adozione da parte degli utenti finali con l'accesso condizionale](https://docs.microsoft.com/intune/plan-design/migration-phase2-drive-end-user-adoption-with-conditional-access)
    
    -   [Ciclo di migrazione tipico](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle)
        -   [Monitoraggio della migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#monitoring-migration)
        -   [Attività post-migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase2-typical-migration-cycle#post-migration)

## <a name="assumptions"></a>Presupposti

-   Il servizio Intune è già stato valutato in un ambiente PoC (modello di verifica) ed è già stata presa la decisione di usarlo come soluzione MDM nell'organizzazione.

-   Familiarità con Intune e le relative funzionalità. 

> [!NOTE]
> Per ottenere una maggiore familiarità con Intune prima di procedere con la migrazione, consultare la [Guida alla valutazione di Intune](https://docs.microsoft.com/intune/understand-explore/sign-up-for-30-day-trial-microsoft-intune).

## <a name="before-you-begin"></a>Prima di iniziare

È importante tenere presente che la nuova distribuzione di Intune potrebbe essere diversa dalla distribuzione della soluzione MDM precedente. Diversamente dai servizi MDM tradizionali, la soluzione Intune è incentrata sul controllo degli accessi in base all'identità e quindi non richiede un appliance proxy di rete per controllare l'accesso ai dati aziendali da dispositivi mobili all'esterno del perimetro di rete dell'organizzazione. Microsoft offre varie soluzioni per proteggere i servizi dati nel cloud stesso tramite una suite di servizi cloud strettamente integrati, un'offerta nota collettivamente come Enterprise Mobility + Security.

-   Vedere i [metodi comuni per l'uso di Intune](https://docs.microsoft.com/intune/understand-explore/common-ways-to-use-intune) e iniziare a compilare le risposte alle domande in [Fase 1: Valutare i requisiti per la gestione dei dispositivi mobili](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="next-steps"></a>Passaggi successivi

[Fase 1: Preparare Intune per la gestione dei dispositivi mobili (MDM)](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management)
