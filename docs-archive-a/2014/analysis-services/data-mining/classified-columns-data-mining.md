---
title: 분류 된 열 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c264dfb6a97b8b8f576966e8929f6b0dc51e4ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653675"
---
# <a name="classified-columns-data-mining"></a><span data-ttu-id="8a738-102">분류된 열(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="8a738-102">Classified Columns (Data Mining)</span></span>
  <span data-ttu-id="8a738-103">분류된 열을 정의할 경우 마이닝 구조의 현재 열과 다른 열 간에 관계를 생성하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-103">When you define a classified column, you create a relationship between the current column and another column in the mining structure.</span></span> <span data-ttu-id="8a738-104">분류된 열로 지정한 마이닝 구조 열의 데이터에는 마이닝 구조의 다른 열의 값을 설명하는 범주 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-104">The data in the mining structure column that you designate as the classified column contains categorical information that describes the values in another column in the mining structure.</span></span>  
  
 <span data-ttu-id="8a738-105">예를 들어 숫자 데이터를 포함하는 두 개의 열이 있다고 가정합니다. [Yearly Purchases] 열에는 특정 달력 연도의 고객당 연간 총 구매액에 들어 있고, 다른 열인 [Standard Deviations] 열에는 그러한 값에 대한 표준 편차가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-105">For example, suppose you have two columns with numerical data: one column, [Yearly Purchases], contains the total yearly purchases per customer for a specific calendar year, and the other column, [Standard Deviations], contains the standard deviations for those values.</span></span> <span data-ttu-id="8a738-106">이 경우 [Yearly Purchases] 열을 분류된 열로 지정할 수 있으며 그러면 모델에서 분석에 이 관계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-106">In this case you could designate the [Yearly Purchases] column as the classified column, and the model would be able to use this relationship in analysis.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8a738-107">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 제공하는 알고리즘은 분류된 열의 사용을 지원하지 않습니다. 이 기능은 사용자 지정 알고리즘을 만드는 데 사용하기 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-107">The algorithms provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] do not support the use of classified columns; this feature is provided for use in creating custom algorithms.</span></span>  
  
## <a name="defining-a-classified-column"></a><span data-ttu-id="8a738-108">분류된 열 정의</span><span class="sxs-lookup"><span data-stu-id="8a738-108">Defining a Classified Column</span></span>  
 <span data-ttu-id="8a738-109">분류된 열의 데이터 형식은 `Long` 또는 `Double` 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-109">The data type of a classified column must be either `Long` or `Double`.</span></span>  
  
 <span data-ttu-id="8a738-110">다음 목록에서는 분류된 열에 대해 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 지원하는 내용 유형을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-110">The following list describes the content types that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports for classified columns.</span></span>  
  
 <span data-ttu-id="8a738-111">**따르는**</span><span class="sxs-lookup"><span data-stu-id="8a738-111">**PROBABILITY**</span></span>  
 <span data-ttu-id="8a738-112">이 열의 값은 관련 값의 확률이며 0에서 1 사이의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-112">The value in the column is the probability of the associated value, and is a number between 0 and 1.</span></span>  
  
 <span data-ttu-id="8a738-113">**반대로**</span><span class="sxs-lookup"><span data-stu-id="8a738-113">**VARIANCE**</span></span>  
 <span data-ttu-id="8a738-114">이 열의 값은 관련 값의 분산입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-114">The value in the column is the variance of the associated value.</span></span>  
  
 <span data-ttu-id="8a738-115">**STDEV**</span><span class="sxs-lookup"><span data-stu-id="8a738-115">**STDEV**</span></span>  
 <span data-ttu-id="8a738-116">이 열의 값은 관련 값의 표준 편차입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-116">The value in the column is the standard deviation of the associated value.</span></span>  
  
 <span data-ttu-id="8a738-117">**PROBABILITY_VARIANCE**</span><span class="sxs-lookup"><span data-stu-id="8a738-117">**PROBABILITY_VARIANCE**</span></span>  
 <span data-ttu-id="8a738-118">이 열의 값은 관련 값에 대한 확률의 분산입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-118">The value in the column is the variance of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="8a738-119">**PROBABILITY_STDEV**</span><span class="sxs-lookup"><span data-stu-id="8a738-119">**PROBABILITY_STDEV**</span></span>  
 <span data-ttu-id="8a738-120">이 열의 값은 관련 값에 대한 확률의 표준 편차입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-120">The value in the column is the standard deviation of the probability for the associated value.</span></span>  
  
 <span data-ttu-id="8a738-121">**지원은**</span><span class="sxs-lookup"><span data-stu-id="8a738-121">**SUPPORT**</span></span>  
 <span data-ttu-id="8a738-122">이 열의 값은 관련 값의 가중치 또는 사례 복제 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8a738-122">The value in the column is the weight, or case replication factor, of the associated value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a738-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a738-123">See Also</span></span>  
 <span data-ttu-id="8a738-124">[데이터 마이닝&#41;&#40;내용 유형](content-types-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8a738-124">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) </span></span>  
 <span data-ttu-id="8a738-125">[마이닝 구조 &#40;Analysis Services 데이터 마이닝&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="8a738-125">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="8a738-126">데이터 형식&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="8a738-126">Data Types &#40;Data Mining&#41;</span></span>](data-types-data-mining.md)  
  
  
