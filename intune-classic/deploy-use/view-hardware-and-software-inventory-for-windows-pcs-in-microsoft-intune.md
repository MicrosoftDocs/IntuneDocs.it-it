---
title: Visualizzare l&quot;inventario software e hardware per PC Windows | Documentazione Microsoft
description: Come visualizzare informazioni sull&quot;hardware e il software di desktop Windows gestiti come PC con il client software di Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: be6089e4a45aa906e458ad114c45b10bce4b9405
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Visualizzare l'inventario software e hardware per PC Windows

Intune raccoglie informazioni dettagliate sull'hardware e sul software dei desktop gestiti come PC con il client software di Intune. Le informazioni delle seguenti procedure consentono di:

-   Creare un report che riporta informazioni sulle funzionalità hardware dei PC gestiti.

-   Creare un report che elenca il software installato in ogni PC.

-   Aggiornare un inventario di PC per garantire che i dati nel report siano correnti.

## <a name="to-display-information-about-pcs-you-manage"></a>Per visualizzare informazioni sui PC gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Report** &gt; **Report inventario computer**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo i PC che eseguono Windows 8.1.

3.  Fare clic su **Visualizza rapporto** per aprire il **Report inventario computer** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Tipo di chassis** o **Produttore** selezionando l'intestazione della colonna.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Per visualizzare il software installato nei PC gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Report** &gt; **Report software rilevato**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo il software pubblicato da Microsoft.

3.  Scegliere **Visualizza rapporto** per aprire il **Report software rilevato** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Autore** o **Categoria** selezionando ogni intestazione di colonna. È possibile espandere gli aggiornamenti nell'elenco per visualizzare maggiori dettagli, ad esempio i PC in cui sono installati gli aggiornamenti, scegliendo la freccia direzionale accanto alla voce dell'elenco.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Per aggiornare l'inventario dei computer per accertarsi che sia aggiornato

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il PC di cui si vuole aggiornare l'inventario.

2.  Selezionare un PC oppure tenere premuto **CTRL** per selezionare più PC.

3.  Sulla barra delle applicazioni scegliere **Attività remote** &gt; **Aggiorna inventario**.

4.  Per visualizzare lo stato dell'attività, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della pagina.

    Nella finestra di dialogo **Stato attività** sono elencate le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati, nonché un collegamento per consultare le informazioni sulla risoluzione dei problemi.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)