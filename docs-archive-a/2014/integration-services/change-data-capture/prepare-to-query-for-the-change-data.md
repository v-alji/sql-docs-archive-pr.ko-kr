---
title: 변경 데이터에 대한 쿼리 준비 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ab732389d5a747c596472f14f5229361dd46275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646582"
---
# <a name="prepare-to-query-for-the-change-data"></a><span data-ttu-id="60e3e-102">변경 데이터에 대한 쿼리 준비</span><span class="sxs-lookup"><span data-stu-id="60e3e-102">Prepare to Query for the Change Data</span></span>
  <span data-ttu-id="60e3e-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 제어 흐름에서 세 번째이자 마지막 태스크는 변경 데이터 쿼리를 준비하고 데이터 흐름 태스크를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to prepare to query for the change data and add a Data Flow task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60e3e-104">제어 흐름에 대한 두 번째 태스크는 선택한 간격에 대한 변경 데이터가 준비되었는지 확인하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-104">The second task for the control flow is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="60e3e-105">이 태스크에 대한 자세한 내용은 [변경 데이터의 준비 여부 확인](determine-whether-the-change-data-is-ready.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60e3e-105">For more information about this task, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span> <span data-ttu-id="60e3e-106">제어 흐름 디자인의 전체 프로세스에 대한 설명은 [데이터 캡처 변경&#40;SSIS&#41;](change-data-capture-ssis.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60e3e-106">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations"></a><span data-ttu-id="60e3e-107">디자인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="60e3e-107">Design Considerations</span></span>  
 <span data-ttu-id="60e3e-108">변경 데이터를 검색하려면 간격의 엔드포인트를 입력 매개 변수로 받아 지정한 간격에 대한 변경 데이터를 반환하는 Transact-SQL 테이블 반환 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-108">To retrieve the change data, you will call a Transact-SQL table-valued function that accepts the endpoints of the interval as input parameters and returns change data for the specified interval.</span></span> <span data-ttu-id="60e3e-109">데이터 흐름의 원본 구성 요소에서 이 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-109">A source component in the data flow calls this function.</span></span> <span data-ttu-id="60e3e-110">이 원본 구성 요소에 대한 자세한 내용은 [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60e3e-110">For information about this source component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
 <span data-ttu-id="60e3e-111">OLE DB 원본, ADO 원본 및 ADO NET 원본을 비롯하여 가장 자주 사용되는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소는 테이블 반환 함수에 대한 매개 변수 정보를 파생시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-111">The most frequently used [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source components, including the OLE DB source, the ADO source, and the ADO NET source, cannot derive parameter information for a table-valued function.</span></span> <span data-ttu-id="60e3e-112">따라서 대부분의 원본은 매개 변수가 있는 함수를 직접 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-112">Therefore, most sources cannot call a parameterized function directly.</span></span>  
  
 <span data-ttu-id="60e3e-113">함수에 입력 매개 변수를 전달하는 데에는 두 개의 디자인 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-113">You have two design options for passing the input parameters to the function:</span></span>  
  
-   <span data-ttu-id="60e3e-114">**매개 변수가 있는 쿼리를 문자열로 조합**.</span><span class="sxs-lookup"><span data-stu-id="60e3e-114">**Assemble the parameterized query as a string**.</span></span> <span data-ttu-id="60e3e-115">스크립트 태스크나 SQL 실행 태스크를 사용하여 매개 변수 값이 문자열로 하드 코딩된 동적 SQL 문자열을 조합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-115">You can use a Script task or an Execute SQL task to assemble a dynamic SQL string with parameter values hard-coded into the string.</span></span> <span data-ttu-id="60e3e-116">그런 다음 이 문자열을 패키지 변수에 저장하고 이를 사용하여 원본 구성 요소의 SqlCommand 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-116">Then, you can store this string in a package variable and use it to set the SqlCommand property of a source component.</span></span> <span data-ttu-id="60e3e-117">원본 구성 요소에서 더 이상 매개 변수 정보를 필요로 하지 않기 때문에 이 방법이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-117">This approach succeeds because the source component no longer requires parameter information.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60e3e-118">미리 컴파일된 스크립트는 SQL 실행 태스크보다 적은 오버헤드를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-118">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="60e3e-119">**매개 변수가 있는 래퍼 사용**.</span><span class="sxs-lookup"><span data-stu-id="60e3e-119">**Use a parameterized wrapper**.</span></span> <span data-ttu-id="60e3e-120">매개 변수가 있는 저장 프로시저를 매개 변수가 있는 테이블 반환 함수를 호출하는 래퍼로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-120">Alternatively, you can create a parameterized stored procedure as a wrapper that calls the parameterized table-valued function.</span></span> <span data-ttu-id="60e3e-121">원본 구성 요소에서 저장 프로시저에 대한 매개 변수 정보를 파생시킬 수 있기 때문에 이 방법이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-121">This approach succeeds because a source component can successfully derive parameter information for a stored procedure.</span></span>  
  
 <span data-ttu-id="60e3e-122">이 항목에서는 첫 번째 디자인 옵션을 사용하여 매개 변수가 있는 쿼리를 문자열로 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-122">This topic uses the first design option and assembles a parameterized query as a string.</span></span>  
  
## <a name="preparing-the-query"></a><span data-ttu-id="60e3e-123">쿼리 준비</span><span class="sxs-lookup"><span data-stu-id="60e3e-123">Preparing the Query</span></span>  
 <span data-ttu-id="60e3e-124">입력 매개 변수의 값을 단일 쿼리 문자열로 연결하려면 먼저 쿼리에 필요한 패키지 변수를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-124">Before you can concatenate the values of the input parameters into a single query string, you have to set up the package variables that the query needs.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="60e3e-125">패키지 변수를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="60e3e-125">To set up package variables</span></span>  
  
-   <span data-ttu-id="60e3e-126">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **변수** 창에서 SQL 실행 태스크에서 반환하는 쿼리 문자열을 보관할 string 데이터 형식의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-126">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create a variable with a string data type to hold the query string returned by the Execute SQL Task.</span></span>  
  
     <span data-ttu-id="60e3e-127">이 예에서는 변수 이름으로 SqlDataQuery를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-127">This example uses the variable name, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="60e3e-128">패키지 변수가 만들어지면 스크립트 태스크나 SQL 실행 태스크를 사용하여 입력 매개 변수의 값을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-128">With the package variable created, you can use either a Script task or Execute SQL task to concatenate the values of the input parameters.</span></span> <span data-ttu-id="60e3e-129">다음 두 절차에서는 이러한 구성 요소를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-129">The following two procedures describe how to configure these components.</span></span>  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a><span data-ttu-id="60e3e-130">스크립트 태스크를 사용하여 쿼리 문자열을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="60e3e-130">To use a Script task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="60e3e-131">**제어 흐름** 탭에서 패키지의 For 루프 컨테이너 뒤에 스크립트 태스크를 추가하고 이 태스크에 For 루프 컨테이너를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-131">On the **Control Flow** tab, add a Script task to the package after the For Loop container and connect the For Loop container to the task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60e3e-132">이 절차에서는 패키지가 단일 테이블에서 증분 로드를 수행한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-132">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="60e3e-133">패키지가 여러 테이블에서 로드하며 여러 자식 패키지가 있는 부모 패키지를 포함하는 경우 이 태스크는 각 자식 패키지에 첫 번째 구성 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-133">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="60e3e-134">자세한 내용은 [여러 테이블의 증분 로드 수행](perform-an-incremental-load-of-multiple-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60e3e-134">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="60e3e-135">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-135">In the **Script Task Editor**, on the **Script** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="60e3e-136">**ReadOnlyVariables**에 대해 목록에서 **User::DataReady**, **User::ExtractStartTime**및 **User::ExtractEndTime** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-136">For **ReadOnlyVariables**, select **User::DataReady**, **User::ExtractStartTime**, and **User::ExtractEndTime** from the.</span></span>  
  
    2.  <span data-ttu-id="60e3e-137">**ReadWriteVariables**에 대해 목록에서 User::SqlDataQuery를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-137">For **ReadWriteVariables**, select User::SqlDataQuery from the list.</span></span>  
  
3.  <span data-ttu-id="60e3e-138">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 **스크립트 편집** 을 클릭하여 스크립트 개발 환경을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-138">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
4.  <span data-ttu-id="60e3e-139">Main 프로시저에 다음 코드 세그먼트 중 하나를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-139">In the Main procedure, enter one of the following code segments:</span></span>  
  
    -   <span data-ttu-id="60e3e-140">C#에서 프로그래밍하는 경우 다음 코드 행을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-140">If you are programming in C#, enter the following lines of code:</span></span>  
  
        ```  
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         <span data-ttu-id="60e3e-141">\- 또는-</span><span class="sxs-lookup"><span data-stu-id="60e3e-141">\- or -</span></span>  
  
    -   <span data-ttu-id="60e3e-142">[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]에서 프로그래밍하는 경우 다음 코드 행을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-142">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following lines of code:</span></span>  
  
        ```  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  <span data-ttu-id="60e3e-143">스크립트 실행에서 `DtsExecResult.Success`를 반환하는 기본 코드 행을 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-143">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
6.  <span data-ttu-id="60e3e-144">스크립트 개발 환경 및 **스크립트 태스크 편집기**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-144">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a><span data-ttu-id="60e3e-145">SQL 실행 태스크를 사용하여 쿼리 문자열을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="60e3e-145">To use an Execute SQL task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="60e3e-146">**제어 흐름** 탭에서 패키지의 For 루프 컨테이너 뒤에 SQL 실행 태스크를 추가하고 이 태스크에 For 루프 컨테이너를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-146">On the **Control Flow** tab, add an Execute SQL task to the package after the For Loop container and connect the For Loop container to this task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="60e3e-147">이 절차에서는 패키지가 단일 테이블에서 증분 로드를 수행한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-147">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="60e3e-148">패키지가 여러 테이블에서 로드하며 여러 자식 패키지가 있는 부모 패키지를 포함하는 경우 이 태스크는 각 자식 패키지에 첫 번째 구성 요소로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-148">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="60e3e-149">자세한 내용은 [여러 테이블의 증분 로드 수행](perform-an-incremental-load-of-multiple-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60e3e-149">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="60e3e-150">**SQL 실행 태스크 편집기**의 **일반** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-150">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="60e3e-151">**ResultSet**에 **단일 행**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-151">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="60e3e-152">원본 데이터베이스에 대한 올바른 연결을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-152">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="60e3e-153">**SQLSourceType**에 **직접 입력**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-153">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="60e3e-154">**SQLStatement**에 다음 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-154">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="60e3e-155">이 샘플의 `else` 절은 시작 날짜 및 시간에 대해 Null 값을 전달하여 변경 데이터의 초기 로드에 대한 쿼리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-155">The `else` clause in this sample generates a query for the initial load of change data by passing a null value for the starting date and time.</span></span> <span data-ttu-id="60e3e-156">이 샘플에서는 변경 데이터 캡처가 설정되기 전에 적용된 변경 내용도 데이터 웨어하우스에 업로드되어야 하는 시나리오를 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-156">This sample does not address the scenario in which changes that were made before change data capture was enabled also have to be uploaded to the data warehouse.</span></span>  
  
3.  <span data-ttu-id="60e3e-157">**SQL 실행 태스크 편집기** 의 **매개 변수 매핑**페이지에서 다음 매핑을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-157">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, do the following mapping:</span></span>  
  
    1.  <span data-ttu-id="60e3e-158">DataReady 변수를 매개 변수 0에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-158">Map the DataReady variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="60e3e-159">ExtractStartTime 변수를 매개 변수 1에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-159">Map the ExtractStartTime variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="60e3e-160">ExtractEndTime 변수를 매개 변수 2에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-160">Map the ExtractEndTime variable to parameter 2.</span></span>  
  
4.  <span data-ttu-id="60e3e-161">**SQL 실행 태스크 편집기** 의 **결과 집합**페이지에서 결과 이름을 SqlDataQuery 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-161">On the **Result Set** page of the **Execute SQL Task Editor**, map the Result Name to the SqlDataQuery variable.</span></span>  
  
     <span data-ttu-id="60e3e-162">결과 이름은 반환된 단일 열의 이름인 SqlDataQuery입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-162">The Result Name is the name of the single column that is returned, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="60e3e-163">이전 절차에서는 입력 매개 변수에 대한 하드 코딩된 문자열 값이 있는 쿼리 문자열을 준비하는 태스크를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-163">The previous procedures configure a task that prepares a query string with hard-coded string values for the input parameters.</span></span> <span data-ttu-id="60e3e-164">다음 코드는 이러한 쿼리 문자열의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-164">The following code is an example of such a query string:</span></span>  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a><span data-ttu-id="60e3e-165">데이터 흐름 태스크 추가</span><span class="sxs-lookup"><span data-stu-id="60e3e-165">Adding a Data Flow Task</span></span>  
 <span data-ttu-id="60e3e-166">패키지의 제어 흐름을 디자인하는 마지막 단계는 데이터 흐름 태스크를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-166">The last step in designing the control flow for the package is to add a Data Flow task.</span></span>  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a><span data-ttu-id="60e3e-167">데이터 흐름 태스크를 추가하고 제어 흐름을 완료하려면</span><span class="sxs-lookup"><span data-stu-id="60e3e-167">To add a Data Flow task and complete the control flow</span></span>  
  
-   <span data-ttu-id="60e3e-168">**제어 흐름** 탭에서 데이터 흐름 태스크를 추가하고 쿼리 문자열을 연결한 태스크를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-168">On the **Control Flow** tab, add a Data Flow task and connect the task that concatenated the query string.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="60e3e-169">다음 단계</span><span class="sxs-lookup"><span data-stu-id="60e3e-169">Next Step</span></span>  
 <span data-ttu-id="60e3e-170">쿼리 문자열을 준비하고 데이터 흐름 태스크를 구성한 후 다음 단계는 데이터베이스에서 변경 데이터를 검색할 테이블 반환 함수를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60e3e-170">After you prepare the query string and configure the Data Flow task, the next step is create the table-valued function that will retrieve the change data from the database.</span></span>  
  
 <span data-ttu-id="60e3e-171">**다음 항목:** [변경 데이터 검색을 위한 함수 만들기](create-the-function-to-retrieve-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="60e3e-171">**Next topic:** [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md)</span></span>  
  
  
