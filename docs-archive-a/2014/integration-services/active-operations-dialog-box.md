---
title: 활성 작업 대화 상자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49861de7be207875c554e02d3f3b1b2f941fff64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647821"
---
# <a name="active-operations-dialog-box"></a><span data-ttu-id="ee6af-102">활성 작업 대화 상자</span><span class="sxs-lookup"><span data-stu-id="ee6af-102">Active Operations Dialog Box</span></span>
  <span data-ttu-id="ee6af-103">**활성 작업** 대화 상자를 사용하여 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서버에서 현재 실행 중인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 작업(예: 배포, 유효성 검사 및 패키지 실행)의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee6af-103">Use the **Active Operations** dialog box to view the status of currently running [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] operations on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, such as deployment, validation, and package execution.</span></span> <span data-ttu-id="ee6af-104">이 데이터는 SSISDB 카탈로그에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee6af-104">This data is stored in the SSISDB catalog.</span></span>  
  
 <span data-ttu-id="ee6af-105">관련된 [!INCLUDE[tsql](../includes/tsql-md.md)] 뷰에 대한 자세한 내용은 [catalog.operations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) 및 [catalog.executions&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ee6af-105">For more information about related [!INCLUDE[tsql](../includes/tsql-md.md)] views, see [catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database), and [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)</span></span>  
  
 <span data-ttu-id="ee6af-106">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="ee6af-106">**What do you want to do?**</span></span>  
  
1.  [<span data-ttu-id="ee6af-107">활성 작업 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="ee6af-107">Open the Active Operations Dialog Box</span></span>](#open_dialog)  
  
2.  [<span data-ttu-id="ee6af-108">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="ee6af-108">Configure the Options</span></span>](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="ee6af-109">활성 작업 대화 상자 열기</span><span class="sxs-lookup"><span data-stu-id="ee6af-109">Open the Active Operations Dialog Box</span></span>  
  
1.  <span data-ttu-id="ee6af-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]열기</span><span class="sxs-lookup"><span data-stu-id="ee6af-110">Open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="ee6af-111">Microsoft SQL Server 데이터베이스 엔진 연결</span><span class="sxs-lookup"><span data-stu-id="ee6af-111">Connect Microsoft SQL Server Database Engine</span></span>  
  
3.  <span data-ttu-id="ee6af-112">개체 탐색기에서 **Integration Services** 노드를 확장하고 **SSISDB**를 마우스 오른쪽 단추로 클릭한 다음 **활성 작업**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee6af-112">In Object Explorer, expand the **Integration Services** node, right-click **SSISDB**, and then click **Active Operations**.</span></span>  
  
##  <a name="configure-the-options"></a><a name="options"></a> <span data-ttu-id="ee6af-113">옵션 구성</span><span class="sxs-lookup"><span data-stu-id="ee6af-113">Configure the Options</span></span>  
  
### <a name="options"></a><span data-ttu-id="ee6af-114">옵션</span><span class="sxs-lookup"><span data-stu-id="ee6af-114">Options</span></span>  
 <span data-ttu-id="ee6af-115">**형식**</span><span class="sxs-lookup"><span data-stu-id="ee6af-115">**Type**</span></span>  
 <span data-ttu-id="ee6af-116">작업 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee6af-116">Specifies the type of operation.</span></span> <span data-ttu-id="ee6af-117">다음은 **형식** 필드에 사용할 수 있는 값과 transact-sql 뷰의 operations_type 열에 있는 해당 값입니다 `catalog.operations` .</span><span class="sxs-lookup"><span data-stu-id="ee6af-117">The following are the possible values for the **Type** field and the corresponding values in the operations_type column of the Transact-SQL `catalog.operations` view.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee6af-118">Integration Services 초기화</span><span class="sxs-lookup"><span data-stu-id="ee6af-118">Integration Services initialization</span></span>|<span data-ttu-id="ee6af-119">1</span><span class="sxs-lookup"><span data-stu-id="ee6af-119">1</span></span>|  
|<span data-ttu-id="ee6af-120">작업 정리(SQL 에이전트 작업)</span><span class="sxs-lookup"><span data-stu-id="ee6af-120">Operations cleanup (SQL Agent job)</span></span>|<span data-ttu-id="ee6af-121">2</span><span class="sxs-lookup"><span data-stu-id="ee6af-121">2</span></span>|  
|<span data-ttu-id="ee6af-122">프로젝트 버전 정리(SQL 에이전트 작업)</span><span class="sxs-lookup"><span data-stu-id="ee6af-122">Project versions cleanup (SQL Agent job)</span></span>|<span data-ttu-id="ee6af-123">3</span><span class="sxs-lookup"><span data-stu-id="ee6af-123">3</span></span>|  
|<span data-ttu-id="ee6af-124">프로젝트 배포</span><span class="sxs-lookup"><span data-stu-id="ee6af-124">Deploy project</span></span>|<span data-ttu-id="ee6af-125">101</span><span class="sxs-lookup"><span data-stu-id="ee6af-125">101</span></span>|  
|<span data-ttu-id="ee6af-126">프로젝트 복원</span><span class="sxs-lookup"><span data-stu-id="ee6af-126">Restore project</span></span>|<span data-ttu-id="ee6af-127">106</span><span class="sxs-lookup"><span data-stu-id="ee6af-127">106</span></span>|  
|<span data-ttu-id="ee6af-128">패키지 실행 생성 및 시작</span><span class="sxs-lookup"><span data-stu-id="ee6af-128">Create and start package execution</span></span>|<span data-ttu-id="ee6af-129">200</span><span class="sxs-lookup"><span data-stu-id="ee6af-129">200</span></span>|  
|<span data-ttu-id="ee6af-130">작업 중지(유효성 검사 또는 실행 중지)</span><span class="sxs-lookup"><span data-stu-id="ee6af-130">Stop operation (stopping a validation or execution</span></span>|<span data-ttu-id="ee6af-131">202</span><span class="sxs-lookup"><span data-stu-id="ee6af-131">202</span></span>|  
|<span data-ttu-id="ee6af-132">프로젝트 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="ee6af-132">Validate project</span></span>|<span data-ttu-id="ee6af-133">300</span><span class="sxs-lookup"><span data-stu-id="ee6af-133">300</span></span>|  
|<span data-ttu-id="ee6af-134">패키지 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="ee6af-134">Validate package</span></span>|<span data-ttu-id="ee6af-135">301</span><span class="sxs-lookup"><span data-stu-id="ee6af-135">301</span></span>|  
|<span data-ttu-id="ee6af-136">카탈로그 구성</span><span class="sxs-lookup"><span data-stu-id="ee6af-136">Configure catalog</span></span>|<span data-ttu-id="ee6af-137">1000</span><span class="sxs-lookup"><span data-stu-id="ee6af-137">1000</span></span>|  
  
 <span data-ttu-id="ee6af-138">**중지**</span><span class="sxs-lookup"><span data-stu-id="ee6af-138">**Stop**</span></span>  
 <span data-ttu-id="ee6af-139">현재 실행 중인 작업을 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee6af-139">Click to stop a currently running operation.</span></span>  
  
  
