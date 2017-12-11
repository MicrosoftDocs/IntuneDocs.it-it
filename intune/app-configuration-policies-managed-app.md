---
title: Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi | Microsoft Docs
titlesuffix: Azure portal
description: Informazioni su come usare i criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi.
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c46d7e8f4291345a9da87f7a7a6f3180415b69a4
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile usare i criteri di configurazione delle app con le app gestite che supportano Intune App SDK anche su dispositivi non registrati. 

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** + **Intune**.
3. Scegliere il carico di lavoro delle **app per dispositivi mobili**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome**  
      Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**  
      La descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**  
      Scegliere **Gestisci le app**.
6. Selezionare **App associata** per scegliere l'app da configurare. Selezionare l'app dall'elenco di app già approvate e sincronizzate con Intune.
7. Per ogni impostazione di configurazione supportata dall'app digitare **Nome** e **Valore** e scegliere i puntini di sospensione (**...**).  
    Per eliminare una configurazione scegliere i puntini di sospensione (**...**) e selezionare **Elimina**.  
    Le app abilitate per Intune App SDK supportano le configurazioni in coppie chiave/valore. Per altre informazioni sulle configurazioni chiave-valore supportate, vedere la documentazione delle singole app.  
    È anche possibile usare token che verranno popolati in modo dinamico con i dati generati dall'applicazione.

## <a name="configuration-values-for-using-tokens"></a>Valori di configurazione per l'uso dei token

Intune può generare token e inviarli all'app gestita. Se ad esempio la configurazione dell'app è in grado di usare un'impostazione di posta elettronica, è possibile aggiungere un indirizzo di posta elettronica dinamico usando un token. Digitare il nome previsto dall'app nel campo **Nome** e quindi digitare `\{\{mail\}\}` nel campo **Valore**.

Intune supporta i tipi di token seguenti nelle impostazioni di configurazione:

- \{\{userprincipalname\}\}, ad esempio **John@contoso.com**
- \{\{mail\}\}, ad esempio **John@contoso.com**
- \{\{partialupn\}\}, ad esempio **John**
- \{\{accountid\}\}, ad esempio **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\}, ad esempio **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\}, ad esempio **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\}, ad esempio **John Doe**
- \{\{PrimarySMTPAddress\}\}, ad esempio **testuser@ad.domain.com** 


> [!Note]  
> I caratteri \{\{ e \}\} vengono usati solo dai tipi di token e non devono essere usati per altri scopi.

## <a name="next-steps"></a>Passaggi successivi

Procedere ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente l'app.