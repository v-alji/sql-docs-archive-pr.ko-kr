---
title: 저장소 할당 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: rothja
ms.author: jroth
ms.openlocfilehash: ada18c91493d91b36ced51bf84c32513a0c5f5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653314"
---
# <a name="assigning-storage"></a><span data-ttu-id="ae07e-102">스토리지 할당</span><span class="sxs-lookup"><span data-stu-id="ae07e-102">Assigning Storage</span></span>
  <span data-ttu-id="ae07e-103">애플리케이션에서 SQL 문 실행 전이나 후에 결과의 스토리지를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-103">An application can assign storage for results before or after it executes a SQL statement.</span></span> <span data-ttu-id="ae07e-104">애플리케이션에서 먼저 SQL 문을 준비하거나 실행하는 경우 결과의 스토리지를 할당하기 전에 결과 집합을 조회할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-104">If an application prepares or executes the SQL statement first, it can inquire about the result set before it assigns storage for results.</span></span> <span data-ttu-id="ae07e-105">예를 들어 결과 집합을 알 수 없는 경우 애플리케이션에서는 결과의 스토리지를 할당하기 전에 열의 수를 검색해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-105">For example, if the result set is unknown, the application must retrieve the number of columns before it can assign storage for them.</span></span>  
  
 <span data-ttu-id="ae07e-106">데이터 열에 대 한 저장소를 연결 하기 위해 응용 프로그램은 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)를 호출 하 고이를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-106">To associate storage for a column of data, an application calls [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)and passes it:</span></span>  
  
-   <span data-ttu-id="ae07e-107">데이터를 변환할 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="ae07e-107">The data type to which the data is to be converted.</span></span>  
  
-   <span data-ttu-id="ae07e-108">데이터에 대한 출력 버퍼의 주소</span><span class="sxs-lookup"><span data-stu-id="ae07e-108">The address of an output buffer for the data.</span></span>  
  
     <span data-ttu-id="ae07e-109">애플리케이션에서는 이 버퍼를 할당해야 하며, 이 버퍼는 변환되는 형식의 데이터를 저장할 수 있을 만큼 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-109">The application must allocate this buffer, and it must be large enough to hold the data in the form to which it is converted.</span></span>  
  
-   <span data-ttu-id="ae07e-110">출력 버퍼의 길이</span><span class="sxs-lookup"><span data-stu-id="ae07e-110">The length of the output buffer.</span></span>  
  
     <span data-ttu-id="ae07e-111">반환된 데이터가 C에서 정수, 실수 또는 날짜 구조와 같이 고정 폭인 경우 이 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-111">This value is ignored if the returned data has a fixed width in C, such as an integer, real number, or date structure.</span></span>  
  
-   <span data-ttu-id="ae07e-112">사용 가능한 데이터의 바이트 수를 반환할 스토리지 버퍼의 주소</span><span class="sxs-lookup"><span data-stu-id="ae07e-112">The address of a storage buffer in which to return the number of bytes of available data.</span></span>  
  
 <span data-ttu-id="ae07e-113">또한 애플리케이션에서는 결과 집합 행을 블록 단위로 인출할 수 있도록 결과 집합 열을 프로그램 변수 배열에 바인딩할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-113">An application can also bind result set columns to arrays of program variables to support fetching result set rows in blocks.</span></span> <span data-ttu-id="ae07e-114">배열 바인딩에는 다음과 같은 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-114">There are two different types of array binding:</span></span>  
  
-   <span data-ttu-id="ae07e-115">열 단위 바인딩은 각 열이 고유한 변수 배열에 바인딩되면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-115">Column-wise binding is finished when each column is bound to its own array of variables.</span></span>  
  
     <span data-ttu-id="ae07e-116">열 단위 바인딩은 *특성* 을 SQL_ATTR_ROW_BIND_TYPE *로 설정 하 고 SQL_BIND_BY_COLUMN* 로 설정 된 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) 를 호출 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-116">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to SQL_BIND_BY_COLUMN.</span></span> <span data-ttu-id="ae07e-117">모든 배열의 요소 수가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-117">All the arrays must have the same number of elements.</span></span>  
  
-   <span data-ttu-id="ae07e-118">행 단위 바인딩은 SQL 문의 모든 매개 변수가 매개 변수의 개별 변수를 포함하는 구조체 배열에 하나의 단위로 바인딩되면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-118">Row-wise binding is finished when all the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>  
  
     <span data-ttu-id="ae07e-119">행 단위 바인딩은 *특성* 을 SQL_ATTR_ROW_BIND_TYPE로 설정 하 고 *valueptr* 을 결과 집합 열을 받는 변수를 포함 하는 구조체의 크기로 설정 하 여 **SQLSetStmtAttr** 를 호출 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-119">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to the size of the structure holding the variables that will receive the result set columns.</span></span>  
  
 <span data-ttu-id="ae07e-120">또한 애플리케이션에서는 SQL_ATTR_ROW_ARRAY_SIZE를 열 또는 행 배열의 요소 수로 설정하고 SQL_ATTR_ROW_STATUS_PTR 및 SQL_ATTR_ROWS_FETCHED_PTR을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ae07e-120">The application also sets SQL_ATTR_ROW_ARRAY_SIZE to the number of elements in the column or row arrays and sets SQL_ATTR_ROW_STATUS_PTR and SQL_ATTR_ROWS_FETCHED_PTR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae07e-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae07e-121">See Also</span></span>  
 [<span data-ttu-id="ae07e-122">ODBC&#41;&#40;결과 처리</span><span class="sxs-lookup"><span data-stu-id="ae07e-122">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
