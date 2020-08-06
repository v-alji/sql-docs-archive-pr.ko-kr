---
title: SQL Server Management Studio의 Reporting Services(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], how-to topics
ms.assetid: 60685458-9108-47bf-820a-5e7db454d408
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f4083d8b288c8816925723f4cfaef4342dd0298
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736004"
---
# <a name="reporting-services-in-sql-server-management-studio-ssrs"></a><span data-ttu-id="59cc0-102">SQL Server Management Studio의 Reporting Services(SSRS)</span><span class="sxs-lookup"><span data-stu-id="59cc0-102">Reporting Services in SQL Server Management Studio (SSRS)</span></span>
  <span data-ttu-id="59cc0-103">보고서 서버 관리자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-103">Report server administrators can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to:</span></span>  
  
-   <span data-ttu-id="59cc0-104">기능을 활성화하고 서버 기본값을 설정하며 실행 중인 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-104">Enable features, set server defaults, and manage running jobs.</span></span>  
  
-   <span data-ttu-id="59cc0-105">보고서를 보고 사용자 지정 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-105">View and create custom reports.</span></span> <span data-ttu-id="59cc0-106">개체 탐색기의 많은 노드에는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]와 함께 설치된 표준 보고서 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-106">In Object Explorer, many nodes display a set of standard reports that are installed with [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="59cc0-107">관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-107">You must have administrator permissions.</span></span> <span data-ttu-id="59cc0-108">사용자 지정 보고서의 스키마가 설치된 보고서의 스키마와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-108">The schema of a custom report must match the schema of the installed reports.</span></span> <span data-ttu-id="59cc0-109">자세한 내용은 [Management Studio의 사용자 지정 보고서](../../ssms/object/custom-reports-in-management-studio.md) 및 [보고서 정의 스키마 버전 찾기&#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59cc0-109">For more information, see [Custom Reports in Management Studio](../../ssms/object/custom-reports-in-management-studio.md) and [Find the Report Definition Schema Version &#40;SSRS&#41;](../reports/find-the-report-definition-schema-version-ssrs.md).</span></span>  
  
 <span data-ttu-id="59cc0-110">보고서 작성자는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 를 사용하여 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-110">Report authors can use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to:</span></span>  
  
-   <span data-ttu-id="59cc0-111">쿼리 결과 집합에서 공간 데이터를 시각화하여 지도 보고서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-111">Visualize spatial data from a query result set for a map report.</span></span> <span data-ttu-id="59cc0-112">쿼리를 실행한 후 결과 집합 창에서 **공간 결과** 탭을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-112">After you run the query, use the **Spatial results** tab in the result set pane.</span></span> <span data-ttu-id="59cc0-113">자세한 내용은 [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="59cc0-113">For more information, see [View Spatial Data in Object Explorer](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md).</span></span>  
  
 <span data-ttu-id="59cc0-114">이 섹션에서는 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 사용하여 단계별로 다양한 보고 태스크를 수행하는 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-114">This section contains step-by-step instructions for performing various reporting tasks using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="59cc0-115">보고서 관리자를 사용하여 공유 일정을 만들고 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59cc0-115">Creating and managing shared schedules can also be performed using Report Manager.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59cc0-116">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="59cc0-116">In This Section</span></span>  
  
-   [<span data-ttu-id="59cc0-117">Management Studio에서 보고서 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="59cc0-117">Connect to a Report Server in Management Studio</span></span>](connect-to-a-report-server-in-management-studio.md)  
  
-   [<span data-ttu-id="59cc0-118">보고서 서버 속성 설정&#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59cc0-118">Set Report Server Properties &#40;Management Studio&#41;</span></span>](set-report-server-properties-management-studio.md)  
  
-   [<span data-ttu-id="59cc0-119">역할 만들기, 삭제 또는 수정&#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59cc0-119">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](../security/role-definitions-create-delete-or-modify.md)  
  
-   [<span data-ttu-id="59cc0-120">항목 삭제&#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59cc0-120">Delete an Item &#40;Management Studio&#41;</span></span>](delete-an-item-management-studio.md)  
  
-   [<span data-ttu-id="59cc0-121">보고서 서버 작업 취소&#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="59cc0-121">Cancel Report Server Jobs &#40;Management Studio&#41;</span></span>](cancel-report-server-jobs-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="59cc0-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59cc0-122">See Also</span></span>  
 <span data-ttu-id="59cc0-123">[Management Studio F1 도움말의 보고서 서버](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="59cc0-123">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 [<span data-ttu-id="59cc0-124">SQL Server Management Studio 소개</span><span class="sxs-lookup"><span data-stu-id="59cc0-124">Introducing SQL Server Management Studio</span></span>](../../ssms/sql-server-management-studio-ssms.md)  
  
  
