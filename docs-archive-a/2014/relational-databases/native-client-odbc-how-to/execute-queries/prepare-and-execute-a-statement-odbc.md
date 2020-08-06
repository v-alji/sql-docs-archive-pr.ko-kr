---
title: 문 준비 및 실행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: rothja
ms.author: jroth
ms.openlocfilehash: 607d8ad1509eca1204f6d029842b04120d3f5d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739873"
---
# <a name="prepare-and-execute-a-statement-odbc"></a><span data-ttu-id="24ae9-102">문 준비 및 실행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="24ae9-102">Prepare and Execute a Statement (ODBC)</span></span>
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a><span data-ttu-id="24ae9-103">문을 한 번 준비한 후 여러 번 실행하려면</span><span class="sxs-lookup"><span data-stu-id="24ae9-103">To prepare a statement once, and then execute it multiple times</span></span>  
  
1.  <span data-ttu-id="24ae9-104">[SQLPrepare 함수](https://go.microsoft.com/fwlink/?LinkId=59360) 를 호출하여 문을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-104">Call [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) to prepare the statement.</span></span>  
  
2.  <span data-ttu-id="24ae9-105">필요에 따라 [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) 를 호출하여 준비된 문의 매개 변수 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-105">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
3.  <span data-ttu-id="24ae9-106">필요에 따라 준비된 문의 각 매개 변수에 대해 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-106">Optionally, for each parameter in the prepared statement:</span></span>  
  
    -   <span data-ttu-id="24ae9-107">[SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) 을 호출하여 매개 변수 정보를 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-107">Call [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to get parameter information.</span></span>  
  
    -   <span data-ttu-id="24ae9-108">[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)를 사용하여 각 매개 변수를 프로그램 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-108">Bind each parameter to a program variable by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="24ae9-109">실행 시 데이터 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-109">Set up any data-at-execution parameters.</span></span>  
  
4.  <span data-ttu-id="24ae9-110">준비된 문을 실행할 때마다 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-110">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="24ae9-111">문에 매개 변수 표식이 있는 경우 데이터 값을 바인딩된 매개 변수 버퍼에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-111">If the statement has parameter markers, put the data values into the bound parameter buffer.</span></span>  
  
    -   <span data-ttu-id="24ae9-112">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 를 호출하여 준비된 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-112">Call [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="24ae9-113">실행 시 데이터 입력 매개 변수를 사용하는 경우 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-113">If data-at-execution input parameters are used, [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="24ae9-114">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 및 [SQLPutData](../../native-client-odbc-api/sqlputdata.md)를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-114">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a><span data-ttu-id="24ae9-115">열 단위 매개 변수 바인딩을 사용하여 문을 준비하려면</span><span class="sxs-lookup"><span data-stu-id="24ae9-115">To prepare a statement with column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="24ae9-116">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-116">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="24ae9-117">SQL_ATTR_PARAMSET_SIZE를 매개 변수 집합 수(S)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-117">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="24ae9-118">SQL_ATTR_PARAM_BIND_TYPE을 SQL_PARAMETER_BIND_BY_COLUMN으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-118">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="24ae9-119">SQL_ATTR_PARAMS_PROCESSED_PTR 특성을 처리된 매개 변수 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-119">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="24ae9-120">SQL_ATTR_PARAMS_STATUS_PTR을 매개 변수 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[S]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-120">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="24ae9-121">SQLPrepare를 호출 하 여 문을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-121">Call SQLPrepare to prepare the statement.</span></span>  
  
3.  <span data-ttu-id="24ae9-122">필요에 따라 [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) 를 호출하여 준비된 문의 매개 변수 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-122">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
4.  <span data-ttu-id="24ae9-123">필요에 따라 준비 된 문의 각 매개 변수에 대해 SQLDescribeParam를 호출 하 여 매개 변수 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-123">Optionally, for each parameter in the prepared statement, call SQLDescribeParam to get parameter information.</span></span>  
  
5.  <span data-ttu-id="24ae9-124">각 매개 변수 표식에 대해 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-124">For each parameter marker:</span></span>  
  
    -   <span data-ttu-id="24ae9-125">데이터 값을 저장할 S 매개 변수 버퍼의 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-125">Allocate an array of S parameter buffers to store data values.</span></span>  
  
    -   <span data-ttu-id="24ae9-126">데이터 길이를 저장할 S개의 매개 변수 버퍼 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-126">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="24ae9-127">SQLBindParameter 를 호출하여 매개 변수 데이터 값과 데이터 길이 배열을 문 매개 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-127">Call SQLBindParameter to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
    -   <span data-ttu-id="24ae9-128">매개 변수가 실행 시 데이터 text 또는 image 매개 변수인 경우 해당 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-128">If the parameter is a data-at-execution text or image parameter, set it up.</span></span>  
  
    -   <span data-ttu-id="24ae9-129">실행 시 데이터 매개 변수를 사용하는 경우 해당 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-129">If any data-at-execution parameters are used, set them up.</span></span>  
  
6.  <span data-ttu-id="24ae9-130">준비된 문을 실행할 때마다 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-130">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="24ae9-131">S 데이터 값과 S 데이터 길이를 바인딩된 매개 변수 배열에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-131">Put the S data values and S data lengths into the bound parameter arrays.</span></span>  
  
    -   <span data-ttu-id="24ae9-132">SQLExecute를 호출하여 준비된 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-132">Call SQLExecute to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="24ae9-133">실행 시 데이터 입력 매개 변수를 사용하는 경우 SQLExecute는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-133">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="24ae9-134">SQLParamData 및 SQLPutData를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-134">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a><span data-ttu-id="24ae9-135">행 단위 바인딩 매개 변수를 사용하여 문을 준비하려면</span><span class="sxs-lookup"><span data-stu-id="24ae9-135">To prepare a statement with row-wise bound parameters</span></span>  
  
1.  <span data-ttu-id="24ae9-136">구조의 배열[S]을 할당합니다. 여기서 S는 매개 변수 집합의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-136">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="24ae9-137">구조에는 각 매개 변수에 대해 요소가 하나씩 포함되고 각 요소에는 두 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-137">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="24ae9-138">첫 번째 부분은 매개 변수의 데이터를 보유하는 적절한 데이터 형식의 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-138">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
    -   <span data-ttu-id="24ae9-139">두 번째 부분은 상태 표시를 보유하는 SQLINTEGER 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-139">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="24ae9-140">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-140">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="24ae9-141">SQL_ATTR_PARAMSET_SIZE를 매개 변수 집합 수(S)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-141">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="24ae9-142">SQL_ATTR_PARAM_BIND_TYPE을 1단계에서 할당한 구조의 크기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-142">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="24ae9-143">SQL_ATTR_PARAMS_PROCESSED_PTR 특성을 처리된 매개 변수 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-143">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="24ae9-144">SQL_ATTR_PARAMS_STATUS_PTR을 매개 변수 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[S]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-144">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="24ae9-145">SQLPrepare를 호출 하 여 문을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-145">Call SQLPrepare to prepare the statement.</span></span>  
  
4.  <span data-ttu-id="24ae9-146">각 매개 변수 표식에 대해 SQLBindParameter를 호출 하 여 1 단계에서 할당 한 구조 배열의 첫 번째 요소에 있는 해당 변수에 대 한 매개 변수 데이터 값 및 데이터 길이 포인터를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-146">For each parameter marker, call SQLBindParameter to point the parameter data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="24ae9-147">매개 변수가 실행 시 데이터 매개 변수인 경우 해당 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-147">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
5.  <span data-ttu-id="24ae9-148">준비된 문을 실행할 때마다 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-148">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="24ae9-149">바인딩된 매개 변수 버퍼 배열을 데이터 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-149">Fill the bound parameter buffer array with data values.</span></span>  
  
    -   <span data-ttu-id="24ae9-150">SQLExecute를 호출하여 준비된 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-150">Call SQLExecute to execute the prepared statement.</span></span> <span data-ttu-id="24ae9-151">드라이버에서는 효율적으로 SQL 문을 각 매개 변수 집합에 대해 한 번씩 총 S번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-151">The driver efficiently executes the SQL statement S times, once for each set of parameters.</span></span>  
  
    -   <span data-ttu-id="24ae9-152">실행 시 데이터 입력 매개 변수를 사용하는 경우 SQLExecute는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-152">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="24ae9-153">SQLParamData 및 SQLPutData를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="24ae9-153">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ae9-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24ae9-154">See Also</span></span>  
 [<span data-ttu-id="24ae9-155">쿼리 실행 방법 도움말 항목 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="24ae9-155">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
