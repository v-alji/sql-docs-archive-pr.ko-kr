---
title: 서버 커서 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: rothja
ms.author: jroth
ms.openlocfilehash: e596af3c46849313d813ce2d7f1dab2a7425c090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649062"
---
# <a name="using-server-cursors"></a><span data-ttu-id="0ec6c-102">서버 커서 사용</span><span class="sxs-lookup"><span data-stu-id="0ec6c-102">Using Server Cursors</span></span>
  <span data-ttu-id="0ec6c-103">Odbc 응용 프로그램에서 ODBC 커서 특성을 기본값 이외의 값으로 설정 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버는 동일한 유형의 API 서버 커서를 구현 하도록 서버에 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-103">If an ODBC application sets any of the ODBC cursor attributes to anything other than the defaults, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver requests the server to implement an API server cursor of the same type.</span></span> <span data-ttu-id="0ec6c-104">API 서버 커서가 사용되면 클라이언트의 메모리가 확보되고 클라이언트와 서버 간의 네트워크 트래픽이 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-104">Using API server cursors frees memory on the client and can significantly reduce network traffic between the client and server.</span></span>  
  
 <span data-ttu-id="0ec6c-105">API 서버 커서의 단점은 현재 모든 SQL 문을 지원하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-105">A potential drawback of API server cursors is that they currently do not support all SQL statements.</span></span> <span data-ttu-id="0ec6c-106">API 서버 커서는 다음을 실행하는 데 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-106">API server cursors cannot be used to execute:</span></span>  
  
-   <span data-ttu-id="0ec6c-107">여러 결과 집합을 반환하는 일괄 처리 또는 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="0ec6c-107">Batches or stored procedures that return multiple result sets.</span></span>  
  
-   <span data-ttu-id="0ec6c-108">COMPUTE, COMPUTE BY, FOR BROWSE 또는 INTO 절을 포함하는 SELECT 문</span><span class="sxs-lookup"><span data-stu-id="0ec6c-108">SELECT statements that contain COMPUTE, COMPUTE BY, FOR BROWSE, or INTO clauses.</span></span>  
  
-   <span data-ttu-id="0ec6c-109">원격 저장 프로시저를 참조하는 EXECUTE 문</span><span class="sxs-lookup"><span data-stu-id="0ec6c-109">An EXECUTE statement referencing a remote stored procedure.</span></span>  
  
 <span data-ttu-id="0ec6c-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결된 경우 서버 커서를 사용하는 이러한 특징이 있는 문을 실행하면 커서가 기본 결과 집합으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-110">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], executing a statement with these characteristics using a server cursor causes the cursor being converted to a default result set.</span></span> <span data-ttu-id="0ec6c-111">그러나 이전 버전의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결된 경우에는 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="0ec6c-111">When connected to earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it causes an error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ec6c-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0ec6c-112">See Also</span></span>  
 [<span data-ttu-id="0ec6c-113">커서 구현 방법</span><span class="sxs-lookup"><span data-stu-id="0ec6c-113">How Cursors Are Implemented</span></span>](how-cursors-are-implemented.md)  
  
  