---
title: 여러 테이블의 증분 로드 수행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e4bf81d1d529e8102271c66839440ef712219600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647812"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a><span data-ttu-id="cd22e-102">여러 테이블의 증분 로드 수행</span><span class="sxs-lookup"><span data-stu-id="cd22e-102">Perform an Incremental Load of Multiple Tables</span></span>
  <span data-ttu-id="cd22e-103">[변경 데이터 캡처를 사용하여 증분 로드 개선](change-data-capture-ssis.md)항목의 다이어그램에서는 한 테이블에서만 증분 로드를 수행하는 기본 패키지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-103">In the topic, [Improving Incremental Loads with Change Data Capture](change-data-capture-ssis.md), the diagram illustrates a basic package that performs an incremental load on just one table.</span></span> <span data-ttu-id="cd22e-104">그러나 한 테이블을 로드하는 작업은 여러 테이블을 증분 로드하는 작업만큼 일반적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-104">However, loading one table is not as common as having to perform an incremental load of multiple tables.</span></span>  
  
 <span data-ttu-id="cd22e-105">여러 테이블을 증분 로드할 때 일부 단계는 모든 테이블에 대해 한 번만 수행해야 하며 다른 단계는 각 원본 테이블에 대해 반복해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-105">When you perform an incremental load of multiple tables, some steps have to be performed once for all the tables, and other steps have to be repeated for each source table.</span></span> <span data-ttu-id="cd22e-106">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 이러한 단계를 구현하는 데에는 다음과 같은 여러 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-106">You have more than one option for implementing these steps in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="cd22e-107">부모 패키지 및 자식 패키지 사용</span><span class="sxs-lookup"><span data-stu-id="cd22e-107">Use a parent package and child packages.</span></span>  
  
-   <span data-ttu-id="cd22e-108">단일 패키지에서 여러 데이터 흐름 태스크 사용</span><span class="sxs-lookup"><span data-stu-id="cd22e-108">Use multiple Data Flow tasks in a single package.</span></span>  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a><span data-ttu-id="cd22e-109">부모 패키지 및 여러 자식 패키지를 사용하여 여러 테이블 로드</span><span class="sxs-lookup"><span data-stu-id="cd22e-109">Loading Multiple Tables by Using a Parent Package and Multiple Child Packages</span></span>  
 <span data-ttu-id="cd22e-110">부모 패키지를 사용하여 한 번만 수행되어야 하는 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-110">You can use a parent package to perform those steps that only have to be done once.</span></span> <span data-ttu-id="cd22e-111">자식 패키지는 각 원본 테이블에 대해 수행되어야 하는 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-111">The child packages will perform those steps that have to be done for each source table.</span></span>  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a><span data-ttu-id="cd22e-112">한 번만 수행되어야 하는 단계를 수행하는 부모 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cd22e-112">To create a parent package that performs those steps that only have to be done once</span></span>  
  
1.  <span data-ttu-id="cd22e-113">부모 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-113">Create a parent package.</span></span>  
  
2.  <span data-ttu-id="cd22e-114">제어 흐름에서 SQL 실행 태스크나 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식을 사용하여 엔드포인트를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-114">In the control flow, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="cd22e-115">엔드포인트를 계산하는 방법의 예는 [변경 데이터의 간격 지정](specify-an-interval-of-change-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-115">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cd22e-116">필요한 경우 For 루프 컨테이너를 사용하여 선택한 기간에 대한 변경 데이터가 준비될 때까지 실행을 지연합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-116">If needed, use a For Loop container to delay execution until change data for the selected period is ready.</span></span>  
  
     <span data-ttu-id="cd22e-117">이러한 For 루프 컨테이너의 예는 [변경 데이터의 준비 여부 확인](determine-whether-the-change-data-is-ready.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-117">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="cd22e-118">여러 패키지 실행 태스크를 사용하여 로드할 각 테이블에 대해 자식 패키지를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-118">Use multiple Execute Package tasks to execute child packages for each table to be loaded.</span></span> <span data-ttu-id="cd22e-119">부모 패키지 변수 구성을 사용하여 부모 패키지에서 계산된 엔드포인트를 각 자식 패키지에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-119">Pass the endpoints calculated in the parent package to each child package by using Parent Package Variable configurations.</span></span>  
  
     <span data-ttu-id="cd22e-120">자세한 내용은 [패키지 실행 태스크](../control-flow/execute-package-task.md) 및 [자식 패키지에서 변수 및 매개 변수의 값 사용](../use-the-values-of-variables-and-parameters-in-a-child-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-120">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a><span data-ttu-id="cd22e-121">각 원본 테이블에 대해 수행되어야 하는 단계를 수행하는 자식 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="cd22e-121">To create child packages to perform those steps that have to be done for each source table</span></span>  
  
1.  <span data-ttu-id="cd22e-122">각 원본 테이블에 대해 자식 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-122">For each source table, create a child package.</span></span>  
  
2.  <span data-ttu-id="cd22e-123">제어 흐름에서 스크립트 태스크나 SQL 실행 태스크를 사용하여 변경 내용을 쿼리하는 데 사용할 SQL 문을 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-123">In the control flow, use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="cd22e-124">쿼리를 조합하는 방법의 예는 [변경 데이터에 대한 쿼리 준비](prepare-to-query-for-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-124">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cd22e-125">각 자식 패키지에서 단일 데이터 흐름 태스크를 사용하여 변경 데이터를 로드하고 대상에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-125">Use a single Data Flow task in each child package to load the change data and apply it to the destination.</span></span> <span data-ttu-id="cd22e-126">다음 단계에 설명된 대로 데이터 흐름을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-126">Configure the Data Flow as described in the following steps:</span></span>  
  
    1.  <span data-ttu-id="cd22e-127">데이터 흐름에서 원본 구성 요소를 사용하여 선택한 엔드포인트 범위에 포함되는 변경 테이블의 변경 내용을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-127">In the data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="cd22e-128">변경 테이블을 쿼리하는 방법의 예는 [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-128">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="cd22e-129">조건부 분할 변환을 사용하여 적절한 처리를 위해 삽입, 업데이트 및 삭제를 다른 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-129">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="cd22e-130">이 변환을 구성하여 출력을 전송하는 방법의 예는 [삽입, 업데이트 및 삭제 처리](process-inserts-updates-and-deletes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-130">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="cd22e-131">대상 구성 요소를 사용하여 대상에 삽입을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-131">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="cd22e-132">또한 OLE DB 명령 변환에 매개 변수가 있는 UPDATE 및 DELETE 문을 사용하여 대상에 업데이트 및 삭제를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-132">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="cd22e-133">이 변환을 사용하여 업데이트 및 삭제를 적용하는 방법의 예는 [대상에 변경 내용 적용](apply-the-changes-to-the-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-133">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="cd22e-134">단일 패키지에서 여러 데이터 흐름 태스크를 사용하여 여러 테이블 로드</span><span class="sxs-lookup"><span data-stu-id="cd22e-134">Loading Multiple Tables by Using Multiple Data Flow Tasks in a Single Package</span></span>  
 <span data-ttu-id="cd22e-135">로드할 각 원본 테이블에 대한 별도의 데이터 흐름 태스크를 포함하는 단일 패키지를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-135">Alternatively, you can use a single package that contains a separate Data Flow task for each source table to be loaded.</span></span>  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a><span data-ttu-id="cd22e-136">단일 패키지에서 여러 데이터 흐름 태스크를 사용하여 여러 테이블을 로드하려면</span><span class="sxs-lookup"><span data-stu-id="cd22e-136">To load multiple tables by using multiple Data Flow tasks in a single package</span></span>  
  
1.  <span data-ttu-id="cd22e-137">단일 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-137">Create a single package.</span></span>  
  
2.  <span data-ttu-id="cd22e-138">제어 흐름에서 SQL 실행 태스크나 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식을 사용하여 엔드포인트를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-138">In the control flow, use an Execute SQL Task or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions to calculate the endpoints.</span></span>  
  
     <span data-ttu-id="cd22e-139">엔드포인트를 계산하는 방법의 예는 [변경 데이터의 간격 지정](specify-an-interval-of-change-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-139">For an example of how to calculate endpoints, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span>  
  
3.  <span data-ttu-id="cd22e-140">필요한 경우 For 루프 컨테이너를 사용하여 선택한 간격에 대한 변경 데이터가 준비될 때까지 실행을 지연합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-140">If needed, use a For Loop container to delay execution until the change data for the selected interval is ready.</span></span>  
  
     <span data-ttu-id="cd22e-141">이러한 For 루프 컨테이너의 예는 [변경 데이터의 준비 여부 확인](determine-whether-the-change-data-is-ready.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-141">For an example of such a For Loop container, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span>  
  
4.  <span data-ttu-id="cd22e-142">스크립트 태스크나 SQL 실행 태스크를 사용하여 변경 내용을 쿼리하는 데 사용할 SQL 문을 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-142">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>  
  
     <span data-ttu-id="cd22e-143">쿼리를 조합하는 방법의 예는 [변경 데이터에 대한 쿼리 준비](prepare-to-query-for-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-143">For an example of how to assemble the query, see [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md).</span></span>  
  
5.  <span data-ttu-id="cd22e-144">여러 데이터 흐름 태스크를 사용하여 각 원본 테이블에서 변경 데이터를 로드하고 대상에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-144">Use multiple Data Flow tasks to load the change data from each source table and apply it to the destination.</span></span> <span data-ttu-id="cd22e-145">다음 단계에 설명된 대로 각 데이터 흐름 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-145">Configure each Data Flow task as described in the following steps.</span></span>  
  
    1.  <span data-ttu-id="cd22e-146">각 데이터 흐름에서 원본 구성 요소를 사용하여 선택한 엔드포인트 범위에 포함되는 변경 테이블의 변경 내용을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-146">In each data flow, use a source component to query the change tables for the changes that fall within the selected endpoints.</span></span>  
  
         <span data-ttu-id="cd22e-147">변경 테이블을 쿼리하는 방법의 예는 [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-147">For an example of how to query the change tables, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
    2.  <span data-ttu-id="cd22e-148">조건부 분할 변환을 사용하여 적절한 처리를 위해 삽입, 업데이트 및 삭제를 다른 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-148">Use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>  
  
         <span data-ttu-id="cd22e-149">이 변환을 구성하여 출력을 전송하는 방법의 예는 [삽입, 업데이트 및 삭제 처리](process-inserts-updates-and-deletes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-149">For an example of how to configure this transformation to direct output, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span>  
  
    3.  <span data-ttu-id="cd22e-150">대상 구성 요소를 사용하여 대상에 삽입을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-150">Use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="cd22e-151">또한 OLE DB 명령 변환에 매개 변수가 있는 UPDATE 및 DELETE 문을 사용하여 대상에 업데이트 및 삭제를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="cd22e-151">Use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span>  
  
         <span data-ttu-id="cd22e-152">이 변환을 사용하여 업데이트 및 삭제를 적용하는 방법의 예는 [대상에 변경 내용 적용](apply-the-changes-to-the-destination.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd22e-152">For an example of how to use this transformation to apply updates and deletes, see [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md).</span></span>  
  
  
