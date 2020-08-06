---
title: 쿼리 매개 변수를 SQL 실행 태스크의 변수에 매핑 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameterized SQL commands [Integration Services]
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- Execute SQL task [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 6a164349-dfcf-4995-80bc-d4e7aee52a83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8511d70b40f2934680e1cb790763045c04e8204a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650161"
---
# <a name="map-query-parameters-to-variables-in-an-execute-sql-task"></a><span data-ttu-id="3e2c4-102">쿼리 매개 변수를 SQL 실행 태스크의 변수에 매핑</span><span class="sxs-lookup"><span data-stu-id="3e2c4-102">Map Query Parameters to Variables in an Execute SQL Task</span></span>

  <span data-ttu-id="3e2c4-103">이 항목에서는 SQL 실행 태스크에서 매개 변수가 있는 SQL 문을 사용하는 방법과 SQL 문의 변수와 매개 변수 간 매핑을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-103">This topic describes how to use a parameterized SQL statement in the Execute SQL task and create mappings between variables and the parameters in the SQL statement.</span></span>  
  
 <span data-ttu-id="3e2c4-104">다른 연결 형식에 사용할 매개 변수 이름, 매개 변수 표식 및 SQL 실행 태스크에 대한 자세한 내용은 [SQL 실행 태스크](control-flow/execute-sql-task.md) 및 [SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-104">To learn more about the Execute SQL task, the parameter markers, and parameter names you use with different connection types, see [Execute SQL Task](control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a><span data-ttu-id="3e2c4-105">쿼리 매개 변수를 변수에 매핑하려면</span><span class="sxs-lookup"><span data-stu-id="3e2c4-105">To map a query parameter to a variable</span></span>  
  
1.  <span data-ttu-id="3e2c4-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업하려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package you want to work with.</span></span>  
  
2.  <span data-ttu-id="3e2c4-107">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3e2c4-108">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="3e2c4-109">패키지에 아직 SQL 실행 태스크가 포함되어 있지 않으면 패키지의 제어 흐름에 해당 작업을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-109">If the package does not already include an Execute SQL task, add one to the control flow of the package.</span></span> <span data-ttu-id="3e2c4-110">자세한 내용은 [제어 흐름에서 태스크 또는 컨테이너 추가 또는 삭제](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-110">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="3e2c4-111">.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-111">.</span></span>  
  
5.  <span data-ttu-id="3e2c4-112">SQL 실행 태스크를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-112">Double-click the Execute SQL task.</span></span>  
  
6.  <span data-ttu-id="3e2c4-113">다음 방법 중 하나로 매개 변수가 있는 SQL 명령을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-113">Provide a parameterized SQL command in one of the following ways:</span></span>  
  
    -   <span data-ttu-id="3e2c4-114">직접 입력을 사용하여 SQLStatement 속성에 SQL 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-114">Use direct input and type the SQL command in the SQLStatement property.</span></span>  
  
    -   <span data-ttu-id="3e2c4-115">직접 입력을 사용하여 **쿼리 작성**을 클릭한 후 쿼리 작성기에서 제공하는 그래픽 도구를 사용하여 SQL 명령을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-115">Use direct input, click **Build Query**, and then create an SQL command using the graphical tools that the Query Builder provides.</span></span>  
  
    -   <span data-ttu-id="3e2c4-116">파일 연결을 사용한 후 SQL 명령이 포함된 파일을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-116">Use a file connection and then reference the file that contains the SQL command.</span></span>  
  
    -   <span data-ttu-id="3e2c4-117">변수를 사용한 후 SQL 명령이 포함된 변수를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-117">Use a variable and then reference the variable that contains the SQL command.</span></span>  
  
     <span data-ttu-id="3e2c4-118">매개 변수가 있는 SQL 문에서 사용하는 매개 변수 표식은 SQL 실행 태스크에서 사용하는 연결 형식에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-118">The parameter markers that you use in parameterized SQL statements depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="3e2c4-119">연결 형식</span><span class="sxs-lookup"><span data-stu-id="3e2c4-119">Connection type</span></span>|<span data-ttu-id="3e2c4-120">매개 변수 표식</span><span class="sxs-lookup"><span data-stu-id="3e2c4-120">Parameter marker</span></span>|  
    |---------------------|----------------------|  
    |<span data-ttu-id="3e2c4-121">ADO</span><span class="sxs-lookup"><span data-stu-id="3e2c4-121">ADO</span></span>|<span data-ttu-id="3e2c4-122">?</span><span class="sxs-lookup"><span data-stu-id="3e2c4-122">?</span></span>|  
    |<span data-ttu-id="3e2c4-123">ADO.NET 및 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="3e2c4-123">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="3e2c4-124">ODBC</span><span class="sxs-lookup"><span data-stu-id="3e2c4-124">ODBC</span></span>|<span data-ttu-id="3e2c4-125">?</span><span class="sxs-lookup"><span data-stu-id="3e2c4-125">?</span></span>|  
    |<span data-ttu-id="3e2c4-126">EXCEL 및 OLE DB</span><span class="sxs-lookup"><span data-stu-id="3e2c4-126">EXCEL and OLE DB</span></span>|<span data-ttu-id="3e2c4-127">?</span><span class="sxs-lookup"><span data-stu-id="3e2c4-127">?</span></span>|  
  
     <span data-ttu-id="3e2c4-128">다음 표에서는 연결 관리자 유형별 SELECT 명령의 예를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-128">The following table lists examples of the SELECT command by connection manager type.</span></span> <span data-ttu-id="3e2c4-129">매개 변수는 WHERE 절에 필터 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-129">Parameters provide the filter values in the WHERE clauses.</span></span> <span data-ttu-id="3e2c4-130">이 예에서는 SELECT를 사용하여 **의** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] 테이블에서 **ProductID** 가 두 매개 변수로 지정된 값보다 크고 작은 제품을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-130">The examples use SELECT to return products from the **Product** table in [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)] that have a **ProductID** greater than and less than the values specified by two parameters.</span></span>  
  
    |<span data-ttu-id="3e2c4-131">연결 형식</span><span class="sxs-lookup"><span data-stu-id="3e2c4-131">Connection type</span></span>|<span data-ttu-id="3e2c4-132">SELECT 구문</span><span class="sxs-lookup"><span data-stu-id="3e2c4-132">SELECT syntax</span></span>|  
    |---------------------|-------------------|  
    |<span data-ttu-id="3e2c4-133">EXCEL, ODBC 및 OLEDB</span><span class="sxs-lookup"><span data-stu-id="3e2c4-133">EXCEL, ODBC, and OLEDB</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |<span data-ttu-id="3e2c4-134">ADO</span><span class="sxs-lookup"><span data-stu-id="3e2c4-134">ADO</span></span>|`SELECT* FROM Production.Product WHERE ProductId > ? AND ProductID < ?`|  
    |[!INCLUDE[vstecado](../includes/vstecado-md.md)]|`SELECT* FROM Production.Product WHERE ProductId > @parmMinProductID AND ProductID < @parmMaxProductID`|  
  
     <span data-ttu-id="3e2c4-135">저장 프로시저에서 매개 변수를 사용하는 예는 [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-135">For examples of using parameters with stored procedures, see [Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>  
  
7.  <span data-ttu-id="3e2c4-136">**매개 변수 매핑**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-136">Click **Parameter Mapping**.</span></span>  
  
8.  <span data-ttu-id="3e2c4-137">매개 변수 매핑을 추가하려면 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-137">To add a parameter mapping, click **Add**.</span></span>  
  
9. <span data-ttu-id="3e2c4-138">**매개 변수 이름** 상자에 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-138">Provide a name in the **Parameter Name** box.</span></span>  
  
     <span data-ttu-id="3e2c4-139">사용하는 매개 변수 이름은 SQL 실행 태스크에 사용하는 연결 형식에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-139">The parameter names that you use depend on the connection type that the Execute SQL task uses.</span></span>  
  
    |<span data-ttu-id="3e2c4-140">연결 형식</span><span class="sxs-lookup"><span data-stu-id="3e2c4-140">Connection type</span></span>|<span data-ttu-id="3e2c4-141">매개 변수 이름</span><span class="sxs-lookup"><span data-stu-id="3e2c4-141">Parameter name</span></span>|  
    |---------------------|--------------------|  
    |<span data-ttu-id="3e2c4-142">ADO</span><span class="sxs-lookup"><span data-stu-id="3e2c4-142">ADO</span></span>|<span data-ttu-id="3e2c4-143">Param1, Param2, ...</span><span class="sxs-lookup"><span data-stu-id="3e2c4-143">Param1, Param2, ...</span></span>|  
    |<span data-ttu-id="3e2c4-144">ADO.NET 및 SQLMOBILE</span><span class="sxs-lookup"><span data-stu-id="3e2c4-144">ADO.NET and SQLMOBILE</span></span>|@\<parameter name>|  
    |<span data-ttu-id="3e2c4-145">ODBC</span><span class="sxs-lookup"><span data-stu-id="3e2c4-145">ODBC</span></span>|<span data-ttu-id="3e2c4-146">1, 2, 3, ...</span><span class="sxs-lookup"><span data-stu-id="3e2c4-146">1, 2, 3, ...</span></span>|  
    |<span data-ttu-id="3e2c4-147">EXCEL 및 OLE DB</span><span class="sxs-lookup"><span data-stu-id="3e2c4-147">EXCEL and OLE DB</span></span>|<span data-ttu-id="3e2c4-148">0, 1, 2, 3, ...</span><span class="sxs-lookup"><span data-stu-id="3e2c4-148">0, 1, 2, 3, ...</span></span>|  
  
10. <span data-ttu-id="3e2c4-149">**변수 이름** 목록에서 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-149">From the **Variable Name** list, select a variable.</span></span> <span data-ttu-id="3e2c4-150">자세한 내용은 [패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-150">For more information, see [Add, Delete, Change Scope of User-Defined Variable in a Package](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md).</span></span>  
  
11. <span data-ttu-id="3e2c4-151">**방향** 목록에서 매개 변수가 입력, 출력 또는 반환 값인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-151">In the **Direction** list, specify if the parameter is an input, an output, or a return value.</span></span>  
  
12. <span data-ttu-id="3e2c4-152">**데이터 형식** 목록에서 매개 변수의 데이터 형식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-152">In the **Data Type** list, set the data type of the parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3e2c4-153">매개 변수의 데이터 형식은 변수의 데이터 형식과 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-153">The data type of the parameter must be compatible with the data type of the variable.</span></span>  
  
13. <span data-ttu-id="3e2c4-154">SQL 문의 각 매개 변수에 대해 8에서 11단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-154">Repeat steps 8 through 11 for each parameter in the SQL statement.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3e2c4-155">매개 변수 매핑의 순서는 SQL 문에 표시된 매개 변수의 순서와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-155">The order of parameter mappings must be the same as the order in which the parameters appear in the SQL statement.</span></span>  
  
14. <span data-ttu-id="3e2c4-156">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3e2c4-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2c4-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e2c4-157">See Also</span></span>  
 <span data-ttu-id="3e2c4-158">[SQL 실행 태스크](control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="3e2c4-158">[Execute SQL Task](control-flow/execute-sql-task.md) </span></span>  
 <span data-ttu-id="3e2c4-159">[SQL 실행 태스크의 매개 변수 및 반환 코드](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="3e2c4-159">[Parameters and Return Codes in the Execute SQL Task](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) </span></span>  
 [<span data-ttu-id="3e2c4-160">Integration Services&#40;SSIS&#41; 변수</span><span class="sxs-lookup"><span data-stu-id="3e2c4-160">Integration Services &#40;SSIS&#41; Variables</span></span>](integration-services-ssis-variables.md)  
  
  
