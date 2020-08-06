---
title: 속성 값 만들기 및 사용 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- property values [MDX]
- queries [MDX], property values
- MDX [Analysis Services], property values
- Multidimensional Expressions [Analysis Services], property values
ms.assetid: 0cafb269-03c8-4183-b6e9-220f071e4ef2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67eadc6bc2f0bf6f318f20ad42a5cc9e7a5afa5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651942"
---
# <a name="creating-and-using-property-values-mdx"></a><span data-ttu-id="7ddec-102">속성 값 만들기 및 사용(MDX)</span><span class="sxs-lookup"><span data-stu-id="7ddec-102">Creating and Using Property Values (MDX)</span></span>
  <span data-ttu-id="7ddec-103">MDX는 차원, 수준, 멤버 및 셀에 대한 기본 및 사용자 정의 속성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-103">Multidimensional Expressions (MDX) supports intrinsic and user-defined properties for dimensions, levels, members, and cells.</span></span> <span data-ttu-id="7ddec-104">기본 속성은 개별 셀에 대해 고유한 이름과 캡션은 물론, 서식과 글꼴 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-104">The intrinsic properties provide unique names, captions, and even formatting and font sizes for individual cells.</span></span> <span data-ttu-id="7ddec-105">반면, 사용자 정의 속성은 거의 모든 종류의 특성을 멤버에 추가로 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-105">User-defined properties, on the other hand, can provide almost any kind of additional attribute to members.</span></span>  
  
 <span data-ttu-id="7ddec-106">기본 및 사용자 정의 속성은 다음 수준에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-106">Intrinsic and user-defined properties are available at the following levels:</span></span>  
  
 <span data-ttu-id="7ddec-107">**멤버 속성**</span><span class="sxs-lookup"><span data-stu-id="7ddec-107">**Member properties**</span></span>  
 <span data-ttu-id="7ddec-108">멤버 속성은 각 튜플에 있는 각 멤버에 대한 기본 정보를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-108">Member properties cover the basic information about each member in each tuple.</span></span> <span data-ttu-id="7ddec-109">이 기본 정보에는 멤버 이름, 부모 수준 및 자식의 수 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-109">This basic information includes the member name, parent level, the number of children, and so on.</span></span>  
  
 <span data-ttu-id="7ddec-110">멤버 속성 및 그 사용법에 대한 자세한 내용은 [멤버 속성 사용&#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddec-110">For information about member properties and how to use them, see [Using Member Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-member-properties.md).</span></span>  
  
 <span data-ttu-id="7ddec-111">**셀 속성**</span><span class="sxs-lookup"><span data-stu-id="7ddec-111">**Cell properties**</span></span>  
 <span data-ttu-id="7ddec-112">셀 속성에는 큐브와 같은 다차원 데이터 원본에 셀 내용과 서식에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ddec-112">Cell properties contain information about the content and format of cells in a multidimensional data source, such as a cube.</span></span>  
  
 <span data-ttu-id="7ddec-113">셀 속성 및 그 사용법에 대한 자세한 내용은 [셀 속성 사용&#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ddec-113">For more information about cell properties and how to use them, see [Using Cell Properties &#40;MDX&#41;](multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddec-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ddec-114">See Also</span></span>  
 [<span data-ttu-id="7ddec-115">MDX 쿼리 기본 사항&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7ddec-115">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
