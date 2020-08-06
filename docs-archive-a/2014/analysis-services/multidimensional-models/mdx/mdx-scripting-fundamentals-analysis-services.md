---
title: MDX 스크립팅 기본 사항 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], scripts
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [MDX]
- cubes [Analysis Services], calculations
- Multidimensional Expressions [Analysis Services], scripts
ms.assetid: fdecb3ce-7c87-4bab-8000-532ba7a29f96
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2f7638339d8fc366ee384d453f6df683f3bd41f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653608"
---
# <a name="mdx-scripting-fundamentals-analysis-services"></a><span data-ttu-id="df3c9-102">MDX 스크립팅 기본 사항(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="df3c9-102">MDX Scripting Fundamentals (Analysis Services)</span></span>
  <span data-ttu-id="df3c9-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]에서 MDX(Multidimensional Expression) 스크립트는 계산으로 큐브를 채우는 한 개 이상의 MDX 식 또는 문으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-103">In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], a Multidimensional Expressions (MDX) script is made up of one or more MDX expressions or statements that populate a cube with calculations.</span></span>  
  
 <span data-ttu-id="df3c9-104">MDX 스크립트는 큐브의 계산 프로세스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-104">An MDX script defines the calculation process for a cube.</span></span> <span data-ttu-id="df3c9-105">MDX 스크립트는 또한 큐브 자체의 일부로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-105">An MDX script is also considered part of the cube itself.</span></span> <span data-ttu-id="df3c9-106">따라서 큐브와 관련된 MDX 스크립트를 변경하면 해당 큐브의 계산 프로세스가 즉시 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-106">Therefore, changing an MDX script associated with a cube immediately changes the calculation process for the cube.</span></span>  
  
 <span data-ttu-id="df3c9-107">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 큐브 디자이너에서 MDX 스크립트를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-107">To create MDX scripts, you can use Cube Designer in the [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="df3c9-108">자세한 내용은 [할당 및 기타 스크립트 명령 정의](../define-assignments-and-other-script-commands.md) 및 [Microsoft SQL Server 2005의 MDX 스크립팅 소개](https://go.microsoft.com/fwlink/?LinkId=81892)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df3c9-108">For more information, see [Define Assignments and Other Script Commands](../define-assignments-and-other-script-commands.md) and [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span>  
  
 <span data-ttu-id="df3c9-109">MDX 쿼리 및 계산과 관련된 성능 문제에 대한 자세한 내용은 [SQL Server Analysis Services 성능 가이드](https://go.microsoft.com/fwlink/p/?LinkId=399050)(영문)의 MDX 최적화 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df3c9-109">For performance issues related to MDX queries and calculations, see the MDX optimization section in the [SQL Server Analysis Services Performance Guide](https://go.microsoft.com/fwlink/p/?LinkId=399050).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df3c9-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="df3c9-110">In This Section</span></span>  
  
|<span data-ttu-id="df3c9-111">항목</span><span class="sxs-lookup"><span data-stu-id="df3c9-111">Topic</span></span>|<span data-ttu-id="df3c9-112">Description</span><span class="sxs-lookup"><span data-stu-id="df3c9-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="df3c9-113">기본 MDX 스크립트&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-113">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)|<span data-ttu-id="df3c9-114">각 큐브에서 제공되는 기본 MDX 스크립트 및 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 큐브 안에서 MDX 스크립트가 작동하는 방식을 포함하여 기본 MDX 스크립트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-114">Details the basic MDX script, including the default MDX script provided in each cube, and how MDX scripts generally function within a cube in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="df3c9-115">범위 및 컨텍스트 관리&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-115">Managing Scope and Context &#40;MDX&#41;</span></span>](managing-scope-and-context-mdx.md)|<span data-ttu-id="df3c9-116">[CALCULATE](/sql/mdx/mdx-scripting-calculate) 문, [SCOPE](/sql/mdx/mdx-scripting-scope) 문, 그리고 [This](/sql/mdx/this-mdx) 함수를 사용하여 MDX 스크립트에서 컨텍스트 및 범위를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-116">Describes how to use the [CALCULATE](/sql/mdx/mdx-scripting-calculate) statement, the [SCOPE](/sql/mdx/mdx-scripting-scope) statement, and the [This](/sql/mdx/this-mdx) function to manage context and scope within an MDX script.</span></span>|  
|[<span data-ttu-id="df3c9-117">변수 및 매개 변수 사용&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-117">Using Variables and Parameters &#40;MDX&#41;</span></span>](using-variables-and-parameters-mdx.md)|<span data-ttu-id="df3c9-118">MDX 스크립트에서 변수 및 매개 변수를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-118">Describes how to use variables and parameters in an MDX script.</span></span>|  
|[<span data-ttu-id="df3c9-119">오류 처리&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-119">Error Handling &#40;MDX&#41;</span></span>](error-handling-mdx.md)|<span data-ttu-id="df3c9-120">MDX 스크립트 내의 오류 처리 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-120">Explains error handling within an MDX script.</span></span>|  
|[<span data-ttu-id="df3c9-121">지원되는 MDX&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-121">Supported MDX &#40;MDX&#41;</span></span>](supported-mdx-mdx.md)|<span data-ttu-id="df3c9-122">MDX 스크립트에서 지원되는 MDX 연산자, 문 및 함수 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df3c9-122">Provides a list of supported MDX operators, statements, and functions within an MDX script.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df3c9-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df3c9-123">See Also</span></span>  
 [<span data-ttu-id="df3c9-124">MDX 언어 참조&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="df3c9-124">MDX Language Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-language-reference-mdx)  
  
  
