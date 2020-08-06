---
title: 사용자 정의 함수 및 저장 프로시저 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727443"
---
# <a name="user-defined-functions-and-stored-procedures"></a><span data-ttu-id="b3da8-102">사용자 정의 함수 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="b3da8-102">User Defined Functions and Stored Procedures</span></span>
  <span data-ttu-id="b3da8-103">ADOMD.NET 서버 개체를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버에서 메타 데이터 및 데이터와 상호 작용 하는 UDF (사용자 정의 함수) 또는 저장 프로시저를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-103">With ADOMD.NET server objects, you can create user defined function (UDF) or stored procedures for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] that interact with metadata and data from the server.</span></span> <span data-ttu-id="b3da8-104">이러한 in-process 메서드는 MDX(Multidimensional Expressions) 또는 DMX(Data Mining Extensions) 문을 통해 호출되어 네트워크 통신에 따른 지연 시간 없이 추가 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-104">These in-process methods are called through Multidimensional Expressions (MDX) or Data Mining Extensions (DMX) statements to provide added functionality without the latencies associated with network communications.</span></span>  
  
## <a name="udf-examples"></a><span data-ttu-id="b3da8-105">UDF 예</span><span class="sxs-lookup"><span data-stu-id="b3da8-105">UDF Examples</span></span>  
 <span data-ttu-id="b3da8-106">UDF는 MDX 또는 DMX 문의 컨텍스트 내에서 호출할 수 있는 메서드로, 사용 가능한 매개 변수 수와 반환하는 데이터 형식에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-106">A UDF is a method that can be called in the context of an MDX or DMX statement, can take any number of parameters, and can return any type of data.</span></span>  
  
 <span data-ttu-id="b3da8-107">MDX를 사용하여 만든 UDF는 DMX용으로 만든 UDF와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-107">A UDF created using MDX is similar to one created for DMX.</span></span> <span data-ttu-id="b3da8-108">주요 차이점은 [microsoft.analysisservices.sharepoint.integration.dll. AdomdServer](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) 개체의 특정 속성 (예: [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) ) 및 microsoft.analysisservices.sharepoint.integration.dll \* 속성은 하나의 스크립팅 언어에만 사용할 수 있다는 것입니다. AdomdServer [\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) 속성은 하나의 스크립팅 언어에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-108">The main difference is that certain properties of the [Microsoft.AnalysisServices.AdomdServer.Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) object, such as the [Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube\*](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) and [Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel\*](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) properties, are available only for one scripting language or the other.</span></span>  
  
 <span data-ttu-id="b3da8-109">다음 예에서는 UDF를 사용하여 노드 설명을 반환하고 튜플을 반환하고 튜플에 필터를 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-109">The following examples show how to use a UDF to return a node description, filter tuples, and apply a filter to a tuple.</span></span>  
  
### <a name="returning-a-node-description"></a><span data-ttu-id="b3da8-110">노드 설명 반환</span><span class="sxs-lookup"><span data-stu-id="b3da8-110">Returning a Node Description</span></span>  
 <span data-ttu-id="b3da8-111">다음 예에서는 지정한 노드에 대한 노드 설명을 반환하는 UDF를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-111">The following example creates a UDF that returns the node description for a specified node.</span></span> <span data-ttu-id="b3da8-112">이 UDF에서는 UDF가 실행되는 현재 컨텍스트를 사용하고 DMX FROM 절을 사용하여 현재 마이닝 모델에서 노드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-112">The UDF uses the current context in which it is being run, and uses a DMX FROM clause to retrieve the node from the current mining model.</span></span>  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 <span data-ttu-id="b3da8-113">위의 예를 배포한 후에는 가장 가능성이 높은 예측 노드를 검색하는 다음 DMX 식으로 해당 UDF를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-113">Once deployed, the previous UDF example can be called by the following DMX expression, which retrieves the most-likely prediction node.</span></span> <span data-ttu-id="b3da8-114">반환된 설명에는 예측 노드를 구성하는 조건을 설명하는 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-114">The description contains information that describes the conditions that make up the prediction node.</span></span>  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a><span data-ttu-id="b3da8-115">튜플 반환</span><span class="sxs-lookup"><span data-stu-id="b3da8-115">Returning Tuples</span></span>  
 <span data-ttu-id="b3da8-116">다음 예에서는 집합과 반환 개수를 매개 변수로 받아 해당 집합에서 무작위로 튜플을 검색한 다음 최종 하위 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-116">The following example takes a set and a return count, and randomly retrieves tuples from the set, returning a final subset:</span></span>  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 <span data-ttu-id="b3da8-117">위의 예는 다음 MDX 예에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-117">The previous example is called in the following MDX example.</span></span> <span data-ttu-id="b3da8-118">이 MDX 예제에서는 5 개의 무작위 상태 또는도를 **놀이 Works** 데이터베이스에서 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-118">In this MDX example, five random states or provinces are retrieved from the **Adventure Works** database.</span></span>  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a><span data-ttu-id="b3da8-119">튜플에 필터 적용</span><span class="sxs-lookup"><span data-stu-id="b3da8-119">Applying a Filter to a Tuple</span></span>  
 <span data-ttu-id="b3da8-120">다음 예의 UDF는 집합을 매개 변수로 받고 Expression 개체를 사용하여 집합의 각 튜플에 필터를 적용하도록 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-120">In the following example, a UDF is defined that takes a set, and applies a filter to each tuple in the set, using the Expression object.</span></span> <span data-ttu-id="b3da8-121">필터에 맞는 모든 튜플은 반환 집합에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-121">Any tuples that conform to the filter will be added to a set that is returned.</span></span>  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 <span data-ttu-id="b3da8-122">위의 예는 이름이 'A'로 시작하는 도시로 집합을 필터링하는 다음 MDX 예에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-122">The previous example is called in the following MDX example, which filters the set to cities with names beginning with 'A'.</span></span>  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a><span data-ttu-id="b3da8-123">저장 프로시저 예</span><span class="sxs-lookup"><span data-stu-id="b3da8-123">Stored Procedure Example</span></span>  
 <span data-ttu-id="b3da8-124">다음 예의 MDX 기반 저장 프로시저는 필요한 경우 AMO를 사용하여 인터넷 판매를 위한 파티션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3da8-124">In the following example, an MDX-based stored procedure uses AMO to create partitions, if needed, for Internet Sales.</span></span>  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
