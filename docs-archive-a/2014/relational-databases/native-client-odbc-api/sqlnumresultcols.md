---
title: SQLNumResultCols | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: rothja
ms.author: jroth
ms.openlocfilehash: 45e72165eef621dc377b02ed3d2e7e1e3cf7ab8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660530"
---
# <a name="sqlnumresultcols"></a><span data-ttu-id="0b18a-102">SQLNumResultCols</span><span class="sxs-lookup"><span data-stu-id="0b18a-102">SQLNumResultCols</span></span>
  <span data-ttu-id="0b18a-103">실행된 문의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버는 결과 집합의 열 수를 보고할 때 서버에 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-103">For executed statements, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not visit the server to report the number of columns in a result set.</span></span> <span data-ttu-id="0b18a-104">이 경우는 `SQLNumResultCols` 서버 왕복을 발생 시 키 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-104">In this case, `SQLNumResultCols` does not cause a server roundtrip.</span></span> <span data-ttu-id="0b18a-105">[SQLDescribeCol](sqldescribecol.md) 및 [sqlcolattribute](sqlcolattribute.md)와 마찬가지로 `SQLNumResultCols` 준비 되었지만 실행 되지 않은 문에 대해를 호출 하면 서버 왕복이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-105">Like [SQLDescribeCol](sqldescribecol.md) and [SQLColAttribute](sqlcolattribute.md), calling `SQLNumResultCols` on prepared but not executed statements generates a server roundtrip.</span></span>  
  
 <span data-ttu-id="0b18a-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 문 일괄 처리에서 여러 결과 행 집합이 반환되는 경우 결과 집합 열의 수가 하나에서 다른 수로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-106">When a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statement batch returns multiple result row sets, it is possible for the number of result set columns to change from one set to another.</span></span> <span data-ttu-id="0b18a-107">`SQLNumResultCols`각 집합에 대해를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-107">`SQLNumResultCols` should be called for each set.</span></span> <span data-ttu-id="0b18a-108">열 수가 변경되면 애플리케이션이 행 결과를 인출하기 전에 데이터 값을 다시 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-108">When the number of columns changes, the application should rebind data values prior to fetching row results.</span></span> <span data-ttu-id="0b18a-109">여러 결과 집합 반환을 처리하는 방법은 [SQLMoreResults](sqlmoreresults.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0b18a-109">For more information about handling multiple result set returns, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="0b18a-110">에서 시작 하는 데이터베이스 엔진의 향상 된 기능으로는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SQLNumResultCols를 사용 하 여 예상 결과에 대 한 보다 정확한 설명을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b18a-110">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLNumResultCols to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="0b18a-111">이러한 보다 정확한 결과는 이전 버전의에서 SQLNumResultCols에서 반환 된 값과 다를 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b18a-111">These more accurate results may differ from the values returned by SQLNumResultCols in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0b18a-112">자세한 내용은 [메타데이터 검색](../native-client/features/metadata-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0b18a-112">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b18a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b18a-113">See Also</span></span>  
 <span data-ttu-id="0b18a-114">[SQLNumResultCols 함수](https://go.microsoft.com/fwlink/?LinkId=59359) </span><span class="sxs-lookup"><span data-stu-id="0b18a-114">[SQLNumResultCols Function](https://go.microsoft.com/fwlink/?LinkId=59359) </span></span>  
 [<span data-ttu-id="0b18a-115">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="0b18a-115">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
