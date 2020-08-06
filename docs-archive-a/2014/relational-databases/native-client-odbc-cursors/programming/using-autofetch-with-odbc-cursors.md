---
title: ODBC 커서와 함께 자동 인출 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, autofetch
- autofetch option
- cursors [ODBC], autofetch
ms.assetid: 57bd55f4-8945-4d8d-9f58-d30c81d2a514
author: rothja
ms.author: jroth
ms.openlocfilehash: e3d9374cf9ceab4a7e73cc0059783486f2bf9c41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653338"
---
# <a name="using-autofetch-with-odbc-cursors"></a><span data-ttu-id="f51ad-102">ODBC 커서로 자동 인출 사용</span><span class="sxs-lookup"><span data-stu-id="f51ad-102">Using Autofetch with ODBC Cursors</span></span>
  <span data-ttu-id="f51ad-103">인스턴스에 연결 된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 드라이버는 서버 커서 유형을 사용할 때 자동 인출 옵션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51ad-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports an autofetch option when using any server cursor type.</span></span> <span data-ttu-id="f51ad-104">자동 인출를 사용 하면 커서를 여는 **Sqlexecute** 또는 **sqlexecdirect** 함수에도 암시적 [sqlfetchscroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f51ad-104">With autofetch, the **SQLExecute** or **SQLExecDirect** function that opens the cursor also has an implicit [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)(SQL_FIRST) function.</span></span> <span data-ttu-id="f51ad-105">문 실행의 일부로 첫 번째 행 집합을 구성하는 행이 바인딩된 애플리케이션 변수에 반환되므로 네트워크를 통해 다시 서버로 왕복할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f51ad-105">The rows comprising the first rowset are returned to the bound application variables as part of the statement execution, saving another roundtrip across the network to the server.</span></span> <span data-ttu-id="f51ad-106">자동 인출 옵션을 사용 하는 경우 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 는 지원 되지 않습니다. 결과 집합 열은 프로그램 변수에 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f51ad-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported when the autofetch option is enabled; the result set columns must be bound to program variables.</span></span>  
  
 <span data-ttu-id="f51ad-107">애플리케이션은 드라이버별 SQL_SOPT_SS_CURSOR_OPTIONS 문 특성을 SQL_CO_AF로 설정하여 자동 인출을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f51ad-107">Applications request autofetch by setting the driver-specific SQL_SOPT_SS_CURSOR_OPTIONS statement attribute to SQL_CO_AF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51ad-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f51ad-108">See Also</span></span>  
 [<span data-ttu-id="f51ad-109">ODBC&#41;&#40;커서 프로그래밍 정보</span><span class="sxs-lookup"><span data-stu-id="f51ad-109">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
