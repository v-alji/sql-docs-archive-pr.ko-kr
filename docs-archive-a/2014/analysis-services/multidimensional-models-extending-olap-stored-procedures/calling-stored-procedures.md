---
title: 저장 프로시저 호출 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c9da6edef576a6ab25c183cbc87ff95cc056845
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732168"
---
# <a name="calling-stored-procedures"></a><span data-ttu-id="95ce0-102">저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="95ce0-102">Calling Stored Procedures</span></span>
  <span data-ttu-id="95ce0-103">저장 프로시저는 서버나 클라이언트 애플리케이션에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-103">Stored procedures can be called on the server or from client application.</span></span> <span data-ttu-id="95ce0-104">어느 경우에나 저장 프로시저는 항상 서버에서 서버나 데이터베이스의 컨텍스트로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-104">In either case, stored procedures always run on the server, either the context of the server or of a database.</span></span> <span data-ttu-id="95ce0-105">저장 프로시저를 실행하는 데 필요한 특별 권한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-105">There are no special permissions required to execute a stored procedure.</span></span> <span data-ttu-id="95ce0-106">어셈블리를 사용하여 서버 또는 데이터베이스 컨텍스트에 저장 프로시저를 추가한 후에는 저장 프로시저에서 수행하는 동작이 허가된 역할의 사용자는 모두 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-106">Once a stored procedure is added by an assembly to the server or database context, any user can execute the stored procedure as long as the role for the user permits the actions performed by the stored procedure.</span></span>  
  
 <span data-ttu-id="95ce0-107">MDX의 저장 프로시저 호출은 내부 MDX 함수 호출과 동일한 방식으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-107">Calling a stored procedure in MDX is done in the same manner as calling an intrinsic MDX function.</span></span> <span data-ttu-id="95ce0-108">매개 변수가 없는 저장 프로시저의 경우 아래와 같이 프로시저 이름과 빈 괄호 쌍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-108">For a stored procedure that takes no parameters, the name of the procedure and an empty pair of parentheses are used, as shown here:</span></span>  
  
```  
MyStoredProcedure()  
```  
  
 <span data-ttu-id="95ce0-109">저장 프로시저에 매개 변수가 한 개 이상 있을 경우 매개 변수를 쉼표로 구분하여 순서대로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-109">If the stored procedure takes one or more parameters, then the parameters are supplied, in order, separated by commas.</span></span> <span data-ttu-id="95ce0-110">다음 예에서는 매개 변수가 세 개 있는 예제 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-110">The following example demonstrates a sample stored procedure with three parameters:</span></span>  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a><span data-ttu-id="95ce0-111">MDX 쿼리에서 저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="95ce0-111">Calling Stored Procedures in MDX Queries</span></span>  
 <span data-ttu-id="95ce0-112">모든 MDX 쿼리에서 저장 프로시저는 MDX 식에 필요한 올바른 구문의 형식을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-112">In all MDX queries, the stored procedure must return the syntactically correct type required by an MDX expression.</span></span> <span data-ttu-id="95ce0-113">저장 프로시저에서 올바른 형식을 반환하지 않으면 MDX 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-113">If a stored procedure does not return the correct type, an MDX error occurs.</span></span> <span data-ttu-id="95ce0-114">다음 예에서는 집합, 멤버 및 수치 연산의 결과를 반환하는 저장 프로시저를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-114">The following examples demonstrate stored procedures that return a set, a member, and the result of a mathematical operation.</span></span>  
  
### <a name="returning-a-set"></a><span data-ttu-id="95ce0-115">집합 반환</span><span class="sxs-lookup"><span data-stu-id="95ce0-115">Returning a Set</span></span>  
 <span data-ttu-id="95ce0-116">다음 예에서는 집합을 반환하는 저장 프로시저 MySproc를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-116">The following examples implement a stored procedure, called MySproc, that returns a set.</span></span> <span data-ttu-id="95ce0-117">첫 번째 예에서 MySproc는 SELECT 식에서 직접 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-117">In the first example, MySproc returns the set directly in the SELECT expression.</span></span> <span data-ttu-id="95ce0-118">나머지 두 예에서는 MySproc가 Crossjoin 및 DrilldownLevel 함수의 인수로 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-118">In the second two examples, MySproc returns the set as an argument for the Crossjoin and DrilldownLevel functions.</span></span>  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a><span data-ttu-id="95ce0-119">멤버 반환</span><span class="sxs-lookup"><span data-stu-id="95ce0-119">Returning a Member</span></span>  
 <span data-ttu-id="95ce0-120">다음 예에서는 멤버를 반환하는 MySproc 함수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-120">The following example shows a function MySproc function that returns a member:</span></span>  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a><span data-ttu-id="95ce0-121">수치 연산의 결과 반환</span><span class="sxs-lookup"><span data-stu-id="95ce0-121">Returning the Result of a Math Operation</span></span>  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a><span data-ttu-id="95ce0-122">Call 문으로 저장 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="95ce0-122">Calling Stored Procedures with the Call Statement</span></span>  
 <span data-ttu-id="95ce0-123">MDX `Call` 문을 사용하면 MDX 쿼리 컨텍스트 외부에서 저장 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-123">Stored procedures can be called outside of the context of an MDX query using the MDX `Call` statement.</span></span>  
  
 <span data-ttu-id="95ce0-124">이 방법을 사용하면 저장 쿼리의 파생 작업을 인스턴스화하거나 애플리케이션에서 저장 쿼리의 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-124">You can use this method to either instantiate the side effects of a stored query or for the application to get the results of a stored query.</span></span> <span data-ttu-id="95ce0-125">`Call` 문은 주로 AMO(Analysis Management Object)를 통해 반환 결과 없이 관리 기능을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-125">A common use of the `Call` statement would be to use Analysis Management Objects (AMO) to perform administrative functions that do not have a return result.</span></span> <span data-ttu-id="95ce0-126">예를 들어 다음 명령에서는 저장 프로시저를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-126">For example, the following command calls a stored procedure:</span></span>  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 <span data-ttu-id="95ce0-127">`Call` 문의 저장 프로시저에서 유일하게 지원하는 반환 형식은 행 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-127">The only supported type returned from stored procedure in a `Call` statement is a rowset.</span></span> <span data-ttu-id="95ce0-128">행 집합 직렬화는 XML for Analysis에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-128">The serialization for a rowset is defined by XML for Analysis.</span></span> <span data-ttu-id="95ce0-129">`Call` 문의 저장 프로시저에서 다른 형식을 반환하는 경우에는 무시되고 호출 애플리케이션에 XML로 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-129">If a stored procedure in a `Call` statement returns any other type, it is ignored and not returned in XML to the calling application.</span></span> <span data-ttu-id="95ce0-130">XML for Analysis 행 집합에 대한 자세한 내용은 XML for Analysis Schema Rowsets를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="95ce0-130">For more information about XML for Analysis rowsets, see, XML for Analysis Schema Rowsets.</span></span>  
  
 <span data-ttu-id="95ce0-131">저장 프로시저에서 .NET 행 집합을 반환하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 서버의 결과를 XML for Analysis 행 집합으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-131">If a stored procedure returns a .NET rowset, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] converts the result on the server to an XML for Analysis rowset.</span></span> <span data-ttu-id="95ce0-132">XML for Analysis 행 집합은 항상 `Call` 함수의 저장 프로시저에 의해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-132">The XML for Analysis rowset is always returned by a stored procedure in the `Call` function.</span></span> <span data-ttu-id="95ce0-133">데이터 세트에 XML for Analysis 행 세트로 표현할 수 없는 기능이 있다면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-133">If a dataset contains features that cannot be expressed in the XML for Analysis rowset, a failure results.</span></span>  
  
 <span data-ttu-id="95ce0-134">Void 값을 반환하는 프로시저(예: Visual Basic의 서브루틴)를 CALL 키워드와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-134">Procedures that return void values (for example, subroutines in Visual Basic) can also be employed with the CALL keyword.</span></span> <span data-ttu-id="95ce0-135">예를 들어 MDX 문에서 MyVoidFunction() 함수를 사용하려면 다음과 같은 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="95ce0-135">If, for example, you wanted to use the function MyVoidFunction() in an MDX statement, the following syntax would be employed:</span></span>  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a><span data-ttu-id="95ce0-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95ce0-136">See Also</span></span>  
 <span data-ttu-id="95ce0-137">[다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="95ce0-137">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="95ce0-138">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="95ce0-138">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
