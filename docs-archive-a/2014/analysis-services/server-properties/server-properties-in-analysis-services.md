---
title: Analysis Services에서 서버 속성 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
ms.openlocfilehash: 087154756960c6d53fbd66ca4c111ac157503a53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650298"
---
# <a name="configure-server-properties-in-analysis-services"></a><span data-ttu-id="0a963-102">Analysis Services에서 서버 속성 구성</span><span class="sxs-lookup"><span data-stu-id="0a963-102">Configure Server Properties in Analysis Services</span></span>
  <span data-ttu-id="0a963-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 기본 서버 구성 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-103">An [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator can modify default server configuration properties for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="0a963-104">각 인스턴스에는 동일한 서버의 다른 인스턴스와 독립적으로 설정할 수 있는 자체 구성 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-104">Each instance has its own configuration properties that can be set independently of other instances on the same server.</span></span>  
  
 <span data-ttu-id="0a963-105">서버 속성을 설정하려면 SQL Server Management Studio를 사용하거나 특정 인스턴스의 msmdsrv.ini 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-105">To set server properties, use SQL Server Management Studio or edit the msmdsrv.ini file of a specific instance.</span></span>  
  
 <span data-ttu-id="0a963-106">이 항목에는 다음과 같은 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-106">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="0a963-107">서버(인스턴스) 속성 구성</span><span class="sxs-lookup"><span data-stu-id="0a963-107">Configure Server (Instance) Properties</span></span>](#bkmk_config)  
  
 [<span data-ttu-id="0a963-108">서버 속성 참조</span><span class="sxs-lookup"><span data-stu-id="0a963-108">Server Property Reference</span></span>](#bkmk_ref)  
  
##  <a name="configure-server-instance-properties"></a><a name="bkmk_config"></a><span data-ttu-id="0a963-109">서버 (인스턴스) 속성 구성</span><span class="sxs-lookup"><span data-stu-id="0a963-109">Configure Server (Instance) Properties</span></span>  
 <span data-ttu-id="0a963-110">SQL Server Management Studio의 속성 페이지에는 사용 가능한 속성의 하위 집합이 포함되어 있으며 수정할 가능성이 높은 속성만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-110">The property pages in SQL Server Management Studio contain a subset of the available properties, showing only those properties that are more likely to be modified.</span></span> <span data-ttu-id="0a963-111">전체 속성 집합은 msmdsrv.ini 파일에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-111">The full set of properties can be found in the msmdsrv.ini file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0a963-112">이 항목에서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 배포 구성 속성에 대해 설명하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-112">This topic does not document the deployment configuration properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="0a963-113">배포 구성에 대 한 자세한 내용은 [솔루션 배포를 위한 구성 설정 지정](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0a963-113">For more information about deployment configuration, see [Specifying Configuration Settings for Solution Deployment](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).</span></span>  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a><span data-ttu-id="0a963-114">Management Studio에서 구성 속성 보기 또는 설정</span><span class="sxs-lookup"><span data-stu-id="0a963-114">View or set configuration properties in Management Studio</span></span>  
  
1.  <span data-ttu-id="0a963-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-115">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
     <span data-ttu-id="0a963-116">개체 탐색기에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-116">In Object Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, and then click **Properties**.</span></span> <span data-ttu-id="0a963-117">일반 페이지가 표시되고 더 일반적으로 사용되는 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-117">The General page appears, displaying the more commonly used properties.</span></span>  
  
2.  <span data-ttu-id="0a963-118">추가 속성을 보려면 페이지 맨 아래의 **고급 속성 모두 표시** 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-118">To view additional properties, click the **Show Advanced (All) Properties** checkbox at the bottom of the page.</span></span>  
  
     <span data-ttu-id="0a963-119">테이블 형식 모드 및 다차원 모드 서버에 대해서만 서버 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-119">Modifying server properties is supported only for tabular mode and multidimensional mode servers.</span></span> <span data-ttu-id="0a963-120">[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]을 설치한 경우 Microsoft 제품 지원 담당자가 다르게 지시한 경우가 아니라면 항상 기본값을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a963-120">If you installed [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], always use the default values unless you are directed otherwise by a Microsoft product support engineer.</span></span>  
  
     <span data-ttu-id="0a963-121">서버 속성을 통해 운영 또는 성능 문제를 해결하는 방법은 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0a963-121">For guidance on how to address operational or performance issues through server properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
     <span data-ttu-id="0a963-122">Microsoft 백서 [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102)(SQL Server 2005 Analysis Services(SSAS) 서버 속성)에 나와 있는 서버 속성도 참조할 수 있습니다. 서버 속성의 대부분은 지난 몇 번의 릴리스에서 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-122">You can also read about server properties (many of which are unchanged over the last several releases) in this Microsoft white paper, [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a963-123">일부 속성은 msmdrsrv.ini 파일에서만 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-123">Some properties can only be set in the msmdrsrv.ini file.</span></span> <span data-ttu-id="0a963-124">고급 속성을 표시한 후에도 설정할 속성이 표시되지 않으면 msmdsrv.ini 파일을 직접 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-124">If the property you want to set is not visible even after you show advanced properties, you might need to edit the msmdsrv.ini file directly.</span></span>  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a><span data-ttu-id="0a963-125">수동으로 msmdsrv.ini 파일의 구성 속성 보기 또는 편집</span><span class="sxs-lookup"><span data-stu-id="0a963-125">View or edit configuration properties in the msmdsrv.ini file</span></span>  
  
1.  <span data-ttu-id="0a963-126">시작하기 전에 Management Studio의 일반 속성 페이지에서 **DataDir** 속성을 검토하여 msmdsrv.ini 파일을 비롯한 Analysis Services 프로그램 파일의 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-126">Before you begin, check the **DataDir** property in the General property page in Management Studio to verify the location of the Analysis Services program files, including the msmdsrv.ini file.</span></span> <span data-ttu-id="0a963-127">이 프로그램 파일의 위치를 확인하면 올바른 파일을 수정하고 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-127">Verifying the location of the program files will ensure that you are modifying the correct file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0a963-128">기본 설치에서는 \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config 폴더에서 이 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-128">In a default installation, the file can be found in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder</span></span>  
  
2.  <span data-ttu-id="0a963-129">원래 파일로 되돌려야 하는 경우를 대비하여 파일의 백업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-129">Create a backup of the file in case you need to revert to the original file.</span></span>  
  
3.  <span data-ttu-id="0a963-130">텍스트 편집기를 사용하여 msmdsrv.ini 파일을 보거나 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-130">Use a text editor to view or edit the msmdsrv.ini file.</span></span>  
  
4.  <span data-ttu-id="0a963-131">파일을 저장한 후 서비스를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-131">After you save the file, you must restart the service.</span></span>  
  
##  <a name="server-property-reference"></a><a name="bkmk_ref"></a> <span data-ttu-id="0a963-132">서버 속성 참조</span><span class="sxs-lookup"><span data-stu-id="0a963-132">Server Property Reference</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0a963-133">구성 속성은 시스템을 제대로 튜닝하기 위해 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-133">configuration properties are important for fine tuning your system.</span></span> <span data-ttu-id="0a963-134">예를 들어 요구 사항과 일관적으로 쿼리 로그 동작을 만들기 위해 관련 속성들을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-134">For example, to make query log behavior consistent with your requirements, you can set the relevant properties.</span></span>  
  
 <span data-ttu-id="0a963-135">다음 항목에서는 여러 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 구성 속성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-135">The following topics explain the various [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] configuration properties:</span></span>  
  
|<span data-ttu-id="0a963-136">항목</span><span class="sxs-lookup"><span data-stu-id="0a963-136">Topic</span></span>|<span data-ttu-id="0a963-137">Description</span><span class="sxs-lookup"><span data-stu-id="0a963-137">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="0a963-138">일반 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-138">General Properties</span></span>](general-properties.md)|<span data-ttu-id="0a963-139">일반 속성에는 데이터 디렉터리, 백업 디렉터리 및 기타 서버 동작을 정의하는 속성을 비롯한 기본 및 고급 속성이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-139">The general properties are both basic and advanced properties, and include properties that define the data directory, backup directory, and other server behaviors.</span></span>|  
|[<span data-ttu-id="0a963-140">데이터 마이닝 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-140">Data Mining Properties</span></span>](data-mining-properties.md)|<span data-ttu-id="0a963-141">데이터 마이닝 속성은 설정 및 해제할 데이터 마이닝 알고리즘을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-141">The data mining properties control which data mining algorithms are enabled and which are disabled.</span></span> <span data-ttu-id="0a963-142">기본적으로 모든 알고리즘이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-142">By default, all of the algorithms are enabled.</span></span>|  
|<span data-ttu-id="0a963-143">DSO</span><span class="sxs-lookup"><span data-stu-id="0a963-143">DSO</span></span>|<span data-ttu-id="0a963-144">DSO는 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-144">DSO is no longer supported.</span></span> <span data-ttu-id="0a963-145">DSO 속성은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-145">DSO properties are ignored.</span></span>|  
|[<span data-ttu-id="0a963-146">기능 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-146">Feature Properties</span></span>](feature-properties.md)|<span data-ttu-id="0a963-147">기능 속성은 서버 인스턴스 간 연결을 제어하는 속성을 비롯한 제품 기능(대부분 고급 기능)에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-147">The feature properties pertain to product features, most of them advanced, including properties that control links between server instances.</span></span>|  
|[<span data-ttu-id="0a963-148">파일 저장소 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-148">Filestore Properties</span></span>](filestore-properties.md)|<span data-ttu-id="0a963-149">파일 저장 속성은 고급 사용을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-149">The file store properties are for advanced use only.</span></span> <span data-ttu-id="0a963-150">여기에는 고급 메모리 관리 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-150">They include advanced memory management settings.</span></span>|  
|[<span data-ttu-id="0a963-151">잠금 관리자 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-151">Lock Manager Properties</span></span>](lock-manager-properties.md)|<span data-ttu-id="0a963-152">잠금 관리자 속성은 잠금 및 제한 시간에 해당하는 서버 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-152">The lock manager properties define server behaviors pertaining to locking and timeouts.</span></span> <span data-ttu-id="0a963-153">이러한 속성은 대부분 고급 사용을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-153">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="0a963-154">로그 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-154">Log Properties</span></span>](log-properties.md)|<span data-ttu-id="0a963-155">로그 속성은 서버에서 이벤트를 기록하는 경우, 장소 및 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-155">The log properties controls if, where, and how events are logged on the server.</span></span> <span data-ttu-id="0a963-156">여기에는 오류 로깅, 예외 로깅, 비행 레코더, 쿼리 로깅 및 추적이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-156">This includes error logging, exception logging, flight recorder, query logging, and traces.</span></span>|  
|[<span data-ttu-id="0a963-157">메모리 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-157">Memory Properties</span></span>](memory-properties.md)|<span data-ttu-id="0a963-158">메모리 속성은 서버의 메모리 사용 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-158">The memory properties control how the server uses memory.</span></span> <span data-ttu-id="0a963-159">이 속성은 주로 고급 사용을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-159">They are primarily for advanced use.</span></span>|  
|[<span data-ttu-id="0a963-160">네트워크 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-160">Network Properties</span></span>](network-properties.md)|<span data-ttu-id="0a963-161">네트워크 속성은 압축 및 이진 XML을 제어하는 속성을 비롯한 네트워킹과 관련된 서버 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-161">The network properties control server behavior pertaining to networking, including properties that control compression and binary XML.</span></span> <span data-ttu-id="0a963-162">이러한 속성은 대부분 고급 사용을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-162">Most of these properties are for advanced use only.</span></span>|  
|[<span data-ttu-id="0a963-163">OLAP 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-163">OLAP Properties</span></span>](olap-properties.md)|<span data-ttu-id="0a963-164">OLAP 속성은 큐브 및 차원 처리, 지연 처리, 데이터 캐싱 및 쿼리 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-164">The OLAP properties control cube and dimension processing, lazy processing, data caching, and query behavior.</span></span> <span data-ttu-id="0a963-165">여기에는 기본 및 고급 속성이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-165">These include both basic and advanced properties.</span></span>|  
|[<span data-ttu-id="0a963-166">보안 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-166">Security Properties</span></span>](security-properties.md)|<span data-ttu-id="0a963-167">보안 섹션에는 액세스 권한을 정의하는 기본 및 고급 속성이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-167">The security section contains both basic and advanced properties that define access permissions.</span></span> <span data-ttu-id="0a963-168">여기에는 관리자 및 사용자와 관련된 설정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-168">This includes settings pertaining to administrators and users.</span></span>|  
|[<span data-ttu-id="0a963-169">스레드 풀 속성</span><span class="sxs-lookup"><span data-stu-id="0a963-169">Thread Pool Properties</span></span>](thread-pool-properties.md)|<span data-ttu-id="0a963-170">스레드 풀 속성은 서버에서 만드는 스레드 개수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-170">The thread pool properties control how many threads the server creates.</span></span> <span data-ttu-id="0a963-171">이 속성은 주로 고급 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="0a963-171">These are primarily advanced properties.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a963-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a963-172">See Also</span></span>  
 <span data-ttu-id="0a963-173">[Analysis Services 인스턴스 관리](../instances/analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="0a963-173">[Analysis Services Instance Management](../instances/analysis-services-instance-management.md) </span></span>  
 [<span data-ttu-id="0a963-174">솔루션 배포를 위한 구성 설정 지정</span><span class="sxs-lookup"><span data-stu-id="0a963-174">Specifying Configuration Settings for Solution Deployment</span></span>](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
