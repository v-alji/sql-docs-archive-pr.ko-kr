---
title: SQLCloseCursor | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLCloseCursor function
ms.assetid: e7134d65-5c1c-4ae2-b119-d9b4b9a42483
author: rothja
ms.author: jroth
ms.openlocfilehash: 770a67432868516e5023d1cf0ff819501b4c130e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742023"
---
# <a name="sqlclosecursor"></a><span data-ttu-id="5d6d0-102">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="5d6d0-102">SQLCloseCursor</span></span>
  <span data-ttu-id="5d6d0-103">**SQLCloseCursor** 는 [SQLFreeStmt](sqlfreestmt.md) 를 SQL_CLOSE의 *옵션* 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-103">**SQLCloseCursor** replaces [SQLFreeStmt](sqlfreestmt.md) with an *Option* value of SQL_CLOSE.</span></span> <span data-ttu-id="5d6d0-104">**SQLCloseCursor**를 수신한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 보류 중인 결과 집합 행을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-104">On receipt of **SQLCloseCursor**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver discards pending result set rows.</span></span> <span data-ttu-id="5d6d0-105">문의 열 및 매개 변수 바인딩(있는 경우)은 **SQLCloseCursor**에 의해 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5d6d0-105">Note that the statement's column and parameter bindings (if any exist) are left unaltered by **SQLCloseCursor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d6d0-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d6d0-106">See Also</span></span>  
 <span data-ttu-id="5d6d0-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span><span class="sxs-lookup"><span data-stu-id="5d6d0-107">[SQLCloseCursor](https://go.microsoft.com/fwlink/?LinkId=59331) </span></span>  
 [<span data-ttu-id="5d6d0-108">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="5d6d0-108">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
