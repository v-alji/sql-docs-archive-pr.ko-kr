---
title: 문 매개 변수 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b7e207416e60af94efd59555980a0edff68a38b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646394"
---
# <a name="using-statement-parameters"></a><span data-ttu-id="61481-102">문 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="61481-102">Using Statement Parameters</span></span>
  <span data-ttu-id="61481-103">매개 변수는 ODBC 애플리케이션에서 다음을 수행할 수 있도록 하는 SQL 문의 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="61481-103">A parameter is a variable in an SQL statement that can enable an ODBC application to:</span></span>  
  
-   <span data-ttu-id="61481-104">효율적으로 테이블의 열 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="61481-104">Efficiently provide values for columns in a table.</span></span>  
  
-   <span data-ttu-id="61481-105">쿼리 조건을 생성하여 사용자 상호 작용을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="61481-105">Enhance user interaction in constructing query criteria.</span></span>  
  
-   <span data-ttu-id="61481-106">**Text**, **ntext**및 **image** 데이터와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관련 C 데이터 형식을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="61481-106">Manage **text**, **ntext**, and **image** data and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types.</span></span>  
  
 <span data-ttu-id="61481-107">예를 들어 **부품** 테이블에는 **PartID**, **설명**및 **가격**이라는 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61481-107">For example, a **Parts** table has columns named **PartID**, **Description**, and **Price**.</span></span> <span data-ttu-id="61481-108">매개 변수 없이 부품을 추가하려면 다음과 같이 SQL 문을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61481-108">To add a part without parameters requires constructing an SQL statement such as:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 <span data-ttu-id="61481-109">알려진 값 집합이 포함된 행 하나를 삽입하는 경우 이 문을 사용해도 되지만 애플리케이션에서 여러 행을 삽입해야 하는 경우에는 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="61481-109">Although this statement is acceptable for inserting one row with a known set of values, it is awkward when an application is required to insert several rows.</span></span> <span data-ttu-id="61481-110">ODBC는 애플리케이션에서 매개 변수 표식을 통해 SQL 문의 모든 데이터 값을 바꿀 수 있도록 하여 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="61481-110">ODBC addresses this by letting an application to replace any data value in an SQL statement by a parameter maker.</span></span> <span data-ttu-id="61481-111">이 경우 물음표(?)가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="61481-111">This is denoted by a question mark (?).</span></span> <span data-ttu-id="61481-112">다음 예에서는 3개의 데이터 값이 매개 변수 표식으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="61481-112">In the following example, three data values are replaced with parameter markers:</span></span>  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 <span data-ttu-id="61481-113">그런 다음 매개 변수 표식이 애플리케이션 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="61481-113">The parameter markers are then bound to application variables.</span></span> <span data-ttu-id="61481-114">새 행을 삽입하려면 애플리케이션에서 변수 값을 설정하고 문을 실행하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="61481-114">To insert a new row, the application has only to set the values of the variables and execute the statement.</span></span> <span data-ttu-id="61481-115">그런 다음 드라이버가 변수의 현재 값을 검색하여 데이터 원본에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="61481-115">The driver then retrieves the current values of the variables and sends them to the data source.</span></span> <span data-ttu-id="61481-116">문이 여러 번 실행되는 경우 애플리케이션에서 문을 준비하여 프로세스를 훨씬 효율적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61481-116">If the statement is executed multiple times, the application can make the process even more efficient by preparing the statement.</span></span>  
  
 <span data-ttu-id="61481-117">각 매개 변수 표식은 왼쪽에서 오른쪽으로 매개 변수에 할당되는 서수 번호로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="61481-117">Each parameter marker is referenced by its ordinal number assigned to the parameters from left to right.</span></span> <span data-ttu-id="61481-118">SQL 문에서 맨 왼쪽에 있는 매개 변수 표식의 서수 값은 1이고, 다음 표식의 서수 값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="61481-118">The leftmost parameter marker in an SQL statement has an ordinal value of 1; the next one is ordinal 2, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61481-119">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="61481-119">In This Section</span></span>  
  
-   [<span data-ttu-id="61481-120">매개 변수 바인딩</span><span class="sxs-lookup"><span data-stu-id="61481-120">Binding Parameters</span></span>](using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a><span data-ttu-id="61481-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="61481-121">See Also</span></span>  
 [<span data-ttu-id="61481-122">ODBC&#41;&#40;쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="61481-122">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
