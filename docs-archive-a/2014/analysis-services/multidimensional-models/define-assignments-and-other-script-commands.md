---
title: 할당 및 기타 스크립트 명령 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 184c998bb4bd27d077cca78e792a7e7712f87666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653616"
---
# <a name="define-assignments-and-other-script-commands"></a><span data-ttu-id="126dc-102">할당 및 기타 스크립트 명령 정의</span><span class="sxs-lookup"><span data-stu-id="126dc-102">Define Assignments and Other Script Commands</span></span>
  <span data-ttu-id="126dc-103">큐브 디자이너의 **계산** 탭에서 도구 모음의 **새 스크립트 명령** 아이콘을 클릭하여 빈 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-103">On the **Calculations** tab of Cube Designer, click the **New ScriptCommand** icon on the toolbar to create an empty script.</span></span> <span data-ttu-id="126dc-104">새 스크립트를 만들면 처음에 계산 탭의 **스크립트 구성 도우미** 창에 빈 제목과 함께 해당 스크립트가 표시 됩니다. 계산 식 창에 입력 한 문자는 **스크립트 구성 도우미**의 항목 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-104">When you create a new script, it initially is displayed with a blank title in the **Script Organizer** pane of the Calculations tab. The characters you type in the Calculation Expressions pane will be visible as the name of the item in **Script Organizer**.</span></span> <span data-ttu-id="126dc-105">따라서 첫 줄에 설명이 포함된 이름을 입력하여 **스크립트 구성 도우미** 창에서 해당 스크립트를 보다 쉽게 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-105">Therefore, you may want to type a commented name on the first line to more easily identify the script in the **Script Organizer** pane.</span></span> <span data-ttu-id="126dc-106">자세한 내용은 [Microsoft SQL Server 2005의 MDX 스크립팅 소개(Introduction to MDX Scripting in Microsoft SQL Server 2005)](https://go.microsoft.com/fwlink/?LinkId=81892)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="126dc-106">For more information, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span> <span data-ttu-id="126dc-107">MDX 쿼리 및 계산과 관련 된 성능 문제에 대 한 자세한 내용은 [SQL Server 2005 Analysis Services 성능 가이드](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)의 "효율적인 MDX 작성" 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="126dc-107">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="126dc-108">처음에 큐브 디자이너의 **계산** 탭으로 전환하면 **스크립트 구성 도우미** 창에 CALCULATE 명령이 포함된 단일 스크립트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-108">When you initially switch to the **Calculations** tab of Cube Designer, the **Script Organizer** pane contains a single script with a CALCULATE command.</span></span> <span data-ttu-id="126dc-109">CALCULATE 명령은 큐브에 있는 셀의 집계를 제어하며 큐브 집계 방법을 수동으로 지정하려는 경우에만 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-109">The CALCULATE command controls the aggregation of the cells in the cube and should be edited only if you intend to manually specify how the cube is to be aggregated.</span></span>  
  
 <span data-ttu-id="126dc-110">계산 식 창을 사용하여 MDX(Multidimensional Expressions) 구문으로 식을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-110">You can use the Calculation Expressions pane to build an expression in Multidimensional Expressions (MDX) syntax.</span></span> <span data-ttu-id="126dc-111">식을 작성하는 동안 **계산 도구** 창에서 계산 식 창으로 큐브 구성 요소, 함수 및 템플릿을 끌거나 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-111">While you build the expression, you can drag or copy cube components, functions, and templates from the **Calculation Tools** pane to the Calculation Expressions pane.</span></span> <span data-ttu-id="126dc-112">그러면 계산 식 창에서 항목을 놓거나 붙여넣은 위치에 해당 항목의 스크립트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-112">Doing so adds the script for the item to the Calculation Expressions pane in the location that you drop or paste it.</span></span> <span data-ttu-id="126dc-113">인수와 구분 기호(« 및 »)를 적절한 값으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-113">Replace arguments and their delimiters (« and ») with the appropriate values.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="126dc-114">계산 식 창을 사용하여 여러 문을 포함하는 식을 작성할 때는 MDX 스크립트의 마지막 줄을 제외한 모든 줄이 세미콜론(;)으로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-114">When writing an expression that contains multiple statements using the Calculation Expressions pane, ensure that all lines except the last line of the MDX script end with a semi-colon (;).</span></span> <span data-ttu-id="126dc-115">계산은 단일 MDX 스크립트로 연결되며 각 스크립트에는 세미콜론이 추가되어 MDX 스크립트가 올바르게 컴파일되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-115">Calculations are concatenated into a single MDX script, and each script has a semi-colon appended to it to ensure that the MDX script compiles correctly.</span></span> <span data-ttu-id="126dc-116">계산 식 창에서 스크립트의 마지막 줄에 세미콜론을 추가하면 큐브가 올바르게 생성되어 배포되지만 해당 큐브에 대해 쿼리를 실행할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="126dc-116">If you add a semi-colon to the last line of the script in the Calculation Expressions pane, the cube will build and deploy correctly but you will be unable to run queries against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126dc-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="126dc-117">See Also</span></span>  
 [<span data-ttu-id="126dc-118">다차원 모델의 계산</span><span class="sxs-lookup"><span data-stu-id="126dc-118">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
