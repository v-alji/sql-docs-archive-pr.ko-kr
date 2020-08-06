---
title: 차원에 대 한 순서 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8cd5ea148e374c18c530ba0a15c80dbb23983020
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648660"
---
# <a name="define-the-ordering-for-a-dimension"></a><span data-ttu-id="d5cd4-102">차원 순서 정의</span><span class="sxs-lookup"><span data-stu-id="d5cd4-102">Define the Ordering for a Dimension</span></span>
  <span data-ttu-id="d5cd4-103">큐브나 차원에 특성 순서 지정 기능을 추가하여 특성 멤버의 순서 지정 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-103">Add the attribute ordering enhancement to a cube or dimension to specify how the members of an attribute are ordered.</span></span> <span data-ttu-id="d5cd4-104">특성의 이름이나 키 또는 특성 관계를 기반으로 하는 다른 특성의 이름이나 키를 기준으로 멤버 순서를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-104">Members can be ordered by the name or the key of the attribute, or by the name or the key of another attribute (based on an attribute relationship).</span></span> <span data-ttu-id="d5cd4-105">기본적으로 멤버는 이름을 기준으로 순서가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-105">By default, members are ordered by the name.</span></span> <span data-ttu-id="d5cd4-106">이 기능은 차원의 특성에 대한 `OrderBy` 및 `OrderByAttributeID` 속성 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-106">This enhancement changes the `OrderBy` and `OrderByAttributeID` property settings for attributes in a dimension.</span></span>  
  
 <span data-ttu-id="d5cd4-107">특성 순서 지정 기능을 추가하려면 비즈니스 인텔리전스 마법사의 **기능 선택** 페이지에서 **특성 순서 지정** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-107">To add attribute ordering, you use the Business Intelligence Wizard, and select the **Specify attribute ordering** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="d5cd4-108">그런 다음 마법사의 안내를 따라 특성 순서 지정을 적용할 차원을 선택하고 선택한 차원에 대한 특성의 순서를 지정하는 방식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply attribute ordering and specifying how to order the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="d5cd4-109">차원 선택</span><span class="sxs-lookup"><span data-stu-id="d5cd4-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="d5cd4-110">마법사의 첫 번째 **특성 순서 지정** 페이지에서 특성 순서 지정을 적용할 차원을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-110">On the first **Specify Attribute Ordering** page of the wizard, you specify the dimension to which you want to apply attribute ordering.</span></span> <span data-ttu-id="d5cd4-111">선택한 차원에 특성 순서 지정 기능을 추가하면 차원이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-111">The attribute ordering enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="d5cd4-112">이러한 변경 내용은 선택된 차원을 포함하는 모든 큐브에 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="specifying-ordering"></a><span data-ttu-id="d5cd4-113">순서 지정</span><span class="sxs-lookup"><span data-stu-id="d5cd4-113">Specifying Ordering</span></span>  
 <span data-ttu-id="d5cd4-114">마법사의 두 번째 **특성 순서 지정** 페이지에서 차원에 있는 모든 특성의 순서를 지정하는 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-114">On the second **Specify Attribute Ordering** page of the wizard, you specify how all the attributes in the dimension will be ordered.</span></span>  
  
 <span data-ttu-id="d5cd4-115">**순서 특성** 열에서 순서 지정에 사용할 특성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-115">In the **Ordering Attribute** column, you can change the attribute used to do the ordering.</span></span> <span data-ttu-id="d5cd4-116">멤버를 정렬 하는 데 사용 하려는 특성이 목록에 없는 경우 목록을 아래로 스크롤하여 선택한 다음 **\<New attribute...>** **열** 선택 대화 상자를 열어 차원 테이블의 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-116">If the attribute that you want to use to order members is not in the list, scroll down the list, and then select **\<New attribute...>** to open the **Select a Column** dialog box, where you can select a column in a dimension table.</span></span> <span data-ttu-id="d5cd4-117">**열 선택** 대화 상자에서 열을 선택하면 특성의 멤버 순서를 지정하는 추가 특성이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-117">Selecting a column by using the **Select a Column** dialog box creates an additional attribute with which to order members of an attribute.</span></span>  
  
 <span data-ttu-id="d5cd4-118">그런 다음 **조건** 열에서 **키** 또는 **이름**을 중에서 어떤 기준으로 특성 멤버의 순서를 지정할 것인지 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d5cd4-118">In the **Criteria** column, you can then select whether to order the members of the attribute by either **Key** or **Name**.</span></span>  
  
  
