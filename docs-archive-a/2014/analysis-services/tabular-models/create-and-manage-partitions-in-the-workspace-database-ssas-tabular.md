---
title: 작업 영역 데이터베이스에서 파티션 만들기 및 관리 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3824dd4763e516dc5e8e34a9ec815d3969f4eb79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649205"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a><span data-ttu-id="66641-102">작업 영역 데이터베이스에서 파티션 만들기 및 관리(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="66641-102">Create and Manage Partitions in the Workspace Database (SSAS Tabular)</span></span>
  <span data-ttu-id="66641-103">파티션은 테이블을 논리적 부분으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="66641-103">Partitions divide a table into logical parts.</span></span> <span data-ttu-id="66641-104">각 파티션은 다른 파티션에 독립적으로 또는 병렬로 처리(새로 고침)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-104">Each partition can then be processed (Refreshed) independently or in parallel with other partitions.</span></span> <span data-ttu-id="66641-105">파티션은 확장성 및 대형 데이터베이스의 관리 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-105">Partitions can improve scalability and manageability of large databases.</span></span> <span data-ttu-id="66641-106">기본적으로 각 테이블에는 모든 열을 포함하는 파티션이 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-106">By default, each table has one partition that includes all columns.</span></span> <span data-ttu-id="66641-107">이 항목의 태스크에서는의 **파티션 관리자** 대화 상자를 사용 하 여 모델 작업 영역 데이터베이스에서 파티션을 만들고 관리 하는 방법에 대해 설명 합니다.[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66641-107">Tasks in this topic describe how to create and manage partitions in the model workspace database by using the **Partition Manager** dialog box in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]</span></span>  
  
 <span data-ttu-id="66641-108">다른 Analysis Services 인스턴스로 모델을 배포한 후 데이터베이스 관리자는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 (배포된) 모델에서 파티션을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-108">After a model has been deployed to another Analysis Services instance, database administrators can create and manage partitions in the (deployed) model by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="66641-109">자세한 내용은 [테이블 형식 모델 파티션 만들기 및 관리&#40;SSAS 테이블 형식&#41;](partitions-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66641-109">For more information, see [Create and Manage Tabular Model Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="66641-110">이 항목에는 다음 태스크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="66641-110">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="66641-111">새 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="66641-111">To create a new partition</span></span>](#bkmk_create_new)  
  
-   [<span data-ttu-id="66641-112">파티션을 복사하려면</span><span class="sxs-lookup"><span data-stu-id="66641-112">To copy a partition</span></span>](#bkmk_copy)  
  
-   [<span data-ttu-id="66641-113">파티션을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="66641-113">To delete a partition</span></span>](#bkmk_delete)  
  
> [!NOTE]  
>  <span data-ttu-id="66641-114">파티션 관리자 대화 상자를 사용하여 모델 작업 영역 데이터베이스에서 파티션을 병합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-114">You cannot merge partitions in the model workspace database by using the Partition Manager dialog box.</span></span> <span data-ttu-id="66641-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]만을 사용하여 배포된 모델에서 파티션을 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-115">Partitions can be merged in a deployed model only by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="66641-116">작업</span><span class="sxs-lookup"><span data-stu-id="66641-116">Tasks</span></span>  
 <span data-ttu-id="66641-117">파티션을 만들고 관리하려면 **파티션 관리자** 대화 상자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-117">To create and manage partitions, you will use the **Partitions Manager** dialog box.</span></span> <span data-ttu-id="66641-118">**파티션 관리자** 대화 상자를 확인하려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **테이블** 메뉴를 클릭한 다음 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-118">To view the **Partitions Manager** dialog box, in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Table** menu, and then click **Partitions**.</span></span>  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a><span data-ttu-id="66641-119">새 파티션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="66641-119">To create a new partition</span></span>  
  
1.  <span data-ttu-id="66641-120">모델 디자이너에서 파티션을 정의할 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-120">In the model designer, select the table for which you want to define a partition.</span></span>  
  
2.  <span data-ttu-id="66641-121">**테이블** 메뉴를 클릭한 다음 **파티션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-121">Click on the **Table** menu, and then click **Partitions**.</span></span>  
  
3.  <span data-ttu-id="66641-122">**파티션 관리자**의 **테이블** 목록 상자에서 분할할 테이블을 확인 또는 선택한 다음 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-122">In **Partition Manager**, in the **Table** listbox, verify or select the table you want to partition, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="66641-123">**파티션 이름**에 파티션의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-123">In **Partition Name**, type a name for the partition.</span></span> <span data-ttu-id="66641-124">기본적으로 기본 파티션의 이름은 새 파티션마다 증분 번호로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="66641-124">By default, the name of the default partition will be incrementally numbered for each new partition.</span></span>  
  
5.  <span data-ttu-id="66641-125">테이블 미리 보기 모드 또는 쿼리 편집기 모드를 사용하여 생성한 SQL 쿼리를 사용해 파티션에 포함할 행과 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-125">You can select the rows and columns to be included in the partition by using Table Preview mode or by using a SQL query created using Query Editor mode.</span></span>  
  
     <span data-ttu-id="66641-126">테이블 미리 보기 모드(기본값)를 사용하려면 미리 보기 창의 오른쪽 위에 있는 **테이블 미리 보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-126">To use Table Preview mode (default), click the **Table Preview** button near the upper-right corner of the preview window.</span></span> <span data-ttu-id="66641-127">열 이름 옆에 있는 확인란을 선택하여 파티션에 포함할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-127">Select the columns you want to include in the partition by selecting the checkbox next to the column name.</span></span> <span data-ttu-id="66641-128">행을 필터링하려면 셀 값을 마우스 오른쪽 단추로 클릭하고 **선택한 셀 값으로 필터링**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-128">To filter rows, right click a cell value, and click **Filter by Selected Cell Value**.</span></span>  
  
     <span data-ttu-id="66641-129">SQL 문을 사용하려면 미리 보기 창의 오른쪽 위에 있는 **쿼리 편집기** 단추를 클릭한 다음 SQL 쿼리 문을 쿼리 창에 입력하거나 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="66641-129">To use a SQL statement, click the **Query Editor** button near the upper-right corner of the preview window, then type or paste a SQL query statement into the query window.</span></span> <span data-ttu-id="66641-130">문의 유효성을 검사하려면 **유효성 검사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-130">To validate your statement, click **Validate**.</span></span> <span data-ttu-id="66641-131">쿼리 디자이너를 사용하려면 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-131">To use the Query Designer, click **Design**.</span></span>  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a><span data-ttu-id="66641-132">파티션을 복사 하려면</span><span class="sxs-lookup"><span data-stu-id="66641-132">To copy a partition</span></span>  
  
1.  <span data-ttu-id="66641-133">**파티션 관리자**의 **테이블** 목록 상자에서 복사할 파티션을 포함하는 테이블을 확인 또는 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-133">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to copy.</span></span>  
  
2.  <span data-ttu-id="66641-134">**파티션** 목록에서 복사할 파티션을 선택한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-134">In the **Partitions** list, select the partition you want to copy and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="66641-135">**파티션 이름**에 파티션의 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-135">In **Partition Name**, type a new name for the partition.</span></span>  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a><span data-ttu-id="66641-136">파티션을 삭제 하려면</span><span class="sxs-lookup"><span data-stu-id="66641-136">To delete a partition</span></span>  
  
1.  <span data-ttu-id="66641-137">**파티션 관리자**의 **테이블** 목록 상자에서 삭제할 파티션을 포함하는 테이블을 확인 또는 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-137">In **Partition Manager**, in the **Table** listbox, verify or select the table that contains the partition you want to delete.</span></span>  
  
2.  <span data-ttu-id="66641-138">**파티션** 목록에서 삭제할 파티션을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66641-138">In the **Partitions** list, select the partition you want to delete and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66641-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66641-139">See Also</span></span>  
 <span data-ttu-id="66641-140">[SSAS 테이블 형식&#41;&#40;파티션](partitions-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="66641-140">[Partitions &#40;SSAS Tabular&#41;](partitions-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="66641-141">SSAS 테이블 형식&#41;&#40;작업 영역 데이터베이스에서 파티션 처리</span><span class="sxs-lookup"><span data-stu-id="66641-141">Process Partitions in the Workspace Database &#40;SSAS Tabular&#41;</span></span>](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
