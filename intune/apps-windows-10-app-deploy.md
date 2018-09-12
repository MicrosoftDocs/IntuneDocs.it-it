---
title: Distribuzione di app di Windows 10 con Microsoft Intune
titlesuffix: ''
description: Informazioni sugli scenari di app di Windows 10 disponibili con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abebfb5e-054b-435a-903d-d1c31767bcf2
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7508f2c2eca06ceacf203103ab2cad53abc39a65
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347433"
---
# <a name="windows-10-app-deployment-using-microsoft-intune"></a>Distribuzione di app di Windows 10 con Microsoft Intune 

Microsoft Intune attualmente supporta un'ampia gamma di tipi di app e scenari di distribuzione nei dispositivi Windows 10. Dopo avere aggiunto un'app a Intune, è possibile assegnarla a utenti e dispositivi. Le informazioni seguenti forniscono ulteriori dettagli sugli scenari di Windows 10 supportati. Le informazioni seguenti, inoltre, forniscono i dettagli chiave da tenere presenti durante la distribuzione delle app in Windows. 

Le app line-of-business e Microsoft Store per le aziende sono i tipi di app che supportano i dispositivi Windows 10.

> [!Note]
> L'aggiornamento di Windows 10 minimo necessario per distribuire le app nel contesto di dispositivo è [23 maggio 2018: KB4100403 (build del sistema operativo 17134.81)](https://support.microsoft.com/en-us/help/4100403/windows-10-update-kb4100403).

## <a name="windows-10-line-of-business-apps"></a>App line-of-business per Windows 10

Le app line-of-business per Windows 10 sono firmate e caricate nella console di amministrazione di Intune e possono essere sia app moderne, ad esempio app per la piattaforma UWP (Universal Windows Platform) e pacchetti applicazione di Windows (AppX), sia app per Win 32, ad esempio semplici file di pacchetti di Microsoft Installer (MSI). Gli aggiornamenti delle app line-of-business devono essere caricati e distribuiti ogni volta manualmente dall'amministratore. Gli aggiornamenti distribuiti vengono installati automaticamente nei dispositivi degli utenti finali che hanno installato l'app senza richiedere l'intervento dell'utente. L'utente non ha alcun controllo sugli aggiornamenti. 

## <a name="microsoft-store-for-business-apps"></a>App di Microsoft Store per le aziende

Le app di Microsoft Store per le aziende sono app moderne acquistate nel portale di amministrazione Microsoft Store per le aziende e quindi sincronizzate in Microsoft Intune per la gestione. Tali app possono essere con **licenza online** oppure **licenza offline**. Gli aggiornamenti delle app di Microsoft Store per le aziende vengono gestiti direttamente dal Microsoft Store, senza richiedere alcun intervento aggiuntivo da parte dell'amministratore. L'amministratore può inoltre impedire l'aggiornamento di app specifiche usando un URI (Uniform Resource Identifier) personalizzato. Per altre informazioni, vedere [Enterprise app management - Prevent app from automatic updates](https://docs.microsoft.com/windows/client-management/mdm/enterprise-app-management#prevent-app-from-automatic-updates) (Gestione delle app aziendali - Impedire gli aggiornamenti automatici delle app). Nel dispositivo l'utente finale può anche disabilitare gli aggiornamenti per tutte le app di Microsoft Store per le aziende presenti nel dispositivo. 

## <a name="installing-apps-on-windows-10-devices"></a>Installare le app nei dispositivi Windows 10
A seconda del tipo di app, l'app può essere installata in un dispositivo Windows 10 in uno dei due modi seguenti:

- **Contesto utente**: quando un'app viene distribuita nel contesto utente, l'app gestita verrà installata per l'utente nel dispositivo nel momento in cui l'utente accede al dispositivo. Si noti che l'installazione dell'app non verrà completata fintanto che l'utente non accede al dispositivo. 
    - Possono essere distribuite nel contesto utente sia le app line-of-business moderne che le app di Microsoft Store per le aziende, sia online che offline, e queste supporteranno sia la finalità obbligatoria che la finalità disponibile.
- **Contesto di dispositivo**: quando un'app viene distribuita nel contesto di dispositivo, l'app gestita verrà installata direttamente nel dispositivo da Intune.
    - Solo le app line-of-business moderne e le app di Microsoft Store per le aziende con licenza online possono essere distribuite nel contesto di dispositivo e supporteranno solo la finalità obbligatoria.

> [!Note]
> La distribuzione di MSI su MDM nel contesto di dispositivo non è ancora supportata nei dispositivi Windows 10.

Quando un'app viene distribuita nel contesto di dispositivo, l'installazione verrà completata solo se il dispositivo di destinazione supporta il contesto di dispositivo. Inoltre, la distribuzione nel contesto di dispositivo comporta le condizioni seguenti:
- Se un'app viene distribuita nel contesto di dispositivo e fa riferimento a un utente, l'installazione avrà esito negativo e nella console di amministrazione verranno visualizzati l'errore e lo stato seguenti:
    - Stato: Non riuscito.
    - Errore: Un utente non può essere incluso con un'installazione del contesto di dispositivo.
- Se un'app viene distribuita nel contesto di dispositivo ma fa riferimento a un dispositivo che non supporta il contesto di dispositivo, l'installazione avrà esito negativo e nella console di amministrazione verranno visualizzati l'errore e lo stato seguenti:
    - Stato: Non riuscito.
    - Errore: Questa piattaforma non supporta l'installazione del contesto di dispositivo. 

> [!Note]
> Dopo che l'assegnazione di un'app è stata salvata con una distribuzione specifica, il contesto non può essere modificato per tale assegnazione, fatta eccezione per le app moderne. Nel caso di app moderne, infatti, il contesto può essere modificato da contesto utente a contesto di dispositivo. 

Nel caso ci siano un conflitto di criteri per un utente/dispositivo, le priorità dei criteri che verranno utilizzate per determinare i criteri finali sono le seguenti:
- Un criterio di contesto di dispositivo ha priorità più alta rispetto a un criterio di contesto utente. 
- Un criterio di installazione ha priorità più alta rispetto a un criterio di disinstallazione.

Per altre informazioni sull'assegnazione delle app con Microsoft Intune, vedere [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md) e [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md). Per altre informazioni sui tipi di app in Intune, vedere [Aggiungere app in Microsoft Intune](apps-add.md).

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'assegnazione delle app ai gruppi, vedere [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).
- Per altre informazioni sul monitoraggio delle assegnazioni di app, vedere [Come monitorare le app](apps-monitor.md).