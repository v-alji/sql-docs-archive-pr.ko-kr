---
title: 원격 파티션 만들기 및 관리 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bd44775a579cc8f770f088594653bb65000407f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639026"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a><span data-ttu-id="0e721-102">원격 파티션 만들기 및 관리(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="0e721-102">Create and Manage a Remote Partition (Analysis Services)</span></span>
  <span data-ttu-id="0e721-103">측정값 그룹을 분할할 때 원격 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 보조 데이터베이스를 파티션 스토리지로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-103">When partitioning a measure group, you can configure a secondary database on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance as partition storage.</span></span>  
  
 <span data-ttu-id="0e721-104">master 데이터베이스라는 큐브의 원격 파티션은 보조 데이터베이스라는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 원격 인스턴스에 있는 전용 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-104">Remote partitions for a cube (called the master database) are stored in a dedicated [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (called the secondary database).</span></span>  
  
 <span data-ttu-id="0e721-105">전용 보조 데이터베이스는 단 하나의 master 데이터베이스에 대한 원격 파티션을 저장할 수 있지만 모든 보조 데이터베이스가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 동일한 원격 인스턴스에 있는 경우 master 데이터베이스는 여러 보조 데이터베이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-105">A dedicated secondary database can store remote partitions for one and only one master database, but the master database can use multiple secondary databases, as long as all the secondary databases are on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="0e721-106">원격 파티션 전용 데이터베이스의 차원은 연결된 차원으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-106">Dimensions in a database dedicated to remote partitions are created as linked dimensions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e721-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="0e721-107">Prerequisites</span></span>  
 <span data-ttu-id="0e721-108">원격 파티션을 만들기 전에 다음 조건이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-108">Before you create a remote partition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="0e721-109">파티션을 저장하려면 두 번째 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스와 전용 데이터베이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-109">You must have a second [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and dedicated database to store the partitions.</span></span> <span data-ttu-id="0e721-110">보조 데이터베이스는 master 데이터베이스에 원격 파티션 스토리지를 제공하는 한 가지 용도로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-110">The secondary database is single-purpose; it provides storage of remote partitions for a master database.</span></span>  
  
-   <span data-ttu-id="0e721-111">두 서버 인스턴스가 같은 버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-111">Both server instances must be the same version.</span></span> <span data-ttu-id="0e721-112">두 데이터베이스는 동일한 기능 수준이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-112">Both databases should be the same functional level.</span></span>  
  
-   <span data-ttu-id="0e721-113">두 인스턴스는 TCP 연결에 맞게 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-113">Both instances must be configured for TCP connections.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0e721-114">는 HTTP 프로토콜을 사용하여 원격 파티션을 만드는 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-114">does not support creation of remote partitions by using the HTTP protocol.</span></span>  
  
-   <span data-ttu-id="0e721-115">두 컴퓨터 모두 방화벽 설정이 외부 연결을 허용하도록 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-115">Firewall settings on both computers must be set to accept outside connections.</span></span> <span data-ttu-id="0e721-116">방화벽을 설정하는 방법에 대한 자세한 내용은 [Analysis Services 액세스를 허용하도록 Windows 방화벽 구성](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0e721-116">For information about setting the firewall, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="0e721-117">master 데이터베이스를 실행하는 인스턴스의 서비스 계정은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 원격 인스턴스에 대한 관리 액세스 권한을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-117">The service account for the instance running the master database must have administrative access to the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="0e721-118">서비스 계정이 변경되면 서버 및 데이터베이스에 대한 사용 권한을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-118">If the service account changes, you must update permissions on both the server and database.</span></span>  
  
-   <span data-ttu-id="0e721-119">두 컴퓨터의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-119">You must be an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator on both computers.</span></span>  
  
-   <span data-ttu-id="0e721-120">재해 복구 계획이 원격 파티션의 백업 및 복원에 적합한지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-120">You must ensure your disaster recovery plan accommodates backup and restore of the remote partitions.</span></span> <span data-ttu-id="0e721-121">원격 파티션을 사용하면 백업 및 복원 작업이 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-121">Using remote partitions can complicate backup and restore operations.</span></span> <span data-ttu-id="0e721-122">필요한 데이터를 복원할 수 있도록 계획을 철저히 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-122">Be sure to test your plan thoroughly to be sure you can restore the necessary data.</span></span>  
  
## <a name="configure-remote-partitions"></a><span data-ttu-id="0e721-123">원격 파티션 구성</span><span class="sxs-lookup"><span data-stu-id="0e721-123">Configure remote partitions</span></span>  
 <span data-ttu-id="0e721-124">인스턴스를 실행 하는 별개의 두 컴퓨터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 각각 한 컴퓨터를 마스터 서버로 지정 하 고 다른 컴퓨터는 하위 서버로 지정 하는 원격 파티션 배열을 만드는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-124">Two separate computers that are running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are each required to create a remote partition arrangement that designates one computer as the master server and the other computer as the subordinate server.</span></span>  
  
 <span data-ttu-id="0e721-125">다음 절차에서는 마스터 서버에 배포된 큐브 데이터베이스가 있는 두 개의 서버 인스턴스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-125">The following procedure assumes that you have two server instances, with a cube database deployed on the master server.</span></span> <span data-ttu-id="0e721-126">이 절차에서는 큐브 데이터베이스를 db 마스터라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-126">For the purposes of this procedure, the cube database is referred to as db-master.</span></span> <span data-ttu-id="0e721-127">원격 파티션을 포함하는 스토리지 데이터베이스는 db 스토리지라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-127">The storage database containing remote partitions is referred to as db-storage.</span></span>  
  
 <span data-ttu-id="0e721-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 및 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용하여 이 절차를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-128">You will use both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to complete this procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e721-129">원격 파티션은 다른 원격 파티션과만 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-129">Remote partitions can be merged only with other remote partitions.</span></span> <span data-ttu-id="0e721-130">로컬 파티션과 원격 파티션을 조합하여 사용하는 경우 다른 방법은 더 이상 사용하지 않는 파티션을 삭제하여 결합된 데이터를 포함하는 새 파티션을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-130">If you are using a combination of local and remote partitions, an alternative approach is to create new partitions that include the combined data, deleting the partitions you no longer use.</span></span>  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a><span data-ttu-id="0e721-131">SSDT의 큐브 배포에 대한 올바른 서버 이름 지정</span><span class="sxs-lookup"><span data-stu-id="0e721-131">Specify valid server names for cube deployment (in SSDT)</span></span>  
  
1.  <span data-ttu-id="0e721-132">마스터 서버: 솔루션 탐색기에서 솔루션 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-132">On the master server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="0e721-133">**속성** 대화 상자에서 **구성 속성**을 클릭한 다음 **배포**를 클릭하고 **서버** 를 클릭한 다음 마스터 서버 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-133">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the master server's name.</span></span>  
  
2.  <span data-ttu-id="0e721-134">종속 서버: 솔루션 탐색기에서 솔루션 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-134">On the subordinate server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="0e721-135">**속성** 대화 상자에서 **구성 속성**을 클릭한 다음 **배포**를 클릭하고 **서버** 를 클릭한 다음 하위 서버 이름을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-135">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the subordinate server's name.</span></span>  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a><span data-ttu-id="0e721-136">SSDT의 보조 데이터베이스 만들기 및 배포</span><span class="sxs-lookup"><span data-stu-id="0e721-136">Create and deploy a secondary database (in SSDT)</span></span>  
  
1.  <span data-ttu-id="0e721-137">종속 서버: 스토리지 데이터베이스용으로 새 Analysis Services 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-137">On the subordinate server: Create a new Analysis Services project for the storage database.</span></span>  
  
2.  <span data-ttu-id="0e721-138">종속 서버: 솔루션 탐색기에서 큐브 데이터베이스 db-master를 가리키는 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-138">On the subordinate server: In Solution Explorer, create a new data source pointing to the cube database, db-master.</span></span> <span data-ttu-id="0e721-139">**네이티브 OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-139">Use the provider **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="0e721-140">종속 서버: 솔루션을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-140">On the subordinate server: Deploy the solution.</span></span>  
  
#### <a name="enable-features-in-ssms"></a><span data-ttu-id="0e721-141">기능 활성화(SSMS)</span><span class="sxs-lookup"><span data-stu-id="0e721-141">Enable features (in SSMS)</span></span>  
  
1.  <span data-ttu-id="0e721-142">종속 서버: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 연결된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-142">On the subordinate server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="0e721-143">**Feature\LinkToOtherInstanceEnabled** 및 **Feature\LinkFromOtherInstanceEnabled** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-143">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
2.  <span data-ttu-id="0e721-144">종속 서버: 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **다시 시작**을 선택하여 서버를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-144">On the subordinate server: Restart the server by right-clicking the server name in Object Explorer and selecting **Restart**.</span></span>  
  
3.  <span data-ttu-id="0e721-145">마스터 서버: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 개체 탐색기에서 연결된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-145">On the master server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="0e721-146">**Feature\LinkToOtherInstanceEnabled** 및 **Feature\LinkFromOtherInstanceEnabled** 를 **True**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-146">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
4.  <span data-ttu-id="0e721-147">마스터 서버: 서버를 다시 시작하려면 개체 탐색기에서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **다시 시작**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-147">On the master server: To restart the server, right-click the server name in Object Explorer and select **Restart**.</span></span>  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a><span data-ttu-id="0e721-148">원격 서버에서 MasterDataSourceID 데이터베이스 속성 설정(SSMS)</span><span class="sxs-lookup"><span data-stu-id="0e721-148">Set the MasterDataSourceID database property on the remote server (in SSMS)</span></span>  
  
1.  <span data-ttu-id="0e721-149">종속 서버: 저장소 데이터베이스인 db 저장소를 마우스 오른쪽 단추로 클릭 하 고 **데이터베이스 스크립팅**  |  **ALTER**  |  **새 쿼리 편집기 창**을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-149">On the subordinate server: Right-click the storage database, db-storage, point to **Script Database as** | **ALTER To** | **New Query Editor Window**.</span></span>  
  
2.  <span data-ttu-id="0e721-150">XMLA에 **MasterDataSourceID** 를 추가한 다음 큐브 데이터베이스(db 마스터) ID를 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-150">Add **MasterDataSourceID** to the XMLA, and then specify the cube database, db-master, ID as the value.</span></span> <span data-ttu-id="0e721-151">XMLA는 다음과 비슷해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-151">The XMLA should look similar to the following.</span></span>  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  <span data-ttu-id="0e721-152">F5 키를 눌러 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-152">Press F5 to execute the script.</span></span>  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a><span data-ttu-id="0e721-153">원격 파티션 설정(SSDT)</span><span class="sxs-lookup"><span data-stu-id="0e721-153">Set up the remote partition (in SSDT)</span></span>  
  
1.  <span data-ttu-id="0e721-154">마스터 서버에서: 큐브 디자이너에서 큐브를 열고 **파티션** 탭을 클릭 합니다. 측정값 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-154">On the master server: Open the cube in Cube Designer and click **Partitions** tab. Expand the measure group.</span></span> <span data-ttu-id="0e721-155">측정값 그룹이 이미 여러 파티션에 맞게 구성되어 있는 경우 **새 파티션** 을 클릭하거나 원본 열에서 찾아보기(.</span><span class="sxs-lookup"><span data-stu-id="0e721-155">Click **New Partition** if the measure group is already configured for multiple partitions, or click the browse (.</span></span> <span data-ttu-id="0e721-156">.</span><span class="sxs-lookup"><span data-stu-id="0e721-156">.</span></span> <span data-ttu-id="0e721-157">) 단추를 클릭하여 기존 파티션을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-157">) button in the Source column to edit the existing partition.</span></span>  
  
2.  <span data-ttu-id="0e721-158">파티션 마법사의 **원본 정보 지정**에서 원래 데이터 원본 뷰 및 팩트 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-158">In the Partition Wizard, in **Specify Source Information**, select the original Data Source View and fact table.</span></span>  
  
3.  <span data-ttu-id="0e721-159">쿼리 바인딩을 사용하는 경우 만드는 새 파티션의 데이터를 분할하는 WHERE 절을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-159">If using a query binding, provide a WHERE clause that segments the data for the new partition you are creating.</span></span>  
  
4.  <span data-ttu-id="0e721-160">**처리 및 스토리지 위치**의 **처리 위치**에서 **원격 Analysis Services 데이터 원본**을 선택하고 **새로 만들기**를 클릭하여 하위 데이터베이스(db 스토리지)를 가리키는 새 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-160">In **Processing and Storage Locations**, under **Processing Location**, choose **Remote Analysis Services data source** and click **New** to create a new data source that points to your subordinate database, db-storage.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0e721-161">컬렉션에 데이터 원본이 없음을 나타내는 오류가 표시되면 스토리지 데이터베이스(db 스토리지)의 프로젝트를 열고 master 데이터베이스(db 마스터)를 가리키는 데이터 원본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-161">If you get an error indicating the data source does not exist in the collection, you must open the project of the storage database, db-storage, and create a data source that points to the master database, db-master.</span></span>  
  
5.  <span data-ttu-id="0e721-162">마스터 서버: 솔루션 탐색기에서 큐브 이름을 마우스 오른쪽 단추로 클릭하고 **처리** 를 선택하여 큐브를 전체 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-162">On the master server: Right-click the cube name in Solution Explorer, select **Process** and fully process the cube.</span></span>  
  
## <a name="administering-remote-partitions"></a><span data-ttu-id="0e721-163">원격 파티션 관리</span><span class="sxs-lookup"><span data-stu-id="0e721-163">Administering remote partitions</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0e721-164">는 원격 파티션의 병렬 및 순차적 처리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-164">supports both parallel and sequential processing of remote partitions.</span></span> <span data-ttu-id="0e721-165">파티션이 정의된 master 데이터베이스는 큐브의 파티션 처리에 참여하는 모든 인스턴스 간의 트랜잭션을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-165">The master database, where the partitions were defined, coordinates the transactions among all the instances that participate in processing the partitions of a cube.</span></span> <span data-ttu-id="0e721-166">그런 다음 파티션을 처리한 모든 인스턴스에 처리 보고서가 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-166">Processing reports are then sent to all instances that processed a partition.</span></span>  
  
 <span data-ttu-id="0e721-167">원격 파티션을 포함하는 큐브는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 단일 인스턴스에 있는 해당 파티션과 함께 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-167">A cube that contains remote partitions can be administered together with its partitions on a single instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="0e721-168">하지만 원격 파티션에 대한 메타데이터는 파티션과 부모 큐브가 정의된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 의 인스턴스에서만 보고 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-168">However, the metadata for the remote partition can be viewed and updated only on the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube were defined.</span></span> <span data-ttu-id="0e721-169">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 원격 인스턴스에서 원격 파티션을 보거나 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-169">The remote partition cannot be viewed or updated on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0e721-170">원격 파티션 스토리지에 전용되는 데이터베이스는 스키마 행 집합에 노출되지 않지만, AMO(Analysis Management Objects)를 사용하는 애플리케이션은 Analysis Discover 명령에 대한 XML을 사용하여 전용 데이터베이스를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-170">Although databases dedicated to storage of remote partitions are not exposed to schema rowsets, applications that use Analysis Management Objects (AMO) can still discover a dedicated database by using the XML for Analysis Discover command.</span></span> <span data-ttu-id="0e721-171">TCP 또는 HTTP 클라이언트를 사용하여 전용 데이터베이스에 직접 전송되는 CREATE 또는 DELETE 명령은 성공하지만, 이 동작을 수행하면 면밀하게 관리되는 이 데이터베이스가 손상될 수 있음을 알리는 경고가 서버에서 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e721-171">Any CREATE or DELETE command that is sent directly to a dedicated database by using a TCP or HTTP client will succeed, but the server will return a warning indicating that the action may damage this closely managed database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e721-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e721-172">See Also</span></span>  
 [<span data-ttu-id="0e721-173">파티션&#40;Analysis Services - 다차원 데이터&#41;</span><span class="sxs-lookup"><span data-stu-id="0e721-173">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
