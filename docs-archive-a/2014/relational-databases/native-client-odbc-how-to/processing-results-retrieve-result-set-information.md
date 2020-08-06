---
title: 결과 집합 정보 검색 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f7ed275eb9b6558a77160c3c7fb2fc233c199cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649039"
---
# <a name="retrieve-result-set-information-odbc"></a><span data-ttu-id="269bf-102">결과 집합 정보 검색(ODBC)</span><span class="sxs-lookup"><span data-stu-id="269bf-102">Retrieve Result Set Information (ODBC)</span></span>
    
### <a name="to-get-information-about-a-result-set"></a><span data-ttu-id="269bf-103">결과 집합에 대한 정보를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="269bf-103">To get information about a result set</span></span>  
  
1.  <span data-ttu-id="269bf-104">[Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md) 를 호출 하 여 결과 집합의 열 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="269bf-104">Call [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns in the result set.</span></span>  
  
2.  <span data-ttu-id="269bf-105">결과 집합의 각 열에 대해 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="269bf-105">For each column in the result set:</span></span>  
  
    -   <span data-ttu-id="269bf-106">[SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) 를 호출 하 여 결과 열에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="269bf-106">Call [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to get information about the result column.</span></span>  
  
     <span data-ttu-id="269bf-107">또는</span><span class="sxs-lookup"><span data-stu-id="269bf-107">Or</span></span>  
  
    -   <span data-ttu-id="269bf-108">[Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md) 를 호출 하 여 결과 열에 대 한 특정 설명자 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="269bf-108">Call [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) to get specific descriptor information about the result column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="269bf-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="269bf-109">See Also</span></span>  
 <span data-ttu-id="269bf-110">[결과 처리 방법 도움말 항목 &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="269bf-110">[Processing Results How-to Topics &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="269bf-111">ODBC&#41;&#40;결과 집합의 특징 확인</span><span class="sxs-lookup"><span data-stu-id="269bf-111">Determining the Characteristics of a Result Set &#40;ODBC&#41;</span></span>](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
