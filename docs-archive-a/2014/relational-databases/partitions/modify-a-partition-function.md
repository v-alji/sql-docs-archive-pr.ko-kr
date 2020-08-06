---
title: 파티션 함수 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae5bfc09-f27a-4ea9-9518-485278b11674
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bf14e633e62839b1abca7f38f833efab933c18f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729420"
---
# <a name="modify-a-partition-function"></a><span data-ttu-id="beea2-102">파티션 함수 수정</span><span class="sxs-lookup"><span data-stu-id="beea2-102">Modify a Partition Function</span></span>
  <span data-ttu-id="beea2-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 을 사용하여 분할된 테이블이나 인덱스의 파티션 함수에 지정된 파티션 수를 하나씩 더하거나 빼서 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 테이블이나 인덱스가 분할되는 방식을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-103">You can change the way a table or index is partitioned in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by adding or subtracting the number of partitions specified, in increments of 1, in the partition function of the partitioned table or index by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="beea2-104">파티션 추가는 기존의 한 파티션을 두 파티션으로 "분할"하고 새 파티션의 경계를 다시 정의하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-104">When you add a partition, you do so by "splitting" an existing partition into two partitions and redefining the boundaries of the new partitions.</span></span> <span data-ttu-id="beea2-105">파티션 삭제는 두 파티션의 경계를 하나로 "병합"하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-105">When you drop a partition, you do so by "merging" the boundaries of two partitions into one.</span></span> <span data-ttu-id="beea2-106">이 마지막 동작에서 한 파티션은 다시 채워지고 다른 한 파티션은 할당되지 않은 상태로 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-106">This last action repopulates one partition and leaves the other partition unassigned.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="beea2-107">둘 이상의 테이블 또는 인덱스가 같은 파티션 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-107">More than one table or index can use the same partition function.</span></span> <span data-ttu-id="beea2-108">파티션 함수를 수정할 경우 단일 트랜잭션에 있는 모든 대상에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-108">When you modify a partition function, you affect all of them in a single transaction.</span></span> <span data-ttu-id="beea2-109">파티션 함수를 수정하기 전에 파티션 함수의 종속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-109">Check the partition function's dependencies before modifying it.</span></span>  
  
 <span data-ttu-id="beea2-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="beea2-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="beea2-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="beea2-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="beea2-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="beea2-112">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="beea2-113">보안</span><span class="sxs-lookup"><span data-stu-id="beea2-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="beea2-114">**다음을 사용하여 파티션 함수 수정**</span><span class="sxs-lookup"><span data-stu-id="beea2-114">**To modify a partition function, using:**</span></span>  
  
     [<span data-ttu-id="beea2-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="beea2-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="beea2-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="beea2-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="beea2-117">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="beea2-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="beea2-118">제한 사항</span><span class="sxs-lookup"><span data-stu-id="beea2-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="beea2-119">ALTER PARTITION FUNCTION은 한 파티션을 둘로 분할하거나 두 파티션을 하나로 병합하는 데만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-119">ALTER PARTITION FUNCTION can only be used for splitting one partition into two, or for merging two partitions into one.</span></span> <span data-ttu-id="beea2-120">10개의 파티션을 5개로 줄이는 것과 같이 테이블이나 인덱스가 분할되는 방식을 변경하려면 다음 옵션 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-120">To change the way a table or index is partitioned (from 10 partitions to 5, for example), you can use any one of the following options:</span></span>  
  
    -   <span data-ttu-id="beea2-121">원하는 파티션 함수가 있는 분할된 테이블을 새로 만든 다음 INSERT INTO ... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] 문 또는 **의** 파티션 관리 마법사 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 이전 테이블의 데이터를 새 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-121">Create a new partitioned table with the desired partition function, and then insert the data from the old table into the new table by using either an INSERT INTO ... SELECT FROM [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or the **Manage Partition Wizard** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
    -   <span data-ttu-id="beea2-122">힙에 분할된 클러스터형 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-122">Create a partitioned clustered index on a heap.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="beea2-123">분할된 클러스터형 인덱스를 삭제하면 힙이 분할됩니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-123">Dropping a partitioned clustered index results in a partitioned heap.</span></span>  
  
    -   <span data-ttu-id="beea2-124">[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX 문에 DROP EXISTING = ON 절을 사용하여 기존의 분할 인덱스를 삭제하고 다시 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-124">Drop and rebuild an existing partitioned index by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX statement with the DROP EXISTING = ON clause.</span></span>  
  
    -   <span data-ttu-id="beea2-125">ALTER PARTITION FUNCTION 문의 시퀀스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-125">Perform a sequence of ALTER PARTITION FUNCTION statements.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="beea2-126">에서는 파티션 함수 수정을 위한 복제 지원을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-126">does not provide replication support for modifying a partition function.</span></span> <span data-ttu-id="beea2-127">게시 데이터베이스의 파티션 함수를 변경하려면 구독 데이터베이스에서 직접 파티션 함수를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-127">If you want to make changes to a partition function in the publication database, you must do this manually in the subscription database.</span></span>  
  
-   <span data-ttu-id="beea2-128">ALTER PARTITION FUNCTION의 영향을 받는 모든 파일 그룹이 온라인 상태여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-128">All filegroups that are affected by ALTER PARTITION FUNCTION must be online.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="beea2-129">보안</span><span class="sxs-lookup"><span data-stu-id="beea2-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="beea2-130">권한</span><span class="sxs-lookup"><span data-stu-id="beea2-130">Permissions</span></span>  
 <span data-ttu-id="beea2-131">ALTER PARTITION FUNCTION을 실행하려면 다음 중 하나의 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-131">Any one of the following permissions can be used to execute ALTER PARTITION FUNCTION:</span></span>  
  
-   <span data-ttu-id="beea2-132">ALTER ANY DATASPACE 권한.</span><span class="sxs-lookup"><span data-stu-id="beea2-132">ALTER ANY DATASPACE permission.</span></span> <span data-ttu-id="beea2-133">이 권한은 기본적으로 **sysadmin** 고정 서버 역할 및 **db_owner** 및 **db_ddladmin** 고정 데이터베이스 역할의 멤버에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-133">This permission defaults to members of the **sysadmin** fixed server role and the **db_owner** and **db_ddladmin** fixed database roles.</span></span>  
  
-   <span data-ttu-id="beea2-134">파티션 함수가 생성된 데이터베이스에 대한 CONTROL 또는 ALTER 권한</span><span class="sxs-lookup"><span data-stu-id="beea2-134">CONTROL or ALTER permission on the database in which the partition function was created.</span></span>  
  
-   <span data-ttu-id="beea2-135">파티션 함수가 생성된 데이터베이스의 서버에 대한 CONTROL SERVER 또는 ALTER ANY DATABASE 권한</span><span class="sxs-lookup"><span data-stu-id="beea2-135">CONTROL SERVER or ALTER ANY DATABASE permission on the server of the database in which the partition function was created.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="beea2-136">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="beea2-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="beea2-137">**파티션 함수를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="beea2-137">**To modify a partition function:**</span></span>  
  
 <span data-ttu-id="beea2-138">이 특정 동작은 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-138">This specific action cannot be performed using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="beea2-139">파티션 함수를 수정하려면 먼저 함수를 삭제한 다음 파티션 작성 마법사를 사용하여 원하는 속성이 포함된 새 함수를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-139">In order to modify a partition function, you must first delete the function and then create a new one with the desired properties using the Create Partition Wizard.</span></span> <span data-ttu-id="beea2-140">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="beea2-140">For more information, see</span></span>  
  
#### <a name="to-delete-a-partition-function"></a><span data-ttu-id="beea2-141">파티션 함수를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="beea2-141">To delete a partition function</span></span>  
  
1.  <span data-ttu-id="beea2-142">파티션 함수를 삭제할 데이터베이스를 확장한 다음 **스토리지** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-142">Expand the database where you want to delete the partition function and then expand the **Storage** folder.</span></span>  
  
2.  <span data-ttu-id="beea2-143">**파티션 함수** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-143">Expand the **Partition Functions** folder.</span></span>  
  
3.  <span data-ttu-id="beea2-144">삭제할 파티션 함수를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-144">Right-click the partition function you want to delete and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="beea2-145">**개체 삭제** 대화 상자에서 올바른 파티선 함수를 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-145">In the **Delete Object** dialog box, ensure that the correct partition function is selected, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="beea2-146">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="beea2-146">Using Transact-SQL</span></span>  
  
#### <a name="to-split-a-single-partition-into-two-partitions"></a><span data-ttu-id="beea2-147">단일 파티션을 두 개의 파티션으로 분할하려면</span><span class="sxs-lookup"><span data-stu-id="beea2-147">To split a single partition into two partitions</span></span>  
  
1.  <span data-ttu-id="beea2-148">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-148">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="beea2-149">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-149">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="beea2-150">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-150">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Split the partition between boundary_values 100 and 1000  
    --to create two partitions between boundary_values 100 and 500  
    --and between boundary_values 500 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    SPLIT RANGE (500);  
    ```  
  
#### <a name="to-merge-two-partitions-into-one-partition"></a><span data-ttu-id="beea2-151">두 개의 파티션을 하나의 파티션으로 병합하려면</span><span class="sxs-lookup"><span data-stu-id="beea2-151">To merge two partitions into one partition</span></span>  
  
1.  <span data-ttu-id="beea2-152">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-152">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="beea2-153">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-153">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="beea2-154">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="beea2-154">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Look for a previous version of the partition function "myRangePF1" and deletes it if it is found.  
    IF EXISTS (SELECT * FROM sys.partition_functions  
        WHERE name = 'myRangePF1')  
        DROP PARTITION FUNCTION myRangePF1;  
    GO  
    -- Create a new partition function called "myRangePF1" that partitions a table into four partitions.  
    CREATE PARTITION FUNCTION myRangePF1 (int)  
    AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
    GO  
    --Merge the partitions between boundary_values 1 and 100  
    --and between boundary_values 100 and 1000 to create one partition  
    --between boundary_values 1 and 1000.  
    ALTER PARTITION FUNCTION myRangePF1 ()  
    MERGE RANGE (100);  
    ```  
  
 <span data-ttu-id="beea2-155">자세한 내용은 [ALTER PARTITION FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="beea2-155">For more information, see [ALTER PARTITION FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-partition-function-transact-sql).</span></span>  
  
  
