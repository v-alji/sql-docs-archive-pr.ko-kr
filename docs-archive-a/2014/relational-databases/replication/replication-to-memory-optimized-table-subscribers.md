---
title: 메모리 액세스에 최적화된 테이블 구독자로 복제 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df61b83d2f6d07cbbd21773b8940dd4e5341f76b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646319"
---
# <a name="replication-to-memory-optimized-table-subscribers"></a><span data-ttu-id="5ac93-102">메모리 액세스에 최적화된 테이블 구독자로 복제</span><span class="sxs-lookup"><span data-stu-id="5ac93-102">Replication to Memory-Optimized Table Subscribers</span></span>
  <span data-ttu-id="5ac93-103">피어 투 피어 트랜잭션 복제를 제외하고 트랜잭션 복제 구독자 역할을 수행하는 테이블은 메모리 최적화 테이블로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-103">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="5ac93-104">다른 복제 구성은 메모리 최적화 테이블과 호환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-104">Other replication configurations are not compatible with memory-optimized tables.</span></span>  
  
## <a name="configuring-a-memory-optimized-table-as-a-subscriber"></a><span data-ttu-id="5ac93-105">메모리 최적화 테이블을 구독자로 구성</span><span class="sxs-lookup"><span data-stu-id="5ac93-105">Configuring a memory-optimized table as a subscriber</span></span>  
 <span data-ttu-id="5ac93-106">메모리 최적화 테이블을 구독자로 구성하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-106">To configure a memory-optimized table as a subscriber, perform the following steps.</span></span>  
  
 <span data-ttu-id="5ac93-107">**게시 만들기 및 사용**</span><span class="sxs-lookup"><span data-stu-id="5ac93-107">**Create and Enable Publication**</span></span>  
  
1.  <span data-ttu-id="5ac93-108">게시 생성</span><span class="sxs-lookup"><span data-stu-id="5ac93-108">Create a publication.</span></span>  
  
2.  <span data-ttu-id="5ac93-109">아티클을 게시에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-109">Add articles to the publication.</span></span> <span data-ttu-id="5ac93-110">`@upd_cmd` 매개 변수에 대해서는 SCALL 또는 SQL 규칙을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-110">For the `@upd_cmd` parameter, use the SCALL or SQL convention.</span></span>  
  
    ```  
    EXEC sp_addarticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @source_owner = N'dbo',  
        @source_object = N'Mem_Table',  
        @type = N'logbased',  
        @description = null,  
        @creation_script = null,  
        @pre_creation_cmd = N'none',  
        @schema_option = 0x00000000080050DF,  
        @identityrangemanagementoption = N'manual',  
        @destination_table = N'Mem_Table',  
        @destination_owner = N'dbo',  
        @vertical_partition = N'false',  
        @ins_cmd = N'CALL sp_MSins_Mem_Table',  
        @del_cmd = N'CALL sp_MSdel_Mem_Table',  
        @upd_cmd = N'SCALL sp_MSupd_Mem_Table';  
    GO  
    ```  
  
 <span data-ttu-id="5ac93-111">**스냅숏 생성 및 스키마 조정**</span><span class="sxs-lookup"><span data-stu-id="5ac93-111">**Generate a Snapshot and Adjust the Schema**</span></span>  
  
1.  <span data-ttu-id="5ac93-112">스냅샷 작업을 만들고 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-112">Create a snapshot job and generate a snapshot.</span></span>  
  
    ```  
    EXEC sp_addpublication_snapshot @publication = N'Publication1', @frequency_type = 1;  
    EXEC sp_startpublication_snapshot @publication = N'Publication1';  
    ```  
  
2.  <span data-ttu-id="5ac93-113">스냅샷 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-113">Navigate to the snapshot folder.</span></span> <span data-ttu-id="5ac93-114">기본 위치는 "C:\Program Files\Microsoft SQL Server\MSSQL12. \<INSTANCE> \MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS \\ ".</span><span class="sxs-lookup"><span data-stu-id="5ac93-114">The default location is "C:\Program Files\Microsoft SQL Server\MSSQL12.\<INSTANCE>\MSSQL\repldata\unc\XXX\YYYYMMDDHHMMSS\\".</span></span>  
  
3.  <span data-ttu-id="5ac93-115">을 찾습니다 \*\*. \*\*테이블에 대 한 sch-m 파일을 만들고 Management Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-115">Locate the **.SCH** file for your table and open it in Management Studio.</span></span> <span data-ttu-id="5ac93-116">아래 설명에 따라 테이블 스키마를 변경하고 저장 프로시저를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-116">Change the table schema and update the stored procedure as described below.</span></span>  
  
     <span data-ttu-id="5ac93-117">IDX 파일에 정의된 인덱스를 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-117">Evaluate the indexes defined in the IDX file.</span></span> <span data-ttu-id="5ac93-118">`CREATE TABLE`을 수정하여 필수 인덱스, 제약 조건, 기본 키 및 메모리 최적화 구문을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-118">Modify `CREATE TABLE` to specify the required indexes, constraints, primary key, and memory-optimized syntax.</span></span> <span data-ttu-id="5ac93-119">메모리 최적화 테이블에서 인덱스 열은 NOT NULL이어야 하며 문지 형식의 인덱스 열은 Unicode여야 하고 BIN2 데이터 정렬을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-119">For memory-optimized tables, index columns should be NOT NULL and index columns of character types must be Unicode and use BIN2 collation.</span></span> <span data-ttu-id="5ac93-120">아래 예제를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ac93-120">See example below:</span></span>  
  
    ```  
    SET ANSI_PADDING ON;  
    GO  
  
    SET ANSI_NULLS ON;  
    GO  
  
    SET QUOTED_IDENTIFIER ON;  
    GO  
  
    CREATE TABLE [dbo].[Mem_Table]([c1] [int] NOT NULL,  
        [c2] [float] NOT NULL,  
        [c3] [decimal](10, 2) NOT NULL,  
        [c4] [nvarchar](5) COLLATE SQL_Latin1_General_CP850_BIN2 NOT NULL,  
        INDEX [hash_index_sample_memoryoptimizedtable_c2] HASH (c2) WITH (BUCKET_COUNT = 1024),  
        INDEX [index_sample_memoryoptimizedtable_c3] NONCLUSTERED ([c3]),  
        INDEX [nvarchar_index_sample_memoryoptimizedtable_c4] ([c4]),  
        CONSTRAINT [PK_sample_memoryoptimizedtable] PRIMARY KEY NONCLUSTERED ([c1])) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA);  
    GO  
    ```  
  
4.  <span data-ttu-id="5ac93-121">`@upd_cmd` 매개 변수에 대해 SCALL 규칙을 사용할 때는 스키마(.SCH) 파일로 이동하고 `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]`에서 테이블 업데이트 문을 변경하여 기본 키 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-121">When using SCALL convention for the `@upd_cmd` parameter, go to the schema (.SCH) file and change the table update statement in `create procedure [sp_MSupd_<SCHEMA><TABLE_NAME>]` to remove primary key columns.</span></span>  
  
     <span data-ttu-id="5ac93-122">기본 키 업데이트를 지원하려면 사용자 정의 업데이트 저장 프로시저를 사용해서 다음과 같이 기본 키 업데이트 문을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-122">To support primary key updates, use a custom update stored procedure to replace the primary key update statement, as follows:</span></span>  
  
    1.  <span data-ttu-id="5ac93-123">누락된 열 값을 선택합니다(SCALL은 업데이트 작업과 관련된 열만 제공).</span><span class="sxs-lookup"><span data-stu-id="5ac93-123">Select missing column values (SCALL only provides the column involved into the update operation).</span></span>  
  
    2.  <span data-ttu-id="5ac93-124">기존 레코드를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-124">Delete the existing record.</span></span>  
  
    3.  <span data-ttu-id="5ac93-125">새 기본 키를 포함해서 제공된 새 값으로 새 레코드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-125">Insert a new record with new values provided including the new primary key.</span></span>  
  
     <span data-ttu-id="5ac93-126">원래 업데이트 프로시저는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-126">The original update procedure looks like this:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
                   [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="5ac93-127">게시자에서 기본 키를 업데이트해서는 안 되는 경우</span><span class="sxs-lookup"><span data-stu-id="5ac93-127">If the primary key should never be updated on a publisher.</span></span> <span data-ttu-id="5ac93-128">다음과 같이 업데이트 프로시저에서 해당 열에 대한 업데이트를 주석 처리하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ac93-128">Comment out the update to such columns in the update procedure as follows:</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                   @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    update [dbo].[Mem_Table] set  
    --             [c1] = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
     <span data-ttu-id="5ac93-129">기본 키에 대한 업데이트 지원을 허용하려면 다음과 같이 업데이트 프로시저를 수정하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ac93-129">To allow the support of updates to the primary key, modify the update procedure to read as follows</span></span>  
  
    ```  
    create procedure [sp_MSupd_Mem_Table]  
                   @c1 int = NULL,  
                   @c2 float = NULL,  
                   @c3 decimal(10,2) = NULL,  
                   @c4 nvarchar(5) = NULL,  
                    @pkc1 int = NULL,  
                   @bitmap binary(1)  
    as  
    begin    
    if (substring(@bitmap,1,1) & 1 = 1)  
    begin   
    select  
                   @c1 = case substring(@bitmap,1,1) & 1 when 1 then @c1 else [c1] end,  
                   @c2 = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   @c3 = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   @c4 = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    from [dbo].[Mem_Table] where [c1] = @pkc1  
    if @@rowcount <> 0 begin  
            delete [dbo].[Mem_Table] where [c1] = @pkc1  
            if @@rowcount <> 0  
                   insert into [dbo].[Mem_Table]([c1],  
                           [c2],  
                           [c3],  
                           [c4]) values (  
                           @c1,  
                           @c2,  
                           @c3,  
                           @c4  
                   )   
    end  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end    
    else  
    begin   
    update [dbo].[Mem_Table] set  
                   [c2] = case substring(@bitmap,1,1) & 2 when 2 then @c2 else [c2] end,  
                   [c3] = case substring(@bitmap,1,1) & 4 when 4 then @c3 else [c3] end,  
                   [c4] = case substring(@bitmap,1,1) & 8 when 8 then @c4 else [c4] end  
    where [c1] = @pkc1  
    if @@rowcount = 0  
        if @@microsoftversion>0x07320000  
            exec sp_MSreplraiserror 20598  
    end   
    end   
    go  
    ```  
  
5.  <span data-ttu-id="5ac93-130">**Snapshot 격리로 승격** 옵션을 사용 하 여 구독자 데이터베이스를 만들고 비유니코드 문자 데이터 형식을 사용 하는 경우 기본 데이터 정렬을 Latin1_General_CS_AS_KS_WS로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-130">Create subscriber database using the **elevate to snapshot isolation** option and set the default collation to Latin1_General_CS_AS_KS_WS in case of using non Unicode character data types.</span></span>  
  
    ```  
    CREATE DATABASE [Sub]   
    CONTAINMENT = NONE   
    ON PRIMARY ( NAME = [Sub], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.mdf]),   
    FILEGROUP [mem] CONTAINS MEMORY_OPTIMIZED_DATA ( NAME = [mem],   
    FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub])  
    LOG ON ( NAME = [Sub_log], FILENAME = [C:\Program Files\Microsoft SQL Server\MSSQL12\MSSQL\DATA\Sub.ldf])  
    COLLATE Latin1_General_CS_AS_KS_WS;  
  
    ALTER DATABASE [Sub] SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT = ON;  
    GO  
    ```  
  
6.  <span data-ttu-id="5ac93-131">구독자의 데이터베이스에 스키마를 적용 하 고 나중에 사용할 수 있도록 스키마를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-131">Apply the schema to a subscriber's database and save the schema for future use.</span></span>  
  
7.  <span data-ttu-id="5ac93-132">구독자에 대해 게시자(원본) 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-132">Load the publisher (source) data to the subscriber.</span></span> <span data-ttu-id="5ac93-133">구독을 추가할 때까지는 게시자에서 데이터가 변경되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-133">Data should not change at the publisher until you add a subscription.</span></span>  <span data-ttu-id="5ac93-134">아래 표시된 것처럼 BCP를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-134">You can use BCP as shown below:</span></span>  
  
    ```  
    bcp Pub.dbo.Mem_Table out Mem_Table.bcp -S. -T -C1252 -n  
    bcp Sub.dbo.Mem_Table in Mem_Table.bcp -S. -T -C1252 -n  
    ```  
  
8.  <span data-ttu-id="5ac93-135">구독자에서 스키마 변경을 사용하지 않도록 아티클을 다시 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-135">Reconfigure the article to disable schema changes on the subscriber:</span></span>  
  
    ```  
    EXEC sp_changearticle  
        @publication = N'Publication1',  
        @article = N'Mem_Table',  
        @property = N'schema_option',  
        @value = 0,  
        @force_invalidate_snapshot = 1,  
        @force_reinit_subscription = 1;  
    GO  
    ```  
  
 <span data-ttu-id="5ac93-136">**비동기 구독 추가**</span><span class="sxs-lookup"><span data-stu-id="5ac93-136">**Add no sync Subscription**</span></span>  
  
 <span data-ttu-id="5ac93-137">비동기 구독을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-137">Add a nosync subscription.</span></span>  
  
```  
EXEC sp_addsubscription  
    @publication = N' Publication1',  
    @subscriber = @@ServerName,  
    @destination_db = N'Sub',  
    @subscription_type = N'Push',  
    @sync_type = N'replication support only',  
    @article = N'all',  
    @update_mode = N'read only',  
    @subscriber_type = 0;  
GO  
```  
  
 <span data-ttu-id="5ac93-138">메모리 액세스에 최적화된 테이블이 이제 게시자로부터 업데이트 수신을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-138">Memory-optimized tables should now start receiving updates from the publisher.</span></span>  
  
## <a name="restrictions"></a><span data-ttu-id="5ac93-139">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5ac93-139">Restrictions</span></span>  
 <span data-ttu-id="5ac93-140">단방향 트랜잭션 복제만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-140">Only one-way transactional replication is supported.</span></span> <span data-ttu-id="5ac93-141">피어 투 피어 트랜잭션 복제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-141">Peer-to-peer transactional replication is not supported.</span></span>  
  
 <span data-ttu-id="5ac93-142">메모리 액세스에 최적화된 테이블은 게시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-142">Memory-optimized tables cannot be published.</span></span>  
  
 <span data-ttu-id="5ac93-143">배포자의 복제 테이블은 메모리 최적화 테이블로 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-143">Replication tables on the distributor cannot be configured as memory-optimized tables.</span></span>  
  
 <span data-ttu-id="5ac93-144">병합 복제는 메모리 최적화 테이블을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-144">Merge replication cannot include memory-optimized tables.</span></span>  
  
 <span data-ttu-id="5ac93-145">구독자에서 트랜잭션 복제와 관련된 테이블은 메모리 최적화 테이블로 구성할 수 있지만 구독자 테이블은 메모리 최적화 테이블의 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-145">At the subscriber, tables involved in transactional replication can be configured as memory optimized tables, but the subscriber tables must meet the requirements of memory-optimized tables.</span></span> <span data-ttu-id="5ac93-146">여기에는 다음과 같은 제한 사항이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-146">This requires the following restrictions.</span></span>  
  
-   <span data-ttu-id="5ac93-147">트랜잭션 복제 구독자에서 메모리 최적화 테이블을 만들려면 메모리 최적화 테이블을 만드는 데 사용된 스냅샷 스키마 파일을 수동으로 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-147">To create a memory-optimized table on a transactional replication subscriber, the snapshot schema files used to create the memory-optimized tables must be manually modified.</span></span> <span data-ttu-id="5ac93-148">자세한 내용은 [스키마 파일 수정](#Schema)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac93-148">For more information, see [Modifying a schema file](#Schema).</span></span>  
  
-   <span data-ttu-id="5ac93-149">구독자에서 메모리 최적화 테이블로 복제된 테이블은 메모리 최적화 테이블의 행당 8060바이트로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-149">Tables replicated to memory-optimized tables on a subscriber are limited to the 8060 bytes per row limit of memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="5ac93-150">구독자에서 메모리 최적화 테이블로 복제된 테이블은 메모리 최적화 테이블에 허용된 데이터 형식으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-150">Tables replicated to memory-optimized tables on a subscriber are limited to the data types permitted in memory-optimized tables.</span></span> <span data-ttu-id="5ac93-151">자세한 내용은 [지원 되는 데이터 형식](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac93-151">For more information, see [Supported Data Types](../in-memory-oltp/supported-data-types-for-in-memory-oltp.md).</span></span>  
  
-   <span data-ttu-id="5ac93-152">구독자에서 메모리 최적화 테이블에 복제하는 테이블의 기본 키는 업데이트하는 데 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-152">There are restrictions on updating the primary key of tables being replicated to a memory-optimized table on a subscriber.</span></span> <span data-ttu-id="5ac93-153">자세한 내용은 [기본 키로 변경 내용 복제](#PrimaryKey)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ac93-153">For more information, see [Replicating changes to a primary key](#PrimaryKey).</span></span>  
  
-   <span data-ttu-id="5ac93-154">외래 키, 고유 제약 조건, 트리거, 스키마 수정, ROWGUIDCOL, 계산 열, 데이터 압축, 별칭 데이터 형식, 버전 관리 및 잠금은 메모리 최적화 테이블에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-154">Foreign key, unique constraint, triggers, schema modifications, ROWGUIDCOL, computed columns, data compression, alias data types, versioning, and locks are not supported in memory-optimized tables.</span></span> <span data-ttu-id="5ac93-155">자세한 내용은 [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5ac93-155">See [Transact-SQL Constructs Not Supported by In-Memory OLTP](../in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) for information.</span></span>  
  
##  <a name="modifying-a-schema-file"></a><a name="Schema"></a><span data-ttu-id="5ac93-156">스키마 파일 수정</span><span class="sxs-lookup"><span data-stu-id="5ac93-156">Modifying a schema file</span></span>  
  
-   <span data-ttu-id="5ac93-157">클러스터형 인덱스는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-157">Clustered indexes are not supported.</span></span> <span data-ttu-id="5ac93-158">클러스터형 인덱스를 비클러스터형 인덱스로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-158">Change any clustered indexes to nonclustered indexes.</span></span>  
  
-   <span data-ttu-id="5ac93-159">인덱스의 키에서 모든 열은 `NOT NULL`로 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-159">All columns in the key of an index must be specified as `NOT NULL`.</span></span>  
  
-   <span data-ttu-id="5ac93-160">메모리 최적화 테이블 옵션 `DURABILITY = SCHEMA_AND_DATA`를 사용할 경우 테이블은 비클러스터형 기본 키 인덱스를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-160">If using the memory-optimized table option `DURABILITY = SCHEMA_AND_DATA` the table must have a nonclustered primary key index.</span></span>  
  
-   <span data-ttu-id="5ac93-161">ANSI_PADDING은 ON이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-161">ANSI_PADDING must be ON.</span></span>  
  
##  <a name="replicating-changes-to-a-primary-key"></a><a name="PrimaryKey"></a><span data-ttu-id="5ac93-162">기본 키에 대 한 변경 내용 복제</span><span class="sxs-lookup"><span data-stu-id="5ac93-162">Replicating changes to a primary key</span></span>  
 <span data-ttu-id="5ac93-163">메모리 최적화 테이블의 기본 키는 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-163">The primary key of a memory-optimized table cannot be updated.</span></span> <span data-ttu-id="5ac93-164">구독자에서 기본 키 업데이트를 복제하려면 삭제 및 삽입 쌍으로 업데이트를 제공하도록 업데이트 저장 프로시저를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="5ac93-164">To replicate a primary key update on a subscriber, modify the update stored procedure to deliver the update as a delete and insert pair.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac93-165">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ac93-165">See Also</span></span>  
 [<span data-ttu-id="5ac93-166">SQL Server 복제</span><span class="sxs-lookup"><span data-stu-id="5ac93-166">SQL Server Replication</span></span>](sql-server-replication.md)  
  
  
