---
title: 저장 프로시저 디자인 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732160"
---
# <a name="designing-stored-procedures"></a><span data-ttu-id="64e06-102">저장 프로시저 디자인</span><span class="sxs-lookup"><span data-stu-id="64e06-102">Designing Stored Procedures</span></span>
  <span data-ttu-id="64e06-103">저장 프로시저에서 관리 개체 모델 AMO(Analysis Management Objects) 및 클라이언트 기반 개체 모델 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ADO MD(ActiveX  Data Objects Multidimensional)를 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-103">Both the administrative object model Analysis Management Objects (AMO) and the client oriented object model [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX® Data Objects (Multidimensional) (ADO MD) are available in stored procedures.</span></span>  
  
 <span data-ttu-id="64e06-104">저장 프로시저는 호출할 MDX(Multidimensional Expressions) 수준에 표시되는 범위(서버 또는 데이터베이스)에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-104">Stored procedures must be in scope (either the server or the database) to be visible at the Multidimensional Expressions (MDX) level to be called.</span></span> <span data-ttu-id="64e06-105">그러나 저장 프로시저를 호출한 후에는 범위가 저장 프로시저의 부모 동작으로 제한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-105">However, once a stored procedure is invoked, its scope is not limited to actions under its parent.</span></span> <span data-ttu-id="64e06-106">저장 프로시저는 저장 프로시저를 호출한 사용자 프로세스의 보안 제한 사항이나 저장 프로시저가 작동 중인 트랜잭션의 제한 사항을 위반하지 않는 한 서버의 모든 범위에서 변경 또는 수정 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-106">A stored procedure may make changes or modifications anywhere on the server, subject only to the security limitations of the user process that invokes it or to the limitations of the transaction in which it is operating.</span></span>  
  
 <span data-ttu-id="64e06-107">서버 범위 프로시저는 서버의 모든 컨텍스트에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-107">Server scope procedures are available in all contexts on the server.</span></span> <span data-ttu-id="64e06-108">데이터베이스 범위 저장 프로시저는 저장 프로시저가 정의된 데이터베이스의 컨텍스트에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-108">Database scope stored procedures are visible only in the database context of the database in which they are defined.</span></span>  
  
 <span data-ttu-id="64e06-109">다른 MDX 함수와 마찬가지로 저장 프로시저가 먼저 해결되어야 MDX 세션이 계속될 수 있습니다. 저장 프로시저는 실행되는 동안 MDX 세션을 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-109">As with any MDX function, stored procedure must be resolved before an MDX session can continue; stored procedures lock MDX sessions while executing.</span></span> <span data-ttu-id="64e06-110">사용자 상호 작용을 보류하는 MDX 세션을 중지해야 할 특별한 이유가 없다면 MDX 세션을 유지하여 대화 상자와 같은 사용자 상호 작용을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-110">Unless a specific reason exists to halt an MDX session pending user interaction, then user interactions (such as dialog boxes) are discouraged.</span></span>  
  
## <a name="dependent-assemblies"></a><span data-ttu-id="64e06-111">종속 어셈블리</span><span class="sxs-lookup"><span data-stu-id="64e06-111">Dependent Assemblies</span></span>  
 <span data-ttu-id="64e06-112">모든 종속 어셈블리는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 로드되어 CLR(공용 언어 런타임)에서 참조할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-112">All dependent assemblies must be loaded into an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to be found by the common language runtime (CLR).</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="64e06-113">에서는 종속 어셈블리를 주 어셈블리와 같은 폴더에 저장하므로 CLR에서 이러한 어셈블리의 함수에 대한 모든 함수 참조가 자동으로 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="64e06-113">stores the dependent assemblies in the same folder as the main assembly, so the CLR automatically resolves all function references to functions in those assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e06-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64e06-114">See Also</span></span>  
 <span data-ttu-id="64e06-115">[다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="64e06-115">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="64e06-116">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="64e06-116">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
