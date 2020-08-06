---
title: ADOMD.NET 서버 기능 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: f00215c6bcc0104c920be29e0837288a469b252e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728919"
---
# <a name="adomdnet-server-functionality"></a><span data-ttu-id="5bc00-102">ADOMD.NET Server 기능</span><span class="sxs-lookup"><span data-stu-id="5bc00-102">ADOMD.NET Server Functionality</span></span>
  <span data-ttu-id="5bc00-103">모든 ADOMD.NET 서버 개체는 서버의 데이터 및 메타데이터에 대해 읽기 전용 액세스를 제공하므로</span><span class="sxs-lookup"><span data-stu-id="5bc00-103">All ADOMD.NET server objects provide read-only access to the data and metadata on the server.</span></span> <span data-ttu-id="5bc00-104">ADOMD.NET 서버 개체 모델을 사용하여 데이터 및 메타데이터를 검색할 수 있습니다. 그러나 이 서버 개체 모델은 스키마 행 집합을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-104">To retrieve data and metadata, you use the ADOMD.NET server object model as the server object model does not support schema rowsets.</span></span>  
  
 <span data-ttu-id="5bc00-105">ADOMD.NET 서버 개체를 사용 하 여에 대 한 UDF (사용자 정의 함수) 또는 저장 프로시저를 만들 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5bc00-105">With ADOMD.NET server objects, you can create a user defined function (UDF) or a stored procedure for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="5bc00-106">이러한 in-process 메서드는 MDX(Multidimensional Expressions), DMX(Data Mining Extensions) 또는 SQL과 같은 언어로 만들어진 쿼리 문을 통해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-106">These in-process methods are called through query statements created in languages such as Multidimensional Expressions (MDX), Data Mining Extensions (DMX), or SQL.</span></span> <span data-ttu-id="5bc00-107">이러한 in-process 메서드는 네트워크 통신에 따른 지연 시간 없이 추가 기능을 제공하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-107">These in-process methods also provide added functionality without the latencies associated with network communications.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bc00-108">[Microsoft.analysisservices.sharepoint.integration.dll AdomdServer. AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) 개체는 DMX만 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-108">The [Microsoft.AnalysisServices.AdomdServer.AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) object only supports DMX.</span></span>  
  
## <a name="what-is-a-udf"></a><span data-ttu-id="5bc00-109">UDF 정의</span><span class="sxs-lookup"><span data-stu-id="5bc00-109">What is a UDF?</span></span>  
 <span data-ttu-id="5bc00-110">*UDF* 는 다음과 같은 특징이 있는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-110">A *UDF* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="5bc00-111">UDF는 쿼리 컨텍스트에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-111">You can call the UDF in the context of a query.</span></span>  
  
-   <span data-ttu-id="5bc00-112">UDF는 매개 변수 수에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-112">The UDF can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="5bc00-113">UDF는 여러 데이터 형식을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-113">The UDF can return various types of data.</span></span>  
  
 <span data-ttu-id="5bc00-114">다음 예제에서는 가상 UDF인 `FinalSalesNumber`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-114">The following example uses the fictional UDF, `FinalSalesNumber`:</span></span>  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a><span data-ttu-id="5bc00-115">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="5bc00-115">What is a Stored Procedure?</span></span>  
 <span data-ttu-id="5bc00-116">*저장 프로시저* 는 다음과 같은 특징이 있는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-116">A *stored procedure* is a method that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="5bc00-117">MDX [call](/sql/mdx/mdx-data-manipulation-call) 문을 사용 하 여 자체적으로 저장 프로시저를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-117">You call a stored procedure on its own with the MDX [CALL](/sql/mdx/mdx-data-manipulation-call) statement.</span></span>  
  
-   <span data-ttu-id="5bc00-118">저장 프로시저는 매개 변수 수에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-118">A stored procedure can take any number of parameters.</span></span>  
  
-   <span data-ttu-id="5bc00-119">저장 프로시저는 데이터 세트, `IDataReader` 또는 빈 결과를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-119">A stored procedure can return a dataset, an `IDataReader`, or an empty result.</span></span>  
  
 <span data-ttu-id="5bc00-120">다음 예제에서는 가상 저장 프로시저인 `FinalSalesNumbers`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bc00-120">The following example uses the fictional stored procedure, `FinalSalesNumbers`:</span></span>  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bc00-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bc00-121">See Also</span></span>  
 [<span data-ttu-id="5bc00-122">ADOMD.NET 서버 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="5bc00-122">ADOMD.NET Server Programming</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
