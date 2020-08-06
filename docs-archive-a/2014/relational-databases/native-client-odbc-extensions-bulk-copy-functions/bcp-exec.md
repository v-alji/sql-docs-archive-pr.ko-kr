---
title: bcp_exec | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: rothja
ms.author: jroth
ms.openlocfilehash: f925c6cb1e3a36f79ba4f560a06c5b6d499ece4e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638740"
---
# <a name="bcp_exec"></a><span data-ttu-id="6bc38-102">bcp_exec</span><span class="sxs-lookup"><span data-stu-id="6bc38-102">bcp_exec</span></span>
  <span data-ttu-id="6bc38-103">데이터베이스 테이블과 사용자 파일 간에 데이터에 대한 전체 대량 복사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-103">Executes a complete bulk copy of data between a database table and a user file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc38-104">구문</span><span class="sxs-lookup"><span data-stu-id="6bc38-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6bc38-105">인수</span><span class="sxs-lookup"><span data-stu-id="6bc38-105">Arguments</span></span>  
 <span data-ttu-id="6bc38-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="6bc38-106">*hdbc*</span></span>  
 <span data-ttu-id="6bc38-107">대량 복사가 가능한 ODBC 연결 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="6bc38-108">*pnRowsProcessed*</span><span class="sxs-lookup"><span data-stu-id="6bc38-108">*pnRowsProcessed*</span></span>  
 <span data-ttu-id="6bc38-109">DBINT에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-109">Is a pointer to a DBINT.</span></span> <span data-ttu-id="6bc38-110">**bcp_exec** 함수는 성공적으로 복사된 행 수로 이 DBINT를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-110">The **bcp_exec** function fills this DBINT with the number of rows successfully copied.</span></span> <span data-ttu-id="6bc38-111">*pnRowsProcessed* 가 NULL이면 **bcp_exec**에서 이 인수를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-111">If *pnRowsProcessed* is NULL, it is ignored by **bcp_exec**.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6bc38-112">반환</span><span class="sxs-lookup"><span data-stu-id="6bc38-112">Returns</span></span>  
 <span data-ttu-id="6bc38-113">SUCCEED, SUCCEED_ASYNC 또는 FAIL.</span><span class="sxs-lookup"><span data-stu-id="6bc38-113">SUCCEED, SUCCEED_ASYNC, or FAIL.</span></span> <span data-ttu-id="6bc38-114">모든 행이 복사되면 **bcp_exec** 함수가 SUCCEED를 반환합니다</span><span class="sxs-lookup"><span data-stu-id="6bc38-114">The **bcp_exec** function returns SUCCEED if all rows are copied.</span></span> <span data-ttu-id="6bc38-115">비동기 대량 복사 작업이 보류 중이면**bcp_exec** 가 SUCCEED_ASYNC를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-115">**bcp_exec** returns SUCCEED_ASYNC if an asynchronous bulk copy operation is still outstanding.</span></span> <span data-ttu-id="6bc38-116">전체 오류가 발생 하거나 오류를 생성 하는 행의 수가 [bcp_control](bcp-control.md)를 사용 하 여 BCPMAXERRS에 지정 된 값에 도달 하면 **bcp_exec** 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-116">**bcp_exec** returns FAIL if a complete failure occurs, or if the number of rows generating errors reaches the value specified for BCPMAXERRS using [bcp_control](bcp-control.md).</span></span> <span data-ttu-id="6bc38-117">BCPMAXERRS의 기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-117">BCPMAXERRS defaults to 10.</span></span> <span data-ttu-id="6bc38-118">BCPMAXERRS 옵션은 데이터 파일에서 행을 읽는 동안 공급자가 발견하는 구문 오류의 수에만 영향을 주고 서버로 전송되는 행 수에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-118">The BCPMAXERRS option affects only the syntax errors detected by the provider while reading the rows from the data file (and not the rows sent to the server).</span></span> <span data-ttu-id="6bc38-119">행에서 오류를 발견하면 서버에서 일괄 처리를 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-119">Server aborts the batch when it detects an error with a row.</span></span> <span data-ttu-id="6bc38-120">성공적으로 복사된 행 수를 보려면 *pnRowsProcessed* 매개 변수를 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="6bc38-120">Check the *pnRowsProcessed* parameter for the number of rows successfully copied.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bc38-121">설명</span><span class="sxs-lookup"><span data-stu-id="6bc38-121">Remarks</span></span>  
 <span data-ttu-id="6bc38-122">이 함수는 *bcp_init* 의 [eDirection](bcp-init.md)매개 변수 값에 따라 사용자 파일에서 데이터베이스 테이블로 또는 데이터베이스 테이블에서 사용자 파일로 데이터를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-122">This function copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter in [bcp_init](bcp-init.md).</span></span>  
  
 <span data-ttu-id="6bc38-123">**bcp_exec**를 호출하기 전에 올바른 사용자 파일 이름을 지정하여 **bcp_init** 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-123">Before calling **bcp_exec**, call **bcp_init** with a valid user file name.</span></span> <span data-ttu-id="6bc38-124">그렇게 하지 않으면 오류가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-124">Failure to do so results in an error.</span></span>  
  
 <span data-ttu-id="6bc38-125">**bcp_exec** 는 무한정 보류될 수 있는 유일한 대량 복사 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-125">**bcp_exec** is the only bulk copy function that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="6bc38-126">따라서 비동기 모드를 지원하는 유일한 대량 복사 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-126">It is therefore the only bulk copy function that supports asynchronous mode.</span></span> <span data-ttu-id="6bc38-127">비동기 모드를 설정하려면 [bcp_exec](../native-client-odbc-api/sqlsetconnectattr.md) 를 호출하기 전에 **SQLSetConnectAttr**을 사용하여 SQL_ATTR_ASYNC_ENABLE을 SQL_ASYNC_ENABLE_ON으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-127">To set asynchronous mode, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set SQL_ATTR_ASYNC_ENABLE to SQL_ASYNC_ENABLE_ON before calling **bcp_exec**.</span></span> <span data-ttu-id="6bc38-128">완료 테스트를 하려면 같은 매개 변수를 사용하여 **bcp_exec** 를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-128">To test for completion, call **bcp_exec** with the same parameters.</span></span> <span data-ttu-id="6bc38-129">대량 복사가 완료되지 않은 경우 **bcp_exec** 가 SUCCEED_ASYNC를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-129">If the bulk copy has not yet completed, **bcp_exec** returns SUCCEED_ASYNC.</span></span> <span data-ttu-id="6bc38-130">또한 서버로 전송된 행 수에 대한 상태 개수를 *pnRowsProcessed* 에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-130">It also returns in *pnRowsProcessed* a status count of the number of rows that have been sent to the server.</span></span> <span data-ttu-id="6bc38-131">서버로 전송된 행은 일괄 처리의 끝에 도달할 때까지 커밋되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-131">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
 <span data-ttu-id="6bc38-132">에서 시작 하는 대량 복사의 주요 변경 내용에 대 한 자세한 내용은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [ODBC&#41;&#40;대량 복사 작업 수행 ](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6bc38-132">For information about a breaking change in bulk-copying beginning in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], see [Performing Bulk Copy Operations &#40;ODBC&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc38-133">예제</span><span class="sxs-lookup"><span data-stu-id="6bc38-133">Example</span></span>  
 <span data-ttu-id="6bc38-134">다음 예에서는 **bcp_exec**를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6bc38-134">The following example shows how to use **bcp_exec**:</span></span>  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bc38-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bc38-135">See Also</span></span>  
 [<span data-ttu-id="6bc38-136">Bulk Copy Functions</span><span class="sxs-lookup"><span data-stu-id="6bc38-136">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
