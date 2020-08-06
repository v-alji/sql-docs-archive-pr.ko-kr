---
title: ADOMD.NET 서버 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- programming [ADOMD.NET]
- ADOMD.NET, programming
ms.assetid: 7f7ff5be-3826-43a5-b94d-ddeec5ddb2eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 522478af0b19f1745d80f167e40345d4751136b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727439"
---
# <a name="adomdnet-server-programming"></a><span data-ttu-id="04c1f-102">ADOMD.NET 서버 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="04c1f-102">ADOMD.NET Server Programming</span></span>
  <span data-ttu-id="04c1f-103">ADOMD.NET의 ADOMD.NET 서버 구성 요소는 `Microsoft.AnalysisServices.AdomdServer` 네임스페이스(msmgdsrv.dll) 안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-103">The ADOMD.NET server components of ADOMD.NET reside within the `Microsoft.AnalysisServices.AdomdServer` namespace (in msmgdsrv.dll).</span></span> <span data-ttu-id="04c1f-104">이러한 서버 구성 요소를 사용 하 여의 인스턴스에서 실행 되는 사용자 지정 MDX (Multidimensional Expressions) 함수 및 저장 프로시저를 만들 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="04c1f-104">You use these server components to create custom Multidimensional Expressions (MDX) functions and stored procedures that are run on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="04c1f-105">서버 개체는 큐브 및 마이닝 모델을 쿼리하고 지정된 컨텍스트에서 식을 평가하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-105">The server objects provide the capabilities for querying cubes and mining models, and for evaluating expressions in a given context.</span></span> <span data-ttu-id="04c1f-106">사용자 지정 함수 및 저장 프로시저를 만들면 실행 속도가 빨라지고 중앙 집중식 배포가 가능하며 관리가 용이해집니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-106">The benefits for creating custom functions and stored procedures include fast execution, centralized deployment, and improved maintainability.</span></span>  
  
 <span data-ttu-id="04c1f-107">다음 표에서는 ADOMD.NET 서버 애플리케이션을 개발하는 데 도움이 되는 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-107">The topics in the following table will help you develop ADOMD.NET server applications.</span></span>  
  
|<span data-ttu-id="04c1f-108">항목</span><span class="sxs-lookup"><span data-stu-id="04c1f-108">Topic</span></span>|<span data-ttu-id="04c1f-109">Description</span><span class="sxs-lookup"><span data-stu-id="04c1f-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="04c1f-110">ADOMD.NET Server 기능</span><span class="sxs-lookup"><span data-stu-id="04c1f-110">ADOMD.NET Server Functionality</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-functionality)|<span data-ttu-id="04c1f-111">ADOMD.NET 서버 개체의 사용 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-111">Describes the uses for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="04c1f-112">ADOMD.NET 서버 개체 아키텍처</span><span class="sxs-lookup"><span data-stu-id="04c1f-112">ADOMD.NET Server Object Architecture</span></span>](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-object-architecture)|<span data-ttu-id="04c1f-113">ADOMD.NET 서버 개체의 개체 아키텍처를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-113">Describes the object architecture for ADOMD.NET server objects.</span></span>|  
|[<span data-ttu-id="04c1f-114">사용자 정의 함수 및 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="04c1f-114">User Defined Functions and Stored Procedures</span></span>](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures)|<span data-ttu-id="04c1f-115">사용자 정의 함수 또는 저장 프로시저를 만드는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="04c1f-115">Walks you through the process of creating a user defined function or stored Procedure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04c1f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04c1f-116">See Also</span></span>  
 <span data-ttu-id="04c1f-117">[ADOMD.NET 클라이언트 프로그래밍](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span><span class="sxs-lookup"><span data-stu-id="04c1f-117">[ADOMD.NET Client Programming](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-client/adomd-net-client-programming) </span></span>  
 [<span data-ttu-id="04c1f-118">ADOMD.NET를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="04c1f-118">Developing with ADOMD.NET</span></span>](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
  
  
