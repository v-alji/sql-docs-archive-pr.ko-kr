---
title: 변경 데이터의 준비 여부 확인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],determining readiness
ms.assetid: 04935f35-96cc-4d70-a250-0fd326f8daff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e672440938e366e53ba150f65d7bcd6aed8a58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740215"
---
# <a name="determine-whether-the-change-data-is-ready"></a><span data-ttu-id="dc25c-102">변경 데이터의 준비 여부 확인</span><span class="sxs-lookup"><span data-stu-id="dc25c-102">Determine Whether the Change Data Is Ready</span></span>
  <span data-ttu-id="dc25c-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 제어 흐름에서 두 번째 태스크는 선택한 간격에 대한 변경 데이터가 준비되었는지 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the second task is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="dc25c-104">비동기 캡처 프로세스에서 선택한 엔드포인트까지 변경 내용을 아직 다 처리하지 않았을 수 있기 때문에 이 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-104">This step is necessary because the asynchronous capture process might not yet have processed all the changes up to the selected endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc25c-105">제어 흐름에 대한 첫 번째 태스크는 변경 간격의 엔드포인트를 계산하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-105">The first task for the control flow is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="dc25c-106">이 태스크에 대한 자세한 내용은 [변경 데이터의 간격 지정](specify-an-interval-of-change-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc25c-106">For more information about this task, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span> <span data-ttu-id="dc25c-107">제어 흐름 디자인의 전체 프로세스에 대한 설명은 [데이터 캡처 변경&#40;SSIS&#41;](change-data-capture-ssis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc25c-107">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="understanding-the-components-of-the-solution"></a><span data-ttu-id="dc25c-108">솔루션의 구성 요소 이해</span><span class="sxs-lookup"><span data-stu-id="dc25c-108">Understanding the Components of the Solution</span></span>  
 <span data-ttu-id="dc25c-109">이 항목에 설명된 솔루션에서는 다음과 같은 4개의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 구성 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-109">The solution described in this topic uses 4 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="dc25c-110">SQL 실행 태스크의 출력을 반복적으로 평가하는 For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="dc25c-110">A For Loop container that repeatedly evaluates the output of an Execute SQL Task.</span></span>  
  
-   <span data-ttu-id="dc25c-111">변경 데이터 캡처 프로세스에서 유지하는 특수 테이블을 쿼리한 다음 이 정보를 사용하여 데이터가 준비되었는지 여부를 확인하는 SQL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="dc25c-111">An Execute SQL task that queries special tables that the change data capture process maintains and then uses this information to determine whether data is ready.</span></span>  
  
-   <span data-ttu-id="dc25c-112">데이터가 준비되지 않았을 때 처리에서 지연을 구현하는 구성 요소.</span><span class="sxs-lookup"><span data-stu-id="dc25c-112">A component that implements a delay in processing when the data is not ready.</span></span> <span data-ttu-id="dc25c-113">이 구성 요소는 스크립트 태스크 또는 SQL 실행 태스크일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-113">This can be either a Script task or an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="dc25c-114">SQL 실행 태스크에서 오류 또는 시간 초과 상태를 나타내는 값을 반환할 때 오류 또는 시간 초과를 보고하는 구성 요소(옵션)</span><span class="sxs-lookup"><span data-stu-id="dc25c-114">Optionally, a component that reports an error or a timeout when the Execute SQL task returns a value that indicates an error or a timeout condition.</span></span>  
  
 <span data-ttu-id="dc25c-115">이러한 구성 요소에서는 여러 패키지 변수의 값을 설정하거나 읽어 루프 내에서 그리고 나중에는 패키지에서 실행의 흐름을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-115">These components set or read the values of several package variables to control the flow of execution inside the loop and later in the package.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="dc25c-116">패키지 변수를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-116">To set up package variables</span></span>  
  
1.  <span data-ttu-id="dc25c-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **변수** 창에서 다음 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="dc25c-118">SQL 실행 태스크에서 반환하는 상태 값을 보관할 integer 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-118">Create a variable with an integer data type to hold the status value returned by the Execute SQL task.</span></span>  
  
         <span data-ttu-id="dc25c-119">이 예에서는 초기 값이 0인 변수 이름으로 DataReady를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-119">This example uses the variable name, DataReady, with an initial value of 0.</span></span>  
  
    2.  <span data-ttu-id="dc25c-120">데이터가 준비되지 않았을 때 지연할 시간을 보관할 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-120">Create a variable to hold the period of time to delay when data is not ready.</span></span> <span data-ttu-id="dc25c-121">스크립트 태스크를 사용하여 지연을 구현하려는 경우 변수의 데이터 형식은 integer여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-121">If you plan to use a Script task to implement the delay, the variable should have an integer data type integer.</span></span> <span data-ttu-id="dc25c-122">WAITFOR 문이 있는 SQL 실행 태스크를 사용하려는 경우에는 "00:00:10"과 같은 값을 허용하기 위해 변수의 데이터 형식이 string이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-122">If you plan to use an Execute SQL task with a WAITFOR statement, the variable should have a string data type to accept values such as "00:00:10".</span></span>  
  
         <span data-ttu-id="dc25c-123">이 예에서는 초기 값이 10인 변수 이름으로 DelaySeconds를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-123">This example uses the variable name, DelaySeconds, with an initial value of 10.</span></span>  
  
    3.  <span data-ttu-id="dc25c-124">루프의 현재 반복을 보관할 integer 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-124">Create a variable with an integer data type to hold the current iteration of the loop.</span></span>  
  
         <span data-ttu-id="dc25c-125">이 예에서는 초기 값이 0인 변수 이름으로 TimeoutCount를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-125">This example uses the variable name, TimeoutCount, with an initial value of 0.</span></span>  
  
    4.  <span data-ttu-id="dc25c-126">시간 초과 상태를 보고하기 전에 루프에서 데이터를 테스트해야 하는 횟수를 지정하는 integer 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-126">Create a variable with an integer data type to specify the number of times that the loop should test for data before reporting a timeout condition.</span></span>  
  
         <span data-ttu-id="dc25c-127">이 예에서는 초기 값이 20인 변수 이름으로 TimeoutCeiling을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-127">This example uses the variable name, TimeoutCeiling, with an initial value of 20.</span></span>  
  
    5.  <span data-ttu-id="dc25c-128">(옵션) 변경 데이터의 첫 번째 로드를 나타내는 데 사용할 수 있는 integer 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-128">(Optional) Create a variable with an integer data type that you can use to indicate the first load of change data.</span></span>  
  
         <span data-ttu-id="dc25c-129">이 예에서는 변수 이름으로 IntervalID를 사용하고 값 0만 검사하여 초기 로드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-129">This example uses the variable name, IntervalID, and checks only for a value of 0 to indicate the initial load.</span></span>  
  
## <a name="configuring-a-for-loop-container"></a><span data-ttu-id="dc25c-130">For 루프 컨테이너 구성</span><span class="sxs-lookup"><span data-stu-id="dc25c-130">Configuring a For Loop Container</span></span>  
 <span data-ttu-id="dc25c-131">변수가 설정되면 For 루프 컨테이너를 첫 번째 구성 요소로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-131">With the variables set, the For Loop container is the first component to be added.</span></span>  
  
#### <a name="to-configure-a-for-loop-container-to-wait-until-change-data-is-ready"></a><span data-ttu-id="dc25c-132">변경 데이터가 준비될 때까지 대기하도록 For 루프 컨테이너를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-132">To configure a For Loop container to wait until change data is ready</span></span>  
  
1.  <span data-ttu-id="dc25c-133">**디자이너의** 제어 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 제어 흐름에 For 루프 컨테이너를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-133">On the **Control Flow** tab of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a For Loop container to the control flow.</span></span>  
  
2.  <span data-ttu-id="dc25c-134">간격의 엔드포인트를 계산하는 SQL 실행 태스크를 For 루프 컨테이너에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-134">Connect the Execute SQL Task that calculates the endpoints of the interval to the For Loop container.</span></span>  
  
3.  <span data-ttu-id="dc25c-135">**For 루프 편집기**에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-135">In the **For Loop Editor**, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-136">**InitExpression**에 `@DataReady = 0`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-136">For **InitExpression**, enter `@DataReady = 0`.</span></span>  
  
         <span data-ttu-id="dc25c-137">이 식은 루프 변수의 초기 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-137">This expression sets the initial value of the loop variable.</span></span>  
  
    2.  <span data-ttu-id="dc25c-138">**EvalExpression**에 `@DataReady == 0`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-138">For **EvalExpression**m, enter `@DataReady == 0`.</span></span>  
  
         <span data-ttu-id="dc25c-139">이 식이 **False**로 평가되면 실행이 루프 밖으로 전달되고 증분 로드가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-139">When this expression evaluates to **False**, execution passes out of the loop and the incremental load starts.</span></span>  
  
## <a name="configuring-the-execute-sql-task-that-queries-for-change-data"></a><span data-ttu-id="dc25c-140">변경 데이터를 쿼리하는 SQL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="dc25c-140">Configuring the Execute SQL Task That Queries for Change Data</span></span>  
 <span data-ttu-id="dc25c-141">For 루프 컨테이너 내에서 SQL 실행 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-141">Inside the For Loop container, you add an Execute SQL task.</span></span> <span data-ttu-id="dc25c-142">이 태스크는 변경 데이터 캡처 프로세스에서 데이터베이스에 유지하는 테이블을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-142">This task queries the tables that the change data capture process maintains in the database.</span></span> <span data-ttu-id="dc25c-143">이 쿼리의 결과는 변경 데이터가 준비되었는지 여부를 나타내는 상태 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-143">The result of this query is a status value that indicates whether the change data is ready.</span></span>  
  
 <span data-ttu-id="dc25c-144">다음 표에서 첫 번째 열은 샘플 Transact-SQL 쿼리에 의해 SQL 실행 태스크에서 반환되는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-144">In the following table, the first column shows the values returned from the Execute SQL task by the sample Transact-SQL query.</span></span> <span data-ttu-id="dc25c-145">두 번째 열은 다른 구성 요소에서 이러한 값에 응답하는 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-145">The second column shows how the other components respond to these values.</span></span>  
  
|<span data-ttu-id="dc25c-146">Return Value</span><span class="sxs-lookup"><span data-stu-id="dc25c-146">Return Value</span></span>|<span data-ttu-id="dc25c-147">의미</span><span class="sxs-lookup"><span data-stu-id="dc25c-147">Meaning</span></span>|<span data-ttu-id="dc25c-148">응답</span><span class="sxs-lookup"><span data-stu-id="dc25c-148">Response</span></span>|  
|------------------|-------------|--------------|  
|<span data-ttu-id="dc25c-149">0</span><span class="sxs-lookup"><span data-stu-id="dc25c-149">0</span></span>|<span data-ttu-id="dc25c-150">변경 데이터가 준비되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-150">Indicates that the change data is not ready.</span></span><br /><br /> <span data-ttu-id="dc25c-151">선택한 간격의 끝 지점 뒤에 오는 변경 데이터 캡처 레코드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-151">There are no change data capture records later than the ending point of the selected interval.</span></span>|<span data-ttu-id="dc25c-152">지연을 구현하는 구성 요소에서 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-152">Execution continues with the component that implements a delay.</span></span> <span data-ttu-id="dc25c-153">그런 다음 제어가 For 루프 컨테이너로 반환되어 반환되는 값이 0인 한 SQL 실행 태스크가 계속 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-153">Then control returns to the For Loop container, which continues to check the Execute SQL task as long as the value returned is 0.</span></span>|  
|<span data-ttu-id="dc25c-154">1</span><span class="sxs-lookup"><span data-stu-id="dc25c-154">1</span></span>|<span data-ttu-id="dc25c-155">변경 데이터가 전체 간격에 대해 캡처되지 않았거나 삭제되었음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-155">Might indicate that the change data has not been captured for the complete interval, or that it has been deleted.</span></span> <span data-ttu-id="dc25c-156">이는 오류 상태로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-156">This is treated as an error condition.</span></span><br /><br /> <span data-ttu-id="dc25c-157">선택한 간격의 시작 지점 앞에 오는 변경 데이터 캡처 레코드가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-157">There are no change data capture records earlier than the starting point of the selected interval</span></span>|<span data-ttu-id="dc25c-158">오류를 기록하는 선택적 구성 요소에서 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-158">Execution continues with the optional component that logs the error.</span></span>|  
|<span data-ttu-id="dc25c-159">2</span><span class="sxs-lookup"><span data-stu-id="dc25c-159">2</span></span>|<span data-ttu-id="dc25c-160">데이터가 준비되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-160">Indicates that data is ready.</span></span><br /><br /> <span data-ttu-id="dc25c-161">선택한 간격의 시작 지점 앞에 오고 끝 지점 뒤에 오는 변경 데이터 캡처 레코드가 모두 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-161">There are change data capture records that are both earlier than the starting point and later than the ending point of the selected interval.</span></span>|<span data-ttu-id="dc25c-162">실행이 For 루프 밖으로 전달되고 증분 로드가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-162">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="dc25c-163">3</span><span class="sxs-lookup"><span data-stu-id="dc25c-163">3</span></span>|<span data-ttu-id="dc25c-164">사용 가능한 모든 변경 데이터의 초기 로드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-164">Indicates the initial load of all available change data.</span></span><br /><br /> <span data-ttu-id="dc25c-165">조건부 논리는 이 용도로만 사용되는 특수 패키지 변수에서 이 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-165">The conditional logic obtains this value from a special package variable that is used only for this purpose.</span></span>|<span data-ttu-id="dc25c-166">실행이 For 루프 밖으로 전달되고 증분 로드가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-166">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="dc25c-167">5</span><span class="sxs-lookup"><span data-stu-id="dc25c-167">5</span></span>|<span data-ttu-id="dc25c-168">TimeoutCeiling에 도달했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-168">Indicates that the TimeoutCeiling has been reached.</span></span><br /><br /> <span data-ttu-id="dc25c-169">루프에서 지정한 횟수만큼 데이터를 테스트했으며 데이터를 여전히 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-169">The loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="dc25c-170">이 테스트나 유사한 테스트를 사용하지 않으면 패키지가 무기한 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-170">Without this test or a similar test, the package might run indefinitely.</span></span>|<span data-ttu-id="dc25c-171">시간 초과를 기록하는 선택적 구성 요소에서 실행이 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-171">Execution continues with the optional component that logs the timeout.</span></span>|  
  
#### <a name="to-configure-an-execute-sql-task-to-query-whether-change-data-is-ready"></a><span data-ttu-id="dc25c-172">변경 데이터가 준비되었는지 여부를 쿼리하는 SQL 실행 태스크를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-172">To configure an Execute SQL task to query whether change data is ready</span></span>  
  
1.  <span data-ttu-id="dc25c-173">For 루프 컨테이너 내에서 SQL 실행 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-173">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="dc25c-174">**SQL 실행 태스크 편집기**의 **일반** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-174">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-175">**ResultSet**에 **단일 행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-175">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="dc25c-176">원본 데이터베이스에 대한 올바른 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-176">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="dc25c-177">**SQLSourceType**에 **직접 입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-177">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="dc25c-178">**SQLStatement**에 다음 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-178">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @DataReady int, @TimeoutCount int  
  
        if not exists (select tran_end_time from cdc.lsn_time_mapping  
                where tran_end_time > ?  )  
            select @DataReady = 0  
        else  
            if ? = 0  
                select @DataReady = 3   
        else  
            if not exists (select tran_end_time from cdc.lsn_time_mapping  
                    where tran_end_time <= ? )  
                select @DataReady = 1   
        else  
            select @DataReady = 2  
  
        select @TimeoutCount = ?  
        if (@DataReady = 0)  
            select @TimeoutCount = @TimeoutCount + 1  
        else  
            select @TimeoutCount = 0  
  
        if (@TimeoutCount > ?)  
            select @DataReady = 5  
  
        select @DataReady as DataReady, @TimeoutCount as TimeoutCount  
  
        ```  
  
3.  <span data-ttu-id="dc25c-179">**SQL 실행 태스크 편집기** 의 **매개 변수 매핑**페이지에서 다음 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-179">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, make the following mappings:</span></span>  
  
    1.  <span data-ttu-id="dc25c-180">ExtractEndTime 변수를 매개 변수 0에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-180">Map the ExtractEndTime variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="dc25c-181">IntervalID 변수를 매개 변수 1에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-181">Map the IntervalID variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="dc25c-182">ExtractStartTime 변수를 매개 변수 2에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-182">Map the ExtractStartTime variable to parameter 2.</span></span>  
  
    4.  <span data-ttu-id="dc25c-183">TimeoutCount 변수를 매개 변수 3에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-183">Map the TimeoutCount variable to parameter 3.</span></span>  
  
    5.  <span data-ttu-id="dc25c-184">TimeoutCeiling 변수를 매개 변수 4에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-184">Map the TimeoutCeiling variable to parameter 4.</span></span>  
  
4.  <span data-ttu-id="dc25c-185">**SQL 실행 태스크 편집기** 의 **결과 집합**페이지에서 DataReady 결과를 DataReady 변수에 매핑하고 TimeoutCount 결과를 TimeoutCount 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-185">On the **Result Set** page of the **Execute SQL Task Editor**, map the DataReady result to the DataReady variable, and the TimeoutCount result to the TimeoutCount variable.</span></span>  
  
## <a name="waiting-until-the-change-data-is-ready"></a><span data-ttu-id="dc25c-186">변경 데이터가 준비될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="dc25c-186">Waiting Until the Change Data Is Ready</span></span>  
 <span data-ttu-id="dc25c-187">변경 데이터가 준비되지 않은 경우 지연을 구현하는 여러 가지 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-187">You can use one of several methods to implement a delay when the change data is not ready.</span></span> <span data-ttu-id="dc25c-188">다음 두 절차에서는 스크립트 태스크나 SQL 실행 태스크를 사용하여 지연을 구현하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-188">The following two procedures illustrate how to use a Script task or an Execute SQL task to implement the delay.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc25c-189">미리 컴파일된 스크립트는 SQL 실행 태스크보다 적은 오버헤드를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-189">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-a-script-task"></a><span data-ttu-id="dc25c-190">스크립트 태스크를 사용하여 지연을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-190">To implement a delay by using a Script task</span></span>  
  
1.  <span data-ttu-id="dc25c-191">For 루프 컨테이너 내에서 스크립트 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-191">Inside the For Loop container, add a Script task.</span></span>  
  
2.  <span data-ttu-id="dc25c-192">변경 데이터가 준비되었는지 여부를 확인하기 위해 쿼리하는 SQL 실행 태스크를 새 스크립트 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-192">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
3.  <span data-ttu-id="dc25c-193">SQL 실행 태스크를 스크립트 태스크에 연결하는 선행 제약 조건을 위해 **선행 제약 조건 편집기** 를 열고 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-193">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-194">**평가 작업**에 **식 및 제약 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-194">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc25c-195">**값**에 **성공**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-195">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc25c-196">**성공** 의 제약 조건 값은 이전 태스크의 성공을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-196">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="dc25c-197">이 경우에는 SQL 실행 태스크의 성공입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-197">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc25c-198">**식**에 `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-198">For **Expression**, enter `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`.</span></span>  
  
    4.  <span data-ttu-id="dc25c-199">**논리적 AND. 모든 제약 조건이 True가 되어야 합니다**가 선택되지 않은 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-199">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
4.  <span data-ttu-id="dc25c-200">**스크립트 태스크 편집기**의 **스크립트** 페이지에 있는 **ReadOnlyVariables**에 대해 목록에서 **User::DelaySeconds** 정수 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-200">In the **Script Task Editor**, on the **Script** page, for **ReadOnlyVariables**, select the **User::DelaySeconds** integer variable from the list.</span></span>  
  
5.  <span data-ttu-id="dc25c-201">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 **스크립트 편집** 을 클릭하여 스크립트 개발 환경을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-201">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="dc25c-202">Main 프로시저에 다음 코드 행 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-202">In the Main procedure, enter one of the following lines of code:</span></span>  
  
    -   <span data-ttu-id="dc25c-203">C#에서 프로그래밍하는 경우 다음 코드 행을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-203">If you are programming in C#, enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep((int)Dts.Variables["DelaySeconds"].Value * 1000);  
        ```  
  
         <span data-ttu-id="dc25c-204">\- 또는-</span><span class="sxs-lookup"><span data-stu-id="dc25c-204">\- or -</span></span>  
  
    -   <span data-ttu-id="dc25c-205">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서 프로그래밍하는 경우 다음 코드 행을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-205">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep(Ctype(Dts.Variables("DelaySeconds").Value, Integer) * 1000)  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="dc25c-206">`Thread.Sleep` 메서드는 밀리초 단위로 지정된 인수를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-206">The `Thread.Sleep` method expects an argument that is specified in milliseconds.</span></span>  
  
7.  <span data-ttu-id="dc25c-207">스크립트 실행에서 `DtsExecResult.Success`를 반환하는 기본 코드 행을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-207">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
8.  <span data-ttu-id="dc25c-208">스크립트 개발 환경 및 **스크립트 태스크 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-208">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-an-execute-sql-task"></a><span data-ttu-id="dc25c-209">SQL 실행 태스크를 사용하여 지연을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-209">To implement a delay by using an Execute SQL task</span></span>  
  
1.  <span data-ttu-id="dc25c-210">For 루프 컨테이너 내에서 SQL 실행 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-210">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="dc25c-211">변경 데이터가 준비되었는지 여부를 확인하기 위해 쿼리하는 SQL 실행 태스크를 새 SQL 실행 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-211">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Execute SQL task.</span></span>  
  
3.  <span data-ttu-id="dc25c-212">두 SQL 실행 태스크를 연결하는 선행 제약 조건을 위해 **선행 제약 조건 편집기** 를 열고 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-212">For the precedence constraint that connects the two Execute SQL tasks, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-213">**평가 작업**에 **식 및 제약 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-213">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc25c-214">**값**에 **성공**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-214">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc25c-215">**성공** 의 제약 조건 값은 이전 SQL 실행 태스크의 성공을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-215">The constraint value of **Success** refers to the success of the previous Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc25c-216">**식**에 `@DataReady == 0`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-216">For **Expression**, enter `@DataReady == 0`.</span></span>  
  
    4.  <span data-ttu-id="dc25c-217">**논리적 AND. 모든 제약 조건이 True가 되어야 합니다**가 선택되지 않은 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-217">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="dc25c-218">이 옵션을 선택하려면 두 가지 조건인 제약 조건과 식이 모두 true여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-218">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
4.  <span data-ttu-id="dc25c-219">**SQL 실행 태스크 편집기**의 **일반** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-219">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-220">**ResultSet**에 **단일 행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-220">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="dc25c-221">원본 데이터베이스에 대한 올바른 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-221">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="dc25c-222">**SQLSourceType**에 **직접 입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-222">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="dc25c-223">**SQLStatement**에 다음 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-223">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        WAITFOR DELAY ?  
  
        ```  
  
5.  <span data-ttu-id="dc25c-224">편집기의 **매개 변수 매핑** 페이지에서 DelaySeconds 문자열 변수를 매개 변수 0에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-224">On the **Parameter Mapping** page of the editor, map the DelaySeconds string variable to parameter 0.</span></span>  
  
## <a name="handling-an-error-condition"></a><span data-ttu-id="dc25c-225">오류 상태 처리</span><span class="sxs-lookup"><span data-stu-id="dc25c-225">Handling an Error Condition</span></span>  
 <span data-ttu-id="dc25c-226">루프 내에 추가 구성 요소를 구성하여 오류 또는 시간 초과 상태를 기록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-226">You can optionally configure an additional component inside the loop to log an error or a timeout condition:</span></span>  
  
-   <span data-ttu-id="dc25c-227">DataReady 변수 값이 1인 경우 이 구성 요소가 오류 상태를 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-227">This component can log an error condition when the value of the DataReady variable = 1.</span></span> <span data-ttu-id="dc25c-228">이 값은 선택한 간격 시작 전에 사용 가능한 변경 데이터가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-228">This value indicates that there is no available change data before the start of the selected interval.</span></span>  
  
-   <span data-ttu-id="dc25c-229">TimeoutCeiling 변수 값에 도달할 경우 이 구성 요소는 시간 초과 상태를 기록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-229">This component can also log a timeout condition when the value of the TimeoutCeiling variable is reached.</span></span> <span data-ttu-id="dc25c-230">이 값은 루프에서 지정한 횟수만큼 데이터를 테스트했으며 데이터를 여전히 사용할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-230">This value indicates the loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="dc25c-231">이 테스트나 유사한 테스트를 사용하지 않으면 패키지가 무기한 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-231">Without this test or a similar test, the package might run indefinitely.</span></span>  
  
#### <a name="to-configure-an-optional-script-task-to-log-an-error-condition"></a><span data-ttu-id="dc25c-232">오류 상태를 기록하는 선택적 스크립트 태스크를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="dc25c-232">To configure an optional Script task to log an error condition</span></span>  
  
1.  <span data-ttu-id="dc25c-233">로그에 메시지를 기록하여 오류 또는 시간 초과를 보고하려는 경우 패키지에 대한 로깅을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-233">If you want to report the error or timeout by writing a message to the log, configure logging for the package.</span></span> <span data-ttu-id="dc25c-234">자세한 내용은 [SQL Server Data Tools에서 패키지 로깅 사용](../enable-package-logging-in-sql-server-data-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc25c-234">For more information, see [Enable Package Logging in SQL Server Data Tools](../enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
2.  <span data-ttu-id="dc25c-235">For 루프 컨테이너 내에서 스크립트 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-235">Inside the For Loop container, add a Script task.</span></span>  
  
3.  <span data-ttu-id="dc25c-236">변경 데이터가 준비되었는지 여부를 확인하기 위해 쿼리하는 SQL 실행 태스크를 새 스크립트 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-236">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
4.  <span data-ttu-id="dc25c-237">SQL 실행 태스크를 스크립트 태스크에 연결하는 선행 제약 조건을 위해 **선행 제약 조건 편집기** 를 열고 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-237">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="dc25c-238">**평가 작업**에 **식 및 제약 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-238">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="dc25c-239">**값**에 **성공**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-239">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="dc25c-240">**성공** 의 제약 조건 값은 이전 태스크의 성공을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-240">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="dc25c-241">이 경우에는 SQL 실행 태스크의 성공입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-241">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="dc25c-242">**식**에 `@DataReady == 1 || @DataReady == 5`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-242">For **Expression**, enter `@DataReady == 1 || @DataReady == 5`.</span></span>  
  
    4.  <span data-ttu-id="dc25c-243">**논리적 AND. 모든 제약 조건이 True가 되어야 합니다**가 선택되지 않은 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-243">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="dc25c-244">이 옵션을 선택하려면 두 가지 조건인 제약 조건과 식이 모두 true여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-244">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
5.  <span data-ttu-id="dc25c-245">**스크립트 태스크 편집기**에서 편집기의 **스크립트** 페이지에 있는 **ReadOnlyVariables**에 대해 목록에서 **User::DataReady** 및 **User::ExtractStartTime** 을 선택하여 해당 값을 스크립트에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-245">In the **Script Task Editor**, on the **Script** page of the editor, for **ReadOnlyVariables**, select **User::DataReady** and **User::ExtractStartTime** from the list to make their values available to the script.</span></span>  
  
     <span data-ttu-id="dc25c-246">로그에 기록하는 정보에 특정 시스템 변수(예: System::PackageName)의 정보를 포함하려는 경우 해당 변수도 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-246">If you want to include information from certain system variables (for example, System::PackageName) in the information that you write to the log, select those variables also.</span></span>  
  
6.  <span data-ttu-id="dc25c-247">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 **스크립트 편집** 을 클릭하여 스크립트 개발 환경을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-247">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
7.  <span data-ttu-id="dc25c-248">Main 프로시저에 `Dts.Log` 메서드를 호출하여 오류를 기록하거나 `Dts.Events` 인터페이스의 메서드 중 하나를 호출하여 이벤트를 발생시키는 코드를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-248">In the Main procedure, enter code to log an error by calling the `Dts.Log` method, or to raise an event by calling one of the methods of the `Dts.Events` interface.</span></span> <span data-ttu-id="dc25c-249">`Dts.TaskResult = Dts.Results.Failure`를 반환하여 패키지에 오류를 알립니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-249">Inform the package of the error by returning `Dts.TaskResult = Dts.Results.Failure`.</span></span>  
  
     <span data-ttu-id="dc25c-250">다음 샘플에서는 로그에 메시지를 기록하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-250">The following sample shows how to write a message to the log.</span></span> <span data-ttu-id="dc25c-251">자세한 내용은 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md), [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md)및 [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc25c-251">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md), [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md), and [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>  
  
    ```  
    ' User variables.  
    Dim dataReady As Integer = _  
      CType(Dts.Variables("DataReady").Value, Integer)  
    Dim extractStartTime As Date = _  
      CType(Dts.Variables("ExtractStartTime").Value, DateTime)  
  
    ' System variables.  
    Dim packageName As String = _  
      Dts.Variables("PackageName").Value.ToString()  
    Dim executionStartTime As Date = _  
      CType(Dts.Variables("StartTime").Value, DateTime)  
  
    Dim eventMessage As New System.Text.StringBuilder()  
  
    If dataReady = 1 OrElse dataReady = 5 Then  
  
      If dataReady = 1 Then  
        eventMessage.AppendLine("Start Time Error")  
      Else  
        eventMessage.AppendLine("Timeout Error")  
      End If  
  
      With eventMessage  
        .Append("The package ")  
        .Append(packageName)  
        .Append(" started at ")  
        .Append(executionStartTime.ToString())  
        .Append(" and ended at ")  
        .AppendLine(DateTime.Now().ToString())  
        If dataReady = 1 Then  
          .Append("The specified ExtractStartTime was ")  
          .AppendLine(extractStartTime.ToString())  
        End If  
      End With  
  
      System.Windows.Forms.MessageBox.Show(eventMessage.ToString())  
  
      Dts.Log(eventMessage.ToString(), 0, Nothing)  
  
      Dts.TaskResult = Dts.Results.Failure  
  
    Else  
  
      Dts.TaskResult = Dts.Results.Success  
  
    End If  
  
    ```  
  
8.  <span data-ttu-id="dc25c-252">스크립트 개발 환경 및 **스크립트 태스크 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-252">Close the script development environment and the **Script Task Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="dc25c-253">다음 단계</span><span class="sxs-lookup"><span data-stu-id="dc25c-253">Next Step</span></span>  
 <span data-ttu-id="dc25c-254">변경 데이터가 준비되었는지 확인한 후 다음 단계는 변경 데이터에 대한 쿼리를 준비하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc25c-254">After you determine that change data is ready, the next step is to prepare to query for the change data.</span></span>  
  
 <span data-ttu-id="dc25c-255">**다음 항목:** [변경 데이터에 대한 쿼리 준비](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="dc25c-255">**Next topic:** [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>  
  
  
