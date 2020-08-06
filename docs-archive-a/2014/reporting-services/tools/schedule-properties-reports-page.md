---
title: 일정 속성(보고서 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da0b5255e73522572fa22da8668329a28f108104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649359"
---
# <a name="schedule-properties-reports-page"></a><span data-ttu-id="8fe9c-102">일정 속성(보고서 페이지)</span><span class="sxs-lookup"><span data-stu-id="8fe9c-102">Schedule Properties (Reports Page)</span></span>
  <span data-ttu-id="8fe9c-103">이 페이지를 사용하여 이 공유 일정을 사용하는 모든 보고서 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-103">Use this page to view a list of all reports that use this shared schedule.</span></span> <span data-ttu-id="8fe9c-104">일정을 사용하여 보고서 스냅샷을 새로 고치거나, 보고서 기록을 생성하거나, 구독을 트리거하거나, 보고서의 캐시된 복사본을 만료시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-104">Schedules can be used to refresh report snapshots, generate report history, trigger a subscription, or expire a cached copy of the report.</span></span> <span data-ttu-id="8fe9c-105">일정 사용 방법을 확인하려면 보고서의 속성 및 구독 정보를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-105">To find out how the schedule is used, view the property and subscription information of the report.</span></span>  
  
 <span data-ttu-id="8fe9c-106">이 페이지는 공유 일정을 사용하는 각 보고서를 표시하지만 단일 보고서 내에서 공유 일정이 사용된 횟수는 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-106">Although this page shows each report that uses the shared schedule, it does not indicate how many times the shared schedule is used within that single report.</span></span> <span data-ttu-id="8fe9c-107">예를 들어 Company Sales 보고서에 대한 20명의 구독자가 모두 동일한 공유 일정을 사용하여 구독 처리를 트리거한다고 가정해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-107">For example, suppose 20 different subscribers to the Company Sales report all use the same shared schedule to trigger subscription processing.</span></span> <span data-ttu-id="8fe9c-108">이 경우 Company Sales 보고서에는 20개의 공유 일정에 대한 참조가 있지만 보고서는 이 목록에 한 번만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-108">In this case, the Company Sales report will only appear once in this list, even though the report has 20 references to the shared schedule.</span></span>  
  
 <span data-ttu-id="8fe9c-109">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버에 연결한 다음 **공유 일정** 폴더를 열고 공유 일정을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 후 **보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-109">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, select **Properties**, and then click **Reports**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fe9c-110">이 기능은 일부 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-110">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8fe9c-111">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [SQL Server 2012 버전에서 지 원하는 기능](https://go.microsoft.com/fwlink/?linkid=232473) 을 참조 하세요 https://go.microsoft.com/fwlink/?linkid=232473) .</span><span class="sxs-lookup"><span data-stu-id="8fe9c-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8fe9c-112">옵션</span><span class="sxs-lookup"><span data-stu-id="8fe9c-112">Options</span></span>  
 <span data-ttu-id="8fe9c-113">**폴더**</span><span class="sxs-lookup"><span data-stu-id="8fe9c-113">**Folder**</span></span>  
 <span data-ttu-id="8fe9c-114">보고서의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-114">Specifies the path of the report.</span></span>  
  
 <span data-ttu-id="8fe9c-115">**Report**</span><span class="sxs-lookup"><span data-stu-id="8fe9c-115">**Report**</span></span>  
 <span data-ttu-id="8fe9c-116">일정을 사용하는 보고서의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-116">Specifies the name of the report that uses the schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe9c-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8fe9c-117">See Also</span></span>  
 <span data-ttu-id="8fe9c-118">[일정 만들기, 수정 및 삭제](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="8fe9c-118">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="8fe9c-119">[일정](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="8fe9c-119">[Schedules](../subscriptions/schedules.md) </span></span>  
 <span data-ttu-id="8fe9c-120">[Management Studio F1 도움말의 보고서 서버](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="8fe9c-120">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="8fe9c-121">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="8fe9c-121">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="8fe9c-122">보고서 &#40;보고서 관리자의 일반 속성 구성&#41;</span><span class="sxs-lookup"><span data-stu-id="8fe9c-122">Configure General Properties for a Report &#40;Report Manager&#41;</span></span>](../configure-general-properties-for-a-report-report-manager.md)  
  
  
