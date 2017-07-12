---
title: "Advanced Threat Analytics 的災害復原 | Microsoft Docs"
description: "描述如何於災害發生後快速復原 ATA 功能"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/7/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 7620e171-76d5-4e3f-8b03-871678217a3a
ms.reviewer: arzinger
ms.suite: ems
ms.openlocfilehash: ce06038a3c3f2e5a6f2a5d57ad814ab8393c0b0c
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2017
---
適用於︰Advanced Threat Analytics 1.8 版



<a id="ata-disaster-recovery" class="xliff"></a>

# ATA 災害復原
本文描述如何在失去 ATA 中心功能，但 ATA 閘道仍可運作的情況下，快速復原 ATA 中心並還原 ATA 功能。 

>[!NOTE]
> 描述的程序並無法復原先前所偵測到的可疑活動，但可以使 ATA 中心恢復完整功能。 除此之外，部分行為偵測的學習期間將會重新開始，但大部分由 ATA 所提供的偵測，在 ATA 中心還原之後便可以運作。 

<a id="back-up-your-ata-center-configuration" class="xliff"></a>

## 備份您的 ATA 中心設定

1. ATA 中心組態會於每小時備份為檔案。 找出最新的 ATA 中心組態備份複本，並將它儲存在另一部電腦上。 如需尋找這些檔案的完整解釋，請參閱[匯出和匯入 ATA 組態](/advanced-threat-analytics/deploy-use/ata-configuration-file)。 
2. 匯出 ATA 中心憑證。
    1. 在 [憑證管理員] 中，瀏覽到 [憑證 (本機電腦)]  ->  [個人]  -> [憑證]，然後選取 [ATA 中心]。
    2. 以滑鼠右鍵按一下 [ATA 中心]，然後選取 [所有工作]，並選取 [匯出]。 
     ![ATA 中心憑證](media/ata-center-cert.png)
    3. 依照指示匯出憑證，也請務必匯出私密金鑰。
    4. 將匯出的憑證檔案備份到另一部電腦上。

  > [!NOTE] 
  > 如果您無法匯出私密金鑰，您必須建立新憑證並將它部署至 ATA (如[變更 ATA 中心憑證](/advanced-threat-analytics/deploy-use/modifying-ata-config-centercert)中所述)，然後將它匯出。 

<a id="recover-your-ata-center" class="xliff"></a>

## 復原您的 ATA 中心

1. 使用和先前的 ATA 中心電腦相同的 IP 位址與電腦名稱，建立新的 Windows Server 電腦。
4. 將您在上面備份的憑證匯入到新的伺服器。
5. 依照指示[將 ATA 中心部署到](/advanced-threat-analytics/deploy-use/install-ata-step1)新建立的 Windows Server 上。 您不需要再次部署 ATA 閘道。 當系統提示您提供憑證時，請提供您在備份 ATA 中心設定時匯出的憑證。 
![ATA 中心還原](media/disaster-recovery-deploymentss.png)
6. 匯入已備份的 ATA 中心組態：
    1. 從 MongoDB 移除預設 ATA 中心系統設定檔文件： 
        1. 移至 **C:\Program Files\Microsoft Advanced Threat Analytics\Center\MongoDB\bin**。 
        2. 執行 `mongo.exe` 
        3. 執行此命令以移除預設系統設定檔：`db.SystemProfile.remove({})`
    2. 使用步驟 1 中的備份檔案執行命令：`mongoimport.exe --db ATA --collection SystemProfile --file "<SystemProfile.json backup file>" --upsert`。</br>
    如需尋找並匯入備份檔案的完整解釋，請參閱[匯出和匯入 ATA 組態](/advanced-threat-analytics/deploy-use/ata-configuration-file)。 
    3. 開啟 ATA 主控台。 您應該會在 [組態/閘道] 索引標籤下看見所有 ATA 閘道皆已連結。 
    5. 請務必定義[目錄服務使用者](/advanced-threat-analytics/deploy-use/install-ata-step2)並選擇[網域控制器同步器](/advanced-threat-analytics/deploy-use/install-ata-step5)。 






<a id="see-also" class="xliff"></a>

## 另請參閱
- [ATA 必要條件](/advanced-threat-analytics/plan-design/ata-prerequisites)
- [ATA 容量規劃](/advanced-threat-analytics/plan-design/ata-capacity-planning)
- [設定事件收集](/advanced-threat-analytics/deploy-use/configure-event-collection)
- [設定 Windows 事件轉送](/advanced-threat-analytics/deploy-use/configure-event-collection#configuring-windows-event-forwarding)
- [查看 ATA 論壇！](https://social.technet.microsoft.com/Forums/security/home?forum=mata)