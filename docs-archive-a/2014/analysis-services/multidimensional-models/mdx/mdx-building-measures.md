---
title: MDX로 측정값 작성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649737"
---
# <a name="building-measures-in-mdx"></a><span data-ttu-id="aafd7-102">MDX로 측정값 만들기</span><span class="sxs-lookup"><span data-stu-id="aafd7-102">Building Measures in MDX</span></span>
  <span data-ttu-id="aafd7-103">MDX에서 측정값은 테이블 형식 모델의 값을 반환하기 위해 식을 계산하여 확인되는 명명된 DAX 식입니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-103">In Multidimensional Expressions (MDX), a measure is a named DAX expression that is resolved by calculating the expression to return a value in a Tabular Model.</span></span> <span data-ttu-id="aafd7-104">이러한 정의에는 놀랄 만한 개념이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-104">This innocuous definition covers an incredible amount of ground.</span></span> <span data-ttu-id="aafd7-105">MDX 쿼리에서 측정값을 구성하고 사용할 수 있으면 테이블 형식 데이터에 대한 상당한 조작 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-105">The ability to construct and use measures in an MDX query provides a great deal of manipulation capability for tabular data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="aafd7-106">측정값은 테이블 형식 모델에서만 정의할 수 있습니다. 데이터베이스가 다차원 모드로 설정된 경우 측정값을 만들면 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-106">Measures can only be defined in tabular models; if your database is set in multidimensional mode, creating a measure will generate an error</span></span>  
  
 <span data-ttu-id="aafd7-107">MDX 쿼리의 일부로 정의되는 측정값을 만들어서 해당 범위가 쿼리로 제한되도록 하려면 WITH 키워드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-107">To create a measure that is defined as part of an MDX query, and therefore whose scope is limited to the query, you use the WITH keyword.</span></span> <span data-ttu-id="aafd7-108">그런 다음 MDX SELECT 문 내에서 측정값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-108">You can then use the measure within an MDX SELECT statement.</span></span> <span data-ttu-id="aafd7-109">이 방식을 사용할 경우 WITH 키워드를 사용하여 만든 계산 멤버는 SELECT 문을 배포하지 않아도 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-109">Using this approach, the calculated member created by using the WITH keyword can be changed without disturbing the SELECT statement.</span></span> <span data-ttu-id="aafd7-110">그러나 MDX 식에서 측정값을 참조하는 방법은 DAX 식에서와는 다릅니다. 측정값을 참조하려면 측정값을 [측정값] 차원의 멤버로 지정해야 합니다. 다음 MDX 예를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aafd7-110">However, in MDX you reference the measure in a different way than when in DAX expressions; to reference the measure you name it as a member of the [Measures] dimension, see the following MDX example:</span></span>  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 <span data-ttu-id="aafd7-111">위 MDX 식을 실행하면 다음 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aafd7-111">It will return the following data when executed:</span></span>  
  
||<span data-ttu-id="aafd7-112">Total Sales Amount</span><span class="sxs-lookup"><span data-stu-id="aafd7-112">Total Sales Amount</span></span>||  
|-|------------------------|-|  
|<span data-ttu-id="aafd7-113">2001</span><span class="sxs-lookup"><span data-stu-id="aafd7-113">2001</span></span>|<span data-ttu-id="aafd7-114">11331808.96</span><span class="sxs-lookup"><span data-stu-id="aafd7-114">11331808.96</span></span>||  
|<span data-ttu-id="aafd7-115">2002</span><span class="sxs-lookup"><span data-stu-id="aafd7-115">2002</span></span>|<span data-ttu-id="aafd7-116">30674773.18</span><span class="sxs-lookup"><span data-stu-id="aafd7-116">30674773.18</span></span>||  
|<span data-ttu-id="aafd7-117">2003</span><span class="sxs-lookup"><span data-stu-id="aafd7-117">2003</span></span>|<span data-ttu-id="aafd7-118">41993729.72</span><span class="sxs-lookup"><span data-stu-id="aafd7-118">41993729.72</span></span>||  
|<span data-ttu-id="aafd7-119">2004</span><span class="sxs-lookup"><span data-stu-id="aafd7-119">2004</span></span>|<span data-ttu-id="aafd7-120">25808962.34</span><span class="sxs-lookup"><span data-stu-id="aafd7-120">25808962.34</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="aafd7-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aafd7-121">See Also</span></span>  
 <span data-ttu-id="aafd7-122">[CREATE MEMBER 문 &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span><span class="sxs-lookup"><span data-stu-id="aafd7-122">[CREATE MEMBER Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member) </span></span>  
 <span data-ttu-id="aafd7-123">[Mdx 함수 참조 &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span><span class="sxs-lookup"><span data-stu-id="aafd7-123">[MDX Function Reference &#40;MDX&#41;](/sql/mdx/mdx-function-reference-mdx) </span></span>  
 [<span data-ttu-id="aafd7-124">SELECT 문&#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="aafd7-124">SELECT Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-manipulation-select)  
  
  
