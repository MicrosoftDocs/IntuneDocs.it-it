---
title: Come usare Windows Hello for Business
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni su come creare un criterio per controllare l&quot;uso di Windows Hello for Business nei dispositivi gestiti.'
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 541be8b8-8668-41be-afce-3f3e08c12191
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4d375a40283a5f3c1e9b7302d659739d4ca3d508
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="use-windows-hello-for-business"></a>Usare Windows Hello for Business


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Microsoft Intune si integra con Windows Hello for Business (precedentemente noto come Microsoft Passport for Work), un metodo di accesso alternativo che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale.

Hello for Business consente di eseguire l'accesso usando un *movimento dell'utente* invece di una password. Un movimento dell'utente può essere un PIN semplice, l'autenticazione biometrica come Windows Hello o un dispositivo esterno come un lettore di impronte digitali.

Intune si integra con Hello for Business in due modi:

-   È possibile usare i criteri di Intune per controllare i movimenti che gli utenti possono usare o meno per l'accesso.

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Nelle versioni di Windows 10 Desktop e Mobile precedenti all'aggiornamento dell'anniversario era possibile impostare due diversi PIN da usare per l'autenticazione alle risorse:
- Il **PIN dispositivo** che poteva essere usato per sbloccare il dispositivo e connetterlo alle risorse cloud.
- Il **PIN per lavoro** che veniva usato per accedere alle risorse di Azure AD nei dispositivi personali dell'utente (BYOD).

>Nell'aggiornamento dell'anniversario questi due PIN sono stati uniti in un unico PIN dispositivo.
Eventuali criteri di configurazione di Intune impostati per controllare il PIN del dispositivo ed eventuali criteri di Windows Hello for Business configurati, ora impostano questo nuovo valore di PIN.
Se entrambi i tipi di criteri sono stati impostati per controllare il PIN, i criteri di Windows Hello for Business verranno applicati ai dispositivi Windows 10 Desktop e Mobile.
Per assicurarsi che i conflitti dei criteri vengano risolti e che i criteri dei PIN vengano applicati correttamente, aggiornare i criteri di Windows Hello for Business in modo che corrispondano alle impostazioni nei criteri di configurazione e chiedere agli utenti di sincronizzare i propri dispositivi nell'app Portale aziendale.



## <a name="create-a-windows-hello-for-business-policy"></a>Creare un criterio di Windows Hello for Business

1.  Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2.  Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Gestisci** > **Windows Hello for Business**.

3.  Nel pannello visualizzato scegliere le impostazioni **predefinite**.

4.  Nel pannello **Tutti gli utenti** fare clic su **Proprietà** e immettere un **nome** e una **descrizione** facoltativa per le impostazioni di Windows Hello for Business.

5. Nel pannello **Tutti gli utenti** fare clic su **Impostazioni** e quindi per **Configura Windows Hello for Business** scegliere tra le seguenti impostazioni:

    - **Disabilitato**. Selezionare questa impostazione se non si vuole usare Windows Hello for Business. Tutte le altre impostazioni nella schermata risultano non disponibili.
    - **Attivata**. Selezionare questa impostazione se si vuole configurare le impostazioni di Windows Hello for Business.
    - **Non configurato**. Selezionare questa impostazione se non si vuole usare Intune per controllare le impostazioni di Windows Hello for Business. Eventuali impostazioni di Windows Hello for Business presenti nei dispositivi Windows 10 non verranno modificate. Tutte le altre impostazioni nel pannello non sono disponibili.

6.  Se si seleziona **Abilitato** nel passaggio precedente, configurare le impostazioni obbligatorie che verranno applicate a tutti i dispositivi Windows 10 e Windows 10 Mobile registrati.

 - **Usa un modulo TPM (Trusted Platform Module)**. Un chip TPM (Trusted Platform Module) fornisce un livello aggiuntivo di sicurezza dei dati.<br>Scegliere uno dei valori seguenti:

     - **Obbligatorio** (impostazione predefinita). Solo i dispositivi con un modulo TPM accessibile possono eseguire il provisioning di Windows Hello for Business.
     - **Preferito**. I dispositivi provano a usare prima un modulo TPM. Se non è disponibile, possono usare la crittografia software.

 - **Richiedi lunghezza minima del PIN**/**Richiedi lunghezza massima del PIN**. Configura i dispositivi in modo che usino i valori massimo e minimo specificati per la lunghezza del PIN per garantire l'accesso protetto. La lunghezza del PIN predefinita è 6 caratteri, ma è possibile applicare una lunghezza minima di 4 caratteri. La lunghezza massima del PIN è 127 caratteri.

 - **Richiedi lettere minuscole nel PIN**/**Richiedi lettere maiuscole nel PIN**/**Caratteri speciali nel PIN**. Per applicare un PIN più complesso, richiedere l'utilizzo di lettere maiuscole, lettere minuscole e caratteri speciali nel PIN. È possibile scegliere tra:

     - **Consentito**. Gli utenti possono usare il tipo di carattere specificato nel proprio PIN, ma non è obbligatorio.
    
     - **Obbligatorio**. Gli utenti devono includere almeno uno dei tipi di carattere specificati nel PIN. Ad esempio, di solito si richiede almeno una lettera maiuscola e un carattere speciale.

     - **Non consentito** (impostazione predefinita). Gli utenti non devono usare questi tipi di carattere nel PIN. Se l'opzione non è configurata, questa è l'impostazione predefinita.<br>I caratteri speciali includono: **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

 - **Scadenza PIN (giorni)**. Si consiglia di specificare un periodo di scadenza dopo il quale gli utenti finali devono modificare il PIN. L'impostazione predefinita è 41 giorni.

 - **Ricorda cronologia PIN**. Limita il riutilizzo di PIN usati in precedenza. Per impostazione predefinita, non è possibile riutilizzare gli ultimi 5 PIN.

 - **Consenti autenticazione biometrica**. Abilita l'autenticazione biometrica, ad esempio il riconoscimento facciale o delle impronte digitali, come alternativa a un PIN di Windows Hello for Business. Gli utenti devono comunque configurare un PIN aziendale in caso di errore dell'autenticazione biometrica. È possibile scegliere tra:

     - **Sì**. Windows Hello for Business consente l'autenticazione biometrica.
     - **No**. Windows Hello for Business impedisce l'autenticazione biometrica per tutti i tipi di account.

 - **Usa anti-spoofing avanzato, se disponibile**. Consente di configurare se usare le funzionalità di anti-spoofing di Windows Hello nei dispositivi che lo supportano, ad esempio il rilevamento di una fotografia di un viso invece di un viso reale.<br>Se impostato su **Sì**, Windows richiede a tutti gli utenti di usare la funzionalità di anti-spoofing per le caratteristiche del viso, se supportata.

 - **Usare l'accesso tramite telefono**. Se questa opzione è impostata su **Sì**, gli utenti possono usare Passport remoto come dispositivo portatile complementare per l'autenticazione del computer desktop. Il computer desktop deve essere aggiunto ad Azure Active Directory e il dispositivo complementare deve essere configurato con un PIN di Windows Hello for Business.


## <a name="further-information"></a>Altre informazioni
Per altre informazioni su Microsoft Passport, vedere [la guida](https://technet.microsoft.com/library/mt589441.aspx) nella documentazione di Windows 10.
