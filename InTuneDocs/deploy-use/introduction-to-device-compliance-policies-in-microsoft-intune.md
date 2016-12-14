---
title: "Criteri di conformità dei dispositivi | Microsoft Intune"
description: "Questo argomento spiega cosa sono e come funzionano i criteri di conformità del dispositivo."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: b41307f620284315e4c71b0d0292b229753876ad


---

# <a name="device-compliance-policies-in-microsoft-intune"></a>Criteri di conformità dei dispositivi in Microsoft Intune
## <a name="what-is-a-compliance-policy"></a>Cos'è un criterio di conformità?
Per proteggere i dati aziendali, è necessario assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali rispettino alcune regole, come l'uso di un PIN per l'accesso ai dispositivi e la crittografia dei dati archiviati nei dispositivi. Un set di regole di questo tipo è detto criterio di conformità.

## <a name="how-should-i-use-compliance-policies"></a>Come usare i criteri di conformità
È possibile usare i criteri di conformità con i criteri di accesso condizionale per consentire l'accesso soltanto ai dispositivi che soddisfano le regole dei criteri di conformità per l'accesso alla posta elettronica e ad altri servizi. Per informazioni su come usare insieme i due tipi di criteri, vedere l'articolo [Limitare l'accesso alla posta elettronica e ai servizi di Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

È anche possibile usare i criteri di conformità indipendentemente dall'accesso condizionale. In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Ad esempio può risultare utile segnalare il numero di dispositivi non crittografati o i dispositivi jailbroken o rooted. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente.
Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere [Gestire impostazioni e funzionalità nei dispositivi](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies).

La tabella seguente elenca i tipi di dispositivi supportati dai criteri di conformità. La tabella descrive anche il modo in cui le impostazioni di non conformità vengono gestite quando i criteri di conformità vengono usati con i criteri di accesso condizionale.

-----------------------------

|Impostazione criterio| Windows 8.1 e versioni successive| Windows Phone 8.1 e versioni successive| iOS 8.0 e versioni successive|Android 4.0 e versioni successive<br/>Samsung KNOX Standard 4.0 e versioni successive|
|-----|----|----|----|----|
|**Configurazione di PIN o password** |Corretto|Corretto|Corretto|In quarantena|
|**Crittografia dispositivo**|Non applicabile|Corretto|Corretto (impostando il PIN)|In quarantena|
|**Dispositivo jailbroken o rooted**|Non applicabile|Non applicabile|In quarantena (non è un'impostazione)|In quarantena (non è un'impostazione)|
|**Profilo di posta elettronica**|Non applicabile|Non applicabile|In quarantena|Non applicabile|
|**Versione minima del sistema operativo**|In quarantena|In quarantena|In quarantena|In quarantena|
|**Versione massima del sistema operativo**|In quarantena|In quarantena|In quarantena|In quarantena|
|**Attestazione dell'integrità di Windows**|In quarantena: Windows 10 e Windows 10 Mobile<br /><br />Non applicabile: Windows 8.1|Non applicabile|Non applicabile|Non applicabile|

------------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. (Ad esempio, l'utente è obbligato a impostare un PIN.)

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

-   Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.

-   Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di conformità dei dispositivi](create-a-device-compliance-policy-in-microsoft-intune.md)

[Distribuire e monitorare i criteri di conformità dei dispositivi](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Vedere anche
[Limitare l'accesso alla posta elettronica e ai servizi di Office 365](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

