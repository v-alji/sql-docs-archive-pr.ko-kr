---
title: 데이터 원본에 시간이 아닌 테이블을 생성 하 여 차원 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Analysis Services], dimensions without data source
- dimensions [Analysis Services], standard
- dimensions [Analysis Services], creating without data source
- standard dimensions [Analysis Services]
ms.assetid: a37f7a46-7451-4582-ba19-2595196d97bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49dbfb0c1fc15c1cbf703514e0fc693dfabf1e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737060"
---
# <a name="create-a-dimension-by-generating-a-non-time-table-in-the-data-source"></a><span data-ttu-id="6e631-102">데이터 원본에 시간이 아닌 테이블을 생성하여 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="6e631-102">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>
  <span data-ttu-id="6e631-103">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 차원 마법사를 사용 하 여 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 기존 데이터 원본을 사용 하지 않고 차원을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a dimension without using an existing data source.</span></span> <span data-ttu-id="6e631-104">이렇게 하려면 마법사의 **생성 방법 선택** 페이지에서 **데이터 원본에 시간이 아닌 테이블 생성** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-104">You do this by selecting the **Generate a non-time table in the data source** option of the **Select Creation Method** page of the wizard.</span></span> <span data-ttu-id="6e631-105">기본 데이터 원본에 새 차원 테이블을 만들려면 기본 데이터 원본에 개체를 만들 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-105">To create a new dimension table in the underlying data source, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="6e631-106">미리 정의된 데이터 원본 뷰 없이 차원을 정의하는 경우 완전히 새로 차원을 정의하거나 차원 템플릿을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-106">When defining a dimension without a predefined data source view, you can either define the dimension from scratch or use a dimension template.</span></span>  
  
 <span data-ttu-id="6e631-107">차원 마법사에서는 일반적인 차원 유형을 작성할 수 있는 예제 차원 템플릿을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-107">The Dimension Wizard provides sample dimension templates from which you can build a common dimension type.</span></span> <span data-ttu-id="6e631-108">다음 차원 유형 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-108">You can select from the following types of dimensions:</span></span>  
  
-   <span data-ttu-id="6e631-109">계정</span><span class="sxs-lookup"><span data-stu-id="6e631-109">Account</span></span>  
  
-   <span data-ttu-id="6e631-110">Customer</span><span class="sxs-lookup"><span data-stu-id="6e631-110">Customer</span></span>  
  
-   <span data-ttu-id="6e631-111">Date</span><span class="sxs-lookup"><span data-stu-id="6e631-111">Date</span></span>  
  
-   <span data-ttu-id="6e631-112">department</span><span class="sxs-lookup"><span data-stu-id="6e631-112">Department</span></span>  
  
-   <span data-ttu-id="6e631-113">Destination Currency</span><span class="sxs-lookup"><span data-stu-id="6e631-113">Destination Currency</span></span>  
  
-   <span data-ttu-id="6e631-114">직원</span><span class="sxs-lookup"><span data-stu-id="6e631-114">Employee</span></span>  
  
-   <span data-ttu-id="6e631-115">Geography</span><span class="sxs-lookup"><span data-stu-id="6e631-115">Geography</span></span>  
  
-   <span data-ttu-id="6e631-116">Internet Sales Order Details</span><span class="sxs-lookup"><span data-stu-id="6e631-116">Internet Sales Order Details</span></span>  
  
-   <span data-ttu-id="6e631-117">조직</span><span class="sxs-lookup"><span data-stu-id="6e631-117">Organization</span></span>  
  
-   <span data-ttu-id="6e631-118">제품</span><span class="sxs-lookup"><span data-stu-id="6e631-118">Product</span></span>  
  
-   <span data-ttu-id="6e631-119">홍보 행사</span><span class="sxs-lookup"><span data-stu-id="6e631-119">Promotion</span></span>  
  
-   <span data-ttu-id="6e631-120">Reseller Sales Order Details</span><span class="sxs-lookup"><span data-stu-id="6e631-120">Reseller Sales Order Details</span></span>  
  
-   <span data-ttu-id="6e631-121">Reseller</span><span class="sxs-lookup"><span data-stu-id="6e631-121">Reseller</span></span>  
  
-   <span data-ttu-id="6e631-122">Sales Channel</span><span class="sxs-lookup"><span data-stu-id="6e631-122">Sales Channel</span></span>  
  
-   <span data-ttu-id="6e631-123">Sales Reason</span><span class="sxs-lookup"><span data-stu-id="6e631-123">Sales Reason</span></span>  
  
-   <span data-ttu-id="6e631-124">Sales Summary Order Details</span><span class="sxs-lookup"><span data-stu-id="6e631-124">Sales Summary Order Details</span></span>  
  
-   <span data-ttu-id="6e631-125">Sales Territory</span><span class="sxs-lookup"><span data-stu-id="6e631-125">Sales Territory</span></span>  
  
-   <span data-ttu-id="6e631-126">시나리오</span><span class="sxs-lookup"><span data-stu-id="6e631-126">Scenario</span></span>  
  
-   <span data-ttu-id="6e631-127">Source Currency</span><span class="sxs-lookup"><span data-stu-id="6e631-127">Source Currency</span></span>  
  
 <span data-ttu-id="6e631-128">각 표준 템플릿에서 지원하는 특성을 선택하여 차원에 포함할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="6e631-128">Each of the standard templates supports attributes that you can choose to include in the dimension.</span></span> <span data-ttu-id="6e631-129">데이터에 자주 사용되는 차원에 대해 고유한 템플릿 파일을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-129">You can also add your own template files for dimensions that are commonly used with your data.</span></span> <span data-ttu-id="6e631-130">차원 템플릿은 다음 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-130">The dimension templates are located in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\100\Tools\Templates\olap\1033\Dimension Templates`  
  
 <span data-ttu-id="6e631-131">차원 마법사를 완료한 후에는 차원 디자이너를 사용하여 차원의 특성과 계층을 추가, 제거 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
 <span data-ttu-id="6e631-132">데이터 원본 없이 시간 차원 이외의 다른 차원을 만드는 경우 차원 마법사가 차원 유형을 지정하고 키 특성 및 느린 변경 차원을 식별하는 과정을 단계별로 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-132">When you are creating a non-time dimension without using a data source, the Dimension Wizard guides you through the steps of specifying the dimension type, and identifying the key attribute and slowly changing dimensions.</span></span>  
  
## <a name="specify-dimension-type"></a><span data-ttu-id="6e631-133">차원 유형 지정</span><span class="sxs-lookup"><span data-stu-id="6e631-133">Specify Dimension Type</span></span>  
 <span data-ttu-id="6e631-134">차원 마법사의 **차원 유형 지정** 페이지에서 차원 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-134">On the **Specify Dimension Type** page of the Dimension Wizard, you can specify the dimension type.</span></span> <span data-ttu-id="6e631-135">템플릿을 기반으로 차원을 작성하는 경우 차원 유형이 자동으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-135">If you are building the dimension based on a template, the dimension type is defined for you.</span></span> <span data-ttu-id="6e631-136">이 페이지에서는 지정된 차원 유형(사용 가능한 경우)의 표준 특성도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-136">On this page, you can also select standard attributes for the specified dimension type if any are available.</span></span>  
  
 <span data-ttu-id="6e631-137">차원 유형에 해당하는 템플릿을 선택한 경우 이 페이지가 해당 차원 유형의 옵션으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-137">If you selected a template that corresponds to a dimension type, this page is populated with the options for that dimension type.</span></span> <span data-ttu-id="6e631-138">템플릿을 선택하지 않았거나 해당하는 차원 유형이 없는 경우 기본 차원 유형은 **Regular**입니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-138">If you did not select a template, or if there is no corresponding dimension type, the default dimension type is **Regular**.</span></span> <span data-ttu-id="6e631-139">차원 유형을 선택하지 않은 경우 생성할 차원에 가장 적합한 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-139">If a dimension type is not already selected, select the most appropriate type for the dimension that you are creating.</span></span> <span data-ttu-id="6e631-140">**차원 유형**에 적절한 유형이 나열되지 않은 경우 **Regular**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-140">If no appropriate type is listed for **Dimension type**, use **Regular**.</span></span>  
  
 <span data-ttu-id="6e631-141">차원 유형을 선택하면 **차원 특성**아래에 해당 차원에 적용할 수 있는 특성 유형이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-141">When you select a dimension type, the wizard lists the attribute types that apply to this dimension under **Dimension attributes**.</span></span> <span data-ttu-id="6e631-142">특성 유형을 선택하려면 특성 유형 옆에 있는 **포함** 확인란을 선택하고 **차원 특성**아래에 특성 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-142">To select an attribute type, select the **Include** check box next to the attribute type, and type the name for the attribute under **Dimension Attribute**.</span></span> <span data-ttu-id="6e631-143">기본 이름은 **특성 유형**과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-143">The default name is the same as **Attribute Type**.</span></span>  
  
## <a name="identify-key-attribute-and-changing-dimensions"></a><span data-ttu-id="6e631-144">키 특성 및 변경 차원 식별</span><span class="sxs-lookup"><span data-stu-id="6e631-144">Identify Key Attribute and Changing Dimensions</span></span>  
 <span data-ttu-id="6e631-145">**차원 키 및 유형 지정** 페이지에서 차원의 키 특성으로 지정할 특성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-145">On the **Specify Dimension Key and Type** page, select the attribute that you want to be the key attribute for the dimension.</span></span> <span data-ttu-id="6e631-146">일반적으로 키 특성은 주 차원 테이블의 기본 키 열에 해당하며 대개 차원의 리프 멤버를 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-146">The key attribute typically corresponds to the primary key column in the main dimension table, and it typically indexes the leaf members of the dimension.</span></span>  
  
 <span data-ttu-id="6e631-147">템플릿을 선택했을 경우 템플릿에 키 특성이 정의되어 있으면 해당 특성이 기본 키 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-147">If you selected a template, and a key attribute is defined in the template, that attribute is the default key attribute.</span></span> <span data-ttu-id="6e631-148">템플릿을 선택했는데 템플릿에 키 특성이 정의되어 있지 않은 경우 목록의 첫 번째 특성이 기본값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-148">If you selected a template but no key attribute is defined in the template, the default is the first attribute in the list.</span></span> <span data-ttu-id="6e631-149">목록에는 **차원 유형 지정** 페이지에서 선택한 모든 특성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-149">The list contains all the attributes that you selected on the **Specify Dimension Type** page.</span></span> <span data-ttu-id="6e631-150">**차원 유형 지정** 페이지에서 키 특성으로 선택한 특성 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-150">You can select any one of the attributes that you selected on the **Specify Dimension Type** page to be the key attribute.</span></span> <span data-ttu-id="6e631-151">아무 특성도 선택하지 않은 경우에는 마법사에서 자동으로 키 특성을 만들고 차원 이름과 "ID"를 합쳐 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-151">If you did not select any attributes, the wizard automatically creates a key attribute and names it by concatenating the dimension name and "ID".</span></span>  
  
 <span data-ttu-id="6e631-152">마지막으로 차원이 변경 차원인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-152">Finally, specify whether this dimension is a changing dimension.</span></span> <span data-ttu-id="6e631-153">변경 차원의 멤버는 시간에 따라 계층 구조 내의 여러 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-153">Members in a changing dimension move over time to different locations in the hierarchy.</span></span> <span data-ttu-id="6e631-154">마법사에서 추가 열을 생성하고 해당 열에 대응하는 특성을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-154">The wizard generates additional columns and creates attributes that correspond to those columns.</span></span> <span data-ttu-id="6e631-155">사용자는 이러한 열을 사용하여 변경에서 팩토링하는 것과 같은 방식으로 차원을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-155">These columns will let users query the dimension in such a way as to factor in the change.</span></span> <span data-ttu-id="6e631-156">이후에 스키마 생성 마법사를 사용하여 만든 모든 패키지는 차원의 느린 변경 차원 특징에 기반하여 서로게이트 키를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-156">Any packages that you subsequently create with the Schema Generation Wizard manage surrogate keys based on slowly changing dimension characteristics of the dimension.</span></span>  
  
 <span data-ttu-id="6e631-157">**변경 차원임** 확인란을 선택한 경우 차원 마법사에서 다음 표에 표시된 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-157">When you select the **This is a changing dimension** check box, the Dimension Wizard defines the attributes indicated in the following table:</span></span>  
  
|<span data-ttu-id="6e631-158">attribute</span><span class="sxs-lookup"><span data-stu-id="6e631-158">Attribute</span></span>|<span data-ttu-id="6e631-159">Type</span><span class="sxs-lookup"><span data-stu-id="6e631-159">Type</span></span>|  
|---------------|----------|  
|<span data-ttu-id="6e631-160">SCD 원래 ID</span><span class="sxs-lookup"><span data-stu-id="6e631-160">SCD OriginalID</span></span>|<span data-ttu-id="6e631-161">SCDOriginalID</span><span class="sxs-lookup"><span data-stu-id="6e631-161">SCDOriginalID</span></span>|  
|<span data-ttu-id="6e631-162">SCD 종료 날짜</span><span class="sxs-lookup"><span data-stu-id="6e631-162">SCD End Date</span></span>|<span data-ttu-id="6e631-163">SCDEndDate</span><span class="sxs-lookup"><span data-stu-id="6e631-163">SCDEndDate</span></span>|  
|<span data-ttu-id="6e631-164">SCD 시작 날짜</span><span class="sxs-lookup"><span data-stu-id="6e631-164">SCD Start Date</span></span>|<span data-ttu-id="6e631-165">SCDStartDate</span><span class="sxs-lookup"><span data-stu-id="6e631-165">SCDStartDate</span></span>|  
|<span data-ttu-id="6e631-166">SCD 상태</span><span class="sxs-lookup"><span data-stu-id="6e631-166">SCD Status</span></span>|<span data-ttu-id="6e631-167">SCDStatus</span><span class="sxs-lookup"><span data-stu-id="6e631-167">SCDStatus</span></span>|  
  
 <span data-ttu-id="6e631-168">이러한 느린 변경 차원 특성이 정의되어 있는 템플릿을 사용할 경우 기본적으로 **변경 차원임** 확인란이 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-168">By default, the **This is a changing dimension** check box is selected if you use a template that has these slowly changing dimension attributes defined.</span></span> <span data-ttu-id="6e631-169">이 확인란의 선택을 취소하면 차원에서 느린 변경 차원 특성이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-169">If you clear the check box, the slowly changing dimension attributes are removed from the dimension.</span></span>  
  
 <span data-ttu-id="6e631-170">차원 디자이너를 사용하여 느린 변경 차원의 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-170">You can use Dimension Designer to configure properties for a slowly changing dimension.</span></span>  
  
## <a name="completing-the-dimension-wizard"></a><span data-ttu-id="6e631-171">차원 마법사 완료</span><span class="sxs-lookup"><span data-stu-id="6e631-171">Completing the Dimension Wizard</span></span>  
 <span data-ttu-id="6e631-172">**마법사 완료** 페이지에서 새 차원의 이름을 입력하고 차원 구조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-172">On the **Completing the Wizard** page, type a name for the new dimension and view the dimension structure.</span></span> <span data-ttu-id="6e631-173">**마침** 을 클릭한 후 스키마 생성 마법사를 시작하려면 **지금 스키마 생성**확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-173">Select the **Generate schema now** check box to start the Schema Generation Wizard after you click **Finish**.</span></span> <span data-ttu-id="6e631-174">대부분의 경우 추가 개체를 만들려면 이 확인란을 선택하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-174">In most cases, you should not select this check box if you plan to create additional objects.</span></span> <span data-ttu-id="6e631-175">이 확인란을 선택하지 않을 경우 나중에 차원 디자이너를 사용하여 스키마를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e631-175">If you do not select this check box, you can use Dimension Designer to generate the schema later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e631-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e631-176">See Also</span></span>  
 <span data-ttu-id="6e631-177">[시간 테이블을 생성 하 여 시간 차원 만들기](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="6e631-177">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 [<span data-ttu-id="6e631-178">시간 테이블을 생성하여 시간 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="6e631-178">Create a Time Dimension by Generating a Time Table</span></span>](create-a-time-dimension-by-generating-a-time-table.md)  
  
  
