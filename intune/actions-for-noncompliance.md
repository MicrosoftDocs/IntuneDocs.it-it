---
title: "Azioni per la non conformità con Intune"
titleSuffix: Intune on Azure
description: "Informazioni su come creare azioni per la non conformità con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3adc3c01d4657accfdb5cd70970ff191d06a9aef
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2017
---
# <a name="automate-actions-for-noncompliance"></a>Automatizzare le azioni per la non conformità

Le **azioni per la non conformità** consentono di configurare una sequenza temporale di azioni da applicare ai dispositivi che non soddisfano i criteri di conformità. Per impostazione predefinita, quando viene rilevato che un dispositivo non soddisfa i criteri di conformità Intune lo contrassegna immediatamente come non conforme, quindi il dispositivo viene bloccato dall'accesso condizionale di Azure Active Directory. Le **azioni per la non conformità** consentono di decidere con maggior flessibilità come procedere quando un dispositivo risulta non conforme. È ad esempio possibile decidere di non bloccare immediatamente il dispositivo e di concedere all'utente un periodo di tolleranza per adeguarsi ai criteri di conformità.

Esistono due tipi di azioni:

-   **Notifica agli utenti finali tramite posta elettronica**: è possibile personalizzare il messaggio di posta elettronica di notifica prima di inviarlo all'utente finale. Intune include opzioni per personalizzare l'oggetto, il corpo del messaggio incluso il logo aziendale, le informazioni di contatto ed eventuali altri destinatari.

-   **Contrassegnare il dispositivo come non conforme**: è possibile pianificare un numero di giorni trascorsi i quali il dispositivo viene contrassegnato come non conforme. È possibile scegliere di applicare il blocco immediatamente oppure concedere all'utente un periodo di tolleranza entro il quale dovrà adeguarsi ai criteri di conformità dei dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare

Per configurare le azioni per la mancata conformità è necessario aver creato almeno un criterio di conformità dei dispositivi.

-   Vedere la procedura per creare criteri di conformità dei dispositivi per:

    -   [Android](compliance-policy-create-android.md)

    -   [Android for Work](compliance-policy-create-android-for-work.md)

    -   [iOS](compliance-policy-create-ios.md)
    
    -   [macOS](compliance-policy-create-mac-os.md)

    -   [Windows](compliance-policy-create-windows.md)

Quando si prevede di applicare criteri di conformità per impedire ai dispositivi di usare le risorse aziendali, è necessario aver configurato l'accesso condizionale di Azure AD.

- Vedere la procedura per [configurare l'accesso condizionale EMS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

È inoltre necessario aver creato un modello di messaggio di notifica. Questo modello verrà usato in un secondo momento, durante la creazione delle azioni per la mancata conformità, per inviare notifiche di posta elettronica agli utenti.

### <a name="to-create-a-notification-message-template"></a>Per creare un modello di messaggio di notifica

1. Passare a [Intune nel portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune.

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**

4. Scegliere **Conformità del dispositivo**, quindi **Notifiche** nella sezione **Gestisci**.

5. Scegliere **Crea la notifica**, quindi immettere quanto segue:

    a.  Nome

    b.  Subject

    c.  Messaggio

    d.  Intestazione del messaggio di posta elettronica - Includere il logo dell'azienda

    e.  Piè di pagina del messaggio di posta elettronica - Includere il nome dell'azienda

    f.  Piè di pagina del messaggio di posta elettronica - Includere le informazioni sul contatto

![esempio del modello di messaggio di notifica](./media/actionsfornoncompliance-1.PNG)

Dopo aver aggiunto le informazioni, scegliere **Crea**. Il modello di messaggio di notifica è disponibile per l'uso.

> [!NOTE] 
> È anche possibile modificare un modello di notifica creato in precedenza.

## <a name="to-create-actions-for-non-compliance"></a>Per creare azioni per la mancata conformità

> [!TIP]
> Intune offre un'azione predefinita nella sezione Azioni per la non conformità. Questa azione contrassegna il dispositivo come non conforme se rileva che non soddisfa i criteri di conformità per i dispositivi. È possibile personalizzare dopo quanto tempo dal rilevamento il dispositivo viene contrassegnato come non conforme. Questa azione non può essere rimossa.

È possibile aggiungere un'azione nel momento in cui si crea un nuovo criterio di conformità dei dispositivi o si modifica un criterio esistente.

1.  Nel carico di lavoro di Intune, nel pannello **Tutti i criteri di conformità del dispositivo** scegliere **Criteri** nella sezione **Gestisci**.

2.  Scegliere un criterio di conformità del dispositivo facendo clic su di esso, quindi scegliere **Proprietà** nella sezione **Gestisci**.

3.  Verrà aperto il pannello **Device compliance policy properties** (Proprietà dei criteri di conformità del dispositivo) in cui scegliere **Azioni per la non conformità**.

4.  Verrà aperto il pannello Azioni per la non conformità in cui scegliere **Aggiungi** per specificare i parametri dell'azione. È possibile scegliere il modello di messaggio creato in precedenza, uno più destinatari aggiuntivi e la pianificazione del periodo di tolleranza. È possibile specificare il numero di giorni (da 0 a 365) nella pianificazione, quindi applicare i criteri di accesso condizionale. Se si specifica **0** come numero di giorni, l'accesso condizionale deve bloccare **immediatamente** l'accesso alle risorse aziendali quando i dispositivi risultano non conformi ai criteri.

5.  Dopo aver aggiunto le informazioni, scegliere **Aggiungi**, quindi **OK**.

## <a name="next-steps"></a>Passaggi successivi

È possibile monitorare l'attività di conformità del dispositivo eseguendo i report disponibili nel pannello di conformità del dispositivo. Per altre informazioni, vedere [Come monitorare la conformità dei dispositivi in Intune](device-compliance-monitor.md).
