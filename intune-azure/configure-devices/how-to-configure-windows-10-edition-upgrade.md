---
title: Configurare gli aggiornamenti edizione di Windows 10 con Intune
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulla modalità d&quot;uso di Intune per aggiornare i dispositivi Windows 10 gestiti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 617ca50569885431394ab630f297ba919d119522
ms.lasthandoff: 03/15/2017


---

# <a name="how-to-configure-windows-10-edition-upgrades-in-microsoft-intune"></a>Come configurare gli aggiornamenti edizione di Windows 10 in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare le informazioni in questo argomento per imparare a configurare un profilo di aggiornamento edizione di Windows 10. Questo profilo consente di aggiornare automaticamente i dispositivi che eseguono una delle versioni seguenti di Windows 10 a un'edizione più recente:

- Windows 10 Home
- Windows 10 Holographic
- Windows 10 Mobile


Sono supportati i seguenti percorsi di aggiornamento:

- Da Windows 10 Pro a Windows 10 Enterprise
- Da Windows 10 Home a Windows 10 Education
- Da Windows 10 Mobile a Windows 10 Mobile Enterprise
- Da Windows 10 Holographic Pro a Windows 10 Holographic Enterprise


## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare l'aggiornamento dei dispositivi alla versione più recente, è necessario uno degli elementi seguenti:

- Un codice Product Key valido per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio le edizioni Windows 10 Desktop. È possibile usare codici ad attivazione multipla o chiavi del server di gestione delle chiavi. o un file di licenza di Microsoft che contiene le informazioni sulle licenze per installare la nuova versione di Windows in tutti i dispositivi da usare come destinazione dei criteri, ad esempio per le edizioni Windows 10 Mobile e Windows 10 Holographic.
- I dispositivi Windows 10 da usare come destinazione devono essere registrati in Microsoft Intune. Non è possibile usare criteri di aggiornamento dell'edizione con PC che eseguono il software client per PC di Intune.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di aggiornamento dell'edizione.
5. Dall'elenco a discesa **Piattaforma** scegliere **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Aggiornamento edizione**.
7. Nel pannello **Aggiornamento edizione** configurare quanto segue:
    - **Edizione da cui eseguire l'aggiornamento**: dall'elenco a discesa selezionare la versione Windows 10 che si desidera aggiornare sui dispositivi.
    - **Edizione a cui eseguire l'aggiornamento**: nell'elenco a discesa selezionare la versione di Windows 10 Desktop, Windows 10 Holographic o Windows 10 Mobile a cui aggiornare i dispositivi specificati.
    - **Codice Product Key**: specificare il codice Product Key ottenuto da Microsoft che può essere usato per aggiornare tutti i dispositivi Windows 10 Desktop di destinazione.<br>Dopo aver creato criteri che contengono un codice Product Key, non è possibile modificarlo in un secondo momento, perché il codice viene nascosto per motivi di sicurezza. Per modificare il codice Product Key, è necessario immettere nuovamente l'intero codice.
    - **File di licenza**: scegliere **Sfoglia** per selezionare il file di licenza ottenuto da Microsoft che contiene informazioni sulla licenza per l'edizione Windows Holographic o Windows 10 Mobile in base alla quale si vogliono aggiornare i dispositivi di destinazione.
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).

