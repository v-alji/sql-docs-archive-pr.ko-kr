---
title: 데이터베이스 메일 구성 개체 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sqlimail.manageexistingaccount.f1
- sql12.swb.sqlimail.addaccounttoprofile.f1
- sql12.swb.sqlmailconfiguration.f1
- sql12.swb.sqlimail.profileandaccountmanagement.f1
- sql12.swb.sqlimail.manageprofilesecurity.principalview.f1
- sql12.swb.sqlimail.newsqlimailaccount.f1
- sql12.swb.sqlimail.configuresystem.f1
- sql12.swb.sqlimail.selectconfiguration.f1
- sql12.swb.sqlimail.newprofile.f1
- sql12.swb.sqlimail.manageexistingprofile.f1
- sql12.swb.sqlimail.welcome.f1
- sql12.swb.sqlimail.manageprofilesecurity.profileview.f1
- sql12.swb.sqlimail.completewizard.f1
- sql12.swb.sqlimail.newaccount.f1
helpviewer_keywords:
- Database Mail [SQL Server], configuration objects
- Database Mail [SQL Server], accounts
- configuration objects [Database Mail]
- Database Mail [SQL Server], profiles
- profiles [SQL Server], Database Mail
- accounts [Database Mail]
ms.assetid: 03f6e4c0-04ff-490a-bd91-637806215bd1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45dd4bfc8cdb382f9ad093e92c5939986a9db8e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742267"
---
# <a name="database-mail-configuration-objects"></a><span data-ttu-id="72b24-102">데이터베이스 메일 구성 개체</span><span class="sxs-lookup"><span data-stu-id="72b24-102">Database Mail Configuration Objects</span></span>
  <span data-ttu-id="72b24-103">데이터베이스 메일에는 두 가지 구성 개체가 있습니다. 데이터베이스 구성 개체를 사용하면 데이터베이스 애플리케이션 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 메일을 보낼 때 데이터베이스 메일에 사용할 설정을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-103">Database Mail has two configuration objects: The database configuration objects provide a way for you to configure the settings that Database mail should use when sending an email from your database application or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
-   <span data-ttu-id="72b24-104">데이터베이스 메일 계정</span><span class="sxs-lookup"><span data-stu-id="72b24-104">Database Mail accounts</span></span>  
  
-   <span data-ttu-id="72b24-105">데이터베이스 메일 프로필</span><span class="sxs-lookup"><span data-stu-id="72b24-105">Database Mail profiles</span></span>  
  
  
##  <a name="database-mail-configuration-object-relationship"></a><a name="VisualElement"></a> <span data-ttu-id="72b24-106">데이터베이스 메일 구성 개체 관계</span><span class="sxs-lookup"><span data-stu-id="72b24-106">Database Mail Configuration Object Relationship</span></span>  
 <span data-ttu-id="72b24-107">위 그림에서는 2개의 프로필, 3개의 계정 및 3명의 사용자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-107">The illustration shows two profiles, three accounts, and three users.</span></span> <span data-ttu-id="72b24-108">사용자 1은 프로필 1에 대한 액세스 권한이 있고, 이 프로필은 계정 1과 계정 2를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-108">User 1 has access to Profile 1, which uses Account 1 and Account 2.</span></span> <span data-ttu-id="72b24-109">사용자 3은 프로필 2에 대한 액세스 권한이 있고, 이 프로필은 계정 2와 계정 3을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-109">User 3 has access to Profile 2, which uses Account 2 and Account 3.</span></span> <span data-ttu-id="72b24-110">사용자 2는 프로필 1과 프로필 2에 대한 액세스 권한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-110">User 2 has access to both Profile 1 and Profile 2.</span></span>  
  
 <span data-ttu-id="72b24-111">![사용자, 프로필 및 계정 관계](../../database-engine/media/databasemailprofileaccount.gif "사용자, 프로필 및 계정 관계")</span><span class="sxs-lookup"><span data-stu-id="72b24-111">![Relationship of users, profiles, and accounts](../../database-engine/media/databasemailprofileaccount.gif "Relationship of users, profiles, and accounts")</span></span>  
  
  
##  <a name="database-mail-account"></a><a name="DBAccount"></a> <span data-ttu-id="72b24-112">데이터베이스 메일 계정</span><span class="sxs-lookup"><span data-stu-id="72b24-112">Database Mail Account</span></span>  
 <span data-ttu-id="72b24-113">데이터베이스 메일 계정에는 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 전자 메일 메시지를 SMTP 서버로 보내기 위해 사용하는 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-113">A Database Mail account contains the information that Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses to send e-mail messages to an SMTP server.</span></span> <span data-ttu-id="72b24-114">각 계정에는 하나의 전자 메일 서버에 대한 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-114">Each account contains information for one e-mail server.</span></span>  
  
 <span data-ttu-id="72b24-115">데이터베이스 메일은 SMTP 서버와 통신하는 다음 3가지 인증 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-115">A Database Mail supports three methods of authentication to communicate with an SMTP server:</span></span>  
  
-   <span data-ttu-id="72b24-116">Windows 인증: 데이터베이스 메일이 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows 서비스 계정의 자격 증명을 사용하여 SMTP 서버에 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-116">Windows Authentication: Database Mail uses the credentials of the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] Windows service account for authentication on the SMTP server.</span></span>  
  
-   <span data-ttu-id="72b24-117">기본 인증:  데이터베이스 메일이 지정된 사용자 이름과 암호를 사용하여 SMTP 서버에 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-117">Basic Authentication:  Database Mail uses the username and password specified to authenticate on the SMTP server.</span></span>  
  
-   <span data-ttu-id="72b24-118">익명 인증:  SMTP 서버에 인증이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-118">Anonymous Authentication:  The SMTP server does not require any authentication.</span></span>  <span data-ttu-id="72b24-119">데이터베이스 메일은 SMTP 서버 인증에 자격 증명을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-119">Database Mail will not use any credentials to authenticate on the SMTP server.</span></span>  
  
 <span data-ttu-id="72b24-120">계정 정보는 **msdb** 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-120">Account information is stored in the **msdb** database.</span></span> <span data-ttu-id="72b24-121">각 계정은 다음 정보로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-121">Each account consists of the following information:</span></span>  
  
-   <span data-ttu-id="72b24-122">계정 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-122">The name of the account.</span></span>  
  
-   <span data-ttu-id="72b24-123">계정에 대한 설명</span><span class="sxs-lookup"><span data-stu-id="72b24-123">A description of the account.</span></span>  
  
-   <span data-ttu-id="72b24-124">운영자의 전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="72b24-124">The e-mail address of the account.</span></span>  
  
-   <span data-ttu-id="72b24-125">계정의 표시 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-125">The display name for the account.</span></span>  
  
-   <span data-ttu-id="72b24-126">계정에 대한 회신 정보로 사용하는 전자 메일 주소</span><span class="sxs-lookup"><span data-stu-id="72b24-126">The e-mail address to use as the reply-to information for the account.</span></span>  
  
-   <span data-ttu-id="72b24-127">전자 메일 서버의 이름</span><span class="sxs-lookup"><span data-stu-id="72b24-127">The name of the e-mail server.</span></span>  
  
-   <span data-ttu-id="72b24-128">전자 메일 서버의 유형.</span><span class="sxs-lookup"><span data-stu-id="72b24-128">The type of the e-mail server.</span></span> <span data-ttu-id="72b24-129">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 항상 SMTP(Simple Mail Transfer Protocol)입니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-129">For [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this is always Simple Mail Transfer Protocol(SMTP).</span></span>  
  
-   <span data-ttu-id="72b24-130">전자 메일 서버의 포트 번호</span><span class="sxs-lookup"><span data-stu-id="72b24-130">The port number of the e-mail server.</span></span>  
  
-   <span data-ttu-id="72b24-131">SSL(Secure Sockets Layer)을 사용하여 SMTP 메일 서버에 연결하는지 여부를 나타내는 bit 열</span><span class="sxs-lookup"><span data-stu-id="72b24-131">A bit column indicating whether the connection to the SMTP mail server is made using Secure Sockets Layer (SSL).</span></span>  
  
-   <span data-ttu-id="72b24-132">[!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]에 대해 구성된 자격 증명을 사용하여 SMTP 서버에 연결하는지 여부를 나타내는 bit 열</span><span class="sxs-lookup"><span data-stu-id="72b24-132">A bit column indicating whether the connection to the SMTP server is made using the credentials configured for the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="72b24-133">전자 메일 서버에 인증이 필요한 경우 전자 메일 서버에 대한 인증에 사용하는 사용자 이름</span><span class="sxs-lookup"><span data-stu-id="72b24-133">The user name to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
-   <span data-ttu-id="72b24-134">전자 메일 서버에 인증이 필요한 경우 전자 메일 서버에 대한 인증에 사용하는 암호</span><span class="sxs-lookup"><span data-stu-id="72b24-134">The password to use for authentication to the e-mail server, if the e-mail server requires authentication.</span></span>  
  
 <span data-ttu-id="72b24-135">데이터베이스 메일 구성 마법사를 사용하면 편리하게 계정을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-135">The Database Mail Configuration Wizard provides a convenient way to create and manage accounts.</span></span> <span data-ttu-id="72b24-136">또한 **msdb** 의 구성 저장 프로시저를 사용하여 계정을 만들고 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-136">You can also use the configuration stored procedures in **msdb** to create and manage accounts.</span></span>  
  
  
##  <a name="database-mail-profile"></a><a name="DBProfile"></a> <span data-ttu-id="72b24-137">데이터베이스 메일 프로필</span><span class="sxs-lookup"><span data-stu-id="72b24-137">Database Mail Profile</span></span>  
 <span data-ttu-id="72b24-138">데이터베이스 메일 프로필은 관련 데이터베이스 메일 계정을 정렬하여 모아 놓은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-138">A Database Mail profile is an ordered collection of related Database Mail accounts.</span></span> <span data-ttu-id="72b24-139">데이터베이스 메일을 사용하여 전자 메일을 보내는 애플리케이션은 계정을 직접 사용하는 대신 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-139">Applications that send e-mail using Database Mail specify profiles, instead of using accounts directly.</span></span> <span data-ttu-id="72b24-140">애플리케이션에서 사용하는 개체와 개별 전자 메일 서버에 대한 정보를 분리하면 유연성과 안정성을 향상시킬 수 있습니다. 프로필은 자동 장애 조치(failover)를 제공하기 때문에 하나의 전자 메일 서버가 응답하지 않아도 데이터베이스 메일이 다른 전자 메일 서버로 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-140">Separating information about the individual e-mail servers from the objects that the application uses improves flexibility and reliability: profiles provide automatic failover, so that if one e-mail server is unresponsive, Database Mail can automatically send mail to another e-mail server.</span></span> <span data-ttu-id="72b24-141">데이터베이스 관리자는 애플리케이션 코드나 작업 단계를 변경할 필요 없이 계정을 추가, 제거 또는 다시 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-141">Database administrators can add, remove, or reconfigure accounts without requiring changes to application code or job steps.</span></span>  
  
 <span data-ttu-id="72b24-142">또한 프로필을 사용하면 데이터베이스 관리자가 전자 메일 액세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-142">Profiles also help database administrators control access to e-mail.</span></span> <span data-ttu-id="72b24-143">데이터베이스 메일을 보내려면 **DatabaseMailUserRole** 의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-143">Membership in the **DatabaseMailUserRole** is required to send Database Mail.</span></span> <span data-ttu-id="72b24-144">프로필이 있으면 관리자는 메일을 보내는 사람과 사용되는 계정을 유연하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-144">Profiles provide additional flexibility for administrators to control who sends mail and which accounts are used.</span></span>  
  
 <span data-ttu-id="72b24-145">프로필은 퍼블릭 또는 프라이빗 프로필일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-145">A profile may be public or private.</span></span>  
  
 <span data-ttu-id="72b24-146">**공개 프로필** 은 **msdb** 데이터베이스에 있는 **DatabaseMailUserRole** 데이터베이스 역할의 모든 멤버에 대해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-146">**Public profiles** are available for all members of the **DatabaseMailUserRole** database role in the **msdb** database.</span></span> <span data-ttu-id="72b24-147">공개 프로필이 있으면 **DatabaseMailUserRole** 역할의 모든 멤버는 해당 프로필을 사용하여 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-147">They allow all members of the **DatabaseMailUserRole** role to send e-mail using the profile.</span></span>  
  
 <span data-ttu-id="72b24-148">**프라이빗 프로필** 은 **msdb** 데이터베이스의 보안 주체에 대해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-148">**Private profiles** are defined for security principals in the **msdb** database.</span></span> <span data-ttu-id="72b24-149">지정된 데이터베이스 사용자, 역할 및 **sysadmin** 고정 서버 역할의 멤버만 개인 프로필을 사용하여 메일을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-149">They allow only specified database users, roles, and members of the **sysadmin** fixed server role to send e-mail using the profile.</span></span> <span data-ttu-id="72b24-150">기본적으로 프로필은 프라이빗 프로필이며 **sysadmin** 고정 서버 역할의 멤버에게만 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-150">By default, a profile is private, and allows access only to members of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="72b24-151">프라이빗 프로필을 사용할 수 있도록 하려면 **sysadmin** 이 사용자에게 프로필 사용 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-151">To use a private profile, **sysadmin** must grant users permission to use the profile.</span></span> <span data-ttu-id="72b24-152">또한 **sp_send_dbmail** 저장 프로시저에 대한 EXECUTE 권한은 **DatabaseMailUserRole**멤버에게만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-152">Additionally, EXECUTE permission on the **sp_send_dbmail** stored procedure is only granted to members of the **DatabaseMailUserRole**.</span></span> <span data-ttu-id="72b24-153">사용자가 메일 메시지를 보내려면 시스템 관리자가 해당 사용자를 **DatabaseMailUserRole** 데이터베이스 역할에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-153">A system administrator must add the user to the **DatabaseMailUserRole** database role for the user to send e-mail messages.</span></span>  
  
 <span data-ttu-id="72b24-154">프로필을 사용하면 전자 메일 서버에 연결할 수 없거나 전자 메일 서버가 메시지를 처리할 수 없는 경우 안정성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-154">Profiles improve reliability in cases where an e-mail server becomes unreachable or unable to process messages.</span></span> <span data-ttu-id="72b24-155">프로필의 계정마다 시퀀스 번호가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-155">Each account in the profile has a sequence number.</span></span> <span data-ttu-id="72b24-156">시퀀스 번호는 데이터베이스 메일에서 프로필의 계정을 사용하는 순서를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-156">The sequence number determines the order in which Database Mail uses accounts in the profile.</span></span> <span data-ttu-id="72b24-157">데이터베이스 메일은 메시지를 성공적으로 보낸 마지막 계정을 새 전자 메일 메시지에 사용합니다. 그러나 아직 보낸 메시지가 없는 경우에는 시퀀스 번호가 가장 낮은 계정을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-157">For a new e-mail message, Database Mail uses the last account that sent a message successfully, or the account that has the lowest sequence number if no message has yet been sent.</span></span> <span data-ttu-id="72b24-158">해당 계정이 실패하면 데이터베이스 메일에서는 시퀀스 번호가 다음으로 높은 계정을 사용하여 메시지가 성공적으로 전송될 때까지 또는 시퀀스 번호가 가장 높은 계정이 실패할 때까지 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-158">Should that account fail, Database Mail uses the account with the next highest sequence number, and so on until either Database Mail sends the message successfully, or the account with the highest sequence number fails.</span></span> <span data-ttu-id="72b24-159">시퀀스 번호가 가장 높은 계정이 실패하면 데이터베이스 메일은 **sysmail_configure_sp** 의 **AccountRetryDelay**매개 변수에서 구성한 기간 동안 메일을 보내려는 시도를 일시 중지했다가 가장 낮은 시퀀스 번호에서 시작하여 다시 메일을 보내려는 시도를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-159">If the account with the highest sequence number fails, the Database Mail pauses attempts to send the mail for the amount of time configured in the **AccountRetryDelay** parameter of **sysmail_configure_sp**, then starts the process of attempting to send the mail again, starting with the lowest sequence number.</span></span> <span data-ttu-id="72b24-160">**sysmail_configure_sp** 의 **AccountRetryAttempts**매개 변수를 사용하여 외부 메일 프로세스가 지정한 프로필의 각 계정을 사용하여 전자 메일 메시지를 보내려고 시도하는 횟수를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-160">Use the **AccountRetryAttempts** parameter of **sysmail_configure_sp**, to configure the number of times that the external mail process attempts to send the e-mail message using each account in the specified profile.</span></span>  
  
 <span data-ttu-id="72b24-161">시퀀스 번호가 같은 계정이 둘 이상 있으면 데이터베이스 메일은 지정된 전자 메일 메시지에 대해 해당 계정 중 하나만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-161">If more than one account exists with the same sequence number, Database Mail only uses one of those accounts for a given e-mail message.</span></span> <span data-ttu-id="72b24-162">이 경우 데이터베이스 메일에서 항상 특정 시퀀스 번호에 대해 해당 계정이 사용되거나 메시지 간 동일한 계정이 사용되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-162">In this case, Database Mail makes no guarantees as to which of the accounts is used for that sequence number or that the same account is used from message to message.</span></span>  
  
  
##  <a name="database-mail-configuration-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="72b24-163">데이터베이스 메일 구성 태스크</span><span class="sxs-lookup"><span data-stu-id="72b24-163">Database Mail Configuration Tasks</span></span>  
 <span data-ttu-id="72b24-164">다음 표에서는 데이터베이스 메일 구성 태스크에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-164">The following table describes the Database Mail configuration tasks.</span></span>  
  
|<span data-ttu-id="72b24-165">구성 태스크</span><span class="sxs-lookup"><span data-stu-id="72b24-165">Configuration Task</span></span>|<span data-ttu-id="72b24-166">항목 링크</span><span class="sxs-lookup"><span data-stu-id="72b24-166">Topic Link</span></span>|  
|------------------------|----------------|  
|<span data-ttu-id="72b24-167">데이터베이스 메일 계정을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-167">Describes how to create a Database Mail accounts</span></span>|[<span data-ttu-id="72b24-168">데이터베이스 메일 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="72b24-168">Create a Database Mail Account</span></span>](create-a-database-mail-account.md)|  
|<span data-ttu-id="72b24-169">데이터베이스 메일 프로필을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-169">Describes how to Create Database Mail profiles</span></span>|[<span data-ttu-id="72b24-170">데이터베이스 메일 프로필 만들기</span><span class="sxs-lookup"><span data-stu-id="72b24-170">Create a Database Mail Profile</span></span>](create-a-database-mail-profile.md)|  
|<span data-ttu-id="72b24-171">데이터베이스 메일을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-171">Describes how to Configure Database mail</span></span>|[<span data-ttu-id="72b24-172">데이터베이스 메일 구성</span><span class="sxs-lookup"><span data-stu-id="72b24-172">Configure Database Mail</span></span>](configure-database-mail.md)|  
|<span data-ttu-id="72b24-173">템플릿을 사용하여 데이터베이스 메일 구성 스크립트를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-173">Describes how to create a Database Mail configuration script using templates</span></span>||  
  
  
##  <a name="additional-database-configuration-tasks-system-stored-procedures"></a><a name="Add_Tasks"></a> <span data-ttu-id="72b24-174">추가 데이터베이스 구성 태스크(시스템 저장 프로시저)</span><span class="sxs-lookup"><span data-stu-id="72b24-174">Additional Database Configuration Tasks (System Stored Procedures)</span></span>  
 <span data-ttu-id="72b24-175">데이터베이스 메일 구성 저장 프로시저는 **msdb** 데이터베이스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-175">Database Mail configuration stored procedures are located in the **msdb** database.</span></span>  
  
 <span data-ttu-id="72b24-176">다음 표에서는 데이터베이스 메일을 구성하고 관리하는 데 사용되는 저장 프로시저를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-176">The following tables list the stored procedures used for configuring and managing Database Mail.</span></span>  
  
### <a name="database-mail-settings"></a><span data-ttu-id="72b24-177">데이터베이스 메일 설정</span><span class="sxs-lookup"><span data-stu-id="72b24-177">Database Mail Settings</span></span>  
  
|<span data-ttu-id="72b24-178">속성</span><span class="sxs-lookup"><span data-stu-id="72b24-178">Name</span></span>|<span data-ttu-id="72b24-179">Description</span><span class="sxs-lookup"><span data-stu-id="72b24-179">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="72b24-180">sysmail_configure_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-180">sysmail_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql)|<span data-ttu-id="72b24-181">데이터베이스 메일의 구성 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-181">Changes configuration settings for Database Mail.</span></span>|  
|[<span data-ttu-id="72b24-182">sysmail_help_configure_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-182">sysmail_help_configure_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql)|<span data-ttu-id="72b24-183">데이터베이스 메일의 구성 설정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-183">Displays configuration settings for Database Mail.</span></span>|  
  
### <a name="accounts-and-profiles"></a><span data-ttu-id="72b24-184">계정 및 프로필</span><span class="sxs-lookup"><span data-stu-id="72b24-184">Accounts and Profiles</span></span>  
  
|<span data-ttu-id="72b24-185">속성</span><span class="sxs-lookup"><span data-stu-id="72b24-185">Name</span></span>|<span data-ttu-id="72b24-186">Description</span><span class="sxs-lookup"><span data-stu-id="72b24-186">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="72b24-187">sysmail_add_profileaccount_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-187">sysmail_add_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql)|<span data-ttu-id="72b24-188">데이터베이스 메일 프로필에 메일 계정을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-188">Adds a mail account to a Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-189">sysmail_delete_account_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-189">sysmail_delete_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-account-sp-transact-sql)|<span data-ttu-id="72b24-190">데이터베이스 메일 계정을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-190">Deletes a Database Mail account.</span></span>|  
|[<span data-ttu-id="72b24-191">sysmail_delete_profile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-191">sysmail_delete_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql)|<span data-ttu-id="72b24-192">데이터베이스 메일 프로필을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-192">Deletes a Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-193">sysmail_delete_profileaccount_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-193">sysmail_delete_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql)|<span data-ttu-id="72b24-194">데이터베이스 메일 프로필에서 계정을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-194">Removes an account from a Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-195">sysmail_help_account_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-195">sysmail_help_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql)|<span data-ttu-id="72b24-196">데이터베이스 메일 계정에 대한 정보를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-196">Lists information about Database Mail accounts.</span></span>|  
|[<span data-ttu-id="72b24-197">sysmail_help_profile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-197">sysmail_help_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql)|<span data-ttu-id="72b24-198">하나 이상의 데이터베이스 메일 프로필에 대한 정보를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-198">Lists information about one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="72b24-199">sysmail_help_profileaccount_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-199">sysmail_help_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql)|<span data-ttu-id="72b24-200">하나 이상의 데이터베이스 메일 프로필과 연관된 계정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-200">Lists the accounts associated with one or more Database Mail profiles.</span></span>|  
|[<span data-ttu-id="72b24-201">sysmail_update_account_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-201">sysmail_update_account_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-account-sp-transact-sql)|<span data-ttu-id="72b24-202">기존 데이터베이스 메일 계정의 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-202">Updates the information in an existing Database Mail account.</span></span>|  
|[<span data-ttu-id="72b24-203">sysmail_update_profile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-203">sysmail_update_profile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profile-sp-transact-sql)|<span data-ttu-id="72b24-204">데이터베이스 메일 프로필의 설명이나 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-204">Changes the description or name of a Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-205">sysmail_update_profileaccount_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-205">sysmail_update_profileaccount_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql)|<span data-ttu-id="72b24-206">데이터베이스 메일 프로필 내에서 계정의 시퀀스 번호를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-206">Updates the sequence number of an account within a Database Mail profile.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="72b24-207">보안</span><span class="sxs-lookup"><span data-stu-id="72b24-207">Security</span></span>  
  
|<span data-ttu-id="72b24-208">속성</span><span class="sxs-lookup"><span data-stu-id="72b24-208">Name</span></span>|<span data-ttu-id="72b24-209">Description</span><span class="sxs-lookup"><span data-stu-id="72b24-209">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="72b24-210">sysmail_add_principalprofile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-210">sysmail_add_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql)|<span data-ttu-id="72b24-211">데이터베이스 보안 주체에 대해 데이터베이스 메일 프로필을 사용할 수 있는 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-211">Grants permission for a database principal to use a Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-212">sysmail_delete_principalprofile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-212">sysmail_delete_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-delete-principalprofile-sp-transact-sql)|<span data-ttu-id="72b24-213">퍼블릭 또는 프라이빗 데이터베이스 메일 프로필을 사용할 수 있는 데이터베이스 보안 주체에 대한 사용 권한을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-213">Removes permission for a database user to use a public or private Database Mail profile.</span></span>|  
|[<span data-ttu-id="72b24-214">sysmail_help_principalprofile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-214">sysmail_help_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-principalprofile-sp-transact-sql)|<span data-ttu-id="72b24-215">지정한 데이터베이스 사용자에 대한 데이터베이스 메일 프로필 정보를 나열합니다</span><span class="sxs-lookup"><span data-stu-id="72b24-215">Lists Database Mail profile information for a given database user.</span></span>|  
|[<span data-ttu-id="72b24-216">sysmail_update_principalprofile_sp(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72b24-216">sysmail_update_principalprofile_sp (Transact-SQL)</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-update-principalprofile-sp-transact-sql)|<span data-ttu-id="72b24-217">지정한 데이터베이스 사용자에 대한 사용 권한 정보를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-217">Updates the permission information for a given database user.</span></span>|  
  
### <a name="system-state"></a><span data-ttu-id="72b24-218">시스템 상태</span><span class="sxs-lookup"><span data-stu-id="72b24-218">System State</span></span>  
  
|<span data-ttu-id="72b24-219">속성</span><span class="sxs-lookup"><span data-stu-id="72b24-219">Name</span></span>|<span data-ttu-id="72b24-220">Description</span><span class="sxs-lookup"><span data-stu-id="72b24-220">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="72b24-221">sysmail_start_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72b24-221">sysmail_start_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|<span data-ttu-id="72b24-222">데이터베이스 메일 외부 프로그램 및 관련 SQL Service Broker 큐를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-222">Starts the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="72b24-223">sysmail_stop_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72b24-223">sysmail_stop_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|<span data-ttu-id="72b24-224">데이터베이스 메일 외부 프로그램 및 관련 SQL Service Broker 큐를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-224">Stops the Database Mail external program and the associated SQL Service Broker queue.</span></span>|  
|[<span data-ttu-id="72b24-225">sysmail_help_status_sp&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="72b24-225">sysmail_help_status_sp &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|<span data-ttu-id="72b24-226">데이터베이스 메일이 시작되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="72b24-226">Indicates if Database Mail is started.</span></span>|  
  
##  <a name="additional-references"></a><a name="RelatedContent"></a> <span data-ttu-id="72b24-227">추가 참조</span><span class="sxs-lookup"><span data-stu-id="72b24-227">Additional References</span></span>  
  
-   [<span data-ttu-id="72b24-228">데이터베이스 메일 로그 및 감사</span><span class="sxs-lookup"><span data-stu-id="72b24-228">Database Mail Log and Audits</span></span>](database-mail-log-and-audits.md)  
  
  
  
