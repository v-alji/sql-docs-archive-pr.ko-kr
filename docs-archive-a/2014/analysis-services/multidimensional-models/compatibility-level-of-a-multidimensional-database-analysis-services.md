---
title: 다차원 데이터베이스의 호환성 수준 설정 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 978279e6-a581-4184-af9d-8701b9826a89
author: minewiskan
ms.author: owend
ms.openlocfilehash: eea3d522abc5133e759cf476f3b169fd570b196f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737120"
---
# <a name="set-the-compatibility-level-of-a-multidimensional-database-analysis-services"></a><span data-ttu-id="bd617-102">다차원 데이터베이스의 호환성 수준 설정(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="bd617-102">Set the Compatibility Level of a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="bd617-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 데이터베이스 호환성 수준 속성은 데이터베이스의 기능 수준을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the database compatibility level property determines the functional level of a database.</span></span> <span data-ttu-id="bd617-104">호환성 수준은 각 모델 유형에 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-104">Compatibility levels are unique to each model type.</span></span> <span data-ttu-id="bd617-105">예를 들어의 호환성 수준은 `1100` 데이터베이스가 다차원 인지 또는 테이블 형식 인지에 따라 의미가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-105">For example, a compatibility level of `1100` has a different meaning depending on whether the database is multidimensional or tabular.</span></span>  
  
 <span data-ttu-id="bd617-106">이 항목에서는 다차원 데이터베이스의 호환성 수준에 대해서만 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-106">This topic describes compatibility level for multidimensional databases only.</span></span> <span data-ttu-id="bd617-107">테이블 형식 솔루션에 대 한 자세한 내용은 [호환성 수준 &#40;SSAS 테이블 형식 SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd617-107">For more information about tabular solutions, see [Compatibility Level &#40;SSAS Tabular SP1&#41;](../tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd617-108">테이블 형식 모델은 다차원 모델에 적용되지 않는 추가 데이터베이스 호환성 수준이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-108">Tabular models have additional database compatibility levels that are not applicable to multidimensional models.</span></span> <span data-ttu-id="bd617-109">호환성 수준 `1103`은 다차원 모델에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-109">Compatibility level `1103` does not exist for multidimensional models.</span></span> <span data-ttu-id="bd617-110">테이블 형식 솔루션에 대 한 자세한 내용은 [SQL Server 2012 SP1 및 호환성 수준에서 테이블 형식 모델의 새로운 기능](https://go.microsoft.com/fwlink/?LinkId=301727) 을 참조 하세요 `1103` .</span><span class="sxs-lookup"><span data-stu-id="bd617-110">See [What is new for the Tabular model in SQL Server 2012 SP1 and compatibility level](https://go.microsoft.com/fwlink/?LinkId=301727) for more information about `1103` for tabular solutions.</span></span>  
  
 <span data-ttu-id="bd617-111">**다차원 데이터베이스의 호환성 수준**</span><span class="sxs-lookup"><span data-stu-id="bd617-111">**Compatibility Levels for multidimensional databases**</span></span>  
  
 <span data-ttu-id="bd617-112">현재 기능 수준에 따라 달라지는 다차원 데이터베이스 동작은 문자열 스토리지 아키텍처뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-112">Currently, the only multidimensional database behavior that varies by functional level is string storage architecture.</span></span> <span data-ttu-id="bd617-113">데이터베이스 호환성 수준을 높여 측정값 및 차원의 문자열 스토리지에 대한 4GB 최대 제한을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-113">By raising the database compatibility level, you can override the 4 gigabyte maximum limit for string storage of measures and dimensions.</span></span>  
  
 <span data-ttu-id="bd617-114">다차원 데이터베이스에 대해 유효한 `CompatibilityLevel` 속성 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-114">For a multidimensional database, valid values for the `CompatibilityLevel` property include the following:</span></span>  
  
|<span data-ttu-id="bd617-115">설정</span><span class="sxs-lookup"><span data-stu-id="bd617-115">Setting</span></span>|<span data-ttu-id="bd617-116">설명</span><span class="sxs-lookup"><span data-stu-id="bd617-116">Description</span></span>|  
|-------------|-----------------|  
|`1050`|<span data-ttu-id="bd617-117">이 값은 스크립트나 도구에 표시되지 않지만 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]또는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서 만든 데이터베이스에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-117">This value is not visible in script or tools, but it corresponds to databases created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span> <span data-ttu-id="bd617-118">`CompatibilityLevel`이 명시적으로 설정되지 않은 모든 데이터베이스는 `1050` 수준에서 암시적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-118">Any database that does not have `CompatibilityLevel` explicitly set is implicitly running at the `1050` level.</span></span>|  
|`1100`|<span data-ttu-id="bd617-119">이 값은 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 또는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 만드는 새 데이터베이스의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-119">This is the default value for new databases that you create in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="bd617-120">이 호환성 수준에서만 지원되는 기능(즉, 차원 특성의 증가된 문자열 스토리지 또는 문자열 데이터가 포함된 고유 카운트 측정값)을 사용할 수 있도록 이전 버전의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 만든 데이터베이스에 대해 이 값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-120">You can also specify it for databases created in earlier versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to enable the use of features that are supported only at this compatibility level (namely, increased string storage for dimension attributes or distinct count measures that contain string data).</span></span><br /><br /> <span data-ttu-id="bd617-121">가 `CompatibilityLevel` 추가 속성을 가져오도록 설정 된 데이터베이스는 `1100` `StringStoresCompatibilityLevel` 파티션 및 차원에 대 한 대체 문자열 저장소를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-121">Databases that have a `CompatibilityLevel` set to `1100` get an additional property, `StringStoresCompatibilityLevel`, that lets you choose alternative string storage for partitions and dimensions.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="bd617-122">데이터베이스 호환성 수준을 더 높여서 설정하는 경우 되돌릴 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-122">Setting the database compatibility to a higher level is irreversible.</span></span> <span data-ttu-id="bd617-123">호환성 수준을로 높인 후에 `1100` 는 계속 해 서 새 서버에서 데이터베이스를 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-123">After you increase the compatibility level to `1100`, you must continue to run the database on newer servers.</span></span> <span data-ttu-id="bd617-124">로 롤백할 수 없습니다 `1050` .</span><span class="sxs-lookup"><span data-stu-id="bd617-124">You cannot rollback to `1050`.</span></span> <span data-ttu-id="bd617-125">또는 보다 이전 버전인 서버 버전에서는 데이터베이스를 연결 하거나 복원할 수 없습니다 `1100` [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bd617-125">You cannot attach or restore an `1100` database on a server version that is earlier than [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bd617-126">필수 조건</span><span class="sxs-lookup"><span data-stu-id="bd617-126">Prerequisites</span></span>  
 <span data-ttu-id="bd617-127">데이터베이스 호환성 수준은 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-127">Database compatibility levels are introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span> <span data-ttu-id="bd617-128">데이터베이스 호환성 수준을 보거나 설정하려면 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 이상이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-128">You must have [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher to view or set the database compatibility level.</span></span>  
  
 <span data-ttu-id="bd617-129">데이터베이스는 로컬 큐브일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-129">The database cannot be a local cube.</span></span> <span data-ttu-id="bd617-130">로컬 큐브는 `CompatibilityLevel` 속성을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-130">Local cubes do not support the `CompatibilityLevel` property.</span></span>  
  
 <span data-ttu-id="bd617-131">데이터베이스가 이전 릴리스(SQL Server 2008 R2 이하)에서 만들어진 다음 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 이상인 서버로 연결되거나 복원되었어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-131">The database must have been created in a previous release (SQL Server 2008 R2 or earlier) and then attached or restored to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or higher server.</span></span> <span data-ttu-id="bd617-132">SQL Server 2012에 배포된 데이터베이스는 이미 `1100`이며 다운그레이드하여 하위 수준에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-132">Databases deployed to SQL Server 2012 are already at `1100` and cannot be downgraded to run at a lower level.</span></span>  
  
## <a name="determine-the-existing-database-compatibility-level-for-a-multidimensional-database"></a><span data-ttu-id="bd617-133">다차원 데이터베이스에 대한 기존 데이터베이스 호환성 수준을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-133">Determine the existing database compatibility level for a multidimensional database</span></span>  
 <span data-ttu-id="bd617-134">데이터베이스 호환성 수준은 XMLA를 통해서만 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-134">The only way to view or modify the database compatibility level is through XMLA.</span></span> <span data-ttu-id="bd617-135">SQL Server Management Studio에서 데이터베이스를 지정하는 XMLA 스크립트를 보거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-135">You can view or modify the XMLA script that specifies your database in SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="bd617-136">`CompatibilityLevel` 속성에 대한 데이터베이스의 XMLA 정의를 검색했지만 그 결과가 없는 경우 `1050` 수준의 데이터베이스가 있을 가능성이 가장 높습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-136">If you search the XMLA definition of a database for the property `CompatibilityLevel` and it does not exist, you most likely have a database at the `1050` level.</span></span>  
  
 <span data-ttu-id="bd617-137">XMLA 스크립트 보기 및 수정에 대한 지침은 다음 섹션에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-137">Instructions for viewing and modifying the XMLA script are provided in the next section.</span></span>  
  
## <a name="set-the-database-compatibility-level-in-sql-server-management-studio"></a><span data-ttu-id="bd617-138">SQL Server Management Studio에서 데이터베이스 호환성 수준 설정</span><span class="sxs-lookup"><span data-stu-id="bd617-138">Set the database compatibility level in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="bd617-139">나중에 변경 내용을 되돌릴 경우에 대비하여 호환성 수준을 올리기 전에 데이터베이스를 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-139">Before raising the compatibility level, backup the database in case you want to reverse your changes later.</span></span>  
  
2.  <span data-ttu-id="bd617-140">SQL Server Management Studio를 사용하여 데이터베이스를 호스팅하는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-140">Using SQL Server Management Studio, connect to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server that hosts the database.</span></span>  
  
3.  <span data-ttu-id="bd617-141">데이터베이스 이름을 마우스 오른쪽 단추로 클릭하고 **데이터베이스 스크립팅**, **ALTER**를 차례로 가리킨 다음 **새 쿼리 편집기 창**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-141">Right-click the database name, point to **Script Database as**, point to **ALTER to**, and then select **New Query Editor Window**.</span></span> <span data-ttu-id="bd617-142">데이터베이스의 XMLA 표현이 새 창에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-142">An XMLA representation of the database will open in a new window.</span></span>  
  
4.  <span data-ttu-id="bd617-143">다음 XML 요소를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-143">Copy the following XML element:</span></span>  
  
    ```  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    ```  
  
5.  <span data-ttu-id="bd617-144">`</Annotations>` 닫는 요소 뒤와 `<Language>` 요소 앞에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-144">Paste it after the `</Annotations>` closing element and before the `<Language>` element.</span></span> <span data-ttu-id="bd617-145">XML은 다음 예와 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-145">The XML should look similar to the following example:</span></span>  
  
    ```  
    </Annotations>  
    <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
    <Language>1033</Language>  
    ```  
  
6.  <span data-ttu-id="bd617-146">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-146">Save the file.</span></span>  
  
7.  <span data-ttu-id="bd617-147">스크립트를 실행하려면 쿼리 메뉴에서 **실행** 을 클릭하거나 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-147">To run the script, click **Execute** on the Query menu or press F5.</span></span>  
  
## <a name="supported-operations-that-require-the-same-compatibility-level"></a><span data-ttu-id="bd617-148">지원되는 작업 중 호환성 수준이 같아야 하는 작업</span><span class="sxs-lookup"><span data-stu-id="bd617-148">Supported Operations that Require the Same Compatibility Level</span></span>  
 <span data-ttu-id="bd617-149">다음 작업의 경우 원본 데이터베이스의 호환성 수준이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-149">The following operations require that the source databases share the same compatibility level.</span></span>  
  
1.  <span data-ttu-id="bd617-150">다른 데이터베이스에서 파티션을 병합하는 경우 두 데이터베이스의 호환성 수준이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-150">Merging partitions from different databases is supported only if both databases share the same compatibility level.</span></span>  
  
2.  <span data-ttu-id="bd617-151">다른 데이터베이스의 연결된 차원을 사용하려면 호환성 수준이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-151">Using linked dimensions from another database requires the same compatibility level.</span></span> <span data-ttu-id="bd617-152">예를 들어 데이터베이스의 데이터베이스에서 연결 된 차원을 사용 하려면 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 데이터베이스를 서버로 이식 하 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 고 호환성 수준을로 설정 해야 합니다 `1100` .</span><span class="sxs-lookup"><span data-stu-id="bd617-152">For example, if you want to use a linked dimension from a [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database in a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database, you must port the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] database to a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] server and set the compatibility level to `1100`.</span></span>  
  
3.  <span data-ttu-id="bd617-153">서버 동기화는 동일한 버전과 데이터베이스 호환성 수준을 공유하는 서버에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-153">Synchronizing servers is only supported for servers that share the same version and database compatibility level.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="bd617-154">다음 단계</span><span class="sxs-lookup"><span data-stu-id="bd617-154">Next Steps</span></span>  
 <span data-ttu-id="bd617-155">데이터베이스 호환성 수준을 높인 후 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 `StringStoresCompatibilityLevel` 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-155">After you increase the database compatibility level, you can set the `StringStoresCompatibilityLevel` property in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="bd617-156">그러면 측정값 및 차원에 대한 문자열 스토리지가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="bd617-156">This increases string storage for measures and dimensions.</span></span> <span data-ttu-id="bd617-157">이 기능에 대한 자세한 내용은 [차원 및 파티션에 대한 문자열 스토리지 구성](configure-string-storage-for-dimensions-and-partitions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd617-157">For more information about this feature, see [Configure String Storage for Dimensions and Partitions](configure-string-storage-for-dimensions-and-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd617-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bd617-158">See Also</span></span>  
 [<span data-ttu-id="bd617-159">데이터베이스 백업, 복원 및 동기화&#40;XMLA&#41;</span><span class="sxs-lookup"><span data-stu-id="bd617-159">Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;</span></span>](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
