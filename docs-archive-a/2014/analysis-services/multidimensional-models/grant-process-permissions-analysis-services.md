---
title: 처리 권한 부여 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], process
- process permissions [Analysis Services]
ms.assetid: c1531c23-6b46-46a8-9ba3-b6d3f2016443
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4e41e8710bc167ef53eb2aad2cbf678019b96e0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734504"
---
# <a name="grant-process-permissions-analysis-services"></a><span data-ttu-id="79940-102">처리 권한 부여(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="79940-102">Grant process permissions (Analysis Services)</span></span>
  <span data-ttu-id="79940-103">관리자는 Analysis Services 처리 작업의 전용 역할을 만들어, 다른 사용자 또는 자동 일정 처리를 위해 사용되는 애플리케이션에 특정 작업을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-103">As an administrator, you can create a role dedicated to Analysis Services processing operations, allowing you to delegate that particular task to other users, or to applications used for unattended scheduled processing.</span></span> <span data-ttu-id="79940-104">처리 권한은 데이터베이스,  큐브,  차원 및 마이닝 구조 수준에서 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-104">Process permissions can be granted at the database, cube, dimension, and mining structure levels.</span></span> <span data-ttu-id="79940-105">대규모 큐브 또는 테이블 형식 데이터베이스에서 작업하지 않는다면 서로 종속된 개체를 비롯한 모든 개체를 포함하여 데이터베이스 수준에서 처리 권한을 부여하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-105">Unless you are working with a very large cube or tabular database, we recommend granting processing rights at the database level, inclusive of all objects, including those having dependencies on each other.</span></span>  
  
 <span data-ttu-id="79940-106">권한은, 개체를 권한 및 Windows 사용자 또는 그룹 계정과 연결하는 역할을 통해 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="79940-106">Permissions are granted through roles that associate objects with permissions and Windows user or group accounts.</span></span> <span data-ttu-id="79940-107">이러한 권한은 부가적입니다.</span><span class="sxs-lookup"><span data-stu-id="79940-107">Remember that permissions are additive.</span></span> <span data-ttu-id="79940-108">한 역할이 큐브를 처리하는 권한을 부여하고 두 번째 역할은 동일한 사용자에게 차원을 처리하는 권한을 부여하는 경우 두 가지 역할의 권한이 결합되어 해당 데이터베이스 내에서 큐브를 처리하고 지정된 차원을 처리하는 권한을 모두 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-108">If one role grants permission to process a cube, while a second role gives the same user permission to process a dimension, the permissions from the two different roles combine to give the user permission to both process the cube and process the specified dimension within that database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="79940-109">처리 권한만 가진 역할의 사용자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 사용해서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에 연결하여 개체를 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-109">A user whose role only has Process permissions will be unable to use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and process objects.</span></span> <span data-ttu-id="79940-110">이러한 도구를 사용하려면 개체 메타데이터에 액세스할 수 있는 `Read Definition` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-110">These tools require the `Read Definition` permission to access object metadata.</span></span> <span data-ttu-id="79940-111">두 가지 도구를 사용할 수 없는 경우 처리 작업을 실행하려면 XMLA 스크립트를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-111">Without the ability to use either tool, XMLA script must be used to execute a processing operation.</span></span>  
>   
>  <span data-ttu-id="79940-112">테스트를 위해 `Read Definition` 권한을 부여하는 것도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-112">We suggest you also grant `Read Definition` permissions for testing purposes.</span></span> <span data-ttu-id="79940-113">`Read Definition` 및 `Process Database` 권한을 모두 가진 사용자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체를 대화형으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-113">A user having both `Read Definition` and `Process Database` permissions can process objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], interactively.</span></span> <span data-ttu-id="79940-114">자세한 내용은 [개체 메타데이터에 대한 정의 읽기 권한 부여&#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="79940-114">See [Grant read definition permissions on object metadata &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md) for details.</span></span>  
  
## <a name="set-processing-permissions-at-the-database-level"></a><span data-ttu-id="79940-115">데이터베이스 수준에서 처리 권한 설정</span><span class="sxs-lookup"><span data-stu-id="79940-115">Set processing permissions at the database level</span></span>  
 <span data-ttu-id="79940-116">이 섹션에서는 데이터베이스의 모든 큐브, 차원, 마이닝 구조 및 마이닝 모델에 대해 관리자가 아닌 사용자의 처리를 사용하도록 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-116">This section explains how to enable processing by non-administrators, for all cubes, dimensions, mining structures, and mining models in the database.</span></span>  
  
1.  <span data-ttu-id="79940-117">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 데이터베이스 폴더를 열고 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-117">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="79940-118">**역할**  |  **새 역할**을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-118">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="79940-119">이름 및 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-119">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="79940-120">**일반** 창에서 확인란을 선택 `Process Database` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-120">In the **General** pane, select the `Process Database` check box.</span></span> <span data-ttu-id="79940-121">또한를 선택 `Read Definition` 하 여와 같은 SQL Server 도구 중 하나를 통해 대화형 처리를 사용 하도록 설정 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-121">Additionally, select `Read Definition` to also enable interactive processing through one of the SQL Server tools, such as [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
4.  <span data-ttu-id="79940-122">**멤버 자격** 창에서 이 데이터베이스의 모든 개체를 처리할 수 있는 권한을 가진 Windows 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-122">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="79940-123">**확인** 을 클릭하여 역할 정의를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-123">Click **OK** to complete the role definition.</span></span>  
  
## <a name="set-processing-permissions-on-individual-objects"></a><span data-ttu-id="79940-124">개별 개체에 대한 처리 권한 설정</span><span class="sxs-lookup"><span data-stu-id="79940-124">Set processing permissions on individual objects</span></span>  
 <span data-ttu-id="79940-125">개별 큐브, 차원, 데이터 마이닝 구조 또는 모델에 대한 처리 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-125">You can set processing permissions on individual cubes, dimensions, data mining structures or models.</span></span>  
  
 <span data-ttu-id="79940-126">함께 처리해야 하는 개체를 실수로 제외하는 경우(예를 들어 관련 차원은 제외하고 큐브에 대한 처리를 사용하도록 설정하는 경우) 처리가 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-126">Processing can fail if you inadvertently exclude objects that need to be processed together (for example, if you enable processing on a cube, but not on its related dimensions).</span></span> <span data-ttu-id="79940-127">개체 종속성은 놓치기 쉬우므로 개별 개체에 대한 처리 권한을 설정할 때 철저한 테스트가 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-127">Because it can be easy to miss object dependencies, thorough testing is essential when setting processing permissions on individual objects.</span></span>  
  
1.  <span data-ttu-id="79940-128">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 데이터베이스 폴더를 열고 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-128">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="79940-129">**역할**  |  **새 역할**을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-129">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="79940-130">이름 및 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-130">Enter a name and description.</span></span>  
  
3.  <span data-ttu-id="79940-131">**일반** 창에서 확인란의 선택을 취소 `Process Database` 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-131">In the **General** pane, clear the `Process Database` check box.</span></span> <span data-ttu-id="79940-132">데이터베이스 권한은 역할 옵션을 회색으로 표시하거나 선택하지 못하도록 설정하여 하위 수준의 개체에 대한 권한을 설정하는 기능을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-132">Database permissions override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
     <span data-ttu-id="79940-133">기술적으로, 전용 처리 역할의 경우 데이터베이스 권한은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-133">Technically, no database permissions are needed for dedicated processing roles.</span></span> <span data-ttu-id="79940-134">그러나 `Read Definition` 데이터베이스 수준에서가 없으면에서 데이터베이스를 볼 수 없으므로 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 테스트가 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="79940-134">But without `Read Definition` at the database level, you cannot view the database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], making testing more difficult.</span></span>  
  
4.  <span data-ttu-id="79940-135">처리할 개별 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-135">Select individual objects to process:</span></span>  
  
    -   <span data-ttu-id="79940-136">**큐브** 창에서 각 큐브에 대한 **처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-136">In the **Cubes** pane, select the **Process** check box for each cube.</span></span>  
  
    -   <span data-ttu-id="79940-137">**차원** 창에서 **모든 데이터베이스 차원**을 선택한 다음 각 차원에 대한 **처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-137">In the **Dimensions** pane, select **All database dimensions**, and then **Process** check box for each dimension.</span></span> <span data-ttu-id="79940-138">또는 모든 행을 선택한 다음 Shift를 클릭하여 확인란 선택을 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-138">Or, select all rows, then use shift-click to toggle the check box selections.</span></span>  
  
5.  <span data-ttu-id="79940-139">**멤버 자격** 창에서 이러한 개체를 처리할 수 있는 권한을 가진 Windows 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-139">In the **Membership** pane, add the Windows user and group accounts having permission to process these objects.</span></span>  
  
6.  <span data-ttu-id="79940-140">**확인** 을 클릭하여 역할 정의를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-140">Click **OK** to complete the role definition.</span></span>  
  
## <a name="test-processing"></a><span data-ttu-id="79940-141">테스트 처리</span><span class="sxs-lookup"><span data-stu-id="79940-141">Test processing</span></span>  
  
1.  <span data-ttu-id="79940-142">Shift 키를 누르고 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 마우스 오른쪽 단추로 클릭하고, **다른 사용자 권한으로 실행** 을 선택하고 테스트 중인 역할에 할당된 Windows 계정을 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-142">Hold down the shift-key and right-click [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select **Run as a different user** and connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using a Windows account assigned to the role you are testing.</span></span>  
  
2.  <span data-ttu-id="79940-143">데이터베이스 폴더를 열고 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-143">Open the Databases folder, and select a database.</span></span> <span data-ttu-id="79940-144">사용 중인 계정이 멤버 자격을 가진 역할에 표시되는 데이터베이스만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-144">You will only see the databases that are visible to the roles for which your account has membership.</span></span>  
  
3.  <span data-ttu-id="79940-145">큐브 또는 차원을 마우스 오른쪽 단추로 클릭하고 **처리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-145">Right-click a cube or dimension and select **Process**.</span></span> <span data-ttu-id="79940-146">처리 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-146">Choose a processing option.</span></span> <span data-ttu-id="79940-147">모든 개체 조합에 대해 모든 옵션을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-147">Test all of the options, for all combinations of objects.</span></span> <span data-ttu-id="79940-148">개체가 누락되어 오류가 발생하는 경우 역할에 개체를 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="79940-148">If errors occur due to missing objects, add the objects to the role.</span></span>  
  
## <a name="set-processing-permissions-on-a-data-mining-structure"></a><span data-ttu-id="79940-149">데이터 마이닝 구조에 대한 처리 권한 설정</span><span class="sxs-lookup"><span data-stu-id="79940-149">Set processing permissions on a data mining structure</span></span>  
 <span data-ttu-id="79940-150">데이터 마이닝 구조를 처리할 수 있는 권한을 부여하는 역할을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-150">You can create a role granting permission to process data mining structures.</span></span> <span data-ttu-id="79940-151">여기에는 모든 마이닝 모델의 처리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="79940-151">This includes the processing of all mining models.</span></span>  
  
 <span data-ttu-id="79940-152">**Drill Through** `Read Definition` 마이닝 모델 및 구조를 검색 하는 데 사용 되는 드릴스루 및 사용 권한은 원자성 이며 동일한 역할에 추가 하거나 다른 역할로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="79940-152">**Drill Through** and `Read Definition` permissions used for browsing a mining model and structure are atomic and can be added to the same role, or separated out into a different role.</span></span>  
  
1.  <span data-ttu-id="79940-153">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스에 연결하고 데이터베이스 폴더를 열고 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-153">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], open the Databases folder, and select a database.</span></span>  
  
2.  <span data-ttu-id="79940-154">**역할**  |  **새 역할**을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-154">Right-click **Roles** | **New Role**.</span></span> <span data-ttu-id="79940-155">이름 및 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-155">Enter a name and description.</span></span> <span data-ttu-id="79940-156">**일반** 창에서 데이터베이스 권한 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-156">In the **General** pane, make sure that the database permission check boxes are clear.</span></span> <span data-ttu-id="79940-157">데이터베이스 권한은 역할 옵션을 회색으로 표시하거나 선택하지 못하도록 설정하여 하위 수준의 개체에 대한 권한을 설정하는 기능을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-157">Database permissions will override the ability to set permissions on lower-level objects by making role options grayed out or un-selectable.</span></span>  
  
3.  <span data-ttu-id="79940-158">**마이닝 구조** 창에서 각 마이닝 구조에 대한 **처리** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-158">In the **Mining Structures** pane, select the **Process** check box for each mining structure.</span></span>  
  
4.  <span data-ttu-id="79940-159">**멤버 자격** 창에서 이 데이터베이스의 모든 개체를 처리할 수 있는 권한을 가진 Windows 사용자 및 그룹 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-159">In the **Membership** pane, add the Windows user and group accounts having permission to process any object in this database.</span></span>  
  
5.  <span data-ttu-id="79940-160">**확인** 을 클릭하여 역할 정의를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="79940-160">Click **OK** to complete the role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79940-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="79940-161">See Also</span></span>  
 <span data-ttu-id="79940-162">[데이터베이스, 테이블 또는 파티션 처리](../tabular-models/process-database-table-or-partition-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="79940-162">[Process Database, Table, or Partition](../tabular-models/process-database-table-or-partition-analysis-services.md) </span></span>  
 <span data-ttu-id="79940-163">[다차원 모델 개체 처리](processing-a-multidimensional-model-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="79940-163">[Multidimensional Model Object Processing](processing-a-multidimensional-model-analysis-services.md) </span></span>  
 <span data-ttu-id="79940-164">[Analysis Services&#41;&#40;데이터베이스 사용 권한 부여](grant-database-permissions-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="79940-164">[Grant database permissions &#40;Analysis Services&#41;](grant-database-permissions-analysis-services.md) </span></span>  
 [<span data-ttu-id="79940-165">개체 메타데이터에 대한 정의 읽기 권한 부여&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="79940-165">Grant read definition permissions on object metadata &#40;Analysis Services&#41;</span></span>](grant-read-definition-permissions-on-object-metadata-analysis-services.md)  
  
  
