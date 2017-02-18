---
title: "Advanced Threat Analytics 的災害復原 | Microsoft Docs"
description: "描述如何於災害發生後快速復原 ATA 功能"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 02/12/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ffbbfd96507612b8ec44f232f4ece42988eb588
ms.openlocfilehash: 3bc9e48f1d8843aef40016a2c5a82f6c7510be3c


---

適用於︰Advanced Threat Analytics 1.7 版



# <a name="ata-disaster-recovery"></a>ATA 災害復原
本文描述如何在失去 ATA 中心功能，但 ATA 閘道仍可運作的情況下，快速復原 ATA 中心並還原 ATA 功能。 

>[!NOTE]
> 描述的程序並無法復原先前所偵測到的可疑活動，但可以使 ATA 中心恢復完整功能。 除此之外，部分行為偵測的學習期間將會重新開始，但大部分由 ATA 所提供的偵測，在 ATA 中心還原之後便可以運作。 

## <a name="how-to-recovery-your-ata-center-after-disaster"></a>如何在災害後復原您的 ATA 中心

1. ATA 中心組態會於每小時備份為檔案。 找出最新的 ATA 中心組態備份複本，並將它儲存在另一部電腦上。 如需尋找這些檔案的完整解釋，請參閱[匯出和匯入 ATA 組態](/advanced-threat-analytics/deploy-use/ata-configuration-file)。 
2. 匯出 ATA 中心憑證。
    1. 在 [憑證管理員] 中，瀏覽到 [憑證 (本機電腦)]  ->  [個人]  -> [憑證]，然後選取 [ATA 中心]。
    2. 以滑鼠右鍵按一下 [ATA 中心]，然後選取 [所有工作]，並選取 [匯出]。 
     ![ATA 中心憑證](media/ata-center-cert.png)
    3. 遵循指示以匯出憑證，也請務必匯出私密金鑰。

    > [!NOTE] 
    > 如果您無法匯出私密金鑰，您必須建立新憑證並將它部署至 ATA (如[變更 ATA 中心憑證](/advanced-threat-analytics/deploy-use/modifying-ata-config-centercert)中所述)，然後將它匯出。 

    4. 將匯出的憑證檔案備份到另一部電腦上。
3. 使用和先前的 ATA 中心電腦相同的 IP 位址和電腦名稱，建立新的 Windows Server 電腦。
4. 將您在步驟 2 中備份的憑證匯入到新的伺服器。
5. 遵循指示以[將 ATA 中心部署到](/advanced-threat-analytics/deploy-use/install-ata-step1)新建立的 Windows Server 上。 您不需要再次部署 ATA 閘道。 當您看見要求憑證的提示時，請提供步驟 2 中的憑證。 
![ATA 中心還原](media/ata-center-restore.png)
6. 匯入已備份的 ATA 中心組態：
    1. 從 MongoDB 移除預設 ATA 中心系統設定檔文件： 
        1. 請移至 **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**。 
        2. 執行 `mongo.exe` 
        3. 執行下列命令以移除預設系統設定檔：`db.SystemProfile.remove({})`
    2. 使用步驟 1 中的備份執行命令：`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`。</br>
    如需尋找並匯入備份檔案的完整解釋，請參閱[匯出和匯入 ATA 組態](/advanced-threat-analytics/deploy-use/ata-configuration-file)。 
    3. 匯入之後，請執行此命令以移除一部分的預設偵測器和分析工具 (以針對新環境重設它們)：`db.SystemProfile.remove({$or:[{"_t":"DetectorProfile"}, "_t":"DirectoryServicesSystemProfile"}]}) `
    4. 開啟 ATA 主控台。 您應該會在 [組態/閘道] 索引標籤下看見所有 ATA 閘道皆已連結。 
    5. 請務必定義「目錄服務使用者」並選擇「網域控制器同步器」。 






## <a name="see-also"></a>另請參閱
- [ATA 必要條件](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA 容量規劃](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [設定事件收集](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [設定 Windows 事件轉送](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [查看 ATA 論壇！](https://social.technet.microsoft.com/Forums/security/home?forum=mata)



<!--HONumber=Feb17_HO2-->

