---
title: SQLEndTran | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: rothja
ms.author: jroth
ms.openlocfilehash: e5d44756131b6133baec69e34da11055a965e2da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730663"
---
# <a name="sqlendtran"></a><span data-ttu-id="d4b66-102">SQLEndTran</span><span class="sxs-lookup"><span data-stu-id="d4b66-102">SQLEndTran</span></span>
  <span data-ttu-id="d4b66-103">기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 **SQLEndTran** 가 작업을 커밋하거나 롤백할 때 문과 연결된 커서를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b66-103">By default, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver closes a statement's associated cursor when **SQLEndTran** commits or rolls back an operation.</span></span> <span data-ttu-id="d4b66-104">서버 커서는 정적 상태가 될 때까지 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="d4b66-104">Server cursors are closed unless they are static.</span></span> <span data-ttu-id="d4b66-105">**SQLEndTran** 가 작업을 커밋하거나 롤백할 때 문과 연결된 커서의 동작은 [SQLSetConnectAttr](sqlsetconnectattr.md)을 통해 설정된, 드라이버 관련 ODBC 연결 특성인 SQL_COPT_SS_PRESERVE_CURSORS의 값에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b66-105">When **SQLEndTran** commits or rolls back an operation, the behavior of the statement's associated cursor is determined by the value of the driver-specific ODBC connection attribute SQL_COPT_SS_PRESERVE_CURSORS, set by [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b66-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4b66-106">See Also</span></span>  
 <span data-ttu-id="d4b66-107">[ODBC API 구현 세부 정보](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="d4b66-107">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="d4b66-108">SQLEndTran 함수(SQLEndTran Function)</span><span class="sxs-lookup"><span data-stu-id="d4b66-108">SQLEndTran Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59342)  
  
  
