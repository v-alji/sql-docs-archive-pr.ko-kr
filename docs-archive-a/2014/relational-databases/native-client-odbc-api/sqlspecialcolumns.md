---
title: SQLSpecialColumns | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLSpecialColumns function
ms.assetid: dffe02ed-8f79-4c9a-af34-98130bbe5462
author: rothja
ms.author: jroth
ms.openlocfilehash: c36ff73606e95ed7ee5e713b81acf7c177a42563
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650955"
---
# <a name="sqlspecialcolumns"></a><span data-ttu-id="1ad04-102">SQLSpecialColumns</span><span class="sxs-lookup"><span data-stu-id="1ad04-102">SQLSpecialColumns</span></span>
  <span data-ttu-id="1ad04-103">행 식별자(*IdentifierType* SQL_BEST_ROWID)를 요청할 경우 **SQLSpecialColumns** 는 SQL_SCOPE_CURROW 이외의 모든 요청 범위에 대해 빈 결과 집합(데이터 행 없음)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-103">When requesting row identifiers (*IdentifierType* SQL_BEST_ROWID), **SQLSpecialColumns** returns an empty result set (no data rows) for any requested scope other than SQL_SCOPE_CURROW.</span></span> <span data-ttu-id="1ad04-104">즉, 생성된 결과 집합은 열이 이 범위 내에서만 유효하다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-104">The generated result set indicates that the columns are only valid within this scope.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1ad04-105">는 식별자에 대한 의사 열을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-105">does not support pseudocolumns for identifiers.</span></span> <span data-ttu-id="1ad04-106">**SQLSpecialColumns** 결과 집합은 모든 열을 SQL_PC_NOT_PSEUDO로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-106">The **SQLSpecialColumns** result set will identify all columns as SQL_PC_NOT_PSEUDO.</span></span>  
  
 <span data-ttu-id="1ad04-107">**SQLSpecialColumns** 는 정적 커서에 대해 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-107">**SQLSpecialColumns** can be executed on a static cursor.</span></span> <span data-ttu-id="1ad04-108">업데이트할 수 있는 커서(키 집합 커서 또는 동적 커서)에 대해 **SQLSpecialColumns** 를 실행하려고 하면 커서 유형이 변경되었음을 나타내는 SQL_SUCCESS_WITH_INFO가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-108">An attempt to execute **SQLSpecialColumns** on an updatable (keyset-driven or dynamic) returns SQL_SUCCESS_WITH_INFO indicating the cursor type has been changed.</span></span>  
  
## <a name="sqlspecialcolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="1ad04-109">향상된 날짜 및 시간 기능에 대한 SQLSpecialColumns 지원</span><span class="sxs-lookup"><span data-stu-id="1ad04-109">SQLSpecialColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="1ad04-110">날짜/시간 형식에서 DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH 및 DECIMAL_DIGTS 열에 반환되는 값에 대한 자세한 내용은 [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ad04-110">For information about the values returned for the columns DATA_TYPE, TYPE_NAME, COLUMN_SIZE, BUFFER_LENGTH, and DECIMAL_DIGTS for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="1ad04-111">보다 일반적인 정보는 [ODBC&#41;&#40;날짜 및 시간 향상 ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1ad04-111">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlspecialcolumns-support-for-large-clr-udts"></a><span data-ttu-id="1ad04-112">큰 CLR UDT에 대한 SQLSpecialColumns 지원</span><span class="sxs-lookup"><span data-stu-id="1ad04-112">SQLSpecialColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="1ad04-113">**SQLSpecialColumns** 는 큰 CLR UDT(사용자 정의 형식)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1ad04-113">**SQLSpecialColumns** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="1ad04-114">자세한 내용은 [ODBC&#41;&#40;LARGE CLR 사용자 정의 형식 ](../native-client/odbc/large-clr-user-defined-types-odbc.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1ad04-114">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad04-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ad04-115">See Also</span></span>  
 <span data-ttu-id="1ad04-116">[SQLSpecialColumns 함수](https://go.microsoft.com/fwlink/?LinkId=59371) </span><span class="sxs-lookup"><span data-stu-id="1ad04-116">[SQLSpecialColumns Function](https://go.microsoft.com/fwlink/?LinkId=59371) </span></span>  
 [<span data-ttu-id="1ad04-117">ODBC API 구현 정보</span><span class="sxs-lookup"><span data-stu-id="1ad04-117">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
