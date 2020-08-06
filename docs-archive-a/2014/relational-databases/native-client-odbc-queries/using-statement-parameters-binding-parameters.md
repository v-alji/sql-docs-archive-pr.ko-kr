---
title: 바인딩 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3402a7efce43d0ce94a20c93504ac1dcb2c7b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646395"
---
# <a name="binding-parameters"></a><span data-ttu-id="55d2a-102">매개 변수 바인딩</span><span class="sxs-lookup"><span data-stu-id="55d2a-102">Binding Parameters</span></span>
  <span data-ttu-id="55d2a-103">SQL 문을 실행하려면 먼저 SQL 문의 각 매개 변수 표식을 애플리케이션의 변수에 연결하거나 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-103">Each parameter marker in an SQL statement must be associated, or bound, to a variable in the application before the statement can be executed.</span></span> <span data-ttu-id="55d2a-104">[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) 함수를 호출 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-104">This is done by calling the [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) function.</span></span> <span data-ttu-id="55d2a-105">**SQLBindParameter** 는 프로그램 변수 (주소, C 데이터 형식 등)를 드라이버에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-105">**SQLBindParameter** describes the program variable (address, C data type, and so on) to the driver.</span></span> <span data-ttu-id="55d2a-106">또한 매개 변수 표식의 서수 값을 나타낸 후 해당 표식이 나타내는 SQL 개체의 특성(SQL 데이터 형식, 전체 자릿수 등)을 설명하여 매개 변수 표식을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-106">It also identifies the parameter marker by indicating its ordinal value and then describes the characteristics of the SQL object it represents (SQL data type, precision, and so on).</span></span>

 <span data-ttu-id="55d2a-107">문을 실행하기 전이라면 언제라도 매개 변수 표식을 바인딩하거나 다시 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-107">Parameter markers can be bound or rebound at any time before a statement is executed.</span></span> <span data-ttu-id="55d2a-108">매개 변수 바인딩은 다음 호출 중 하나가 발생하기 전까지 계속 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-108">A parameter binding remains in effect until one of the following occurs:</span></span>

-   <span data-ttu-id="55d2a-109">*Option* 매개 변수를 SQL_RESET_PARAMS 설정 하 여 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) 를 호출 하면 문 핸들에 바인딩된 모든 매개 변수가 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-109">A call to [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the *Option* parameter set to SQL_RESET_PARAMS frees all parameters bound to the statement handle.</span></span>

-   <span data-ttu-id="55d2a-110">*Parameternumber* 가 바인딩된 매개 변수 표식의 서 수로 설정 된 **SQLBindParameter** 에 대 한 호출은 자동으로 이전 바인딩을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-110">A call to **SQLBindParameter** with *ParameterNumber* set to the ordinal of a bound parameter marker automatically releases the previous binding.</span></span>

 <span data-ttu-id="55d2a-111">애플리케이션에서 매개 변수를 프로그램 변수의 배열에 바인딩하여 SQL 문을 일괄 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-111">An application can also bind parameters to arrays of program variables to process an SQL statement in batches.</span></span> <span data-ttu-id="55d2a-112">배열 바인딩에는 다음과 같은 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-112">There are two types of array binding:</span></span>

-   <span data-ttu-id="55d2a-113">열 단위 바인딩은 각 매개 변수가 고유한 변수 배열에 바인딩될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-113">Column-wise binding is done when each individual parameter is bound to its own array of variables.</span></span>

     <span data-ttu-id="55d2a-114">열 단위 바인딩은 *특성* 을 SQL_ATTR_PARAM_BIND_TYPE *로 설정 하 고 SQL_PARAM_BIND_BY_COLUMN* 로 설정 된 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 를 호출 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-114">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to SQL_PARAM_BIND_BY_COLUMN.</span></span>

-   <span data-ttu-id="55d2a-115">행 단위 바인딩은 SQL 문의 모든 매개 변수가 매개 변수의 개별 변수를 포함하는 구조체 배열에 하나의 단위로 바인딩될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-115">Row-wise binding is done when all of the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>

     <span data-ttu-id="55d2a-116">행 단위 바인딩은 *특성* 을 SQL_ATTR_PARAM_BIND_TYPE로 설정 하 고 *valueptr* 을 프로그램 변수를 포함 하는 구조체의 크기로 설정 하 여 **SQLSetStmtAttr** 를 호출 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-116">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to the size of the structure holding the program variables.</span></span>

 <span data-ttu-id="55d2a-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 문자 또는 이진 문자열 매개 변수를 서버에 보낼 때 **SQLBindParameter** *columnsize* 매개 변수에 지정 된 길이까지 값을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sends character or binary string parameters to the server, it pads the values to the length specified in **SQLBindParameter** *ColumnSize* parameter.</span></span> <span data-ttu-id="55d2a-118">ODBC 2.x 응용 프로그램에서 *Columnsize*에 대해 0을 지정 하는 경우 드라이버는 매개 변수 값을 데이터 형식의 전체 자릿수로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-118">If an ODBC 2.x application specifies 0 for *ColumnSize*, the driver pads the parameter value to the precision of the data type.</span></span> <span data-ttu-id="55d2a-119">전체 자릿수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서버에 연결할 경우 8000이고 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 경우 255입니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-119">The precision is 8000 when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers, 255 when connected to earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="55d2a-120">*Columnsize* 는 변형 열의 경우 바이트 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-120">*ColumnSize* is in bytes for variant columns.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="55d2a-121">는 저장 프로시저 매개 변수의 이름 정의를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-121">supports defining names for stored procedure parameters.</span></span> <span data-ttu-id="55d2a-122">ODBC 3.5에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저를 호출할 때 사용되는 명명된 매개 변수에 대한 지원이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-122">ODBC 3.5 also introduced support for named parameters used when calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="55d2a-123">이 지원을 통해 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-123">This support can be used to:</span></span>

-   <span data-ttu-id="55d2a-124">저장 프로시저를 호출하고 저장 프로시저에 대해 정의된 매개 변수의 하위 집합에 대한 값을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-124">Call a stored procedure and provide values for a subset of the parameters defined for the stored procedure.</span></span>

-   <span data-ttu-id="55d2a-125">저장 프로시저를 만들 때 지정한 것과 다른 순서로 애플리케이션에서 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-125">Specify the parameters in a different order in the application than the order specified when the stored procedure was created.</span></span>

 <span data-ttu-id="55d2a-126">명명 된 매개 변수는 [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` 문 또는 ODBC CALL 이스케이프 시퀀스를 사용 하 여 저장 프로시저를 실행 하는 경우에만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-126">Named parameters are only supported when using the [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` statement or the ODBC CALL escape sequence to execute a stored procedure.</span></span>

 <span data-ttu-id="55d2a-127">저장 프로시저 매개 변수에 `SQL_DESC_NAME`을 설정할 경우 쿼리의 모든 저장 프로시저 매개 변수도 `SQL_DESC_NAME`을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-127">If `SQL_DESC_NAME` is set for a stored procedure parameter, all stored procedure parameters in the query should also set `SQL_DESC_NAME`.</span></span>  <span data-ttu-id="55d2a-128">매개 변수가 설정 된 저장 프로시저 호출에 리터럴이 사용 되는 경우 `SQL_DESC_NAME` 리터럴은 *' name* = *value*' 형식을 사용 해야 합니다. 여기서 *name* 은 저장 프로시저 매개 변수 이름 (예: @p1 )입니다.</span><span class="sxs-lookup"><span data-stu-id="55d2a-128">If literals are used in stored procedure calls, where parameters have `SQL_DESC_NAME` set, the literals should use the format *'name*=*value*', where *name* is the stored procedure parameter name (for example, @p1).</span></span> <span data-ttu-id="55d2a-129">자세한 내용은 [이름으로 매개 변수 바인딩 (명명 된 매개 변수)](https://go.microsoft.com/fwlink/?LinkId=167215)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="55d2a-129">For more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkId=167215).</span></span>

## <a name="see-also"></a><span data-ttu-id="55d2a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55d2a-130">See Also</span></span>
 [<span data-ttu-id="55d2a-131">문 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="55d2a-131">Using Statement Parameters</span></span>](using-statement-parameters.md)


