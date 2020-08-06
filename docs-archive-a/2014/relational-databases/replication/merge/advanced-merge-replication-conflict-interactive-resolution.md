---
title: 대화형 충돌 해결 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- interactive conflict resolution [SQL Server replication]
- interactive resolver [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57d0de17c4d958a1b842748810ba24717e6866e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638723"
---
# <a name="interactive-conflict-resolution"></a><span data-ttu-id="fd134-102">Interactive Conflict Resolution</span><span class="sxs-lookup"><span data-stu-id="fd134-102">Interactive Conflict Resolution</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="fd134-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 복제는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 동기화 관리자에서 요청 시 동기화 중에 수동으로 충돌을 해결할 수 있는 대화형 해결 프로그램을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on-demand synchronization in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Synchronization Manager.</span></span> <span data-ttu-id="fd134-104">런타임 시 활성화되는 대화형 해결 프로그램은 충돌하는 각 행의 데이터를 표시하여 충돌 데이터를 보고 편집하며 각 충돌을 개별적으로 해결하는 옵션을 제공하는 그래픽 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-104">Activated at run time, the Interactive Resolver is a graphical interface that displays data for each conflicting row, and provides options for viewing and editing the conflict data, and resolving each conflict individually.</span></span>  
  
 <span data-ttu-id="fd134-105">대화형 해결 프로그램은 충돌 뷰어와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-105">The Interactive Resolver resembles the Conflict Viewer.</span></span> <span data-ttu-id="fd134-106">그러나 충돌 뷰어는 병합 동기화 후 이미 해결된 충돌의 결과를 표시하는 반면 대화형 해결 프로그램은 해결 전 각 충돌을 표시하여 병합 동기화 중 각 충돌의 결과를 결정하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-106">However, the Conflict Viewer displays the results of conflicts that are already resolved after merge synchronization, and the Interactive Resolver displays each conflict prior to resolution, allowing you to determine the outcome of each conflict during merge synchronization.</span></span> <span data-ttu-id="fd134-107">사용자는 충돌 발생 시 대화형 해결 프로그램을 모니터링할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-107">Someone should be available to monitor the Interactive Resolver when a conflict occurs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fd134-108">대화형 해결을 사용하려면 Windows 동기화 관리자가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-108">Interactive Resolution requires Windows Synchronization Manager.</span></span> <span data-ttu-id="fd134-109">동기화가 Windows 동기화 관리자 외부(예: [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 또는 복제 모니터의 예약 동기화 또는 요청 시 동기화)에서 수행된 경우 아티클에 지정된 해결 프로그램에 따라 사용자 개입 없이도 자동으로 충돌이 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-109">If a synchronization is performed outside of Windows Synchronization Manager (as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or Replication Monitor), conflicts are resolved automatically without user intervention, according to the resolver specified for the article.</span></span> <span data-ttu-id="fd134-110">논리적 레코드와 관련된 충돌은 대화형 해결 프로그램에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-110">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="fd134-111">이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-111">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="fd134-112">자세한 내용은 [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](../view-conflict-information-for-merge-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd134-112">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="article-resolvers-and-the-interactive-resolver"></a><span data-ttu-id="fd134-113">아티클 해결 프로그램 및 대화형 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="fd134-113">Article Resolvers and the Interactive Resolver</span></span>  
 <span data-ttu-id="fd134-114">게시가 만들어질 때 충돌 해결 프로그램(기본 해결 프로그램, 비즈니스 논리 처리기 또는 사용자 지정 해결 프로그램)은 특정 아티클에 할당되며 규칙 집합을 사용하여 충돌하는 행 데이터 입력 시 사용해야 하는 데이터 집합을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-114">Conflict resolvers (either the default resolver, a business logic handler, or a custom resolver) are assigned to specific articles when a publication is created, and use a set of rules to determine which set of data should be used when conflicting row data is entered.</span></span> <span data-ttu-id="fd134-115">대화형 해결 프로그램은 충돌 시 적용되는 내용과 삭제되는 내용을 결정하는 규칙을 가진 별도의 충돌 해결 프로그램이 아니라 기본 및 사용자 지정 해결 프로그램과 함께 사용되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-115">The Interactive Resolver is not a separate conflict resolver with rules for determining conflict winners and losers, but a tool used in conjunction with default and custom resolvers.</span></span> <span data-ttu-id="fd134-116">아티클 해결 프로그램도 적용할 행 및 삭제할 행을 결정하지만 대화형 해결 프로그램으로 사용자는 결과를 승인, 거부 또는 수정할 수 있는 간섭 기능을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-116">The article resolver still determines the winning and losing row, but the Interactive Resolver allows user intervention to accept, reject, or modify the results.</span></span>  
  
 <span data-ttu-id="fd134-117">대화형 해결 프로그램을 사용하려면 필요한 각 아티클과 구독에 대해 대화형 해결을 사용할 수 있게 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-117">To use the Interactive Resolver, interactive resolution must be enabled for each article and subscription that requires it.</span></span> <span data-ttu-id="fd134-118">하나 이상의 아티클과 구독에 대해 대화형 해결을 사용할 수 있게 설정하면 병합 동기화 중 충돌이 감지될 때 대화형 해결 프로그램이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd134-118">After it is enabled for one or more articles and subscriptions, the Interactive Resolver is used when a conflict is detected during merge synchronization.</span></span>  
  
 <span data-ttu-id="fd134-119">대화형 해결 프로그램을 사용하려면 [병합 아티클에 대한 상호 충돌 해결 프로그램 지정](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) 및 [Windows 동기화 관리자를 사용하여 구독 동기화&#40;Windows 동기화 관리자&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd134-119">To use the Interactive Resolver, see [Specify Interactive Conflict Resolution for Merge Articles](..//publish/specify-merge-replication-properties.md#interactive-conflict-resolution) and [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../synchronize-a-subscription-using-windows-synchronization-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd134-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd134-120">See Also</span></span>  
 [<span data-ttu-id="fd134-121">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="fd134-121">Advanced Merge Replication Conflict Detection and Resolution</span></span>](advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
