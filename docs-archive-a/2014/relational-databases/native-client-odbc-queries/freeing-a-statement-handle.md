---
title: 문 핸들 해제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- reusing statement handles
- freeing statement handles
- statements [ODBC], statement handles
- SQLFreeStmt function
- ODBC applications, statements
- statement handles [ODBC]
ms.assetid: 96fdff84-0ca7-460a-a240-94ee826ea41c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d7a1e93d222e2b87058bc878f7eca85313b4108
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646397"
---
# <a name="freeing-a-statement-handle"></a><span data-ttu-id="43dba-102">문 핸들 해제</span><span class="sxs-lookup"><span data-stu-id="43dba-102">Freeing a Statement Handle</span></span>
  <span data-ttu-id="43dba-103">문 핸들을 다시 사용하는 것이 문 핸들을 삭제한 다음 새로 할당하는 것보다 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-103">It is more efficient to reuse statement handles than to drop them and allocate new ones.</span></span> <span data-ttu-id="43dba-104">따라서 문 핸들에 대해 새 SQL 문을 실행하기 전에 애플리케이션에서 현재 문 설정이 적절한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-104">Before executing a new SQL statement on a statement handle, applications should verify that the current statement settings are appropriate.</span></span> <span data-ttu-id="43dba-105">이러한 설정에는 문 특성, 매개 변수 바인딩 및 결과 집합 바인딩이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-105">These include statement attributes, parameter bindings, and result set bindings.</span></span> <span data-ttu-id="43dba-106">일반적으로 이전 SQL 문에 대 한 매개 변수 및 결과 집합은 SQL_RESET_PARAMS와 SQL_UNBIND 옵션을 사용 하 여 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) 를 호출한 다음 새 SQL 문에 대해 다시 바인딩하여 바인딩 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-106">Generally, parameters and result sets for the old SQL statement must be unbound by calling [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the SQL_RESET_PARAMS and SQL_UNBIND options and then re-bound for the new SQL statement.</span></span>  
  
 <span data-ttu-id="43dba-107">응용 프로그램에서 문 사용을 마치면 [Sqlfreehandle](../native-client-odbc-api/sqlfreehandle.md) 을 호출 하 여 문을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-107">When the application has finished using the statement, it calls [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) to free the statement.</span></span> <span data-ttu-id="43dba-108">**Sqldisconnect** 는 연결에서 모든 문을 자동으로 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="43dba-108">Note that **SQLDisconnect** automatically frees all statements on a connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43dba-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="43dba-109">See Also</span></span>  
 [<span data-ttu-id="43dba-110">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="43dba-110">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
