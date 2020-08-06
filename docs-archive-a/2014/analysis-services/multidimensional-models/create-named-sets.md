---
title: 명명 된 집합 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
ms.openlocfilehash: e92984102ceb8ad0ac049c15870e9f1efd6090fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728895"
---
# <a name="create-named-sets"></a><span data-ttu-id="5c995-102">명명된 집합 만들기</span><span class="sxs-lookup"><span data-stu-id="5c995-102">Create Named Sets</span></span>
  <span data-ttu-id="5c995-103">명명된 집합은 MDX(Multidimensional Expressions) 쿼리 등에서 다시 사용할 수 있도록 생성되는 집합 식이나 차원 멤버 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-103">A named set is a set of dimension members or a set expression that is created for reuse, for example in Multidimensional Expressions (MDX) queries.</span></span> <span data-ttu-id="5c995-104">큐브 데이터, 산술 연산자, 숫자 및 함수를 조합하여 명명된 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-104">You can create named sets by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="5c995-105">예를 들어 Production 측정값에 대한 최상위 값을 갖는 Factories 차원의 10개 멤버가 포함된 명명된 집합을 Top Ten Factories라는 이름으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-105">For example, you can create a named set called Top Ten Factories that contains the ten members of the Factories dimension that have the highest values for the Production measure.</span></span> <span data-ttu-id="5c995-106">이 Top Ten Factories를 최종 사용자가 쿼리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-106">Top Ten Factories can then be used in queries by end users.</span></span> <span data-ttu-id="5c995-107">예를 들어 최종 사용자는 Top Ten Factories를 한 축에 배치하고 다른 축에는 Production을 포함하여 Measures 차원을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-107">For example, an end user can place Top Ten Factories on one axis and the Measures dimension, including Production, on another axis.</span></span> <span data-ttu-id="5c995-108">자세한 내용은 [다차원 모델의 계산](calculations-in-multidimensional-models.md) 및 [명명된 집합을 MDX로 작성&#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5c995-108">For more information, see [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md), and [Building Named Sets in MDX &#40;MDX&#41;](mdx/mdx-named-sets-building-named-sets.md).</span></span>  
  
 <span data-ttu-id="5c995-109">명명된 집합을 만들려면 큐브 디자이너의 **계산** 탭에 있는 **새 명명된 집합** 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-109">To create a named set, use the **New Named Set** command on the **Calculations** tab of Cube Designer.</span></span> <span data-ttu-id="5c995-110">**계산** 탭 도구 모음의 **큐브** 메뉴에서 이 명령을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-110">This command can be invoked on the **Cube** menu on the **Calculations** tab toolbar.</span></span> <span data-ttu-id="5c995-111">이 명령은 명명된 집합에 대해 다음과 같은 옵션을 지정할 수 있는 폼을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-111">This command displays a form to specify the following options for the named set:</span></span>  
  
 <span data-ttu-id="5c995-112">**이름**</span><span class="sxs-lookup"><span data-stu-id="5c995-112">**Name**</span></span>  
 <span data-ttu-id="5c995-113">명명된 집합의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-113">Select the name of the named set.</span></span> <span data-ttu-id="5c995-114">이 이름은 큐브를 찾아볼 때 최종 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-114">This name appears to end users when they browse the cube.</span></span>  
  
 <span data-ttu-id="5c995-115">**식**</span><span class="sxs-lookup"><span data-stu-id="5c995-115">**Expression**</span></span>  
 <span data-ttu-id="5c995-116">명명된 집합을 만드는 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-116">Specify the expression that produces the named set.</span></span> <span data-ttu-id="5c995-117">MDX로 이 식을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-117">This expression can be written in MDX.</span></span> <span data-ttu-id="5c995-118">식에 포함할 수 있는 항목들은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-118">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="5c995-119">차원, 수준, 측정값 등 큐브 구성 요소를 나타내는 데이터 식</span><span class="sxs-lookup"><span data-stu-id="5c995-119">Data expressions that represent cube components such as dimensions, levels, measures, and so on.</span></span>  
  
-   <span data-ttu-id="5c995-120">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="5c995-120">Arithmetic operators.</span></span>  
  
-   <span data-ttu-id="5c995-121">숫자</span><span class="sxs-lookup"><span data-stu-id="5c995-121">Numbers.</span></span>  
  
-   <span data-ttu-id="5c995-122">함수</span><span class="sxs-lookup"><span data-stu-id="5c995-122">Functions.</span></span>  
  
 <span data-ttu-id="5c995-123">**계산 도구** 창의 **메타데이터** 탭에서 큐브 구성 요소를 복사하거나 **명명된 집합 폼 편집기** 창의 **식** 상자로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-123">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span> <span data-ttu-id="5c995-124">**계산 도구** 창의 **함수** 탭에서 함수를 복사하거나 **명명된 집합 폼 편집기** 창의 **식** 상자로 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5c995-124">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the **Named Set Form Editor** pane.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5c995-125">집합에 있는 멤버의 이름을 명시적으로 지정 하 여 집합 식을 만드는 경우 멤버 목록을 중괄호 () 쌍으로 묶습니다 {} .</span><span class="sxs-lookup"><span data-stu-id="5c995-125">If you create the set expression by explicitly naming the members in the set, enclose the list of members in a pair of braces ({}).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c995-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5c995-126">See Also</span></span>  
 [<span data-ttu-id="5c995-127">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="5c995-127">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
