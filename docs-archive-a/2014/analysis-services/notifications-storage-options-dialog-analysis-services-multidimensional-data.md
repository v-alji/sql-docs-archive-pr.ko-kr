---
title: 알림 (저장소 옵션 대화 상자) (Analysis Services 다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.notifications.f1
ms.assetid: 5675cdbf-bfaa-4b6e-b716-31b8e9da72b4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 62e2a00c2b8dd5d2b0a5f3faae71f477de436e69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648642"
---
# <a name="notifications-storage-options-dialog-box-analysis-services---multidimensional-data"></a><span data-ttu-id="5bcd0-102">알림(스토리지 옵션 대화 상자)(Analysis Services - 다차원 데이터)</span><span class="sxs-lookup"><span data-stu-id="5bcd0-102">Notifications (Storage Options Dialog Box) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="5bcd0-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 **스토리지 옵션** 대화 상자의 **알림** 탭을 사용하여 차원, 큐브, 측정값 그룹 또는 파티션에 대한 알림 방법 및 관련 설정을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-103">Use the **Notifications** tab of the **Storage Options** dialog box in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to set the notification method and related settings for a dimension, cube, measure group, or partition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5bcd0-104">이러한 설정을 수정하려면 스토리지 모드와 자동 관리 캐싱 기능에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-104">You should be familiar with storage mode and proactive caching functionality before modifying these settings.</span></span> <span data-ttu-id="5bcd0-105">자세한 내용은 [자동 관리 캐싱&#40;파티션&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-105">For more information, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5bcd0-106">옵션</span><span class="sxs-lookup"><span data-stu-id="5bcd0-106">Options</span></span>  
  
|<span data-ttu-id="5bcd0-107">용어</span><span class="sxs-lookup"><span data-stu-id="5bcd0-107">Term</span></span>|<span data-ttu-id="5bcd0-108">정의</span><span class="sxs-lookup"><span data-stu-id="5bcd0-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="5bcd0-109">**스토리지 모드**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-109">**Storage mode**</span></span>|<span data-ttu-id="5bcd0-110">개체에 사용할 스토리지 모드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-110">Selects the storage mode to use for the object.</span></span><br /><br /> <span data-ttu-id="5bcd0-111">**MOLAP**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-111">**MOLAP**</span></span><br /> <span data-ttu-id="5bcd0-112">개체가 MOLAP(다차원 OLAP) 스토리지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-112">The object uses multidimensional OLAP (MOLAP) storage.</span></span><br /><br /> <span data-ttu-id="5bcd0-113">**HOLAP**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-113">**HOLAP**</span></span><br /> <span data-ttu-id="5bcd0-114">개체가 HOLAP(하이브리드 OLAP) 스토리지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-114">The object uses hybrid OLAP (HOLAP) storage.</span></span><br /><br /> <span data-ttu-id="5bcd0-115">**ROLAP**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-115">**ROLAP**</span></span><br /> <span data-ttu-id="5bcd0-116">개체가 ROLAP(관계형 OLAP) 스토리지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-116">The object uses relational OLAP (ROLAP) storage.</span></span>|  
|<span data-ttu-id="5bcd0-117">**자동 관리 캐싱을 설정합니다.**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-117">**Enable proactive caching**</span></span>|<span data-ttu-id="5bcd0-118">자동 관리 캐싱을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-118">Enables proactive caching.</span></span><br /><br /> <span data-ttu-id="5bcd0-119">참고: 이 옵션을 선택하지 않으면 **스토리지 모드**를 제외한 모든 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-119">Note: If this option is not selected, all options except **Storage mode** are disabled.</span></span>|  
|<span data-ttu-id="5bcd0-120">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-120">**SQL Server**</span></span>|<span data-ttu-id="5bcd0-121">에서 특수 추적 메커니즘을 사용 하 여 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 기본 테이블에 대 한 변경 내용을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-121">Uses a specialized trace mechanism on [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to identify changes to underlying tables for the object.</span></span>|  
|<span data-ttu-id="5bcd0-122">**추적 테이블 지정**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-122">**Specify tracking tables**</span></span>|<span data-ttu-id="5bcd0-123">개체에 대해 추적할 기본 테이블을 지정한 다음 세미콜론(;)으로 구분된 테이블 목록을 입력하거나 줄임표 단추(**...**)를 클릭하여 **관계형 개체** 대화 상자를 열고 추적할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-123">Specify the underlying tables to be tracked for the object, then type a list of tables delimited by semi-colon (;) characters or click the ellipsis button (**...**) to open the **Relational Objects** dialog box and choose the tables to be tracked.</span></span> <span data-ttu-id="5bcd0-124">자세한 내용은 [관계형 개체 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-124">For more information, see [Relational Objects Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="5bcd0-125">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 특정 요구 사항이 만족되면 개체에 대해 추적할 기본 테이블 목록 확인을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-125">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tries to determine the list of underlying tables to be tracked for the object, if certain requirements are met.</span></span> <span data-ttu-id="5bcd0-126">이러한 요구 사항에 대한 자세한 내용은 [자동 관리 캐싱&#40;파티션&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-126">For more information about these requirements, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>|  
|<span data-ttu-id="5bcd0-127">**클라이언트 시작**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-127">**Client initiated**</span></span>|<span data-ttu-id="5bcd0-128">XMLA(XML for Analysis) 명령 `NotifyTableChange`를 사용하여 개체에 대한 기본 테이블의 변경 내용을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-128">Select to use the XML for Analysis (XMLA) command, `NotifyTableChange`, to identify changes to underlying tables for the object.</span></span> <span data-ttu-id="5bcd0-129">일반적으로 이 옵션은 클라이언트 기반 알림 프로세스를 사용할 경우 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-129">This option is typically selected if you plan to use a client-based notification process.</span></span>|  
|<span data-ttu-id="5bcd0-130">**추적 테이블 지정**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-130">**Specify tracking tables**</span></span>|<span data-ttu-id="5bcd0-131">선택하여 개체에 대해 추적할 기본 테이블을 지정한 다음 세미콜론(;)으로 구분된 테이블 목록을 입력하거나 줄임표 단추(**...**)를 클릭하여 **관계형 개체** 대화 상자를 열고 추적할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-131">Select to specify the underlying tables to be tracked for the object, then type a list of tables delimited by semi-colon (;) characters or click the ellipsis button (**...**) to open the **Relational Objects** dialog box and choose the tables to be tracked.</span></span> <span data-ttu-id="5bcd0-132">자세한 내용은 [관계형 개체 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-132">For more information, see [Relational Objects Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](relational-objects-dialog-box-analysis-services-multidimensional-data.md).</span></span><br /><br /> <span data-ttu-id="5bcd0-133">이 옵션을 선택하지 않으면 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서는 특정 요구 사항이 만족되면 개체에 대해 추적할 기본 테이블 목록 확인을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-133">If this option is not selected, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] tries to determine the list of underlying tables to be tracked for the object, if certain requirements are met.</span></span> <span data-ttu-id="5bcd0-134">이러한 요구 사항에 대한 자세한 내용은 [자동 관리 캐싱&#40;파티션&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-134">For more information about these requirements, see [Proactive Caching &#40;Partitions&#41;](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).</span></span>|  
|<span data-ttu-id="5bcd0-135">**예약된 폴링**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-135">**Scheduled polling**</span></span>|<span data-ttu-id="5bcd0-136">폴링 메커니즘을 통해 개체에 대한 기본 테이블에 대해 일련의 쿼리를 실행하여 변경 내용을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-136">Uses a polling mechanism to identify changes by running a series of queries on the underlying tables for the object.</span></span>|  
|<span data-ttu-id="5bcd0-137">**폴링 간격**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-137">**Polling interval**</span></span>|<span data-ttu-id="5bcd0-138">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 가 폴링 표에 정의된 폴링 쿼리 및 처리 쿼리를 실행하기 전에 경과해야 하는 시간 간격 및 단위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-138">Specifies the interval and units of time for the period that should pass before [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] executes the polling queries and processing queries defined in the polling grid.</span></span>|  
|<span data-ttu-id="5bcd0-139">**증분 업데이트 설정**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-139">**Enable incremental updates**</span></span>|<span data-ttu-id="5bcd0-140">추가 데이터만 식별하도록 디자인된 폴링 및 처리 쿼리 집합에 기초하여 개체에 대한 MOLAP 캐시를 증분 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-140">Incrementally updates the MOLAP cache for an object based on a set of polling and processing queries designed to identify only additional data.</span></span> <span data-ttu-id="5bcd0-141">이 옵션을 선택하면 폴링 쿼리가 데이터 원본 뷰의 테이블 식별자와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-141">If this option is selected, the polling query is associated with a table identifier in the data source view.</span></span> <span data-ttu-id="5bcd0-142">그런 다음 처리 쿼리를 사용하여 폴링 쿼리의 현재 값을 이전에 실행한 폴링 쿼리의 저장된 값과 비교하여 변경 내용을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-142">The processing query is then used to compare the current value of the polling query with the stored value of the previously executed polling query to identify changes.</span></span><br /><br /> <span data-ttu-id="5bcd0-143">이 옵션을 선택하지 않으면 MOLAP 캐시가 전체 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-143">If this option is not selected, the MOLAP cache is fully updated.</span></span> <span data-ttu-id="5bcd0-144">폴링 쿼리를 사용하여 변경 내용 발생 여부를 식별합니다. 처리 쿼리 또는 테이블 식별자는 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-144">The polling query is used to identify that a change has occurred, and no processing query or table identifier is required.</span></span>|  
|<span data-ttu-id="5bcd0-145">**폴링 표**</span><span class="sxs-lookup"><span data-stu-id="5bcd0-145">**Polling grid**</span></span>|<span data-ttu-id="5bcd0-146">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 에서 데이터 원본을 폴링하고 개체에 대한 기본 테이블의 변경 내용을 식별하는 데 사용하는 폴링 쿼리, 처리 쿼리 및 테이블 식별자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-146">Contains the polling queries, processing queries, and table identifiers used by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] to poll the data source and identify changes to underlying tables for the object.</span></span> <span data-ttu-id="5bcd0-147">표에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-147">The grid contains the following columns:</span></span><br /><br /> <span data-ttu-id="5bcd0-148">**폴링 쿼리**: 폴링 간격으로 실행 되는 단일 쿼리를 입력 하 여 개체에 대 한 변경 내용을 식별 하거나, 줄임표 단추 (**...**)를 클릭 하 여 **폴링 쿼리 만들기** 대화 상자를 열고 단일 쿼리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-148">**Polling query**: Type the singleton query executed at the polling interval to identify changes for the object, or click the ellipsis button (**...**) to open the **Create Polling Query** dialog box and define the singleton query.</span></span> <span data-ttu-id="5bcd0-149">자세한 내용은 [폴링 쿼리 만들기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-149">For more information, see [Create Polling Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-polling-query-dialog-box-analysis-services-multidimensional-data.md).</span></span> <span data-ttu-id="5bcd0-150">**증분 업데이트 설정** 을 선택하면 폴링 쿼리가 **테이블**에서 식별된 테이블에 마지막으로 추가된 레코드를 식별하는 값을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-150">If **Enable incremental updates** is selected, the polling query should return a value that identifies the last record added to the table identified in **Table**.</span></span> <span data-ttu-id="5bcd0-151">**증분 업데이트 설정** 을 선택하지 않으면 폴링 쿼리가 테이블의 현재 레코드 수를 식별하는 값을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-151">If **Enable incremental updates** is not selected, the polling query should return a value that identifies the current number of records in the table.</span></span><br /><br /> <span data-ttu-id="5bcd0-152">**쿼리 처리**: 폴링 간격으로 실행 되는 쿼리를 입력 하 여 **테이블**에서 식별 된 테이블에서 새 레코드를 검색 하거나 줄임표 단추 (**...**)를 클릭 하 여 **처리 쿼리 만들기** 대화 상자를 열고 쿼리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-152">**Processing query**: Type the query executed at the polling interval to retrieve new records from the table identified in **Table**, or click the ellipsis button (**...**) to open the **Create Processing Query** dialog box and define the query.</span></span> <span data-ttu-id="5bcd0-153">자세한 내용은 [처리 쿼리 만들기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-153">For more information, see [Create Processing Query Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](create-processing-query-dialog-box-analysis-services-multidimensional-data.md).</span></span> <span data-ttu-id="5bcd0-154">쿼리는 폴링 기간 중에 추가 된 레코드만 식별 및 추출 하는 데 사용할 수 있는 두 개의 매개 변수 ( **폴링 쿼리의** 쿼리에서 반환 된 이전 값과 **폴링 쿼리**의 쿼리에 의해 반환 된 현재 값)를 허용 하도록 매개 변수화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-154">The query should be parameterized to accept two parameters-the previous value returned by the query in **Polling query** and the current value returned by the query in **Polling query**-that can be used to identify and extract only the records that have been added during the polling period.</span></span> <span data-ttu-id="5bcd0-155">이 옵션은 **증분 업데이트 설정** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-155">Note that this option is enabled only if **Enable incremental updates** is selected.</span></span><br /><br /> <span data-ttu-id="5bcd0-156">**테이블**: **폴링 쿼리의** 쿼리가 마지막 레코드를 추적 하는 테이블의 식별자를 입력 하거나 줄임표 단추 (**...**)를 클릭 하 여 **테이블 찾기** 대화 상자를 열고 테이블을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-156">**Table**: Type the identifier of the table against which the query in **Polling query** tracks the last record, or click the ellipsis button (**...**) to open the **Find Table** dialog box and select the table.</span></span> <span data-ttu-id="5bcd0-157">자세한 내용은 [테이블 찾기 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bcd0-157">For more information, see [Find Table Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](find-table-dialog-box-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bcd0-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5bcd0-158">See Also</span></span>  
 [<span data-ttu-id="5bcd0-159">저장소 옵션 대화 상자 &#40;Analysis Services 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="5bcd0-159">Storage Options Dialog Box &#40;Analysis Services - Multidimensional Data&#41;</span></span>](storage-options-dialog-box-analysis-services-multidimensional-data.md)  
  
  