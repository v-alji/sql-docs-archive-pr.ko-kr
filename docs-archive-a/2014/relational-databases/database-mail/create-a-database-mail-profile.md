---
title: 데이터베이스 메일 프로필 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], public profiles
- profiles [SQL Server], Database Mail
- public profiles [Database Mail]
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0453d495c90c1e599bfc7777b4899f30e6659c52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649097"
---
# <a name="create-a-database-mail-profile"></a><span data-ttu-id="51136-102">데이터베이스 메일 프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="51136-102">Create a Database Mail Profile</span></span>
  <span data-ttu-id="51136-103">**데이터베이스 메일 구성 마법사** 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 데이터베이스 메일 퍼블릭 프로필 및 프라이빗 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51136-103">Use either the **Database Mail Configuration Wizard** or [!INCLUDE[tsql](../../includes/tsql-md.md)] to create Database Mail public and private profiles.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="51136-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="51136-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="51136-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="51136-105">Prerequisites</span></span>  
 <span data-ttu-id="51136-106">프로필에 대한 데이터베이스 메일 계정을 하나 이상 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="51136-106">Create one or more Database Mail accounts for the profile.</span></span> <span data-ttu-id="51136-107">데이터베이스 메일 계정을 만드는 방법은 [데이터베이스 메일 계정 만들기](create-a-database-mail-account.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51136-107">For more information about creating Database Mail accounts, see [Create a Database Mail Account](create-a-database-mail-account.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="51136-108">보안</span><span class="sxs-lookup"><span data-stu-id="51136-108">Security</span></span>  
 <span data-ttu-id="51136-109">공개 프로필을 사용하여 **msdb** 데이터베이스에 액세스할 수 있는 모든 사용자는 해당 프로필을 사용하여 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51136-109">A public profile allows any user with access to the **msdb** database to send e-mail using that profile.</span></span> <span data-ttu-id="51136-110">프라이빗 프로필은 사용자 또는 역할에 의해 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51136-110">A private profile can be used by a user or by a role.</span></span> <span data-ttu-id="51136-111">프로필에 대한 액세스 권한을 역할에 부여하면 보다 쉽게 유지 관리되는 아키텍처가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="51136-111">Granting roles access to profiles creates a more easily maintained architecture.</span></span> <span data-ttu-id="51136-112">메일을 보내려면 **msdb** 데이터베이스에서 **DatabaseMailUserRole** 의 멤버여야 하며 적어도 하나 이상의 데이터베이스 메일 프로필에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-112">To send mail you must be a member of the **DatabaseMailUserRole** in the **msdb** database, and have access to at least one Database Mail profile.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="51136-113">권한</span><span class="sxs-lookup"><span data-stu-id="51136-113">Permissions</span></span>  
 <span data-ttu-id="51136-114">프로필 계정을 만들고 저장 프로시저를 실행하는 사용자는 sysadmin 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-114">The user creating the profiles accounts and executing stored procedures should be a member of the sysadmin fixed server role.</span></span>  
  

  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="51136-115">데이터베이스 메일 구성 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="51136-115">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="51136-116">**데이터베이스 메일 프로필을 만들려면**</span><span class="sxs-lookup"><span data-stu-id="51136-116">**To Create a Database Mail profile**</span></span>  
  
-   <span data-ttu-id="51136-117">개체 탐색기에서 데이터베이스 메일을 구성할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결한 다음 서버 트리를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-117">In Object Explorer, connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you want to configure Database Mail on, and expand the server tree.</span></span>  
  
-   <span data-ttu-id="51136-118">**관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-118">Expand the **Management** node</span></span>  
  
-   <span data-ttu-id="51136-119">데이터베이스 메일을 두 번 클릭하여 데이터베이스 메일 구성 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="51136-119">Double click Database Mail to open the Database Mail Configuration Wizard.</span></span>  
  
-   <span data-ttu-id="51136-120">**구성 태스크 선택** 페이지에서 **데이터베이스 메일 계정 및 프로필 관리** 옵션을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-120">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option and click **Next**.</span></span>  
  
-   <span data-ttu-id="51136-121">**프로필 및 계정 관리** 페이지에서 **새 프로필 만들기** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-121">On the **Manage Profiles and Accounts** page, select **Create a new profile** option, and click **Next**.</span></span>  
  
-   <span data-ttu-id="51136-122">**새 프로필** 페이지에서 프로필 이름과 설명을 지정하고, 프로필에 포함할 계정을 추가하고, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-122">On the **New Profile** page, specify the Profile name, Description and add accounts to be included in the profile, and click **Next**.</span></span>  
  
-   <span data-ttu-id="51136-123">**마법사 완료** 페이지에서 수행할 동작을 검토하고 **마침** 을 클릭하여 새 프로필 만들기를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-123">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete creating the new profile.</span></span>  
  
-   <span data-ttu-id="51136-124">**데이터베이스 메일 프라이빗 프로필을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="51136-124">**To configure a Database Mail private profile:**</span></span>  
  
    -   <span data-ttu-id="51136-125">데이터베이스 메일 구성 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="51136-125">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="51136-126">**구성 태스크 선택** 페이지에서 **데이터베이스 메일 계정 및 프로필 관리** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-126">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-127">**프로필 및 계정 관리** 페이지에서 **프로필 보안 관리** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-127">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-128">**프라이빗 프로필** 탭에서 구성하려는 프로필에 대한 확인란을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-128">In the **Private Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-129">**마법사 완료** 페이지에서 수행할 동작을 검토하고 **마침** 을 클릭하여 프로필 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-129">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  
-   <span data-ttu-id="51136-130">**데이터베이스 메일 공개 프로필을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="51136-130">**To configure a Database Mail public profile:**</span></span>  
  
    -   <span data-ttu-id="51136-131">데이터베이스 메일 구성 마법사를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="51136-131">Open the Database Mail Configuration Wizard.</span></span>  
  
    -   <span data-ttu-id="51136-132">**구성 태스크 선택** 페이지에서 **데이터베이스 메일 계정 및 프로필 관리** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-132">On the **Select Configuration Task** page, select **Manage Database Mail accounts and profiles** option, and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-133">**프로필 및 계정 관리** 페이지에서 **프로필 보안 관리** 옵션을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-133">On the **Manage Profiles and Accounts** page, select **Manage profile security** option and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-134">**공개 프로필** 탭에서 구성하려는 프로필에 대한 확인란을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-134">In the **Public Profiles** tab, select the check box for the profile you would like to configure and click **Next**.</span></span>  
  
    -   <span data-ttu-id="51136-135">**마법사 완료** 페이지에서 수행할 동작을 검토하고 **마침** 을 클릭하여 프로필 구성을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-135">On the **Complete the Wizard** page, review the actions to be performed and click **Finish** to complete configuring the profile.</span></span>  
  

  
## <a name="using-transact-sql"></a><span data-ttu-id="51136-136">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="51136-136">Using Transact-SQL</span></span>  
  
###  <a name="to-create-a-database-mail-private-profile"></a><a name="PrivateProfile"></a><span data-ttu-id="51136-137">데이터베이스 메일 개인 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="51136-137">To Create a Database Mail private profile</span></span>  
  
-   <span data-ttu-id="51136-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-138">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="51136-139">새 프로필을 만들려면 시스템 저장 프로시저 [sysmail_add_profile_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-139">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-140">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="51136-141">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-141">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="51136-142">*@description*= '*설명을*'</span><span class="sxs-lookup"><span data-stu-id="51136-142">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="51136-143">여기서 *@profile_name* 은 프로필의 이름이 고은 프로필에 대 한 *@description* 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="51136-143">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="51136-144">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="51136-144">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="51136-145">각 계정에 대해 저장 프로시저 [sysmail_add_profileaccount_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-145">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-146">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="51136-147">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-147">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="51136-148">*@account_name*= '*계정 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-148">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="51136-149">*@sequence_number*= '*프로필 내 계정의 시퀀스 번호입니다.*</span><span class="sxs-lookup"><span data-stu-id="51136-149">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="51136-150">'</span><span class="sxs-lookup"><span data-stu-id="51136-150">'</span></span>  
  
     <span data-ttu-id="51136-151">여기서 *@profile_name* 은 프로필의 이름이 고,은 프로필 *@account_name* 에 추가할 계정의 이름이 며,는 *@sequence_number* 프로필에서 계정이 사용 되는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-151">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="51136-152">이 프로필을 사용하여 메일을 보내는 각 데이터베이스 역할 또는 사용자에게 프로필에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-152">For each database role or user that will send mail using this profile, grant access to the profile.</span></span> <span data-ttu-id="51136-153">이렇게 하려면 저장 프로시저 [sysmail_add_principalprofile_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-153">To do this, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-154">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="51136-155">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-155">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="51136-156">*@ principal_name* = '*데이터베이스 사용자 또는 역할의 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-156">*@ principal_name* = '*Name of the database user or role*'</span></span>  
  
     <span data-ttu-id="51136-157">*@is_default*= '*기본 프로필 상태* '</span><span class="sxs-lookup"><span data-stu-id="51136-157">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="51136-158">여기서 *@profile_name* 은 프로필의 이름이 고, *@principal_name* 은 데이터베이스 사용자 또는 역할의 이름이 며,는 *@is_default* 이 프로필이 데이터베이스 사용자 또는 역할에 대 한 기본값 인지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-158">where *@profile_name* is the name of the profile, and *@principal_name* is the name of the database user or role, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="51136-159">다음 예에서는 데이터베이스 메일 계정을 만들고, 데이터베이스 메일 프라이빗 프로필을 만든 다음 프로필에 계정을 추가하며, **msdb** 데이터베이스의 **DBMailUsers** 데이터베이스 역할에 해당 프로필에 대한 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-159">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants access to the profile to the **DBMailUsers** database role in the **msdb** database.</span></span>  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
 
  
###  <a name="to-create-a-database-mail-public-profile"></a><a name="PublicProfile"></a><span data-ttu-id="51136-160">데이터베이스 메일 공개 프로필을 만들려면</span><span class="sxs-lookup"><span data-stu-id="51136-160">To Create a Database Mail public profile</span></span>  
  
-   <span data-ttu-id="51136-161">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-161">Connect to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="51136-162">새 프로필을 만들려면 시스템 저장 프로시저 [sysmail_add_profile_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-162">To create a new profile, run the system stored procedure [sysmail_add_profile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-163">**EXECUTEmsdb.dbo.sysmail_add_profile_sp**</span></span>  
  
     <span data-ttu-id="51136-164">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-164">*@profile_name* = '*Profile Name*'</span></span>  
  
     <span data-ttu-id="51136-165">*@description*= '*설명을*'</span><span class="sxs-lookup"><span data-stu-id="51136-165">*@description* = '*Desciption*'</span></span>  
  
     <span data-ttu-id="51136-166">여기서 *@profile_name* 은 프로필의 이름이 고은 프로필에 대 한 *@description* 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="51136-166">where *@profile_name* is the name of the profile, and *@description* is the description of the profile.</span></span> <span data-ttu-id="51136-167">이 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="51136-167">This parameter is optional.</span></span>  
  
-   <span data-ttu-id="51136-168">각 계정에 대해 저장 프로시저 [sysmail_add_profileaccount_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-168">For each account, run the stored procedure [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-169">**EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**</span></span>  
  
     <span data-ttu-id="51136-170">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-170">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="51136-171">*@account_name*= '*계정 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-171">*@account_name* = '*Name of the account*'</span></span>  
  
     <span data-ttu-id="51136-172">*@sequence_number*= '*프로필 내 계정의 시퀀스 번호입니다.*</span><span class="sxs-lookup"><span data-stu-id="51136-172">*@sequence_number* = '*sequence number of the account within the profile.*</span></span> <span data-ttu-id="51136-173">'</span><span class="sxs-lookup"><span data-stu-id="51136-173">'</span></span>  
  
     <span data-ttu-id="51136-174">여기서 *@profile_name* 은 프로필의 이름이 고,은 프로필 *@account_name* 에 추가할 계정의 이름이 며,는 *@sequence_number* 프로필에서 계정이 사용 되는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-174">where *@profile_name* is the name of the profile, and *@account_name* is the name of the account to add to the profile, *@sequence_number* determines the order in which the accounts are used in the profile.</span></span>  
  
-   <span data-ttu-id="51136-175">공용 액세스를 허용하려면 저장 프로시저 [sysmail_add_principalprofile_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)를 다음과 같이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-175">To grant public access, run the stored procedure [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql) as follows:</span></span>  
  
     <span data-ttu-id="51136-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span><span class="sxs-lookup"><span data-stu-id="51136-176">**EXECUTEmsdb.sysmail_add_principalprofile_sp**</span></span>  
  
     <span data-ttu-id="51136-177">*@profile_name*= '*프로필 이름*'</span><span class="sxs-lookup"><span data-stu-id="51136-177">*@profile_name* = '*Name of the profile*'</span></span>  
  
     <span data-ttu-id="51136-178">*@ principal_name* = '**public** 또는 **0**'</span><span class="sxs-lookup"><span data-stu-id="51136-178">*@ principal_name* = '**public** or **0**'</span></span>  
  
     <span data-ttu-id="51136-179">*@is_default*= '*기본 프로필 상태* '</span><span class="sxs-lookup"><span data-stu-id="51136-179">*@is_default* = '*Default Profile status* '</span></span>  
  
     <span data-ttu-id="51136-180">여기서 *@profile_name* 은 프로필의 이름이 고은 *@principal_name* 공개 프로필 임을 나타내려면 *@is_default* 는이 프로필이 데이터베이스 사용자 또는 역할에 대 한 기본값 인지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-180">where *@profile_name* is the name of the profile, and *@principal_name* to indicate this is a public profile, *@is_default* determines the whether this profile is the default for the database user or role.</span></span>  
  
 <span data-ttu-id="51136-181">다음 예에서는 데이터베이스 메일 계정을 만들고, 데이터베이스 메일 프라이빗 프로필을 만든 다음 프로필에 계정을 추가하며, 프로필에 대한 퍼블릭 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="51136-181">The following example creates a Database Mail account, creates a Database Mail private profile, then adds the account to the profile and grants public access to the profile.</span></span>  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  

  
  
