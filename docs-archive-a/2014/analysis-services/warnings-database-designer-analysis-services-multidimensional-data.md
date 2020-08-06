---
title: 경고 (데이터베이스 디자이너) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: bf635460187fe56f4811de5090cada002ea8ca3b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649188"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="ffd8e-102">경고(데이터베이스 디자이너)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="ffd8e-102">Warnings (Database Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="ffd8e-103">**경고** 탭을 사용하여 규칙을 전역적으로 확인 및 해제하고 해제된 경고의 특정 인스턴스를 확인 및 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-103">Use the **Warnings** tab to view and dismiss rules globally, and to view and re-enable specific instances of dismissed warnings.</span></span> <span data-ttu-id="ffd8e-104">**경고** 탭에는 **디자인 경고 규칙** 과 **해제된 경고**라는 두 개의 표가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-104">The **Warnings** tab displays two grids: **Design Warning Rules** and **Dismissed Warnings**.</span></span>  
  
 <span data-ttu-id="ffd8e-105">**경고 탭을 표시하려면**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-105">**To display the Warnings tab**</span></span>  
  
1.  <span data-ttu-id="ffd8e-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="ffd8e-107">**솔루션 탐색기**에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트를 마우스 오른쪽 단추로 클릭하고 **데이터베이스 편집**을 클릭한 다음 **경고** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-107">In **Solution Explorer**, right-click the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, click **Edit Database**, and then click the **Warnings** tab.</span></span>  
  
## <a name="design-warning-rules-grid"></a><span data-ttu-id="ffd8e-108">디자인 경고 규칙 표</span><span class="sxs-lookup"><span data-stu-id="ffd8e-108">Design Warning Rules Grid</span></span>  
 <span data-ttu-id="ffd8e-109">**디자인 경고 규칙** 표에는 모든 디자인 경고 규칙이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-109">The **Design Warning Rules** grid displays all the design warning rules.</span></span> <span data-ttu-id="ffd8e-110">이 표는 데이터베이스에 대해 설정할 수 있는 규칙도 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-110">This grid also controls which rules are enabled for the database.</span></span> <span data-ttu-id="ffd8e-111">경고 규칙을 설정하거나 해제하려면 해당 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-111">To enable or disable a warning rule, select or clear its check box.</span></span>  
  
 <span data-ttu-id="ffd8e-112">**디자인 경고 규칙** 표에는 다음과 같은 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-112">The **Design Warning Rules** grid has the following columns:</span></span>  
  
 <span data-ttu-id="ffd8e-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-113">**Description**</span></span>  
 <span data-ttu-id="ffd8e-114">규칙의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-114">Displays the name of the rule.</span></span> <span data-ttu-id="ffd8e-115">규칙은 범주별로 그룹화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-115">Rules are grouped by category.</span></span>  
  
 <span data-ttu-id="ffd8e-116">**중요도**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-116">**Importance**</span></span>  
 <span data-ttu-id="ffd8e-117">규칙에 할당된 중요도를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-117">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="ffd8e-118">**설명**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-118">**Comments**</span></span>  
 <span data-ttu-id="ffd8e-119">(옵션) 사용자가 경고 해제 이유에 대한 설명을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-119">(Optional) Allows the user to type a comment that explains why you are dismissing the warning.</span></span>  
  
## <a name="dismissed-warnings-grid"></a><span data-ttu-id="ffd8e-120">해제된 경고 표</span><span class="sxs-lookup"><span data-stu-id="ffd8e-120">Dismissed Warnings Grid</span></span>  
 <span data-ttu-id="ffd8e-121">**해제된 경고** 표에는 **오류 목록**에서 해제된 특정 경고가 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-121">The **Dismissed Warnings** grid displays all specific warning occurrences that have been dismissed from the **Error List**.</span></span> <span data-ttu-id="ffd8e-122">경고를 다시 설정하려면 표에서 경고를 선택한 다음 **다시 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-122">To re-enable a warning, select it in the grid, and then click **Re-enable**.</span></span>  
  
 <span data-ttu-id="ffd8e-123">**해제된 경고** 표에는 다음과 같은 항목이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-123">The **Dismissed Warnings** grid has the following :</span></span>  
  
 <span data-ttu-id="ffd8e-124">**Object**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-124">**Object**</span></span>  
 <span data-ttu-id="ffd8e-125">개체 유형과 개체 이름을 나타내는 아이콘을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-125">Displays an icon that represents the object type and the object name.</span></span>  
  
 <span data-ttu-id="ffd8e-126">**형식**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-126">**Type**</span></span>  
 <span data-ttu-id="ffd8e-127">개체 유형을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-127">Displays the object type.</span></span>  
  
 <span data-ttu-id="ffd8e-128">**설명**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-128">**Description**</span></span>  
 <span data-ttu-id="ffd8e-129">규칙의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-129">Displays the name of the rule.</span></span>  
  
 <span data-ttu-id="ffd8e-130">**중요도**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-130">**Importance**</span></span>  
 <span data-ttu-id="ffd8e-131">규칙에 할당된 중요도를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-131">Displays the importance assigned to the rule.</span></span>  
  
 <span data-ttu-id="ffd8e-132">**설명**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-132">**Comments**</span></span>  
 <span data-ttu-id="ffd8e-133">경고를 해제할 때 입력한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-133">Displays the comment that was entered when the warning was dismissed.</span></span> <span data-ttu-id="ffd8e-134">여기에서 설명을 추가하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-134">You can add or modify a comment here.</span></span>  
  
 <span data-ttu-id="ffd8e-135">**다시 사용**</span><span class="sxs-lookup"><span data-stu-id="ffd8e-135">**Re-enable**</span></span>  
 <span data-ttu-id="ffd8e-136">선택한 경고를 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-136">Re-enables the selected warnings.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ffd8e-137">경고가 있는 개체의 경우 이 개체가 잘못된 상태이거나 프로젝트에서 수동으로 제거되면 목록에 있는 경고 옆에 오류 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-137">If an object has a warning, but the object is in an invalid state or was manually removed from the project, an error icon appears next to the warning in the list.</span></span> <span data-ttu-id="ffd8e-138">경고를 해제하려면 경고를 선택한 다음 **다시 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ffd8e-138">To dismiss the warning, select it and then click **Re-enable**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd8e-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ffd8e-139">See Also</span></span>  
 <span data-ttu-id="ffd8e-140">[경고 해제 대화 상자 &#40;Analysis Services 다차원 데이터&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="ffd8e-140">[Dismiss Warning Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="ffd8e-141">일반 &#40;데이터베이스 디자이너&#41; &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="ffd8e-141">General &#40;Database Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
