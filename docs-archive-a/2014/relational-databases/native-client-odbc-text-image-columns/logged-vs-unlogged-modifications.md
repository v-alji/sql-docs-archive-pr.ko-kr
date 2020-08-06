---
title: 기록 및 기록 되지 않는 수정 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8768acc75d18ea2236f0e9280e5d0c805e688107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741940"
---
# <a name="logged-vs-unlogged-modifications"></a><span data-ttu-id="f63c6-102">기록되는 수정 및 기록되지 않는 수정</span><span class="sxs-lookup"><span data-stu-id="f63c6-102">Logged vs. Unlogged Modifications</span></span>
  <span data-ttu-id="f63c6-103">응용 프로그램에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 드라이버가 **text**, **ntext**및 **image** 를 기록 하지 않도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f63c6-103">An application can request that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver not log **text**, **ntext**, and **image** modifications.</span></span> <span data-ttu-id="f63c6-104">하지만 이 옵션을 사용할 때는 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63c6-104">Care should be used with this option, however.</span></span> <span data-ttu-id="f63c6-105">**Text**, **ntext**또는 **image** 데이터가 중요 하지 않으며 데이터 소유자가 더 높은 성능을 위해 데이터를 복구 하는 기능을 절충 하는 경우에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f63c6-105">It should be used only for those situations where the **text**, **ntext**, or **image** data is not critical and data owners are willing to trade off the ability to recover data for higher performance.</span></span>  
  
 <span data-ttu-id="f63c6-106">**Text**, **ntext**및 **image** 수정의 로깅은 *특성* 매개 변수를 SQL_SOPT_SS_ TEXTPTR_LOGGING *로 설정 하 고 SQL_TL_OFF* SQL_TL_ON, [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 를 호출 하 여 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f63c6-106">The logging of **text**, **ntext**, and **image** modifications is controlled by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with the *Attribute* parameter set to SQL_SOPT_SS_ TEXTPTR_LOGGING and *ValuePtr* set to either SQL_TL_ON or SQL_TL_OFF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63c6-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f63c6-107">See Also</span></span>  
 [<span data-ttu-id="f63c6-108">text 및 image 열 관리</span><span class="sxs-lookup"><span data-stu-id="f63c6-108">Managing Text and Image Columns</span></span>](managing-text-and-image-columns.md)  
  
  
