---
title: 결과 집합의 특징 확인 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], characteristics
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLDescribeCol function
- metadata [ODBC]
- SQLColAttribute function
- SQLNumResultCols function
ms.assetid: 90be414c-04b3-46c0-906b-ae7537989b7d
author: rothja
ms.author: jroth
ms.openlocfilehash: 5957092cdddfbcbce904d9a6483914672565d337
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649038"
---
# <a name="determining-the-characteristics-of-a-result-set-odbc"></a><span data-ttu-id="4201a-102">결과 집합의 특징 확인(ODBC)</span><span class="sxs-lookup"><span data-stu-id="4201a-102">Determining the Characteristics of a Result Set (ODBC)</span></span>
  <span data-ttu-id="4201a-103">메타데이터는 다른 데이터를 설명하는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-103">Metadata is data that describes other data.</span></span> <span data-ttu-id="4201a-104">예를 들어 결과 집합 메타데이터는 결과 집합에 있는 열 수, 이러한 열의 데이터 형식, 이름, 전체 자릿수, Null 허용 여부 등과 같은 결과 집합의 특징을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-104">For example, result set metadata describes the characteristics of a result set, such as the number of columns in the result set, the data types of those columns, their names, precision, and nullability.</span></span>  
  
 <span data-ttu-id="4201a-105">ODBC는 카탈로그 API 함수를 통해 애플리케이션에 메타데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-105">ODBC supplies metadata to applications through its catalog API functions.</span></span> <span data-ttu-id="4201a-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc 드라이버는 해당 카탈로그 프로시저에 대 한 호출로 많은 ODBC API 카탈로그 함수를 구현 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver implements many of the ODBC API catalog functions as calls to a corresponding [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] catalog procedure.</span></span>  
  
 <span data-ttu-id="4201a-107">애플리케이션에서는 대부분의 결과 집합 작업에 대해 메타데이터를 요구합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-107">Applications require metadata for most result set operations.</span></span> <span data-ttu-id="4201a-108">예를 들어 애플리케이션에서는 열의 데이터 형식을 사용하여 해당 열에 바인딩할 변수의 종류를 확인하고</span><span class="sxs-lookup"><span data-stu-id="4201a-108">For example, the application uses the data type of a column to determine what kind of variable to bind to that column.</span></span> <span data-ttu-id="4201a-109">문자 열의 바이트 길이를 사용하여 열 데이터를 표시하는 데 필요한 공간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-109">It uses the byte length of a character column to determine how much space it must have to display data from that column.</span></span> <span data-ttu-id="4201a-110">애플리케이션에서 열의 메타데이터를 확인하는 방법은 애플리케이션 종류에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-110">How an application determines the metadata for a column depends on the type of the application.</span></span>  
  
 <span data-ttu-id="4201a-111">일반적으로 수직 시장 애플리케이션에서는 미리 정의된 테이블을 사용하여 미리 정의된 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-111">Vertical applications typically work with predefined tables and perform predefined operations on those tables.</span></span> <span data-ttu-id="4201a-112">이러한 애플리케이션의 결과 집합 메타데이터는 개발자가 애플리케이션을 작성하고 제어하기 전에 정의되므로 용용 프로그램에 하드 코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-112">Because the result set metadata for such applications is defined before the application is even written and is controlled by the developer, it can be hard-coded into the application.</span></span> <span data-ttu-id="4201a-113">예를 들어 주문 ID 열이 데이터 원본에 4바이트 정수로 정의된 경우 애플리케이션에서는 항상 해당 열에 4바이트 정수를 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-113">For example, if an order ID column is defined as a 4-byte integer in the data source, the application can always bind a 4-byte integer to that column.</span></span> <span data-ttu-id="4201a-114">메타데이터가 애플리케이션에 하드 코딩되면 애플리케이션에서 사용하는 테이블의 변경은 일반적으로 애플리케이션 코드의 변경을 암시합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-114">When metadata is hard-coded in the application, a change to the tables used by the application generally implies a change to the application code.</span></span>  
  
 <span data-ttu-id="4201a-115">임시 쿼리를 지원하는 애플리케이션과 같은 일반 애플리케이션에서는 일반적으로 애플리케이션에서 만든 결과 집합의 메타데이터를 런타임 이전에 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-115">In generic applications, especially applications that support ad hoc queries, the metadata of the result sets they create is typically unknown until run time.</span></span>  
  
 <span data-ttu-id="4201a-116">결과 집합의 특징을 확인하기 위해 애플리케이션에서는 다음과 같이 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-116">To determine the characteristics of a result set, an application can call:</span></span>  
  
-   <span data-ttu-id="4201a-117">요청에서 반환 된 열 수를 확인 하기 위한 [Sqlnumresultcols](../native-client-odbc-api/sqlnumresultcols.md)</span><span class="sxs-lookup"><span data-stu-id="4201a-117">[SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) to determine how many columns a request returned.</span></span>  
  
-   <span data-ttu-id="4201a-118">결과 집합의 열을 설명 하는 [Sqlcolattribute](../native-client-odbc-api/sqlcolattribute.md) 또는 [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md)</span><span class="sxs-lookup"><span data-stu-id="4201a-118">[SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) or [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) to describe a column in the result set.</span></span>  
  
 <span data-ttu-id="4201a-119">잘 디자인된 애플리케이션은 결과 집합을 알 수 없고 결과 집합이 이러한 함수에서 반환하는 정보를 사용하여 해당 결과 집합의 열을 바인딩한다는 가정 하에 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-119">A well-designed application is written with the assumption that the result set is unknown and uses the information returned by these functions to bind the columns in the result set.</span></span> <span data-ttu-id="4201a-120">애플리케이션에서는 문이 준비되거나 실행된 후 언제든지 이러한 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-120">An application can call these functions at any time after a statement is prepared or executed.</span></span> <span data-ttu-id="4201a-121">그러나 최적의 성능을 위해 응용 프로그램은 문이 실행 된 후 **Sqlcolattribute**, **SQLDescribeCol**및 **sqlnumresultcols** 를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-121">However, for optimal performance, an application should call **SQLColAttribute**, **SQLDescribeCol**, and **SQLNumResultCols** after a statement is executed.</span></span>  
  
 <span data-ttu-id="4201a-122">메타데이터는 동시에 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-122">You can have multiple concurrent calls for metadata.</span></span> <span data-ttu-id="4201a-123">ODBC 카탈로그 API 구현을 기반으로 하는 시스템 카탈로그 프로시저는 ODBC 드라이버가 정적 서버 커서를 사용하는 동안 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-123">The system catalog procedures underlying the ODBC catalog API implementations can be called by the ODBC driver while it is using static server cursors.</span></span> <span data-ttu-id="4201a-124">이렇게 하면 애플리케이션에서 ODBC 카탈로그 함수에 대한 여러 호출을 동시에 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-124">This lets applications concurrently process multiple calls to ODBC catalog functions.</span></span>  
  
 <span data-ttu-id="4201a-125">애플리케이션에서 특정 메타데이터 세트을 두 번 이상 사용하는 경우 이러한 메타데이터 세트을 처음으로 가져올 때 프라이빗 변수에 해당 정보가 캐시되는 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-125">If an application uses a particular set of metadata more than one time, it will probably benefit from caching the information in private variables when it is first obtained.</span></span> <span data-ttu-id="4201a-126">이는 나중에 드라이버를 강제로 서버에 왕복하게 하는 ODBC 카탈로그 함수가 동일한 정보에 대해 호출되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4201a-126">This prevents later calls to the ODBC catalog functions for the same information, which force the driver to make round trips to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4201a-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4201a-127">See Also</span></span>  
 [<span data-ttu-id="4201a-128">ODBC&#41;&#40;결과 처리</span><span class="sxs-lookup"><span data-stu-id="4201a-128">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
