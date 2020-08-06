---
title: 데이터베이스 엔진 구성-계정 프로 비전 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7885bdda72668ac96e90b0900772a4f56575d5fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639258"
---
# <a name="database-engine-configuration---account-provisioning"></a><span data-ttu-id="71097-102">데이터베이스 엔진 구성 - 계정 프로비전</span><span class="sxs-lookup"><span data-stu-id="71097-102">Database Engine Configuration - Account Provisioning</span></span>
  <span data-ttu-id="71097-103">이 페이지를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 모드를 설정하고 Windows 사용자 또는 그룹을 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]의 관리자로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-103">Use this page to set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security mode, and to add Windows users or groups as administrators of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="considerations-for-running-sscurrent"></a><span data-ttu-id="71097-104">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 실행 고려 사항</span><span class="sxs-lookup"><span data-stu-id="71097-104">Considerations for Running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]</span></span>  
 <span data-ttu-id="71097-105">이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 **BUILTIN\Administrators** 그룹이 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 로그인으로 프로비전되었으며 로컬 관리자 그룹의 멤버는 해당 관리자 자격 증명을 사용하여 로그인할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-105">On previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the **BUILTIN\Administrators** group was provisioned as a login in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and members of the local Administrators group could login using their Administrator credentials.</span></span> <span data-ttu-id="71097-106">그러나 높은 권한은 가급적 사용하지 않는 것이 좋으므로</span><span class="sxs-lookup"><span data-stu-id="71097-106">Using elevated permissions is not a best practice.</span></span> <span data-ttu-id="71097-107">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 **BUILTIN\Administrators** 그룹이 로그인으로 프로비전되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-107">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] the **BUILTIN\Administrators** group is not provisioned as a login.</span></span> <span data-ttu-id="71097-108">따라서 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 설치하는 동안 각 관리자에 대해 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로그인을 만들고 이 로그인을 sysadmin 고정 서버 역할에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-108">As a result, you should create a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login for each administrative user, and add that login to the sysadmin fixed server role during installation of a new instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="71097-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업(복제 에이전트 작업 포함)을 실행하는 데 사용되는 Windows 계정에 대해서도</span><span class="sxs-lookup"><span data-stu-id="71097-109">You should also do this for Windows accounts that are used to run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent jobs.</span></span> <span data-ttu-id="71097-110">이 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-110">These include replication agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="71097-111">옵션</span><span class="sxs-lookup"><span data-stu-id="71097-111">Options</span></span>  
 <span data-ttu-id="71097-112">**보안 모드** - 설치에 사용할 인증(Windows 인증 또는 혼합 모드 인증)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-112">**Security Mode** - Select Windows Authentication or Mixed Mode Authentication for your installation.</span></span>  
  
 <span data-ttu-id="71097-113">**Windows 보안 주체 프로비전** - 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 Windows Builtin\Administrator 로컬 그룹이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin 서버 역할에 배치되어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 액세스 권한이 사실상 Windows 관리자에게 부여되었습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-113">**Windows Principal Provisioning** - In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the Windows Builtin\Administrator local group was placed into the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sysadmin server role, effectively granting Windows administrators access to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="71097-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 Builtin\Administrator 그룹은 sysadmin 서버 역할로 프로비전되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-114">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], the Builtin\Administrator group is not provisioned in the sysadmin server role.</span></span> <span data-ttu-id="71097-115">대신 설치 중에 새 설치에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자를 명시적으로 프로비전해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-115">Instead, you should explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="71097-116">설치 중에 새 설치에 대해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자를 명시적으로 프로비전해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-116">You must explicitly provision [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administrators for new installations during Setup.</span></span> <span data-ttu-id="71097-117">이 단계를 완료해야 설치 프로그램이 다음 단계로 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="71097-117">Setup will not allow you to continue until you complete this step.</span></span>  
  
 <span data-ttu-id="71097-118">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 관리자 지정** - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 Windows 보안 주체를 한 명 이상 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-118">**Specify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Administrators** - You must specify at least one Windows principal for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="71097-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램이 실행되는 계정을 추가하려면 **현재 사용자** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-119">To add the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup is running, click the **Current User** button.</span></span> <span data-ttu-id="71097-120">시스템 관리자 목록에 계정을 추가하거나 목록의 계정을 제거하려면 **추가** 또는 **제거**를 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 관리자 권한을 가질 사용자, 그룹 또는 컴퓨터 목록을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-120">To add or remove accounts from the list of system administrators, click **Add** or **Remove**, and then edit the list of users, groups, or computers that will have administrator privileges for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="71097-121">목록 편집을 마치면 **확인**을 클릭한 다음 구성 대화 상자에서 관리자 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-121">When you are finished editing the list, click **OK**, then verify the list of administrators in the configuration dialog.</span></span> <span data-ttu-id="71097-122">목록 구성을 완료했으면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-122">When the list is complete, click **Next**.</span></span>  
  
 <span data-ttu-id="71097-123">혼합 모드 인증을 선택한 경우 기본 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SA(시스템 관리자) 계정에 대해 로그온 자격 증명을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-123">If you select Mixed Mode Authentication, you must provide logon credentials for the builtin [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator (SA) account.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 <span data-ttu-id="71097-124">**Windows 인증 모드**</span><span class="sxs-lookup"><span data-stu-id="71097-124">**Windows Authentication Mode**</span></span>  
 <span data-ttu-id="71097-125">사용자가 Microsoft Windows 사용자 계정을 통해 연결되면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 운영 체제의 Windows 보안 주체 토큰을 사용하여 계정 이름과 암호가 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-125">When a user connects through a Windows user account, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] validates the account name and password using the Windows principal token in the operating system.</span></span> <span data-ttu-id="71097-126">이것은 기본 인증 모드이며 혼합 모드보다 훨씬 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-126">This is the default authentication mode, and is much more secure than Mixed Mode.</span></span> <span data-ttu-id="71097-127">Windows 인증은 Kerberos 보안 프로토콜을 사용하고, 암호 정책을 적용하여 강력한 암호에 대해 적합한 복잡성 수준을 유지하도록 하며, 계정 잠금 및 암호 만료를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-127">Windows Authentication utilizes Kerberos security protocol, provides password policy enforcement in terms of complexity validation for strong passwords, provides support for account lockout, and supports password expiration.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] <span data-ttu-id="71097-128">비어 있거나 약한 sa 암호는 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="71097-128">Never set a blank or weak sa password.</span></span>  
  
 <span data-ttu-id="71097-129">**혼합 모드 (Windows 인증 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증)**</span><span class="sxs-lookup"><span data-stu-id="71097-129">**Mixed Mode (Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication)**</span></span>  
 <span data-ttu-id="71097-130">사용자가 Windows 인증 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 연결할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-130">Allows users to connect by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="71097-131">Windows 사용자 계정을 통해 연결하는 사용자는 Windows에서 유효성을 검사하는 트러스트된 연결을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-131">Users who connect through a Windows user account can use trusted connections that are validated by Windows.</span></span>  
  
 <span data-ttu-id="71097-132">혼합 모드 인증을 선택해야 하며 레거시 애플리케이션을 수용하기 위해 SQL 로그인을 사용해야 할 경우 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정에 대해 강력한 암호를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-132">If you must choose Mixed Mode Authentication and you have a requirement for using SQL logins to accommodate legacy applications, you must set strong passwords for all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accounts.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71097-133">인증은 오로지 이전 버전과의 호환성을 위해서만 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="71097-133">Authentication is provided for backward compatibility only.</span></span> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 <span data-ttu-id="71097-134">**암호 입력**</span><span class="sxs-lookup"><span data-stu-id="71097-134">**Enter Password**</span></span>  
 <span data-ttu-id="71097-135">시스템 관리자(sa) 로그인을 입력하고 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="71097-135">Enter and confirm the system administrator (sa) login.</span></span> <span data-ttu-id="71097-136">암호는 침입을 막는 최전방 방어선이므로 시스템 보안을 위해서는 반드시 강력한 암호를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-136">Passwords are the first line of defense against intruders, so setting strong passwords is essential to the security of your system.</span></span> <span data-ttu-id="71097-137">빈 암호나 약한 sa 암호로는 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="71097-137">Never set a blank or weak sa password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="71097-138">암호는 문자, 기호 및 숫자를 임의로 조합하여 1자에서 128자까지 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-138">passwords can contain from 1 to 128 characters, including any combination of letters, symbols, and numbers.</span></span> <span data-ttu-id="71097-139">혼합 모드 인증을 선택한 경우 설치 마법사의 다음 페이지로 이동하기 전에 강력한 sa 암호를 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-139">If you choose Mixed Mode authentication, you must enter a strong sa password before you can continue to the next page of the Installation Wizard.</span></span>  
  
 <span data-ttu-id="71097-140">**강력한 암호 지침**</span><span class="sxs-lookup"><span data-stu-id="71097-140">**Strong Password Guidelines**</span></span>  
 <span data-ttu-id="71097-141">강력한 암호는 쉽게 추측할 수 없으며 컴퓨터 프로그램을 사용하여 해킹하기도 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-141">Strong passwords are not readily guessed by a person, and are not easily hacked using a computer program.</span></span> <span data-ttu-id="71097-142">강력한 암호에는 다음을 비롯한 금지된 조건 및 용어를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-142">Strong passwords cannot use prohibited conditions or terms, including:</span></span>  
  
-   <span data-ttu-id="71097-143">빈 조건 또는 NULL 조건</span><span class="sxs-lookup"><span data-stu-id="71097-143">A blank or NULL condition</span></span>  
  
-   <span data-ttu-id="71097-144">"Password"</span><span class="sxs-lookup"><span data-stu-id="71097-144">"Password"</span></span>  
  
-   <span data-ttu-id="71097-145">"Admin"</span><span class="sxs-lookup"><span data-stu-id="71097-145">"Admin"</span></span>  
  
-   <span data-ttu-id="71097-146">"Administrator"</span><span class="sxs-lookup"><span data-stu-id="71097-146">"Administrator"</span></span>  
  
-   <span data-ttu-id="71097-147">"sa"</span><span class="sxs-lookup"><span data-stu-id="71097-147">"sa"</span></span>  
  
-   <span data-ttu-id="71097-148">"sysadmin"</span><span class="sxs-lookup"><span data-stu-id="71097-148">"sysadmin"</span></span>  
  
 <span data-ttu-id="71097-149">강력한 암호에는 설치 컴퓨터와 관련된 다음 용어를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71097-149">A strong password cannot be the following terms associated with the installation computer:</span></span>  
  
-   <span data-ttu-id="71097-150">컴퓨터에 현재 로그온한 사용자의 이름</span><span class="sxs-lookup"><span data-stu-id="71097-150">The name of the user currently logged onto the machine.</span></span>  
  
-   <span data-ttu-id="71097-151">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="71097-151">The computer name.</span></span>  
  
 <span data-ttu-id="71097-152">강력한 암호는 8자 이상이어야 하며 다음의 네 가지 조건 중 세 가지 이상을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-152">A strong password must be more than 8 characters in length and satisfy at least three of the following four criteria:</span></span>  
  
-   <span data-ttu-id="71097-153">대문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-153">It must contain uppercase letters.</span></span>  
  
-   <span data-ttu-id="71097-154">소문자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-154">It must contain lowercase letters.</span></span>  
  
-   <span data-ttu-id="71097-155">숫자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-155">It must contain numbers.</span></span>  
  
-   <span data-ttu-id="71097-156">#, % 또는 ^과 같은 비영숫자를 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-156">It must contain non-alphanumeric characters; for example, #, %, or ^.</span></span>  
  
 <span data-ttu-id="71097-157">이 페이지에 입력하는 암호는 강력한 암호 정책 요구 사항을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71097-157">Passwords entered on this page must meet strong password policy requirements.</span></span> <span data-ttu-id="71097-158">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 자동화가 있으면 암호가 강력한 암호 정책 요구 사항을 만족하는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="71097-158">If you have any automation that uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, ensure that the password meets strong password policy requirements.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="71097-159">관련 내용</span><span class="sxs-lookup"><span data-stu-id="71097-159">Related Content</span></span>  
 <span data-ttu-id="71097-160">Windows 인증과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 중 어느 것을 선택할지 알아보려면 **온라인 설명서의** 인증 모드 선택 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71097-160">For more information about choosing Windows Authentication vs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, see the topic **Choose an Authentication Mode** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="71097-161">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]을 실행할 계정을 선택하는 방법에 대한 자세한 내용은 **온라인 설명서의** Windows 서비스 계정 및 권한 구성 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="71097-161">For more information about choosing an account to run the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], see the topic **Configure Windows Service Accounts and Permissions** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71097-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71097-162">See Also</span></span>  
 [<span data-ttu-id="71097-163">Windows 서비스 계정 및 권한 구성</span><span class="sxs-lookup"><span data-stu-id="71097-163">Configure Windows Service Accounts and Permissions</span></span>](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
