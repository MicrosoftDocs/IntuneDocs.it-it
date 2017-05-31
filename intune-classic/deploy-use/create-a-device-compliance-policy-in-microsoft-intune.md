---
title: "Creare criteri di conformità dei dispositivi | Documentazione Microsoft"
description: "Creare criteri di conformità per consentire ai dispositivi mobili e ai PC in uso di accedere ai dati della società."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 018fc2ff3b5609d3cc5f130db548f1dd3c839020
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Creare criteri di conformità dei dispositivi in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

In questo argomento sono illustrati i passaggi per creare criteri di conformità che un dispositivo deve osservare per essere considerato conforme.

##  <a name="step-1-add-a-new-policy"></a>Passaggio 1: Aggiungere nuovi criteri
  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Criteri di conformità** &gt; **Aggiungi**.

  ![Schermata della pagina dei criteri di conformità nella console di amministrazione di Intune, con l'opzione Aggiungi visualizzata nel menu in alto nella pagina](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>Passaggio 2: Configurare le impostazioni
Nella pagina **Crea criterio** abilitare le impostazioni richieste:
  -   Impostazioni di protezione del sistema, come la password e la crittografia.
  -   Impostazioni di integrità del dispositivo, ad esempio se il dispositivo è jailbroken oppure se viene segnalato come integro dal servizio di attestazione dell'integrità di Windows.
  -   Impostazioni delle proprietà del dispositivo, come la versione minima del sistema operativo richiesta o la versione massima del sistema operativo consentita.
![Scheda Generale della pagina Crea criterio ](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>Passaggio 3: Salvare i criteri
Al termine, scegliere **Salva criterio**.

È possibile scegliere di distribuire i criteri subito dopo il salvataggio o in un secondo momento. Il nuovo criterio viene visualizzato nel nodo **Criteri di conformità** dell'area di lavoro **Criteri**.

##  <a name="step-4-set-the-compliance-status-validity-period"></a>Passaggio 4: Impostare il periodo di validità dello stato di conformità
Per specificare l'intervallo di tempo in cui il dispositivo deve eseguire l'archiviazione prima di essere considerato non conforme, passare alle impostazioni dei criteri di conformità e aggiornare l'intervallo. Per impostazione predefinita, questo intervallo è impostato su 30 giorni.

![Opzione delle impostazioni dei criteri di conformità nella barra dei menu dei criteri](../media/mdm-compliance-policy-settings.png)

![Finestra di dialogo dei criteri di conformità](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>Impostazioni dei criteri supportate
La tabella seguente include le impostazioni dei criteri di conformità e le piattaforme nelle quali sono supportate.

-------------
|Impostazioni|iOS|Android|Windows|
|-----|----|-----|-----|
|Richiedi una password per sbloccare i dispositivi mobili|iOS 6 e versioni successive|Android 4.0 e versioni successive <br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive|
|Consenti password semplici|iOS 6 e versioni successive|Non supportato|Windows Phone 8.1 e versioni successive|
|Lunghezza minima password|iOS 6 e versioni successive| Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive| Windows Phone 8.1 e versioni successive<br>Windows 8.1|
|Tipo di password richiesto|iOS 6 e versioni successive|Non disponibile|Windows Phone 8.1 e versioni successive <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Numero minimo di set di caratteri|iOS 6 e versioni successive|Non disponibile|Windows Phone 8.1 e versioni successive <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|Qualità password|Non disponibile|Android 4.0 e versioni successive <br>Samsung KNOX Standard 4.0 e versioni successive|Non disponibile|
|Minuti di inattività prima che venga richiesta la password|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Scadenza password (giorni)|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Ricorda cronologia password|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Impedisci riutilizzo delle password precedenti|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br>Windows RT e Windows RT 8.1<br>Windows 8.1|
|Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività| Non disponibile| Non disponibile|Windows 10 Mobile|
|Richiedi crittografia sui dispositivi mobili|Non applicabile|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br> Windows 8.1|
|Richiedi che i dispositivi siano riportati come integri| Non disponibile| Non disponibile|Windows <br>Windows 10 Mobile|
|Il dispositivo non deve essere jailbroken o rooted|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Non disponibile|
|L'account di posta elettronica deve essere gestito da Intune|iOS 6 e versioni successive|Non disponibile| Non disponibile|
|Selezionare il profilo di posta elettronica che deve essere gestito da Intune|iOS 6 e versioni successive|Non disponibile| Non disponibile|
|Versione minima richiesta del sistema operativo|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive| Windows Phone 8.1 e versioni successive<br>Windows 8.1|
|Versione massima consentita del sistema operativo|iOS 6 e versioni successive|Android 4.0 e versioni successive<br>Samsung KNOX Standard 4.0 e versioni successive|Windows Phone 8.1 e versioni successive<br>Windows 8.1|

Per altre informazioni sulle impostazioni di conformità supportate in ogni piattaforma, selezionare una delle seguenti voci:
> [!div class="op_single_selector"]
- [Impostazioni dei criteri di conformità per i dispositivi iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per i dispositivi Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Impostazioni dei criteri di conformità per Windows e Windows Phone ](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>Passaggi successivi
[Distribuire e monitorare criteri di conformità](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Vedere anche
[Introduzione ai criteri di conformità dei dispositivi](introduction-to-device-compliance-policies-in-microsoft-intune.md)
