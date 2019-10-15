---
title: Attivare la modalità di supervisione di iOS con Microsoft Intune
titleSuffix: ''
description: Informazioni su come attivare la modalità di supervisione di iOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 79e6ba1541a516b36ae4bd02cf9f60f1a12c8896
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728442"
---
# <a name="turn-on-ios-supervised-mode"></a>Attivare la modalità di supervisione di iOS


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La modalità di supervisione di Apple iOS offre agli amministrazioni più opzioni per la gestione dei dispositivi Apple ed è utile per i dispositivi di proprietà dell'azienda distribuiti su vasta scala. Ad esempio, è possibile limitare AirDrop o impedire agli utenti di modificare il nome del dispositivo. Per un elenco di impostazioni che richiedono la modalità di supervisione, vedere [Impostazioni relative alle restrizioni dei dispositivi iOS in Microsoft Intune](../configuration/device-restrictions-ios.md).

Intune supporta la modalità di supervisione nell'ambito del programma [Device Enrollment Program (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) di Apple.

Per un elenco di controlli Apple che richiedono la supervisione, vedere le [informazioni di riferimento sulle impostazioni del payload](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) di Apple.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Attivare la modalità di supervisione durante la registrazione

In Intune è possibile attivare la modalità di supervisione per i dispositivi quando [si crea un profilo di registrazione Apple nel programma DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). In **Impostazioni di gestione dei dispositivi** selezionare la casella **Supervisione eseguita**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Attivare la modalità di supervisione dopo la registrazione

Dopo la registrazione, l'unico modo per attivare la modalità di supervisione è connettere un dispositivo iOS a un computer Mac e [usare Apple Configurator](../enrollment/apple-configurator-enroll-ios.md) (che reimposta il dispositivo). Non è possibile configurare un dispositivo per la modalità di supervisione in Intune dopo la registrazione.

## <a name="identify-a-supervised-device"></a>Identificare un dispositivo supervisionato

Per determinare se un dispositivo è supervisionato, controllare la schermata di blocco o la pagina **Informazioni**:
- Sulla schermata di blocco del dispositivo verrà indicato **Questo iPhone è gestito da: "Nome società"** .
- Nella pagina **Informazioni** del dispositivo, verrà indicato **Questo iPhone è supervisionato. Nome società può monitorare il traffico Internet e localizzare questo dispositivo**.

## <a name="next-steps"></a>Passaggi successivi

Per altre opzioni di gestione dei dispositivi, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md)