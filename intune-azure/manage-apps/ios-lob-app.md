---
title: Come aggiungere app line-of-business iOS in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: Informazioni sull&quot;aggiunta di app line-of-business per iOS a Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 141207ac61aade0816a66eb6e672596416bc0906
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per iOS in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello Intune, scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere Gestisci > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **File di installazione del software**.
7. Nel pannello **Selezionare un file di installazione** fare clic sul pulsante Sfoglia e individuare il file di installazione di app per iOS con estensione ipa, quindi fare clic su **OK**.

## <a name="step-2---configure-app-information"></a>Passaggio 2: configurare le informazioni sull'app

1. Nel pannello **Modifica l'app** configurare le informazioni seguenti. Al termine, fare clic su **Aggiungi**. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
    - **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione app**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Tipo di dispositivo applicabile**: selezionare questa impostazione se l'app può essere installata su iPad, iPhone o iPod compatibili.
    - **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria** (facoltativo): selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Carica l'icona**: Caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
2. Al termine, nel pannello **Aggiungi app** scegliere **Salva**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).