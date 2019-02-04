---
title: Impostazioni di aggiornamento e modalità S di Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni e delle loro funzioni durante l'aggiornamento di un'edizione di Windows 10 in un dispositivo oppure abilitare la modalità S in un dispositivo tramite un profilo di configurazione del dispositivo in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2a7d7ab1603300119f28596e81ae49cbbcbf550
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832307"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Impostazioni dei dispositivi Windows 10 e versioni successive per l'aggiornamento dell'edizione o per l'abilitazione della modalità S in Intune

Microsoft Intune include diverse impostazioni utili per la gestione e la protezione dei dispositivi. Questo articolo elenca e descrive le impostazioni per l'aggiornamento dell'edizione o per l'abilitazione della modalità S nei dispositivi Windows 10. Queste impostazioni vengono create in un profilo di configurazione dell'aggiornamento in Intune di cui viene eseguito il push o la distribuzione nei dispositivi.

Nell'ambito della soluzione di gestione di dispositivi mobili (MDM, Mobile Device Management) in uso, usare queste impostazioni per controllare le opzioni relative all'edizione e alla modalità S per i dispositivi Windows 10.

Per altre informazioni su questa funzionalità, vedere [Aggiornare le edizioni di Windows 10 o abilitare la modalità S](edition-upgrade-configure-windows-10.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare il profilo](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>Aggiornamento dell'edizione

- **Edizione a cui eseguire l'aggiornamento**: selezionare l'edizione Windows 10 a cui eseguire l'aggiornamento. I dispositivi a cui è destinato questo criterio vengono aggiornati all'edizione che scelta.
- **Codice Product Key**: immettere il codice Product Key ricevuto da Microsoft. Dopo aver creato il criterio con il codice Product Key, la chiave non può essere aggiornata e viene nascosta per motivi di sicurezza. Per modificare il codice Product Key, immettere nuovamente l'intero codice.
- **File di licenza**: per l'edizione **Windows 10 Holographic for Business** o **Windows 10 Mobile**, scegliere **Sfoglia** per selezionare il file di licenza ricevuto da Microsoft. Il file di licenza include le informazioni di licenza delle edizioni a cui si stanno aggiornando i dispositivi.

## <a name="mode-switch"></a>Cambio di modalità

- **Nessuna configurazione**: un dispositivo in modalità S rimane in modalità S. Un utente finale può disattivare la modalità S sul dispositivo.
- **Mantieni in modalità S**: impedisce all'utente finale di disattivare la modalità S nel dispositivo.
- **Switch** (Cambia): disattiva la modalità S nel dispositivo.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma potrebbe non essere ancora operativo. Assicurarsi di [assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di aggiornamento dell'edizione per dispositivi [Windows Holographic for Business](holographic-upgrade.md).