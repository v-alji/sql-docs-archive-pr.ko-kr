---
title: 변경 데이터의 간격 지정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70b9c14d609f2db69ee5751eca18acb5262a07a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649123"
---
# <a name="specify-an-interval-of-change-data"></a><span data-ttu-id="db177-102">변경 데이터의 간격 지정</span><span class="sxs-lookup"><span data-stu-id="db177-102">Specify an Interval of Change Data</span></span>
  <span data-ttu-id="db177-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 제어 흐름에서 첫 번째 태스크는 변경 간격의 엔드포인트를 계산하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db177-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="db177-104">이러한 엔드포인트는 `datetime` 값이며 패키지에서 나중에 사용하기 위해 패키지 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="db177-104">These endpoints are `datetime` values and will be stored in package variables for use later in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db177-105">제어 흐름 디자인의 전체 프로세스에 대한 설명은 [데이터 캡처 변경&#40;SSIS&#41;](change-data-capture-ssis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db177-105">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="set-up-package-variables-for-the-endpoints"></a><span data-ttu-id="db177-106">엔드포인트에 대한 패키지 변수 설정</span><span class="sxs-lookup"><span data-stu-id="db177-106">Set Up Package Variables for the Endpoints</span></span>  
 <span data-ttu-id="db177-107">SQL 실행 태스크를 구성하여 엔드포인트를 계산하기 전에 엔드포인트를 저장할 패키지 변수를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-107">Before configuring the Execute SQL task to calculate the endpoints, the package variables that will store the endpoints have to be defined.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="db177-108">패키지 변수를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="db177-108">To set up package variables</span></span>  
  
1.  <span data-ttu-id="db177-109">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 새 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="db177-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="db177-110">**변수** 창에서 다음 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db177-110">In the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="db177-111">간격의 시작 지점을 보관할 `datetime` 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db177-111">Create a variable with the `datetime` data type to hold the starting point for the interval.</span></span>  
  
         <span data-ttu-id="db177-112">이 예에서는 변수 이름으로 ExtractStartTime을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-112">This example uses the variable name, ExtractStartTime.</span></span>  
  
    2.  <span data-ttu-id="db177-113">간격의 끝 지점을 보관할 `datetime` 데이터 형식의 다른 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="db177-113">Create another variable with the `datetime` data type to hold the ending point for the interval.</span></span>  
  
         <span data-ttu-id="db177-114">이 예에서는 변수 이름으로 ExtractEndTime을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-114">This example uses the variable name, ExtractEndTime.</span></span>  
  
 <span data-ttu-id="db177-115">여러 자식 패키지를 실행하는 마스터 패키지에서 엔드포인트를 계산하는 경우 부모 패키지 변수 구성을 사용하여 이러한 변수 값을 각 자식 패키지에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-115">If you calculate the endpoints in a master package that executes multiple child packages, you can use Parent Package Variable configurations to pass the values of these variables to each child package.</span></span> <span data-ttu-id="db177-116">자세한 내용은 [패키지 실행 태스크](../control-flow/execute-package-task.md) 및 [자식 패키지에서 변수 및 매개 변수의 값 사용](../use-the-values-of-variables-and-parameters-in-a-child-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="db177-116">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a><span data-ttu-id="db177-117">변경 데이터의 시작 지점 및 끝 지점 계산</span><span class="sxs-lookup"><span data-stu-id="db177-117">Calculate a Starting Point and an Ending Point for Change Data</span></span>  
 <span data-ttu-id="db177-118">간격 엔드포인트에 대한 패키지 변수를 설정한 후 해당 엔드포인트의 실제 값을 계산하고 이러한 값을 해당 패키지 변수에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-118">After you set up the package variables for the interval endpoints, you can calculate the actual values for those endpoints and map those values to the corresponding package variables.</span></span> <span data-ttu-id="db177-119">이러한 엔드포인트는 `datetime` 값이므로 `datetime` 값을 계산하거나 사용할 수 있는 함수를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-119">Because those endpoints are `datetime` values, you will have to use functions that can calculate or work with `datetime` values.</span></span> <span data-ttu-id="db177-120">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식 언어와 Transact-SQL 모두에 `datetime` 값을 사용하는 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-120">Both the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language and Transact-SQL have functions that work with `datetime` values:</span></span>  
  
 <span data-ttu-id="db177-121">`datetime` 값을 사용하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식 언어의 함수</span><span class="sxs-lookup"><span data-stu-id="db177-121">Functions in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language that work with `datetime` values</span></span>  
 -   [<span data-ttu-id="db177-122">DATEADD&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-122">DATEADD &#40;SSIS Expression&#41;</span></span>](../expressions/dateadd-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-123">DATEDIFF&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-123">DATEDIFF &#40;SSIS Expression&#41;</span></span>](../expressions/datediff-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-124">DATEPART&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-124">DATEPART &#40;SSIS Expression&#41;</span></span>](../expressions/datepart-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-125">DAY&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-125">DAY &#40;SSIS Expression&#41;</span></span>](../expressions/day-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-126">GETDATE&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-126">GETDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getdate-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-127">GETUTCDATE&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-127">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getutcdate-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-128">MONTH&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-128">MONTH &#40;SSIS Expression&#41;</span></span>](../expressions/month-ssis-expression.md)  
  
-   [<span data-ttu-id="db177-129">YEAR&#40;SSIS 식&#41;</span><span class="sxs-lookup"><span data-stu-id="db177-129">YEAR &#40;SSIS Expression&#41;</span></span>](../expressions/year-ssis-expression.md)  
  
 <span data-ttu-id="db177-130">`datetime` 값을 사용하는 Transact-SQL의 함수</span><span class="sxs-lookup"><span data-stu-id="db177-130">Functions in Transact-SQL that work with `datetime` values</span></span>  
 <span data-ttu-id="db177-131">[날짜 및 시간 데이터 형식 및 함수&#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span><span class="sxs-lookup"><span data-stu-id="db177-131">[Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="db177-132">이러한 `datetime` 함수 중 하나를 사용하여 엔드포인트를 계산하기 전에 간격이 고정되어 있고 정기적으로 발생하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-132">Before you use any one of these `datetime` functions to calculate the endpoints, you have to determine whether the interval is fixed and occurs on a regular schedule.</span></span> <span data-ttu-id="db177-133">일반적으로 원본 테이블에서 발생한 변경 내용을 정기적으로 대상 테이블에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-133">Typically, you want to apply changes that have occurred in source tables to destination tables on a regular schedule.</span></span> <span data-ttu-id="db177-134">예를 들어 이러한 변경 내용을 매시간, 매일 또는 매주 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-134">For example, you might want to apply those changes on an hourly, daily, or weekly basis.</span></span>  
  
 <span data-ttu-id="db177-135">변경 간격이 고정적인지, 아니면 보다 임의적인지 이해한 후 엔드포인트를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-135">After you understand whether your change interval is fixed or is more random, you can calculate the endpoints:</span></span>  
  
-   <span data-ttu-id="db177-136">**시작 날짜 및 시간 계산**.</span><span class="sxs-lookup"><span data-stu-id="db177-136">**Calculating the starting date and time**.</span></span> <span data-ttu-id="db177-137">이전 로드의 종료 날짜 및 시간을 현재 시작 날짜 및 시간으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-137">You use the ending date and time from the previous load as the current starting date and time.</span></span> <span data-ttu-id="db177-138">증분 로드에 고정 간격을 사용하는 경우 Transact-SQL 또는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 식 언어의 `datetime` 함수를 사용하여 이 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-138">If you use a fixed interval for incremental loads, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span> <span data-ttu-id="db177-139">그렇지 않은 경우 실행 간 엔드포인트를 유지하고 SQL 실행 태스크 또는 스크립트 태스크를 사용하여 이전 엔드포인트를 로드해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db177-139">Otherwise, you might have to persist the endpoints between executions, and use an Execute SQL task or a Script task to load the previous endpoint.</span></span>  
  
-   <span data-ttu-id="db177-140">**종료 날짜 및 시간 계산**.</span><span class="sxs-lookup"><span data-stu-id="db177-140">**Calculating the ending date and time**.</span></span> <span data-ttu-id="db177-141">증분 로드에 고정 간격을 사용하는 경우 현재 종료 날짜 및 시간을 시작 날짜 및 시간의 오프셋으로 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-141">If you use a fixed interval for incremental loads, calculate the current ending date and time as an offset from the starting date and time.</span></span> <span data-ttu-id="db177-142">`datetime`Transact-sql 또는 식 언어의 함수를 사용 하 여이 값을 계산할 수 있습니다 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="db177-142">Again, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span>  
  
 <span data-ttu-id="db177-143">다음 절차에서는 변경 간격에 고정 간격을 사용하며 증분 로드 패키지가 예외 없이 매일 실행된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-143">In the following procedure, the change interval uses a fixed interval and assumes that the incremental load package is run daily without exception.</span></span> <span data-ttu-id="db177-144">그렇지 않으면 누락된 간격의 변경 데이터가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="db177-144">Otherwise, change data for missed intervals would be lost.</span></span> <span data-ttu-id="db177-145">간격의 시작 지점은 이틀 전 자정입니다. 즉, 24-48시간 전입니다.</span><span class="sxs-lookup"><span data-stu-id="db177-145">The starting point for the interval is midnight the day before yesterday, that is, between 24 and 48 hours ago.</span></span> <span data-ttu-id="db177-146">간격의 끝 지점은 어제 자정입니다. 즉, 0-24시간 전의 전날 밤입니다.</span><span class="sxs-lookup"><span data-stu-id="db177-146">The ending point for the interval is midnight yesterday, that is, the previous night, between 0 and 24 hours ago.</span></span>  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a><span data-ttu-id="db177-147">캡처 간격의 시작 지점 및 끝 지점을 계산하려면</span><span class="sxs-lookup"><span data-stu-id="db177-147">To calculate the starting point and ending point for the capture interval</span></span>  
  
1.  <span data-ttu-id="db177-148">**디자이너의** 제어 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 패키지에 SQL 실행 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-148">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add an Execute SQL Task to the package.</span></span>  
  
2.  <span data-ttu-id="db177-149">**SQL 실행 태스크 편집기**의 **일반** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-149">Open the **Execute SQL Task Editor**, and on the **General** page of the editor, select the following options:</span></span>  
  
    1.  <span data-ttu-id="db177-150">**ResultSet**에 **단일 행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-150">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="db177-151">원본 데이터베이스에 대한 올바른 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-151">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="db177-152">**SQLSourceType**에 **직접 입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-152">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="db177-153">**SQLStatement**에 다음 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-153">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  <span data-ttu-id="db177-154">**SQL 실행 태스크 편집기** 의 **결과 집합**페이지에서 ExtractStartTime 결과를 ExtractStartTime 패키지 변수에 매핑하고 ExtractEndTime 결과를 ExtractEndTime 패키지 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="db177-154">On the **Result Set** page of the **Execute SQL Task Editor**, map the ExtractStartTime result to the ExtractStartTime package variable, and map the ExtractEndTime result to the ExtractEndTime package variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="db177-155">식을 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 변수의 값을 설정하면 변수의 값에 액세스할 때마다 식이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="db177-155">When you use an expression to set the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, the expression is evaluated every time that the value of the variable is accessed.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="db177-156">다음 단계</span><span class="sxs-lookup"><span data-stu-id="db177-156">Next Step</span></span>  
 <span data-ttu-id="db177-157">변경 범위의 시작 지점 및 끝 지점을 계산한 후 다음 단계는 변경 데이터가 준비되었는지 여부를 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db177-157">After you calculate the starting point and ending point for a range of changes, the next step is to determine whether the change data is ready.</span></span>  
  
 <span data-ttu-id="db177-158">**다음 항목:** [변경 데이터의 준비 여부 확인](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="db177-158">**Next topic:** [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db177-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db177-159">See Also</span></span>  
 <span data-ttu-id="db177-160">[패키지에서 변수 사용](../use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="db177-160">[Use Variables in Packages](../use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="db177-161">[Integration Services&#40;SSIS&#41; 식](../expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="db177-161">[Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="db177-162">[SQL 실행 태스크](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="db177-162">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="db177-163">스크립트 태스크</span><span class="sxs-lookup"><span data-stu-id="db177-163">Script Task</span></span>](../control-flow/script-task.md)  
  
  
