---
title: 진행률 페이지 (AlwaysOn 가용성 그룹 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.progress.f1
- sql12.swb.newagwizard.progress.f1
- sql11.swb.failoverwizard.progress.f1
- sql11.swb.adddatabasewizard.progress.f1
- sql11.swb.addreplicawizard.progress.f1
- sql11.swb.newagwizard.progress.f1
- sql12.swb.adddatabasewizard.progress.f1
- sql12.swb.failoverwixard.progress.f1
ms.assetid: bd3b0306-8384-4120-a1c9-03825f0ae26a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7de8df6906d930215d71a0adc562bd7cef961ebb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740492"
---
# <a name="progress-page-alwayson-availability-group-wizards"></a><span data-ttu-id="25201-102">진행률 페이지(AlwaysOn 가용성 그룹 마법사)</span><span class="sxs-lookup"><span data-stu-id="25201-102">Progress Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="25201-103">이 대화 상자를 사용하여 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 실행 중인 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]마법사의 진행률을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25201-103">Use this dialog box to view the progress of a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard that you are running in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="25201-104">진행률 표시줄에는 마법사에서 수행 중인 단계의 상대적 진행률이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25201-104">The progress bar indicates the relative progress of the steps that the wizard is performing.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="25201-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="25201-105">UI element list</span></span>  
 <span data-ttu-id="25201-106">**자세한 정보**</span><span class="sxs-lookup"><span data-stu-id="25201-106">**More details**</span></span>  
 <span data-ttu-id="25201-107">아래쪽 화살표를 클릭하여 완료된 단계와 현재 진행 중인 작업을 순서대로 나열하는 진행률 표를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-107">Click the down arrow to display a progress grid that lists any completed steps, in order, followed by the current in-progress operation.</span></span> <span data-ttu-id="25201-108">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25201-108">The grid contains the following columns:</span></span>  
  
 <span data-ttu-id="25201-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="25201-109">**Name**</span></span>  
 <span data-ttu-id="25201-110">특정 단계를 설명하는 문구를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-110">Displays a phrase that describes a specific step.</span></span>  
  
 <span data-ttu-id="25201-111">**상태**</span><span class="sxs-lookup"><span data-stu-id="25201-111">**Status**</span></span>  
 <span data-ttu-id="25201-112">완료된 단계의 결과와 현재 단계의 완료 비율을 다음과 같이 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25201-112">Indicates the outcome of completed steps and the percentage of completion of the current step, as follows:</span></span>  
  
|<span data-ttu-id="25201-113">결과</span><span class="sxs-lookup"><span data-stu-id="25201-113">Result</span></span>|<span data-ttu-id="25201-114">Description</span><span class="sxs-lookup"><span data-stu-id="25201-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="25201-115">**오류**</span><span class="sxs-lookup"><span data-stu-id="25201-115">**Error**</span></span>|<span data-ttu-id="25201-116">이 단계의 작업에서 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25201-116">Indicates the operation for this step experienced an error.</span></span> <span data-ttu-id="25201-117">오류를 설명하는 메시지 대화 상자를 표시하려면 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-117">Click the link to display a message dialog box that describes the error.</span></span>|  
|<span data-ttu-id="25201-118">**진행 중(** ‘완료율’ **)** </span><span class="sxs-lookup"><span data-stu-id="25201-118">**In Progress (** *percentage-completed* **)**</span></span>|<span data-ttu-id="25201-119">작업이 지금 수행되고 있음을 나타내고 이 단계의 완료율을 추정합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-119">Indicates that the operation is occurring now and estimates the percentage of this step that has completed.</span></span>|  
|<span data-ttu-id="25201-120">**Success**</span><span class="sxs-lookup"><span data-stu-id="25201-120">**Success**</span></span>|<span data-ttu-id="25201-121">이 단계에서 완료된 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25201-121">Indicates the operation for this step completed successfully.</span></span>|  
  
 <span data-ttu-id="25201-122">**간략 정보**</span><span class="sxs-lookup"><span data-stu-id="25201-122">**Fewer Details**</span></span>  
 <span data-ttu-id="25201-123">진행률 표를 숨기려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-123">Click to hide the progress grid.</span></span>  
  
 <span data-ttu-id="25201-124">**취소**</span><span class="sxs-lookup"><span data-stu-id="25201-124">**Cancel**</span></span>  
 <span data-ttu-id="25201-125">나머지 작업을 건너뛰고 마법사를 종료하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="25201-125">Click to skip any remaining operations and then exit the wizard.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="25201-126">관련 작업</span><span class="sxs-lookup"><span data-stu-id="25201-126">Related Tasks</span></span>  
  
-   [<span data-ttu-id="25201-127">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="25201-127">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="25201-128">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="25201-128">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="25201-129">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="25201-129">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="25201-130">가용성 그룹 장애 조치(Failover) 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="25201-130">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="25201-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25201-131">See Also</span></span>  
 [<span data-ttu-id="25201-132">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="25201-132">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
