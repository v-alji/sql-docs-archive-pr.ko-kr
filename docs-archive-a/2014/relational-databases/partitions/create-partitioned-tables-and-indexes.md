---
title: 분할된 테이블 및 인덱스 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.createpartition.partitionscheme.f1
- sql12.swb.createpartition.selectoutput.f1
- sql12.swb.createpartition.finish.f1
- sql12.swb.createpartition.summary.f1
- sql12.swb.createpartition.mappartition.f1
- sql12.swb.createpartition.partitioncolumn.f1
- sql12.swb.createpartition.progress.f1
- sql12.swb.createpartition.createjob.f1
- sql12.swb.createpartition.getstart.f1
- sql12.swb.createpartition.partitionfunction.f1
helpviewer_keywords:
- partitioned indexes [SQL Server], creating
- partition schemes [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], creating
- partition functions [SQL Server]
- partition schemes [SQL Server]
ms.assetid: 7641df10-1921-42a7-ba6e-4cb03b3ba9c8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 76ccd8b784902f8542f06f3823e5f8dcb78e9201
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649504"
---
# <a name="create-partitioned-tables-and-indexes"></a><span data-ttu-id="1e181-102">분할된 테이블 및 인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="1e181-102">Create Partitioned Tables and Indexes</span></span>
  <span data-ttu-id="1e181-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 분할된 테이블 또는 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-103">You can create a partitioned table or index in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="1e181-104">분할된 테이블 및 인덱스에 있는 데이터는 데이터베이스의 여러 파일 그룹에 분산할 수 있는 가로로 구분된 단위로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-104">The data in partitioned tables and indexes is horizontally divided into units that can be spread across more than one filegroup in a database.</span></span> <span data-ttu-id="1e181-105">큰 테이블과 인덱스를 분할하면 더 효율적으로 관리 및 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-105">Partitioning can make large tables and indexes more manageable and scalable.</span></span>  
  
 <span data-ttu-id="1e181-106">분할된 테이블 또는 인덱스를 만드는 과정은 대개 다음 네 단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-106">Creating a partitioned table or index typically happens in four parts:</span></span>  
  
1.  <span data-ttu-id="1e181-107">파티션 구성표에서 지정한 파티션을 보유할 파일 그룹 및 해당 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-107">Create a filegroup or filegroups and corresponding files that will hold the partitions specified by the partition scheme.</span></span>  
  
2.  <span data-ttu-id="1e181-108">지정된 열 값을 기반으로 테이블 또는 인덱스의 행을 파티션에 매핑하는 파티션 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-108">Create a partition function that maps the rows of a table or index into partitions based on the values of a specified column.</span></span>  
  
3.  <span data-ttu-id="1e181-109">분할된 테이블 또는 인덱스의 파티션을 새 파일 그룹에 매핑하는 파티션 구성표를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-109">Create a partition scheme that maps the partitions of a partitioned table or index to the new filegroups.</span></span>  
  
4.  <span data-ttu-id="1e181-110">테이블 또는 인덱스를 만들거나 수정하고 파티션 구성표를 스토리지 위치로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-110">Create or modify a table or index and specify the partition scheme as the storage location.</span></span>  
  
 <span data-ttu-id="1e181-111">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1e181-111">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1e181-112">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1e181-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1e181-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1e181-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1e181-114">보안</span><span class="sxs-lookup"><span data-stu-id="1e181-114">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1e181-115">**분할된 테이블 또는 인덱스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="1e181-115">**To create a partitioned table or index, using:**</span></span>  
  
     [<span data-ttu-id="1e181-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e181-116">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1e181-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e181-117">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1e181-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1e181-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1e181-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1e181-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1e181-120">파티션 함수 및 구성표의 범위는 해당 함수 및 구성표가 만들어진 데이터베이스로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-120">The scope of a partition function and scheme is limited to the database in which they have been created.</span></span> <span data-ttu-id="1e181-121">데이터베이스 내에서 파티션 함수는 다른 함수와 서로 다른 네임스페이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-121">Within the database, partition functions reside in a separate namespace from other functions.</span></span>  
  
-   <span data-ttu-id="1e181-122">파티션 함수 내부의 행에 값이 null인 분할 열이 있으면 이러한 행은 가장 왼쪽의 파티션에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-122">If any rows within a partition function have partitioning columns with null values, these rows are allocated to the left-most partition.</span></span> <span data-ttu-id="1e181-123">하지만 NULL이 경계 값으로 지정되고 RIGHT가 지정된 경우에는 맨 왼쪽 파티션이 빈 상태로 유지되고 NULL 값이 두 번째 파티션에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-123">However, if NULL is specified as a boundary value and RIGHT is indicated, the left-most partition remains empty and NULL values are placed in the second partition.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1e181-124">보안</span><span class="sxs-lookup"><span data-stu-id="1e181-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1e181-125">권한</span><span class="sxs-lookup"><span data-stu-id="1e181-125">Permissions</span></span>  
 <span data-ttu-id="1e181-126">분할된 테이블을 만들려면 데이터베이스에는 CREATE TABLE 권한이 필요하고 테이블을 만들 구성표에 대해서는 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-126">Creating a partitioned table requires CREATE TABLE permission in the database and ALTER permission on the schema in which the table is being created.</span></span> <span data-ttu-id="1e181-127">분할된 인덱스를 만들려면 인덱스를 만들 테이블이나 뷰에 대한 ALTER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-127">Creating a partitioned index requires ALTER permission on the table or view where the index is being created.</span></span> <span data-ttu-id="1e181-128">분할된 테이블 또는 인덱스를 만들려면 다음과 같은 추가 권한 중 하나가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-128">Creating either a partitioned table or index requires any one of the following additional permissions:</span></span>  
  
-   <span data-ttu-id="1e181-129">ALTER ANY DATASPACE 권한.</span><span class="sxs-lookup"><span data-stu-id="1e181-129">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="1e181-130">이 권한은 기본적으로 **sysadmin** 고정 서버 역할 및 **db_owner** 및 **db_ddladmin** 고정 데이터베이스 역할의 멤버에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-130">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="1e181-131">파티션 함수 및 파티션 구성표를 만들 데이터베이스에 대한 CONTROL 또는 ALTER 권한</span><span class="sxs-lookup"><span data-stu-id="1e181-131">CONTROL or ALTER permission on the database in which the partition function and partition scheme are being created.</span></span>  
  
-   <span data-ttu-id="1e181-132">파티션 함수 및 파티션 구성표를 만들 데이터베이스의 서버에 대한 CONTROL SERVER 또는 ALTER ANY DATABASE 권한</span><span class="sxs-lookup"><span data-stu-id="1e181-132">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function and partition scheme are being created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1e181-133">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1e181-133">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1e181-134">이 절차의 단계를 수행하여 하나 이상의 파일 그룹, 해당 파일 및 테이블을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-134">Follow the steps in this procedure to create one or more filegroups, corresponding files, and a table.</span></span> <span data-ttu-id="1e181-135">다음 절차에서 분할된 테이블을 만들 때 이 개체를 참조하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-135">You will reference these objects in the next procedure when you create the partitioned table.</span></span>  
  
#### <a name="to-create-new-filegroups-for-a-partitioned-table"></a><span data-ttu-id="1e181-136">분할된 테이블에 대한 새 파일 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1e181-136">To create new filegroups for a partitioned table</span></span>  
  
1.  <span data-ttu-id="1e181-137">개체 탐색기에서 분할된 테이블을 만들 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-137">In Object Explorer, right-click the database in which you want to create a partitioned table and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1e181-138">**데이터베이스 속성 –** *database_name* 대화 상자의 **페이지 선택**에서 **파일 그룹**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-138">In the **Database Properties -** *database_name* dialog box, under **Select a page**, select **Filegroups**.</span></span>  
  
3.  <span data-ttu-id="1e181-139">**행**아래에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-139">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="1e181-140">새 행에 파일 그룹 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-140">In the new row, enter the filegroup name.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="1e181-141">파티션을 만들 경우 경계 값에 대해 지정된 수의 파일 그룹보다 파일 그룹이 한 개 더 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-141">You must always have one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
4.  <span data-ttu-id="1e181-142">분할된 테이블에 대한 파일 그룹을 모두 만들 때까지 계속하여 행을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-142">Continue adding rows until you have created all of the filegroups for the partitioned table.</span></span>  
  
5.  <span data-ttu-id="1e181-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-143">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="1e181-144">**페이지 선택**아래에서 **파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-144">Under **Select a page**, select **Files**.</span></span>  
  
7.  <span data-ttu-id="1e181-145">**행**아래에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-145">Under **Rows**, click **Add**.</span></span> <span data-ttu-id="1e181-146">새 행에 파일 이름을 입력하고 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-146">In the new row, enter a filename and select a filegroup.</span></span>  
  
8.  <span data-ttu-id="1e181-147">각 파일 그룹에 대해 하나 이상의 파일을 만들 때까지 계속하여 행을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-147">Continue adding rows until you have created at least one file for each filegroup.</span></span>  
  
9. <span data-ttu-id="1e181-148">**테이블** 폴더를 확장하고 일반적인 방식으로 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-148">Expand the **Tables** folder and create a table as you normally would.</span></span> <span data-ttu-id="1e181-149">자세한 내용은 [테이블 만들기&#40;데이터베이스 엔진&#41;](../tables/create-tables-database-engine.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e181-149">For more information, see [Create Tables &#40;Database Engine&#41;](../tables/create-tables-database-engine.md).</span></span> <span data-ttu-id="1e181-150">또는 다음 절차에서 기존 테이블을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-150">Alternatively, you can specify an existing table in the next procedure.</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="1e181-151">분할된 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1e181-151">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="1e181-152">분할하려는 테이블을 마우스 오른쪽 단추로 클릭하고 **스토리지**를 가리킨 다음, **파티션 만들기...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-152">Right-click the table that you wish to partition, point to **Storage**, and then click **Create Partition...**.</span></span>  
  
2.  <span data-ttu-id="1e181-153">**파티션 작성 마법사**의 **파티션 작성 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-153">In the **Create Partition Wizard**, on the **Welcome to the Create Partition Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="1e181-154">**분할 열 선택** 페이지의 **사용 가능한 분할 열** 표에서 테이블을 분할할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-154">On the **Select a Partitioning Column** page, in the **Available partitioning columns** grid, select the column on which you want to partition your table.</span></span> <span data-ttu-id="1e181-155">데이터를 분할하는 데 사용할 수 있는 데이터 형식을 가진 열만 **사용 가능한 분할 열** 표에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-155">Only columns with data types that can be used to partition data will be displayed in the **Available partitioning columns** grid.</span></span> <span data-ttu-id="1e181-156">계산 열을 분할 열로 선택하면 해당 열은 지속형 열로 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-156">If you select a computed column as the partitioning column, the column must be designated as a persisted column.</span></span>  
  
     <span data-ttu-id="1e181-157">분할 열과 값 범위를 선택할 때는 논리적 방법으로 데이터를 그룹화할 수 있는 정도를 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-157">The choices you have for the partitioning column and the values range are determined primarily by the extent to which your data can be grouped in a logical way.</span></span> <span data-ttu-id="1e181-158">예를 들어 월 또는 연도의 분기에 따라 논리적 그룹으로 데이터를 분할하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-158">For example, you may choose to divide your data into logical groupings by months or quarters of a year.</span></span> <span data-ttu-id="1e181-159">데이터에 대해 만들게 될 쿼리에 따라 이 논리적 그룹이 테이블 파티션을 관리하기에 충분한지 여부가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-159">The queries you plan to make against your data will determine whether this logical grouping is adequate for managing your table partitions.</span></span> <span data-ttu-id="1e181-160">`text`, `ntext`, `image`, `xml`, `timestamp`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, 별칭 데이터 형식 또는 CLR 사용자 정의 데이터 형식을 제외한 모든 데이터 형식을 분할 열로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-160">All data types are valid for use as partitioning columns, except `text`, `ntext`, `image`, `xml`, `timestamp`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, alias data types, or CLR user-defined data types.</span></span>  
  
     <span data-ttu-id="1e181-161">이 페이지에서는 다음과 같은 옵션을 추가로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-161">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="1e181-162">**선택한 분할된 테이블에 맞춰 이 테이블 배치**</span><span class="sxs-lookup"><span data-stu-id="1e181-162">**Collocate this table to the selected partitioned table**</span></span>  
     <span data-ttu-id="1e181-163">이 옵션을 선택하면 분할 열에서 이 테이블과 조인할 관련 데이터가 포함된 분할된 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-163">Allows you to select a partitioned table that contains related data to join with this table on the partitioning column.</span></span> <span data-ttu-id="1e181-164">분할 열에서 조인된 파티션이 있는 테이블의 쿼리는 일반적으로 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-164">Tables with partitions joined on the partitioning columns are typically queried more efficiently.</span></span>  
  
     <span data-ttu-id="1e181-165">**인덱싱된 파티션 열이 있는 고유하지 않은 인덱스 및 고유한 인덱스를 스토리지에 정렬**</span><span class="sxs-lookup"><span data-stu-id="1e181-165">**Storage-align non-unique indexes and unique indexes with an indexed partition column**</span></span>  
     <span data-ttu-id="1e181-166">동일한 파티션 구성표를 사용하여 분할된 테이블의 모든 인덱스를 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-166">Aligns all indexes of the table that are partitioned with the same partition scheme.</span></span> <span data-ttu-id="1e181-167">테이블과 해당 인덱스가 정렬되면 데이터가 동일한 알고리즘으로 분할되므로 분할된 테이블의 안팎으로 보다 효율적으로 파티션을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-167">When a table and its indexes are aligned, you can move partitions in and out of partitioned tables more effectively, because your data is partitioned with the same algorithm.</span></span>  
  
     <span data-ttu-id="1e181-168">분할 열 및 기타 옵션을 선택한 후 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-168">After selecting the partitioning column and any other options, click **Next**.</span></span>  
  
4.  <span data-ttu-id="1e181-169">**파티션 함수 선택** 페이지의 **파티션 함수 선택**에서 **새 파티션 함수** 또는 **기존 파티션 함수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-169">On the **Select a Partition Function** page, under **Select partition function**, click either **New partition function** or **Existing partition function**.</span></span> <span data-ttu-id="1e181-170">**새 파티션 함수**를 선택하는 경우 함수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-170">If you choose **New partition function**, enter the name of the function.</span></span> <span data-ttu-id="1e181-171">**기존 파티션 함수**를 선택하는 경우 사용하려는 함수 이름을 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-171">If you choose **Existing partition function**, select the name of the function you'd like to use from the list.</span></span> <span data-ttu-id="1e181-172">데이터베이스에 다른 파티션 함수가 없는 경우에는 **기존 파티션 함수** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-172">The **Existing partition function** option will not be available if there are no other partition functions on the database.</span></span>  
  
     <span data-ttu-id="1e181-173">이 페이지를 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-173">After completing this page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="1e181-174">**파티션 구성표 선택** 페이지의 **파티션 구성표 선택**에서 **새 파티션 구성표** 또는 **기존 파티션 구성표**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-174">On the **Select a Partition Scheme** page, under **Select partition scheme**, click either **New partition scheme** or **Existing partition scheme**.</span></span> <span data-ttu-id="1e181-175">**새 파티션 구성표**를 선택하는 경우 구성표 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-175">If you choose **New partition scheme**, enter the name of the scheme.</span></span> <span data-ttu-id="1e181-176">**기존 파티션 구성표**를 선택하는 경우 사용하려는 구성표 이름을 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-176">If you choose **Existing partition scheme**, select the name of the scheme you'd like to use from the list.</span></span> <span data-ttu-id="1e181-177">데이터베이스에 다른 파티션 구성표가 없는 경우에는 **기존 파티션 구성표** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-177">The **Existing partition scheme** option will not be available if there are no other partition schemes on the database.</span></span>  
  
     <span data-ttu-id="1e181-178">이 페이지를 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-178">After completing this page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="1e181-179">**파티션 매핑** 페이지의 **범위**에서 **왼쪽 경계** 또는 **오른쪽 경계** 중 하나를 선택하여 만들려는 각 파일 그룹 내에 최고 또는 최저 경계 값을 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-179">On the **Map Partitions** page, under **Range**, select either **Left boundary** or **Right boundary** to specify whether to include the highest or lowest bounding value within each filegroup you create.</span></span> <span data-ttu-id="1e181-180">파티션을 만들 때 경계 값에 대해 지정된 파일 그룹의 수에 하나의 파일 그룹을 추가로 더해 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-180">You must always enter one extra filegroup in addition to the number of filegroups specified for the boundary values when you are creating partitions.</span></span>  
  
     <span data-ttu-id="1e181-181">**파일 그룹 선택 및 경계 값 지정** 표의 **파일 그룹**에서 데이터를 분할하여 저장할 파일 그룹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-181">In the **Select filegroups and specify boundary values** grid, under **Filegroup**, select the filegroup into which you want to partition your data.</span></span> <span data-ttu-id="1e181-182">**경계**아래에서 각 파일 그룹에 대한 경계 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-182">Under **Boundary**, enter the boundary value for each filegroup.</span></span> <span data-ttu-id="1e181-183">경계 값을 비워 두면 파티션 함수는 파티션 함수 이름을 사용하여 전체 테이블 또는 인덱스를 단일 파티션으로 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-183">If boundary value is left empty, the partition function maps the whole table or index into a single partition using the partition function name.</span></span>  
  
     <span data-ttu-id="1e181-184">이 페이지에서는 다음과 같은 옵션을 추가로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-184">The following additional options are available on this page:</span></span>  
  
     <span data-ttu-id="1e181-185">**경계 설정...**</span><span class="sxs-lookup"><span data-stu-id="1e181-185">**Set Boundaries...**</span></span>  
     <span data-ttu-id="1e181-186">**경계 값 설정** 대화 상자를 열어 파티션에 사용할 경계 값과 날짜 범위를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-186">Opens the **Set Boundary Values** dialog box to select the boundary values and date ranges you want for your partitions.</span></span> <span data-ttu-id="1e181-187">이 옵션은 `date`, `datetime`, `smalldatetime`, `datetime2` 또는 `datetimeoffset` 데이터 형식 중 하나를 포함하는 분할 열을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-187">This option is only available when you have selected a partitioning column that contains one of the following data types: `date`, `datetime`, `smalldatetime`, `datetime2`, or `datetimeoffset`.</span></span>  
  
     <span data-ttu-id="1e181-188">**스토리지 계산**</span><span class="sxs-lookup"><span data-stu-id="1e181-188">**Estimate storage**</span></span>  
     <span data-ttu-id="1e181-189">파티션에 대해 지정된 각 파일 그룹에 대해 행 개수, 필요한 공간 및 사용 가능한 스토리지 공간을 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-189">Estimates rowcount, required space, and available space for storage for each filegroup specified for the partitions.</span></span> <span data-ttu-id="1e181-190">이러한 값은 표에 읽기 전용 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-190">These values are displayed in the grid as read-only values.</span></span>  
  
     <span data-ttu-id="1e181-191">**경계 값 설정** 대화 상자에서 다음 옵션을 추가로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-191">The **Set Boundary Values** dialog box allows for the following additional options:</span></span>  
  
     <span data-ttu-id="1e181-192">**시작 날짜**</span><span class="sxs-lookup"><span data-stu-id="1e181-192">**Start date**</span></span>  
     <span data-ttu-id="1e181-193">파티션의 범위 값에 대해 시작 날짜를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-193">Selects the starting date for the range values of your partitions.</span></span>  
  
     <span data-ttu-id="1e181-194">**종료 날짜**</span><span class="sxs-lookup"><span data-stu-id="1e181-194">**End date**</span></span>  
     <span data-ttu-id="1e181-195">파티션의 범위 값에 대해 종료 날짜를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-195">Selects the ending date for the range values of your partitions.</span></span> <span data-ttu-id="1e181-196">**파티션 매핑** 페이지에서 **왼쪽 경계** 를 선택한 경우 이 날짜가 각 파일 그룹/파티션의 마지막 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-196">If you selected **Left boundary** on the **Map Partitions** page, this date will be the last value for each filegroup/partition.</span></span> <span data-ttu-id="1e181-197">**파티션 매핑** 페이지에서 **오른쪽 경계** 를 선택한 경우 이 날짜가 마지막에서 두 번째 파일 그룹의 첫 번째 값이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-197">If you selected **Right boundary** on the **Map Partitions** page, this date will be the first value in the next-to-last filegroup.</span></span>  
  
     <span data-ttu-id="1e181-198">**날짜 범위**</span><span class="sxs-lookup"><span data-stu-id="1e181-198">**Date range**</span></span>  
     <span data-ttu-id="1e181-199">각 파티션에 사용할 날짜 세분성이나 범위 값 증분을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-199">Selects the date granularity or range value increment you want for each partition.</span></span>  
  
     <span data-ttu-id="1e181-200">이 페이지를 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-200">After completing this page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="1e181-201">**출력 옵션 선택** 페이지에서 분할된 테이블을 완료하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-201">In the **Select an Output Option** page, specify how you want to complete your partitioned table.</span></span> <span data-ttu-id="1e181-202">마법사의 이전 페이지를 기반으로 SQL 스크립트를 만들려면 **스크립트 만들기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-202">Select **Create Script** to create a SQL script based the previous pages in the wizard.</span></span> <span data-ttu-id="1e181-203">마법사의 남은 페이지를 모두 완료한 후 새 분할된 테이블을 만들려면 **즉시 실행** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-203">Select **Run immediately** to create the new partitioned table after completing all remaining pages in the wizard.</span></span> <span data-ttu-id="1e181-204">향후 미리 결정된 시간에 새 분할된 테이블을 만들려면 **일정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-204">Select **Schedule** to create the new partitioned table at a predetermined time in the future.</span></span>  
  
     <span data-ttu-id="1e181-205">**스크립트 만들기**를 선택하는 경우 **스크립트 옵션**에서 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-205">If you select **Create script**, the following options are available under **Script options**:</span></span>  
  
     <span data-ttu-id="1e181-206">**파일로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="1e181-206">**Script to file**</span></span>  
     <span data-ttu-id="1e181-207">스크립트를 .sql 파일로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-207">Generates the script as a .sql file.</span></span> <span data-ttu-id="1e181-208">**파일 이름** 상자에 파일 이름 및 위치를 입력하거나 **찾아보기** 를 클릭하여 **스크립트 파일 위치** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-208">Enter a file name and location in the **File name** box or click **Browse** to open the **Script File Location** dialog box.</span></span> <span data-ttu-id="1e181-209">**다른 이름으로 저장**에서 **유니코드 텍스트** 또는 **ANSI 텍스트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-209">From **Save As**, select **Unicode text** or **ANSI text**.</span></span>  
  
     <span data-ttu-id="1e181-210">**클립보드로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="1e181-210">**Script to Clipboard**</span></span>  
     <span data-ttu-id="1e181-211">스크립트를 클립보드에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-211">Saves the script to the Clipboard.</span></span>  
  
     <span data-ttu-id="1e181-212">**새 쿼리 창으로 스크립팅**</span><span class="sxs-lookup"><span data-stu-id="1e181-212">**Script to New Query Window**</span></span>  
     <span data-ttu-id="1e181-213">새 쿼리 편집기 창에 스크립트를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-213">Generates the script to a new Query Editor window.</span></span> <span data-ttu-id="1e181-214">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-214">This is the default selection.</span></span>  
  
     <span data-ttu-id="1e181-215">**일정**을 선택하는 경우 **일정 변경**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-215">If you select **Schedule**, click **Change schedule**.</span></span>  
  
    1.  <span data-ttu-id="1e181-216">**새 작업 일정** 대화 상자의 **이름** 상자에 작업 일정 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-216">In the **New Job Schedule** dialog box, in the **Name** box, enter the job schedule's name.</span></span>  
  
    2.  <span data-ttu-id="1e181-217">**일정 유형** 목록에서 다음과 같은 일정 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-217">On the **Schedule type** list, select the type of schedule:</span></span>  
  
        -   <span data-ttu-id="1e181-218">**SQL Server 에이전트가 시작될 때 자동으로 시작**</span><span class="sxs-lookup"><span data-stu-id="1e181-218">**Start automatically when SQL Server Agent starts**</span></span>  
  
        -   <span data-ttu-id="1e181-219">**CPU가 유휴 상태로 될 때마다 시작**</span><span class="sxs-lookup"><span data-stu-id="1e181-219">**Start whenever the CPUs become idle**</span></span>  
  
        -   <span data-ttu-id="1e181-220">**되풀이**.</span><span class="sxs-lookup"><span data-stu-id="1e181-220">**Recurring**.</span></span> <span data-ttu-id="1e181-221">새 분할된 테이블을 정기적으로 새로운 정보로 업데이트하는 경우 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-221">Select this option if your new partitioned table updates with new information on a regular basis.</span></span>  
  
        -   <span data-ttu-id="1e181-222">**한 번**.</span><span class="sxs-lookup"><span data-stu-id="1e181-222">**One time**.</span></span> <span data-ttu-id="1e181-223">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-223">This is the default selection.</span></span>  
  
    3.  <span data-ttu-id="1e181-224">일정을 사용하거나 사용하지 않으려면 **사용** 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-224">Select or clear the **Enabled** check box to enable or disable the schedule.</span></span>  
  
    4.  <span data-ttu-id="1e181-225">**되풀이**를 선택하는 경우 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-225">If you select **Recurring**:</span></span>  
  
        1.  <span data-ttu-id="1e181-226">**빈도**아래의 **되풀이** 목록에서 다음과 같이 발생 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-226">Under **Frequency**, on the **Occurs** list, specify the frequency of occurrence:</span></span>  
  
            -   <span data-ttu-id="1e181-227">**일별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 일 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-227">If you select **Daily**, in the **Recurs every** box, enter how often the job schedule repeats in days.</span></span>  
  
            -   <span data-ttu-id="1e181-228">**주별**을 선택하는 경우 **매** 상자에 작업 일정을 반복하는 주 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-228">If you select **Weekly**, in the **Recurs every** box, enter how often the job schedule repeats in weeks.</span></span> <span data-ttu-id="1e181-229">작업 일정을 실행할 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-229">Select the day or days of the week on which the job schedule is run.</span></span>  
  
            -   <span data-ttu-id="1e181-230">**월별**을 선택한 경우 **매(Day)** 또는 **매(The)** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-230">If you select **Monthly**, select either **Day** or **The**.</span></span>  
  
                -   <span data-ttu-id="1e181-231">**매(Day)** 를 선택한 경우 작업 일정을 실행할 날짜와 작업 일정을 반복할 월 수를 모두 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-231">If you select **Day**, enter both the date of the month you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="1e181-232">예를 들어 작업 일정을 격월로 15일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 상자에 "15", 두 번째 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-232">For example, if you want the job schedule to run on the 15th day of the month every other month, select **Day** and enter "15" in the first box and "2" in the second box.</span></span> <span data-ttu-id="1e181-233">두 번째 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-233">Please note that the largest number allowed in the second box is "99".</span></span>  
  
                -   <span data-ttu-id="1e181-234">**매(The)** 를 선택한 경우 작업 일정을 실행할 요일 및 작업 일정을 반복할 월 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-234">If you select **The**, select the specific day of the week within the month that you want the job schedule to run and how often the job schedule repeats in months.</span></span> <span data-ttu-id="1e181-235">예를 들어 작업 일정을 격월로 마지막 평일에 실행하려면 **매(Day)** 를 선택하고 첫 번째 목록에서 **마지막**, 두 번째 목록에서 **평일**을 선택한 다음, 마지막 상자에 "2"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-235">For example, if you want the job schedule to run on the last weekday of the month every other month, select **Day**, select **last** from the first list and **weekday** from the second list, and then enter "2" in the last box.</span></span> <span data-ttu-id="1e181-236">처음 두 목록에서 **첫 번째**, **두 번째**, **세 번째**또는 **네 번째**및 특정 평일(예: 일요일 또는 수요일)을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-236">You can also select **first**, **second**, **third**, or **fourth**, as well as specific weekdays (for example: Sunday or Wednesday) from the first two lists.</span></span> <span data-ttu-id="1e181-237">마지막 상자에 허용되는 가장 큰 숫자는 "99"입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-237">Please note that the largest number allowed in the last box is "99".</span></span>  
  
        2.  <span data-ttu-id="1e181-238">**일별 빈도**에서 작업 일정이 실행되는 날에 작업 일정을 반복하는 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-238">Under **Daily frequency**, specify how often the job schedule repeats on the day the job schedule runs:</span></span>  
  
            -   <span data-ttu-id="1e181-239">**한 번 수행**을 선택하는 경우 **한 번 수행** 상자에 작업 일정을 실행할 특정 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-239">If you select **Occurs once at**, enter the specific time of day when the job schedule should run in the **Occurs once at** box.</span></span> <span data-ttu-id="1e181-240">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-240">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
            -   <span data-ttu-id="1e181-241">**되풀이 수행**을 선택하는 경우 **빈도**에 선택한 날 동안 작업 일정을 실행할 빈도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-241">If you select **Occurs every**, specify how often the job schedule runs during the day chosen under **Frequency**.</span></span> <span data-ttu-id="1e181-242">예를 들어 작업 일정을 실행하는 날에 2시간마다 작업 일정을 반복하려면 **되풀이 수행**을 선택하고 첫 번째 상자에 "2"를 입력한 다음, 목록에서 **시간**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-242">For example, if you want the job schedule to repeat every 2 hours during the day that the job schedule is run, select **Occurs every**, enter "2" in the first box, and then select **hour(s)** from the list.</span></span> <span data-ttu-id="1e181-243">이 목록에서 **분** 과 **초**도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-243">From this list you can also select **minute(s)** and **second(s)**.</span></span> <span data-ttu-id="1e181-244">첫 번째 상자에 허용되는 가장 큰 숫자는 "100"입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-244">Please note that the largest number allowed in the first box is "100".</span></span>  
  
                 <span data-ttu-id="1e181-245">**시작** 상자에 작업 일정 실행을 시작할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-245">In the **Starting at** box, enter the time that the job schedule should start running.</span></span> <span data-ttu-id="1e181-246">**종료** 상자에 작업 일정 반복을 중지할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-246">In the **Ending at** box, enter the time that the job schedule should stop repeating.</span></span> <span data-ttu-id="1e181-247">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-247">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
        3.  <span data-ttu-id="1e181-248">**기간**아래의 **시작 날짜**에 작업 일정 실행을 시작할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-248">Under **Duration**, in **Start date**, enter the date that you want the job schedule to start running.</span></span> <span data-ttu-id="1e181-249">**종료 날짜** 또는 **종료 날짜 없음** 을 선택하여 작업 일정 실행을 중지할 시기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-249">Select **End date** or **No end date** to indicate when the job schedule should stop running.</span></span> <span data-ttu-id="1e181-250">**종료 날짜**를 선택하는 경우 작업 일정 실행을 중지할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-250">If you select **End date**, enter the date that you want to job schedule to stop running.</span></span>  
  
    5.  <span data-ttu-id="1e181-251">**한 번**을 선택하는 경우 **한 번 발생**아래 **날짜** 상자에 작업 일정을 실행할 날짜를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-251">If you select **One Time**, under **One-time occurrence**, in the **Date** box, enter the date that the job schedule will be run.</span></span> <span data-ttu-id="1e181-252">**시간** 상자에 작업 일정을 실행할 시간을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-252">In the **Time** box, enter the time that the job schedule will be run.</span></span> <span data-ttu-id="1e181-253">시간, 분, 초와 오전 또는 오후를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-253">Enter the hour, minute, and second of the day, as well as AM or PM.</span></span>  
  
    6.  <span data-ttu-id="1e181-254">**요약**아래 **설명**에서 모든 작업 일정 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-254">Under **Summary**, in **Description**, verify that all job schedule settings are correct.</span></span>  
  
    7.  <span data-ttu-id="1e181-255">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-255">Click **OK**.</span></span>  
  
     <span data-ttu-id="1e181-256">이 페이지를 마쳤으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-256">After completing this page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="1e181-257">**요약 검토** 페이지의 **선택 항목 검토**아래에서 사용 가능한 옵션을 모두 확장하여 모든 파티션 설정이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-257">On the **Review Summary** page, under **Review your selections**, expand all available options to verify that all partition settings are correct.</span></span> <span data-ttu-id="1e181-258">모두 맞으면 **마침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-258">If everything is as expected, click **Finish**.</span></span>  
  
9. <span data-ttu-id="1e181-259">**파티션 작성 마법사 진행률** 페이지에서 파티션 작성 마법사의 동작에 대한 상태 정보를 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-259">On the **Create Partition Wizard Progress** page, monitor status information about the actions of the Create Partition Wizard.</span></span> <span data-ttu-id="1e181-260">마법사에서 선택한 옵션에 따라 진행률 페이지에 하나 이상의 동작이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-260">Depending on the options that you selected in the wizard, the progress page might contain one or more actions.</span></span> <span data-ttu-id="1e181-261">맨 위에 있는 상자에는 전반적인 마법사 상태와 수신된 상태, 오류 및 경고 메시지의 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-261">The top box displays the overall status of the wizard and the number of status, error, and warning messages that the wizard has received.</span></span>  
  
     <span data-ttu-id="1e181-262">다음은 **파티션 작성 마법사 진행률** 페이지에서 선택할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-262">The following options are available on the **Create Partition Wizard Progress** page:</span></span>  
  
     <span data-ttu-id="1e181-263">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="1e181-263">**Details**</span></span>  
     <span data-ttu-id="1e181-264">동작, 상태 및 마법사가 수행한 동작의 결과로 반환된 모든 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-264">Provides the action, status, and any messages that are returned from action taken by the wizard.</span></span>  
  
     <span data-ttu-id="1e181-265">**동작**</span><span class="sxs-lookup"><span data-stu-id="1e181-265">**Action**</span></span>  
     <span data-ttu-id="1e181-266">각 동작의 이름과 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-266">Specifies the type and name of each action.</span></span>  
  
     <span data-ttu-id="1e181-267">**상태**</span><span class="sxs-lookup"><span data-stu-id="1e181-267">**Status**</span></span>  
     <span data-ttu-id="1e181-268">마법사 동작 결과 전체적으로 **성공** 값을 반환했는지 또는 **실패**값을 반환했는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-268">Indicates whether the wizard action as a whole returned the value of **Success** or **Failure**.</span></span>  
  
     <span data-ttu-id="1e181-269">**메시지**</span><span class="sxs-lookup"><span data-stu-id="1e181-269">**Message**</span></span>  
     <span data-ttu-id="1e181-270">프로세스에서 반환된 모든 오류 또는 경고 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-270">Provides any error or warning messages that are returned from the process.</span></span>  
  
     <span data-ttu-id="1e181-271">**Report**</span><span class="sxs-lookup"><span data-stu-id="1e181-271">**Report**</span></span>  
     <span data-ttu-id="1e181-272">파티션 작성 마법사의 결과가 포함된 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-272">Creates a report that contains the results of the Create Partition Wizard.</span></span> <span data-ttu-id="1e181-273">**보고서 보기**, **보고서를 파일로 저장**, **클립보드에 보고서 복사**및 **보고서를 전자 메일로 보내기**중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-273">The options are **View Report**, **Save Report to File**, **Copy Report to Clipboard**, and **Send Report as Email**.</span></span>  
  
     <span data-ttu-id="1e181-274">**보고서 보기**</span><span class="sxs-lookup"><span data-stu-id="1e181-274">**View Report**</span></span>  
     <span data-ttu-id="1e181-275">파티션 작성 마법사의 진행률에 대한 텍스트 보고서가 포함된 **보고서 보기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-275">Opens the **View Report** dialog box, which contains a text report of the progress of the Create Partition Wizard.</span></span>  
  
     <span data-ttu-id="1e181-276">**보고서를 파일로 저장**</span><span class="sxs-lookup"><span data-stu-id="1e181-276">**Save Report to File**</span></span>  
     <span data-ttu-id="1e181-277">**보고서를 다른 이름으로 저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-277">Opens the **Save Report As** dialog box.</span></span>  
  
     <span data-ttu-id="1e181-278">**클립보드에 보고서 복사**</span><span class="sxs-lookup"><span data-stu-id="1e181-278">**Copy Report to Clipboard**</span></span>  
     <span data-ttu-id="1e181-279">마법사의 진행률 보고서 결과를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-279">Copies the results of the wizard's progress report to the Clipboard.</span></span>  
  
     <span data-ttu-id="1e181-280">**보고서를 전자 메일로 보내기**</span><span class="sxs-lookup"><span data-stu-id="1e181-280">**Send Report as Email**</span></span>  
     <span data-ttu-id="1e181-281">마법사의 진행률 보고서 결과를 이메일 메시지에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-281">Copies the results of the wizard's progress report into an email message.</span></span>  
  
     <span data-ttu-id="1e181-282">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-282">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="1e181-283">파티션 만들기 마법사는 파티션 함수 및 스키마를 만들고 파티션을 지정된 테이블에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-283">The Create Partition Wizard creates the partition function and scheme and then applies the partitioning to the specified table.</span></span> <span data-ttu-id="1e181-284">테이블 파티션을 확인하려면 개체 탐색기에서 테이블을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-284">To verify the table partitioning, in Object Explorer, right-click the table and select **Properties**.</span></span> <span data-ttu-id="1e181-285">**스토리지** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-285">Click the **Storage** page.</span></span> <span data-ttu-id="1e181-286">이 페이지에는 파티션 함수 및 스키마 이름과 파티션 수와 같은 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-286">The page displays information such as the name of the partition function and scheme and the number of partitions.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1e181-287">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1e181-287">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-partitioned-table"></a><span data-ttu-id="1e181-288">분할된 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="1e181-288">To create a partitioned table</span></span>  
  
1.  <span data-ttu-id="1e181-289">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-289">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1e181-290">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-290">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1e181-291">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-291">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="1e181-292">이 예에서는 새 파일 그룹, 파티션 함수 및 파티션 스키마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-292">The example creates new filegroups, a partition function, and a partition scheme.</span></span> <span data-ttu-id="1e181-293">스토리지 위치로 지정된 파티션 스키마를 사용하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-293">A new table is created with the partition scheme specified as the storage location.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Adds four new filegroups to the AdventureWorks2012 database  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test1fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012  
    ADD FILEGROUP test4fg;   
  
    -- Adds one file for each filegroup.  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test1dat1,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t1dat1.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test1fg;  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test2dat2,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t2dat2.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test2fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test3dat3,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t3dat3.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test3fg;  
    GO  
    ALTER DATABASE AdventureWorks2012   
    ADD FILE   
    (  
        NAME = test4dat4,  
        FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\t4dat4.ndf',  
        SIZE = 5MB,  
        MAXSIZE = 100MB,  
        FILEGROWTH = 5MB  
    )  
    TO FILEGROUP test4fg;  
    GO  
    -- Creates a partition function called myRangePF1 that will partition a table into four partitions  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
        AS RANGE LEFT FOR VALUES (1, 100, 1000) ;  
    GO  
    -- Creates a partition scheme called myRangePS1 that applies myRangePF1 to the four filegroups created above  
    CREATE PARTITION SCHEME myRangePS1  
        AS PARTITION myRangePF1  
        TO (test1fg, test2fg, test3fg, test4fg) ;  
    GO  
    -- Creates a partitioned table called PartitionTable that uses myRangePS1 to partition col1  
    CREATE TABLE PartitionTable (col1 int PRIMARY KEY, col2 char(10))  
        ON myRangePS1 (col1) ;  
    GO  
    ```  
  
#### <a name="to-determine-if-a-table-is-partitioned"></a><span data-ttu-id="1e181-294">테이블이 분할되었는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="1e181-294">To determine if a table is partitioned</span></span>  
  
1.  <span data-ttu-id="1e181-295">다음 쿼리는 `PartitionTable` 테이블이 분할된 경우 하나 이상의 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-295">The following query returns one or more rows if the table `PartitionTable` is partitioned.</span></span> <span data-ttu-id="1e181-296">테이블이 분할되지 않은 경우 행이 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-296">If the table is not partitioned, no rows are returned.</span></span>  
  
    ```  
    SELECT *   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] IN (0,1)   
    JOIN sys.partition_schemes ps   
        ON i.data_space_id = ps.data_space_id   
    WHERE t.name = 'PartitionTable';   
    GO  
    ```  
  
#### <a name="to-determine-the-boundary-values-for-a-partitioned-table"></a><span data-ttu-id="1e181-297">분할된 테이블에 대한 경계 값을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="1e181-297">To determine the boundary values for a partitioned table</span></span>  
  
1.  <span data-ttu-id="1e181-298">다음 쿼리는 `PartitionTable` 테이블의 각 파티션에 대해 경계 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-298">The following query returns the boundary values for each partition in the `PartitionTable` table.</span></span>  
  
    ```  
    SELECT t.name AS TableName, i.name AS IndexName, p.partition_number, p.partition_id, i.data_space_id, f.function_id, f.type_desc, r.boundary_id, r.value AS BoundaryValue   
    FROM sys.tables AS t  
    JOIN sys.indexes AS i  
        ON t.object_id = i.object_id  
    JOIN sys.partitions AS p  
        ON i.object_id = p.object_id AND i.index_id = p.index_id   
    JOIN  sys.partition_schemes AS s   
        ON i.data_space_id = s.data_space_id  
    JOIN sys.partition_functions AS f   
        ON s.function_id = f.function_id  
    LEFT JOIN sys.partition_range_values AS r   
        ON f.function_id = r.function_id and r.boundary_id = p.partition_number  
    WHERE t.name = 'PartitionTable' AND i.type <= 1  
    ORDER BY p.partition_number;  
    ```  
  
#### <a name="to-determine-the-partition-column-for-a-partitioned-table"></a><span data-ttu-id="1e181-299">분할된 테이블에 대한 파티션 열을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="1e181-299">To determine the partition column for a partitioned table</span></span>  
  
1.  <span data-ttu-id="1e181-300">다음 쿼리는 테이블에 대한 분할 열의 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-300">The following query returns the name of the partitioning column for table.</span></span> <span data-ttu-id="1e181-301">`PartitionTable`입니다.</span><span class="sxs-lookup"><span data-stu-id="1e181-301">`PartitionTable`.</span></span>  
  
    ```  
    SELECT   
        t.[object_id] AS ObjectID   
        , t.name AS TableName   
        , ic.column_id AS PartitioningColumnID   
        , c.name AS PartitioningColumnName   
    FROM sys.tables AS t   
    JOIN sys.indexes AS i   
        ON t.[object_id] = i.[object_id]   
        AND i.[type] <= 1 -- clustered index or a heap   
    JOIN sys.partition_schemes AS ps   
        ON ps.data_space_id = i.data_space_id   
    JOIN sys.index_columns AS ic   
        ON ic.[object_id] = i.[object_id]   
        AND ic.index_id = i.index_id   
        AND ic.partition_ordinal >= 1 -- because 0 = non-partitioning column   
    JOIN sys.columns AS c   
        ON t.[object_id] = c.[object_id]   
        AND ic.column_id = c.column_id   
    WHERE t.name = 'PartitionTable' ;   
    GO  
    ```  
  
 <span data-ttu-id="1e181-302">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1e181-302">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1e181-303">ALTER DATABASE 파일 및 파일 그룹 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e181-303">ALTER DATABASE File and Filegroup Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
-   [<span data-ttu-id="1e181-304">CREATE PARTITION FUNCTION&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e181-304">CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-function-transact-sql)  
  
-   [<span data-ttu-id="1e181-305">CREATE PARTITION SCHEME&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e181-305">CREATE PARTITION SCHEME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-partition-scheme-transact-sql)  
  
-   [<span data-ttu-id="1e181-306">CREATE TABLE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1e181-306">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
  
