---
title: Microsoft 복제 상호 충돌 해결 프로그램 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8cbd2231ab1ab357321f9887bced986e182e608
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741844"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a><span data-ttu-id="1e40d-102">Microsoft 복제 상호 충돌 해결 프로그램</span><span class="sxs-lookup"><span data-stu-id="1e40d-102">Microsoft Replication Interactive Conflict Resolver</span></span>
  <span data-ttu-id="1e40d-103">상호 충돌 해결 프로그램은 Windows 동기화 관리자로 동기화하는 병합 구독에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-103">The Interactive Conflict Resolver can be used for merge subscriptions that are synchronized using Windows Synchronization Manager.</span></span> <span data-ttu-id="1e40d-104">상호 충돌 해결 프로그램을 사용하여 데이터 충돌 결과를 확인, 비교, 편집 및 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-104">It allows you to view, compare, edit, and select the outcome for data conflicts.</span></span> <span data-ttu-id="1e40d-105">또한 복제에는 충돌 결과를 커밋한 다음 충돌 결과를 보고 수정할 수 있는 충돌 뷰어가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-105">Replication also includes the Conflict Viewer, which allows you to view and modify conflict outcomes after they have been committed.</span></span> <span data-ttu-id="1e40d-106">상호 충돌 해결 프로그램을 사용하여 동기화 중에 결과를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-106">The Interactive Conflict Resolver allows you to select the outcome during synchronization.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e40d-107">논리적 레코드와 관련된 충돌은 대화형 해결 프로그램에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-107">Conflicts that involve logical records are not displayed in the Interactive Resolver.</span></span> <span data-ttu-id="1e40d-108">이러한 충돌에 대한 정보를 보려면 복제 저장 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-108">To view information about these conflicts, use replication stored procedures.</span></span> <span data-ttu-id="1e40d-109">자세한 내용은 [병합 게시에 대한 충돌 정보 보기&#40;복제 Transact-SQL 프로그래밍&#41;](view-conflict-information-for-merge-publications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e40d-109">For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](view-conflict-information-for-merge-publications.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="1e40d-110">옵션</span><span class="sxs-lookup"><span data-stu-id="1e40d-110">Options</span></span>  
 <span data-ttu-id="1e40d-111">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="1e40d-111">**Column name**</span></span>  
 <span data-ttu-id="1e40d-112">테이블에 있는 모든 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-112">The name of all columns in the table.</span></span> <span data-ttu-id="1e40d-113">하나 이상의 열에 충돌하는 데이터가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-113">One or more columns might have conflicting data.</span></span> <span data-ttu-id="1e40d-114">충돌하는 열에 상관없이 적용되는 전체 행이 무시되는 전체 행을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-114">Regardless of which columns conflict, the entire winning row will overwrite the entire losing row.</span></span>  
  
 <span data-ttu-id="1e40d-115">**권장 해결 방법**</span><span class="sxs-lookup"><span data-stu-id="1e40d-115">**Suggested Resolution**</span></span>  
 <span data-ttu-id="1e40d-116">해당 아티클에 대한 충돌 해결 프로그램에서 제공하는 권장 해결 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-116">The suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="1e40d-117">**게시자**</span><span class="sxs-lookup"><span data-stu-id="1e40d-117">**Publisher**</span></span>  
 <span data-ttu-id="1e40d-118">게시자의 데이터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-118">The data value at the Publisher.</span></span>  
  
 <span data-ttu-id="1e40d-119">**구독자**</span><span class="sxs-lookup"><span data-stu-id="1e40d-119">**Subscriber**</span></span>  
 <span data-ttu-id="1e40d-120">구독자의 데이터 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-120">The data value at the Subscriber.</span></span>  
  
 <span data-ttu-id="1e40d-121">**제안 허용**, **게시자 허용**및 **구독자 허용**</span><span class="sxs-lookup"><span data-stu-id="1e40d-121">**Accept Suggested**, **Accept Publisher**, and **Accept Subscriber**</span></span>  
 <span data-ttu-id="1e40d-122">충돌 시 게시자와 구독자 중 어떤 것을 무시하는지에 따라 게시자 또는 구독자에 적용되는 행을 허용하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-122">Click to accept the row that will be applied at either the Publisher or the Subscriber, depending on which one lost the conflict.</span></span> <span data-ttu-id="1e40d-123">충돌 시 게시자를 무시할 경우 다른 모든 구독자는 다음에 게시자와 동기화할 때 적용되는 행을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-123">If the Publisher lost the conflict, all other Subscribers will receive the winning row the next time they synchronize with the Publisher.</span></span>  
  
 <span data-ttu-id="1e40d-124">**남아 있는 충돌 자동 해결**</span><span class="sxs-lookup"><span data-stu-id="1e40d-124">**Resolve remaining conflicts automatically**</span></span>  
 <span data-ttu-id="1e40d-125">해당 아티클에 대한 충돌 해결 프로그램에서 제공하는 권장 해결 방법을 사용하여 남아 있는 충돌을 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-125">Resolve all remaining conflicts using the suggested resolution provided by the conflict resolver for the article.</span></span>  
  
 <span data-ttu-id="1e40d-126">**나중에 참조하도록 이 충돌 정보 기록**</span><span class="sxs-lookup"><span data-stu-id="1e40d-126">**Log the details of the conflict for later reference**</span></span>  
 <span data-ttu-id="1e40d-127">시스템 테이블에 충돌 정보를 자세히 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="1e40d-127">Logs the details of the conflict in system tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e40d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e40d-128">See Also</span></span>  
 <span data-ttu-id="1e40d-129">[대화형 충돌 해결](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="1e40d-129">[Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md) </span></span>  
 <span data-ttu-id="1e40d-130">[병합 게시에 대한 데이터 충돌 보기 및 해결&#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span><span class="sxs-lookup"><span data-stu-id="1e40d-130">[View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md) </span></span>  
 <span data-ttu-id="1e40d-131">[Windows 동기화 관리자를 사용하여 구독 동기화&#40;Windows 동기화 관리자&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span><span class="sxs-lookup"><span data-stu-id="1e40d-131">[Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](synchronize-a-subscription-using-windows-synchronization-manager.md) </span></span>  
 [<span data-ttu-id="1e40d-132">Advanced Merge Replication Conflict Detection and Resolution</span><span class="sxs-lookup"><span data-stu-id="1e40d-132">Advanced Merge Replication Conflict Detection and Resolution</span></span>](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
