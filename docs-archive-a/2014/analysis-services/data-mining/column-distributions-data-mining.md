---
title: 열 배포 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- normal distribution type [data mining]
- uniform distribution type [data mining]
- columns [data mining], distributions
- log normal distribution type [data mining]
- continuous columns
- distributions [data mining]
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
author: minewiskan
ms.author: owend
ms.openlocfilehash: 29aad33535c4cc4d9baf4c453249ce3b51595e78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661435"
---
# <a name="column-distributions-data-mining"></a><span data-ttu-id="75d89-102">열 배포(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="75d89-102">Column Distributions (Data Mining)</span></span>
  <span data-ttu-id="75d89-103">에서는 마이닝 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 구조에서 열 배포를 정의 하 여 마이닝 모델을 만들 때 알고리즘이 이러한 열의 데이터를 처리 하는 방법에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models.</span></span> <span data-ttu-id="75d89-104">이렇게 하면 공통적인 값 배포가 열에 포함되어 있을 경우 모델을 처리하기 전에 몇몇 알고리즘에서 연속 열 배포를 정의하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-104">For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values.</span></span> <span data-ttu-id="75d89-105">배포를 정의하지 않으면 알고리즘이 데이터를 해석하는 데 사용할 정보가 더 줄어듭니다. 따라서 마이닝 모델에서 얻는 예측의 정확도가 배포를 정의했을 경우보다 낮아질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-105">If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.</span></span>

 <span data-ttu-id="75d89-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 사용 가능한 알고리즘은 다음 배포 유형을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-106">The algorithms that are available in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] support the following distribution types:</span></span>

 <span data-ttu-id="75d89-107">`Normal`연속 열에 대 한 값은 정규 분포를 사용 하는 히스토그램을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-107">`Normal` The values for the continuous column form a histogram with a normal distribution.</span></span>

 <span data-ttu-id="75d89-108">![정규 분포를 보여 주는 히스토그램](../media/normal-distribution.gif "정규 분포를 보여 주는 히스토그램")</span><span class="sxs-lookup"><span data-stu-id="75d89-108">![Histogram with normal distribution](../media/normal-distribution.gif "Histogram with normal distribution")</span></span>

 <span data-ttu-id="75d89-109">`Log Normal`연속 열에 대 한 값은 히스토그램을 형성 합니다. 여기서 곡선이 위쪽 끝에 곡선은 늘어나고 곡선은 아래쪽 끝에 기울어집니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-109">`Log Normal` The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.</span></span>

 <span data-ttu-id="75d89-110">![로그 정규 분포를 보여 주는 히스토그램](../media/log-normal-distribution.gif "로그 정규 분포를 보여 주는 히스토그램")</span><span class="sxs-lookup"><span data-stu-id="75d89-110">![Histogram with log normal distribution](../media/log-normal-distribution.gif "Histogram with log normal distribution")</span></span>

 <span data-ttu-id="75d89-111">`Uniform`연속 열에 대 한 값은 모든 값이 동일 하 게 될 가능성이 있는 플랫 곡선을 형성 합니다.</span><span class="sxs-lookup"><span data-stu-id="75d89-111">`Uniform` The values for the continuous column form a flat curve, in which all values are equally likely.</span></span>

 <span data-ttu-id="75d89-112">![균일한 분포를 보여 주는 히스토그램](../media/uniform-distribution.gif "균일한 분포를 보여 주는 히스토그램")</span><span class="sxs-lookup"><span data-stu-id="75d89-112">![Histogram with uniform distribution](../media/uniform-distribution.gif "Histogram with uniform distribution")</span></span>

 <span data-ttu-id="75d89-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 제공하는 알고리즘에 대한 자세한 내용은 [데이터 마이닝 알고리즘&#40;Analysis Services - 데이터 마이닝&#41;](data-mining-algorithms-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75d89-113">For more information about the algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75d89-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75d89-114">See Also</span></span>
 <span data-ttu-id="75d89-115">[콘텐츠 형식 &#40;데이터 마이닝&#41;](content-types-data-mining.md) [마이닝 구조 &#40;Analysis Services 데이터](mining-structures-analysis-services-data-mining.md) 마이닝&#41;분할 메서드 &#40;[DMX](/sql/dmx/distributions-dmx)&#41;[마이닝 구조 열](mining-structure-columns.md) &#40;데이터 마이닝&#41;분할 [방법](discretization-methods-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="75d89-115">[Content Types &#40;Data Mining&#41;](content-types-data-mining.md) [Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) [Discretization Methods &#40;Data Mining&#41;](discretization-methods-data-mining.md) [Distributions &#40;DMX&#41;](/sql/dmx/distributions-dmx) [Mining Structure Columns](mining-structure-columns.md)</span></span>


