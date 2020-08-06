---
title: 파티션 쓰기 저장 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], writeback
- partitions [Analysis Services], write-enabled
- writeback [Analysis Services], partitions
ms.assetid: 38bb09cc-2652-4971-8373-0cf468cdc7a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: eaea005bf919545e5d63be481eb3478b286c16d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651349"
---
# <a name="set-partition-writeback"></a><span data-ttu-id="c8883-102">파티션 쓰기 저장(writeback) 설정</span><span class="sxs-lookup"><span data-stu-id="c8883-102">Set Partition Writeback</span></span>
  <span data-ttu-id="c8883-103">측정값을 쓰기 가능하게 설정하면 최종 사용자가 큐브 데이터를 검색하는 동안 변경할 수 있으며, 변경 내용은 큐브 데이터 또는 원본 데이터가 아닌 쓰기 저장 테이블이라는 별도의 테이블에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-103">If you write-enable a measure group, end users can change cube data while they browse it, where changes are saved in a separate table called a writeback table, not in the cube data or source data.</span></span> <span data-ttu-id="c8883-104">쓰기 가능한 파티션을 검색하는 최종 사용자에게 해당 파티션에 대한 쓰기 저장 테이블의 모든 변경 내용에 대한 최종 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-104">End users who browse a write-enabled partition see the net effect of all changes in the writeback table for the partition.</span></span>  
  
 <span data-ttu-id="c8883-105">쓰기 저장 데이터를 찾아보거나 삭제할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="c8883-105">You can browse or delete writeback data.</span></span> <span data-ttu-id="c8883-106">쓰기 저장 데이터를 파티션으로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-106">You can also convert writeback data to a partition.</span></span> <span data-ttu-id="c8883-107">쓰기 가능한 파티션의 경우 큐브 역할을 사용하여 사용자 및 사용자 그룹에 읽기/쓰기 권한을 부여하고 파티션의 특정 셀 또는 셀 그룹에 대한 액세스를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-107">On a write-enabled partition, you can use cube roles to grant read/write access to users and groups of users, and to limit access to specific cells or groups of cells in the partition.</span></span>  
  
 <span data-ttu-id="c8883-108">쓰기 저장에 대한 간략한 비디오 지침은 [Analysis Services에 대한 Excel 2010 쓰기 저장](https://go.microsoft.com/fwlink/p/?LinkId=394951)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c8883-108">For a short video introduction to writeback, see [Excel 2010 Writeback to Analysis Services](https://go.microsoft.com/fwlink/p/?LinkId=394951).</span></span> <span data-ttu-id="c8883-109">이 기능에 대한 자세한 내용은 블로그 포스트 시리즈인 [Building a Writeback Application with Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977)(Analysis Services를 사용하여 쓰기 저장 애플리케이션 빌드(블로그))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8883-109">A more detailed exploration of this feature is available through this blog post series, [Building a Writeback Application with Analysis Services (blog)](https://go.microsoft.com/fwlink/?LinkId=394977).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c8883-110">쓰기 저장은 SQL Server 관계형 데이터베이스 및 데이터 마트, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 다차원 모델에 대해서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-110">Writeback is supported for SQL Server relational databases and data marts only, and only for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] multidimensional models.</span></span>  
  
## <a name="how-to-write-enable-a-partition"></a><span data-ttu-id="c8883-111">파티션을 쓰기 가능으로 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="c8883-111">How to write-enable a partition</span></span>  
 <span data-ttu-id="c8883-112">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 큐브 디자이너에서 파티션 자체를 쓰기 가능으로 설정하여 파티션의 측정값 그룹을 쓰기 가능하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-112">You can write-enable a partition's measure groups by write-enabling the partition itself in Cube Designer in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="c8883-113">큐브 디자이너의 파티션 탭에서 파티션을 마우스 오른쪽 단추로 클릭하고 **쓰기 저장 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-113">In Cube Designer, in the Partitions tab, right-click a partition and choose **Writeback Settings**.</span></span>  
  
-   <span data-ttu-id="c8883-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 데이터베이스 |큐브| 측정값 그룹을 확장한 다음 **쓰기 저장** 을 마우스 오른쪽 단추로 클릭하고 **쓰기 저장 사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-114">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], expand the database | cube | measure group, and then right-click **Writeback** and choose **Enable Writeback**.</span></span>  
  
 <span data-ttu-id="c8883-115">쓰기 저장은 SUM 집계를 사용하는 측정값에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-115">Writeback is only supported for measures that use the SUM aggregation.</span></span> <span data-ttu-id="c8883-116">AdventureWorks 샘플 데이터베이스에서 Sales Targets 측정값 그룹을 사용하여 쓰기 저장 동작을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-116">In the AdventureWorks sample database, you can use the Sales Targets measure group to test writeback behaviors.</span></span>  
  
 <span data-ttu-id="c8883-117">파티션을 쓰기 가능으로 설정할 때는 쓰기 저장 테이블 저장을 위한 테이블 이름 및 데이터 원본을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-117">When you write-enable a partition, you specify a table name and a data source for storing the write-back table.</span></span> <span data-ttu-id="c8883-118">측정값 그룹에 대한 모든 후속 변경 내용은 이 테이블에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-118">Any subsequent changes to the measure group are recorded in this table.</span></span>  
  
## <a name="browse-writeback-data-in-a-partition"></a><span data-ttu-id="c8883-119">파티션에서 쓰기 저장 데이터 찾아보기</span><span class="sxs-lookup"><span data-stu-id="c8883-119">Browse writeback data in a partition</span></span>  
 <span data-ttu-id="c8883-120">큐브 디자이너의 **파티션** 탭에 있는 쓰기 가능한 파티션을 마우스 오른쪽 단추로 클릭하여 액세스할 수 있는 **데이터 찾아보기** 대화 상자에서 큐브의 쓰기 저장 테이블의 내용을 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-120">You can browse the contents of a cube's writeback table in the **Browse Data** dialog box, which you can access by right-clicking a write-enabled partition on the **Partitions** tab in Cube Designer.</span></span>  
  
## <a name="delete-writeback-data-or-disable-writeback"></a><span data-ttu-id="c8883-121">쓰기 저장 데이터 삭제 또는 쓰기 저장 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="c8883-121">Delete writeback data or disable writeback</span></span>  
 <span data-ttu-id="c8883-122">쓰기 저장 데이터를 삭제하면 쓰기 저장 캐시가 지워지며 해당 데이터를 삭제한 직후부터 추가 쓰기 저장 작업은 백지 상태에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-122">Deleting writeback data clears the writeback cache; as soon as that data is deleted, additional writeback work is performed on a clean slate.</span></span> <span data-ttu-id="c8883-123">큐브 파티션에 대해 쓰기 저장을 해제하면 해당 파티션에 대한 쓰기 저장이 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-123">Disabling writeback for a cube partition simply turns off writeback for that partition.</span></span>  
  
## <a name="convert-writeback-data-to-a-partition"></a><span data-ttu-id="c8883-124">쓰기 저장 데이터를 파티션으로 변환</span><span class="sxs-lookup"><span data-stu-id="c8883-124">Convert writeback data to a partition</span></span>  
 <span data-ttu-id="c8883-125">파티션의 쓰기 저장 테이블에 포함된 데이터를 파티션으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-125">You can convert the data in a partition's writeback table to a partition.</span></span> <span data-ttu-id="c8883-126">이 절차로 인해 쓰기 저장 테이블이 새 파티션의 팩트 테이블이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-126">This procedure causes the writeback table to become the new partition's fact table.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c8883-127">파티션을 잘못 사용하면 정확하지 않은 큐브 데이터가 만들어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-127">Incorrect use of partitions can result in inaccurate cube data.</span></span> <span data-ttu-id="c8883-128">자세한 내용은 [로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8883-128">For more information, see [Create and Manage a Local Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md).</span></span>  
  
 <span data-ttu-id="c8883-129">쓰기 저장 데이터 테이블을 파티션으로 변환하면 파티션이 쓰기 불가능으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-129">Converting the writeback data table to a partition also write-disables the partition.</span></span> <span data-ttu-id="c8883-130">파티션의 셀에 대한 모든 제한 없는 읽기/쓰기 정책 및 읽기/쓰기 권한이 해제되며 최종 사용자는 표시된 큐브 데이터를 변경할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-130">All unrestricted read/write policies and read/write permissions for the partition's cells are disabled, and end users will not be able to change displayed cube data.</span></span> <span data-ttu-id="c8883-131">제한 없는 읽기/쓰기 정책 또는 읽기/쓰기 권한이 해제된 최종 사용자도 큐브를 찾아볼 수는 있습니다. 읽기 권한 및 불확정 읽기 권한은 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-131">(End users with disabled unrestricted read/write policies or disabled read/write permissions will still be able to browse the cube.) Read and read-contingent permissions are not affected.</span></span>  
  
 <span data-ttu-id="c8883-132">쓰기 저장 데이터를 파티션으로 변환하려면 **파티션으로 변환** 대화 상자를 사용합니다. 이 대화 상자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쓰기 가능 파티션에 대한 쓰기 저장 테이블을 마우스 오른쪽 단추로 클릭하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-132">To convert writeback data to a partition, use the **Convert to Partition** dialog box, which is accessed by right-clicking the writeback table for a write-enabled partition in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c8883-133">대화 상자에서 파티션의 이름을 지정하고 파티션에 대한 집계를 파티션을 만들 때 디자인할지, 아니면 나중에 디자인할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-133">You specify a name for the partition and whether to design the aggregation for the partition later or at the same time that you create it.</span></span> <span data-ttu-id="c8883-134">파티션을 선택할 때 집계를 만들려면 기존 파티션에서 집계 디자인을 복사하도록 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-134">To create the aggregation at the same time you choose the partition, you must choose to copy the aggregation design from an existing partition.</span></span> <span data-ttu-id="c8883-135">기존 파티션은 반드시 그런 것은 아니지만 일반적으로 현재 쓰기 저장 파티션입니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-135">This is normally, but not necessarily, the current writeback partition.</span></span> <span data-ttu-id="c8883-136">파티션을 만들 때 해당 파티션을 처리하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8883-136">You can also choose to process the partition at the same time that you create it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8883-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c8883-137">See Also</span></span>  
 <span data-ttu-id="c8883-138">[쓰기 가능 파티션](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span><span class="sxs-lookup"><span data-stu-id="c8883-138">[Write-Enabled Partitions](../multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions.md) </span></span>  
 <span data-ttu-id="c8883-139">[Excel 2010의 셀 수준에서 OLAP 큐브에 쓰기 다시 쓰기 설정](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span><span class="sxs-lookup"><span data-stu-id="c8883-139">[Enabling Write-back to an OLAP Cube at Cell Level in Excel 2010](https://go.microsoft.com/fwlink/p/?LinkId=394952) </span></span>  
 [<span data-ttu-id="c8883-140">Analysis Services 쓰기 저장으로 데이터 엔트리 활성화 및 보안</span><span class="sxs-lookup"><span data-stu-id="c8883-140">Enabling and Securing Data Entry with Analysis Services Writeback</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=394953)  
  
  
