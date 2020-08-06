---
title: SQLGetStmtAttr | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: rothja
ms.author: jroth
ms.openlocfilehash: f1f9b6a0c0668540b566c9b3d7ede781c97a1dbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651672"
---
# <a name="sqlgetstmtattr"></a><span data-ttu-id="c09e8-102">SQLGetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="c09e8-102">SQLGetStmtAttr</span></span>
  <span data-ttu-id="c09e8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 드라이버는 SQLGetStmtAttr를 확장 하 여 드라이버별 문 특성을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver extends SQLGetStmtAttr to expose driver-specific statement attributes.</span></span>  
  
 <span data-ttu-id="c09e8-104">[SQLSetStmtAttr](sqlsetstmtattr.md) 에서는 읽기 및 쓰기 문 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-104">[SQLSetStmtAttr](sqlsetstmtattr.md) lists statement attributes that are both read and write.</span></span> <span data-ttu-id="c09e8-105">이 항목에서는 읽기 전용 문 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-105">This topic lists the read only statement attributes.</span></span>  
  
## <a name="sql_sopt_ss_current_command"></a><span data-ttu-id="c09e8-106">SQL_SOPT_SS_CURRENT_COMMAND</span><span class="sxs-lookup"><span data-stu-id="c09e8-106">SQL_SOPT_SS_CURRENT_COMMAND</span></span>  
 <span data-ttu-id="c09e8-107">SQL_SOPT_SS_CURRENT_COMMAND 특성은 명령 일괄 처리의 현재 명령을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-107">The SQL_SOPT_SS_CURRENT_COMMAND attribute exposes the current command of a command batch.</span></span> <span data-ttu-id="c09e8-108">반환 값은 일괄 처리에서 명령의 위치를 지정하는 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-108">The return is an integer that specifies the location of the command in the batch.</span></span> <span data-ttu-id="c09e8-109">*ValuePtr* 값은 SQLLEN 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-109">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
## <a name="sql_sopt_ss_nocount_status"></a><span data-ttu-id="c09e8-110">SQL_SOPT_SS_NOCOUNT_STATUS</span><span class="sxs-lookup"><span data-stu-id="c09e8-110">SQL_SOPT_SS_NOCOUNT_STATUS</span></span>  
 <span data-ttu-id="c09e8-111">SQL_SOPT_SS_NOCOUNT_STATUS 특성은 NOCOUNT 옵션의 현재 설정을 나타냅니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQLRowCount [를 호출할 때](sqlrowcount.md) 가 문의 영향을 받는 행 수를 보고할지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-111">The SQL_SOPT_SS_NOCOUNT_STATUS attribute indicates the current setting of the NOCOUNT option, which controls whether [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reports the numbers of rows affected by a statement when [SQLRowCount](sqlrowcount.md) is called.</span></span> <span data-ttu-id="c09e8-112">*ValuePtr* 값은 SQLLEN 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-112">The *ValuePtr* value is of type SQLLEN.</span></span>  
  
|<span data-ttu-id="c09e8-113">값</span><span class="sxs-lookup"><span data-stu-id="c09e8-113">Value</span></span>|<span data-ttu-id="c09e8-114">Description</span><span class="sxs-lookup"><span data-stu-id="c09e8-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c09e8-115">SQL_NC_OFF</span><span class="sxs-lookup"><span data-stu-id="c09e8-115">SQL_NC_OFF</span></span>|<span data-ttu-id="c09e8-116">NOCOUNT가 OFF입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-116">NOCOUNT is OFF.</span></span> <span data-ttu-id="c09e8-117">SQLRowCount는 영향을 받는 행의 수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-117">SQLRowCount returns number of rows affected.</span></span>|  
|<span data-ttu-id="c09e8-118">SQL_NC_ON</span><span class="sxs-lookup"><span data-stu-id="c09e8-118">SQL_NC_ON</span></span>|<span data-ttu-id="c09e8-119">NOCOUNT가 ON입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-119">NOCOUNT is ON.</span></span> <span data-ttu-id="c09e8-120">영향을 받는 행 수는 SQLRowCount에서 반환 되지 않으며 반환 된 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-120">The number of rows affected is not returned by SQLRowCount and the returned value is 0.</span></span>|  
  
 <span data-ttu-id="c09e8-121">SQLRowCount가 0을 반환 하는 경우 응용 프로그램은 SQL_SOPT_SS_NOCOUNT_STATUS를 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-121">If SQLRowCount returns 0, the application should test SQL_SOPT_SS_NOCOUNT_STATUS.</span></span> <span data-ttu-id="c09e8-122">SQL_NC_ON 반환 되는 경우 SQLRowCount의 값 0은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 행 개수를 반환 하지 못했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-122">If SQL_NC_ON is returned, the value of 0 from SQLRowCount only indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has not returned a row count.</span></span> <span data-ttu-id="c09e8-123">SQL_NC_OFF가 반환되는 경우 NOCOUNT가 해제되어 있음을 의미하고, SQLRowCount 값 0은 문이 어떤 행에도 적용되지 않았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-123">If SQL_NC_OFF is returned, it means that NOCOUNT is off and the value of 0 from SQLRowCount indicates that the statement did not affect any rows.</span></span>  
  
 <span data-ttu-id="c09e8-124">SQL_SOPT_SS_NOCOUNT_STATUS가 SQL_NC_OFF인 경우에는 응용 프로그램에서 SQLRowCount 값을 표시하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-124">Applications should not display the value of SQLRowCount when SQL_SOPT_SS_NOCOUNT_STATUS is SQL_NC_OFF.</span></span> <span data-ttu-id="c09e8-125">대규모 일괄 처리나 저장 프로시저에서는 여러 개의 SET NOCOUNT 문을 포함할 수 있으므로 SQL_SOPT_SS_NOCOUNT_STATUS가 일정하게 유지되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-125">Large batches or stored procedures can contain multiple SET NOCOUNT statements, so it cannot be assumed that SQL_SOPT_SS_NOCOUNT_STATUS remains constant.</span></span> <span data-ttu-id="c09e8-126">SQLRowCount가 0을 반환할 때마다이 옵션을 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-126">This option should be tested each time SQLRowCount returns 0.</span></span>  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a><span data-ttu-id="c09e8-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="c09e8-127">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
 <span data-ttu-id="c09e8-128">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT 특성은 쿼리 알림 요청에 대한 메시지 텍스트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-128">The SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT attribute returns the message text for the query notification request.</span></span>  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a><span data-ttu-id="c09e8-129">SQLGetStmtAttr 및 테이블 반환 매개 변수</span><span class="sxs-lookup"><span data-stu-id="c09e8-129">SQLGetStmtAttr and Table-valued Parameters</span></span>  
 <span data-ttu-id="c09e8-130">SQLGetStmtAttr를 호출 하 여 테이블 반환 매개 변수를 사용할 때 APD (응용 프로그램 매개 변수 설명자)의 SQL_SOPT_SS_PARAM_FOCUS 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c09e8-130">SQLGetStmtAttr can be called to get the value of SQL_SOPT_SS_PARAM_FOCUS in the application parameter descriptor (APD) when working with table-valued parameters.</span></span> <span data-ttu-id="c09e8-131">SQL_SOPT_SS_PARAM_FOCUS에 대한 자세한 내용은 [SQLSetStmtAttr](sqlsetstmtattr.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c09e8-131">For more information on SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="c09e8-132">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c09e8-132">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09e8-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c09e8-133">See Also</span></span>  
 <span data-ttu-id="c09e8-134">[SQLSetStmtAttr 함수](https://go.microsoft.com/fwlink/?LinkId=59370) </span><span class="sxs-lookup"><span data-stu-id="c09e8-134">[SQLSetStmtAttr Function](https://go.microsoft.com/fwlink/?LinkId=59370) </span></span>  
 [<span data-ttu-id="c09e8-135">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="c09e8-135">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
