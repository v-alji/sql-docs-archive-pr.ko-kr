---
title: 차원 및 파티션에 대 한 문자열 저장소 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987f6cfc-da82-4b2e-96ef-a8af88339e5f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2817af382599d4495dddbd8951a72a47629cf824
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737107"
---
# <a name="configure-string-storage-for-dimensions-and-partitions"></a><span data-ttu-id="65451-102">차원 및 파티션에 대한 문자열 스토리지 구성</span><span class="sxs-lookup"><span data-stu-id="65451-102">Configure String Storage for Dimensions and Partitions</span></span>
  <span data-ttu-id="65451-103">문자열 스토리지에 대한 4GB 파일 크기 제한을 초과하는 차원 특성 또는 파티션의 매우 큰 문자열을 수용할 수 있도록 문자열 저장소를 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-103">You can reconfigure string storage to accommodate very large strings in dimension attributes or partitions that exceed the 4 GB file size limit for string stores.</span></span> <span data-ttu-id="65451-104">차원 또는 파티션이 이 크기의 문자열 저장소를 포함하는 경우, 연결된(로컬 또는 원격) 개체는 물론 로컬 개체에 대해 차원 또는 파티션 수준에서 **StringStoresCompatibilityLevel** 속성을 변경하여 파일 크기 제한을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-104">If your dimensions or partitions include string stores of this size, you can work around the file size constraint by changing the **StringStoresCompatibilityLevel** property at the dimension or partition level, for local as well as linked (local or remote) objects.</span></span>  
  
 <span data-ttu-id="65451-105">추가 용량을 필요로 하는 개체에 대해서만 문자열 스토리지를 늘릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-105">Note that you can increase string storage on just those objects that require additional capacity.</span></span> <span data-ttu-id="65451-106">대부분의 다차원 모델에서 문자열 데이터는 차원과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="65451-106">In most multidimensional models, string data is associated with dimensions.</span></span> <span data-ttu-id="65451-107">하지만 문자열의 맨 위에 고유 카운트 측정값이 들어 있는 파티션도 이 설정의 혜택을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-107">However, partitions that contain distinct count measures on top of strings can also benefit from this setting.</span></span> <span data-ttu-id="65451-108">이 설정은 문자열용이므로 숫자 데이터는 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-108">Because the setting is for strings, numeric data is unaffected.</span></span>  
  
 <span data-ttu-id="65451-109">이 속성에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-109">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="65451-110">값</span><span class="sxs-lookup"><span data-stu-id="65451-110">Value</span></span>|<span data-ttu-id="65451-111">설명</span><span class="sxs-lookup"><span data-stu-id="65451-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65451-112">**1050**</span><span class="sxs-lookup"><span data-stu-id="65451-112">**1050**</span></span>|<span data-ttu-id="65451-113">저장소당 최대 파일 크기가 4GB인 기본 문자열 스토리지 아키텍처를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-113">Specifies the default string storage architecture, subject to a 4 GB maximum file size per store.</span></span>|  
|<span data-ttu-id="65451-114">**1100**</span><span class="sxs-lookup"><span data-stu-id="65451-114">**1100**</span></span>|<span data-ttu-id="65451-115">저장소당 최대 40억 개의 고유 문자열을 지원하는 더 큰 문자열 스토리지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-115">Specifies larger string storage, supports up to 4 billion unique strings per store.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="65451-116">개체의 문자열 스토리지 설정을 변경하면 개체 자체 및 모든 종속 개체를 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-116">Changing the string storage settings of an object requires that you reprocess the object itself and any dependent object.</span></span> <span data-ttu-id="65451-117">이 절차를 완료하려면 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-117">Processing is required to complete the procedure.</span></span>  
  
 <span data-ttu-id="65451-118">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="65451-119">문자열 저장소 정보</span><span class="sxs-lookup"><span data-stu-id="65451-119">About String Stores</span></span>](#bkmk_background)  
  
-   [<span data-ttu-id="65451-120">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="65451-120">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="65451-121">1단계: SQL Server Data Tools에서 StringStoreCompatiblityLevel 속성 설정</span><span class="sxs-lookup"><span data-stu-id="65451-121">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>](#bkmk_step1)  
  
-   [<span data-ttu-id="65451-122">2단계: 개체 처리</span><span class="sxs-lookup"><span data-stu-id="65451-122">Step 2: Process the Objects</span></span>](#bkmk_step2)  
  
##  <a name="about-string-stores"></a><a name="bkmk_background"></a> <span data-ttu-id="65451-123">문자열 저장소 정보</span><span class="sxs-lookup"><span data-stu-id="65451-123">About String Stores</span></span>  
 <span data-ttu-id="65451-124">문자열 스토리지 구성은 선택 사항이므로 새 데이터베이스를 만들 때에도 최대 파일 크기가 4GB인 기본 문자열 저장소 아키텍처를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-124">String storage configuration is optional, which means that even new databases that you create use the default string store architecture that is subject to the 4 GB maximum file size.</span></span> <span data-ttu-id="65451-125">더 큰 문자열 스토리지 아키텍처를 사용하면 성능에 작지만 눈에 띄는 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65451-125">Using the larger string storage architecture has a small but noticeable impact on performance.</span></span> <span data-ttu-id="65451-126">따라서 문자열 스토리지 파일이 최대 4GB 제한에 근접했거나 도달한 경우에만 이 아키텍처를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-126">You should use it only if your string storage files are close to or at the maximum 4 GB limit.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="65451-127">이 설정은 데이터 마이닝 모델에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-127">This setting does not apply to data mining models.</span></span> <span data-ttu-id="65451-128">현재까지는 데이터 마이닝 구조를 포함하는 모델에서 GB 파일 크기 제한이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-128">Currently, it is still possible to encounter the GB file size limitation on models containing data mining structures.</span></span>  
  
 <span data-ttu-id="65451-129">Analysis Services 다차원 데이터베이스에서는 데이터의 특성에 따른 최적화를 허용하기 위해 문자열이 숫자 데이터와 별도로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="65451-129">In an Analysis Services multidimensional database, strings are stored separately from numeric data to allow for optimizations based on characteristics of the data.</span></span> <span data-ttu-id="65451-130">일반적으로 문자열 데이터는 이름이나 설명을 나타내는 차원 특성에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-130">String data is typically found in dimension attributes that represent names or descriptions.</span></span> <span data-ttu-id="65451-131">고유 카운트 측정값에도 문자열 데이터가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-131">It is also possible to have string data in distinct count measures.</span></span> <span data-ttu-id="65451-132">문자열 데이터는 키에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-132">String data can also be used in keys.</span></span>  
  
 <span data-ttu-id="65451-133">파일 확장명(예: .asstore, .bstore, .ksstore 또는 .string 파일)으로 문자열 저장소를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-133">You can identify a string store by its file extension (for example, asstore, .bstore, .ksstore, or .string files).</span></span> <span data-ttu-id="65451-134">기본적으로 이러한 각 파일에는 최대 4GB 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65451-134">By default, each of these files is subject to a maximum 4 GB limit.</span></span> <span data-ttu-id="65451-135">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에서는 필요에 따라 문자열 저장소가 커질 수 있도록 하는 대체 스토리지 메커니즘을 지정하여 최대 파일 크기를 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-135">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can override the maximum file size by specifying an alternative storage mechanism that allows a string store to grow as needed.</span></span>  
  
 <span data-ttu-id="65451-136">실제 파일의 크기를 제한하는 기본 문자열 스토리지 아키텍처와 달리, 더 큰 문자열 스토리지는 최대 문자열 수를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-136">In contrast with the default string storage architecture which limits the size of the physical file, larger string storage is based on a maximum number of strings.</span></span> <span data-ttu-id="65451-137">더 큰 문자열 스토리지의 최대 제한은 40억 개의 고유 문자열 또는 40억 개의 레코드 중 먼저 발생하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="65451-137">The maximum limit for larger string storage is 4 billion unique strings or 4 billion records, whichever occurs first.</span></span> <span data-ttu-id="65451-138">더 큰 문자열 스토리지는 짝수 크기의 레코드를 만들며 각 레코드는 64K페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="65451-138">Larger string storage creates records of an even size, where each record is equal to a 64K page.</span></span> <span data-ttu-id="65451-139">단일 레코드에 맞지 않는 매우 긴 문자열이 있는 경우 효과적인 제한은 40억 개의 문자열 미만입니다.</span><span class="sxs-lookup"><span data-stu-id="65451-139">If you have very long strings that do not fit in a single record, your effective limit will be less than 4 billion strings.</span></span>  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="65451-140">필수 조건</span><span class="sxs-lookup"><span data-stu-id="65451-140">Prerequisites</span></span>  
 <span data-ttu-id="65451-141">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 이상 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-141">You must have a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="65451-142">차원 및 파티션은 MOLAP 스토리지를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-142">Dimensions and partitions must use MOLAP storage.</span></span>  
  
 <span data-ttu-id="65451-143">데이터베이스 호환성 수준이 1100으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-143">The database compatibility level must be set to 1100.</span></span> <span data-ttu-id="65451-144">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 및 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 이상 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 사용하여 데이터베이스를 만들거나 배포하는 경우 데이터베이스 호환성 수준은 이미 1100으로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-144">If you created or deployed a database using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or later version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level is already set to 1100.</span></span> <span data-ttu-id="65451-145">이전 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 만든 데이터베이스를 ssSQL11 이상으로 이동한 경우 호환성 수준을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-145">If you moved a database created in an earlier version of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to ssSQL11 or later, you must update the compatibility level.</span></span> <span data-ttu-id="65451-146">이동은 하지만 다시 배포하지 않으려는 데이터베이스의 경우 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 호환성 수준을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65451-146">For databases that you are moving, but not redeploying, you can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to set the compatibility level.</span></span> <span data-ttu-id="65451-147">자세한 내용은 [다차원 데이터베이스의 호환성 수준 설정 &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="65451-147">For more information, see [Set the Compatibility Level of a Multidimensional Database &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).</span></span>  
  
##  <a name="step-1-set-the-stringstorecompatiblitylevel-property-in-sql-server-data-tools"></a><a name="bkmk_step1"></a><span data-ttu-id="65451-148">1 단계: SQL Server Data Tools에서 StringStoreCompatiblityLevel 속성 설정</span><span class="sxs-lookup"><span data-stu-id="65451-148">Step 1: Set the StringStoreCompatiblityLevel Property in SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="65451-149">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 수정할 차원 또는 파티션이 포함된 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65451-149">Using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the dimensions or partitions you want to modify.</span></span>  
  
2.  <span data-ttu-id="65451-150">차원에 대한 문자열 스토리지를 변경하려면 솔루션 탐색기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65451-150">To change the string storage for dimensions, open Solution Explorer.</span></span> <span data-ttu-id="65451-151">문자열 스토리지를 수정할 차원을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-151">Double-click the dimension for which you are modifying string storage.</span></span>  
  
3.  <span data-ttu-id="65451-152">차원 디자이너의 특성 창에서 차원의 부모 노드가 선택되어 있는지 확인합니다. 예를 들어, 차원이 Customers이면 자식 특성 중 하나가 아니라 Customers를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-152">In Dimension Designer, in the Attributes pane, make sure that the parent node of the dimension is selected (for example, if the dimension is Customers, select Customers and not one of the child attributes).</span></span>  
  
4.  <span data-ttu-id="65451-153">속성 창의 고급 섹션에서 **StringStoresCompatibilityLevel** 을 **1100**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-153">In the Properties pane, in the Advanced section, set **StringStoresCompatibilityLevel** to **1100**.</span></span> <span data-ttu-id="65451-154">더 큰 스토리지가 필요한 다른 차원에 대해 반복하거나 나머지 차원 값을 **1050** 으로 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="65451-154">Repeat for other dimensions that require larger storage, otherwise leave the remaining dimensions at the **1050** value.</span></span>  
  
5.  <span data-ttu-id="65451-155">솔루션 탐색기에서 파티션에 대한 큐브를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65451-155">For partitions, open a cube from Solution Explorer.</span></span>  
  
6.  <span data-ttu-id="65451-156">파티션 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-156">Click the Partitions tab.</span></span>  
  
7.  <span data-ttu-id="65451-157">파티션을 확장하고 추가 스토리지 용량이 필요한 파티션을 선택한 다음 **StringStoresCompatibilityLevel** 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-157">Expand the partition, select the partition that requires extra storage capacity, and then modify the **StringStoresCompatibilityLevel** property.</span></span>  
  
8.  <span data-ttu-id="65451-158">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-158">Save the file.</span></span>  
  
##  <a name="step-2-process-the-objects"></a><a name="bkmk_step2"></a><span data-ttu-id="65451-159">2 단계: 개체 처리</span><span class="sxs-lookup"><span data-stu-id="65451-159">Step 2: Process the Objects</span></span>  
 <span data-ttu-id="65451-160">새 스토리지 아키텍처는 개체를 처리한 후 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65451-160">The new storage architecture will be used after you process the objects.</span></span> <span data-ttu-id="65451-161">개체를 처리하면 이전에 문자열 저장소 오버플로 조건을 보고한 오류가 더 이상 발생하지 않으므로 스토리지 제한 문제를 성공적으로 해결한 것도 증명됩니다.</span><span class="sxs-lookup"><span data-stu-id="65451-161">Processing objects also proves you have successfully resolved storage constraint problem because the error that previously reported a string store overflow condition should no longer occur.</span></span>  
  
-   <span data-ttu-id="65451-162">솔루션 탐색기에서 수정한 차원을 마우스 오른쪽 단추로 클릭하고 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-162">In Solution Explorer, right-click the dimension or you just modified and select **Process**.</span></span>  
  
 <span data-ttu-id="65451-163">새 문자열 저장소 아키텍처를 사용하는 각 개체에 대해 전체 처리 옵션을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-163">You must use the Process Full option on each object that is using the new string store architecture.</span></span> <span data-ttu-id="65451-164">처리하기 전에 차원에 대한 영향 분석을 실행하여 종속 개체에도 재처리가 필요한지 여부를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65451-164">Before processing, be sure to run an impact analysis on the dimension to check whether dependent objects also require reprocessing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65451-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65451-165">See Also</span></span>  
 <span data-ttu-id="65451-166">[&#40;Analysis Services를 처리 하는 도구 및 접근 방식&#41;](tools-and-approaches-for-processing-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="65451-166">[Tools and Approaches for Processing &#40;Analysis Services&#41;](tools-and-approaches-for-processing-analysis-services.md) </span></span>  
 <span data-ttu-id="65451-167">[처리 옵션 및 설정 &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="65451-167">[Processing Options and Settings &#40;Analysis Services&#41;](processing-options-and-settings-analysis-services.md) </span></span>  
 <span data-ttu-id="65451-168">[파티션 저장소 모드 및 처리](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span><span class="sxs-lookup"><span data-stu-id="65451-168">[Partition Storage Modes and Processing](../multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md) </span></span>  
 [<span data-ttu-id="65451-169">차원 스토리지</span><span class="sxs-lookup"><span data-stu-id="65451-169">Dimension Storage</span></span>](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)  
  
  
