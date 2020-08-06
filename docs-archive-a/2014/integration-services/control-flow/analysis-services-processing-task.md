---
title: Analysis Services 처리 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.f1
helpviewer_keywords:
- Analysis Services Processing task
- processing objects [Integration Services]
ms.assetid: e5748836-b4ce-4e17-ab6b-617a336f02f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19ef8046c06c9131b3ea2eb8ffe267c026808dfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729716"
---
# <a name="analysis-services-processing-task"></a><span data-ttu-id="869d1-102">Analysis Services 처리 태스크</span><span class="sxs-lookup"><span data-stu-id="869d1-102">Analysis Services Processing Task</span></span>
  <span data-ttu-id="869d1-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크는 테이블 형식 모델, 큐브, 차원 및 마이닝 모델과 같은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task processes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects such as tabular models, cubes, dimensions, and mining models.</span></span>  
  
 <span data-ttu-id="869d1-104">테이블 형식 모델을 처리할 때는 다음 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-104">When processing tabular models, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="869d1-105">테이블 형식 모델에서는 영향 분석을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-105">You cannot perform impact analysis on tabular models.</span></span>  
  
-   <span data-ttu-id="869d1-106">조각 모음 처리 및 다시 계산 처리와 같은 테이블 형식 모드에 대한 일부 처리 옵션은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="869d1-107">DDL 실행 태스크를 사용하여 이러한 함수를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
-   <span data-ttu-id="869d1-108">인덱스 처리 및 업데이트 처리 옵션은 테이블 형식 모델에 적합하지 않으며 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-108">The options Process Index and Process Update are not appropriate for tabular models and should not be used.</span></span>  
  
-   <span data-ttu-id="869d1-109">테이블 형식 모델에서는 일괄 설정이 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-109">Batch settings are ignored for tabular models.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="869d1-110">에는 DDL(데이터 정의 언어) 문과 데이터 마이닝 예측 쿼리 실행 등의 비즈니스 인텔리전스 태스크를 수행하는 많은 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-110">includes a number of tasks that perform business intelligence operations, such as running Data Definition Language (DDL) statements and data mining prediction queries.</span></span> <span data-ttu-id="869d1-111">관련 비즈니스 인텔리전스 태스크에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="869d1-111">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="869d1-112">Analysis Services DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="869d1-112">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="869d1-113">데이터 마이닝 쿼리 태스크</span><span class="sxs-lookup"><span data-stu-id="869d1-113">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="object-processing"></a><span data-ttu-id="869d1-114">개체 처리</span><span class="sxs-lookup"><span data-stu-id="869d1-114">Object Processing</span></span>  
 <span data-ttu-id="869d1-115">동시에 여러 개의 개체를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-115">Multiple objects can be processed at the same time.</span></span> <span data-ttu-id="869d1-116">여러 개의 개체를 처리하는 경우 일괄 처리의 모든 개체 처리에 적용되는 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-116">When processing multiple objects, you define settings that apply to the processing of all the objects in the batch.</span></span>  
  
 <span data-ttu-id="869d1-117">일괄 처리의 개체를 순서대로 또는 병렬로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-117">Objects in a batch can be processed in sequence or in parallel.</span></span> <span data-ttu-id="869d1-118">처리 시퀀스가 중요한 개체가 일괄 처리에 포함되어 있지 않으면 병렬 처리를 사용하여 처리 속도를 증가시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-118">If the batch does not contain objects for which processing sequence is important, parallel processing can speed up processing.</span></span> <span data-ttu-id="869d1-119">일괄 처리의 개체가 병렬로 처리되는 경우 태스크에서 병렬로 처리할 개체 수를 결정하도록 구성하거나 동시에 처리할 개체 수를 직접 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-119">If objects in the batch are processed in parallel, you can configure the task to let it determine how many objects to process in parallel, or you can manually specify the number of objects to process at the same time.</span></span> <span data-ttu-id="869d1-120">개체가 순서대로 처리되는 경우 한 트랜잭션에 모든 개체를 나열하거나 일괄 처리의 각 개체에 대해 별도의 트랜잭션을 사용하여 일괄 처리에 트랜잭션 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-120">If objects are processed sequentially, you can set a transaction attribute on the batch either by enlisting all objects in one transaction or by using a separate transaction for each object in the batch.</span></span>  
  
 <span data-ttu-id="869d1-121">분석 개체를 처리할 때 종속 개체를 함께 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-121">When you process analytic objects, you might also want to process the objects that depend on them.</span></span> <span data-ttu-id="869d1-122">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크에는 선택한 개체 외에 모든 종속 개체를 처리하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-122">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task includes an option to process any dependent objects in addition to the selected objects.</span></span>  
  
 <span data-ttu-id="869d1-123">일반적으로 팩트 테이블을 처리하기 전에 차원 테이블을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-123">Typically, you process dimension tables before processing fact tables.</span></span> <span data-ttu-id="869d1-124">차원 테이블을 처리하기 전에 팩트 테이블을 처리하려고 할 경우 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-124">You may encounter errors if you try to process fact tables before processing the dimension tables.</span></span>  
  
 <span data-ttu-id="869d1-125">이 태스크를 사용하여 차원 키 오류 처리를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-125">This task also lets you configure the handling of errors in dimension keys.</span></span> <span data-ttu-id="869d1-126">예를 들어 이 태스크는 오류를 무시하거나 지정한 수의 오류가 발생한 후 중지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-126">For example, the task can ignore errors or stop after a specified number of errors occur.</span></span> <span data-ttu-id="869d1-127">기본 오류 구성을 태스크에 사용하거나 사용자 지정 오류 구성을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-127">The task can use the default error configuration, or you can construct a custom error configuration.</span></span> <span data-ttu-id="869d1-128">사용자 지정 오류 구성에서는 태스크의 오류 처리 방법과 오류 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-128">In the custom error configuration, you specify how the task handles errors and the error conditions.</span></span> <span data-ttu-id="869d1-129">예를 들어 4번째 오류가 발생한 후 태스크 실행을 중지하도록 지정하거나 태스크에서 **Null** 키 값을 처리하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-129">For example, you can specify that the task should stop running when the fourth error occurs, or specify how the task should handle **Null** key values.</span></span> <span data-ttu-id="869d1-130">사용자 지정 오류 구성에 오류 로그 경로를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-130">The custom error configuration can also include the path of an error log.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="869d1-131">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 도구를 사용하여 만든 분석 개체만 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-131">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task can process only analytic objects created by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools.</span></span>  
  
 <span data-ttu-id="869d1-132">이 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 데이터를 로드하는 대량 삽입 태스크나 데이터를 테이블에 로드하는 데이터 흐름을 구현하는 데이터 흐름 태스크와 함께 자주 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-132">This task is frequently used in combination with a Bulk Insert task that loads data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, or a Data Flow task that implements a data flow that loads data into a table.</span></span> <span data-ttu-id="869d1-133">예를 들어 OLTP(온라인 트랜잭션 데이터베이스) 데이터베이스에서 데이터를 추출하여 데이터 웨어하우스의 팩트 테이블에 로드하는 데이터 흐름이 데이터 흐름 태스크에 포함될 수 있습니다. 그런 다음 데이터 웨어하우스에 작성된 큐브 처리를 위해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-133">For example, the Data Flow task might have a data flow that extracts data from an online transactional database (OLTP) database and loads it into a fact table in a data warehouse, after which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task is called to process the cube built on the data warehouse.</span></span>  
  
 <span data-ttu-id="869d1-134">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 처리 태스크는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-134">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="869d1-135">자세한 내용은 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="869d1-135">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="869d1-136">오류 처리</span><span class="sxs-lookup"><span data-stu-id="869d1-136">Error Handling</span></span>  
  
## <a name="configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="869d1-137">Analysis Services 처리 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="869d1-137">Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="869d1-138">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="869d1-138">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="869d1-139">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="869d1-139">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="869d1-140">Analysis Services 처리 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="869d1-140">Analysis Services Processing Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="869d1-141">Analysis Services 처리 태스크 편집기&#40;Analysis Services 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="869d1-141">Analysis Services Processing Task Editor &#40;Analysis Services Page&#41;</span></span>](../analysis-services-processing-task-editor-analysis-services-page.md)  
  
-   [<span data-ttu-id="869d1-142">식 페이지</span><span class="sxs-lookup"><span data-stu-id="869d1-142">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="869d1-143">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="869d1-143">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="869d1-144">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="869d1-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="869d1-145">Analysis Services 처리 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="869d1-145">Programmatic Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="869d1-146">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="869d1-146">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.DTSProcessingTask>  
  
  
