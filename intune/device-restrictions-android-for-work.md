---
title: Impostazioni delle restrizioni dei dispositivi Intune per Android for Work | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Anteprima di Intune di Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità dei dispositivi Android for Work aziendali."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 857522ef4931407accf98b2a2ad97334278c138f
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="work-profile-settings"></a>Impostazioni del profilo di lavoro
-     **Condivisione dei dati tra i profili di lavoro e personali**: usare questa impostazione per controllare se le app nel profilo di lavoro possono condividere dati con le app nel profilo personale. È possibile scegliere tra:
    - **Restrizioni predefinite per la condivisione**: questo è il comportamento di condivisione predefinito del dispositivo che varia a seconda della versione di Android in esecuzione. Per impostazione predefinita, la condivisione di dati dal profilo personale al profilo di lavoro è consentita. Per impostazione predefinita, la condivisione tra il profilo di lavoro e il profilo personale è bloccata. Questo impedisce il trasferimento di dati dal profilo di lavoro al profilo personale. Google non offre un modo per bloccare i dati che vanno dal profilo personale al profilo di lavoro in dispositivi che eseguono versioni precedenti alla 6.0.  
    - **Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale**: usare questa opzione per abilitare la funzionalità Android predefinita che consente la condivisione dal profilo personale al profilo di lavoro. Quando questa opzione è abilitata, una richiesta di condivisione iniziata da un'app nel profilo personale sarà in grado di condividere dati con app nel profilo di lavoro. Questo è il comportamento predefinito per i dispositivi Android che eseguono versioni precedenti alla 6.0.
    - **Le app nel profilo personale possono gestire una richiesta di condivisione dal profilo di lavoro**: abilita la condivisione all'interno dell'area del profilo di lavoro in entrambe le direzioni. Quando si seleziona questa impostazione, le app nel profilo di lavoro possono condividere dati con app non gestite nel profilo personale.  Usare questa impostazione con cautela poiché consente di trasferire dati gestiti nel profilo di lavoro alla parte non gestita del dispositivo.


-     **Notifiche del profilo di lavoro durante il blocco del dispositivo**: controlla se le app del profilo di lavoro possono visualizzare notifiche sulla schermata quando il dispositivo è bloccato.
-     **Autorizzazioni delle app predefinite**: imposta i criteri di autorizzazione predefiniti per tutte le app del profilo di lavoro. A partire da Android 6, alcune autorizzazioni necessarie per le app vengono richieste all'utente finale in fase di esecuzione. Questa impostazione dei criteri consente di determinare se e come viene richiesto agli utenti di concedere autorizzazioni per le app nel profilo di lavoro.
Ad esempio, si può eseguire il push nel profilo di lavoro di un'app che richiede l'accesso alla posizione. In genere viene visualizzata una finestra di dialogo per chiedere all'utente se vuole concedere all'app l'accesso alla posizione e l'utente può approvare o rifiutare questa richiesta. Questi criteri consentono di decidere se tutte le autorizzazioni devono essere concesse o rifiutate automaticamente senza visualizzare un messaggio di richiesta oppure se lasciare la scelta all'utente finale. È possibile scegliere tra:
    -     **Impostazione predefinita dispositivo**
    -     **Messaggio di richiesta**
    -     **Concedi automaticamente**
    -     **Nega automaticamente**

## <a name="password"></a>Password

- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono contenere (da **4**-**14**)
- **Numero massimo di minuti di inattività fino al blocco dello schermo**: selezionare la quantità di tempo che deve trascorrere prima che un dispositivo inattivo si blocchi automaticamente.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che i dati vengano cancellati dal dispositivo.
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. È possibile scegliere tra:
    - **Impostazione predefinita dispositivo**
    - **Protezione biometrica bassa**
    - **Richiesto**
    - **Almeno numerico**
    - **Complessa numerica**: (numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti)
    - **Almeno alfabetico**
    - **Almeno alfanumerico**
    - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di password nuove da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: impedisce a un utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo.
- **Smart Lock e altri agenti di attendibilità**: consente di controllare la funzionalità Smart Lock su dispositivi compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire che gli utenti configurino Smart Lock.

## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati
Usare i **criteri di configurazione personalizzati Android for Work** di Microsoft Intune per assegnare le impostazioni OMA-URI che è possibile usare per controllare le funzionalità nei dispositivi Android for Work. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di assegnare le impostazioni Android non configurabili con i criteri di Intune.
Intune supporta attualmente un numero limitato di criteri personalizzati Android. Vedere gli esempi in questo argomento per scoprire quali criteri è possibile configurare.

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome** |Immettere un nome univoco per il criterio personalizzato Android che consenta di identificarlo nella console di Intune.|
    |**Descrizione** |Fornire una descrizione di carattere generale sul criterio personalizzato Android e altre informazioni rilevanti per consentirne l'individuazione.|

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

  |Nome impostazione|Dettagli|
  |--------|--------------------|
  |**Nome** |Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
  |**Descrizione** |Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**OMA-URI (maiuscole/minuscole)** |Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
  |**Tipo di dati** |Selezionare il tipo di dati in cui verrà specificata questa impostazione OMA URI. Scegliere tra **Stringa, Stringa (XML), Data e ora, Intero, Virgola mobile** o **Booleano**.|
  |**Valore** |Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|
