---
title: 데이터 파일 및 서식 파일 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e0ee92f79e2c8cab9605db0188e01898df8c23e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742028"
---
# <a name="using-data-files-and-format-files"></a><span data-ttu-id="51486-102">데이터 파일 및 서식 파일 사용</span><span class="sxs-lookup"><span data-stu-id="51486-102">Using Data Files and Format Files</span></span>
  <span data-ttu-id="51486-103">가장 간단한 대량 복사 프로그램은 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-103">The simplest bulk copy program does the following:</span></span>  
  
1.  <span data-ttu-id="51486-104">[Bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) 를 호출 하 여 테이블 또는 뷰에서 데이터 파일로의 대량 복사 (BCP_OUT 설정)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-104">Calls [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to specify bulk copying out (set BCP_OUT) from a table or view to a data file.</span></span>  
  
2.  <span data-ttu-id="51486-105">[Bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) 를 호출 하 여 대량 복사 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-105">Calls [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="51486-106">데이터 파일은 기본 모드에서 만들어지기 때문에 테이블 또는 뷰에서 가져온 모든 열의 데이터는 데이터베이스에서와 동일한 형식으로 데이터 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="51486-106">The data file is created in native mode; therefore, data from all columns in the table or view are stored in the data file in the same format as in the database.</span></span> <span data-ttu-id="51486-107">그런 후 다음과 같은 단계를 수행하고 DB_OUT 대신 DB_IN을 설정하여 파일을 서버에 대량 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-107">The file can then be bulk copied into a server by using these same steps and setting DB_IN instead of DB_OUT.</span></span> <span data-ttu-id="51486-108">이 작업은 원본 테이블과 대상 테이블의 구조가 정확히 일치하는 경우에만 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-108">This works only if both the source and target tables have exactly the same structure.</span></span> <span data-ttu-id="51486-109">결과 데이터 파일은 **/n** (기본 모드) 스위치를 사용 하 여 **bcp** 유틸리티에 입력할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-109">The resulting data file can also be input to the **bcp** utility by using the **/n** (native mode) switch.</span></span>  
  
 <span data-ttu-id="51486-110">테이블이나 뷰에서 직접 복사하는 대신 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 결과 집합을 대량 복사하려면</span><span class="sxs-lookup"><span data-stu-id="51486-110">To bulk copy out the result set of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement instead of directly from a table or view:</span></span>  
  
1.  <span data-ttu-id="51486-111">**Bcp_init** 를 호출 하 여 대량 복사를 지정 하지만 테이블 이름에 NULL을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-111">Call **bcp_init** to specify bulk copying out, but specify NULL for the table name.</span></span>  
  
2.  <span data-ttu-id="51486-112">*Eoption* 을 BCPHINTS로 설정 하 고 *ivalue* 를 transact-sql 문을 포함 하는 sqltchar 문자열에 대 한 포인터로 설정 하 여 [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-112">Call [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) with *eOption* set to BCPHINTS and *iValue* set to a pointer to a SQLTCHAR string containing the Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="51486-113">**bcp_exec** 를 호출하여 대량 복사 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-113">Call **bcp_exec** to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="51486-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 결과 집합을 생성하는 모든 문이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be any statement that generates a result set.</span></span> <span data-ttu-id="51486-115">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 첫 번째 결과 집합이 포함된 데이터 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="51486-115">The data file is created containing the first result set of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="51486-116">대량 복사 시 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하여 결과 집합이 여러 개 생성될 경우 첫 번째 결과 집합 다음의 결과 집합은 모두 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="51486-116">Bulk copy ignores any result set after the first if the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple result sets.</span></span>  
  
 <span data-ttu-id="51486-117">열 데이터가 테이블과 다른 형식으로 저장 되는 데이터 파일을 만들려면 [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) 를 호출 하 여 변경할 열 수를 지정한 다음 해당 형식을 변경할 각 열에 대해 [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-117">To create a data file in which column data is stored in a different format than in the table, call [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to specify how many columns will be changed, then call [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column whose format you want to change.</span></span> <span data-ttu-id="51486-118">이 작업은 **bcp_init** 를 호출한 후 **bcp_exec**를 호출 하기 전에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51486-118">This is done after calling **bcp_init** but before calling **bcp_exec**.</span></span> <span data-ttu-id="51486-119">**bcp_colfmt** 데이터 파일에 열 데이터가 저장 되는 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-119">**bcp_colfmt** specifies the format in which the column's data is stored in the data file.</span></span> <span data-ttu-id="51486-120">대량 복사를 수행할 때 사용할 수 있습니다. **Bcp_colfmt** 를 사용 하 여 행 및 열 종결자를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-120">It can be used when bulk copying in or out. You can also use **bcp_colfmt** to set the row and column terminators.</span></span> <span data-ttu-id="51486-121">예를 들어 데이터에 탭 문자가 없는 경우 **bcp_colfmt** 를 사용 하 여 탭으로 구분 된 파일을 만들어 탭 문자를 각 열의 종결자로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-121">For example, if your data contains no tab characters, you can create a tab-delimited file by using **bcp_colfmt** to set the tab character as the terminator for each column.</span></span>  
  
 <span data-ttu-id="51486-122">**Bcp_colfmt**를 대량으로 복사 하 고 사용 하는 경우 **bcp_colfmt**를 마지막으로 호출한 후 [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) 를 호출 하 여 만든 데이터 파일을 설명 하는 서식 파일을 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-122">When bulk copying out and using **bcp_colfmt**, you can easily create a format file describing the data file you have created by calling [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) after the last call to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="51486-123">서식 파일에서 설명 하는 데이터 파일에서 대량 복사를 수행 하는 경우 **bcp_init** 후 **bcp_exec**전에 [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) 을 호출 하 여 서식 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="51486-123">When bulk copying in from a data file described by a format file, read the format file by calling [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) after **bcp_init** but before **bcp_exec**.</span></span>  
  
 <span data-ttu-id="51486-124">**Bcp_control** 함수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 파일에서로의 대량 복사에 대 한 몇 가지 옵션을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-124">The **bcp_control** function controls several options when bulk copying into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file.</span></span> <span data-ttu-id="51486-125">**bcp_control** 는 종료 전 최대 오류 수, 대량 복사를 시작할 파일의 행, 중지할 행 및 일괄 처리 크기와 같은 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51486-125">**bcp_control** sets options, such as the maximum number of errors before termination, the row in the file on which to start the bulk copy, the row to stop on, and the batch size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51486-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51486-126">See Also</span></span>  
 [<span data-ttu-id="51486-127">ODBC&#41;&#40;대량 복사 작업 수행</span><span class="sxs-lookup"><span data-stu-id="51486-127">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
