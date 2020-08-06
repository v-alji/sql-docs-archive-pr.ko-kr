---
title: 캐시 새로 고침 옵션 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83b2ef4396c774f3ac344704756cd1c7e90d4e04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650809"
---
# <a name="cache-refresh-options-report-manager"></a><span data-ttu-id="34835-102">캐시 새로 고침 옵션(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="34835-102">Cache Refresh Options (Report Manager)</span></span>
  <span data-ttu-id="34835-103">캐시 새로 고침 옵션 페이지를 사용하여 보고서 또는 공유 데이터 세트의 임시 데이터 복사본과 함께 캐시를 사전 로드하는 일정을 계획할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-103">Use the Cache Refresh options page to create schedules for preloading the cache with temporary copies of data for a report or for a shared dataset.</span></span> <span data-ttu-id="34835-104">새로 고침 계획에는 일정 및 매개 변수 값을 지정하거나 재정의하는 옵션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="34835-104">A refresh plan includes a schedule and the option to specify or override values for parameters.</span></span> <span data-ttu-id="34835-105">공유 데이터 세트의 경우 읽기 전용으로 표시된 매개 변수의 값은 재정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-105">For a shared dataset, you cannot override values for parameters that are marked read-only.</span></span> <span data-ttu-id="34835-106">새로 고침 옵션 페이지에서는 새로 고침 계획을 여러 개 만들어 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-106">You can create and use more than one refresh plan as part of the refresh options page.</span></span>  
  
 <span data-ttu-id="34835-107">캐시 새로 고침 계획의 관련 보고서 및 공유 데이터 세트를 추가, 삭제, 변경 및 볼 수 있는 기본 역할 할당은 내용 관리자, 내 보고서 및 게시자입니다.</span><span class="sxs-lookup"><span data-stu-id="34835-107">Default role assignments that enable you to add, delete, change, and view related reports and shared datasets for cache refresh plans are Content Manager, My Reports, and Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="34835-108">이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-108">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="34835-109">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34835-109">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a><span data-ttu-id="34835-110">보고서 또는 공유 데이터 세트에 대한 캐시 새로 고침 계획 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="34835-110">To open the Cache Refresh Plan properties page for a report or shared dataset</span></span>  
  
1.  <span data-ttu-id="34835-111">보고서 관리자를 열고 캐시 새로 고침 속성을 구성할 보고서나 공유 데이터 세트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-111">Open Report Manager, and locate the report or shared dataset for which you want to configure cache refresh plan properties.</span></span>  
  
2.  <span data-ttu-id="34835-112">보고서 또는 공유 데이터 세트 위로 마우스를 이동하고 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-112">Hover over the report or shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="34835-113">드롭다운 목록에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-113">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="34835-114">**일반 속성** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="34835-114">The **General properties** page opens.</span></span>  
  
4.  <span data-ttu-id="34835-115">**캐시 새로 고침 계획** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-115">Click the **Cache Refresh Plan** tab.</span></span>  
  
5.  <span data-ttu-id="34835-116">캐시 계획을 새로 만들려면 **새 캐시 새로 고침 계획**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-116">To create a new cache plan, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="34835-117">SQL Server 에이전트 서비스를 사용하도록 설정하고 시작하여 캐시 새로 고침 계획을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-117">You must enable and start the SQL Server Agent service to create a cache refresh plan.</span></span>  
  
6.  <span data-ttu-id="34835-118">캐시 계획 복사본을 만들어 사용자 지정하려면 **기존 계획에서 새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-118">To create a copy of a cache plan and then customize it, click **New from Existing**.</span></span>  
  
## <a name="cache-refresh-options"></a><span data-ttu-id="34835-119">캐시 새로 고침 옵션</span><span class="sxs-lookup"><span data-stu-id="34835-119">Cache Refresh Options</span></span>  
 <span data-ttu-id="34835-120">**삭제**</span><span class="sxs-lookup"><span data-stu-id="34835-120">**Delete**</span></span>  
 <span data-ttu-id="34835-121">선택한 새로 고침 계획을 모두 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-121">Deletes all of the currently selected refresh plans.</span></span>  
  
 <span data-ttu-id="34835-122">**기존 계획에서 새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="34835-122">**New from existing**</span></span>  
 <span data-ttu-id="34835-123">이 옵션은 캐시 새로 고침 계획을 하나 선택한 경우에만 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="34835-123">This option is enabled when one and only one cache refresh plan is selected.</span></span> <span data-ttu-id="34835-124">이 옵션은 원래 계획에서 복사하여 새로운 새로 고침 옵션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34835-124">This option will create a new refresh plan which is copied from the original plan.</span></span> <span data-ttu-id="34835-125">캐시 새로 고침 계획 페이지의 정보가 선택한 계획의 정보로 채워져서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="34835-125">The cache refresh plan page opens pre-populated with details from the plan that was selected.</span></span> <span data-ttu-id="34835-126">그런 다음 새로 고침 계획 옵션을 수정하고 새로운 설명과 함께 계획을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-126">You can then modify the refresh plan options and save the plan with a new description.</span></span>  
  
 <span data-ttu-id="34835-127">**새 캐시 새로 고침 계획**</span><span class="sxs-lookup"><span data-stu-id="34835-127">**New cache refresh plan**</span></span>  
 <span data-ttu-id="34835-128">현재 캐시 새로 고침 옵션에서 사용할 새로 고침 계획을 새로 만들려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-128">Click to create a new refresh plan to be used in the current cache refresh options.</span></span>  
  
 <span data-ttu-id="34835-129">**편집**</span><span class="sxs-lookup"><span data-stu-id="34835-129">**Edit**</span></span>  
 <span data-ttu-id="34835-130">현재 새로 고침 계획을 편집하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-130">Select this option to edit the current refresh plan.</span></span>  
  
## <a name="cache-refresh-plan-options"></a><span data-ttu-id="34835-131">캐시 새로 고침 계획 옵션</span><span class="sxs-lookup"><span data-stu-id="34835-131">Cache Refresh Plan Options</span></span>  
 <span data-ttu-id="34835-132">**설명**</span><span class="sxs-lookup"><span data-stu-id="34835-132">**Description**</span></span>  
 <span data-ttu-id="34835-133">캐시 새로 고침 계획에 대한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-133">Specify a description for the cache refresh plan.</span></span>  
  
 <span data-ttu-id="34835-134">**항목별 일정**</span><span class="sxs-lookup"><span data-stu-id="34835-134">**Item-specific schedule**</span></span>  
 <span data-ttu-id="34835-135">이 항목 전용의 일정을 만들려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-135">Select this option to create a schedule that is used only by this item.</span></span>  
  
 <span data-ttu-id="34835-136">**구성**</span><span class="sxs-lookup"><span data-stu-id="34835-136">**Configure**</span></span>  
 <span data-ttu-id="34835-137">빈도 정보를 지정하는 데 사용되는 일정 페이지를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-137">Click to open the Schedule page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="34835-138">자세한 내용은 [새 일정: 일정 편집 페이지 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34835-138">For more information, see [New Schedule: Edit Schedule Page &#40;Report Manager&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="34835-139">**공유 일정**</span><span class="sxs-lookup"><span data-stu-id="34835-139">**Shared schedule**</span></span>  
 <span data-ttu-id="34835-140">기존 일정을 선택하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-140">Select this option to select an existing schedule.</span></span>  
  
 <span data-ttu-id="34835-141">자세한 내용은 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34835-141">For more information, see [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md).</span></span>  
  
 **@\<** *Parameter* **>**  
 <span data-ttu-id="34835-142">매개 변수 값의 한 조합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-142">Specify one combination of parameter values.</span></span> <span data-ttu-id="34835-143">이 섹션은 현재 데이터 세트나 보고서에 매개 변수가 있을 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="34835-143">This section appears only if the current dataset or report has parameters.</span></span>  
  
 <span data-ttu-id="34835-144">다음 섹션의 [매개 변수 지정](#Parameters) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="34835-144">See [Specifying Parameters](#Parameters) in the next section.</span></span>  
  
 <span data-ttu-id="34835-145">**기본값 사용**</span><span class="sxs-lookup"><span data-stu-id="34835-145">**Use Default**</span></span>  
 <span data-ttu-id="34835-146">이 매개 변수의 미리 정의된 기본값을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-146">Select this option to use the predefined default value for this parameter.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="34835-147">매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="34835-147">Specifying Parameters</span></span>  
 <span data-ttu-id="34835-148">캐시 새로 고침 계획을 만들려면 각 보고서나 공유 데이터 세트 매개 변수에 값이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-148">To create a cache refresh plan, each report or shared dataset parameter must have a value.</span></span> <span data-ttu-id="34835-149">보고서나 공유 데이터 세트 항목의 정의에 기본값이 없으면 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-149">If the report or shared dataset item does not have a default value specified in the definition, you must specify a value.</span></span> <span data-ttu-id="34835-150">기본값이 있으면 여기서 기본값을 제공할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-150">If a default value exists, you do not need to provide one here.</span></span> <span data-ttu-id="34835-151">값을 제공하면 제공한 값이 기본값을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-151">If you do provide a value, the value overrides the default value.</span></span>  
  
 <span data-ttu-id="34835-152">여러 개의 매개 변수 값 조합을 지정하려면 각 조합에 대해 별도의 캐시 새로 고침 계획을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="34835-152">To specify multiple combinations of parameter values, create a separate cache refresh plan for each combination.</span></span>  
  
 <span data-ttu-id="34835-153">보고서나 공유 데이터 세트의 매개 변수에 대해 수행한 추가, 변경, 삭제 내용을 캐시 새로 고침 계획에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-153">Additions, changes, and deletions made to parameters on a report or shared dataset can affect the cache refresh plan.</span></span> <span data-ttu-id="34835-154">보고서에 대해 기본값을 포함하는 매개 변수를 추가하거나, 매개 변수를 제거하거나, 공유 데이터 세트 매개 변수의 읽기 전용 옵션 또는 데이터 형식을 변경할 경우 이러한 변경 내용은 다음에 캐시 새로 고침 계획이 처리될 때 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="34835-154">If you add a parameter with a default value for a report, remove a parameter, or change the data type or the read-only option for a shared dataset parameter, the changes take affect the next time the cache refresh plan is processed.</span></span>  
  
### <a name="shared-dataset-parameters"></a><span data-ttu-id="34835-155">공유 데이터 세트 매개 변수</span><span class="sxs-lookup"><span data-stu-id="34835-155">Shared Dataset Parameters</span></span>  
 <span data-ttu-id="34835-156">공유 데이터 세트의 경우 다음 정보가 공유 데이터 세트 정의에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="34835-156">For a shared dataset, the following information is derived from the shared dataset definition:</span></span>  
  
-   <span data-ttu-id="34835-157">**이름** 쿼리 매개 변수의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-157">**Name** Specifies the name of the query parameter.</span></span>  
  
-   <span data-ttu-id="34835-158">**유형** 쿼리 매개 변수의 데이터 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-158">**Type** Specifies the data type of the query parameter.</span></span> <span data-ttu-id="34835-159">이 데이터 형식은 데이터 공급자가 데이터 세트 쿼리를 처리할 때까지 알 수 없기 때문에 데이터 형식 유효성 검사는 공유 데이터 세트가 처리될 때까지 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-159">Because this data type is unknown until the data provider processes the dataset query, data type validation cannot occur until the shared dataset is processed.</span></span>  
  
-   <span data-ttu-id="34835-160">**Null 허용** NULL을 유효한 값으로 간주할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-160">**Nullable** Specifies whether NULL is a valid value.</span></span>  
  
-   <span data-ttu-id="34835-161">**ReadOnly** 공유 데이터 세트 정의에서 이 매개 변수를 읽기 전용으로 표시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-161">**ReadOnly** Specifies whether this parameter is marked read-only in the shared dataset definition.</span></span> <span data-ttu-id="34835-162">읽기 전용 매개 변수는 캐시 새로 고침 옵션의 매개 변수 목록에 나타나지 않으며 공유 데이터 세트 정의에 기본값이 지정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-162">Read only parameters do not appear in the parameter list for cache refresh options and must have a default specified as part of the shared dataset definition.</span></span>  
  
-   <span data-ttu-id="34835-163">**DefaultValues** 공유 데이터 세트 정의에 지정된 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="34835-163">**DefaultValues** Default values that have been specified in the shared dataset definition.</span></span> <span data-ttu-id="34835-164">쿼리 매개 변수는 다중값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-164">Query parameters can be multivalued.</span></span> <span data-ttu-id="34835-165">기본값을 재정의하려면 입력란 프롬프트 영역에 새 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-165">To override the default values, type new values in the text box prompt areas.</span></span>  
  
 <span data-ttu-id="34835-166">공유 데이터 세트 정의에서 매개 변수에 대해 **쿼리에서 생략** 옵션을 지정할 경우 기본값을 제공할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-166">If the shared dataset definition specifies the option **Omit from query** for a parameter, you do not need to provide a default value.</span></span> <span data-ttu-id="34835-167">이 플래그는 해당 데이터 세트 매개 변수가 쿼리에 사용되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="34835-167">This flag indicates that the dataset parameter is not used in the query.</span></span> <span data-ttu-id="34835-168">예를 들어 이 매개 변수는 데이터 세트 필터에만 사용되는 보고서 매개 변수이기 때문에 공유 데이터 세트 정의에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="34835-168">For example, the parameter appears in the shared dataset definition because it is a report parameter that is used in the dataset filter only.</span></span>  
  
 <span data-ttu-id="34835-169">데이터 세트 매개 변수 옵션을 보거나 변경하려면 공유 데이터 세트 정의를 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-169">To view or change dataset parameter options, you must edit the shared dataset definition.</span></span> <span data-ttu-id="34835-170">자세한 내용은 [공유 데이터 세트 관리](report-data/manage-shared-datasets.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34835-170">For more information, see [Manage Shared Datasets](report-data/manage-shared-datasets.md).</span></span>  
  
### <a name="report-parameters"></a><span data-ttu-id="34835-171">보고서 매개 변수</span><span class="sxs-lookup"><span data-stu-id="34835-171">Report Parameters</span></span>  
 <span data-ttu-id="34835-172">보고서의 경우 캐시 새로 고침 계획을 만들려면 각 매개 변수 값이 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-172">For a report, each parameter value must be valid before you can successfully create a cache refresh plan.</span></span> <span data-ttu-id="34835-173">각 보고서 매개 변수에 대해 기본값을 입력하거나 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-173">You must type or select a default value for each report parameter.</span></span> <span data-ttu-id="34835-174">사용자가 설정한 값은 보고서 서버에서 보고서 매개 변수에 대해 정의된 기본값을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-174">The value that you set overrides the default value that is defined for the report parameter on the report server.</span></span>  
  
 <span data-ttu-id="34835-175">매개 변수는 보고서 서버의 매개 변수 속성에 지정된 요구 사항을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-175">Parameters must conform to the requirements specified in the parameter properties on the report server.</span></span> <span data-ttu-id="34835-176">예를 들어 보고서 매개 변수에 대해 AllowBlank 속성이 false 인 경우 빈 문자열은 유효한 값이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="34835-176">For example, if the property AllowBlank is false for a report parameter, an empty string is not a valid value.</span></span>  
  
 <span data-ttu-id="34835-177">보고서 매개 변수 옵션을 보거나 변경하려면 보고서의 보고서 매개 변수를 편집하거나 보고서 서버에서 개별적으로 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-177">To view or change report parameter options, you must edit the report parameters in the report, or independently, on the report server.</span></span> <span data-ttu-id="34835-178">자세한 내용은 [보고서 매개 변수 개념 &#40;보고서 작성기 및 SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34835-178">For more information, see [Report Parameters Concept &#40;Report Builder and SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md).</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a><span data-ttu-id="34835-179">캐시 새로 고침 계획이 비활성화되는 조건</span><span class="sxs-lookup"><span data-stu-id="34835-179">Conditions that Cause a Cache Refresh Plan to be Inactive</span></span>  
 <span data-ttu-id="34835-180">다음 조건에서는 공유 데이터 세트 또는 보고서 캐시 새로 고침 계획이 비활성화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-180">The following conditions can cause a shared dataset or report cache refresh plan to become inactive.</span></span>  
  
-   <span data-ttu-id="34835-181">공유 데이터 세트 캐시 또는 보고서 캐시 옵션이 사용되지 않도록 설정될 경우.</span><span class="sxs-lookup"><span data-stu-id="34835-181">The shared dataset cache or report cache option is disabled.</span></span>  
  
-   <span data-ttu-id="34835-182">필요한 매개 변수 값이 정의되지 않거나 유효하지 않거나 없을 경우.</span><span class="sxs-lookup"><span data-stu-id="34835-182">The required parameter values are not defined, not valid, or missing.</span></span> <span data-ttu-id="34835-183">보고서를 처리하려면 보고서의 모든 쿼리가 유효해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-183">All queries for a report must be valid before the report will be processed.</span></span> <span data-ttu-id="34835-184">포함된 포고서가 있는 보고서의 경우 하위 보고서의 데이터 세트를 포함하여 모든 데이터 세트 쿼리가 먼저 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="34835-184">For a report that has subreports, all dataset queries, including datasets for the subreport, are processed first.</span></span> <span data-ttu-id="34835-185">데이터 세트를 처리할 수 없을 경우 보고서를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34835-185">If any dataset cannot be successfully processed, the report cannot run.</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a><span data-ttu-id="34835-186">캐시 새로 고침 계획이 다시 활성화되는 조건</span><span class="sxs-lookup"><span data-stu-id="34835-186">Conditions that Cause a Cache Refresh Plan to be Reactivated</span></span>  
 <span data-ttu-id="34835-187">계획이 비활성화된 후 다음 중 하나를 수행하여 캐시 새로 고침 계획의 평가를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-187">After a plan is inactive, do one of the following to trigger evaluation of a cache refresh plan:</span></span>  
  
-   <span data-ttu-id="34835-188">계획의 옵션을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-188">Change an option for the plan.</span></span>  
  
-   <span data-ttu-id="34835-189">새로 고침 계획과 연결된 공유 데이터 세트나 보고서에 대해 캐싱을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-189">Enable caching for a shared dataset or report that is associated with the refresh plan.</span></span>  
  
-   <span data-ttu-id="34835-190">새로 고침 계획과 연결된 데이터 세트 쿼리 매개 변수의 읽기 전용 옵션을 선택하거나 선택을 취소한 다음, 새 정의를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="34835-190">Clear or select the read-only option for a dataset query parameter associated with the refresh plan, and then save the new definition to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34835-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34835-191">See Also</span></span>  
 <span data-ttu-id="34835-192">[항목 수준 태스크](security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="34835-192">[Item-Level Tasks](security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="34835-193">[보고서 관리자&#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="34835-193">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="34835-194">[F1 도움말 보고서 관리자](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="34835-194">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="34835-195">[보고서 캐시&#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="34835-195">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="34835-196">공유 데이터 세트 관리</span><span class="sxs-lookup"><span data-stu-id="34835-196">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
  
