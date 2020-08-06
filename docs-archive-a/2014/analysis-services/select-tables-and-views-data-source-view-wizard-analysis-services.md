---
title: 테이블 및 뷰 선택 (데이터 원본 뷰 마법사) (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.datasourceviewwizard.selecttablesandviews.f1
ms.assetid: ea7d1232-f213-46e9-90d9-0fd616ca003d
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac7159255ef526d871ed8906fc873d9f16d2eb64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738884"
---
# <a name="select-tables-and-views-data-source-view-wizard-analysis-services"></a><span data-ttu-id="658c6-102">테이블 및 뷰 선택(데이터 원본 뷰 마법사)(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="658c6-102">Select Tables and Views (Data Source View Wizard) (Analysis Services)</span></span>
  <span data-ttu-id="658c6-103">**테이블 및 뷰 선택** 페이지를 사용하여 데이터 원본 뷰에 포함시킬 데이터 원본의 테이블 또는 뷰를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-103">Use the **Select Tables and Views** page to select the tables or views from the data source that you want to include in the data source view.</span></span>  
  
## <a name="options"></a><span data-ttu-id="658c6-104">옵션</span><span class="sxs-lookup"><span data-stu-id="658c6-104">Options</span></span>  
 <span data-ttu-id="658c6-105">**Available objects**</span><span class="sxs-lookup"><span data-stu-id="658c6-105">**Available objects**</span></span>  
 <span data-ttu-id="658c6-106">데이터 원본 스키마의 테이블 및 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-106">Lists the tables and views in the data source schema.</span></span> <span data-ttu-id="658c6-107">두 개 이상의 스키마가 나열되는 경우 모든 개체의 이름 앞에 스키마 이름이 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-107">The schema name prefixes the name of every object if more than one schema is listed.</span></span> <span data-ttu-id="658c6-108">스키마가 하나만 나열되는 경우 개체 이름 앞에 스키마의 이름이 붙지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-108">If only one schema is listed, the schema's name does not prefix the object names.</span></span>  
  
 <span data-ttu-id="658c6-109">목록을 오름차순이나 내림차순으로 다시 정렬하려면 **이름** 또는 **유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-109">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="658c6-110">**Included objects**</span><span class="sxs-lookup"><span data-stu-id="658c6-110">**Included objects**</span></span>  
 <span data-ttu-id="658c6-111">데이터 원본 뷰에 포함시킬 테이블 및 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-111">Lists the tables and views to include in the data source view.</span></span>  
  
 <span data-ttu-id="658c6-112">목록을 오름차순이나 내림차순으로 다시 정렬하려면 **이름** 또는 **유형**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-112">To reorder the list in ascending or descending order, click either **Name** or **Type**.</span></span>  
  
 <span data-ttu-id="658c6-113">**Filter**</span><span class="sxs-lookup"><span data-stu-id="658c6-113">**Filter**</span></span>  
 <span data-ttu-id="658c6-114">**사용 가능한 개체**에 나열된 개체를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-114">Filters the objects listed under **Available objects**.</span></span> <span data-ttu-id="658c6-115">문자열을 입력한 다음 **필터** 를 클릭하여 지정한 문자열이 포함된 이름만 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-115">Type a string, and then click **Filter** to list only the names that contain a specified string.</span></span> <span data-ttu-id="658c6-116">입력한 문자열과 정확히 일치하는 개체를 찾으려면 해당 문자열을 큰따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-116">To find an exact string of characters, enclose the string between double quotation marks.</span></span> <span data-ttu-id="658c6-117">필터는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-117">The filter is not case sensitive.</span></span>  
  
 <span data-ttu-id="658c6-118">아래 표에 나열된 와일드카드 문자는 필터 문자열의 어느 위치에나 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-118">You can include the wildcard characters listed in the following table anywhere in the filter string.</span></span>  
  
|<span data-ttu-id="658c6-119">와일드카드 문자</span><span class="sxs-lookup"><span data-stu-id="658c6-119">Wildcard character</span></span>|<span data-ttu-id="658c6-120">값</span><span class="sxs-lookup"><span data-stu-id="658c6-120">Value</span></span>|  
|------------------------|-----------|  
|**\***|<span data-ttu-id="658c6-121">임의의 문자열</span><span class="sxs-lookup"><span data-stu-id="658c6-121">Any string of characters</span></span>|  
|**%**|<span data-ttu-id="658c6-122">임의의 문자열</span><span class="sxs-lookup"><span data-stu-id="658c6-122">Any string of characters</span></span>|  
|<span data-ttu-id="658c6-123">**?**</span><span class="sxs-lookup"><span data-stu-id="658c6-123">**?**</span></span>|<span data-ttu-id="658c6-124">단일 문자</span><span class="sxs-lookup"><span data-stu-id="658c6-124">A single character</span></span>|  
|<span data-ttu-id="658c6-125">**"** *string* **"**</span><span class="sxs-lookup"><span data-stu-id="658c6-125">**"** *string* **"**</span></span>|<span data-ttu-id="658c6-126">리터럴 문자열.</span><span class="sxs-lookup"><span data-stu-id="658c6-126">A literal string of characters.</span></span> <span data-ttu-id="658c6-127">이 와일드카드 문자가 개체 이름의 부분 문자열과 일치하는 경우 모두 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-127">This wildcard character will match any substring within the object name.</span></span>|  
  
 <span data-ttu-id="658c6-128">**Show system objects**</span><span class="sxs-lookup"><span data-stu-id="658c6-128">**Show system objects**</span></span>  
 <span data-ttu-id="658c6-129">**사용 가능한 개체**에 시스템 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-129">Displays system objects under **Available objects**.</span></span> <span data-ttu-id="658c6-130">이 옵션은 데이터 원본 공급자가 시스템 개체를 표시하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-130">This option is available only if the data source provider exposes system objects.</span></span> <span data-ttu-id="658c6-131">**포함된 개체** 목록에서 시스템 개체를 제거하면 이 옵션이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-131">Removing a system object from the **Included objects** list automatically selects this option.</span></span>  
  
 <span data-ttu-id="658c6-132">**Add related tables**</span><span class="sxs-lookup"><span data-stu-id="658c6-132">**Add related tables**</span></span>  
 <span data-ttu-id="658c6-133">**포함된 개체**에 나열된 테이블과 관련된 모든 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-133">Adds all the tables that are related to those listed under **Included objects**.</span></span> <span data-ttu-id="658c6-134">이 옵션을 통해 뷰는 추가할 수 없지만</span><span class="sxs-lookup"><span data-stu-id="658c6-134">This option does not add views.</span></span> <span data-ttu-id="658c6-135">분할된 테이블은 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-135">However, this option does add partitioned tables.</span></span> <span data-ttu-id="658c6-136">마법사의 **이름 일치** 페이지에서 이름 일치 조건을 선택한 경우에는 선택한 조건에 따라 논리적으로 관련된 테이블도 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-136">If you select name-matching criteria on the **Name Matching** page of the wizard, this option also includes logically related tables according to the criteria you select.</span></span> <span data-ttu-id="658c6-137">새로 추가된 관련 테이블과 관련되어 있고 원래 테이블과 구조가 동일한 테이블도 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="658c6-137">Tables are also included if they are related to the newly added related tables, and if they have an identical structure to the original table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658c6-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="658c6-138">See Also</span></span>  
 <span data-ttu-id="658c6-139">[데이터 원본 뷰 마법사 F1 도움말 &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="658c6-139">[Data Source View Wizard F1 Help &#40;Analysis Services&#41;](data-source-view-wizard-f1-help-analysis-services.md) </span></span>  
 [<span data-ttu-id="658c6-140">다차원 모델의 데이터 원본 뷰</span><span class="sxs-lookup"><span data-stu-id="658c6-140">Data Source Views in Multidimensional Models</span></span>](multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
