---
title: Abilitare la regola di protezione del dispositivo | Microsoft Docs
description: "Abilitare la regola di protezione dalle minacce per i dispositivi mobili nei criteri di conformità del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f05e516723976dcf6862475dbb78f9dce2913be
ms.openlocfilehash: 08edca426901eda3017bf17dda3b330dd186ce58


---

# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune con la protezione dalle minacce per i dispositivi mobili Lookout consente di rilevare le minacce nei dispositivi mobili e valutare i rischi in tali dispositivi. È possibile creare una regola dei criteri di conformità con la valutazione dei rischi per determinare se il dispositivo è conforme. Si possono quindi usare i criteri di accesso condizionale per bloccare l'accesso ai servizi in base alla conformità del dispositivo.

Prerequisiti per i criteri di conformità con la protezione dalle minacce per il dispositivo di Lookout:

- [Configurare la sottoscrizione per la protezione dalle minacce per il dispositivo di Lookout](set-up-your-subscription-with-lookout-mtp.md)
- [Abilitare la connessione a Lookout in Intune](enable-lookout-mtp-connection-in-intune.md)
- [Configurare l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)

Nell'ambito della configurazione della protezione dalle minacce per il dispositivo di Lookout, nella [console di Lookout](https://aad.lookout.com) è stato creato un criterio per la classificazione delle varie minacce in base ai livelli alto, medio e basso. Nei criteri di conformità di Intune si imposterà il livello di minaccia massimo consentito.

1. Nella [console di amministrazione di Intune](https://manage.microsoft.com) passare alla pagina **Criteri di conformità**. È possibile usare criteri di conformità esistenti o crearne di nuovi. Passare a **Integrità del dispositivo** e abilitare **Protezione dalle minacce per il dispositivo**.
  ![screenshot che mostra l'impostazione della regola di protezione dalle minacce per il dispositivo](../media/mtp/mtp-compliance-policy-rule.png)

2. Selezionare **Livello di minaccia massimo consentito**:
  * **Nessuno (protetto)**: questo è il livello più sicuro.  Nel dispositivo non possono essere presenti minacce per poter accedere alle risorse aziendali.  Se viene rilevata qualsiasi minaccia, il dispositivo viene valutato come non conforme.  
  * **Basso**: il dispositivo è conforme se sono presenti solo minacce di livello basso. In presenza di minacce di livello superiore, il dispositivo verrà messo in stato di non conformità.
  * **Medio**: il dispositivo è conforme se le minacce presenti nel dispositivo sono di livello basso o medio. Se viene rilevata la presenza di minacce di livello alto, il dispositivo viene determinato come non conforme.
  * **Alta**: questo è il livello meno sicuro. Con questa impostazione sono consentiti tutti i livelli di minacce e la protezione dalle minacce del dispositivo di Lookout viene usata solo a scopi di report.

![screenshot che mostra l'opzione del livello di minaccia per l'impostazione della regola di protezione dalle minacce per il dispositivo](../media/mtp/mtp-compliance-policy-setting.png)

Se si creano criteri di accesso condizionale per Office 365 e altri servizi, questa valutazione di conformità viene considerata e per i dispositivi non conformi viene bloccato l'accesso a questi servizi fino alla risoluzione della condizione di minaccia.

## <a name="monitor-device-threats"></a>Monitorare le minacce per i dispositivi
Per visualizzare lo stato di conformità di un dispositivo, passare alla [console di amministrazione di Intune](https://manage.microsoft.com) e visualizzare **Tutti i dispositivi**.

![screenshot della pagina dei dispositivi nella console di amministrazione Intune che mostra lo stato di conformità di un dispositivo](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>Passaggi successivi
* Creare criteri di accesso condizionale
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange locale](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Jan17_HO4-->

