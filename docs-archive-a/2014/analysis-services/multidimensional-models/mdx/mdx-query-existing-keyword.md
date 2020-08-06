---
title: EXISTING 키워드 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- EXISTING
helpviewer_keywords:
- Existing keyword
ms.assetid: 651ee9ac-04ef-4316-87c9-a3df5ac27d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 115444c832fe8fe9b258a0c23b97b97553f32e8e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646682"
---
# <a name="existing-keyword-mdx"></a><span data-ttu-id="962df-102">EXISTING 키워드(MDX)</span><span class="sxs-lookup"><span data-stu-id="962df-102">EXISTING Keyword (MDX)</span></span>
  <span data-ttu-id="962df-103">지정한 집합이 현재 컨텍스트 내에서 계산되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="962df-103">Forces a specified set to be evaluated within the current context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962df-104">구문</span><span class="sxs-lookup"><span data-stu-id="962df-104">Syntax</span></span>  
  
```  
  
Existing Set_Expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="962df-105">인수</span><span class="sxs-lookup"><span data-stu-id="962df-105">Arguments</span></span>  
 <span data-ttu-id="962df-106">*Set_Expression*</span><span class="sxs-lookup"><span data-stu-id="962df-106">*Set_Expression*</span></span>  
 <span data-ttu-id="962df-107">유효한 MDX 집합 식입니다.</span><span class="sxs-lookup"><span data-stu-id="962df-107">A valid Multidimensional Expressions (MDX) set expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="962df-108">설명</span><span class="sxs-lookup"><span data-stu-id="962df-108">Remarks</span></span>  
 <span data-ttu-id="962df-109">기본적으로 집합은 집합의 멤버가 포함된 큐브의 컨텍스트 내에서 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="962df-109">By default, sets are evaluated within the context of the cube that contains the members of the set.</span></span> <span data-ttu-id="962df-110">그러나 `Existing` 키워드는 지정된 집합이 현재 컨텍스트 내에서 계산되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="962df-110">The `Existing` keyword forces a specified set to be evaluated within the current context instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="962df-111">예제</span><span class="sxs-lookup"><span data-stu-id="962df-111">Example</span></span>  
 <span data-ttu-id="962df-112">다음 예에서는 사용자가 선택한 State-Province 멤버에 대해 `Aggregate` 함수를 사용하여 계산한 값에 따라 이전 기간에 비해 판매량이 감소한 대리점의 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="962df-112">The following example returns the count of the resellers whose sales have declined over the previous time period, based on user-selected State-Province member values evaluated using the `Aggregate` function.</span></span> <span data-ttu-id="962df-113">그러나 [Hierarchize&#40;MDX&#41;](/sql/mdx/hierarchize-mdx) 및 [DrilldownLevel(MDX)](/sql/mdx/drilldownlevel-mdx) 함수는 Product 차원의 제품 범주에 대해 판매량 감소 값을 반환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="962df-113">The [Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) and [DrilldownLevel (MDX)](/sql/mdx/drilldownlevel-mdx) functions are used to return values for declining sales for product categories in the Product dimension.</span></span> <span data-ttu-id="962df-114">`Existing`키워드는 `Filter` 현재 컨텍스트에서 (즉, 시/도 특성 계층의 워싱턴 및 Oregon 멤버에 대 한) 함수의 집합을 강제로 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="962df-114">The `Existing` keyword forces the set in the `Filter` function to be evaluated in the current context - that is, for the Washington and Oregon members of the State-Province attribute hierarchy.</span></span>  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS  
   Count  
      (Filter  
         (Existing  
            (Reseller.Reseller.Reseller)  
         , [Measures].[Reseller Sales Amount] <   
            ([Measures].[Reseller Sales Amount]  
               ,[Date].Calendar.PrevMember  
            )  
        )  
      )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate   
      ( {[Geography].[State-Province].&[WA]&[US]  
         , [Geography].[State-Province].&[OR]&[US] }   
      )  
SELECT NON EMPTY HIERARCHIZE   
      (AddCalculatedMembers   
         (   
            {DrillDownLevel  
               ({[Product].[All Products]}  
               )  
            }   
         )   
      ) DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE   
      ( [Geography].[State-Province].x  
        , [Date].[Calendar].[Calendar Quarter].&[2003]&[4]  
        ,[Measures].[Declining Reseller Sales]  
      )  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="962df-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="962df-115">See Also</span></span>  
 <span data-ttu-id="962df-116">[MDX&#41; &#40;&#40;집합 수&#41;](/sql/mdx/count-set-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-116">[Count &#40;Set&#41; &#40;MDX&#41;](/sql/mdx/count-set-mdx) </span></span>  
 <span data-ttu-id="962df-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-117">[AddCalculatedMembers &#40;MDX&#41;](/sql/mdx/addcalculatedmembers-mdx) </span></span>  
 <span data-ttu-id="962df-118">[MDX &#40;집계&#41;](/sql/mdx/aggregate-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-118">[Aggregate &#40;MDX&#41;](/sql/mdx/aggregate-mdx) </span></span>  
 <span data-ttu-id="962df-119">[MDX &#40;필터&#41;](/sql/mdx/filter-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-119">[Filter &#40;MDX&#41;](/sql/mdx/filter-mdx) </span></span>  
 <span data-ttu-id="962df-120">[MDX &#40;속성&#41;](/sql/mdx/properties-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-120">[Properties &#40;MDX&#41;](/sql/mdx/properties-mdx) </span></span>  
 <span data-ttu-id="962df-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-121">[DrilldownLevel &#40;MDX&#41;](/sql/mdx/drilldownlevel-mdx) </span></span>  
 <span data-ttu-id="962df-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span><span class="sxs-lookup"><span data-stu-id="962df-122">[Hierarchize &#40;MDX&#41;](/sql/mdx/hierarchize-mdx) </span></span>  
 [<span data-ttu-id="962df-123">MDX 함수 참조&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="962df-123">MDX Function Reference &#40;MDX&#41;</span></span>](/sql/mdx/mdx-function-reference-mdx)  
  
  
