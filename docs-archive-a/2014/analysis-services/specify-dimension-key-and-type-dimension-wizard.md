---
title: 차원 키 및 유형 지정 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653560"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a><span data-ttu-id="7c82a-102">차원 키 및 유형 지정(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="7c82a-102">Specify Dimension Key and Type (Dimension Wizard)</span></span>
  <span data-ttu-id="7c82a-103">**차원 키 및 유형 지정** 페이지를 사용하여 차원의 키 특성을 정의하고 차원이 SCD(느린 변경 차원)인지 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-103">Use the **Specify Dimension Key and Type** page to define the key attribute of the dimension and to indicate whether the dimension is a slowly changing dimension (SCD).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c82a-104"> 이 페이지는 **생성 방법 선택** 페이지에서 **데이터 원본을 사용하지 않고 차원 생성** 을 선택하고 **차원 유형 선택** 페이지에서 **표준 차원** 을 선택한 경우에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-104">This page is displayed only if you selected **Build the dimension without using a data source** on the **Select Build Method** page and if you selected **Standard dimension** on the **Select the Dimension Type** page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7c82a-105">옵션</span><span class="sxs-lookup"><span data-stu-id="7c82a-105">Options</span></span>  
 <span data-ttu-id="7c82a-106">**키 특성**</span><span class="sxs-lookup"><span data-stu-id="7c82a-106">**Key attribute**</span></span>  
 <span data-ttu-id="7c82a-107">차원의 키 특성으로 할 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-107">Select the attribute that will be the key attribute for the dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c82a-108">차원에 정의된 특성이 없는 경우 이 옵션에 대해 **키 특성을 자동으로 만듭니다**</span><span class="sxs-lookup"><span data-stu-id="7c82a-108">If no attributes have been defined for the dimension, the only value available for this option is **Create key attribute automatically.**</span></span> <span data-ttu-id="7c82a-109">값만 사용할 수 있습니다. 차원에 정의된 특성이 있는 경우에는 이 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-109">This value is not available if any attributes are defined for the dimension.</span></span>  
  
 <span data-ttu-id="7c82a-110">**변경 차원임**</span><span class="sxs-lookup"><span data-stu-id="7c82a-110">**This is a changing dimension**</span></span>  
 <span data-ttu-id="7c82a-111">차원이 느린 변경 차원임을 나타내려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-111">Select to indicate that the dimension is a slowly changing dimension.</span></span> <span data-ttu-id="7c82a-112">이 옵션을 선택하면 차원의 계층 내에 있는 멤버의 시간에 따른 이동을 추적하는 데 사용할 수 있는 추가 열 및 특성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="7c82a-112">Selecting this option will create additional columns and attributes that can be used to track the movement of members within the hierarchies of the dimension over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c82a-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c82a-113">See Also</span></span>  
 <span data-ttu-id="7c82a-114">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="7c82a-114">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="7c82a-115">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7c82a-115">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7c82a-116">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="7c82a-116">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
