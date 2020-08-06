---
title: SQLExecute | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: rothja
ms.author: jroth
ms.openlocfilehash: 514436c65ef103cafae2189a03b560255b447eda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649980"
---
# <a name="sqlexecute"></a><span data-ttu-id="545c6-102">SQLExecute</span><span class="sxs-lookup"><span data-stu-id="545c6-102">SQLExecute</span></span>
  <span data-ttu-id="545c6-103">SQL_SOPT_SS_PARAM_FOCUS statement 특성이 0으로 설정 되지 않은 경우 SQLExecute는 SQL_ERROR를 반환 하 고 SQLSTATE = HY024 및 "잘못 된 특성 값, SQL_SOPT_SS_PARAM_FOCUS (실행 시 0 이어야 함)" 라는 메시지와 함께 진단 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="545c6-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not set to 0, SQLExecute will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="545c6-104">SQL_SOPT_SS_PARAM_FOCUS에 대한 자세한 내용은 [SQLSetStmtAttr](sqlsetstmtattr.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="545c6-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="545c6-105">설명</span><span class="sxs-lookup"><span data-stu-id="545c6-105">Remarks</span></span>  
 <span data-ttu-id="545c6-106">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="545c6-106">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545c6-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="545c6-107">See Also</span></span>  
 <span data-ttu-id="545c6-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span><span class="sxs-lookup"><span data-stu-id="545c6-108">[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708) </span></span>  
 [<span data-ttu-id="545c6-109">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="545c6-109">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
