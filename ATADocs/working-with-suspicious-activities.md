---
title: "處理 Advanced Threat Analytics 中的可疑活動 | Microsoft Docs"
description: "描述如何檢閱 ATA 所識別的可疑活動"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: advanced-threat-analytics
ms.technology: 
ms.assetid: 44d7c899-816c-4f7f-91d3-84a09d291a24
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: 1ff15a323f461cf8436e1ff7e15738a49bf3973c
ms.sourcegitcommit: 470675730967e0c36ebc90fc399baa64e7901f6b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2017
---
適用於︰Advanced Threat Analytics 1.8 版



<a id="working-with-suspicious-activities" class="xliff"></a>

# 處理可疑活動
本主題說明如何使用 Advanced Threat Analytics 的基本概念。

<a id="review-suspicious-activities-on-the-attack-time-line" class="xliff"></a>

## 在攻擊時間表上檢閱可疑活動
登入 ATA 主控台之後，您會自動進入開啟的**可疑活動時間表**。 可疑活動會依時間順序列出，最新的可疑活動位於時間表頂端。
每個可疑活動都有下列資訊︰

-   涉及的實體，包括使用者、電腦、伺服器、網域控制站以及資源。

-   可疑活動的時間和時間範圍。

-   可疑活動的嚴重性，高級、中級或低級。

-   狀態︰[開啟]、[已關閉] 或 [已隱藏]。

-   能力

    -   透過電子郵件與組織中的其他人員分享可疑的活動。

    -   將可疑活動匯出至 Excel。

    -   新增可疑活動的注意事項。

    -   提供可疑活動的輸入。

-   提供如何回應可疑活動的建議。

> [!NOTE]
> -   當滑鼠停留在使用者或電腦上時，會顯示實體小型設定檔，提供實體的其他相關資訊，並包含實體連結的可疑活動數目。
> -   如果您按一下實體，它會帶您到使用者或電腦的實體設定檔。

![ATA 可疑活動時間表影像](media/ATA-Suspicious-Activity-Timeline.JPG)

<a id="filter-suspicious-activities-list" class="xliff"></a>

## 篩選可疑活動清單
篩選可疑活動清單：

1.  在畫面左側的 [篩選依據] 窗格中，選取下列其中一個項目︰[所有]、[開啟的]、[已解析] 或 [已關閉]。

2.  若要進一步篩選清單，請選取 [高級]、[中級] 或 [低級]。

**可疑活動嚴重性**

-   **低**

    表示可能會導致攻擊的可疑活動，這些攻擊專為惡意使用者或軟體設計來存取組織的資料。

-   **中**

    表示可能會讓特定身分識別處於更嚴重攻擊之風險中的可疑活動，這些攻擊可能會導致身分識別盜用或特殊權限的提升

-   **高**

    表示可能會導致身分識別盜用、權限提升或其他高影響攻擊的可疑活動




<a id="remediating-suspicious-activities" class="xliff"></a>

## 修復可疑活動
您可以按一下可疑活動的目前狀態，然後選取下列的其中一項來變更可疑活動的狀態：[開啟]、[已隱藏]、[已關閉] 或 [已刪除]。
若要這樣做，請按一下特定可疑活動右上角的三個點，以顯示可用動作清單。

![可疑活動的 ATA 動作](./media/sa-actions.png)

**可疑活動狀態**

-   **開啟**：所有新的可疑活動都出現在此清單中。

-   **關閉**：用於追蹤您已識別、研究與修正以緩解的可疑活動。

    > [!NOTE]
    > 如果在短時間內偵測到相同的活動，ATA 可能會重新開啟已經解析的活動。

-   **隱藏**：隱藏活動表示您想要暫時將它忽略，只有出現新的執行個體時才會再次收到警示。 這表示如果有類似的警示，ATA 不會將它重新開啟。 但如果此警示停止 7 天，然後再次出現，您將會再次收到警示。

- **刪除**：如果您刪除警示，則會將它從系統和資料庫中刪除，而且您將「無法」予以還原。 按一下 [刪除] 之後，您將可以刪除相同類型的所有可疑活動。

- **排除**：排除實體使其不會引發更多特定警示類型的功能。 例如，您可以將 ATA 設定為排除特定實體 (使用者或電腦)，使其不會再引發特定類型的可疑活動警示，例如執行遠端程式碼的特定系統管理員，或執行 DNS 探查的安全性掃描程式。 除了能夠直接在可疑活動上新增排除項目之外 (因為已在時間表中偵測到此活動)，您也可以移至 [設定] 頁面，再移至 [排除]，而且針對每個可疑活動，您可以手動新增及移除排除的實體或子網路 (例如針對傳遞票證)。 
> [!NOTE]
> 只有 ATA 系統管理員才能修改設定頁面。


<a id="see-also" class="xliff"></a>

## 另請參閱
- [查看 ATA 論壇！](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [使用 ATA 偵測設定](working-with-detection-settings.md)
- [修改 ATA 組態](modifying-ata-center-configuration.md)