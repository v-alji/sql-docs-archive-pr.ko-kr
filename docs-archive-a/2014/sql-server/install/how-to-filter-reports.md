---
title: '방법: 보고서 필터링 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reports [Upgrade Advisor], filtering
- filtering reports [Reporting Services]
ms.assetid: bc3dbe16-f6c1-4f07-8d88-2b8e86302c7e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4946b9ea208c0fad98426b7c7fc4247cfaa47680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660314"
---
# <a name="how-to-filter-reports"></a><span data-ttu-id="43722-102">방법: 보고서 필터링</span><span class="sxs-lookup"><span data-stu-id="43722-102">How to: Filter Reports</span></span>
  <span data-ttu-id="43722-103">이 항목에서는 업그레이드 관리자 보고서 뷰어를 사용하여 보고서에 필터를 적용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-103">This topic describes how you can use the Upgrade Advisor Report Viewer to apply filters to a report.</span></span>  
  
### <a name="to-filter-reports"></a><span data-ttu-id="43722-104">보고서를 필터링하려면</span><span class="sxs-lookup"><span data-stu-id="43722-104">To filter reports</span></span>  
  
1.  <span data-ttu-id="43722-105">보고서 뷰어에서 필터링할 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-105">In the report viewer, display the report that you want to filter.</span></span> <span data-ttu-id="43722-106">자세한 내용은 [방법: 업그레이드 관리자 보고서 보기](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43722-106">For instructions, see [How to: View an Upgrade Advisor Report](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md).</span></span>  
  
2.  <span data-ttu-id="43722-107">**필터 기준** 목록에서 보려는 문제 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-107">In the **Filter by** list, select a type of issue to view:</span></span>  
  
    -   <span data-ttu-id="43722-108">**모든 문제**</span><span class="sxs-lookup"><span data-stu-id="43722-108">**All issues**.</span></span> <span data-ttu-id="43722-109">해결된 것으로 표시되지 않은 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-109">This displays all issues that have not been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="43722-110">**모든 업그레이드 문제**입니다.</span><span class="sxs-lookup"><span data-stu-id="43722-110">**All upgrade issues**.</span></span> <span data-ttu-id="43722-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하는 것과 관련된 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-111">This displays all issues that are related to upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="43722-112">**업그레이드 이전 문제**</span><span class="sxs-lookup"><span data-stu-id="43722-112">**Pre-upgrade issues**.</span></span> <span data-ttu-id="43722-113">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 해결해야 하는 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-113">This displays all issues that should or must be fixed before upgrading to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="43722-114">**모든 마이그레이션 문제**</span><span class="sxs-lookup"><span data-stu-id="43722-114">**All migration issues**.</span></span> <span data-ttu-id="43722-115">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 데이터 또는 애플리케이션을 마이그레이션하는 것과 관련된 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-115">This displays all issues that are related to migrating data or applications to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
    -   <span data-ttu-id="43722-116">**해결 된 문제**입니다.</span><span class="sxs-lookup"><span data-stu-id="43722-116">**Resolved Issues**.</span></span> <span data-ttu-id="43722-117">해결된 것으로 표시된 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-117">This displays all issues that have been marked as resolved.</span></span>  
  
    -   <span data-ttu-id="43722-118">**해결 되지 않은 문제**</span><span class="sxs-lookup"><span data-stu-id="43722-118">**Unresolved Issues**.</span></span> <span data-ttu-id="43722-119">아직 해결되지 않은 모든 문제를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43722-119">This displays all issues that have not yet been resolved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43722-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43722-120">See Also</span></span>  
 <span data-ttu-id="43722-121">[방법: 업그레이드 관리자 분석 마법사 실행](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="43722-121">[How to: Run the Upgrade Advisor Analysis Wizard](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md) </span></span>  
 <span data-ttu-id="43722-122">[업그레이드 문제 해결](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="43722-122">[Resolving Upgrade Issues](../../../2014/sql-server/install/resolving-upgrade-issues.md) </span></span>  
 <span data-ttu-id="43722-123">[업그레이드 관리자 방법 도움말 항목](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="43722-123">[Upgrade Advisor How-to Topics](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md) </span></span>  
 [<span data-ttu-id="43722-124">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="43722-124">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
