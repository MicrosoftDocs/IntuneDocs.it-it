---
title: Limitare l&quot;accesso alla posta elettronica e ai servizi di Office 365 | Microsoft Intune
description: "Questo argomento descrive in che modo è possibile usare l&quot;accesso condizionale per consentire solo ai dispositivi conformi di accedere alla posta elettronica e ai dati aziendali in SharePoint Online e altri servizi."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 5665ca431eb186d4378953b7047228e07ae9dc60


---

# <a name="restrict-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Limitare l'accesso alla posta elettronica, a Office 365 e ad altri servizi con Microsoft Intune
È possibile limitare l'accesso alla posta elettronica aziendale, a Office 365 e ad altri servizi usando l'accesso condizionale di Intune. L'accesso condizionale di Intune assicura che l'accesso alla posta elettronica aziendale e ai servizi di Office 365 venga limitato ai dispositivi conformi alle regole definite.
## <a name="how-does-conditional-access-work"></a>Come funziona l'accesso condizionale?
È possibile usare le impostazioni dei criteri di conformità per valutare la conformità di un dispositivo. I criteri di accesso condizionale usano la versione di valutazione per limitare o consentire l'accesso a un servizio specifico. Quando i criteri di accesso condizionale vengono usati in combinazione con i criteri di conformità, possono accedere al servizio solo i dispositivi conformi. I criteri di conformità e di accesso condizionale vengono distribuiti all'utente. Di qualsiasi dispositivo usato dall'utente per accedere ai servizi viene verificata la conformità ai criteri.

Tenere presente che l'utente che usa il dispositivo deve disporre di criteri di conformità distribuiti, così da consentire la valutazione della conformità del dispositivo stesso.
Se all'utente non viene distribuito alcun criterio di conformità, il dispositivo viene considerato conforme e non vengono applicate restrizioni di accesso.

Se i dispositivi non soddisfano le condizioni definite nei criteri, l'utente finale viene guidato nel processo di registrazione del dispositivo e di risoluzione del problema che impedisce la conformità del dispositivo.

Un flusso di accesso condizionale tipico:

![Immagine che illustra gli aspetti tenuti in considerazione per determinare se a un dispositivo è consentito o meno l'accesso a un servizio](../media/ConditionalAccess4.png)

## <a name="how-to-configure-conditional-access"></a>Come configurare l'accesso condizionale
Usare l'accesso condizionale per gestire l'accesso a Microsoft **Exchange locale**, **Exchange Online**, **Exchange Online dedicato**, **SharePoint Online** e **Skype for Business Online**.

Per impostare l'accesso condizionale, configurare i criteri di conformità del dispositivo e i criteri di accesso condizionale.

I criteri di conformità includono impostazioni quali passcode e crittografia e la specifica se un dispositivo è jailbroken. Per poter essere considerato conforme, il dispositivo deve soddisfare le regole seguenti.

È possibile impostare criteri di accesso condizionale per limitare l'accesso in base a:
- Stato di conformità del dispositivo.
- Piattaforma in esecuzione nel dispositivo.
- Tipo di app usate per l'accesso ai servizi.

A differenza degli altri criteri di Intune, i criteri di accesso condizionale non vengono distribuiti. Dopo aver configurato i criteri e aver selezionato gli utenti che devono disporre di tali criteri, questi vengono applicati a tutti gli utenti destinatari. Per poter accedere alle risorse, un utente di destinazione di un criterio deve usare solo dispositivi conformi.


## <a name="next-steps"></a>Passaggi successivi
1. [Informazioni sui criteri di conformità del dispositivo e sul relativo funzionamento](introduction-to-device-compliance-policies-in-microsoft-intune.md).

2. [Creare i criteri di conformità](create-a-device-compliance-policy-in-microsoft-intune.md).

2.  Creare criteri di accesso condizionale per:
> [!div class="op_single_selector"]
  - [Creare criteri di accesso condizionale per Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per Exchange locale](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per il nuovo ambiente Exchange Online dedicato](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per l'ambiente legacy Exchange Online dedicato](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per Skype for Business Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Creare criteri di accesso condizionale per Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

