---
title: "Monitorare la conformità dell&quot;accesso condizionale per Exchange locale ed Exchange Online"
titleSuffix: Intune Azure preview
description: "Monitorare la conformità dell&quot;accesso condizionale per Exchange locale ed Exchange Online tramite il portale di Azure in Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 9d5521de8709bf232dedfeeb1874f8db1898f2d0
ms.lasthandoff: 04/26/2017


---

# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune-azure-preview"></a>Monitorare la conformità dell'accesso condizionale per Exchange locale ed Exchange Online nell'anteprima di Azure in Intune

A partire dalla versione 1704 di Intune, gli amministratori possono vedere informazioni di report correlate ai record dei dispositivi Exchange ActiveSync sincronizzati con Intune tramite On-Premises Exchange Connector o il connettore da servizio a servizio di Intune (Exchange Online Connector). Le informazioni di report sulla conformità dell'accesso condizionale offrono un riepilogo dei dispositivi con stati di sincronizzazione diversi:

-   **Consentito**

-   **Bloccato**

-   **Quarantena**

## <a name="to-monitor-conditional-access-compliance"></a>Per monitorare la conformità dell'accesso condizionale

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2.  Dopo l'accesso viene visualizzato il **dashboard di Azure**.

3.  Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

4.  Scegliere **Intune**. Verrà visualizzato il **dashboard di Intune**.

5.  Scegliere **Accesso condizionale** e quindi scegliere **Panoramica**.

6.  Scegliere una delle tre aree (**Bloccato**, **Quarantena** o **Consentito**) nel grafico per visualizzare le informazioni di report sulla conformità dell'accesso condizionale.

    ![Dashboard dell'accesso condizionale](../media/CA-reporting-intune-1.png)

Dopo aver scelto una delle tre aree, è possibile visualizzare ulteriori dettagli sui dispositivi consentiti, bloccati o in quarantena.

È anche possibile eseguire il drill-down di dispositivi specifici per visualizzare ulteriori dettagli. Ad esempio, il dispositivo scelto nell'immagine seguente è bloccato. Intune offre la possibilità di rimuovere i dati aziendali dal pannello del report di conformità dell'accesso condizionale.

![Report dei dettagli del dispositivo per l'accesso condizionale](../media/CA-reporting-intune-3.png)

Nella pannello dei dettagli del dispositivo, è possibile visualizzare ulteriori informazioni:

-   **Panoramica:** sono visualizzate proprietà del dispositivo come versione del sistema operativo, modello, proprietà, numero di serie, produttore, numero di telefono e ora dell'ultima archiviazione.

-   **Proprietà:** è possibile impostare la proprietà del dispositivo (personale o aziendale).

-   **Hardware:** fornisce le informazioni visualizzate nella sezione Panoramica e inoltre altri dettagli su spazio di archiviazione (spazio totale e spazio disponibile), chassis di sistema, dettagli della rete, servizio di rete e altri dettagli di blocco dell'accesso condizionale.

-   **App individuate:** mostra tutte le applicazioni installate nel dispositivo. È anche possibile esportare l'elenco delle app installate in formato CSV.

-   **Conformità:** mostra tutti i dettagli dei criteri di conformità del dispositivo.

-   **Configurazione del dispositivo:** mostra tutti i dettagli di configurazione del dispositivo.

-   **Accesso ad Exchange:** in questa sezione sono disponibili ulteriori informazioni sullo stato del dispositivo dopo l'applicazione dei criteri di accesso condizionale.
