---
title: 차원 특성 선택 (차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4961092517ce1d38cfd4086ec083a939242652d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648638"
---
# <a name="select-dimension-attributes-dimension-wizard"></a><span data-ttu-id="05f5d-102">차원 특성 선택(차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="05f5d-102">Select Dimension Attributes (Dimension Wizard)</span></span>
  <span data-ttu-id="05f5d-103">**차원 특성 선택** 페이지를 사용하여 차원에 대해 만들 특성을 선택하고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-103">Use the **Select Dimension Attributes** page to select and modify the attributes for the dimension to be created.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05f5d-104">열 값을 읽을 수 없으면 마법사 창을 최대화하고 값을 읽을 수 있을 때까지 각 열 머리글의 너비를 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="05f5d-104">If you cannot read the values for any column, maximize the wizard window and change the width of each column heading until you can read the values.</span></span>  
  
 <span data-ttu-id="05f5d-105">**차원 마법사를 열려면**</span><span class="sxs-lookup"><span data-stu-id="05f5d-105">**To open the Dimension Wizard**</span></span>  
  
-   <span data-ttu-id="05f5d-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 **솔루션 탐색기**에서 **프로젝트의** 차원 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 폴더를 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in **Solution Explorer**, right-click the **Dimensions** folder for an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and then click **New Dimension**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="05f5d-107">옵션</span><span class="sxs-lookup"><span data-stu-id="05f5d-107">Options</span></span>  
 <span data-ttu-id="05f5d-108">(확인란이 있는 열)</span><span class="sxs-lookup"><span data-stu-id="05f5d-108">(Column with check boxes)</span></span>  
 <span data-ttu-id="05f5d-109">차원에 특성을 포함시키려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-109">Select to include an attribute in the dimension.</span></span>  
  
 <span data-ttu-id="05f5d-110">특정 특성을 포함시키려면 해당 특성의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-110">To include a specific attribute, select the check box for that attribute.</span></span>  
  
 <span data-ttu-id="05f5d-111">모든 특성을 포함시키려면 열 머리글의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-111">To include all attributes, select the check box in the column header.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="05f5d-112">키 특성의 확인란은 선택 취소할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-112">The check box for the key attribute cannot be cleared.</span></span>  
  
 <span data-ttu-id="05f5d-113">**특성 이름**</span><span class="sxs-lookup"><span data-stu-id="05f5d-113">**Attribute Name**</span></span>  
 <span data-ttu-id="05f5d-114">사용 가능한 특성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-114">Lists the available attributes.</span></span>  
  
 <span data-ttu-id="05f5d-115">특성의 이름을 변경하려면 특성 이름을 클릭하고 특성의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-115">To change the name of an attribute, click the attribute name and type a new name for the attribute.</span></span>  
  
 <span data-ttu-id="05f5d-116">**찾아보기 사용**</span><span class="sxs-lookup"><span data-stu-id="05f5d-116">**Enable Browsing**</span></span>  
 <span data-ttu-id="05f5d-117">최종 사용자가 특성을 찾아보고 필터링할 수 있게 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-117">Select to make the attribute available to the end user for browsing and filtering.</span></span> <span data-ttu-id="05f5d-118">키 특성에 대해**찾아보기 사용** 을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-118">**Enable Browsing** must be selected for the key attribute.</span></span> <span data-ttu-id="05f5d-119">키가 아닌 특성의 경우에는 **찾아보기 사용** 이 기본적으로 선택되어 있지 않습니다. 따라서 키가 아닌 특성은 멤버 속성으로만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-119">For non-key attributes, the default is not to have **Enable Browsing** selected, which causes the non-key attributes to be shown only as member properties.</span></span>  
  
 <span data-ttu-id="05f5d-120">대부분의 경우 `AttributeHierarchyEnabled` 속성을 `True` 또는 `False`로 설정하여 특성을 찾아보기에 사용하거나 사용하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-120">In most cases, the attribute is made available or not available for browsing by setting the `AttributeHierarchyEnabled` property to `True` or `False`, respectively.</span></span> <span data-ttu-id="05f5d-121">그러나 다음 세 가지 사례에서 마법사는 다른 설정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-121">However, in the following three cases, the wizard uses different settings.</span></span>  
  
|<span data-ttu-id="05f5d-122">사례</span><span class="sxs-lookup"><span data-stu-id="05f5d-122">Case</span></span>|<span data-ttu-id="05f5d-123">설정</span><span class="sxs-lookup"><span data-stu-id="05f5d-123">Settings</span></span>|  
|----------|--------------|  
|<span data-ttu-id="05f5d-124">차원에 부모-자식 계층이 포함되고 **찾아보기 사용** 이 선택되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="05f5d-124">A dimension contains a parent-child hierarchy and **Enable Browsing** is not selected</span></span>|<span data-ttu-id="05f5d-125">마법사는 `AttributeHierarchyEnabled` 속성을 `True`로 두고, 키 특성에 대해 `AttributeHierarchyVisible` 특성을 `False`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-125">The wizard leaves the `AttributeHierarchyEnabled` property set to `True`, and sets the `AttributeHierarchyVisible` attribute to `False` for the key attribute.</span></span>|  
|<span data-ttu-id="05f5d-126">차원 내의 테이블에 차원에 없는 테이블에 대한 외래 키가 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="05f5d-126">A table in a dimension contains a foreign key to a table that is not in the dimension</span></span>|<span data-ttu-id="05f5d-127">마법사는 외래 키를 포함되는 특성으로 선택하지만 **찾아보기 사용**은 선택하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-127">The wizard selects the foreign key as an attribute to be included, but will not select **Enable Browsing**.</span></span> <span data-ttu-id="05f5d-128">이 설정을 유지하면 특성의 `AttributeHiearchyEnabled` 속성이 `True`로 설정되고 `AttributeHierarchyVisible` 속성이 `False`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-128">If you keep these settings, the `AttributeHiearchyEnabled` property of the attribute will be set to `True`, and the `AttributeHierarchyVisible` property will be set to `False`.</span></span>|  
|<span data-ttu-id="05f5d-129">null이 허용되는 외래 키 열을 통해 도달하는 눈송이 테이블이 차원에 포함된 경우</span><span class="sxs-lookup"><span data-stu-id="05f5d-129">A dimension contains snowflake tables that are reached through nullable foreign key columns</span></span><br /><br /> <span data-ttu-id="05f5d-130">및</span><span class="sxs-lookup"><span data-stu-id="05f5d-130">-and-</span></span><br /><br /> <span data-ttu-id="05f5d-131">눈송이 테이블의 키를 기반으로 한 특성에 대해 찾아보기 사용이 선택되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="05f5d-131">Enable Browsing for the attribute that is based on the key of the snowflake table is not selected</span></span>|<span data-ttu-id="05f5d-132">마법사는 `AttributeHiearchyEnabled` 속성이 `True`로 설정되고 `AttributeHierarchyVisible` 속성이 `False`로 설정된 새 특성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-132">The wizard will create the new attribute that has the `AttributeHiearchyEnabled` property set to `True`, and the `AttributeHierarchyVisible` property set to `False`.</span></span>|  
  
 <span data-ttu-id="05f5d-133">**특성 유형**</span><span class="sxs-lookup"><span data-stu-id="05f5d-133">**Attribute Type**</span></span>  
 <span data-ttu-id="05f5d-134">(옵션) 특성의 유형을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-134">(Optional) Set the type for the attribute.</span></span> <span data-ttu-id="05f5d-135">기본값은 **Regular**입니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-135">The default value is **Regular**.</span></span> <span data-ttu-id="05f5d-136">특성 유형은 특성에 포함할 정보에 대한 지침을 클라이언트 애플리케이션에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="05f5d-136">The attribute type provides guidance to client applications on what information the attribute might contain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f5d-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="05f5d-137">See Also</span></span>  
 <span data-ttu-id="05f5d-138">[차원 마법사 F1 도움말](dimension-wizard-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="05f5d-138">[Dimension Wizard F1 Help](dimension-wizard-f1-help.md) </span></span>  
 <span data-ttu-id="05f5d-139">[차원 &#40;Analysis Services 다차원 데이터&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="05f5d-139">[Dimensions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="05f5d-140">다차원 모델의 차원</span><span class="sxs-lookup"><span data-stu-id="05f5d-140">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
