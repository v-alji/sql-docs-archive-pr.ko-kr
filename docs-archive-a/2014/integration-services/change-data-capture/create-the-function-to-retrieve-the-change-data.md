---
title: 변경 데이터 검색을 위한 함수 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],creating function
ms.assetid: 55dd0946-bd67-4490-9971-12dfb5b9de94
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc1d5af0a64225aca4ff54570ad6504d25d62812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740233"
---
# <a name="create-the-function-to-retrieve-the-change-data"></a><span data-ttu-id="f1fba-102">변경 데이터 검색을 위한 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="f1fba-102">Create the Function to Retrieve the Change Data</span></span>
  <span data-ttu-id="f1fba-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 제어 흐름을 완료한 후 다음 태스크는 변경 데이터를 검색하는 테이블 반환 함수를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-103">After completing the control flow for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the next task is to create a table-valued function that retrieves the change data.</span></span> <span data-ttu-id="f1fba-104">첫 번째 증분 로드 전에 이 함수를 한 번만 만들면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-104">You only have to create this function one time before the first incremental load.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1fba-105">변경 데이터를 검색하는 함수 생성 작업은 변경 데이터를 증분 로드하는 패키지 생성 프로세스의 두 번째 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-105">The creation of a function to retrieve the change data is the second step in the process of creating a package that performs an incremental load of change data.</span></span> <span data-ttu-id="f1fba-106">이 패키지를 만들기 위한 전체 프로세스에 대한 설명은 [변경 데이터 캡처&#40;SSIS&#41;](change-data-capture-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-106">For a description of the overall process for creating this package, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations-for-change-data-capture-functions"></a><span data-ttu-id="f1fba-107">변경 데이터 캡처 함수에 대한 디자인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="f1fba-107">Design Considerations for Change Data Capture Functions</span></span>  
 <span data-ttu-id="f1fba-108">변경 데이터를 검색하기 위해 패키지 데이터 흐름의 원본 구성 요소는 다음 변경 데이터 캡처 쿼리 함수 중 하나를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-108">To retrieve change data, a source component in the data flow of the package calls one of the following change data capture query functions:</span></span>  
  
-   <span data-ttu-id="f1fba-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** 이 쿼리의 경우 각 업데이트에 대해 반환된 단일 행에는 변경된 각 행의 최종 상태가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-109">**cdc.fn_cdc_get_net_changes_<capture_instance>** For this query, the single row returned for each update contains the final state of each changed row.</span></span> <span data-ttu-id="f1fba-110">대부분의 경우 순 변경 내용에 대해 쿼리에서 반환하는 데이터만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-110">In most cases, you only need the data returned by a query for net changes.</span></span> <span data-ttu-id="f1fba-111">자세한 내용은 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-111">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
-   <span data-ttu-id="f1fba-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** 이 쿼리는 캡처 간격 동안 각 행에 발생한 모든 변경 내용을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-112">**cdc.fn_cdc_get_all_changes_<capture_instance>** This query returns all the changes that have occurred in each row during the capture interval.</span></span> <span data-ttu-id="f1fba-113">자세한 내용은 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-113">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="f1fba-114">그런 다음 원본 구성 요소는 함수에서 반환한 결과를 사용하고 최종 대상에 변경 데이터를 적용하는 다운스트림 변환 및 대상에 해당 결과를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-114">The source component then takes the results returned by the function and passes them to downstream transformations and destinations, which apply the change data to the final destination.</span></span>  
  
 <span data-ttu-id="f1fba-115">그러나 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소는 이러한 변경 데이터 캡처 함수를 직접 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-115">However, an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component cannot call these change data capture functions directly.</span></span> <span data-ttu-id="f1fba-116">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소에는 쿼리에서 반환하는 열에 대한 메타데이터가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-116">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component requires metadata about the columns that the query returns.</span></span> <span data-ttu-id="f1fba-117">변경 데이터 캡처 함수는 해당 출력 테이블의 열을 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-117">The change data capture functions do not define the columns of their output table.</span></span> <span data-ttu-id="f1fba-118">따라서 이러한 함수는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소에 대해 충분한 메타데이터를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-118">Thus, these functions do not return sufficient metadata for an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
 <span data-ttu-id="f1fba-119">테이블 반환 래퍼 함수와 같은 함수는 해당 RETURNS 절에 출력 테이블의 열을 명시적으로 정의하므로 테이블 반환 래퍼 함수를 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-119">Instead, you use a table-valued wrapper function because this kind of function explicitly defines the columns of its output table in its RETURNS clause.</span></span> <span data-ttu-id="f1fba-120">이렇게 열을 명시적으로 정의하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소에 필요한 메타데이터가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-120">This explicit definition of columns provides the metadata that an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component needs.</span></span> <span data-ttu-id="f1fba-121">변경 데이터를 검색하려는 각 테이블에 대해 이 함수를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-121">You have to create this function for each table for which you want to retrieve change data.</span></span>  
  
 <span data-ttu-id="f1fba-122">변경 데이터 캡처 쿼리 함수를 호출하는 테이블 반환 래퍼 함수를 만드는 데는 두 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-122">You have two options for creating the table-valued wrapper function that calls the change data capture query function:</span></span>  
  
-   <span data-ttu-id="f1fba-123">**sys.sp_cdc_generate_wrapper_function** 시스템 저장 프로시저를 호출하여 테이블 반환 함수를 자동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-123">You can call the **sys.sp_cdc_generate_wrapper_function** system stored procedure to create the table-valued functions for you.</span></span>  
  
-   <span data-ttu-id="f1fba-124">이 항목에 나와 있는 지침과 예를 사용하여 테이블 반환 함수를 직접 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-124">You can write your own table-valued function by using the guidelines and the example in this topic.</span></span>  
  
## <a name="calling-a-stored-procedure-to-create-the-table-valued-function"></a><span data-ttu-id="f1fba-125">저장 프로시저를 호출하여 테이블 반환 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="f1fba-125">Calling a Stored Procedure to Create the Table-valued Function</span></span>  
 <span data-ttu-id="f1fba-126">필요한 테이블 반환 함수를 만드는 가장 쉽고 빠른 방법은 **sys.sp_cdc_generate_wrapper_function** 시스템 저장 프로시저를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-126">The quickest and easiest way to create the table-valued functions that you need is to call the **sys.sp_cdc_generate_wrapper_function** system stored procedure.</span></span> <span data-ttu-id="f1fba-127">이 저장 프로시저는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본 구성 요소의 필요에 맞게 특별히 설계된 래퍼 함수를 만드는 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-127">This stored procedure generates scripts to create wrapper functions that are designed specifically to meet the needs of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source component.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f1fba-128">**sys.sp_cdc_generate_wrapper_function** 시스템 저장 프로시저는 래퍼 함수를 직접 만드는 대신</span><span class="sxs-lookup"><span data-stu-id="f1fba-128">The **sys.sp_cdc_generate_wrapper_function** system stored procedure does not directly create the wrapper functions.</span></span> <span data-ttu-id="f1fba-129">래퍼 함수에 대한 CREATE 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-129">Instead, the stored procedure generates the CREATE scripts for the wrapper functions.</span></span> <span data-ttu-id="f1fba-130">개발자는 저장 프로시저에서 생성한 CREATE 스크립트를 실행해야 증분 로드 패키지에서 래퍼 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-130">The developer must run the CREATE scripts that the stored procedure generates before an incremental load package can call the wrapper functions.</span></span>  
  
 <span data-ttu-id="f1fba-131">이 시스템 저장 프로시저를 사용하는 방법을 이해하려면 이 프로시저의 작업 내용, 프로시저에서 생성하는 스크립트 및 스크립트에서 만드는 래퍼 함수를 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-131">To understand how to use this system stored procedure, you should understand what the procedure does, what scripts the procedure generates, and what wrapper functions the scripts create.</span></span>  
  
### <a name="understanding-and-using-the-stored-procedure"></a><span data-ttu-id="f1fba-132">저장 프로시저 이해 및 사용</span><span class="sxs-lookup"><span data-stu-id="f1fba-132">Understanding and Using the Stored Procedure</span></span>  
 <span data-ttu-id="f1fba-133">**sys.sp_cdc_generate_wrapper_function** 시스템 저장 프로시저는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지에서 사용할 래퍼 함수를 만드는 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-133">The **sys.sp_cdc_generate_wrapper_function** system stored procedure generates scripts to create wrapper functions for use by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span>  
  
 <span data-ttu-id="f1fba-134">이 저장 프로시저의 정의 중 처음 몇 줄은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-134">Here are the first few lines of the definition of the stored procedure:</span></span>  
  
 `CREATE PROCEDURE sys.sp_cdc_generate_wrapper_function`  
  
 `(`  
  
 `@capture_instance sysname = null`  
  
 `@closed_high_end_point bit = 1,`  
  
 `@column_list = null,`  
  
 `@update_flag_list = null`  
  
 `)`  
  
 <span data-ttu-id="f1fba-135">이 저장 프로시저의 모든 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-135">All the parameters for the stored procedure are optional.</span></span> <span data-ttu-id="f1fba-136">어떠한 매개 변수에도 값을 제공하지 않고 저장 프로시저를 호출하면 액세스 권한이 있는 모든 캡처 인스턴스에 대한 래퍼 함수가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-136">If you call the stored procedure without supplying values for any of the parameters, the stored procedure creates wrapper functions for all the capture instances to which you have access.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f1fba-137">이 저장 프로시저의 구문과 해당 매개 변수에 대한 자세한 내용은 [sys.sp_cdc_generate_wrapper_function&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-137">For more information about the syntax of this stored procedure and its parameters, see [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql).</span></span>  
  
 <span data-ttu-id="f1fba-138">이 저장 프로시저는 항상 각 캡처 인스턴스의 모든 변경 내용을 반환하는 래퍼 함수를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-138">The stored procedure always generates a wrapper function to return all changes from each capture instance.</span></span> <span data-ttu-id="f1fba-139">*@supports_net_changes*캡처 인스턴스를 만들 때 매개 변수가 설정 된 경우 저장 프로시저는 적용 가능한 각 캡처 인스턴스에서 순 변경 내용을 반환 하는 래퍼 함수도 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-139">If the *@supports_net_changes* parameter was set when the capture instance was created, the stored procedure also generates a wrapper function to return net changes from each applicable capture instance.</span></span>  
  
 <span data-ttu-id="f1fba-140">이 저장 프로시저는 열이 두 개 있는 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-140">The stored procedure returns a result set with two columns:</span></span>  
  
-   <span data-ttu-id="f1fba-141">저장 프로시저에서 생성한 래퍼 함수의 이름.</span><span class="sxs-lookup"><span data-stu-id="f1fba-141">The name of the wrapper function that the stored procedure has generated.</span></span> <span data-ttu-id="f1fba-142">이 저장 프로시저는 캡처 인스턴스의 이름에서 함수 이름을 파생합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-142">This stored procedure derives the function name from the name of the capture instance name.</span></span> <span data-ttu-id="f1fba-143">함수 이름은 'fn_all_changes_' 뒤에 캡처 인스턴스 이름을 추가한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-143">(The function name is 'fn_all_changes_' followed by the capture instance name.</span></span> <span data-ttu-id="f1fba-144">순 변경 함수가 만들어지는 경우에는 'fn_net_changes_'라는 접두사가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-144">The prefix used for the net changes function, if it is created, is 'fn_net_changes_'.)</span></span>  
  
-   <span data-ttu-id="f1fba-145">래퍼 함수에 대한 CREATE 문</span><span class="sxs-lookup"><span data-stu-id="f1fba-145">The CREATE statement for the wrapper function.</span></span>  
  
### <a name="understanding-and-using-the-scripts-created-by-the-stored-procedure"></a><span data-ttu-id="f1fba-146">저장 프로시저에서 만든 스크립트 이해 및 사용</span><span class="sxs-lookup"><span data-stu-id="f1fba-146">Understanding and Using the Scripts Created by the Stored Procedure</span></span>  
 <span data-ttu-id="f1fba-147">일반적으로 개발자는 INSERT...EXEC 문을 사용하여 **sys.sp_cdc_generate_wrapper_function** 저장 프로시저를 호출하고 저장 프로시저에서 만든 스크립트를 임시 테이블에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-147">Typically, a developer would use an INSERT...EXEC statement to call the **sys.sp_cdc_generate_wrapper_function** stored procedure and save the scripts that the stored procedure creates to a temporary table.</span></span> <span data-ttu-id="f1fba-148">그런 다음 각 스크립트를 개별적으로 선택 및 실행하여 해당 래퍼 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-148">Each script could then be individually selected and run to create the corresponding wrapper function.</span></span> <span data-ttu-id="f1fba-149">그러나 개발자는 다음 예제 코드와 같이 일련의 SQL 명령을 사용하여 모든 CREATE 스크립트를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-149">However, a developer could also use one set of SQL commands to run all the CREATE scripts, as shown in the following sample code:</span></span>  
  
```  
create table #wrapper_functions  
      (function_name sysname, create_stmt nvarchar(max))  
insert into #wrapper_functions  
exec sys.sp_cdc_generate_wrapper_function  
  
declare @stmt nvarchar(max)  
declare #hfunctions cursor local fast_forward for   
      select create_stmt from #wrapper_functions  
open #hfunctions  
fetch #hfunctions into @stmt  
while (@@fetch_status <> -1)  
begin  
      exec sp_executesql @stmt  
      fetch #hfunctions into @stmt  
end  
close #hfunctions  
deallocate #hfunctions  
```  
  
### <a name="understanding-and-using-the-functions-created-by-the-stored-procedure"></a><span data-ttu-id="f1fba-150">저장 프로시저에서 만든 함수 이해 및 사용</span><span class="sxs-lookup"><span data-stu-id="f1fba-150">Understanding and Using the Functions Created by the Stored Procedure</span></span>  
 <span data-ttu-id="f1fba-151">캡처된 변경 데이터의 타임 라인을 체계적으로 탐색 하기 위해 생성 된 래퍼 함수는 *@end_time* 한 간격의 매개 변수가 *@start_time* 후속 간격의 매개 변수일 것으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-151">To systematically walk the timeline of captured change data, the generated wrapper functions expect that the *@end_time* parameter for one interval will be the *@start_time* parameter for the subsequent interval.</span></span> <span data-ttu-id="f1fba-152">이러한 규칙이 준수되는 경우 생성된 래퍼 함수에서 다음과 같은 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-152">When this convention is followed, the generated wrapper functions can do the following tasks:</span></span>  
  
-   <span data-ttu-id="f1fba-153">날짜/시간 값을 내부적으로 사용되는 LSN 값에 매핑</span><span class="sxs-lookup"><span data-stu-id="f1fba-153">Map the date/time values to the LSN values that are used internally.</span></span>  
  
-   <span data-ttu-id="f1fba-154">손실되거나 반복되는 데이터가 없는지 확인</span><span class="sxs-lookup"><span data-stu-id="f1fba-154">Ensure that no data is lost or repeated.</span></span>  
  
 <span data-ttu-id="f1fba-155">생성된 래퍼 함수에서는 변경 테이블의 모든 행을 간단히 쿼리할 수 있도록 다음과 같은 규칙도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-155">To make querying for all rows of a change table simpler, the generated wrapper functions also support the following conventions:</span></span>  
  
-   <span data-ttu-id="f1fba-156">@start_time 매개 변수가 null이면 래퍼 함수는 캡처 인스턴스에서 가장 낮은 LSN 값을 쿼리의 하한으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-156">If the @start_time parameter is null, the wrapper functions use the lowest LSN value in the capture instance as the lower bound of the query.</span></span>  
  
-   <span data-ttu-id="f1fba-157">@end_time 매개 변수가 null이면 래퍼 함수는 캡처 인스턴스에서 가장 높은 LSN 값을 쿼리의 상한으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-157">If the @end_time parameter is null, the wrapper functions use the highest LSN value in the capture instance as the upper bound of the query.</span></span>  
  
 <span data-ttu-id="f1fba-158">대부분의 사용자는 **sys.sp_cdc_generate_wrapper_function** 시스템 저장 프로시저에서 만드는 래퍼 함수를 수정하지 않고 그대로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-158">Most users should be able to use the wrapper functions that the **sys.sp_cdc_generate_wrapper_function** system stored procedure creates without modification.</span></span> <span data-ttu-id="f1fba-159">그러나 래퍼 함수를 사용자 지정하려면 CREATE 스크립트를 사용자 지정한 다음 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-159">However, to customize the wrapper functions, you have to customize the CREATE scripts before you run the scripts.</span></span>  
  
 <span data-ttu-id="f1fba-160">패키지에서 래퍼 함수를 호출하는 경우 패키지에서 세 가지 매개 변수에 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-160">When your package calls the wrapper functions, the package must supply values for three parameters.</span></span> <span data-ttu-id="f1fba-161">이러한 세 가지 매개 변수는 변경 데이터 캡처 함수에서 사용하는 세 가지 매개 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-161">These three parameters are like the three parameters that the change data capture functions use.</span></span> <span data-ttu-id="f1fba-162">이러한 세 가지 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-162">These three parameters are as follows:</span></span>  
  
-   <span data-ttu-id="f1fba-163">간격의 시작 날짜/시간 값 및 종료 날짜/시간 값.</span><span class="sxs-lookup"><span data-stu-id="f1fba-163">The starting date/time value and the ending date/time value for the interval.</span></span> <span data-ttu-id="f1fba-164">래퍼 함수는 날짜/시간 값을 쿼리 간격의 끝점으로 사용하지만 변경 데이터 캡처 함수는 두 LSN 값을 끝점으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-164">While the wrapper functions use date/time values as the end points for the query interval, the change data capture functions use two LSN values as the end points.</span></span>  
  
-   <span data-ttu-id="f1fba-165">행 필터.</span><span class="sxs-lookup"><span data-stu-id="f1fba-165">The row filter.</span></span> <span data-ttu-id="f1fba-166">래퍼 함수와 변경 데이터 캡처 함수의 경우 *@row_filter_option* 매개 변수는 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-166">For both the wrapper functions and the change data capture functions, the *@row_filter_option* parameter is the same.</span></span> <span data-ttu-id="f1fba-167">자세한 내용은 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) 및 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-167">For more information, see [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql) and [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
 <span data-ttu-id="f1fba-168">래퍼 함수에서 반환하는 결과 집합에는 다음과 같은 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-168">The result set returned by the wrapper functions includesthe following data:</span></span>  
  
-   <span data-ttu-id="f1fba-169">변경 데이터의 모든 요청된 열</span><span class="sxs-lookup"><span data-stu-id="f1fba-169">All of the requested columns of change data.</span></span>  
  
-   <span data-ttu-id="f1fba-170">1문자 또는 2문자 필드를 사용하여 행에 연결된 작업을 식별하는 __CDC_OPERATION이라는 열.</span><span class="sxs-lookup"><span data-stu-id="f1fba-170">A column named __CDC_OPERATION that uses a one- or two-character field to identify the operation that is associated with the row.</span></span> <span data-ttu-id="f1fba-171">이 필드의 유효한 값은 다음과 같습니다. ‘I’는 삽입, ‘D’는 삭제, ‘UO’는 이전 값 업데이트 및 ‘UN’은 새 값 업데이트입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-171">The valid values for this field are as follows: 'I' for insert, 'D' for delete, 'UO' for update old values, and 'UN' for update new values.</span></span>  
  
-   <span data-ttu-id="f1fba-172">요청 시 작업 코드 뒤에 비트 열로 표시 되 고 매개 변수에 지정 된 순서로 플래그를 업데이트 *@update_flag_list* 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-172">Update flags, when you request them, that appear as bit columns after the operation code and in the order that is specified in the *@update_flag_list* parameter.</span></span> <span data-ttu-id="f1fba-173">이러한 열의 이름은 관련 열 이름에 '_uflag'를 추가한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-173">These columns are named by appending '_uflag' to the associated column name.</span></span>  
  
 <span data-ttu-id="f1fba-174">패키지에서 모든 변경을 쿼리하는 래퍼 함수를 호출하는 경우 래퍼 함수는 __CDC_STARTLSN 및 \__CDC_SEQVAL 열도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-174">If your package calls a wrapper function that queries for all changes, the wrapper function also returns the columns, __CDC_STARTLSN and \__CDC_SEQVAL.</span></span> <span data-ttu-id="f1fba-175">이러한 두 열은 각각 결과 집합의 첫 번째 열과 두 번째 열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-175">These two columns become the first and second columns, respectively, of the result set.</span></span> <span data-ttu-id="f1fba-176">또한 래퍼 함수는 이러한 두 열에 따라 결과 집합을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-176">The wrapper function also sorts the result set based on these two columns.</span></span>  
  
## <a name="writing-your-own-table-value-function"></a><span data-ttu-id="f1fba-177">테이블 반환 함수 직접 작성</span><span class="sxs-lookup"><span data-stu-id="f1fba-177">Writing Your Own Table-Value Function</span></span>  
 <span data-ttu-id="f1fba-178">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 통해 변경 데이터 캡처 쿼리 함수를 호출하는 테이블 반환 함수를 직접 작성하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-178">You can also use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to write your own table-valued wrapper function that calls the change data capture query function, and store the table-valued wrapper function in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f1fba-179">TRANSACT-SQL 함수를 만드는 방법에 대한 자세한 내용은 [CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-179">For more information about how to create a Transact-SQL function, see [CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql).</span></span>  
  
 <span data-ttu-id="f1fba-180">다음 예에서는 지정한 변경 간격 동안 Customer 테이블에서 변경 내용을 검색하는 테이블 반환 함수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-180">The following example defines a table-valued function that retrieves changes from a Customer table for the specified change interval.</span></span> <span data-ttu-id="f1fba-181">이 함수는 변경 데이터 캡처 함수를 사용하여 변경 테이블이 내부적으로 사용하는 이진 LSN(로그 시퀀스 번호) 값에 `datetime` 값을 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-181">This function uses change data capture functions to map the `datetime` values to the binary log sequence number (LSN) values that the change tables use internally.</span></span> <span data-ttu-id="f1fba-182">또한 이 함수는 다음과 같은 몇 가지 특수 상황을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-182">This function also handles several special conditions:</span></span>  
  
-   <span data-ttu-id="f1fba-183">시작 시간에 대해 Null 값이 전달되는 경우 이 함수는 사용할 수 있는 가장 오래된 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-183">When a null value is passed for the starting time, this function uses the earliest available value.</span></span>  
  
-   <span data-ttu-id="f1fba-184">종료 시간에 대해 Null 값이 전달되는 경우 이 함수는 사용할 수 있는 최근 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-184">When a null value is passed for the ending time, this function uses the latest available value.</span></span>  
  
-   <span data-ttu-id="f1fba-185">시작 LSN이 끝 LSN과 같은 경우(일반적으로 선택 간격에 대한 레코드가 없음을 나타냄) 이 함수는 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-185">When the starting LSN is equal to the ending LSN, which usually indicates that there are no records for the selected interval, this function exits.</span></span>  
  
### <a name="example-of-a-table-value-function-that-queries-for-change-data"></a><span data-ttu-id="f1fba-186">변경 데이터를 쿼리하는 테이블 반환 함수의 예</span><span class="sxs-lookup"><span data-stu-id="f1fba-186">Example of a Table-Value Function that Queries for Change Data</span></span>  
  
```  
CREATE function CDCSample.uf_Customer (  
     @start_time datetime  
    ,@end_time datetime  
)  
returns @Customer table (  
     CustomerID int  
    ,TerritoryID int  
    ,CustomerType nchar(1)  
    ,rowguid uniqueidentifier  
    ,ModifiedDate datetime  
    ,CDC_OPERATION varchar(1)  
) as  
begin  
    declare @from_lsn binary(10), @to_lsn binary(10)  
  
    if (@start_time is null)  
        select @from_lsn = sys.fn_cdc_get_min_lsn('Customer')  
    else  
        select @from_lsn = sys.fn_cdc_increment_lsn(sys.fn_cdc_map_time_to_lsn('largest less than or equal',@start_time))  
  
    if (@end_time is null)  
        select @to_lsn = sys.fn_cdc_get_max_lsn()  
    else  
        select @to_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal',@end_time)  
  
    if (@from_lsn = sys.fn_cdc_increment_lsn(@to_lsn))  
        return  
  
    -- Query for change data  
    insert into @Customer  
    select   
        CustomerID,      
        TerritoryID,   
        CustomerType,   
        rowguid,   
        ModifiedDate,   
        case __$operation  
                when 1 then 'D'  
                when 2 then 'I'  
                when 4 then 'U'  
                else null  
         end as CDC_OPERATION  
    from   
        cdc.fn_cdc_get_net_changes_Customer(@from_lsn, @to_lsn, 'all')  
  
    return  
end   
go  
  
```  
  
### <a name="retrieving-additional-metadata-with-the-change-data"></a><span data-ttu-id="f1fba-187">변경 데이터의 추가 메타데이터 검색</span><span class="sxs-lookup"><span data-stu-id="f1fba-187">Retrieving Additional Metadata with the Change Data</span></span>  
 <span data-ttu-id="f1fba-188">위에 나와 있는 사용자가 만든 테이블 반환 함수는 **__$operation** 열을 사용하지만 **cdc.fn_cdc_get_net_changes_<capture_instance>** 함수는 각 변경 행의 메타데이터 열 4개를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-188">Although the user-created table-valued function shown earlier uses only the **__$operation** column, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns four columns of metadata for each change row.</span></span> <span data-ttu-id="f1fba-189">데이터 흐름에 이러한 값을 사용하려면 테이블 반환 래퍼 함수에서 추가 열로 이러한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-189">If you want to use these values in your data flow, you can return them as additional columns from the table-valued wrapper function.</span></span>  
  
|<span data-ttu-id="f1fba-190">열 이름</span><span class="sxs-lookup"><span data-stu-id="f1fba-190">Column name</span></span>|<span data-ttu-id="f1fba-191">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f1fba-191">Data type</span></span>|<span data-ttu-id="f1fba-192">Description</span><span class="sxs-lookup"><span data-stu-id="f1fba-192">Description</span></span>|  
|-----------------|---------------|-----------------|  
|<span data-ttu-id="f1fba-193">**__$start_lsn**</span><span class="sxs-lookup"><span data-stu-id="f1fba-193">**__$start_lsn**</span></span>|`binary(10)`|<span data-ttu-id="f1fba-194">변경에 대한 커밋 트랜잭션과 연관된 LSN입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-194">LSN associated with the commit transaction for the change.</span></span><br /><br /> <span data-ttu-id="f1fba-195">동일한 트랜잭션에서 커밋된 변경의 커밋 LSN은 모두 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-195">All changes committed in the same transaction share the same commit LSN.</span></span> <span data-ttu-id="f1fba-196">예를 들어 원본 테이블의 업데이트 작업에서 두 개의 서로 다른 행을 수정하면 변경 테이블에는 모두 동일한 **__$start_lsn** 값이 있는 4개의 행(이전 값과 새 값 두 개씩 포함)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-196">For example, if an update operation on the source table modifies two different rows, the change table will contain four rows (two with the old values and two with the new values), each with the same **__$start_lsn** value.</span></span>|  
|<span data-ttu-id="f1fba-197">**__$seqval**</span><span class="sxs-lookup"><span data-stu-id="f1fba-197">**__$seqval**</span></span>|`binary(10)`|<span data-ttu-id="f1fba-198">트랜잭션에서 행 변경 내용을 정렬하는 데 사용되는 시퀀스 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-198">Sequence value that is used to order the row changes in a transaction.</span></span>|  
|<span data-ttu-id="f1fba-199">**__$operation**</span><span class="sxs-lookup"><span data-stu-id="f1fba-199">**__$operation**</span></span>|`int`|<span data-ttu-id="f1fba-200">변경과 연관된 DML(데이터 조작 언어) 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-200">The data manipulation language (DML) operation associated with the change.</span></span> <span data-ttu-id="f1fba-201">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-201">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="f1fba-202">1 = 삭제</span><span class="sxs-lookup"><span data-stu-id="f1fba-202">1 = delete</span></span><br /><br /> <span data-ttu-id="f1fba-203">2 = 삽입</span><span class="sxs-lookup"><span data-stu-id="f1fba-203">2 = insert</span></span><br /><br /> <span data-ttu-id="f1fba-204">3 = 업데이트(업데이트 작업 전의 값)</span><span class="sxs-lookup"><span data-stu-id="f1fba-204">3 = update (Values before the update operation.)</span></span><br /><br /> <span data-ttu-id="f1fba-205">4 = 업데이트(업데이트 작업 후의 값)</span><span class="sxs-lookup"><span data-stu-id="f1fba-205">4 = update (Values after the update operation.)</span></span>|  
|<span data-ttu-id="f1fba-206">**__$update_mask**</span><span class="sxs-lookup"><span data-stu-id="f1fba-206">**__$update_mask**</span></span>|`varbinary(128)`|<span data-ttu-id="f1fba-207">변경된 열을 식별하는 변경 테이블의 열 서수를 기준으로 하는 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-207">A bitmask that is based on the column ordinals of the change table identifying those columns that changed.</span></span> <span data-ttu-id="f1fba-208">변경된 열을 확인해야 하는 경우 이 값을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-208">You could examine this value if you had to determine which columns have changed.</span></span>|  
|**\<captured source table columns>**|<span data-ttu-id="f1fba-209">다름</span><span class="sxs-lookup"><span data-stu-id="f1fba-209">varies</span></span>|<span data-ttu-id="f1fba-210">함수에서 반환되는 나머지 열은 캡처 인스턴스 생성 시 캡처된 열로 식별된 원본 테이블의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-210">The remaining columns returned by the function are the columns from the source table that were identified as captured columns when the capture instance was created.</span></span> <span data-ttu-id="f1fba-211">캡처된 열 목록에 열이 원래 지정되어 있지 않은 경우 원본 테이블의 모든 열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-211">If no columns were originally specified in the captured column list, all columns in the source table are returned.</span></span>|  
  
 <span data-ttu-id="f1fba-212">자세한 내용은 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62;&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1fba-212">For more information, see [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql).</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f1fba-213">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f1fba-213">Next Step</span></span>  
 <span data-ttu-id="f1fba-214">변경 데이터를 쿼리하는 테이블 반환 함수를 만든 후 다음 단계는 패키지의 데이터 흐름 디자인을 시작하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1fba-214">After you have created the table-valued function that queries for change data, the next step is to start designing the data flow in the package.</span></span>  
  
 <span data-ttu-id="f1fba-215">**다음 항목:** [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="f1fba-215">**Next topic:** [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>  
  
  
