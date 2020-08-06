---
title: 지원 되는 MDX (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], statements
- MDX [Analysis Services], functions
ms.assetid: 308bc0b3-4fd6-4435-972b-5e40d9e3c99b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e8df6a2aa6da6b88a07a2abdef99d6ea03d8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737029"
---
# <a name="supported-mdx-mdx"></a><span data-ttu-id="00ba1-102">지원되는 MDX(MDX)</span><span class="sxs-lookup"><span data-stu-id="00ba1-102">Supported MDX (MDX)</span></span>
  <span data-ttu-id="00ba1-103">MDX 스크립트 내에서는 다음 문과 함수가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="00ba1-103">The following statements and functions are supported within Multidimensional Expressions (MDX) Script:</span></span>  
  
 [<span data-ttu-id="00ba1-104">&#40;설명&#41;&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-104">&#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="00ba1-105">-- &#40;설명&#41;&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-105">-- &#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="00ba1-106">설명&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-106">Comment &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="00ba1-107">ALTER CUBE 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-107">ALTER CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-alter-cube)  
  
> [!NOTE]  
>  <span data-ttu-id="00ba1-108">MDX 스크립팅에서는 기본 멤버 변경만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="00ba1-108">Only altering the default member is supported in MDX Scripting.</span></span>  
  
 [<span data-ttu-id="00ba1-109">CALCULATE 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-109">CALCULATE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
 [<span data-ttu-id="00ba1-110">CASE 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-110">CASE Statement &#40;MDX&#41;</span></span>](/sql/mdx/case-statement-mdx)  
  
 [<span data-ttu-id="00ba1-111">CREATE CELL CALCULATION 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-111">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
 [<span data-ttu-id="00ba1-112">CREATE MEMBER 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-112">CREATE MEMBER Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-member)  
  
 [<span data-ttu-id="00ba1-113">CREATE SET 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-113">CREATE SET Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-set)  
  
 [<span data-ttu-id="00ba1-114">EXISTING 키워드&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-114">EXISTING Keyword &#40;MDX&#41;</span></span>](mdx-query-existing-keyword.md)  
  
 [<span data-ttu-id="00ba1-115">FREEZE 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-115">FREEZE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
 [<span data-ttu-id="00ba1-116">IF 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-116">IF Statement  &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-if)  
  
 [<span data-ttu-id="00ba1-117">This&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-117">This &#40;MDX&#41;</span></span>](/sql/mdx/this-mdx)  
  
> [!NOTE]  
>  <span data-ttu-id="00ba1-118">MDX는 `BACK_COLOR`, `FORE_COLOR`, `FORMAT_STRING`, `FONT_FLAGS`, `FONT_NAME` 및 `FONT_SIZE` 셀 속성에 대한 할당을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="00ba1-118">MDX supports assignment to the following cell properties: `BACK_COLOR`, `FORE_COLOR`, `FORMAT_STRING`, `FONT_FLAGS`, `FONT_NAME`, and `FONT_SIZE`.</span></span> <span data-ttu-id="00ba1-119">자세한 내용은 [셀 속성 사용&#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="00ba1-119">For more information, see [Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md).</span></span> <span data-ttu-id="00ba1-120">MDX는 `NON_EMPTY_BEHAVIOR` [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) 문의 속성에 대 한 할당도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="00ba1-120">MDX also supports assignment to the `NON_EMPTY_BEHAVIOR` property of the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span>  
  
 [<span data-ttu-id="00ba1-121">SCOPE 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-121">SCOPE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-scope)  
  
## <a name="see-also"></a><span data-ttu-id="00ba1-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00ba1-122">See Also</span></span>  
 [<span data-ttu-id="00ba1-123">기본 MDX 스크립트&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="00ba1-123">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)  
  
  
