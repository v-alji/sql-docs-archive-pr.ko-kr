---
title: SQLProcedures Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: rothja
ms.author: jroth
ms.openlocfilehash: e37f15841a36eb95c1e9263d137ba2734d622367
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660526"
---
# <a name="sqlprocedures"></a><span data-ttu-id="08dcc-102">SQLProcedures</span><span class="sxs-lookup"><span data-stu-id="08dcc-102">SQLProcedures</span></span>
  <span data-ttu-id="08dcc-103">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 저장 프로시저는 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-103">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures return a value.</span></span> <span data-ttu-id="08dcc-104">**Sqlprocedures** 는 결과 집합 열 PROCEDURE_TYPE에 대 한 SQL_PT_FUNCTION를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-104">**SQLProcedures** reports SQL_PT_FUNCTION for the result set column PROCEDURE_TYPE.</span></span>  
  
 <span data-ttu-id="08dcc-105">**Sqlprocedures** *CatalogName, SchemaName* 또는 *ProcName* 매개 변수에 대 한 값이 있는지 여부를 SQL_SUCCESS을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-105">**SQLProcedures** returns SQL_SUCCESS whether or not values exist for *CatalogName, SchemaName,* or *ProcName* parameters.</span></span> <span data-ttu-id="08dcc-106">이러한 매개 변수에 잘못 된 값이 사용 되는 경우 **Sqlfetch** SQL_NO_DATA 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-106">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="08dcc-107">**Sqlprocedures** 는 정적 서버 커서에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-107">**SQLProcedures** can be executed on a static server cursor.</span></span> <span data-ttu-id="08dcc-108">업데이트할 수 있는 (동적 또는 키 집합) 커서에 대해 **Sqlprocedures** 를 실행 하려고 하면 커서 유형이 변경 되었음을 나타내는 SQL_SUCCESS_WITH_INFO 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-108">An attempt to execute **SQLProcedures** on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO, indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="08dcc-109">**Sqlprocedures** 는 이름이 *ProcName* 와 일치 하 고 현재 사용자가 실행 하거나 현재 사용자에 게 VIEW DEFINITION 권한이 부여 된 프로시저에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="08dcc-109">**SQLProcedures** returns information about any procedures whose names match *ProcName* and can be executed by the current user, or for which the current user has been granted VIEW DEFINITION permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dcc-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08dcc-110">See Also</span></span>  
 <span data-ttu-id="08dcc-111">[SQLProcedures 함수](https://go.microsoft.com/fwlink/?LinkId=59364) </span><span class="sxs-lookup"><span data-stu-id="08dcc-111">[SQLProcedures Function](https://go.microsoft.com/fwlink/?LinkId=59364) </span></span>  
 [<span data-ttu-id="08dcc-112">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="08dcc-112">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
