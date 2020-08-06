---
title: 게시자 및 배포자 속성 보기 및 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- Distributors [SQL Server replication], modifying
- modifying replication properties, Distributors
- Distributors [SQL Server replication], properties
ms.assetid: 5dae1d59-c377-4c6e-adc9-b68c5b328f79
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 571f6f3a0d44f0fc87c67885249fca441776946d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648916"
---
# <a name="view-and-modify-distributor-and-publisher-properties"></a><span data-ttu-id="c0b37-102">게시자 및 배포자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="c0b37-102">View and Modify Distributor and Publisher Properties</span></span>
  <span data-ttu-id="c0b37-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]또는 RMO(복제 관리 개체)를 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 배포자 및 게시자 속성을 보고 수정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-103">This topic describes how to view and modify Distributor and Publisher properties in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="c0b37-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="c0b37-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c0b37-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="c0b37-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c0b37-106">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c0b37-106">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="c0b37-107">보안</span><span class="sxs-lookup"><span data-stu-id="c0b37-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c0b37-108">**다음을 사용하여 배포자 및 게시자 속성을 보고 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="c0b37-108">**To view and modify Distributor and Publisher properties, using:**</span></span>  
  
     [<span data-ttu-id="c0b37-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c0b37-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c0b37-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c0b37-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="c0b37-111">RMO(복제 관리 개체)</span><span class="sxs-lookup"><span data-stu-id="c0b37-111">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c0b37-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c0b37-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="c0b37-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="c0b37-113">Recommendations</span></span>  
  
-   <span data-ttu-id="c0b37-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 버전을 실행하는 게시자의 경우, **sysadmin** 고정 서버 역할의 사용자가 **구독자** 페이지에서 구독자를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-114">For Publishers running versions prior to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], a user in the **sysadmin** fixed server role can register Subscribers on the **Subscribers** page.</span></span> <span data-ttu-id="c0b37-115">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터는 더 이상 복제에 대해 구독자를 명시적으로 등록하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-115">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], it is no longer necessary to explicitly register Subscribers for replication.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c0b37-116">보안</span><span class="sxs-lookup"><span data-stu-id="c0b37-116">Security</span></span>  
 <span data-ttu-id="c0b37-117">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-117">When possible, prompt users to enter security credentials at runtime.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c0b37-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="c0b37-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="c0b37-119">배포자 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-119">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="c0b37-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 배포자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-120">Connect to the Distributor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="c0b37-121">**복제** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **배포자 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-121">Right-click the **Replication** folder, and then click **Distributor Properties**.</span></span>  
  
3.  <span data-ttu-id="c0b37-122">**배포자 속성 - \<Distributor>** 대화 상자에서 속성을 보고 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-122">View and modify properties in the **Distributor Properties - \<Distributor>** dialog box.</span></span>  
  
    -   <span data-ttu-id="c0b37-123">배포 데이터베이스의 속성을 보고 수정하려면 대화 상자의 **일반** 페이지에서 해당 데이터베이스에 대한 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-123">To view and modify properties for a distribution database, click the properties button (**...**) for the database on the **General** page of thedialog box.</span></span>  
  
    -   <span data-ttu-id="c0b37-124">배포자와 관련된 게시자 속성을 보고 수정하려면 대화 상자의**게시자**페이지에서 해당 게시자에 대한 속성 단추 ( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-124">To view and modify Publisher properties associated with the Distributor, click the properties button (**...**) for the Publisher on the **Publishers** page of the dialog box.</span></span>  
  
    -   <span data-ttu-id="c0b37-125">복제 에이전트에 대한 프로필에 액세스하려면 대화 상자의 **일반** 페이지에서 **프로필 기본값** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-125">To access profiles for replication agents, click the **Profile Defaults** button on the **General** page of the dialog box.</span></span> <span data-ttu-id="c0b37-126">자세한 내용은 [Replication Agent Profiles](agents/replication-agent-profiles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b37-126">For more information, see [Replication Agent Profiles](agents/replication-agent-profiles.md).</span></span>  
  
    -   <span data-ttu-id="c0b37-127">관리 저장 프로시저가 게시자에서 실행되고 배포자에서 정보를 업데이트할 때 사용되는 계정의 암호를 변경하려면 대화 상자의 **게시자** 페이지에서 **암호** 및 **암호 확인** 상자에 새 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-127">To change the password for the account used when administrative stored procedures execute at the Publisher and update information at the Distributor, enter a new password in the **Password** and **Confirm password** boxes on the **Publishers** page of the dialog box.</span></span> <span data-ttu-id="c0b37-128">자세한 내용은 [배포자 보안 설정](security/secure-the-distributor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b37-128">For more information, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
4.  <span data-ttu-id="c0b37-129">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-129">Modify any properties if necessary, and then click **OK**.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="c0b37-130">게시자 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-130">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="c0b37-131">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 게시자에 연결한 다음 해당 서버 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-131">Connect to the Publisher in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="c0b37-132">**복제** 폴더를 마우스 오른쪽 단추로 클릭한 다음 **게시자 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-132">Right-click the **Replication** folder, and then click **Publisher Properties**.</span></span>  
  
3.  <span data-ttu-id="c0b37-133">\*\*게시자 속성- \< Publisher > \*\* 대화 상자에서 속성을 보고 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-133">View and modify properties in the **Publisher Properties - \< Publisher >** dialog box.</span></span>  
  
    -   <span data-ttu-id="c0b37-134">**sysadmin** 고정 서버 역할의 사용자는 **게시 데이터베이스** 페이지에서 복제에 사용할 데이터베이스를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-134">A user in the **sysadmin** fixed server role can enable databases for replication on the **Publication Databases** page.</span></span> <span data-ttu-id="c0b37-135">데이터베이스를 설정한다고 해서 그 데이터베이스가 게시되는 것은 아닙니다. 데이터베이스를 설정하면 설정된 데이터베이스에 대한 **db_owner** 고정 데이터베이스 역할의 사용자가 그 데이터베이스에 하나 이상의 게시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-135">Enabling a database does not publish that database; rather, it allows any user in the **db_owner** fixed database role for that database to create one or more publications in the database.</span></span>  
  
4.  <span data-ttu-id="c0b37-136">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-136">Modify any properties if necessary, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c0b37-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="c0b37-137">Using Transact-SQL</span></span>  
 <span data-ttu-id="c0b37-138">복제 저장 프로시저를 사용하여 프로그래밍 방식으로 게시자와 배포자 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-138">Publisher and Distributor properties can be viewed programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-view-distributor-and-distribution-database-properties"></a><span data-ttu-id="c0b37-139">배포자 및 배포 데이터베이스 속성을 보려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-139">To view Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="c0b37-140">배포자, 배포 데이터베이스 및 작업 디렉터리에 대한 정보를 반환하려면 [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-140">Execute [sp_helpdistributor](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql) to return information about the Distributor, distribution database, and working directory.</span></span>  
  
2.  <span data-ttu-id="c0b37-141">지정한 배포 데이터베이스에 대한 속성을 반환하려면 [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-141">Execute [sp_helpdistributiondb](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql) to return properties of a specified distribution database.</span></span>  
  
#### <a name="to-change-distributor-and-distribution-database-properties"></a><span data-ttu-id="c0b37-142">배포자 및 배포 데이터베이스 속성을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-142">To change Distributor and distribution database properties</span></span>  
  
1.  <span data-ttu-id="c0b37-143">배포자 속성을 수정하려면 배포자에서 [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-143">At the Distributor, execute [sp_changedistributor_property](/sql/relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql) to modify Distributor properties.</span></span>  
  
2.  <span data-ttu-id="c0b37-144">배포자 데이터베이스 속성을 수정하려면 배포자에서 [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-144">At the Distributor, execute [sp_changedistributiondb](/sql/relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql) to modify distribution database properties.</span></span>  
  
3.  <span data-ttu-id="c0b37-145">배포자 암호를 변경하려면 배포자에서 [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-145">At the Distributor, execute [sp_changedistributor_password](/sql/relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql) to change the Distributor password.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c0b37-146">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-146">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="c0b37-147">스크립트 파일에 자격 증명을 저장해야 하는 경우에는 무단으로 액세스하지 못하도록 파일에 보안을 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b37-147">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
4.  <span data-ttu-id="c0b37-148">배포자를 사용하는 게시자의 속성을 변경하려면 배포자에서 [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) 를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-148">At the Distributor, execute [sp_changedistpublisher](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql) to change the properties of a Publisher using the Distributor.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="c0b37-149">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="c0b37-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="c0b37-150">다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 예에서는 배포자와 배포자 데이터베이스에 대한 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-150">The following example [!INCLUDE[tsql](../../includes/tsql-md.md)] script returns information about the Distributor and distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_helpdistributor](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributor)]  
  
 [!code-sql[HowTo#sp_helpdistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_helpdistributiondb)]  
  
 <span data-ttu-id="c0b37-151">다음 예에서는 배포자의 보존 기간, 배포자에 연결할 때 사용되는 암호, 배포자가 여러 복제 에이전트의 상태를 확인하는 간격(하트비트 간격이라고도 함)을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-151">This example changes retention periods for the Distributor, the password used when connecting to the Distributor, and the interval at which the Distributor checks the status of various replication agents (also known as the heartbeat interval).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c0b37-152">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-152">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="c0b37-153">스크립트 파일에 자격 증명을 저장해야 하는 경우에는 무단으로 액세스하지 못하도록 파일에 보안을 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="c0b37-153">If you must store credentials in a script file, secure the file to prevent unauthorized access.</span></span>  
  
 [!code-sql[HowTo#sp_changedistributor_property](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_property)]  
  
 [!code-sql[HowTo#sp_changedistributiondb](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributiondb)]  
  
 [!code-sql[HowTo#sp_changedistributor_password](../../snippets/tsql/SQL15/replication/howto/tsql/changedistpub.sql#sp_changedistributor_password)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="c0b37-154">RMO(복제 관리 개체) 사용</span><span class="sxs-lookup"><span data-stu-id="c0b37-154">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-view-and-modify-distributor-properties"></a><span data-ttu-id="c0b37-155">배포자 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-155">To view and modify Distributor properties</span></span>  
  
1.  <span data-ttu-id="c0b37-156"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c0b37-157"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="c0b37-158">1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-158">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="c0b37-159">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> 속성에서 현재 연결된 서버가 배포자인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-159">(Optional) Check the <xref:Microsoft.SqlServer.Replication.ReplicationServer.IsDistributor%2A> property to verify that the currently connected server is a Distributor.</span></span>  
  
4.  <span data-ttu-id="c0b37-160"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 메서드를 호출하여 서버에서 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties from the server.</span></span>  
  
5.  <span data-ttu-id="c0b37-161">(옵션) 속성을 변경하려면 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 개체에 설정할 수 있는 하나 이상의 배포자 속성에 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-161">(Optional) To change properties, set a new value for one or more of the Distributor properties that can be set on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object.</span></span>  
  
6.  <span data-ttu-id="c0b37-162">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 개체의 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 속성이 `true`로 설정되면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-162">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.ReplicationServer> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-distribution-database-properties"></a><span data-ttu-id="c0b37-163">배포 데이터베이스 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-163">To view and modify distribution database properties</span></span>  
  
1.  <span data-ttu-id="c0b37-164"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-164">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c0b37-165"><xref:Microsoft.SqlServer.Replication.DistributionDatabase> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-165">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> class.</span></span> <span data-ttu-id="c0b37-166">이름 속성을 지정하고 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-166">Specify the name property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="c0b37-167"><xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 메서드를 호출하여 서버에서 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-167">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties from the server.</span></span> <span data-ttu-id="c0b37-168">이 메서드가 `false`를 반환하는 경우 지정된 이름의 데이터베이스가 서버에 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-168">If this method returns `false`, the database with the specified name does not exist on the server.</span></span>  
  
4.  <span data-ttu-id="c0b37-169">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 속성 중 하나에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-169">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> properties that can be set.</span></span>  
  
5.  <span data-ttu-id="c0b37-170">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 개체의 <xref:Microsoft.SqlServer.Replication.DistributionDatabase> 속성이 `true`로 설정되면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-170">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionDatabase> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-view-and-modify-publisher-properties"></a><span data-ttu-id="c0b37-171">게시자 속성을 보고 수정하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-171">To view and modify Publisher properties</span></span>  
  
1.  <span data-ttu-id="c0b37-172"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-172">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c0b37-173"><xref:Microsoft.SqlServer.Replication.DistributionPublisher> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="c0b37-174"><xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 속성을 지정하고 1단계에서 만든 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-174">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 1.</span></span>  
  
3.  <span data-ttu-id="c0b37-175">(옵션) 속성을 변경하려면 설정할 수 있는 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 속성 중 하나에 대해 새 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-175">(Optional) To change properties, set a new value for one of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> properties that can be set.</span></span>  
  
4.  <span data-ttu-id="c0b37-176">(옵션) <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> 개체의 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 속성이 `true`로 설정되면 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 메서드를 호출하여 서버의 변경 내용을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-176">(Optional) If the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property on the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> object is set to `true`, call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method to commit the changes to the server.</span></span>  
  
#### <a name="to-change-the-password-for-the-administrative-connection-from-the-publisher-to-the-distributor"></a><span data-ttu-id="c0b37-177">관리 연결의 암호를 게시자에서 배포자로 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c0b37-177">To change the password for the administrative connection from the Publisher to the Distributor</span></span>  
  
1.  <span data-ttu-id="c0b37-178"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 배포자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-178">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="c0b37-179"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-179">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
3.  <span data-ttu-id="c0b37-180"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 1단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-180">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="c0b37-181"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-181">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
5.  <span data-ttu-id="c0b37-182"><xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-182">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="c0b37-183">*password* 매개 변수에 대해 새 암호 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-183">Pass the new password value for the *password* parameter.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c0b37-184">가능한 경우 런타임 시 사용자에게 보안 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-184">When possible, prompt users to enter security credentials at runtime.</span></span> <span data-ttu-id="c0b37-185">자격 증명을 저장해야 하는 경우 [Windows .NET Framework에서 제공하는](https://go.microsoft.com/fwlink/?LinkId=34733) 암호화 서비스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-185">If you must store credentials, use the [cryptographic services](https://go.microsoft.com/fwlink/?LinkId=34733) provided by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.</span></span>  
  
6.  <span data-ttu-id="c0b37-186">(옵션) 다음 단계를 수행하여 이 배포자를 사용하는 각 원격 게시자에서 암호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-186">(Optional) Perform the following steps to change the password at each remote Publisher that uses this Distributor:</span></span>  
  
    1.  <span data-ttu-id="c0b37-187"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> 클래스를 사용하여 게시자 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-187">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
    2.  <span data-ttu-id="c0b37-188"><xref:Microsoft.SqlServer.Replication.ReplicationServer> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-188">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span>  
  
    3.  <span data-ttu-id="c0b37-189"><xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 속성을 6a단계에서 만든 연결로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-189">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 6a.</span></span>  
  
    4.  <span data-ttu-id="c0b37-190"><xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> 메서드를 호출하여 개체 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-190">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.Load%2A> method to get the properties of the object.</span></span>  
  
    5.  <span data-ttu-id="c0b37-191"><xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-191">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.ChangeDistributorPassword%2A> method.</span></span> <span data-ttu-id="c0b37-192">*password* 매개 변수에 대해 5단계에서 만든 새 암호 값을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-192">Pass the new password value from Step 5 for the *password* parameter.</span></span>  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="c0b37-193">예(RMO)</span><span class="sxs-lookup"><span data-stu-id="c0b37-193">Example (RMO)</span></span>  
 <span data-ttu-id="c0b37-194">이 예에서는 배포 및 배포 데이터베이스 속성을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-194">This example shows how to change Distribution and distribution database properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c0b37-195">자격 증명을 코드에 저장하지 않도록 런타임에 새 배포자 암호가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0b37-195">To avoid storing credentials in the code, the new Distributor password is supplied at runtime.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changedistpub)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changedistpub)]  
  
## <a name="see-also"></a><span data-ttu-id="c0b37-196">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0b37-196">See Also</span></span>  
 <span data-ttu-id="c0b37-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-197">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="c0b37-198">[게시 및 배포 해제](disable-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-198">[Disable Publishing and Distribution](disable-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="c0b37-199">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-199">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="c0b37-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-200">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 <span data-ttu-id="c0b37-201">[배포자 및 게시자 정보 스크립트](administration/distributor-and-publisher-information-script.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-201">[Distributor and Publisher Information Script](administration/distributor-and-publisher-information-script.md) </span></span>  
 <span data-ttu-id="c0b37-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="c0b37-202">[Replication System Stored Procedures Concepts](concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="c0b37-203">복제 모니터를 사용 하 여 정보 보기 및 태스크 수행</span><span class="sxs-lookup"><span data-stu-id="c0b37-203">View Information and Perform Tasks using Replication Monitor</span></span>](monitor/view-information-and-perform-tasks-replication-monitor.md)  
  
  
