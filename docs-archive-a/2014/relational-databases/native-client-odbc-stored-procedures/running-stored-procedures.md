---
title: 저장 프로시저 실행 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e5de6a9a13c95b417657a1d108403fa27abe34b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741947"
---
# <a name="running-stored-procedures"></a><span data-ttu-id="6b75a-102">저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="6b75a-102">Running Stored Procedures</span></span>
  <span data-ttu-id="6b75a-103">저장 프로시저는 데이터베이스에 저장된 실행 가능한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-103">A stored procedure is an executable object stored in a database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6b75a-104">에서는 다음과 같은 프로시저를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-104">supports:</span></span>  
  
-   <span data-ttu-id="6b75a-105">저장 프로시저:</span><span class="sxs-lookup"><span data-stu-id="6b75a-105">Stored procedures:</span></span>  
  
     <span data-ttu-id="6b75a-106">실행 가능한 단일 프로시저로 미리 컴파일된 하나 이상의 SQL 문입니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-106">One or more SQL statements precompiled into a single executable procedure.</span></span>  
  
-   <span data-ttu-id="6b75a-107">확장 저장 프로시저:</span><span class="sxs-lookup"><span data-stu-id="6b75a-107">Extended stored procedures:</span></span>  
  
     <span data-ttu-id="6b75a-108">SQL Server 개방형 Data Services API에 확장 저장 프로시저에 대해 작성된 C 또는 C++ DLL(동적 연결 라이브러리)입니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-108">C or C++ dynamic-link libraries (DLL) written to the SQL Server Open Data Services API for extended stored procedures.</span></span> <span data-ttu-id="6b75a-109">개방형 Data Services API는 C 또는 C++ 코드를 포함하도록 저장 프로시저의 기능을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-109">The Open Data Services API extends the capabilities of stored procedures to include C or C++ code.</span></span>  
  
 <span data-ttu-id="6b75a-110">문을 실행할 때 클라이언트 애플리케이션에서 직접 문을 실행하거나 준비하는 대신 데이터 원본의 저장 프로시저를 호출하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-110">When executing statements, calling a stored procedure on the data source (instead of directly executing or preparing a statement in the client application) can provide:</span></span>  
  
-   <span data-ttu-id="6b75a-111">성능 향상</span><span class="sxs-lookup"><span data-stu-id="6b75a-111">Higher performance</span></span>  
  
     <span data-ttu-id="6b75a-112">프로시저가 생성될 때 SQL 문이 구문 분석되고 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-112">SQL statements are parsed and compiled when procedures are created.</span></span> <span data-ttu-id="6b75a-113">프로시저를 실행할 때는 이러한 오버헤드가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-113">This overhead is then saved when the procedures are executed.</span></span>  
  
-   <span data-ttu-id="6b75a-114">네트워크 오버헤드 감소</span><span class="sxs-lookup"><span data-stu-id="6b75a-114">Reduced network overhead</span></span>  
  
     <span data-ttu-id="6b75a-115">네트워크를 통해 복잡한 쿼리를 전송하는 대신 프로시저를 실행하면 네트워크 트래픽을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-115">Executing a procedure instead of sending complex queries across the network can reduce network traffic.</span></span> <span data-ttu-id="6b75a-116">ODBC 애플리케이션이 ODBC { CALL } 구문을 사용하여 저장 프로시저를 실행하는 경우 ODBC 드라이버가 추가 최적화를 수행하므로 매개 변수 데이터를 변환하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-116">If an ODBC application uses the ODBC { CALL } syntax to execute a stored procedure, the ODBC driver makes additional optimizations that eliminate the need to convert parameter data.</span></span>  
  
-   <span data-ttu-id="6b75a-117">일관성 향상</span><span class="sxs-lookup"><span data-stu-id="6b75a-117">Greater consistency</span></span>  
  
     <span data-ttu-id="6b75a-118">조직의 규칙을 저장 프로시저와 같은 중앙 리소스에 구현하면 이러한 규칙을 한 번에 코딩, 테스트 및 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-118">If an organization's rules are implemented in a central resource, such as a stored procedure, they can be coded, tested, and debugged once.</span></span> <span data-ttu-id="6b75a-119">프로그래머는 직접 구현을 개발하는 대신 이러한 테스트된 저장 프로시저를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-119">Individual programmers can then use the tested stored procedures instead of developing their own implementations.</span></span>  
  
-   <span data-ttu-id="6b75a-120">정확도 향상</span><span class="sxs-lookup"><span data-stu-id="6b75a-120">Greater accuracy</span></span>  
  
     <span data-ttu-id="6b75a-121">저장 프로시저는 일반적으로 숙련된 프로그래머가 작성하기 때문에 기술 수준이 서로 다른 프로그래머들이 여러 차례 개발하는 코드보다 효율적이고 오류가 적은 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-121">Because stored procedures are usually developed by experienced programmers, they tend to be more efficient and have fewer errors than code developed multiple times by programmers of varying skill levels.</span></span>  
  
-   <span data-ttu-id="6b75a-122">기능 추가</span><span class="sxs-lookup"><span data-stu-id="6b75a-122">Added functionality</span></span>  
  
     <span data-ttu-id="6b75a-123">확장 저장 프로시저는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 제공되지 않는 C 및 C++ 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b75a-123">Extended stored procedures can use C and C++ features not available in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="6b75a-124">저장 프로시저를 호출 하는 방법에 대 한 예제는 [ODBC&#41;&#40;반환 코드 및 출력 매개 변수 처리 ](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6b75a-124">For an example of how to call a stored procedure, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b75a-125">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6b75a-125">In This Section</span></span>  
  
-   [<span data-ttu-id="6b75a-126">저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="6b75a-126">Calling a Stored Procedure</span></span>](calling-a-stored-procedure.md)  
  
-   [<span data-ttu-id="6b75a-127">저장 프로시저 호출 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="6b75a-127">Batching Stored Procedure Calls</span></span>](batching-stored-procedure-calls.md)  
  
-   [<span data-ttu-id="6b75a-128">저장 프로시저 결과 처리</span><span class="sxs-lookup"><span data-stu-id="6b75a-128">Processing Stored Procedure Results</span></span>](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b75a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b75a-129">See Also</span></span>  
 <span data-ttu-id="6b75a-130">[ODBC&#41;SQL Server Native Client &#40;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="6b75a-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="6b75a-131">저장 프로시저 실행 방법 항목 ODBC&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="6b75a-131">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
