---
title: 일반 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- IdleConnectionTimeout property
- InstanceVisible property
- TempDir property
- AdminTimeout property
- MinIdleSessionTimeout property
- MaxIdleSessionTimeout property
- IdleOrphanSessionTimeout property
- BackupDir property
- CommitTimeout property
- ExternalCommandTimeout property
- Enabled property
- ForceCommitTimeout property
- Port property
- CoordinatorShutdownMode property
- ServerTimeout property
- AllowedBrowsingFolders property
- CoordinatorCancelCount property
- DataDir property
- CoordinatorQueryMaxThreads property
- CoordinatorExecutionMode property
- ExternalConnectionTimeout property
- CollationName property
- EnableFast1033Locale property
- CoordinatorBuildMaxThreads property
- Language property
- StatisticsStoreSize property
- RepositoryConnectionString property
ms.assetid: 88a8117c-396a-469f-a62d-c6f262504021
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca746a1bb57e84cf0f6a8f47622b118c7180eb1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743499"
---
# <a name="general-properties"></a><span data-ttu-id="2e06b-102">일반 속성</span><span class="sxs-lookup"><span data-stu-id="2e06b-102">General Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="2e06b-103">에서는 다음 표에 나열된 서버 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-103">supports the server properties listed in the following tables.</span></span> <span data-ttu-id="2e06b-104">이 항목에서는 msmdsrv.ini 파일의 서버 속성 중 보안, 네트워크, ThreadPool 등 특정 섹션에 포함되지 않은 속성에 대해 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-104">This topic documents those server properties in the msmdsrv.ini file that are not otherwise included in a specific section, such as Security, Network, or ThreadPool.</span></span> <span data-ttu-id="2e06b-105">추가 서버 속성 및 해당 속성 설정 방법은 [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e06b-105">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="2e06b-106">**적용 대상:** 다차원 및 테이블 형식 서버 모드(다르게 표시되지 않은 경우)</span><span class="sxs-lookup"><span data-stu-id="2e06b-106">**Applies to:** Multidimensional and Tabular server mode, unless noted otherwise</span></span>  
  
## <a name="non-specific-category"></a><span data-ttu-id="2e06b-107">일반 범주</span><span class="sxs-lookup"><span data-stu-id="2e06b-107">Non-Specific Category</span></span>  
 `AdminTimeout`  
 <span data-ttu-id="2e06b-108">관리자 제한 시간(초)을 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-108">A signed 32-bit integer property that defines the administrator timeout in seconds.</span></span> <span data-ttu-id="2e06b-109">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 이 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-109">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 <span data-ttu-id="2e06b-110">이 속성의 기본값은 0으로 제한 시간이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-110">The default value for this property is zero (0), which indicates there is no timeout.</span></span>  
  
 `AllowedBrowsingFolders`  
 <span data-ttu-id="2e06b-111">Analysis Services 대화 상자에서 파일을 저장하고 열고 찾을 때 검색할 수 있는 폴더를 쉼표로 구분된 목록으로 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-111">A string property that specifies in a delimited list the folders that can be browsed when saving, opening, and finding files in Analysis Services dialog boxes.</span></span> <span data-ttu-id="2e06b-112">Analysis Services 서비스 계정은 목록에 추가되는 모든 폴더에 대해 읽기 및 쓰기 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-112">The Analysis Services service account must have read and write permissions to any folders that you add to the list.</span></span>  
  
 `BackupDir`  
 <span data-ttu-id="2e06b-113">백업 명령의 일부로 경로가 지정 되지 않은 경우 기본적으로 백업 파일이 저장 되는 디렉터리의 이름을 식별 하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-113">A string property that identifies the name of the directory where backup files are stored by default, in the event a path is not specified as part of the Backup command.</span></span>  
  
 `CollationName`  
 <span data-ttu-id="2e06b-114">서버 데이터 정렬을 식별하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-114">A string property that identifies the server collation.</span></span> <span data-ttu-id="2e06b-115">자세한 내용은 [언어 및 데이터 정렬&#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e06b-115">For more information, see [Languages and Collations &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md).</span></span>  
  
 `CommitTimeout`  
 <span data-ttu-id="2e06b-116">서버가 트랜잭션을 커밋하기 위해 쓰기 잠금을 획득할 때까지 대기하는 시간(밀리초)을 지정하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-116">An integer property that specifies how long (in milliseconds) the server will wait to acquire a write lock for the purpose of committing a transaction.</span></span> <span data-ttu-id="2e06b-117">서버에서는 트랜잭션을 커밋하는 쓰기 잠금을 적용하기 전에 다른 잠금이 해제될 때까지 기다려야 하므로 대기 기간이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-117">A waiting period is often required because the server must wait for other locks to be released before it can take a write lock that commits the transaction.</span></span>  
  
 <span data-ttu-id="2e06b-118">이 속성의 기본값은 0으로 서버에서 무기한 대기함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-118">The default value for this property is zero (0), which indicates that the server will wait indefinitely.</span></span> <span data-ttu-id="2e06b-119">잠금 관련 속성에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539)(SQL Server 2008 R2 Analysis Services 작업 가이드)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e06b-119">For more information about lock-related properties, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorBuildMaxThreads`  
 <span data-ttu-id="2e06b-120">파티션 인덱스를 작성하도록 할당된 최대 스레드 수를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-120">A signed 32-bit integer property that defines the maximum number of threads allocated to building partition indexes.</span></span> <span data-ttu-id="2e06b-121">메모리 사용을 늘리는 대신 파티션 인덱싱 속도를 높이려면 이 값을 늘리십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-121">Increase this value in order to speed-up partition indexing, at the cost of memory usage.</span></span> <span data-ttu-id="2e06b-122">이 속성에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-122">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorCancelCount`  
 <span data-ttu-id="2e06b-123">내부 반복 횟수에 따라 Cancel 이벤트가 발생했는지 여부를 서버에서 검사하는 빈도를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-123">A signed 32-bit integer property that defines how frequently the server should check whether a Cancel event occurred (based on internal iteration count).</span></span> <span data-ttu-id="2e06b-124">일반 성능 대신 Cancel 이벤트를 보다 자주 검사하려면 이 값을 줄이십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-124">Decrease this number in order to check for Cancel more frequently, at the expense of general performance.</span></span>  
  
 <span data-ttu-id="2e06b-125">테이블 형식 서버 모드에서는 `CoordinatorCancelCount`가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-125">`CoordinatorCancelCount` is ignored in tabular server mode.</span></span>  
  
 `CoordinatorExecutionMode`  
 <span data-ttu-id="2e06b-126">서버에서 시도하는 작업 처리 및 쿼리를 포함한 최대 병렬 작업 수를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-126">A signed 32-bit integer property that defines the maximum number of parallel operations the server will attempt, including processing and querying operations.</span></span> <span data-ttu-id="2e06b-127">0으로 설정하면 내부 알고리즘에 따라 서버에서 작업 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-127">Zero (0) indicates that the server will decide, based on an internal algorithm.</span></span> <span data-ttu-id="2e06b-128">양수 값은 최대 작업 수의 합계를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-128">A positive number indicates the maximum number of operations in total.</span></span> <span data-ttu-id="2e06b-129">음수 값은 부호를 반대로 하여 프로세서당 최대 작업 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-129">A negative number, with the sign reversed, indicates the maximum number of operations per processor.</span></span>  
  
 <span data-ttu-id="2e06b-130">테이블 형식 서버 모드에서는 `CoordinatorExecutionMode`가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-130">`CoordinatorExecutionMode` is ignored in tabular server mode.</span></span>  
  
 <span data-ttu-id="2e06b-131">이 속성의 기본값은 -4로 프로세서당 4개의 병렬 작업으로 서버가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-131">The default value for this property is -4, which indicates the server is limited to 4 parallel operations per processor.</span></span> <span data-ttu-id="2e06b-132">이 속성에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-132">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
 `CoordinatorQueryMaxThreads`  
 <span data-ttu-id="2e06b-133">쿼리 해결 중 파티션 세그먼트당 최대 스레드 수를 정의하는 부호 있는 32비트 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-133">A signed 32-bit integer property that defines the maximum number of threads per partition segment during query resolution.</span></span> <span data-ttu-id="2e06b-134">동시 사용자 수가 적을수록 메모리 사용량이 높은 대신 이 값을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-134">The fewer the number of concurrent users, the higher this value can be, at the cost of memory.</span></span> <span data-ttu-id="2e06b-135">반대로 동시 사용자 수가 많으면 값을 줄여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-135">Conversely, it may need to be lowered if there are a large number of concurrent users.</span></span>  
  
 `CoordinatorShutdownMode`  
 <span data-ttu-id="2e06b-136">코디네이터 종료 모드를 정의하는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-136">A Boolean property that defines coordinator shutdown mode.</span></span> <span data-ttu-id="2e06b-137">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 이 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-137">This is an advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataDir`  
 <span data-ttu-id="2e06b-138">데이터가 저장되는 디렉터리의 이름을 식별하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-138">A string property that identifies the name of the directory where data is stored.</span></span>  
  
 `DeploymentMode`  
 <span data-ttu-id="2e06b-139">Analysis Services 서버 인스턴스의 작업 컨텍스트를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-139">Determines the operational context of an Analysis Services server instance.</span></span> <span data-ttu-id="2e06b-140">대화 상자, 메시지 및 설명서에서는이 속성을 ' 서버 모드 ' 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-140">This property is referred to as 'server mode' in dialog boxes, messages, and documentation.</span></span> <span data-ttu-id="2e06b-141">이 속성은 Analysis Services를 설치할 때 선택한 서버 모드를 기준으로 SQLServer 설치 프로그램이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-141">This property is configured by SQL Server Setup based on the server mode you selected when installing Analysis Services.</span></span> <span data-ttu-id="2e06b-142">이 속성을 내부 값으로만 간주하여 항상 설치 프로그램에서 지정한 값을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-142">This property should be considered internal only, always using the value specified by Setup.</span></span>  
  
 <span data-ttu-id="2e06b-143">이 속성에 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-143">Valid values for this property include the following:</span></span>  
  
|<span data-ttu-id="2e06b-144">값</span><span class="sxs-lookup"><span data-stu-id="2e06b-144">Value</span></span>|<span data-ttu-id="2e06b-145">설명</span><span class="sxs-lookup"><span data-stu-id="2e06b-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e06b-146">0</span><span class="sxs-lookup"><span data-stu-id="2e06b-146">0</span></span>|<span data-ttu-id="2e06b-147">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-147">This is the default value.</span></span> <span data-ttu-id="2e06b-148">이 설정은 MOLAP, HOLAP 및 ROLAP 스토리지를 사용하는 다차원 데이터베이스와 데이터 마이닝 모델에 서비스를 제공하는 데 사용되는 다차원 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-148">It specifies multidimensional mode, used to service multidimensional databases that use MOLAP, HOLAP, and ROLAP storage, as well as data mining models.</span></span>|  
|<span data-ttu-id="2e06b-149">1</span><span class="sxs-lookup"><span data-stu-id="2e06b-149">1</span></span>|<span data-ttu-id="2e06b-150">SharePoint용 PowerPivot 배포의 일부로 설치된 Analysis Services 인스턴스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-150">Specifies Analysis Services instances that were installed as part of a PowerPivot for SharePoint deployment.</span></span> <span data-ttu-id="2e06b-151">SharePoint용 PowerPivot 설치의 일부인 Analysis Services 인스턴스의 배포 모드 속성은 변경하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-151">Do not change the deployment mode property of Analysis Services instance that is part of a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="2e06b-152">모드를 변경하면 PowerPivot 데이터가 서버에서 더 이상 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-152">PowerPivot data will no longer run on the server if you change the mode.</span></span>|  
|<span data-ttu-id="2e06b-153">2</span><span class="sxs-lookup"><span data-stu-id="2e06b-153">2</span></span>|<span data-ttu-id="2e06b-154">메모리 내 스토리지나 DirectQuery 스토리지를 사용하는 테이블 형식 model 데이터베이스를 호스팅하는 데 사용되는 테이블 형식 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-154">Specifies Tabular mode used for hosting tabular model databases that use in-memory storage or DirectQuery storage.</span></span>|  
  
 <span data-ttu-id="2e06b-155">각 모드는 다른 모드와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-155">Each mode is exclusive of the other.</span></span> <span data-ttu-id="2e06b-156">테이블 형식 모드용으로 구성된 서버는 큐브 및 차원이 포함된 기본 Analysis Services 데이터베이스를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-156">A server that is configured for tabular mode cannot run Analysis Services databases that contain cubes and dimensions.</span></span> <span data-ttu-id="2e06b-157">기본 컴퓨터 하드웨어에서 지원하는 경우 같은 컴퓨터에 Analysis Services 인스턴스를 여러 개 설치하고 각 인스턴스가 다른 배포 모드를 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-157">If the underlying computer hardware can support it, you can install multiple instances of Analysis Services on the same computer and configure each instance to use a different deployment mode.</span></span> <span data-ttu-id="2e06b-158">Analysis Services는 리소스를 많이 사용하는 애플리케이션이므로</span><span class="sxs-lookup"><span data-stu-id="2e06b-158">Remember that Analysis Services is a resource intensive application.</span></span> <span data-ttu-id="2e06b-159">고성능 서버인 경우에만 한 시스템에 여러 개의 인스턴스를 배포하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-159">Deploying multiple instances on the same system is recommended only for high-end servers.</span></span>  
  
 `EnableFast1033Locale`  
 <span data-ttu-id="2e06b-160">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-160">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ExternalCommandTimeout`  
 <span data-ttu-id="2e06b-161">관계형 데이터 원본 및 외부 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버를 포함하여 외부 서버에 실행된 명령의 제한 시간(초)을 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-161">An integer property that defines the timeout, in seconds, for commands issued to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span>  
  
 <span data-ttu-id="2e06b-162">이 속성의 기본값은 3600(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-162">The default value for this property is 3600 (seconds).</span></span>  
  
 `ExternalConnectionTimeout`  
 <span data-ttu-id="2e06b-163">관계형 데이터 원본 및 외부 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버를 포함하여 외부 서버에 대한 연결을 만들기 위한 제한 시간(초)을 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-163">An integer property that defines the timeout, in seconds, for creating connections to external servers, including relational data sources and external [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] servers.</span></span> <span data-ttu-id="2e06b-164">연결 제한 시간이 연결 문자열에 지정된 경우 이 속성은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-164">This property is ignored if a connection timeout is specified on the connection string.</span></span>  
  
 <span data-ttu-id="2e06b-165">이 속성의 기본값은 60(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-165">The default value for this property is 60 (seconds).</span></span>  
  
 `ForceCommitTimeout`  
 <span data-ttu-id="2e06b-166">진행 중인 쿼리를 포함하여 현재 명령 이전의 다른 명령을 취소하기 전에 쓰기 커밋 작업이 대기해야 하는 시간(밀리초)을 지정하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-166">An integer property that specifies how long, in milliseconds, a write commit operation should wait before canceling other commands that preceded the current command, including queries in progress.</span></span> <span data-ttu-id="2e06b-167">이 속성을 사용하면 쿼리와 같이 우선 순위가 낮은 작업을 취소하여 커밋 트랜잭션을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-167">This allows the commit transaction to proceed by canceling lower priority operations, such as queries.</span></span>  
  
 <span data-ttu-id="2e06b-168">이 속성의 기본값은 30초(30000밀리초)로, 커밋 트랜잭션이 30초 동안 대기한 후에만 다른 명령이 강제로 시간 초과됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-168">The default value for this property is 30 seconds (30000 milliseconds), which indicates that other commands will not be forced to timeout until the commit transaction has been waiting for 30 seconds.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e06b-169">이 이벤트에 의해 취소된 쿼리와 프로세스는 "`Server: The operation has been cancelled`"라는 오류 메시지를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-169">Queries and processes cancelled by this event will report the following error message: "`Server: The operation has been cancelled`"</span></span>  
  
 <span data-ttu-id="2e06b-170">이 속성에 대한 자세한 내용은 [SQL Server 2008 R2 Analysis Services 작업 가이드](https://go.microsoft.com/fwlink/?LinkID=225539)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2e06b-170">For more information about this property, see [SQL Server 2008 R2 Analysis Services Operations Guide](https://go.microsoft.com/fwlink/?LinkID=225539).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2e06b-171">`ForceCommitTimeout`은 큐브 처리 명령과 쓰기 저장 작업에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-171">`ForceCommitTimeout` applies to cube processing commands and to writeback operations.</span></span>  
  
 `IdleConnectionTimeout`  
 <span data-ttu-id="2e06b-172">비활성 상태의 연결에 대한 제한 시간(초)을 지정하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-172">An integer property that specifies a timeout, in seconds, for connections that are inactive.</span></span>  
  
 <span data-ttu-id="2e06b-173">이 속성의 기본값은 0으로 유휴 연결이 시간 초과되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-173">The default value for this property is zero (0), which indicates that idle connections will not be timed out.</span></span>  
  
 `IdleOrphanSessionTimeout`  
 <span data-ttu-id="2e06b-174">서버 메모리에서 분리된 세션이 유지되는 시간(초)을 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-174">An integer property that defines how long, in seconds, orphaned sessions will be retained in server memory.</span></span> <span data-ttu-id="2e06b-175">분리된 세션은 더 이상 관련 연결이 없는 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-175">An orphaned session is one that no longer has an associated connection.</span></span> <span data-ttu-id="2e06b-176">기본값은 120초입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-176">The default is 120 seconds.</span></span>  
  
 `InstanceVisible`  
 <span data-ttu-id="2e06b-177">서버 인스턴스가 SQL Server Browser 서비스에서 인스턴스 요청을 검색하도록 표시되는지 여부를 나타내는 부울 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-177">A Boolean property that indicates whether the server instance is visible to discover instance requests from SQL Server Browser service.</span></span> <span data-ttu-id="2e06b-178">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-178">The default is True.</span></span> <span data-ttu-id="2e06b-179">이 속성을 false로 설정하면 인스턴스가 SQL Server Browser에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-179">If you set it to false, the instance is not visible to SQL Server Browser.</span></span>  
  
 `Language`  
 <span data-ttu-id="2e06b-180">오류 메시지 및 번호 서식 지정을 포함하여 언어를 정의하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-180">A string property that defines the language, including error messages and number formatting.</span></span> <span data-ttu-id="2e06b-181">이 속성은 CollationName 속성을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-181">This property overrides the CollationName property.</span></span>  
  
 <span data-ttu-id="2e06b-182">이 속성의 기본값은 빈 문자열로 CollationName 속성이 언어를 정의함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-182">The default value for this property is blank, which indicates that the CollationName property defines the language.</span></span>  
  
 `LogDir`  
 <span data-ttu-id="2e06b-183">서버 로그가 포함된 디렉터리 이름을 식별하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-183">A string property that identifies the name of the directory that contains server logs.</span></span> <span data-ttu-id="2e06b-184">이 속성은 데이터베이스 테이블과는 달리 디스크 파일이 로깅용으로 사용되는 경우에만 적용됩니다(기본 동작).</span><span class="sxs-lookup"><span data-stu-id="2e06b-184">This property only applies when disk files are used for logging, as opposed to database tables (the default behavior).</span></span>  
  
 `MaxIdleSessionTimeout`  
 <span data-ttu-id="2e06b-185">최대 유휴 세션 제한 시간(초)을 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-185">An integer property that defines the maximum idle session timeout, in seconds.</span></span> <span data-ttu-id="2e06b-186">기본값은 0 이며,이는 세션이 시간 초과 되지 않음을 나타냅니다. 그러나 서버에서 리소스 제약 조건을 적용 하는 경우에도 유휴 세션이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-186">The default is zero (0), indicating that sessions are never timed out. However, idle sessions will still be removed if the server is under resource constraints.</span></span>  
  
 `MinIdleSessionTimeout`  
 <span data-ttu-id="2e06b-187">유휴 세션이 시간 초과되는 최소 시간(초)을 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-187">An integer property that defines the minimum time, in seconds, that idle sessions will timeout.</span></span> <span data-ttu-id="2e06b-188">기본값은 2700초입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-188">The default is 2700 seconds.</span></span> <span data-ttu-id="2e06b-189">이 시간이 만료되면 서버에서 유휴 세션을 종료할 수 있지만 이를 위한 메모리가 필요한 경우에만 세션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-189">After this time expires, the server is permitted to end the idle session, but will only do so as memory is needed.</span></span>  
  
 `Port`  
 <span data-ttu-id="2e06b-190">서버에서 클라이언트 연결을 수신할 포트 번호를 정의하는 정수 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-190">An integer property that defines the port number on which server will listen for client connections.</span></span> <span data-ttu-id="2e06b-191">설정하지 않으면 서버가 사용되지 않은 첫 번째 포트를 동적으로 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-191">If not set, server dynamically finds first unused port.</span></span>  
  
 <span data-ttu-id="2e06b-192">이 속성의 기본값은 0으로 이후 포트 2383이 기본값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-192">The default value for this property is zero (0), which in turn defaults to port 2383.</span></span> <span data-ttu-id="2e06b-193">포트 구성에 대한 자세한 내용은 [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e06b-193">For more information about port configuration, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
 `ServerTimeout`  
 <span data-ttu-id="2e06b-194">쿼리에 대한 제한 시간(초)을 정의하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-194">An integer that defines the timeout, in seconds, for queries.</span></span> <span data-ttu-id="2e06b-195">기본값은 3600초(또는 60분)입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-195">The default is 3600 seconds (or 60 minutes).</span></span> <span data-ttu-id="2e06b-196">0을 지정하면 쿼리가 시간 초과되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-196">Zero (0) specifies that no queries will timeout.</span></span>  
  
 `TempDir`  
 <span data-ttu-id="2e06b-197">처리, 복원 및 기타 작업 중에 사용되는 임시 파일을 정의하기 위한 위치를 지정하는 문자열 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-197">A string property that specifies the location for storing temporary files used during processing, restoring, and other operations.</span></span> <span data-ttu-id="2e06b-198">이 속성의 기본값은 설치 프로그램에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-198">The default value for this property is determined by setup.</span></span> <span data-ttu-id="2e06b-199">지정하지 않는 경우의 기본값은 Data 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-199">If not specified, the default is the Data directory.</span></span>  
  
## <a name="requestprioritization-category"></a><span data-ttu-id="2e06b-200">RequestPrioritization 범주</span><span class="sxs-lookup"><span data-stu-id="2e06b-200">RequestPrioritization Category</span></span>  
 `Enabled`  
 <span data-ttu-id="2e06b-201">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-201">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `StatisticsStoreSize`  
 <span data-ttu-id="2e06b-202">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 지원 지침에 따라 변경하는 경우를 제외하고 고급 속성을 변경하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e06b-202">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e06b-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e06b-203">See Also</span></span>  
 <span data-ttu-id="2e06b-204">[Analysis Services에서 서버 속성 구성](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="2e06b-204">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="2e06b-205">Analysis Services 인스턴스의 서버 모드 확인</span><span class="sxs-lookup"><span data-stu-id="2e06b-205">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
