---
title: SQLExecDirect | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: rothja
ms.author: jroth
ms.openlocfilehash: 68188506546e7b4a5dd4c05bc9a94cbf34300001
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649989"
---
# <a name="sqlexecdirect"></a><span data-ttu-id="c2130-102">SQLExecDirect</span><span class="sxs-lookup"><span data-stu-id="c2130-102">SQLExecDirect</span></span>
  <span data-ttu-id="c2130-103">SQL_SOPT_SS_PARAM_FOCUS statement 특성이 0이 아니면 SQLExecDirect는 SQL_ERROR를 반환 하 고 SQLSTATE = HY024 및 "잘못 된 특성 값 SQL_SOPT_SS_PARAM_FOCUS (실행 시 0 이어야 함)" 라는 메시지가 포함 된 진단 레코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2130-103">If the statement attribute SQL_SOPT_SS_PARAM_FOCUS is not 0, SQLExecDirect will return SQL_ERROR and generate a diagnostic record with SQLSTATE=HY024 and the message "Invalid attribute value, SQL_SOPT_SS_PARAM_FOCUS (must be zero at execution time)".</span></span> <span data-ttu-id="c2130-104">SQL_SOPT_SS_PARAM_FOCUS에 대한 자세한 내용은 [SQLSetStmtAttr](sqlsetstmtattr.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c2130-104">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="c2130-105">테이블 반환 매개 변수에 대 한 자세한 내용은 [ODBC&#41;&#40;테이블 반환 매개 변수 ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c2130-105">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2130-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2130-106">See Also</span></span>  
 <span data-ttu-id="c2130-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span><span class="sxs-lookup"><span data-stu-id="c2130-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709) </span></span>  
 [<span data-ttu-id="c2130-108">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="c2130-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
