---
title: 'Guida introduttiva: creare un profilo di posta elettronica del dispositivo per iOS'
titleSuffix: Microsoft Intune
description: Informazioni su come usare Microsoft Intune per creare un profilo di posta elettronica del dispositivo affinché i dispositivi iOS possano connettersi in modo sicuro alla posta elettronica aziendale.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ad26077c00bf4ad4350ebd9ee124d61a69b324
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723866"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>Guida introduttiva: Creare un profilo di posta elettronica del dispositivo per iOS

In questa guida introduttiva verrà illustrato come creare un profilo di posta elettronica per i dispositivi iOS. Questo profilo specifica le impostazioni necessarie per l'app di posta elettronica predefinita per consentire al dispositivo iOS di connettersi alla posta elettronica aziendale. I profili di posta elettronica del dispositivo facilitano l'omogeneità delle impostazioni tra i dispositivi e consentono agli utenti finali di accedere alla posta elettronica aziendale dai dispositivi personali senza alcuna configurazione manuale. Per proteggere ulteriormente la posta elettronica, è possibile usare un profilo di posta elettronica per determinare se i dispositivi sono conformi e quindi configurare l'accesso condizionale per consentire ai soli dispositivi conformi di accedere alla posta elettronica. Per altre informazioni sui profili di posta elettronica, vedere [Come configurare le impostazioni di posta elettronica in Microsoft Intune](email-settings-configure.md)

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="create-an-ios-email-profile"></a>Creare un profilo di posta elettronica iOS
1. In Intune selezionare **Configurazione del dispositivo** e quindi **Profili**.
2. Selezionare **Crea profilo**.
   
   ![Creare un profilo di posta elettronica per iOS](./media/quickstart-email-profile/ios-create-profile.png)

3. In **Nome** immettere un nome descrittivo per il nuovo profilo. Per questo esempio, immettere **Dispositivi iOS richiedono posta elettronica aziendale**.
4. Immettere le seguenti informazioni per il profilo:
   - Per **Descrizione** immettere **Richiedi che i dispositivi iOS usino la posta elettronica aziendale**.
   - Per **Piattaforma**, selezionare **iOS**.
   - Per **Tipo di profilo** selezionare **Posta elettronica**.
    
     ![Creare un profilo di posta elettronica per l'uso con iOS](./media/quickstart-email-profile/ios-email-profile-name.png)

5. Selezionare **Impostazioni** e immettere le impostazioni seguenti, lasciando i valori predefiniti per le altre:
   - **Server di posta elettronica**: per questa guida introduttiva, immettere **outlook.office365.com**. Questa impostazione specifica la posizione di Exchange (URL) del server di posta elettronica che l'app di posta elettronica iOS userà per connettersi alla posta elettronica.
   - **Nome account**: immettere **Indirizzo di posta elettronica dell'azienda**.
   - **Attributo nome utente da AAD**: questo nome è l'attributo che Intune ottiene da Azure Active Directory (Azure AD). Intune genera in modo dinamico il nome utente usato da questo profilo basandosi su questo nome. Per questa guida introduttiva si presuppone che si desideri usare **Nome dell'entità utente** come nome utente per il profilo (ad esempio, user1@contoso.com).
   - **Attributo indirizzo di posta elettronica da AAD**: questa impostazione è l'indirizzo di posta elettronica di Azure AD che verrà usato per accedere a Exchange. Per questa guida introduttiva, selezionare **Nome dell'entità utente**.
   - **Metodo di autenticazione**: per questa guida introduttiva, selezionare **Nome utente e password**. In alternativa, è possibile scegliere **Certificato** se è già stato impostato un certificato per Intune.
    
     ![Creare un profilo di posta elettronica per l'uso con iOS](./media/quickstart-email-profile/ios-email-profile.png)

6. Selezionare **OK**.
7. Selezionare **Crea**. Il nuovo profilo compare nell'elenco dei profili con il dashboard visualizzato così da poter monitorare il modo in cui il profilo è stato assegnato ai dispositivi iOS e agli utenti iOS.
8. Selezionare **Assegnazioni**.
9. Selezionare la scheda **Includi** e quindi selezionare **Tutti gli utenti e tutti i dispositivi**. 
10. Selezionare **Salva**.

## <a name="clean-up-resources"></a>Pulizia delle risorse
Se non si prevede di usare il profilo creato per esercitazioni o test aggiuntivi, è possibile eliminarlo ora.
1. In Intune selezionare **Configurazione del dispositivo** e quindi **Profili**.
2. Selezionare il profilo di test appena creato **Dispositivi iOS richiedono posta elettronica aziendale**.
3. Selezionare i punti di sospensione ( **...** ) accanto al profilo, quindi fare clic su **Elimina**.

## <a name="next-steps"></a>Passaggi successivi

In questa guida introduttiva è stato creato un profilo di posta elettronica per i dispositivi iOS. Ora è possibile usare questo profilo per determinare se un dispositivo iOS è conforme ai criteri di conformità che contrassegnano come non conformi tutti i dispositivi iOS che non corrispondono al profilo. Per un'ulteriore protezione, è possibile creare un criterio di accesso condizionale che impedisce ai dispositivi iOS non conformi di accedere alla posta elettronica. Per altre informazioni sui criteri di conformità dei dispositivi, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](../protect/device-compliance-get-started.md).

> [!div class="nextstepaction"]
> [Esercitazione: Proteggere la posta elettronica di Exchange Online nei dispositivi gestiti](../tutorial-protect-email-on-enrolled-devices.md)