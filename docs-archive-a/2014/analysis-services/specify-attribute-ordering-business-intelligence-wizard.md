---
title: 특성 순서 지정 (비즈니스 인텔리전스 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.specifyordering.setordering.f1
ms.assetid: fc0678fc-e188-4d13-8deb-9daa1281b734
author: minewiskan
ms.author: owend
ms.openlocfilehash: b6a361aa4ef69d83e321de90f316eab4e5659a61
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736843"
---
# <a name="specify-attribute-ordering-business-intelligence-wizard"></a><span data-ttu-id="82e5f-102">특성 순서 지정(비즈니스 인텔리전스 마법사)</span><span class="sxs-lookup"><span data-stu-id="82e5f-102">Specify Attribute Ordering (Business Intelligence Wizard)</span></span>
  <span data-ttu-id="82e5f-103">**특성 순서 지정** 페이지를 사용하여 선택한 차원 내 특성의 순서 특성 및 순서 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-103">Use the **Specify Attribute Ordering** page to specify the ordering attributes and ordering criteria for attributes in the selected dimension.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82e5f-104">옵션</span><span class="sxs-lookup"><span data-stu-id="82e5f-104">Options</span></span>  
 <span data-ttu-id="82e5f-105">**특성**</span><span class="sxs-lookup"><span data-stu-id="82e5f-105">**Attribute**</span></span>  
 <span data-ttu-id="82e5f-106">차원에 사용 가능한 특성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-106">Displays the attributes available for the dimension.</span></span>  
  
 <span data-ttu-id="82e5f-107">**순서 특성**</span><span class="sxs-lookup"><span data-stu-id="82e5f-107">**Ordering Attribute**</span></span>  
 <span data-ttu-id="82e5f-108">해당 **특성**의 순서를 지정할 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-108">Select the attribute with which to order the corresponding **Attribute**.</span></span> <span data-ttu-id="82e5f-109">동일한 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-109">You can specify the same attribute.</span></span>  
  
 <span data-ttu-id="82e5f-110">새 순서 특성을 만들려면를 선택 하 **\<New attribute>** 고 **열 선택** 대화 상자에서 새 특성이 기반으로 할 열을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-110">To create a new ordering attribute, select **\<New attribute>**, and in the **Select a Column** dialog box, select the column on which the new attribute is to be based.</span></span>  
  
 <span data-ttu-id="82e5f-111">**조건**</span><span class="sxs-lookup"><span data-stu-id="82e5f-111">**Criteria**</span></span>  
 <span data-ttu-id="82e5f-112">해당 **특성** 내 멤버의 순서를 지정하는 데 사용할 조건을 **순서 특성**에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-112">Specify the criteria from the **Ordering Attribute** to use to order the members in the corresponding **Attribute**.</span></span> <span data-ttu-id="82e5f-113">다음 표에서는 사용 가능한 조건을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-113">The following table lists the available criteria.</span></span>  
  
|<span data-ttu-id="82e5f-114">값</span><span class="sxs-lookup"><span data-stu-id="82e5f-114">Value</span></span>|<span data-ttu-id="82e5f-115">설명</span><span class="sxs-lookup"><span data-stu-id="82e5f-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="82e5f-116">**이름**</span><span class="sxs-lookup"><span data-stu-id="82e5f-116">**Name**</span></span>|<span data-ttu-id="82e5f-117">**특성** 을 **순서 특성**내 특성의 멤버 이름을 기준으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-117">Sort **Attribute** by the member names of the attribute in **Ordering Attribute**.</span></span>|  
|<span data-ttu-id="82e5f-118">**Key**</span><span class="sxs-lookup"><span data-stu-id="82e5f-118">**Key**</span></span>|<span data-ttu-id="82e5f-119">**특성** 을 **순서 특성**내 특성의 멤버 키를 기준으로 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="82e5f-119">Sort **Attribute** by the member keys of the attribute in **Ordering Attribute**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82e5f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82e5f-120">See Also</span></span>  
 <span data-ttu-id="82e5f-121">[비즈니스 인텔리전스 마법사 F1 도움말](business-intelligence-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="82e5f-121">[Business Intelligence Wizard F1 Help](business-intelligence-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="82e5f-122">[큐브 디자이너 &#40;Analysis Services 다차원 데이터&#41;](cube-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="82e5f-122">[Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](cube-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="82e5f-123">차원 디자이너 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="82e5f-123">Dimension Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
