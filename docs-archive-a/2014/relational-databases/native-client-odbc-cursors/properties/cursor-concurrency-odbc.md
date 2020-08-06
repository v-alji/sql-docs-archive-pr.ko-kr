---
title: 커서 동시성 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: rothja
ms.author: jroth
ms.openlocfilehash: c47f24152978fedf8f2c3d49ec3b721969712814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653339"
---
# <a name="cursor-concurrency-odbc"></a><span data-ttu-id="73aee-102">커서 동시성(ODBC)</span><span class="sxs-lookup"><span data-stu-id="73aee-102">Cursor Concurrency (ODBC)</span></span>
  <span data-ttu-id="73aee-103">커서 작업은 커서 유형처럼 애플리케이션에서 설정한 동시성 옵션의 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="73aee-103">Cursor operations, like cursor types, are affected by the concurrency options set by the application.</span></span> <span data-ttu-id="73aee-104">동시성 옵션은 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)의 SQL_ATTR_CONCURRENCY 옵션을 사용 하 여 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="73aee-104">Concurrency options are set using the SQL_ATTR_CONCURRENCY option of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span> <span data-ttu-id="73aee-105">동시성 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="73aee-105">The concurrency types are:</span></span>  
  
-   <span data-ttu-id="73aee-106">읽기 전용(SQL_CONCUR_READONLY)</span><span class="sxs-lookup"><span data-stu-id="73aee-106">Read-only (SQL_CONCUR_READONLY)</span></span>  
  
-   <span data-ttu-id="73aee-107">값(SQL_CONCUR_VALUES)</span><span class="sxs-lookup"><span data-stu-id="73aee-107">Values (SQL_CONCUR_VALUES)</span></span>  
  
-   <span data-ttu-id="73aee-108">행 버전(SQL_CONCUR_ROWVER)</span><span class="sxs-lookup"><span data-stu-id="73aee-108">Row version (SQL_CONCUR_ROWVER)</span></span>  
  
-   <span data-ttu-id="73aee-109">잠금(SQL_CONCUR_LOCK)</span><span class="sxs-lookup"><span data-stu-id="73aee-109">Lock (SQL_CONCUR_LOCK)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73aee-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73aee-110">See Also</span></span>  
 [<span data-ttu-id="73aee-111">커서 속성</span><span class="sxs-lookup"><span data-stu-id="73aee-111">Cursor Properties</span></span>](cursor-properties.md)  
  
  
