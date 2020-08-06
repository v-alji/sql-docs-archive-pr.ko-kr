---
title: 보고서 기록 제한(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01318b1e1ccf0b0bf4512ab57de90cbf5ebc7365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730103"
---
# <a name="limit-report-history-report-manager"></a><span data-ttu-id="9cc1f-102">보고서 기록 제한(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="9cc1f-102">Limit Report History (Report Manager)</span></span>
  <span data-ttu-id="9cc1f-103">보고서 기록은 시간에 따라 만든 보고서 스냅샷의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-103">Report history is a collection of report snapshots that you create over time.</span></span> <span data-ttu-id="9cc1f-104">요청 시 보고서 기록을 만들거나 스냅샷이 만들어져 보고서 기록에 추가되는 빈도를 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-104">You can create report history on demand, or schedule how often a snapshot is created and added to report history.</span></span>  
  
 <span data-ttu-id="9cc1f-105">보고서 기록은 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-105">Report history is stored in the report server database.</span></span> <span data-ttu-id="9cc1f-106">보고서 스냅샷에 많은 양의 데이터가 포함된 경우 데이터베이스 크기에 영향을 주는 스냅샷 보존이 최소화되도록 보고서 기록을 제한해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-106">If report snapshots contain a large amount of data, you might consider limiting report history to minimize the affect of snapshot retention on database size.</span></span>  
  
### <a name="to-configure-report-history-for-a-report-server"></a><span data-ttu-id="9cc1f-107">보고서 서버에 대한 보고서 기록을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9cc1f-107">To configure report history for a report server</span></span>  
  
1.  <span data-ttu-id="9cc1f-108">보고서 관리자의 일반 도구 모음에서 **사이트 설정** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-108">In Report Manager, click **Site Settings** on the global toolbar.</span></span>  
  
2.  <span data-ttu-id="9cc1f-109">모든 보고서 기록을 무제한 보관하려면 **보고서 기록에 스냅샷을 무제한으로 보관** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-109">Select **Keep an unlimited number of snapshots in report history** if you want to keep all report history indefinitely.</span></span> <span data-ttu-id="9cc1f-110">그렇지 않은 경우 **보고서 기록의 복사본 개수 제한** 을 선택하여 지정된 보고서에 대해 보관할 수 있는 스냅샷의 최대 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-110">Otherwise, select **Limit the copies of report history** to specify the maximum number of snapshots that can be kept for any given report.</span></span>  
  
3.  <span data-ttu-id="9cc1f-111">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-111">Click **Apply**.</span></span>  
  
### <a name="to-configure-report-history-for-a-specific-report"></a><span data-ttu-id="9cc1f-112">특정 보고서에 대한 보고서 기록을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="9cc1f-112">To configure report history for a specific report</span></span>  
  
1.  <span data-ttu-id="9cc1f-113">보고서 관리자에서 기록을 구성하려는 보고서로 이동한 후 보고서를 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-113">In Report Manager, navigate to the report for which you want to configure history, and then click the report to open it.</span></span>  
  
2.  <span data-ttu-id="9cc1f-114">**속성** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-114">Click the **Properties** tab.</span></span>  
  
3.  <span data-ttu-id="9cc1f-115">**기록** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-115">Click the **History** tab.</span></span>  
  
4.  <span data-ttu-id="9cc1f-116">보고서에 대한 옵션을 선택하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-116">Select the options for your report and click **Apply**.</span></span> <span data-ttu-id="9cc1f-117">각 옵션에 대한 자세한 내용은 [스냅샷 옵션 속성 페이지&#40;보고서 관리자&#41;](../snapshot-options-properties-page-report-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cc1f-117">For details about each option, see [Snapshot Options Properties Page &#40;Report Manager&#41;](../snapshot-options-properties-page-report-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc1f-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9cc1f-118">See Also</span></span>  
 <span data-ttu-id="9cc1f-119">[보고서 기록에 스냅숏을 추가 &#40;보고서 관리자&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="9cc1f-119">[Add a Snapshot to Report History &#40;Report Manager&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md) </span></span>  
 [<span data-ttu-id="9cc1f-120">보고서 관리자&#40;SSRS 기본 모드&#41;</span><span class="sxs-lookup"><span data-stu-id="9cc1f-120">Report Manager  &#40;SSRS Native Mode&#41;</span></span>](../report-manager-ssrs-native-mode.md)  
  
  
