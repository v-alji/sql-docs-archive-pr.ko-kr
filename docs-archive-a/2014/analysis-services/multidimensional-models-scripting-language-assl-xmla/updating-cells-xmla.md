---
title: 셀 업데이트 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- modifying cells
- XMLA, cells
- updating cells
- cells [Analysis Services]
- XML for Analysis, cells
ms.assetid: a1c61496-36ee-4bce-98d9-d13440d349aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2c3d9a7c27533666c75102d9eac3b8311bfe4af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738944"
---
# <a name="updating-cells-xmla"></a><span data-ttu-id="4398a-102">셀 업데이트(XMLA)</span><span class="sxs-lookup"><span data-stu-id="4398a-102">Updating Cells (XMLA)</span></span>
  <span data-ttu-id="4398a-103">[UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) 명령을 사용 하 여 큐브 쓰기 저장 (writeback)에 사용 하도록 설정 된 큐브에 있는 하나 이상의 셀 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-103">You can use the [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) command to change the value of one or more cells in a cube enabled for cube writeback.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="4398a-104">업데이트할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 셀을 포함 하는 각 파티션에 대해 업데이트 된 정보를 별도의 쓰기 저장 (writeback) 테이블에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stores the updated information in a separate writeback table for each partition that contains cells to be updated.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4398a-105">`UpdateCells` 명령은 큐브 쓰기 저장(writeback) 동안 할당을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-105">The `UpdateCells` command does not support allocations during cube writeback.</span></span> <span data-ttu-id="4398a-106">할당 된 쓰기 저장 (writeback)을 사용 하려면 [statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) 명령을 사용 하 여 MDX (Multidimensional EXPRESSIONS) UPDATE 문을 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-106">To use allocated writeback, you should use the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command to send a Multidimensional Expressions (MDX) UPDATE statement.</span></span> <span data-ttu-id="4398a-107">자세한 내용은 [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4398a-107">For more information, see [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).</span></span>  
  
## <a name="specifying-cells"></a><span data-ttu-id="4398a-108">셀 지정</span><span class="sxs-lookup"><span data-stu-id="4398a-108">Specifying Cells</span></span>  
 <span data-ttu-id="4398a-109">명령의 [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) 속성은 `UpdateCells` 업데이트할 셀을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-109">The [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property of the `UpdateCells` command contains the cells to be updated.</span></span> <span data-ttu-id="4398a-110">해당 셀의 서수 번호를 사용하여 `Cell` 속성의 각 셀을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-110">You identify each cell in the `Cell` property using that cell's ordinal number.</span></span> <span data-ttu-id="4398a-111">개념적으로는 큐브가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] *p*차원 배열인 것 처럼 큐브에서 셀의 번호를 표시 합니다. 여기서 *p* 는 축 수입니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-111">Conceptually, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] numbers cells in a cube as if the cube were a *p*-dimensional array, where *p* is the number of axes.</span></span> <span data-ttu-id="4398a-112">셀은 행 중심의 순서로 번호가 매겨집니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-112">Cells are addressed in row-major order.</span></span> <span data-ttu-id="4398a-113">다음 그림에서는 셀의 서수 번호를 계산하는 수식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-113">The following illustration shows the formula for calculating the ordinal number of a cell.</span></span>  
  
 <span data-ttu-id="4398a-114">![셀 서수 위치 계산 수식](../../analysis-services/dev-guide/media/cellordinalformula.gif "셀 서수 위치 계산 수식")</span><span class="sxs-lookup"><span data-stu-id="4398a-114">![Formula to calculate the cell ordinal position](../../analysis-services/dev-guide/media/cellordinalformula.gif "Formula to calculate the cell ordinal position")</span></span>  
  
 <span data-ttu-id="4398a-115">셀의 서 수를 알고 있는 경우 [셀](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) 속성의 [value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) 속성에 원하는 셀 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4398a-115">Once you know a cell's ordinal number, you can indicate the intended value of the cell in the [Value](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/value-element-xmla) property of the [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4398a-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4398a-116">See Also</span></span>  
 <span data-ttu-id="4398a-117">[XMLA&#41;요소 &#40;업데이트](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="4398a-117">[Update Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla) </span></span>  
 [<span data-ttu-id="4398a-118">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="4398a-118">Developing with XMLA in Analysis Services</span></span>](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
