---
title: 스냅샷 속성 구성(복제 Transact-SQL 프로그래밍) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server replication], properties
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c7dd645fed073f73132c6993f12925a885a8e0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736172"
---
# <a name="configure-snapshot-properties-replication-transact-sql-programming"></a><span data-ttu-id="d170f-102">스냅샷 속성 구성(복제 Transact-SQL 프로그래밍)</span><span class="sxs-lookup"><span data-stu-id="d170f-102">Configure Snapshot Properties (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="d170f-103">복제 저장 프로시저를 사용하여 스냅샷 속성을 프로그래밍 방식으로 정의 및 수정할 수 있습니다. 사용되는 저장 프로시저는 게시 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-103">Snapshot properties can be defined and modified programmatically using replication stored procedures, where the stored procedures used depend on the type of publication.</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-snapshot-or-transactional-publication"></a><span data-ttu-id="d170f-104">스냅샷 또는 트랜잭션 게시를 만들 때 스냅샷 속성을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d170f-104">To configure snapshot properties when creating a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="d170f-105">게시자에서 [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-105">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="d170f-106">에 게시 이름을 지정 하 **@publication** 고, **스냅숏** 또는 **연속** 값을 지정 **@repl_freq** 하 고, 다음 스냅숏 관련 매개 변수 중 하나 이상을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-106">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="d170f-107">**@alt_snapshot_folder**-이 게시에 대 한 스냅숏이 스냅숏 기본 폴더 대신 또는 해당 위치에서 액세스 되는 경우 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-107">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="d170f-108">**@compress_snapshot**-대체 스냅숏 폴더의 스냅숏 파일이 CAB 파일 형식으로 압축 되는 경우 **true** 값을 지정 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-108">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] CAB file format.</span></span>  
  
    -   <span data-ttu-id="d170f-109">**@pre_snapshot_script**-초기 스냅숏을 적용 하기 전에 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-109">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-110">**@post_snapshot_script**-초기 스냅숏을 적용 한 후 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-110">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-111">**@snapshot_in_defaultfolder**-스냅숏이 기본 위치가 아닌 위치 에서만 사용 가능한 경우 **false** 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-111">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
     <span data-ttu-id="d170f-112">게시를 만드는 방법은 [Create a Publication](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d170f-112">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-configure-snapshot-properties-when-creating-a-merge-publication"></a><span data-ttu-id="d170f-113">병합 게시를 만들 때 스냅샷 속성을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d170f-113">To configure snapshot properties when creating a merge publication</span></span>  
  
1.  <span data-ttu-id="d170f-114">게시자에서 [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-114">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="d170f-115">에 게시 이름을 지정 하 **@publication** 고, **스냅숏** 또는 **연속** 값을 지정 **@repl_freq** 하 고, 다음 스냅숏 관련 매개 변수 중 하나 이상을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-115">Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl_freq**, and one or more of the following snapshot-related parameters:</span></span>  
  
    -   <span data-ttu-id="d170f-116">**@alt_snapshot_folder**-이 게시에 대 한 스냅숏이 스냅숏 기본 폴더 대신 또는 해당 위치에서 액세스 되는 경우 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-116">**@alt_snapshot_folder** - specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.</span></span>  
  
    -   <span data-ttu-id="d170f-117">**@compress_snapshot**-대체 스냅숏 폴더의 스냅숏 파일이 CAB 파일 형식으로 압축 되는 경우 **true** 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-117">**@compress_snapshot** - specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="d170f-118">**@pre_snapshot_script**-초기 스냅숏을 적용 하기 전에 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-118">**@pre_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-119">**@post_snapshot_script**-초기 스냅숏을 적용 한 후 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-119">**@post_snapshot_script** - specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-120">**@snapshot_in_defaultfolder**-스냅숏이 기본 위치가 아닌 위치 에서만 사용 가능한 경우 **false** 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-120">**@snapshot_in_defaultfolder** - specify a value of **false** if the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="d170f-121">게시를 만드는 방법은 [Create a Publication](create-a-publication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d170f-121">For more information about creating publications, see [Create a Publication](create-a-publication.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-snapshot-or-transactional-publication"></a><span data-ttu-id="d170f-122">기존 스냅샷 또는 트랜잭션 게시의 스냅샷 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="d170f-122">To modify snapshot properties of an existing snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="d170f-123">게시 데이터베이스의 게시자에서 [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-123">At the Publisher on the publication database, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="d170f-124">에 값 **1** 을 지정 **@force_invalidate_snapshot** 하 고에 다음 값 중 하나를 지정 합니다 **@property** .</span><span class="sxs-lookup"><span data-stu-id="d170f-124">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="d170f-125">**alt_snapshot_folder** -에 대 한 대체 스냅숏 폴더의 새 경로를 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-125">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="d170f-126">**compress_snapshot** - **false** 대체 스냅숏 폴더의 스냅숏 파일이 **true** **@value** CAB 파일 형식으로 압축 되는지 여부를 나타내기 위해에 true 또는 false 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-126">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="d170f-127">**pre_snapshot_script** - **@value** 초기 스냅숏을 적용 하기 전에 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 파일 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-127">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-128">**post_snapshot_script** -또한 **@value** 초기 스냅숏을 적용 한 후 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 파일 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-128">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-129">**snapshot_in_defaultfolder** - 마찬가지로 스냅샷을 기본 위치 이외 위치에서만 사용할 수 있는지 여부를 나타내는 **true** 또는 **false** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-129">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="d170f-130">(옵션) 게시 데이터베이스의 게시자에서 [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-130">(Optional) At the Publisher on the publication database, execute [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql).</span></span> <span data-ttu-id="d170f-131">**@publication**및 하나 이상의 일정 또는 보안 자격 증명 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-131">Specify **@publication** and one or more of the scheduling or security credential parameters being changed.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d170f-132">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-132">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="d170f-133">자격 증명을 스크립트 파일에 저장해야 하는 경우에는 파일에 무단으로 액세스하지 못하도록 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-133">If you must store credentials in a script file, you must secure the file to prevent unauthorized access.</span></span>  
  
3.  <span data-ttu-id="d170f-134">명령 프롬프트에서 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 를 실행하거나 스냅샷 에이전트 작업을 시작하여 새 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-134">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="d170f-135">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d170f-135">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
### <a name="to-modify-snapshot-properties-of-an-existing-merge-publication"></a><span data-ttu-id="d170f-136">기존 병합 게시의 스냅샷 속성을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="d170f-136">To modify snapshot properties of an existing merge publication</span></span>  
  
1.  <span data-ttu-id="d170f-137">게시 데이터베이스의 게시자에서 [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-137">At the Publisher on the publication database, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="d170f-138">에 값 **1** 을 지정 **@force_invalidate_snapshot** 하 고에 다음 값 중 하나를 지정 합니다 **@property** .</span><span class="sxs-lookup"><span data-stu-id="d170f-138">Specify a value of **1** for **@force_invalidate_snapshot** and one of the following values for **@property**:</span></span>  
  
    -   <span data-ttu-id="d170f-139">**alt_snapshot_folder** -에 대 한 대체 스냅숏 폴더의 새 경로를 지정 **@value** 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-139">**alt_snapshot_folder** -also specify a new path to the alternate snapshot folder for **@value**.</span></span>  
  
    -   <span data-ttu-id="d170f-140">**compress_snapshot** - **false** 대체 스냅숏 폴더의 스냅숏 파일이 **true** **@value** CAB 파일 형식으로 압축 되는지 여부를 나타내기 위해에 true 또는 false 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-140">**compress_snapshot** - also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.</span></span>  
  
    -   <span data-ttu-id="d170f-141">**pre_snapshot_script** - **@value** 초기 스냅숏을 적용 하기 전에 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 파일 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-141">**pre_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-142">**post_snapshot_script** -또한 **@value** 초기 스냅숏을 적용 한 후 초기화 하는 동안 구독자에서 실행할 **.sql** 파일의 파일 이름 및 전체 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-142">**post_snapshot_script** - also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.</span></span>  
  
    -   <span data-ttu-id="d170f-143">**snapshot_in_defaultfolder** - 마찬가지로 스냅샷을 기본 위치 이외 위치에서만 사용할 수 있는지 여부를 나타내는 **true** 또는 **false** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-143">**snapshot_in_defaultfolder** - also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non-default location.</span></span>  
  
2.  <span data-ttu-id="d170f-144">명령 프롬프트에서 [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) 를 실행하거나 스냅샷 에이전트 작업을 시작하여 새 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-144">Run the [Replication Snapshot Agent](../agents/replication-snapshot-agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot.</span></span> <span data-ttu-id="d170f-145">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d170f-145">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d170f-146">예제</span><span class="sxs-lookup"><span data-stu-id="d170f-146">Example</span></span>  
 <span data-ttu-id="d170f-147">이 예제에서는 대체 스냅샷 폴더 및 압축 스냅샷을 사용하는 게시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d170f-147">This example creates a publication that uses an alternate snapshot folder and a compressed snapshot.</span></span>  
  
 [!code-sql[HowTo#sp_mergealtsnapshot](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubaltsnapshot.sql#sp_mergealtsnapshot)]  
  
## <a name="see-also"></a><span data-ttu-id="d170f-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d170f-148">See Also</span></span>  
 <span data-ttu-id="d170f-149">[대체 스냅숏 폴더 위치](../alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="d170f-149">[Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="d170f-150">[압축 스냅숏](../compressed-snapshots.md) </span><span class="sxs-lookup"><span data-stu-id="d170f-150">[Compressed Snapshots](../compressed-snapshots.md) </span></span>  
 <span data-ttu-id="d170f-151">[스냅샷 적용 전후에 스크립트 실행](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span><span class="sxs-lookup"><span data-stu-id="d170f-151">[Execute Scripts Before and After the Snapshot Is Applied](../snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied) </span></span>  
 <span data-ttu-id="d170f-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="d170f-152">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 <span data-ttu-id="d170f-153">[FTP를 통해 스냅샷 전송](../transfer-snapshots-through-ftp.md) </span><span class="sxs-lookup"><span data-stu-id="d170f-153">[Transfer Snapshots Through FTP](../transfer-snapshots-through-ftp.md) </span></span>  
 [<span data-ttu-id="d170f-154">게시 및 아티클 속성 변경</span><span class="sxs-lookup"><span data-stu-id="d170f-154">Change Publication and Article Properties</span></span>](change-publication-and-article-properties.md)  
  
  
