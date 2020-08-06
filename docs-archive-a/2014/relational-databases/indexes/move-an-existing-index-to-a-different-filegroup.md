---
title: 다른 파일 그룹으로 기존 인덱스 이동 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- moving tables
- switching filegroups for index
- moving indexes
- indexes [SQL Server], moving
- filegroups [SQL Server], switching
ms.assetid: 167ebe77-487d-4ca8-9452-4b2c7d5cb96e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c99847dcb8d4d65272dd3660c7fd60d3efb8d951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660559"
---
# <a name="move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="5a945-102">다른 파일 그룹으로 기존 인덱스 이동</span><span class="sxs-lookup"><span data-stu-id="5a945-102">Move an Existing Index to a Different Filegroup</span></span>
  <span data-ttu-id="5a945-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 현재 파일 그룹에서 다른 파일 그룹으로 기존 인덱스를 이동하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-103">This topic describes how to move an existing index from its current filegroup to a different filegroup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="5a945-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="5a945-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="5a945-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="5a945-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="5a945-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5a945-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="5a945-107">보안</span><span class="sxs-lookup"><span data-stu-id="5a945-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="5a945-108">**기존 인덱스를 다른 파일 그룹으로 이동하려면**</span><span class="sxs-lookup"><span data-stu-id="5a945-108">**To move an existing index to a different filegroup, using:**</span></span>  
  
     [<span data-ttu-id="5a945-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="5a945-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="5a945-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="5a945-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="5a945-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="5a945-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="5a945-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5a945-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="5a945-113">테이블에 클러스터형 인덱스가 있는 경우 클러스터형 인덱스를 새 파일 그룹으로 이동하면 테이블도 해당 파일 그룹으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-113">If a table has a clustered index, moving the clustered index to a new filegroup moves the table to that filegroup.</span></span>  
  
-   <span data-ttu-id="5a945-114">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]에서 UNIQUE 또는 PRIMARY KEY 제약 조건을 사용하여 만든 인덱스를 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-114">You cannot move indexes created using a UNIQUE or PRIMARY KEY constraint using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="5a945-115">이러한 인덱스를 이동하려면 [에서](/sql/t-sql/statements/create-index-transact-sql) CREATE INDEX [!INCLUDE[tsql](../../includes/tsql-md.md)]문을 (DROP_EXISTING=ON) 옵션과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-115">To move these indexes use the [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) statement with the (DROP_EXISTING=ON) option in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="5a945-116">보안</span><span class="sxs-lookup"><span data-stu-id="5a945-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="5a945-117">권한</span><span class="sxs-lookup"><span data-stu-id="5a945-117">Permissions</span></span>  
 <span data-ttu-id="5a945-118">테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-118">Requires ALTER permission on the table or view.</span></span> <span data-ttu-id="5a945-119">사용자는 **sysadmin** 고정 서버 역할의 멤버 또는 **db_ddladmin** 및 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-119">User must be a member of the **sysadmin** fixed server role or the **db_ddladmin** and **db_owner** fixed database roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="5a945-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="5a945-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-using-table-designer"></a><span data-ttu-id="5a945-121">테이블 디자이너를 사용하여 기존 인덱스를 다른 파일 그룹으로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="5a945-121">To move an existing index to a different filegroup using Table Designer</span></span>  
  
1.  <span data-ttu-id="5a945-122">개체 탐색기에서 더하기 기호를 클릭하여 이동할 인덱스가 포함된 테이블이 있는 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-122">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="5a945-123">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-123">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="5a945-124">이동할 인덱스가 포함된 테이블을 마우스 오른쪽 단추로 클릭하고 **디자인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-124">Right-click the table containing the index that you want to move and select **Design**.</span></span>  
  
4.  <span data-ttu-id="5a945-125">**테이블 디자이너** 메뉴에서 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-125">On the **Table Designer** menu, click **Indexes/Keys**.</span></span>  
  
5.  <span data-ttu-id="5a945-126">이동할 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-126">Select the index that you want to move.</span></span>  
  
6.  <span data-ttu-id="5a945-127">주 표에서 **데이터 공간 사양**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-127">In the main grid, expand **Data Space Specification**.</span></span>  
  
7.  <span data-ttu-id="5a945-128">**파일 그룹 또는 파티션 구성표 이름** 을 선택하고 목록에서 인덱스를 이동할 파일 그룹 또는 파티션 구성표를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-128">Select **Filegroup or Partition Scheme Name** and select from the list the filegroup or partition scheme to where you want to move the index.</span></span>  
  
8.  <span data-ttu-id="5a945-129">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-129">Click **Close**.</span></span>  
  
9. <span data-ttu-id="5a945-130">**파일** 메뉴에서 _table_name_**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-130">On the **File** menu, select **Save**_table_name_.</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup-in-object-explorer"></a><span data-ttu-id="5a945-131">개체 탐색기에서 기존 인덱스를 다른 파일 그룹으로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="5a945-131">To move an existing index to a different filegroup in Object Explorer</span></span>  
  
1.  <span data-ttu-id="5a945-132">개체 탐색기에서 더하기 기호를 클릭하여 이동할 인덱스가 포함된 테이블이 있는 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-132">In Object Explorer, click the plus sign to expand the database that contains the table containing the index that you want to move.</span></span>  
  
2.  <span data-ttu-id="5a945-133">더하기 기호를 클릭하여 **테이블** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-133">Click the plus sign to expand the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="5a945-134">더하기 기호를 클릭하여 이동할 인덱스가 포함된 테이블을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-134">Click the plus sign to expand the table containing the index that you want to move.</span></span>  
  
4.  <span data-ttu-id="5a945-135">더하기 기호를 클릭하여 **인덱스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-135">Click the plus sign to expand the **Indexes** folder.</span></span>  
  
5.  <span data-ttu-id="5a945-136">이동할 인덱스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-136">Right-click the index that you want to move and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="5a945-137">**페이지 선택**아래에서 **스토리지**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-137">Under **Select a page**, select **Storage**.</span></span>  
  
7.  <span data-ttu-id="5a945-138">인덱스를 이동할 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-138">Select the filegroup in which to move the index.</span></span>  
  
     <span data-ttu-id="5a945-139">테이블 또는 인덱스가 분할된 경우 인덱스를 이동할 파티션 구성표를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-139">If the table or index is partitioned, select the partition scheme in which to move the index.</span></span> <span data-ttu-id="5a945-140">분할된 인덱스에 대한 자세한 내용은 [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a945-140">For more information about partitioned indexes, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
     <span data-ttu-id="5a945-141">클러스터형 인덱스를 이동할 경우 온라인 처리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-141">If you are moving a clustered index, you can use online processing.</span></span> <span data-ttu-id="5a945-142">온라인 처리는 인덱스 작업 중 기본 데이터 및 비클러스터형 인덱스에 대한 동시 사용자 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-142">Online processing allows concurrent user access to the underlying data and to nonclustered indexes during the index operation.</span></span> <span data-ttu-id="5a945-143">자세한 내용은 [Perform Index Operations Online](perform-index-operations-online.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a945-143">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
     <span data-ttu-id="5a945-144">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 사용하는 다중 프로세서 컴퓨터에서는 최대 병렬 처리 값을 지정하여 인덱스 문 실행에 사용되는 프로세서 수를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-144">On multiprocessor computers using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can configure the number of processors used to execute the index statement by specifying a maximum degree of parallelism value.</span></span> <span data-ttu-id="5a945-145">병렬 인덱스 작업 기능은 일부 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-145">The Parallel indexed operations feature is not available in every edition of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5a945-146">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a945-146">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span> <span data-ttu-id="5a945-147">병렬 인덱스 작업에 대한 자세한 내용은 [병렬 인덱스 작업 구성](configure-parallel-index-operations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a945-147">For more information about Parallel indexed operations, see [Configure Parallel Index Operations](configure-parallel-index-operations.md).</span></span>  
  
8.  <span data-ttu-id="5a945-148">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-148">Click **OK**.</span></span>  
  
 <span data-ttu-id="5a945-149">**인덱스 속성 –** **index_name** 대화 상자의 _스토리지_ 페이지에서 다음 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-149">The following information is available on the **Storage** page of the **Index Properties -** _index_name_ dialog box:</span></span>  
  
 <span data-ttu-id="5a945-150">**파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="5a945-150">**Filegroup**</span></span>  
 <span data-ttu-id="5a945-151">지정한 파일 그룹에 인덱스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-151">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="5a945-152">목록에는 표준(행) 파일 그룹만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-152">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="5a945-153">목록에서는 기본적으로 데이터베이스의 PRIMARY 파일 그룹이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-153">The default list selection is the PRIMARY filegroup of the database.</span></span>  
  
 <span data-ttu-id="5a945-154">**Filestream 파일 그룹**</span><span class="sxs-lookup"><span data-stu-id="5a945-154">**Filestream filegroup**</span></span>  
 <span data-ttu-id="5a945-155">FILESTREAM 데이터의 파일 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-155">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="5a945-156">이 목록에는 FILESTREAM 파일 그룹만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-156">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="5a945-157">목록에서는 기본적으로 PRIMARY FILESTREAM 파일 그룹이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-157">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span>  
  
 <span data-ttu-id="5a945-158">**파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="5a945-158">**Partition scheme**</span></span>  
 <span data-ttu-id="5a945-159">파티션 구성표에 인덱스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-159">Stores the index in a partition scheme.</span></span> <span data-ttu-id="5a945-160">**파티션 구성표** 를 클릭하면 아래의 표가 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-160">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="5a945-161">목록에서는 기본적으로 테이블 데이터를 저장하는 데 사용되는 파티션 구성표가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-161">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="5a945-162">목록에서 다른 파티션 구성표를 선택하면 표의 정보가 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-162">When you select a different partition scheme in the list, the information in the grid is updated.</span></span>  
  
 <span data-ttu-id="5a945-163">데이터베이스에 파티션 구성표가 없으면 파티션 구성표 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-163">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="5a945-164">**Filestream 파티션 구성표**</span><span class="sxs-lookup"><span data-stu-id="5a945-164">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="5a945-165">FILESTREAM 데이터의 파티션 구성표를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-165">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="5a945-166">이 파티션 구성표는 **파티션 구성표** 옵션에서 지정한 구성표와 대칭이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-166">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="5a945-167">테이블이 분할되지 않은 경우 이 필드가 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-167">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="5a945-168">**파티션 구성표 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="5a945-168">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="5a945-169">파티션 구성표에 포함되는 열의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-169">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="5a945-170">**테이블 열**</span><span class="sxs-lookup"><span data-stu-id="5a945-170">**Table Column**</span></span>  
 <span data-ttu-id="5a945-171">파티션 구성표에 매핑할 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-171">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="5a945-172">**열 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="5a945-172">**Column Data Type**</span></span>  
 <span data-ttu-id="5a945-173">열의 데이터 형식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-173">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a945-174">테이블 열이 계산 열이면 **열 데이터 형식** 에 "계산 열"이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-174">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="5a945-175">**인덱스를 이동하는 동안 DML 문의 온라인 처리 허용**</span><span class="sxs-lookup"><span data-stu-id="5a945-175">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="5a945-176">이 옵션을 사용하면 사용자는 인덱스 작업 중에 기본 테이블이나 클러스터형 인덱스 데이터 및 연관된 모든 비클러스터형 인덱스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-176">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a945-177">이 옵션은 XML 인덱스에 대해서는 사용할 수 없으며 인덱스가 비활성화된 클러스터형 인덱스인 경우에도 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-177">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="5a945-178">**최대 병렬 처리 수준 설정**</span><span class="sxs-lookup"><span data-stu-id="5a945-178">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="5a945-179">병렬 계획 실행 중 사용할 프로세서 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-179">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="5a945-180">기본값인 0으로 설정하면 사용 가능한 실제 CPU 수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-180">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="5a945-181">값을 1로 설정하면 병렬 계획이 생성되지 않습니다. 값을 1보다 큰 값으로 설정하면 단일 쿼리 실행에서 사용하는 최대 프로세서 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-181">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="5a945-182">이 옵션은 대화 상자가 **다시 작성** 또는 **다시 만들기** 상태에 있을 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-182">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a945-183">사용 가능한 CPU 수보다 더 큰 수를 지정하면 사용 가능한 실제 CPU 수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-183">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="5a945-184">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="5a945-184">Using Transact-SQL</span></span>  
  
#### <a name="to-move-an-existing-index-to-a-different-filegroup"></a><span data-ttu-id="5a945-185">기존 인덱스를 다른 파일 그룹으로 이동하려면</span><span class="sxs-lookup"><span data-stu-id="5a945-185">To move an existing index to a different filegroup</span></span>  
  
1.  <span data-ttu-id="5a945-186">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-186">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="5a945-187">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-187">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="5a945-188">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a945-188">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Creates the TransactionsFG1 filegroup on the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP TransactionsFG1;  
    GO  
    /* Adds the TransactionsFG1dat3 file to the TransactionsFG1 filegroup. Please note that you will have to change the filename parameter in this statement to execute it without errors.  
    */  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = TransactionsFG1dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\TransactionsFG1dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP TransactionsFG1;  
    GO  
    /*Creates the IX_Employee_OrganizationLevel_OrganizationNode index  
      on the TransactionsPS1 filegroup and drops the original IX_Employee_OrganizationLevel_OrganizationNode index.  
    */  
    CREATE NONCLUSTERED INDEX IX_Employee_OrganizationLevel_OrganizationNode  
        ON HumanResources.Employee (OrganizationLevel, OrganizationNode)  
        WITH (DROP_EXISTING = ON)  
        ON TransactionsFG1;  
    GO  
    ```  
  
 <span data-ttu-id="5a945-189">자세한 내용은 [CREATE INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a945-189">For more information, see [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).</span></span>  
  
  
