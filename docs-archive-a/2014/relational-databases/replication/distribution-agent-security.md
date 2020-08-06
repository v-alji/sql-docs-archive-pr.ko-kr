---
title: 배포 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.DA.f1
helpviewer_keywords:
- Distribution Agent Security dialog box
ms.assetid: de40cc21-2e58-4464-9be7-b5b90c925e9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4342d44a221d9b816a95a283917f005eb018827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646920"
---
# <a name="distribution-agent-security"></a><span data-ttu-id="c0e2b-102">배포 에이전트 보안</span><span class="sxs-lookup"><span data-stu-id="c0e2b-102">Distribution Agent Security</span></span>
  <span data-ttu-id="c0e2b-103">**배포 에이전트 보안** 대화 상자를 사용하여 배포 에이전트를 실행하는 Windows 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-103">The **Distribution Agent Security** dialog box allows you to specify the Windows account under which the Distribution Agent runs.</span></span> <span data-ttu-id="c0e2b-104">배포 에이전트는 밀어넣기 구독을 위한 배포자 또는 끌어오기 구독을 위한 구독자에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-104">The Distribution Agent runs at the Distributor for push subscriptions and at the Subscriber for pull subscriptions.</span></span> <span data-ttu-id="c0e2b-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정으로 에이전트 프로세스가 실행되기 때문에 이 계정을 *프로세스 계정*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span> <span data-ttu-id="c0e2b-106">이 대화 상자에서 사용 가능한 추가 옵션은 대화 상자에 액세스하는 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-106">Additional options available in the dialog box depend on how you access it:</span></span>  
  
-   <span data-ttu-id="c0e2b-107">새 구독 마법사에서 이 대화 상자에 액세스하는 경우 배포 에이전트를 구독자(밀어넣기 구독의 경우) 또는 배포자(끌어오기 구독의 경우)에 연결하는 컨텍스트도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-107">If the dialog box is accessed from the New Subscription Wizard, it also allows you to specify the context under which the Distribution Agent makes connections to the Subscriber (for push subscriptions) or the Distributor (for pull subscriptions).</span></span> <span data-ttu-id="c0e2b-108">Windows 계정을 가장하거나 지정한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정의 컨텍스트에서 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-108">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
-   <span data-ttu-id="c0e2b-109">**구독 속성** 대화 상자에서 이 대화 상자에 액세스하는 경우 해당 대화 상자의**구독자 연결**또는 **배포자 연결** 행의 속성 단추 ( **...** )를 클릭하여 배포 에이전트를 연결하는 컨텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-109">If the dialog box is accessed from the **Subscription Properties** dialog box, specify the context under which the Distribution Agent makes connections by clicking the properties button (**...**) in the **Subscriber Connection** or **Distributor Connection** row of that dialog box.</span></span> <span data-ttu-id="c0e2b-110">**구독 속성** 대화 상자에 액세스하는 방법은 [밀어넣기 구독 속성 보기 및 수정](view-and-modify-push-subscription-properties.md) 및 방법: [끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-110">For more information about accessing the **Subscription Properties** dialog box, see [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) and how to: [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).</span></span>  
  
 <span data-ttu-id="c0e2b-111">모든 계정이 유효해야 하며 각 계정에 대해 올바른 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-111">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="c0e2b-112">계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-112">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c0e2b-113">옵션</span><span class="sxs-lookup"><span data-stu-id="c0e2b-113">Options</span></span>  
 <span data-ttu-id="c0e2b-114">**Process Account**</span><span class="sxs-lookup"><span data-stu-id="c0e2b-114">**Process Account**</span></span>  
 <span data-ttu-id="c0e2b-115">배포 에이전트를 실행하는 Windows 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-115">Enter a Windows account under which the Distribution Agent runs:</span></span>  
  
-   <span data-ttu-id="c0e2b-116">밀어넣기 구독의 경우 계정이 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-116">For push subscriptions, the account must:</span></span>  
  
    -   <span data-ttu-id="c0e2b-117">적어도 배포 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-117">At minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
    -   <span data-ttu-id="c0e2b-118">PAL(게시 액세스 목록)의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-118">Be a member of the publication access list (PAL).</span></span>  
  
    -   <span data-ttu-id="c0e2b-119">스냅샷 공유에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-119">Have read permissions on the snapshot share.</span></span>  
  
    -   <span data-ttu-id="c0e2b-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대한 구독인 경우에는 구독자에 대한 OLE DB 공급자의 설치 디렉터리에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-120">Have read permissions on the install directory of the OLE DB provider for the Subscriber if the subscription is for a non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscriber.</span></span>  
  
-   <span data-ttu-id="c0e2b-121">끌어오기 구독의 경우 계정이 적어도 구독 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-121">For pull subscriptions, the account must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
 <span data-ttu-id="c0e2b-122">연결을 설정할 때 프로세스 계정을 가장하면 추가 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-122">Additional permissions are required if the process account is impersonated when connections are made.</span></span> <span data-ttu-id="c0e2b-123">아래의 **배포자에 연결** 및 **구독자에 연결** 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-123">See the **Connect to the Distributor** and **Connect to the Subscriber** sections below.</span></span>  
  
 <span data-ttu-id="c0e2b-124">배포 에이전트가 **인스턴스에서 실행되지 않기 때문에** [!INCLUDE[msCoName](../../includes/msconame-md.md)]에 대한 끌어오기 구독에 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]프로세스 계정[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-124">**Process Account** cannot be specified for pull subscriptions to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], because the Distribution Agent does not run on instances of [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span>  
  
 <span data-ttu-id="c0e2b-125">**암호** 및 **암호 확인**</span><span class="sxs-lookup"><span data-stu-id="c0e2b-125">**Password** and **Confirm Password**</span></span>  
 <span data-ttu-id="c0e2b-126">Windows 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-126">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="c0e2b-127">**배포자에 연결**</span><span class="sxs-lookup"><span data-stu-id="c0e2b-127">**Connect to the Distributor**</span></span>  
 <span data-ttu-id="c0e2b-128">밀어넣기 구독의 경우 항상 **프로세스 계정** 입력란에 지정한 계정을 가장하여 배포자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-128">For push subscriptions, connections to the Distributor are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="c0e2b-129">끌어오기 구독의 경우 배포 에이전트를 배포자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-129">For pull subscriptions, select whether the Distribution Agent should make connections to the Distributor by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="c0e2b-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-130">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0e2b-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 것보다 Windows 계정을 가장하도록 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-131">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="c0e2b-132">연결에 사용할 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 다음 조건을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-132">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must:</span></span>  
  
-   <span data-ttu-id="c0e2b-133">PAL의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-133">Be a member of the PAL.</span></span>  
  
-   <span data-ttu-id="c0e2b-134">스냅샷 공유에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-134">Have read permissions on the snapshot share.</span></span>  
  
 <span data-ttu-id="c0e2b-135">**구독자에 연결**</span><span class="sxs-lookup"><span data-stu-id="c0e2b-135">**Connect to the Subscriber**</span></span>  
 <span data-ttu-id="c0e2b-136">끌어오기 구독의 경우 항상 **프로세스 계정** 입력란에 지정한 계정을 가장하여 구독자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-136">For pull subscriptions, connections to the Subscriber are always made by impersonating the account specified in the **Process account** text box.</span></span>  
  
 <span data-ttu-id="c0e2b-137">밀어넣기 구독의 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자 및[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대한 옵션이 다음과 같이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-137">For push subscriptions, the options are different for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="c0e2b-138">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구독자의 경우 배포 에이전트를 구독자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-138">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers: select whether the Distribution Agent should make connections to the Subscriber by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="c0e2b-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-139">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c0e2b-140">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 것보다 Windows 계정을 가장하도록 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-140">It is recommended that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
     <span data-ttu-id="c0e2b-141">구독자 연결에 사용되는 Windows 계정 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 적어도 구독 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-141">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection to the Subscriber must at minimum be a member of the **db_owner** fixed database role in the subscription database.</span></span>  
  
-   <span data-ttu-id="c0e2b-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자의 경우 배포 에이전트를 구독자에 연결할 때 사용할 데이터베이스 로그인을 구독자에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-142">For non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, specify the database login at the Subscriber that should be used when the Distribution Agent connects to the Subscriber.</span></span> <span data-ttu-id="c0e2b-143">해당 로그인에는 구독 데이터베이스에서 개체를 만들 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-143">The login should have sufficient permissions to create objects in the subscription database.</span></span> <span data-ttu-id="c0e2b-144">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대한 자세한 내용은 [SQL Server 이외 구독자에 대한 구독 만들기](create-a-subscription-for-a-non-sql-server-subscriber.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-144">For more information about configuring non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers, see [Create a Subscription for a Non-SQL Server Subscriber](create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
 <span data-ttu-id="c0e2b-145">**추가 연결 옵션**</span><span class="sxs-lookup"><span data-stu-id="c0e2b-145">**Additional connection options**</span></span>  
 <span data-ttu-id="c0e2b-146">이 옵션은[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이외 구독자에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-146">Non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Subscribers only.</span></span> <span data-ttu-id="c0e2b-147">연결 문자열 형식으로 구독자에 대한 연결 옵션을 지정하십시오. Oracle에서는 추가 옵션을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-147">Specify any connection options for the Subscriber in the form of a connection string (Oracle does not require additional options).</span></span> <span data-ttu-id="c0e2b-148">각 옵션은 세미콜론으로 구분해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-148">Each option should be separated by a semi-colon.</span></span> <span data-ttu-id="c0e2b-149">다음은 IBM DB2 연결 문자열의 예입니다. 이 예에서는 읽기 쉽도록 줄 바꿈을 넣었습니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-149">The following is an example of an IBM DB2 connection string (line breaks are for readability):</span></span>  
  
```  
Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
Persist Security Info=False;Connection Pooling=True;  
```  
  
 <span data-ttu-id="c0e2b-150">이 문자열의 옵션 대부분은 구성 중인 DB2 서버와만 관련이 있지만 **Process Binary as Character** 옵션은 항상 **False**로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-150">Most of the options in the string are specific to the DB2 server you are configuring, but the **Process Binary as Character** option should always be set to **False**.</span></span> <span data-ttu-id="c0e2b-151">구독 데이터베이스를 식별하려면 **Initial Catalog** 옵션 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-151">A value is required for the **Initial Catalog** option to identify the subscription database.</span></span> <span data-ttu-id="c0e2b-152">자세한 내용은 [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0e2b-152">For more information, see [IBM DB2 Subscribers](non-sql/ibm-db2-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e2b-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0e2b-153">See Also</span></span>  
 <span data-ttu-id="c0e2b-154">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="c0e2b-154">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="c0e2b-155">[복제 에이전트 보안 모델](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="c0e2b-155">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="c0e2b-156">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c0e2b-156">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 <span data-ttu-id="c0e2b-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span><span class="sxs-lookup"><span data-stu-id="c0e2b-157">[Replication Security Best Practices](security/replication-security-best-practices.md) </span></span>  
 [<span data-ttu-id="c0e2b-158">게시 구독</span><span class="sxs-lookup"><span data-stu-id="c0e2b-158">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
