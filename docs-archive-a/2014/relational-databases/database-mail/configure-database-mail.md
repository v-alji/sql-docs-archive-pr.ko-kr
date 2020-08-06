---
title: 데이터베이스 메일 구성 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- Sql12.swb.sqlimail.newaccount.f1
- Sql12.swb.sqlimail.manageexistingaccount.f1
- Sql12.swb.dbmail.manageexistingaccount.f1
- Sql12.swb.sqlimail.manageexistingprofile.f1
- Sql12.swb.sqlimail.newprofile.f1
- Sql12.swb.sqlimail.profileandaccountmanagement.f1
- Sql12.swb.dbmail.configuresystem.f1
- Sql12.swb.dbmail.profileandaccountmanagement.f1
- Sql12.swb.dbmail. manageprofilesecurity.profileview.f1
- Sql12.swb.dbmail.selectconfiguration.f1
- Sql12.swb.dbmail.newsqlimailaccount.f1
- Sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- Sql12.swb.sqlimail.newsqlimailaccount.f1
- Sql12.swb.dbmail.newaccount.f1
- Sql12.swb.dbmail.manageexistingprofile.f1
- Sql12.swb.sqlimail.configuresystem.f1
- Sql12.swb.sqlimail.selectconfiguration.f1
- Sql12.swb.dbmail.completewizard.f1
- Sql12.swb.sqlimail.welcome.f1
- sql12.swb.dbmail.sendtestemail.f1
- Sql12.swb.sqlimail.addaccounttoprofile.f1
- Sql12.swb.dbmail.welcome.f1
- Sql12.swb.dbmail.newprofile.f1
- Sql12.swb.dbmail.addaccounttoprofile.f1
- sql12.swb.dbmail.sendtestemail.test.f1
- Sql12.swb.sqlimail.completewizard.f1
- Sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- Sql12.swb.dbmail.manageprofilesecurity.principalview.f1
ms.assetid: 7edc21d4-ccf3-42a9-84c0-3f70333efce6
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbf9af4b5af3043c6ca8fa2cba01ebe43019fb41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661137"
---
# <a name="configure-database-mail"></a><span data-ttu-id="8fe76-102">데이터베이스 메일 구성</span><span class="sxs-lookup"><span data-stu-id="8fe76-102">Configure Database Mail</span></span>
  <span data-ttu-id="8fe76-103">이 항목에서는 데이터베이스 메일 구성 마법사를 사용하여 데이터베이스 메일을 활성화 및 구성하고, 템플릿을 사용하여 데이터베이스 메일 구성 스크립트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-103">This topic describes how to enable and configure Database Mail using the Database Mail Configuration Wizard, and create a Database Mail Configuration script using templates.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8fe76-104">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8fe76-104">Before You Begin</span></span>  
 <span data-ttu-id="8fe76-105">**DatabaseMail XPs** 옵션을 사용하여 서버에서 데이터베이스 메일을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-105">Use the **DatabaseMail XPs** option to enable Database Mail on this server.</span></span> <span data-ttu-id="8fe76-106">자세한 내용은 [Database Mail XPs 서버 구성 옵션](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8fe76-106">For more information, see [Database Mail XPs Server Configuration Option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) reference topic.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8fe76-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8fe76-107">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8fe76-108">어느 데이터베이스에서든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker를 활성화하려면 데이터베이스 잠금이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-108">Enabling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Broker in any database requires a database lock.</span></span> <span data-ttu-id="8fe76-109">**msdb**에서 Service Broker가 비활성화되어 있는 경우 데이터베이스 메일을 활성화하려면 Service Broker가 필요한 잠금을 얻을 수 있도록 먼저 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-109">If Service Broker was deactivated in **msdb**, to enable Database Mail, first stop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent so Service Broker can obtain the necessary lock.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8fe76-110">보안</span><span class="sxs-lookup"><span data-stu-id="8fe76-110">Security</span></span>  
 <span data-ttu-id="8fe76-111">데이터베이스 메일을 구성하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-111">To configure Database Mail you must be a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="8fe76-112">데이터베이스 메일을 보내려면 **msdb** 데이터베이스에서 **DatabaseMailUserRole** 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-112">To send Database Mail you must be a member of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span>  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8fe76-113">데이터베이스 메일 구성 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="8fe76-113">Using Database Mail Configuration Wizard</span></span>  
 <span data-ttu-id="8fe76-114">**마법사를 사용하여 데이터베이스 메일을 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="8fe76-114">**To configure Database Mail using a wizard**</span></span>  
  
1.  <span data-ttu-id="8fe76-115">개체 탐색기에서 데이터베이스 메일을 구성할 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-115">In Object Explorer, expand the node for the instance  you want to configure Database mail.</span></span>  
  
2.  <span data-ttu-id="8fe76-116">**관리** 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-116">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="8fe76-117">**데이터베이스 메일**을 마우스 오른쪽 단추로 클릭하고 **데이터베이스 메일 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-117">Right-click **Database Mail**, and then click **Configure Database Mail**.</span></span>  
  
4.  <span data-ttu-id="8fe76-118">마법사의 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-118">Complete the Wizard dialogs</span></span>  
  

  
  
  
###  <a name="welcome-page"></a><a name="Welcome"></a><span data-ttu-id="8fe76-119">시작 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-119">Welcome Page</span></span>  
 <span data-ttu-id="8fe76-120">이 페이지에서는 데이터베이스 메일을 구성하는 단계를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-120">This page describes the steps to configuring Database Mail.</span></span>  
  
 <span data-ttu-id="8fe76-121">**이 페이지를 다시 표시 안 함** - 이후에 이 시작 페이지가 표시되지 않도록 하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-121">**Do not show this page again** - Check this to skip this welcome page from displaying in the future.</span></span>  
  
 <span data-ttu-id="8fe76-122">**다음** - **구성 태스크 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-122">**Next** - Proceeds to the **Select a configuration task** page.</span></span>  
  
 <span data-ttu-id="8fe76-123">**취소** -데이터베이스 메일를 구성 하지 않고 마법사를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-123">**Cancel** - Terminates the wizard without configuring Database Mail</span></span>  
  
 
  
###  <a name="select-configuration-task"></a><a name="ConfigTask"></a><span data-ttu-id="8fe76-124">구성 태스크 선택</span><span class="sxs-lookup"><span data-stu-id="8fe76-124">Select Configuration Task</span></span>  
 <span data-ttu-id="8fe76-125">마법사를 사용할 때마다 **구성 태스크 선택** 페이지를 사용하여 수행할 작업을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-125">Use the **Select Configuration Task** page, to indicate which task you will complete each time you use the wizard.</span></span> <span data-ttu-id="8fe76-126">마법사를 완료하기 전에 태스크를 취소하고 다른 태스크를 수행하려면 **뒤로** 단추를 눌러 이 페이지로 다시 돌아와 다른 태스크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-126">If you change your mind before you complete the wizard, use the **Back** button to return to this page and select a different task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8fe76-127">데이터베이스 메일이 설정되지 않은 경우 **데이터베이스 메일 기능을 사용할 수 없습니다.  이 기능을 설정하시겠습니까?** 라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-127">If Database Mail has not been enabled, you will receive the message: **The Database Mail feature is not available.  Would you like to enable this feature?**</span></span> <span data-ttu-id="8fe76-128">**예**를 선택하면 [sp_configure](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) 시스템 저장 프로시저의 **Database Mail XPs 옵션** 을 사용하는 경우와 동일하게 데이터베이스 메일을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-128">Responding **Yes**, is equivalent to enabling Database Mail by using the [Database Mail XPs option](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) of the **sp_configure** system stored procedure.</span></span>  
  
 <span data-ttu-id="8fe76-129">**다음 태스크를 수행하여 데이터베이스 메일 설치**</span><span class="sxs-lookup"><span data-stu-id="8fe76-129">**Set up Database Mail by performing the following tasks**</span></span>  
 <span data-ttu-id="8fe76-130">최초로 데이터베이스 메일을 설정하는 데 필요한 모든 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-130">Perform all of the tasks required to set up Database Mail for the first time.</span></span> <span data-ttu-id="8fe76-131">이 옵션에는 다른 세 가지 옵션이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-131">This option includes all of the other three options.</span></span>  
  
 <span data-ttu-id="8fe76-132">**데이터베이스 메일 계정 및 프로필 관리**</span><span class="sxs-lookup"><span data-stu-id="8fe76-132">**Manage Database Mail accounts and profiles**</span></span>  
 <span data-ttu-id="8fe76-133">새 데이터베이스 메일 계정 및 프로필을 만들거나 기존 데이터베이스 메일 계정과 프로필을 확인, 변경 또는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-133">Create new Database Mail accounts and profiles or to view, change, or delete existing Database Mail accounts and profiles.</span></span>  
  
 <span data-ttu-id="8fe76-134">**프로필 보안 관리**</span><span class="sxs-lookup"><span data-stu-id="8fe76-134">**Manage profile security**</span></span>  
 <span data-ttu-id="8fe76-135">데이터베이스 메일 프로필에 액세스할 수 있는 사용자를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-135">Configure which users have access to Database Mail profiles.</span></span>  
  
 <span data-ttu-id="8fe76-136">**시스템 매개 변수 확인 또는 변경**</span><span class="sxs-lookup"><span data-stu-id="8fe76-136">**View or change system parameters**</span></span>  
 <span data-ttu-id="8fe76-137">최대 첨부 파일 크기와 같은 데이터베이스 메일 시스템 매개 변수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-137">Configure Database Mail system parameters such as the maximum file size for attachments.</span></span>  
  

  
###  <a name="new-account-page"></a><a name="NewAccount"></a><span data-ttu-id="8fe76-138">새 계정 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-138">New Account Page</span></span>  
 <span data-ttu-id="8fe76-139">이 페이지를 사용하여 새 데이터베이스 메일 계정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-139">Use this page to create a new Database Mail account.</span></span> <span data-ttu-id="8fe76-140">데이터베이스 메일 계정에는 전자 메일을 SMTP 서버로 보내기 위한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-140">A Database Mail account contains information for sending e-mail to an SMTP server.</span></span>  
  
 <span data-ttu-id="8fe76-141">데이터베이스 메일 계정에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 전자 메일 메시지를 SMTP 서버로 보내기 위해 사용하는 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-141">A Database Mail account contains the information that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="8fe76-142">각 계정에는 하나의 전자 메일 서버에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-142">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="8fe76-143">데이터베이스 메일 계정은 데이터베이스 메일에 대해서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-143">A Database Mail account is only used for Database Mail.</span></span> <span data-ttu-id="8fe76-144">데이터베이스 메일 계정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정 또는 Microsoft Windows 계정에 해당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-144">A Database Mail account does not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account or a Microsoft Windows account.</span></span> <span data-ttu-id="8fe76-145">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 자격 증명 또는 사용자가 제공하는 다른 자격 증명을 사용하거나 익명으로 데이터베이스 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-145">Database Mail can be sent using the credentials of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], using other credentials that you supply, or anonymously.</span></span> <span data-ttu-id="8fe76-146">기본 인증을 사용하는 경우 데이터베이스 메일 계정의 사용자 이름과 암호는 전자 메일 서버 인증에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-146">When using basic authentication, the user name and password in a Database Mail account are only used for authentication with the e-mail server.</span></span> <span data-ttu-id="8fe76-147">계정이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 실행하는 컴퓨터 사용자에 해당할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-147">An account need not correspond to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user or a user on the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8fe76-148">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-148">**Account name**</span></span>  
 <span data-ttu-id="8fe76-149">새 계정의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-149">Type the name of the new account.</span></span>  
  
 <span data-ttu-id="8fe76-150">**설명**</span><span class="sxs-lookup"><span data-stu-id="8fe76-150">**Description**</span></span>  
 <span data-ttu-id="8fe76-151">계정에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-151">Type a description of the account.</span></span> <span data-ttu-id="8fe76-152">설명은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-152">The description is optional.</span></span>  
  
 <span data-ttu-id="8fe76-153">**전자 메일 주소**</span><span class="sxs-lookup"><span data-stu-id="8fe76-153">**E-mail address**</span></span>  
 <span data-ttu-id="8fe76-154">계정에 대한 전자 메일 주소의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-154">Type the name of the e-mail address for the account.</span></span> <span data-ttu-id="8fe76-155">이 주소는 전자 메일을 보내는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-155">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="8fe76-156">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트의 계정은 SqlAgent@Adventure-Works.com 주소에서 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-156">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may send e-mail from the address SqlAgent@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="8fe76-157">**표시 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-157">**Display name**</span></span>  
 <span data-ttu-id="8fe76-158">이 계정을 사용하여 보낼 전자 메일 메시지에 표시할 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-158">Type the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="8fe76-159">표시 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-159">The display name is optional.</span></span> <span data-ttu-id="8fe76-160">이 이름은 이 계정에서 보내는 메시지에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-160">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="8fe76-161">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 계정은 전자 메일 메시지에 "SQL Server Agent Automated Mailer"라는 이름을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-161">For example, an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may display the name "SQL Server Agent Automated Mailer" on e-mail messages.</span></span>  
  
 <span data-ttu-id="8fe76-162">**회신 전자 메일**</span><span class="sxs-lookup"><span data-stu-id="8fe76-162">**Reply e-mail**</span></span>  
 <span data-ttu-id="8fe76-163">이 계정에서 보낸 전자 메일 메시지에 대한 회신에 사용할 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-163">Type the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="8fe76-164">회신 전자 메일은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-164">The reply e-mail is optional.</span></span> <span data-ttu-id="8fe76-165">예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 계정에 대한 회신은 데이터베이스 관리자인 danw@Adventure-Works.com을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-165">For example, replies to an account for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent may go to the database administrator, danw@Adventure-Works.com.</span></span>  
  
 <span data-ttu-id="8fe76-166">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-166">**Server name**</span></span>  
 <span data-ttu-id="8fe76-167">계정에서 전자 메일을 보내기 위해 사용하는 SMTP 서버의 이름 또는 IP 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-167">Type the name or IP address of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="8fe76-168">일반적으로이는 `smtp.` *<your_company>* 와 비슷한 형식으로 되어 `.com` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-168">Typically this is in a format similar to `smtp.`*<your_company>*`.com`.</span></span> <span data-ttu-id="8fe76-169">이에 대한 도움을 얻으려면 메일 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-169">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="8fe76-170">**포트 번호**</span><span class="sxs-lookup"><span data-stu-id="8fe76-170">**Port number**</span></span>  
 <span data-ttu-id="8fe76-171">이 계정에 대한 SMTP 서버의 포트 번호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-171">Type the port number of the SMTP server for this account.</span></span> <span data-ttu-id="8fe76-172">대부분의 SMTP 서버에서는 포트 25를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-172">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="8fe76-173">**이 서버에는 보안 연결(SSL)이 필요합니다.**</span><span class="sxs-lookup"><span data-stu-id="8fe76-173">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="8fe76-174">SSL(Secure Sockets Layer)을 사용하여 통신을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-174">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="8fe76-175">**데이터베이스 엔진 서비스 자격 증명을 사용한 Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-175">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="8fe76-176">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스에 대해 구성된 자격 증명을 사용하여 SMTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-176">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8fe76-177">**기본 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-177">**Basic Authentication**</span></span>  
 <span data-ttu-id="8fe76-178">SMTP 서버에 필요한 사용자 이름과 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-178">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="8fe76-179">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-179">**User name**</span></span>  
 <span data-ttu-id="8fe76-180">데이터베이스 메일에서 SMTP 서버에 로그인하는 데 사용하는 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-180">Type the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8fe76-181">SMTP 서버에 기본 인증이 필요한 경우 사용자 이름은 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-181">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-182">**암호**</span><span class="sxs-lookup"><span data-stu-id="8fe76-182">**Password**</span></span>  
 <span data-ttu-id="8fe76-183">데이터베이스 메일에서 SMTP 서버에 로그인하는 데 사용하는 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-183">Type the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8fe76-184">SMTP 서버에 기본 인증이 필요한 경우 암호는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-184">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-185">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="8fe76-185">**Confirm password**</span></span>  
 <span data-ttu-id="8fe76-186">암호를 다시 입력하여 암호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-186">Type the password again to confirm the password.</span></span> <span data-ttu-id="8fe76-187">SMTP 서버에 기본 인증이 필요한 경우 암호는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-187">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-188">**익명 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-188">**Anonymous authentication**</span></span>  
 <span data-ttu-id="8fe76-189">메일이 로그인 자격 증명 없이 SMTP 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-189">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="8fe76-190">SMTP 서버에 인증이 필요하지 않은 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-190">Use this option when the SMTP server does not require authentication.</span></span>  
  
 
  
###  <a name="manage-existing-account-page"></a><a name="ExistingAccount"></a><span data-ttu-id="8fe76-191">기존 계정 관리 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-191">Manage Existing Account Page</span></span>  
 <span data-ttu-id="8fe76-192">이 페이지를 사용하여 기존 데이터베이스 메일 계정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-192">Use this page to manage an existing Database Mail account.</span></span>  
  
 <span data-ttu-id="8fe76-193">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-193">**Account name**</span></span>  
 <span data-ttu-id="8fe76-194">표시, 업데이트 또는 삭제할 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-194">Select the account to view, update or delete.</span></span>  
  
 <span data-ttu-id="8fe76-195">**삭제**</span><span class="sxs-lookup"><span data-stu-id="8fe76-195">**Delete**</span></span>  
 <span data-ttu-id="8fe76-196">선택한 계정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-196">Delete the selected account.</span></span> <span data-ttu-id="8fe76-197">선택한 계정을 삭제하기 전에 연결된 프로필에서 이 계정을 제거하거나 이러한 프로필을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-197">You must remove this account from associated profiles, or delete such profiles, before you delete the selected account.</span></span>  
  
 <span data-ttu-id="8fe76-198">**설명**</span><span class="sxs-lookup"><span data-stu-id="8fe76-198">**Description**</span></span>  
 <span data-ttu-id="8fe76-199">계정에 대한 설명을 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-199">View or update the description of the account.</span></span> <span data-ttu-id="8fe76-200">설명은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-200">The description is optional.</span></span>  
  
 <span data-ttu-id="8fe76-201">**전자 메일 주소**</span><span class="sxs-lookup"><span data-stu-id="8fe76-201">**E-mail address**</span></span>  
 <span data-ttu-id="8fe76-202">계정에 대한 전자 메일 주소의 이름을 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-202">View or update the name of the e-mail address for the account.</span></span> <span data-ttu-id="8fe76-203">이 주소는 전자 메일을 보내는 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-203">This is the e-mail address that e-mail is sent from.</span></span> <span data-ttu-id="8fe76-204">예를 들어 Microsoft SQL Server 에이전트에 대 한 계정은 주소에서 전자 메일을 보낼 수 있습니다 **SqlAgent@Adventure-Works.com** .</span><span class="sxs-lookup"><span data-stu-id="8fe76-204">For example, an account for Microsoft SQL Server Agent may send e-mail from the address **SqlAgent@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="8fe76-205">**표시 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-205">**Display name**</span></span>  
 <span data-ttu-id="8fe76-206">이 계정을 사용하여 보낼 전자 메일 메시지에 표시할 이름을 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-206">View or update the name to show on e-mail messages sent from this account.</span></span> <span data-ttu-id="8fe76-207">표시 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-207">The display name is optional.</span></span> <span data-ttu-id="8fe76-208">이 이름은 이 계정에서 보내는 메시지에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-208">This is the name displayed on messages sent from this account.</span></span> <span data-ttu-id="8fe76-209">예를 들어 SQL Server 에이전트의 계정은 메일 메시지에 **SQL Server Agent Automated Mailer** 의 이름을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-209">For example, an account for SQL Server Agent may display the name **SQL Server Agent Automated Mailer** on e-mail messages.</span></span>  
  
 <span data-ttu-id="8fe76-210">**회신 전자 메일**</span><span class="sxs-lookup"><span data-stu-id="8fe76-210">**Reply e-mail**</span></span>  
 <span data-ttu-id="8fe76-211">이 계정에서 보낸 전자 메일 메시지에 대한 회신에 사용할 전자 메일 주소를 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-211">View or update the e-mail address that will be used for replies to e-mail messages sent from this account.</span></span> <span data-ttu-id="8fe76-212">회신 전자 메일은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-212">The reply e-mail is optional.</span></span> <span data-ttu-id="8fe76-213">예를 들어 SQL Server 에이전트 계정에 대 한 회신은 데이터베이스 관리자 인로 이동할 수 있습니다 **danw@Adventure-Works.com** .</span><span class="sxs-lookup"><span data-stu-id="8fe76-213">For example, replies to an account for SQL Server Agent may go to the database administrator, **danw@Adventure-Works.com**.</span></span>  
  
 <span data-ttu-id="8fe76-214">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-214">**Server name**</span></span>  
 <span data-ttu-id="8fe76-215">계정에서 전자 메일 전송을 위해 사용하는 SMTP 서버의 이름을 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-215">View or update the name of the SMTP server the account uses to send e-mail.</span></span> <span data-ttu-id="8fe76-216">일반적으로 이 주소는 **smtp.<your_company>.com**과 유사한 형식으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-216">Typically this is in a format similar to **smtp.<your_company>.com**.</span></span> <span data-ttu-id="8fe76-217">이에 대한 도움을 얻으려면 메일 관리자에게 문의하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-217">For help with this, consult your mail administrator.</span></span>  
  
 <span data-ttu-id="8fe76-218">**포트 번호**</span><span class="sxs-lookup"><span data-stu-id="8fe76-218">**Port number**</span></span>  
 <span data-ttu-id="8fe76-219">이 계정에 대한 SMTP 서버의 포트 번호를 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-219">View or update the port number of the SMTP server for this account.</span></span> <span data-ttu-id="8fe76-220">대부분의 SMTP 서버에서는 포트 25를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-220">Most SMTP servers use port 25.</span></span>  
  
 <span data-ttu-id="8fe76-221">**이 서버에는 보안 연결(SSL)이 필요합니다.**</span><span class="sxs-lookup"><span data-stu-id="8fe76-221">**This server requires a secure connection (SSL)**</span></span>  
 <span data-ttu-id="8fe76-222">SSL(Secure Sockets Layer)을 사용하여 통신을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-222">Encrypts communication using Secure Sockets Layer.</span></span>  
  
 <span data-ttu-id="8fe76-223">**데이터베이스 엔진 서비스 자격 증명을 사용한 Windows 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-223">**Windows Authentication using Database Engine service credentials**</span></span>  
 <span data-ttu-id="8fe76-224">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스에 대해 구성된 자격 증명을 사용하여 SMTP 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-224">Connection is made to the SMTP server using the credentials configured for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service.</span></span>  
  
 <span data-ttu-id="8fe76-225">**기본 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-225">**Basic Authentication**</span></span>  
 <span data-ttu-id="8fe76-226">SMTP 서버에 필요한 사용자 이름과 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-226">Specify the user name and password required by the SMTP server.</span></span>  
  
 <span data-ttu-id="8fe76-227">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-227">**User name**</span></span>  
 <span data-ttu-id="8fe76-228">데이터베이스 메일에서 SMTP 서버에 로그인하는 데 사용하는 사용자 이름을 확인하거나 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-228">View or update the user name that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8fe76-229">SMTP 서버에 기본 인증이 필요한 경우 사용자 이름은 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-229">The user name is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-230">**암호**</span><span class="sxs-lookup"><span data-stu-id="8fe76-230">**Password**</span></span>  
 <span data-ttu-id="8fe76-231">데이터베이스 메일에서 SMTP 서버에 로그인하는 데 사용하는 암호를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-231">Change the password that Database Mail uses to log in to the SMTP server.</span></span> <span data-ttu-id="8fe76-232">SMTP 서버에 기본 인증이 필요한 경우 암호는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-232">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-233">**암호 확인**</span><span class="sxs-lookup"><span data-stu-id="8fe76-233">**Confirm password**</span></span>  
 <span data-ttu-id="8fe76-234">암호를 다시 입력하여 암호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-234">Type the password again to confirm the password.</span></span> <span data-ttu-id="8fe76-235">SMTP 서버에 기본 인증이 필요한 경우 암호는 필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-235">The password is required if the SMTP server requires basic authentication.</span></span>  
  
 <span data-ttu-id="8fe76-236">**익명 인증**</span><span class="sxs-lookup"><span data-stu-id="8fe76-236">**Anonymous authentication**</span></span>  
 <span data-ttu-id="8fe76-237">메일이 로그인 자격 증명 없이 SMTP 서버로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-237">Mail is sent to the SMTP server without login credentials.</span></span> <span data-ttu-id="8fe76-238">SMTP 서버에 인증이 필요하지 않은 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-238">Use this option when the SMTP server does not require authentication.</span></span>  
  

  
###  <a name="new-profile-page"></a><a name="NewProfile"></a> <span data-ttu-id="8fe76-239">새 프로필 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-239">New Profile Page</span></span>  
 <span data-ttu-id="8fe76-240">이 페이지를 사용하여 데이터베이스 메일 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-240">Use this page to create a Database Mail profile.</span></span> <span data-ttu-id="8fe76-241">데이터베이스 메일 프로필은 데이터베이스 메일 계정의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-241">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="8fe76-242">프로필은 대체 데이터베이스 메일 계정을 제공하여 전자 메일 서버에 접근할 수 없는 경우에 안정성을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-242">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="8fe76-243">데이터베이스 메일 계정이 적어도 하나 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-243">At least one Database Mail account is required.</span></span> <span data-ttu-id="8fe76-244">프로필에서 데이터베이스 메일 계정의 우선 순위를 설정하는 방법은 [Create a Database Mail Profile](create-a-database-mail-profile.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-244">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="8fe76-245">**위로 이동** 및 **아래로 이동** 단추를 사용하여 데이터베이스 메일 계정이 사용되는 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-245">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="8fe76-246">이 순서는 시퀀스 번호라고 하는 값에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-246">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="8fe76-247">**위로 이동** 을 클릭하면 시퀀스 번호가 낮아지고 **아래로 이동** 을 클릭하면 시퀀스 번호가 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-247">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="8fe76-248">시퀀스 번호는 데이터베이스 메일에서 프로필의 계정을 사용하는 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-248">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="8fe76-249">새 전자 메일 메시지의 경우 데이터베이스 메일은 시퀀스 번호가 가장 낮은 계정에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-249">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="8fe76-250">해당 계정이 실패하면 데이터베이스 메일에서는 시퀀스 번호가 다음으로 높은 계정을 사용하여 메시지가 성공적으로 전송될 때까지 또는 시퀀스 번호가 가장 높은 계정이 실패할 때까지 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-250">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="8fe76-251">시퀀스 번호가 가장 높은 계정이 실패하면 데이터베이스 메일은 데이터베이스 메일 **AccountRetryDelay** 매개 변수에서 구성한 기간 동안 메일을 보내려는 시도를 일시 중지했다가 가장 낮은 시퀀스 번호에서 시작하여 다시 메일 보내기를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-251">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="8fe76-252">데이터베이스 메일 **AccountRetryAttempts** 매개 변수를 사용하여 외부 메일 프로세스가 지정한 프로필의 각 계정을 사용하여 메일 메시지 보내기를 시도하는 시간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-252">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="8fe76-253">데이터베이스 메일 구성 마법사의 **시스템 매개 변수 구성** 페이지에서 **AccountRetryDelay** 및 **AccountRetryAttempts** 매개 변수를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-253">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="8fe76-254">**프로필 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-254">**Profile name**</span></span>  
 <span data-ttu-id="8fe76-255">새 프로필의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-255">Type the name for the new profile.</span></span> <span data-ttu-id="8fe76-256">이 이름으로 프로필이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-256">The profile is created with this name.</span></span> <span data-ttu-id="8fe76-257">기존 프로필의 이름은 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-257">Do not use the name of an existing profile.</span></span>  
  
 <span data-ttu-id="8fe76-258">**설명**</span><span class="sxs-lookup"><span data-stu-id="8fe76-258">**Description**</span></span>  
 <span data-ttu-id="8fe76-259">프로필에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-259">Type a description for the profile.</span></span> <span data-ttu-id="8fe76-260">설명은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-260">The description is optional.</span></span>  
  
 <span data-ttu-id="8fe76-261">**SMTP 계정**</span><span class="sxs-lookup"><span data-stu-id="8fe76-261">**SMTP accounts**</span></span>  
 <span data-ttu-id="8fe76-262">프로필에 대한 계정을 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-262">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="8fe76-263">우선 순위는 데이터베이스 메일에서 계정을 사용하는 순서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-263">The priority sets the order in which Database Mail uses the accounts.</span></span> <span data-ttu-id="8fe76-264">나열된 계정이 없는 경우 계속하려면 **추가** 를 클릭한 다음 새 SMTP 계정을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-264">If no accounts are listed, you must click **Add** to continue, and add a new SMTP account.</span></span>  
  
 <span data-ttu-id="8fe76-265">**추가**</span><span class="sxs-lookup"><span data-stu-id="8fe76-265">**Add**</span></span>  
 <span data-ttu-id="8fe76-266">프로필에 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-266">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="8fe76-267">**제거**</span><span class="sxs-lookup"><span data-stu-id="8fe76-267">**Remove**</span></span>  
 <span data-ttu-id="8fe76-268">선택한 계정을 프로필에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-268">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="8fe76-269">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="8fe76-269">**Move Up**</span></span>  
 <span data-ttu-id="8fe76-270">선택한 계정의 우선 순위를 높입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-270">Increase the priority of the selected account.</span></span>  
  
 <span data-ttu-id="8fe76-271">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="8fe76-271">**Move Down**</span></span>  
 <span data-ttu-id="8fe76-272">선택한 계정의 우선 순위를 낮춥니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-272">Decrease the priority of the selected account.</span></span>  
  

  
###  <a name="manage-existing-profile-page"></a><a name="ExistingProfile"></a><span data-ttu-id="8fe76-273">기존 프로필 관리 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-273">Manage Existing Profile Page</span></span>  
 <span data-ttu-id="8fe76-274">이 페이지를 사용하여 기존 데이터베이스 메일 프로필을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-274">Use this page to manage an existing Database Mail profile.</span></span> <span data-ttu-id="8fe76-275">데이터베이스 메일 프로필은 데이터베이스 메일 계정의 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-275">A Database Mail profile is a collection of Database Mail accounts.</span></span> <span data-ttu-id="8fe76-276">프로필은 대체 데이터베이스 메일 계정을 제공하여 전자 메일 서버에 접근할 수 없는 경우에 안정성을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-276">Profiles improve reliability in cases where an e-mail server becomes unreachable, by providing alternative Database Mail accounts.</span></span> <span data-ttu-id="8fe76-277">데이터베이스 메일 계정이 적어도 하나 이상 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-277">At least one Database Mail account is required.</span></span> <span data-ttu-id="8fe76-278">프로필에서 데이터베이스 메일 계정의 우선 순위를 설정하는 방법은 [Create a Database Mail Profile](create-a-database-mail-profile.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-278">For more information about setting the priority of Database Mail accounts in the profile, see [Create a Database Mail Profile](create-a-database-mail-profile.md).</span></span>  
  
 <span data-ttu-id="8fe76-279">**위로 이동** 및 **아래로 이동** 단추를 사용하여 데이터베이스 메일 계정이 사용되는 순서를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-279">Use the **Move Up** and **Move Down** buttons to change the order in which Database Mail accounts are used.</span></span> <span data-ttu-id="8fe76-280">이 순서는 시퀀스 번호라고 하는 값에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-280">This order is determined by a value called the sequence number.</span></span> <span data-ttu-id="8fe76-281">**위로 이동** 을 클릭하면 시퀀스 번호가 낮아지고 **아래로 이동** 을 클릭하면 시퀀스 번호가 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-281">**Move Up** lowers the sequence number and **Move Down** increases the sequence number.</span></span> <span data-ttu-id="8fe76-282">시퀀스 번호는 데이터베이스 메일에서 프로필의 계정을 사용하는 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-282">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="8fe76-283">새 전자 메일 메시지의 경우 데이터베이스 메일은 시퀀스 번호가 가장 낮은 계정에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-283">For a new e-mail message, Database Mail starts with the account that has the lowest sequence number.</span></span> <span data-ttu-id="8fe76-284">해당 계정이 실패하면 데이터베이스 메일에서는 시퀀스 번호가 다음으로 높은 계정을 사용하여 메시지가 성공적으로 전송될 때까지 또는 시퀀스 번호가 가장 높은 계정이 실패할 때까지 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-284">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="8fe76-285">시퀀스 번호가 가장 높은 계정이 실패하면 데이터베이스 메일은 데이터베이스 메일 **AccountRetryDelay** 매개 변수에서 구성한 기간 동안 메일을 보내려는 시도를 일시 중지했다가 가장 낮은 시퀀스 번호에서 시작하여 다시 메일 보내기를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-285">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the Database Mail **AccountRetryDelay** parameter, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="8fe76-286">데이터베이스 메일 **AccountRetryAttempts** 매개 변수를 사용하여 외부 메일 프로세스가 지정한 프로필의 각 계정을 사용하여 메일 메시지 보내기를 시도하는 시간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-286">Use the Database Mail **AccountRetryAttempts** parameter, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span> <span data-ttu-id="8fe76-287">데이터베이스 메일 구성 마법사의 **시스템 매개 변수 구성** 페이지에서 **AccountRetryDelay** 및 **AccountRetryAttempts** 매개 변수를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-287">You can configure the **AccountRetryDelay** and **AccountRetryAttempts** parameters on the **Configure System Parameters** page of the Database Mail Configuration Wizard.</span></span>  
  
 <span data-ttu-id="8fe76-288">**프로필 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-288">**Profile name**</span></span>  
 <span data-ttu-id="8fe76-289">관리할 프로필의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-289">Select the name of the profile to manage.</span></span>  
  
 <span data-ttu-id="8fe76-290">**삭제**</span><span class="sxs-lookup"><span data-stu-id="8fe76-290">**Delete**</span></span>  
 <span data-ttu-id="8fe76-291">선택한 프로필을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-291">Delete the selected profile.</span></span> <span data-ttu-id="8fe76-292">메시지가 표시되는 경우 선택한 프로필을 삭제하고 보내지 않은 메시지가 모두 실패하도록 하려면 **예** 를 선택하고 보내지 않은 메시지가 없을 경우에만 선택한 프로필을 삭제하려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-292">You will be prompted to select **Yes** to delete the selected profile and to fail any unsent messages, or to select **No** to delete the selected profile only if there are no unsent messages.</span></span>  
  
 <span data-ttu-id="8fe76-293">**설명**</span><span class="sxs-lookup"><span data-stu-id="8fe76-293">**Description**</span></span>  
 <span data-ttu-id="8fe76-294">선택한 프로필에 대한 설명을 보거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-294">View or change the description of the selected profile.</span></span> <span data-ttu-id="8fe76-295">설명은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-295">The description is optional.</span></span>  
  
 <span data-ttu-id="8fe76-296">**SMTP 계정**</span><span class="sxs-lookup"><span data-stu-id="8fe76-296">**SMTP accounts**</span></span>  
 <span data-ttu-id="8fe76-297">프로필에 대한 계정을 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-297">Choose one or more accounts for the profile.</span></span> <span data-ttu-id="8fe76-298">장애 조치(Failover) 우선 순위는 장애 조치 시 데이터베이스 메일에서 계정을 사용하는 순서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-298">The failover priority sets the order in which Database Mail uses the account in case of a failover.</span></span>  
  
 <span data-ttu-id="8fe76-299">**추가**</span><span class="sxs-lookup"><span data-stu-id="8fe76-299">**Add**</span></span>  
 <span data-ttu-id="8fe76-300">프로필에 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-300">Add an account to the profile.</span></span>  
  
 <span data-ttu-id="8fe76-301">**제거**</span><span class="sxs-lookup"><span data-stu-id="8fe76-301">**Remove**</span></span>  
 <span data-ttu-id="8fe76-302">선택한 계정을 프로필에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-302">Remove the selected account from the profile.</span></span>  
  
 <span data-ttu-id="8fe76-303">**위로 이동**</span><span class="sxs-lookup"><span data-stu-id="8fe76-303">**Move Up**</span></span>  
 <span data-ttu-id="8fe76-304">선택한 계정의 장애 조치 우선 순위를 높입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-304">Increase the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="8fe76-305">**아래로 이동**</span><span class="sxs-lookup"><span data-stu-id="8fe76-305">**Move Down**</span></span>  
 <span data-ttu-id="8fe76-306">선택한 계정의 장애 조치 우선 순위를 낮춥니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-306">Decrease the failover priority of the selected account.</span></span>  
  
 <span data-ttu-id="8fe76-307">**우선 순위**</span><span class="sxs-lookup"><span data-stu-id="8fe76-307">**Priority**</span></span>  
 <span data-ttu-id="8fe76-308">계정의 현재 장애 조치 우선 순위를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-308">View the current failover priority of the account.</span></span>  
  
 <span data-ttu-id="8fe76-309">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-309">**Account name**</span></span>  
 <span data-ttu-id="8fe76-310">계정의 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-310">View the name of the account.</span></span>  
  
 <span data-ttu-id="8fe76-311">**전자 메일 주소**</span><span class="sxs-lookup"><span data-stu-id="8fe76-311">**E-mail Address**</span></span>  
 <span data-ttu-id="8fe76-312">계정의 전자 메일 주소를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-312">View the e-mail address of the account.</span></span>  
  

  
###  <a name="add-account-to-profile-page"></a><a name="AddAccount"></a><span data-ttu-id="8fe76-313">프로필에 계정 추가 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-313">Add Account to Profile Page</span></span>  
 <span data-ttu-id="8fe76-314">이 페이지를 사용하여 프로필에 추가할 계정을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-314">Use this page to choose the account to add to the profile.</span></span> <span data-ttu-id="8fe76-315">**계정 이름** 상자에서 기존 계정을 선택하거나 **새 계정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-315">Either choose an existing account from the **Account name** box, or click **New Account**.</span></span>  
  
 <span data-ttu-id="8fe76-316">**계정 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-316">**Account name**</span></span>  
 <span data-ttu-id="8fe76-317">프로필에 추가할 계정의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-317">Select the name of the account to add to the profile.</span></span>  
  
 <span data-ttu-id="8fe76-318">**전자 메일 주소**</span><span class="sxs-lookup"><span data-stu-id="8fe76-318">**E-mail address**</span></span>  
 <span data-ttu-id="8fe76-319">선택한 계정의 전자 메일 주소를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-319">View the e-mail address for the selected account.</span></span> <span data-ttu-id="8fe76-320">이 페이지에서는 전자 메일 주소를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-320">You cannot change the e-mail address from this page.</span></span> <span data-ttu-id="8fe76-321">계정의 메일 주소를 변경하려면 마법사의 기본 페이지로 돌아가서 **데이터베이스 메일 계정 및 프로필 관리** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-321">To change the e-mail address for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="8fe76-322">**서버 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-322">**Server name**</span></span>  
 <span data-ttu-id="8fe76-323">선택한 계정의 메일 서버 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-323">View the mail server name for the selected account.</span></span> <span data-ttu-id="8fe76-324">이 페이지에서는 서버 이름을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-324">You cannot change the server name from this page.</span></span> <span data-ttu-id="8fe76-325">계정의 서버 이름을 변경하려면 마법사의 기본 페이지로 돌아가서 **데이터베이스 메일 계정 및 프로필 관리** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-325">To change the server name for the account, go back to the main page of the wizard and select the **Manage Database Mail accounts and profiles** option.</span></span>  
  
 <span data-ttu-id="8fe76-326">**새 계정**</span><span class="sxs-lookup"><span data-stu-id="8fe76-326">**New Account**</span></span>  
 <span data-ttu-id="8fe76-327">새 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-327">Create a new account.</span></span>  
  

  
###  <a name="manage-accounts-and-profiles-page"></a><a name="AccountsProfiles"></a> <span data-ttu-id="8fe76-328">프로필 및 계정 관리 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-328">Manage Accounts and Profiles Page</span></span>  
 <span data-ttu-id="8fe76-329">이 페이지를 사용하여 프로필 또는 계정을 관리하는 태스크를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-329">Use this page to choose a task for managing a profile or account.</span></span>  
  
 <span data-ttu-id="8fe76-330">**새 계정 만들기**</span><span class="sxs-lookup"><span data-stu-id="8fe76-330">**Create a new account**</span></span>  
 <span data-ttu-id="8fe76-331">새 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-331">Create a new account.</span></span>  
  
 <span data-ttu-id="8fe76-332">**기존 계정 확인, 변경 또는 삭제**</span><span class="sxs-lookup"><span data-stu-id="8fe76-332">**View, change or delete an existing account**</span></span>  
 <span data-ttu-id="8fe76-333">기존 계정을 관리하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-333">Manage or delete an existing account.</span></span>  
  
 <span data-ttu-id="8fe76-334">**새 프로필 만들기**</span><span class="sxs-lookup"><span data-stu-id="8fe76-334">**Create a new profile**</span></span>  
 <span data-ttu-id="8fe76-335">새 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-335">Create a new profile.</span></span>  
  
 <span data-ttu-id="8fe76-336">**기존 프로필을 확인, 변경 또는 삭제 합니다. 프로필에 연결 된 계정을 관리할 수도 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8fe76-336">**View, change or delete an existing profile. You can also manage accounts associated with the profile.**</span></span>  
 <span data-ttu-id="8fe76-337">기존 프로필을 업데이트하거나 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-337">Update or delete an existing profile.</span></span> <span data-ttu-id="8fe76-338">이 옵션을 사용하면 프로필에 연결된 계정을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-338">This option also allows you to manage accounts associated with the profile.</span></span>  
  

  
###  <a name="manage-profile-security-public-tab"></a><a name="ProfileSecurityPublic"></a><span data-ttu-id="8fe76-339">프로필 보안 관리, 공개 탭</span><span class="sxs-lookup"><span data-stu-id="8fe76-339">Manage Profile Security, Public Tab</span></span>  
 <span data-ttu-id="8fe76-340">이 페이지를 사용하여 공개 프로필을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-340">Use this page to configure a public profile.</span></span>  
  
 <span data-ttu-id="8fe76-341">프로필에는 퍼블릭 프로필과 프라이빗 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-341">Profiles are either public or private.</span></span> <span data-ttu-id="8fe76-342">프라이빗 프로필은 특정 사용자나 역할만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-342">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="8fe76-343">공개 프로필은 메일 호스트 데이터베이스(**msdb**)에 액세스할 수 있는 모든 사용자나 역할이 사용할 수 있으며 해당 프로필을 사용하여 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-343">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="8fe76-344">프로필은 기본 프로필일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-344">A profile may be a default profile.</span></span> <span data-ttu-id="8fe76-345">이 경우 사용자나 역할은 명시적으로 프로필을 지정하지 않고도 프로필을 사용하여 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-345">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="8fe76-346">전자 메일 메시지를 보내는 사용자나 역할에 기본 프라이빗 프로필이 있을 경우 데이터베이스 메일은 해당 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-346">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="8fe76-347">사용자나 역할에 기본 프라이빗 프로필이 없을 경우 **sp_send_dbmail**은 **msdb** 데이터베이스의 기본 퍼블릭 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-347">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="8fe76-348">사용자 또는 역할의 기본 프라이빗 프로필과 데이터베이스의 기본 퍼블릭 프로필이 둘 다 없을 경우 **sp_send_dbmail**은 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-348">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span> <span data-ttu-id="8fe76-349">하나의 프로필만 기본 프로필로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-349">Only one profile can be marked as the default profile.</span></span>  
  
 <span data-ttu-id="8fe76-350">**공용**</span><span class="sxs-lookup"><span data-stu-id="8fe76-350">**Public**</span></span>  
 <span data-ttu-id="8fe76-351">지정된 프로필을 공개 프로필로 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-351">Select this option to make the specified profile public.</span></span>  
  
 <span data-ttu-id="8fe76-352">**프로필 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-352">**Profile Name**</span></span>  
 <span data-ttu-id="8fe76-353">프로필 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-353">Displays the name of the profile.</span></span>  
  
 <span data-ttu-id="8fe76-354">**기본 프로필**</span><span class="sxs-lookup"><span data-stu-id="8fe76-354">**Default Profile**</span></span>  
 <span data-ttu-id="8fe76-355">지정된 프로필을 기본 프로필로 지정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-355">Select this option to make the specified profile the default profile.</span></span>  
  
 <span data-ttu-id="8fe76-356">**기존 공개 프로필만 표시**</span><span class="sxs-lookup"><span data-stu-id="8fe76-356">**Show only existing public profiles**</span></span>  
 <span data-ttu-id="8fe76-357">특정 데이터베이스에 있는 공개 프로필만 보려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-357">Select this option to show only public profiles in the specified database.</span></span>  
  

  
###  <a name="manage-profile-security-private-tab"></a><a name="ProfileSecurityPrivate"></a><span data-ttu-id="8fe76-358">프로필 보안 관리, 개인 탭</span><span class="sxs-lookup"><span data-stu-id="8fe76-358">Manage Profile Security, Private Tab</span></span>  
 <span data-ttu-id="8fe76-359">이 페이지를 사용하여 프라이빗 프로필을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-359">Use this page to configure a private profile.</span></span>  
  
 <span data-ttu-id="8fe76-360">프로필에는 퍼블릭 프로필과 프라이빗 프로필이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-360">Profiles are either public or private.</span></span> <span data-ttu-id="8fe76-361">프라이빗 프로필은 특정 사용자나 역할만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-361">A private profile is accessible only to specific users or roles.</span></span> <span data-ttu-id="8fe76-362">공개 프로필은 메일 호스트 데이터베이스(**msdb**)에 액세스할 수 있는 모든 사용자나 역할이 사용할 수 있으며 해당 프로필을 사용하여 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-362">A public profile allows any user or role with access to the mail host database (**msdb**) to send e-mail using that profile.</span></span>  
  
 <span data-ttu-id="8fe76-363">프로필은 기본 프로필일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-363">A profile may be a default profile.</span></span> <span data-ttu-id="8fe76-364">이 경우 사용자나 역할은 명시적으로 프로필을 지정하지 않고도 프로필을 사용하여 전자 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-364">In this case, users or roles can send e-mail using the profile without explicitly specifying the profile.</span></span> <span data-ttu-id="8fe76-365">전자 메일 메시지를 보내는 사용자나 역할에 기본 프라이빗 프로필이 있을 경우 데이터베이스 메일은 해당 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-365">If the user or role sending the e-mail message has a default private profile, Database Mail uses that profile.</span></span> <span data-ttu-id="8fe76-366">사용자나 역할에 기본 프라이빗 프로필이 없을 경우 **sp_send_dbmail**은 **msdb** 데이터베이스의 기본 퍼블릭 프로필을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-366">If the user or role has no default private profile, **sp_send_dbmail** uses the default public profile for the **msdb** database.</span></span> <span data-ttu-id="8fe76-367">사용자 또는 역할의 기본 프라이빗 프로필과 데이터베이스의 기본 퍼블릭 프로필이 둘 다 없을 경우 **sp_send_dbmail**은 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-367">If there is no default private profile for the user or role and no default public profile for the database, **sp_send_dbmail** returns an error.</span></span>  
  
 <span data-ttu-id="8fe76-368">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-368">**User name**</span></span>  
 <span data-ttu-id="8fe76-369">**msdb** 데이터베이스에서 사용자 또는 역할 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-369">Select the name of a user or role in the **msdb** database.</span></span>  
  
 <span data-ttu-id="8fe76-370">**Access**</span><span class="sxs-lookup"><span data-stu-id="8fe76-370">**Access**</span></span>  
 <span data-ttu-id="8fe76-371">해당 사용자나 역할이 특정 프로필에 액세스 권한이 있는지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-371">Select whether the user or role has access to the specified profile.</span></span>  
  
 <span data-ttu-id="8fe76-372">**프로필 이름**</span><span class="sxs-lookup"><span data-stu-id="8fe76-372">**Profile name**</span></span>  
 <span data-ttu-id="8fe76-373">프로필 이름을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-373">View the name of the profile.</span></span>  
  
 <span data-ttu-id="8fe76-374">**기본 프로필 여부**</span><span class="sxs-lookup"><span data-stu-id="8fe76-374">**Is Default Profile**</span></span>  
 <span data-ttu-id="8fe76-375">이 프로필이 사용자 또는 역할의 기본 프로필인지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-375">Select whether the profile is the default profile for the user or role.</span></span> <span data-ttu-id="8fe76-376">각각의 사용자 또는 역할은 하나의 기본 프로필만 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-376">Each user or role may have only one default profile.</span></span>  
  
 <span data-ttu-id="8fe76-377">**이 사용자의 기존 프라이빗 프로필만 표시**</span><span class="sxs-lookup"><span data-stu-id="8fe76-377">**Show only existing private profiles for this user**</span></span>  
 <span data-ttu-id="8fe76-378">지정된 사용자 또는 역할이 이미 액세스 권한을 가진 프로필만 표시하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-378">Select this option to display only profiles that the specified user or role already has access to.</span></span>  
  

  
###  <a name="configure-system-parameters"></a><a name="SystemParameters"></a><span data-ttu-id="8fe76-379">시스템 매개 변수 구성</span><span class="sxs-lookup"><span data-stu-id="8fe76-379">Configure System Parameters</span></span>  
 <span data-ttu-id="8fe76-380">이 페이지를 사용하여 데이터베이스 메일 시스템 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-380">Use this page to specify Database Mail system parameters.</span></span> <span data-ttu-id="8fe76-381">이 페이지에서 시스템 매개 변수와 각 매개 변수의 현재 값을 볼 수 있으며</span><span class="sxs-lookup"><span data-stu-id="8fe76-381">View the system parameters and the current value of each parameter.</span></span> <span data-ttu-id="8fe76-382">매개 변수를 선택하면 정보 창에 표시되는 짧은 설명도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-382">Select a parameter to view a short description in the information pane.</span></span>  
  
 <span data-ttu-id="8fe76-383">**계정 다시 시도 횟수**</span><span class="sxs-lookup"><span data-stu-id="8fe76-383">**Account Retry Attempts**</span></span>  
 <span data-ttu-id="8fe76-384">외부 메일 프로세스에서 지정된 프로필의 각 계정을 사용하여 전자 메일 메시지를 보내려고 시도하는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-384">The number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="8fe76-385">**계정 다시 시도 간격(초)**</span><span class="sxs-lookup"><span data-stu-id="8fe76-385">**Account Retry Delay (seconds)**</span></span>  
 <span data-ttu-id="8fe76-386">외부 메일 프로세스가 프로필의 모든 계정을 사용하여 메시지 보내기를 시도한 후 모든 계정에 대해 다시 시도하기 전까지 대기하는 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-386">The amount of time, in seconds, for the external mail process to wait after it tries to deliver a message using all accounts in the profile before it attempts all accounts again.</span></span>  
  
 <span data-ttu-id="8fe76-387">**최대 파일 크기(바이트)**</span><span class="sxs-lookup"><span data-stu-id="8fe76-387">**Maximum File Size (Bytes)**</span></span>  
 <span data-ttu-id="8fe76-388">첨부 파일의 최대 크기(바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-388">The maximum size of an attachment, in bytes.</span></span>  
  
 <span data-ttu-id="8fe76-389">**금지할 첨부 파일 확장명**</span><span class="sxs-lookup"><span data-stu-id="8fe76-389">**Prohibited Attachment File Extensions**</span></span>  
 <span data-ttu-id="8fe76-390">전자 메일 메시지에 대한 첨부 파일로 보낼 수 없는 쉼표로 구분된 확장명 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-390">A comma-separated list of extensions which cannot be sent as an attachment to an e-mail message.</span></span> <span data-ttu-id="8fe76-391">확장명을 추가하려면 찾아보기 단추(**...**)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-391">Click the browse button (**...**) to add additional extensions.</span></span>  
  
 <span data-ttu-id="8fe76-392">**데이터베이스 메일 실행 파일의 최소 수명(초)**</span><span class="sxs-lookup"><span data-stu-id="8fe76-392">**Database Mail Executable Minimum Lifetime (seconds)**</span></span>  
 <span data-ttu-id="8fe76-393">외부 메일 프로세스가 활성 상태로 유지되는 최소 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-393">The minimum amount of time, in seconds, that the external mail process remains active.</span></span> <span data-ttu-id="8fe76-394">데이터베이스 메일 큐에 전자 메일이 있는 한 프로세스는 활성 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-394">The process remains active as long as there are e-mails in the Database Mail queue.</span></span> <span data-ttu-id="8fe76-395">이 매개 변수는 처리할 메시지가 없을 경우 해당 프로세스를 활성 상태로 유지할 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-395">This parameter specifies the time the process remains active if there are no messages to process.</span></span>  
  
 <span data-ttu-id="8fe76-396">**로깅 수준**</span><span class="sxs-lookup"><span data-stu-id="8fe76-396">**Logging level**</span></span>  
 <span data-ttu-id="8fe76-397">데이터베이스 메일 로그에 기록할 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-397">Specify which messages are recorded in the Database Mail log.</span></span> <span data-ttu-id="8fe76-398">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-398">Possible values are:</span></span>  
  
-   <span data-ttu-id="8fe76-399">보통 - 오류만 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-399">Normal - logs only errors</span></span>  
  
-   <span data-ttu-id="8fe76-400">확장 - 오류, 경고 및 정보 메시지를 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-400">Extended - logs errors, warnings, and informational messages</span></span>  
  
-   <span data-ttu-id="8fe76-401">자세히 - 오류, 경고, 정보 메시지, 성공 메시지 및 추가 내부 메시지를 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-401">Verbose - logs errors, warnings, informational messages, success messages, and additional internal messages.</span></span> <span data-ttu-id="8fe76-402">자세한 로깅은 문제 해결에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-402">Use verbose logging for troubleshooting.</span></span>  
  
 <span data-ttu-id="8fe76-403">기본값은 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-403">Default value is Extended.</span></span>  
  
 <span data-ttu-id="8fe76-404">**모두 다시 설정**</span><span class="sxs-lookup"><span data-stu-id="8fe76-404">**Reset All**</span></span>  
 <span data-ttu-id="8fe76-405">페이지의 값을 기본값으로 다시 설정하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-405">Select this option to reset the values on the page to the default values.</span></span>  
  

  
###  <a name="complete-the-wizard-page"></a><a name="CompleteWizard"></a><span data-ttu-id="8fe76-406">마법사 완료 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-406">Complete the Wizard Page</span></span>  
 <span data-ttu-id="8fe76-407">이 페이지를 사용하여 **데이터베이스 메일 구성 마법사** 가 수행할 동작을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-407">Use this page to review the actions that **Database Mail Configuration Wizard** will perform.</span></span> <span data-ttu-id="8fe76-408">마법사를 끝내기 전까지는 변경 내용이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-408">No changes are made until you finish the wizard.</span></span>  
  

  
###  <a name="send-test-e-mail-page"></a><a name="TestEmail"></a><span data-ttu-id="8fe76-409">테스트 전자 메일 보내기 페이지</span><span class="sxs-lookup"><span data-stu-id="8fe76-409">Send Test E-Mail Page</span></span>  
 <span data-ttu-id="8fe76-410">_<instance_name>_ 에서 **테스트 메일 보내기** 페이지를 사용하여 지정된 데이터베이스 메일 프로필을 통해 메일 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-410">Use the **Send Test E-Mail from**_<instance_name>_ page to send an e-mail message using the specified Database Mail profile.</span></span> <span data-ttu-id="8fe76-411">**sysadmin** 고정 서버 역할의 멤버만 이 페이지를 사용하여 테스트 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-411">Only members of the **sysadmin** fixed server role can send test e-mail using this page.</span></span>  
  
 <span data-ttu-id="8fe76-412">**데이터베이스 메일 프로필**</span><span class="sxs-lookup"><span data-stu-id="8fe76-412">**Database Mail Profile**</span></span>  
 <span data-ttu-id="8fe76-413">목록에서 데이터베이스 메일 프로필을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-413">Select a Database Mail profile from the list.</span></span> <span data-ttu-id="8fe76-414">이 이름은 반드시 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-414">This is a required field.</span></span> <span data-ttu-id="8fe76-415">아무 프로필도 나타나지 않으면 프로필이 없거나 프로필에 대한 권한이 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-415">If no profiles are shown, there are no profiles or you do not have permission to a profile.</span></span> <span data-ttu-id="8fe76-416">**데이터베이스 메일 구성 마법사** 를 사용하여 프로필을 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-416">Use the **Database Mail Configuration Wizard** to create and configure profiles.</span></span> <span data-ttu-id="8fe76-417">나열되는 프로필이 없을 경우 데이터베이스 메일 구성 마법사를 통해 사용할 프로필을 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-417">If no profiles are listed, use the Database Mail Configuration Wizard to create a profile for your use.</span></span>  
  
 <span data-ttu-id="8fe76-418">**수행할 작업**</span><span class="sxs-lookup"><span data-stu-id="8fe76-418">**To**</span></span>  
 <span data-ttu-id="8fe76-419">메시지를 받는 사람의 전자 메일 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-419">The e-mail address of the message recipients.</span></span> <span data-ttu-id="8fe76-420">받는 사람은 한 명 이상 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-420">At least one recipient is required.</span></span>  
  
 <span data-ttu-id="8fe76-421">**Subject**</span><span class="sxs-lookup"><span data-stu-id="8fe76-421">**Subject**</span></span>  
 <span data-ttu-id="8fe76-422">테스트 전자 메일의 제목입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-422">The subject line for the test e-mail.</span></span> <span data-ttu-id="8fe76-423">문제 해결을 위해 사용자의 전자 메일을 보다 잘 식별할 수 있도록 기본 제목을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-423">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="8fe76-424">**본문**</span><span class="sxs-lookup"><span data-stu-id="8fe76-424">**Body**</span></span>  
 <span data-ttu-id="8fe76-425">테스트 전자 메일의 본문입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-425">The body of the test e-mail.</span></span> <span data-ttu-id="8fe76-426">문제 해결을 위해 사용자의 전자 메일을 보다 잘 식별할 수 있도록 기본 제목을 변경하십시오.</span><span class="sxs-lookup"><span data-stu-id="8fe76-426">Change the default subject to better identify your email for troubleshooting.</span></span>  
  
 <span data-ttu-id="8fe76-427">**데이터베이스 메일 테스트 메일** 대화 상자에서 데이터베이스 메일이 메시지 보내기를 시도할 테스트 메시지를 확인하고 테스트 메일 메시지에 대한 **mailitem_id** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-427">The **Database Mail Test E-Mail** dialog box confirms that the test message that Database Mail attempted to send the message and provides the **mailitem_id** for the test e-mail message.</span></span> <span data-ttu-id="8fe76-428">받는 사람에게 전자 메일이 도착했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-428">Check with the recipient to determine if the e-mail arrived.</span></span> <span data-ttu-id="8fe76-429">전자 메일은 보통 몇 분 안에 도착하지만 네트워크의 낮은 성능, 메일 서버로의 메시지 백로그, 서버의 일시적 사용 불가 상태 등에 따라 지연될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-429">Normally e-mail is received in a few minutes, but the e-mail can be delayed because of slow network performance, a backlog of messages at the mail server, or if the server is temporarily unavailable.</span></span> <span data-ttu-id="8fe76-430">문제 해결을 위해 **mailitem_id** 를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="8fe76-430">Use the **mailitem_id** for troubleshooting.</span></span>  
  
 <span data-ttu-id="8fe76-431">**보낸 전자 메일**</span><span class="sxs-lookup"><span data-stu-id="8fe76-431">**Sent e-mail**</span></span>  
 <span data-ttu-id="8fe76-432">테스트 메일 메시지의 **mailitem_id** 입니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-432">The **mailitem_id** of the test e-mail message.</span></span>  
  
 <span data-ttu-id="8fe76-433">**문제 해결**</span><span class="sxs-lookup"><span data-stu-id="8fe76-433">**Troubleshoot**</span></span>  
 <span data-ttu-id="8fe76-434">온라인 설명서의 [데이터베이스 메일 문제 해결](https://msdn.microsoft.com/library/ms188663.aspx)항목을 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-434">Click to open Books Online to the [Troubleshooting Database Mail](https://msdn.microsoft.com/library/ms188663.aspx)topic.</span></span>  
  

  
##  <a name="using-templates"></a><a name="Template"></a><span data-ttu-id="8fe76-435">템플릿 사용</span><span class="sxs-lookup"><span data-stu-id="8fe76-435">Using Templates</span></span>  
 <span data-ttu-id="8fe76-436">**데이터베이스 메일 구성 스크립트를 만들려면**</span><span class="sxs-lookup"><span data-stu-id="8fe76-436">**To create a Database Mail configuration script**</span></span>  
  
1.  <span data-ttu-id="8fe76-437">**보기** 메뉴에서 **템플릿 탐색기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-437">On the **View** menu, select **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="8fe76-438">**템플릿 탐색기** 창에서 **데이터베이스 메일** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-438">In the **Template Explorer** window, expand the **Database Mail** folder.</span></span>  
  
3.  <span data-ttu-id="8fe76-439">**단순 데이터베이스 메일 구성**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-439">Double-click **Simple Database Mail Configuration**.</span></span> <span data-ttu-id="8fe76-440">템플릿이 새 쿼리 창에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-440">The template opens in a new query window.</span></span>  
  
4.  <span data-ttu-id="8fe76-441">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-441">On the **Query** menu, select **Specify Values for Template Parameters**.</span></span> <span data-ttu-id="8fe76-442">**템플릿 매개 변수 값 지정** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-442">The **Replace Template Parameters** window opens.</span></span>  
  
5.  <span data-ttu-id="8fe76-443">**profile_name**, **account_name**, **SMTP_servername**, **email_address**및 **display_name**에 대한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-443">Type values for the **profile_name**, **account_name**, **SMTP_servername**, **email_address**, and **display_name**.</span></span> <span data-ttu-id="8fe76-444">SQL Server Management Studio는 사용자가 제공한 값으로 템플릿을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-444">SQL Server Management Studio fills in the template with the values you provide.</span></span>  
  
6.  <span data-ttu-id="8fe76-445">스크립트를 실행하여 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-445">Execute the script to create the configuration.</span></span>  
  
7.  <span data-ttu-id="8fe76-446">스크립트는 데이터베이스 사용자에게 프로필에 대한 액세스를 부여하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-446">The script does not grant any database users access to the profile.</span></span> <span data-ttu-id="8fe76-447">따라서 기본적으로 프로필은 **sysadmin** 고정 보안 역할의 멤버만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe76-447">Therefore, by default, the profile can only be used by members of the **sysadmin** fixed security role.</span></span> <span data-ttu-id="8fe76-448">프로필에 대한 액세스 권한 부여에 대한 자세한 내용은 [sysmail_add_principalprofile_sp&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8fe76-448">For more information about granting access to profiles, see [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)</span></span>  
  
  
