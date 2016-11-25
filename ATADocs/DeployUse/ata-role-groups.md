---
title: "使用角色群組 - 完整 | Microsoft ATA"
description: "逐步引導您使用 ATA 角色群組。"
keywords: 
author: rkarlin
manager: mbaldwin
ms.date: 09/20/2016
ms.topic: get-started-article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 3715b69e-e631-449b-9aed-144d0f9bcee7
ms.reviewer: bennyl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d47d9e7be294c68d764710c15c4bb78539e42f62
ms.openlocfilehash: 869d8f830d5dc70c927f172d77642b0c97bdcd84


---

*適用於︰Advanced Threat Analytics 1.7 版*




# ATA 角色群組

角色群組可以進行 ATA 的存取管理。 使用角色群組可以隔離安全性小組內的責任，並授與使用者執行工作所需的存取權。 本文說明存取管理和 ATA 角色授權，以及協助您在 ATA 中準備和執行角色群組。
## ATA 角色群組的類型 

ATA 引進了 3 種類型的角色群組︰ATA 管理員、ATA 分析員及 ATA 執行者。 下表描述 ATA 中每個角色可用的存取類型。 視您指派何種角色而定，ATA 中的各種畫面與功能表選項將無法使用，如下所示︰

|活動 |Microsoft Advanced Threat Analytics 管理員|Microsoft Advanced Threat Analytics 分析員|Microsoft Advanced Threat Analytics 執行者|
|----|----|----|----|
|登入|可用|可用|可用|
|提供可疑活動的輸入|可用|可用|無法使用|
|變更可疑活動的狀態|可用|可用|無法使用|
|透過電子郵件/取得連結共用/匯出可疑的活動|可用|可用|無法使用|
|新增/編輯可疑活動的附註|可用|可用|無法使用|
|變更監視警示的狀態|可用|可用|無法使用|
|更新 ATA 設定|可用|無法使用|無法使用|
|閘道 - 新增|可用|無法使用|無法使用|
|閘道 - 刪除 |可用|無法使用|無法使用|
|監視的 DC - 新增 |可用|無法使用|無法使用|
|監視的 DC - 刪除|可用|無法使用|無法使用|

當使用者嘗試存取不適用於其角色群組的頁面時，他們會被重新導向至 ATA 未授權的頁面。 

## 新增 \ 移除使用者 - ATA 角色群組 

ATA 使用本機的 Windows 群組做為角色群組的基礎。 若要新增或移除使用者，請使用 [本機使用者和群組] MMC (Lusrmgr.msc)。 您可以在加入網域的電腦上新增網域帳戶以及本機帳戶。 




<!--HONumber=Sep16_HO4-->

