---
title: 직접 문 실행 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeada906a925cff93455ffd92e7c17822a80124
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638730"
---
# <a name="execute-a-statement-directly-odbc"></a><span data-ttu-id="8f069-102">직접 문 실행(ODBC)</span><span class="sxs-lookup"><span data-stu-id="8f069-102">Execute a Statement Directly (ODBC)</span></span>
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a><span data-ttu-id="8f069-103">문을 한 번만 직접 실행하려면</span><span class="sxs-lookup"><span data-stu-id="8f069-103">To execute a statement directly and one time only</span></span>  
  
1.  <span data-ttu-id="8f069-104">문에 매개 변수 표식이 있으면 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) 를 사용하여 프로그램 변수에 각 매개 변수를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-104">If the statement has parameter markers, use [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind each parameter to a program variable.</span></span> <span data-ttu-id="8f069-105">프로그램 변수를 데이터 값으로 채운 다음 실행 시 데이터 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-105">Fill the program variables with data values, and then set up any data-at-execution parameters.</span></span>  
  
2.  <span data-ttu-id="8f069-106">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 를 호출하여 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-106">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span>  
  
3.  <span data-ttu-id="8f069-107">실행 시 데이터 입력 매개 변수를 사용하면 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-107">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="8f069-108">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 및 [SQLPutData](../../native-client-odbc-api/sqlputdata.md)를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-108">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a><span data-ttu-id="8f069-109">열 단위 매개 변수 바인딩을 사용하여 문을 여러 번 실행하려면</span><span class="sxs-lookup"><span data-stu-id="8f069-109">To execute a statement multiple times by using column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="8f069-110">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-110">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="8f069-111">SQL_ATTR_PARAMSET_SIZE를 매개 변수 집합 수(S)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-111">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="8f069-112">SQL_ATTR_PARAM_BIND_TYPE을 SQL_PARAMETER_BIND_BY_COLUMN으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-112">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
     <span data-ttu-id="8f069-113">SQL_ATTR_PARAMS_PROCESSED_PTR 특성을 처리된 매개 변수 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-113">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="8f069-114">SQL_ATTR_PARAMS_STATUS_PTR을 매개 변수 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[S]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-114">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="8f069-115">각 매개 변수 표식에 대해 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-115">For each parameter marker:</span></span>  
  
     <span data-ttu-id="8f069-116">데이터 값을 저장할 S 매개 변수 버퍼의 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-116">Allocate an array of S parameter buffers to store data values.</span></span>  
  
     <span data-ttu-id="8f069-117">데이터 길이를 저장할 S개의 매개 변수 버퍼 배열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-117">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
     <span data-ttu-id="8f069-118">[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) 를 호출하여 매개 변수 데이터 값과 데이터 길이 배열을 문 매개 변수에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-118">Call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
     <span data-ttu-id="8f069-119">실행 시 데이터 텍스트 또는 이미지 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-119">Set up any data-at-execution text or image parameters.</span></span>  
  
     <span data-ttu-id="8f069-120">S개의 데이터 값과 S개의 데이터 길이를 바인딩된 매개 변수 배열에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-120">Put S data values and S data lengths into the bound parameter arrays.</span></span>  
  
3.  <span data-ttu-id="8f069-121">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 를 호출하여 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-121">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="8f069-122">드라이버에서는 효율적으로 문을 각 매개 변수 집합에 대해 한 번씩 총 S번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-122">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
4.  <span data-ttu-id="8f069-123">실행 시 데이터 입력 매개 변수를 사용하면 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-123">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="8f069-124">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 및 [SQLPutData](../../native-client-odbc-api/sqlputdata.md)를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-124">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a><span data-ttu-id="8f069-125">행 단위 매개 변수 바인딩을 사용하여 문을 여러 번 실행하려면</span><span class="sxs-lookup"><span data-stu-id="8f069-125">To execute a statement multiple times by using row-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="8f069-126">구조의 배열[S]을 할당합니다. 여기서 S는 매개 변수 집합의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-126">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="8f069-127">구조에는 각 매개 변수에 대해 요소가 하나씩 포함되고 각 요소에는 두 부분이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-127">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
     <span data-ttu-id="8f069-128">첫 번째 부분은 매개 변수의 데이터를 보유하는 적절한 데이터 형식의 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-128">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
     <span data-ttu-id="8f069-129">두 번째 부분은 상태 표시를 보유하는 SQLINTEGER 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-129">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="8f069-130">[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 을 호출하여 다음 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-130">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="8f069-131">SQL_ATTR_PARAMSET_SIZE를 매개 변수 집합 수(S)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-131">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="8f069-132">SQL_ATTR_PARAM_BIND_TYPE을 1단계에서 할당한 구조의 크기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-132">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
     <span data-ttu-id="8f069-133">SQL_ATTR_PARAMS_PROCESSED_PTR 특성을 처리된 매개 변수 수를 보유하는 SQLUINTEGER 변수를 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-133">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="8f069-134">SQL_ATTR_PARAMS_STATUS_PTR을 매개 변수 상태 표시를 보유하는 SQLUSSMALLINT 변수의 배열[S]을 가리키도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-134">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="8f069-135">각 매개 변수 표식에 대해 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) 를 호출하여 1단계에서 할당한 구조 배열의 첫 번째 요소에 있는 해당 변수에 대한 매개 변수 데이터 값 및 데이터 길이 포인터를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-135">For each parameter marker, call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to point the parameter's data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="8f069-136">매개 변수가 실행 시 데이터 매개 변수인 경우 해당 매개 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-136">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
4.  <span data-ttu-id="8f069-137">바인딩된 매개 변수 버퍼 배열을 데이터 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-137">Fill the bound parameter buffer array with data values.</span></span>  
  
5.  <span data-ttu-id="8f069-138">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 를 호출하여 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-138">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="8f069-139">드라이버에서는 효율적으로 문을 각 매개 변수 집합에 대해 한 번씩 총 S번 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-139">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
6.  <span data-ttu-id="8f069-140">실행 시 데이터 입력 매개 변수를 사용하면 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 는 SQL_NEED_DATA를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-140">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="8f069-141">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) 및 [SQLPutData](../../native-client-odbc-api/sqlputdata.md)를 사용하여 데이터를 청크로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-141">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
 <span data-ttu-id="8f069-142">**참고** 열 단위 및 행 단위 바인딩은 일반적으로 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=59360) 보다는 [SQLPrepare 함수](https://go.microsoft.com/fwlink/?LinkId=58400) 및 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58399)와 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f069-142">**Note** Column-wise and row-wise binding are more typically used in conjunction with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) and [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) than with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f069-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f069-143">See Also</span></span>  
 [<span data-ttu-id="8f069-144">쿼리 실행 방법 도움말 항목 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="8f069-144">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
