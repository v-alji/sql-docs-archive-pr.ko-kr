---
title: SQLFreeHandle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649512"
---
# <a name="sqlfreehandle"></a><span data-ttu-id="860d8-102">SQLFreeHandle</span><span class="sxs-lookup"><span data-stu-id="860d8-102">SQLFreeHandle</span></span>
  <span data-ttu-id="860d8-103">수동 커밋 모드에서 트랜잭션이 열려 있을 때 문 핸들에 대해 **SQLFreeHandle** 을 호출하면 보류 중인 변경 내용이 데이터베이스에 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="860d8-103">In manual-commit mode, calling **SQLFreeHandle** on a statement handle with an open transaction causes a rollback of pending changes to the database.</span></span> <span data-ttu-id="860d8-104">문 핸들에 대해 **SQLFreeHandle** 을 호출하면 항상 열려 있는 모든 커서가 닫히고 보류 중인 결과가 삭제되어 문 핸들에 연결된 모든 리소스가 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="860d8-104">Calling **SQLFreeHandle** on a statement handle always closes any open cursors and discards pending results, freeing all resources associated with the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860d8-105">참고 항목</span><span class="sxs-lookup"><span data-stu-id="860d8-105">See Also</span></span>  
 <span data-ttu-id="860d8-106">[SQLFreeHandle 함수](https://go.microsoft.com/fwlink/?LinkId=59345) </span><span class="sxs-lookup"><span data-stu-id="860d8-106">[SQLFreeHandle Function](https://go.microsoft.com/fwlink/?LinkId=59345) </span></span>  
 [<span data-ttu-id="860d8-107">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="860d8-107">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
