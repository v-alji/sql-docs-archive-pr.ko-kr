---
title: 로그인 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.LOGIN.SERVERROLES.F1
- sql12.swb.login.databaseaccess.f1
- sql12.swb.login.general.f1
- sql12.swb.login.effectivepermissions.f1
- sql12.swb.login.status.f1
helpviewer_keywords:
- authentication [SQL Server], logins
- logins [SQL Server], creating
- creating logins with Management Studio
- Create login [SQL Server]
- SQL Server logins
ms.assetid: fb163e47-1546-4682-abaa-8c9494e9ddc7
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e476880103a69ae016c6720f36e26ef884db6f5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730379"
---
# <a name="create-a-login"></a><span data-ttu-id="3f137-102">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="3f137-102">Create a Login</span></span>
  <span data-ttu-id="3f137-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 로그인을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-103">This topic describes how to create a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="3f137-104">로그인은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에 연결하는 사용자 또는 프로세스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-104">A login is the identity of the person or process that is connecting to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3f137-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="3f137-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="3f137-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="3f137-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="3f137-107">배경</span><span class="sxs-lookup"><span data-stu-id="3f137-107">Background</span></span>](#Background)  
  
     [<span data-ttu-id="3f137-108">보안</span><span class="sxs-lookup"><span data-stu-id="3f137-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="3f137-109">**로그인을 만들려면 다음을 사용합니다.**</span><span class="sxs-lookup"><span data-stu-id="3f137-109">**To create a login, using:**</span></span>  
  
     [<span data-ttu-id="3f137-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3f137-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="3f137-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3f137-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="3f137-112">**후속 작업:**  [로그인을 만든 후 수행할 단계](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="3f137-112">**Follow Up:**  [Steps to take after you create a login](#FollowUp)</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="3f137-113">배경</span><span class="sxs-lookup"><span data-stu-id="3f137-113">Background</span></span>  
 <span data-ttu-id="3f137-114">로그인은 보안 시스템에서 인증을 수행할 수 있는 보안 주체 또는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-114">A login is a security principal, or an entity that can be authenticated by a secure system.</span></span> <span data-ttu-id="3f137-115">사용자가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결하려면 로그인이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-115">Users need a login to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f137-116">도메인 사용자 또는 Windows 도메인 그룹 등의 Windows 주체에 기반한 로그인을 만들거나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인과 같은 Windows 주체에 기반한 로그인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-116">You can create a login based on a Windows principal (such as a domain user or a Windows domain group) or you can create a login that is not based on a Windows principal (such as an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f137-117">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하려면 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]에서 혼합 모드 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-117">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must use mixed mode authentication.</span></span> <span data-ttu-id="3f137-118">자세한 내용은 [인증 모드 선택](../choose-an-authentication-mode.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-118">For more information, see [Choose an Authentication Mode](../choose-an-authentication-mode.md).</span></span>  
  
 <span data-ttu-id="3f137-119">보안 주체는 사용 권한을 로그인에 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-119">As a security principal, permissions can be granted to logins.</span></span> <span data-ttu-id="3f137-120">로그인의 범위는 전체 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-120">The scope of a login is the whole [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="3f137-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에서 특정 데이터베이스에 연결하려면 로그인을 데이터베이스 사용자에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-121">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="3f137-122">이 경우 로그인이 아니라 데이터베이스 내의 사용 권한이 데이터베이스 사용자에게 부여되며 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-122">Permissions inside the database are granted and denied to the database user, not the login.</span></span> <span data-ttu-id="3f137-123">범위가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 전체 인스턴스에 속하는 사용 권한(예: `CREATE ENDPOINT` 권한)을 로그인에 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-123">Permissions that have the scope of the whole instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (for example, the `CREATE ENDPOINT` permission) can be granted to a login.</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3f137-124">보안</span><span class="sxs-lookup"><span data-stu-id="3f137-124">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="3f137-125">사용 권한</span><span class="sxs-lookup"><span data-stu-id="3f137-125">Permissions</span></span>  
 <span data-ttu-id="3f137-126">서버에 대한 `ALTER ANY LOGIN` 또는 `ALTER LOGIN` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-126">Requires `ALTER ANY LOGIN` or `ALTER LOGIN` permission on the server.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="3f137-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="3f137-127">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-sql-server-login"></a><span data-ttu-id="3f137-128">SQL Server 로그인을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3f137-128">To create a SQL Server login</span></span>  
  
1.  <span data-ttu-id="3f137-129">개체 탐색기에서 새 로그인을 만들려는 서버 인스턴스의 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-129">In Object Explorer, expand the folder of the server instance in which you want to create the new login.</span></span>  
  
2.  <span data-ttu-id="3f137-130">**보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 후 **로그인...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-130">Right-click the **Security** folder, point to **New**, and select **Login...**.</span></span>  
  
3.  <span data-ttu-id="3f137-131">**로그인 - 신규** 대화 상자의 **일반** 페이지에서 **로그인 이름** 상자에 사용자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-131">In the **Login - New** dialog box, on the **General** page, enter the name of a user in the **Login name** box.</span></span> <span data-ttu-id="3f137-132">또는 **검색...** 을 클릭하여 **사용자 또는 그룹 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-132">Alternately, click **Search...** to open the **Select User or Group** dialog box.</span></span>  
  
     <span data-ttu-id="3f137-133">**검색...** 을 클릭한 경우:</span><span class="sxs-lookup"><span data-stu-id="3f137-133">If you click **Search...**:</span></span>  
  
    1.  <span data-ttu-id="3f137-134">**개체 유형 선택**에서 **개체 유형...** 을 클릭하여 **개체 유형** 대화 상자를 열고 다음 중에서 일부 또는 전부를 선택합니다. **기본 제공 보안 주체**, **그룹** 및 **사용자**.</span><span class="sxs-lookup"><span data-stu-id="3f137-134">Under **Select this object type**, click **Object Types...** to open the **Object Types** dialog box and select any or all of the following: **Built-in security principals**, **Groups**, and **Users**.</span></span> <span data-ttu-id="3f137-135">**기본 제공 보안 주체** 및 **사용자** 는 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-135">**Built-in security principals** and **Users** are selected by default.</span></span> <span data-ttu-id="3f137-136">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-136">When finished, click **OK**.</span></span>  
  
    2.  <span data-ttu-id="3f137-137">**찾을 위치를 선택하세요.** 에서 **위치...** 를 클릭하여 **위치** 대화 상자를 열고 사용 가능한 서버 위치 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-137">Under **From this location**, click **Locations...** to open the **Locations** dialog box and select one of the available server locations.</span></span> <span data-ttu-id="3f137-138">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-138">When finished, click **OK**.</span></span>  
  
    3.  <span data-ttu-id="3f137-139">**선택할 개체 이름을 입력하세요(예제)** 에서 찾으려는 사용자 또는 그룹 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-139">Under **Enter the object name to select (examples)**, enter the user or group name that you want to find.</span></span> <span data-ttu-id="3f137-140">자세한 내용은 [사용자, 컴퓨터 또는 그룹 선택 대화 상자](https://technet.microsoft.com/library/cc771712.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-140">For more information, see [Select Users, Computers, or Groups Dialog Box](https://technet.microsoft.com/library/cc771712.aspx).</span></span>  
  
    4.  <span data-ttu-id="3f137-141">고급 검색 옵션을 보려면 **고급...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-141">Click **Advanced...** for more advanced search options.</span></span> <span data-ttu-id="3f137-142">자세한 내용은 [사용자, 컴퓨터 또는 그룹 선택 대화 상자 - 고급 페이지](https://technet.microsoft.com/library/cc733110.aspx)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-142">For more information, see [Select Users, Computers, or Groups Dialog Box - Advanced Page](https://technet.microsoft.com/library/cc733110.aspx).</span></span>  
  
    5.  <span data-ttu-id="3f137-143">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-143">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="3f137-144">보안 주체에 따라 로그인을 만들려면 **Windows 인증**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-144">To create a login based on a Windows principal, select **Windows authentication**.</span></span> <span data-ttu-id="3f137-145">이 옵션이 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-145">This is the default selection.</span></span>  
  
5.  <span data-ttu-id="3f137-146">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 저장된 로그인을 만들려면 **SQL Server 인증**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-146">To create a login that is saved on a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database, select **SQL Server authentication**.</span></span>  
  
    1.  <span data-ttu-id="3f137-147">**암호** 상자에 새 사용자의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-147">In the **Password** box, enter a password for the new user.</span></span> <span data-ttu-id="3f137-148">**암호 확인** 상자에 암호를 다시 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-148">Enter that password again into the **Confirm Password** box.</span></span>  
  
    2.  <span data-ttu-id="3f137-149">기존 암호를 변경할 때는 **이전 암호 지정**을 선택하고 **이전 암호** 상자에 이전 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-149">When changing an existing password, select **Specify old password**, and then type the old password in the **Old password** box.</span></span>  
  
    3.  <span data-ttu-id="3f137-150">복잡성 및 강제 적용에 대한 암호 정책 옵션을 강제로 적용하려면 **암호 정책 강제 적용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-150">To enforce password policy options for complexity and enforcement, select **Enforce password policy**.</span></span> <span data-ttu-id="3f137-151">자세한 내용은 [Password Policy](../password-policy.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-151">For more information, see [Password Policy](../password-policy.md).</span></span> <span data-ttu-id="3f137-152">이 옵션은 **SQL Server 인증** 을 선택한 경우 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-152">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    4.  <span data-ttu-id="3f137-153">만료에 대한 암호 정책 옵션을 강제로 적용하려면 **암호 만료 강제 적용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-153">To enforce password policy options for expiration, select **Enforce password expiration**.</span></span> <span data-ttu-id="3f137-154">이 확인란은**암호 정책 강제 적용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-154">**Enforce password policy** must be selected to enable this checkbox.</span></span> <span data-ttu-id="3f137-155">이 옵션은 **SQL Server 인증** 을 선택한 경우 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-155">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
    5.  <span data-ttu-id="3f137-156">사용자가 처음 로그인을 사용한 후 새 암호를 만들도록 하려면 **다음 로그인할 때 반드시 암호 변경**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-156">To force the user to create a new password after the first time the login is used, select **User must change password at next login**.</span></span> <span data-ttu-id="3f137-157">이 확인란은**암호 만료 강제 적용** 을 선택한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-157">**Enforce password expiration** must be selected to enable this checkbox.</span></span> <span data-ttu-id="3f137-158">이 옵션은 **SQL Server 인증** 을 선택한 경우 기본 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-158">This is a default option when **SQL Server authentication** is selected.</span></span>  
  
6.  <span data-ttu-id="3f137-159">로그인을 독립형 보안 인증서와 연결하려면 **인증서로 매핑** 을 선택한 후 목록에서 기존 인증서의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-159">To associate the login with a stand-alone security certificate, select **Mapped to certificate** and then select the name of an existing certificate from the list.</span></span>  
  
7.  <span data-ttu-id="3f137-160">로그인을 독립형 비대칭 키와 연결하려면 **비대칭 키로 매핑** 을 선택한 후 목록에서 기존 키의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-160">To associate the login with a stand-alone asymmetric key, select **Mapped to asymmetric key** to, and then select the name of an existing key from the list.</span></span>  
  
8.  <span data-ttu-id="3f137-161">로그인을 보안 인증서와 연결하려면 **인증서로 매핑** 확인란을 선택한 후 목록에서 기존 인증서를 선택하거나 **추가** 를 클릭하여 새 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-161">To associate the login with a security credential, select the **Mapped to Credential** check box, and then either select an existing credential from the list or click **Add** to create a new credential.</span></span> <span data-ttu-id="3f137-162">로그인에서 보안 인증서에 대한 매핑을 제거하려면 **인증서로 매핑** 에서 인증서를 선택하고 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-162">To remove a mapping to a security credential from the login, select the credential from **Mapped Credentials** and click **Remove**.</span></span> <span data-ttu-id="3f137-163">일반적으로 인증서에 대한 자세한 내용은 [자격 증명&#40;데이터베이스 엔진&#41;](credentials-database-engine.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-163">For more information about credentials in general, see [Credentials &#40;Database Engine&#41;](credentials-database-engine.md).</span></span>  
  
9. <span data-ttu-id="3f137-164">**기본 데이터베이스** 목록에서 로그인에 대한 기본 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-164">From the **Default database** list, select a default database for the login.</span></span> <span data-ttu-id="3f137-165">**Master** 는 이 옵션의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-165">**Master** is the default for this option.</span></span>  
  
10. <span data-ttu-id="3f137-166">**기본 언어** 목록에서 로그인에 대한 기본 언어를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-166">From the **Default language** list, select a default language for the login.</span></span>  
  
11. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="3f137-167">추가 옵션</span><span class="sxs-lookup"><span data-stu-id="3f137-167">Additional Options</span></span>  
 <span data-ttu-id="3f137-168">**로그인 - 신규** 대화 상자에서는 다음 네 가지 추가 페이지에 대한 옵션도 제공합니다. **서버 역할**, **사용자 매핑**, **보안 개체** 및 **상태**.</span><span class="sxs-lookup"><span data-stu-id="3f137-168">The **Login - New** dialog box also offers options on four additional pages: **Server Roles**, **User Mapping**, **Securables**, and **Status**.</span></span>  
  
### <a name="server-roles"></a><span data-ttu-id="3f137-169">서버 역할</span><span class="sxs-lookup"><span data-stu-id="3f137-169">Server Roles</span></span>  
 <span data-ttu-id="3f137-170">**서버 역할** 페이지에는 새 로그인에 할당할 수 있는 모든 사용 가능한 역할이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-170">The **Server Roles** page lists all possible roles that can be assigned to the new login.</span></span> <span data-ttu-id="3f137-171">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-171">The following options are available:</span></span>  
  
 <span data-ttu-id="3f137-172">**bulkadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-172">**bulkadmin** check box</span></span>  
 <span data-ttu-id="3f137-173">**bulkadmin** 고정 서버 역할의 멤버는 BULK INSERT 문을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-173">Members of the **bulkadmin** fixed server role can run the BULK INSERT statement.</span></span>  
  
 <span data-ttu-id="3f137-174">**dbcreator** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-174">**dbcreator** check box</span></span>  
 <span data-ttu-id="3f137-175">**dbcreator** 고정 서버 역할의 멤버는 데이터베이스를 생성, 변경, 삭제, 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-175">Members of the **dbcreator** fixed server role can create, alter, drop, and restore any database.</span></span>  
  
 <span data-ttu-id="3f137-176">**diskadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-176">**diskadmin** check box</span></span>  
 <span data-ttu-id="3f137-177">**dbcreator** 고정 서버 역할의 멤버는 디스크 파일을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-177">Members of the **diskadmin** fixed server role can manage disk files.</span></span>  
  
 <span data-ttu-id="3f137-178">**processadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-178">**processadmin** check box</span></span>  
 <span data-ttu-id="3f137-179">**processadmin** 고정 서버 역할의 멤버는 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]의 인스턴스에서 실행되는 프로세스를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-179">Members of the **processadmin** fixed server role can terminate processes running in an instance of the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="3f137-180">**public** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-180">**public** check box</span></span>  
 <span data-ttu-id="3f137-181">모든 SQL Server 사용자, 그룹 및 역할은 기본적으로 **public** 고정 서버 역할에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-181">All SQL Server users, groups, and roles belong to the **public** fixed server role by default.</span></span>  
  
 <span data-ttu-id="3f137-182">**securityadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-182">**securityadmin** check box</span></span>  
 <span data-ttu-id="3f137-183">**securityadmin** 고정 서버 역할의 멤버는 로그인 및 해당 속성을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-183">Members of the **securityadmin** fixed server role manage logins and their properties.</span></span> <span data-ttu-id="3f137-184">이러한 멤버는 서버 수준의 사용 권한을 부여(GRANT), 거부(DENY) 및 취소(REVOKE)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-184">They can GRANT, DENY, and REVOKE server-level permissions.</span></span> <span data-ttu-id="3f137-185">또한 데이터베이스 수준의 사용 권한을 부여(GRANT), 거부(DENY) 및 취소(REVOKE)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-185">They can also GRANT, DENY, and REVOKE database-level permissions.</span></span> <span data-ttu-id="3f137-186">또한 이 역할의 멤버는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 로그인 암호를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-186">Additionally, they can reset passwords for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span>  
  
 <span data-ttu-id="3f137-187">**serveradmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-187">**serveradmin** check box</span></span>  
 <span data-ttu-id="3f137-188">**serveradmin** 고정 서버 역할의 멤버는 서버 차원의 구성 옵션을 변경하고 서버를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-188">Members of the **serveradmin** fixed server role can change server-wide configuration options and shut down the server.</span></span>  
  
 <span data-ttu-id="3f137-189">**setupadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-189">**setupadmin** check box</span></span>  
 <span data-ttu-id="3f137-190">**setupadmin** 고정 서버 역할의 멤버는 연결된 서버를 추가하거나 제거하고 일부 시스템 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-190">Members of the **setupadmin** fixed server role can add and remove linked servers, and they can execute some system stored procedures.</span></span>  
  
 <span data-ttu-id="3f137-191">**sysadmin** 확인란</span><span class="sxs-lookup"><span data-stu-id="3f137-191">**sysadmin** check box</span></span>  
 <span data-ttu-id="3f137-192">**sysadmin** 고정 서버 역할의 멤버는 모든 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-192">Members of the **sysadmin** fixed server role can perform any activity in the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
### <a name="user-mapping"></a><span data-ttu-id="3f137-193">사용자 매핑</span><span class="sxs-lookup"><span data-stu-id="3f137-193">User Mapping</span></span>  
 <span data-ttu-id="3f137-194">**사용자 매핑** 페이지에는 사용 가능한 모든 데이터베이스와 이러한 데이터베이스에서 해당 로그인에 적용할 수 있는 데이터베이스 역할이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-194">The **User Mapping** page lists all possible databases and the database role memberships on those databases that can be applied to the login.</span></span> <span data-ttu-id="3f137-195">선택한 데이터베이스에 따라 로그인에 사용할 수 있는 역할 멤버 자격이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-195">The databases selected determine the role memberships that are available for the login.</span></span> <span data-ttu-id="3f137-196">이 페이지에서는 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-196">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="3f137-197">**이 로그인으로 매핑된 사용자**</span><span class="sxs-lookup"><span data-stu-id="3f137-197">**Users mapped to this login**</span></span>  
 <span data-ttu-id="3f137-198">이 로그인으로 액세스할 수 있는 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-198">Select the databases that this login can access.</span></span> <span data-ttu-id="3f137-199">데이터베이스를 선택하면 **데이터베이스 역할 멤버 자격 대상:** _database_name_ 창에 유효한 데이터베이스 역할이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-199">When you select a database, its valid database roles are displayed in the **Database role membership for:** _database_name_ pane.</span></span>  
  
 <span data-ttu-id="3f137-200">**Map**</span><span class="sxs-lookup"><span data-stu-id="3f137-200">**Map**</span></span>  
 <span data-ttu-id="3f137-201">아래 나열되는 데이터베이스에 해당 로그인이 액세스하는 것을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-201">Allow the login to access the databases listed below.</span></span>  
  
 <span data-ttu-id="3f137-202">**Database**</span><span class="sxs-lookup"><span data-stu-id="3f137-202">**Database**</span></span>  
 <span data-ttu-id="3f137-203">서버의 사용 가능한 데이터베이스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-203">Lists the databases available on the server.</span></span>  
  
 <span data-ttu-id="3f137-204">**사용자**</span><span class="sxs-lookup"><span data-stu-id="3f137-204">**User**</span></span>  
 <span data-ttu-id="3f137-205">로그인에 매핑할 데이터베이스 사용자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-205">Specify a database user to map to the login.</span></span> <span data-ttu-id="3f137-206">기본적으로 데이터베이스 사용자의 이름은 로그인과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-206">By default, the database user has the same name as the login.</span></span>  
  
 <span data-ttu-id="3f137-207">**기본 스키마**</span><span class="sxs-lookup"><span data-stu-id="3f137-207">**Default Schema**</span></span>  
 <span data-ttu-id="3f137-208">사용자의 기본 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-208">Specifies the default schema of the user.</span></span> <span data-ttu-id="3f137-209">사용자를 처음 만들 경우 기본 스키마는 **dbo**입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-209">When a user is first created, its default schema is **dbo**.</span></span> <span data-ttu-id="3f137-210">아직 존재하지 않는 기본 스키마를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-210">It is possible to specify a default schema that does not yet exist.</span></span> <span data-ttu-id="3f137-211">Windows 그룹, 인증서 또는 비대칭 키에 매핑된 사용자에 대해서는 기본 스키마를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-211">You cannot specify a default schema for a user that is mapped to a Windows group, a certificate, or an asymmetric key.</span></span>  
  
 <span data-ttu-id="3f137-212">**게스트 계정 활성화 대상:**  _database_name_</span><span class="sxs-lookup"><span data-stu-id="3f137-212">**Guest account enabled for:**  _database_name_</span></span>  
 <span data-ttu-id="3f137-213">선택한 데이터베이스에 게스트 계정이 설정되어 있는지 여부를 나타내는 읽기 전용 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-213">Read-only attribute indicating whether the Guest account is enabled on the selected database.</span></span> <span data-ttu-id="3f137-214">게스트 계정에 대한 **로그인 속성** 대화 상자의 **상태** 페이지를 사용하여 게스트 계정을 설정하거나 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-214">Use the **Status** page of the **Login Properties** dialog box of the Guest account to enable or disable the Guest account.</span></span>  
  
 <span data-ttu-id="3f137-215">**데이터베이스 역할 멤버 자격 대상:**  _database_name_</span><span class="sxs-lookup"><span data-stu-id="3f137-215">**Database role membership for:**  _database_name_</span></span>  
 <span data-ttu-id="3f137-216">지정한 데이터베이스 사용자에 대한 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-216">Select the roles for the user in the specified database.</span></span> <span data-ttu-id="3f137-217">모든 사용자는 모든 데이터베이스에서 **public** 역할의 멤버이며 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-217">All users are members of the **public** role in every database and cannot be removed.</span></span> <span data-ttu-id="3f137-218">데이터베이스 역할에 대한 자세한 내용은 [데이터베이스 수준 역할](database-level-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-218">For more information about database roles, see [Database-Level Roles](database-level-roles.md).</span></span>  
  
### <a name="securables"></a><span data-ttu-id="3f137-219">보안 개체</span><span class="sxs-lookup"><span data-stu-id="3f137-219">Securables</span></span>  
 <span data-ttu-id="3f137-220">**보안 개체** 페이지에는 사용 가능한 모든 보안 개체와 이러한 보안 개체에서 로그인에 부여할 수 있는 권한이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-220">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span> <span data-ttu-id="3f137-221">이 페이지에서는 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-221">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="3f137-222">**상단 표**</span><span class="sxs-lookup"><span data-stu-id="3f137-222">**Upper Grid**</span></span>  
 <span data-ttu-id="3f137-223">사용 권한을 설정할 수 있는 항목이 하나 이상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-223">Contains one or more items for which permissions can be set.</span></span> <span data-ttu-id="3f137-224">상단 표에 표시되는 열은 보안 주체 또는 보안 개체에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-224">The columns that are displayed in the upper grid vary depending on the principal or securable.</span></span>  
  
 <span data-ttu-id="3f137-225">상단 표에 항목을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="3f137-225">To add items to the upper grid:</span></span>  
  
1.  <span data-ttu-id="3f137-226">**검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-226">Click **Search**.</span></span>  
  
2.  <span data-ttu-id="3f137-227">**개체 추가** 대화 상자에서 다음 옵션 중 하나를 선택 합니다. **특정 개체 ...**, **유형의 모든 개체**... 또는 **서버**_server_name_</span><span class="sxs-lookup"><span data-stu-id="3f137-227">In the **Add Objects** dialog box, select one of the following options: **Specific objects...**, **All objects of the types...**, or **The server**_server_name_.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="3f137-228">**서버**_server_name_ 를 선택 하면 상단 표에 해당 서버의 모든 보안 개체가 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-228">Selecting **The server**_server_name_ automatically fills the upper grid with all of that servers' securable objects.</span></span>  
  
3.  <span data-ttu-id="3f137-229">**특정 개체...** 를 선택한 경우:</span><span class="sxs-lookup"><span data-stu-id="3f137-229">If you select **Specific objects...**:</span></span>  
  
    1.  <span data-ttu-id="3f137-230">**개체 선택** 대화 상자의 **개체 유형 선택**에서 **개체 유형...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-230">In the **Select Objects** dialog box, under **Select these object types**, click **Object Types...**.</span></span>  
  
    2.  <span data-ttu-id="3f137-231">**개체 유형 선택** 대화 상자에서 다음 개체 유형 중 하나를 선택합니다. **엔드포인트**, **로그인**, **서버**, **가용성 그룹** 및 **서버 역할**.</span><span class="sxs-lookup"><span data-stu-id="3f137-231">In the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
    3.  <span data-ttu-id="3f137-232">**선택할 개체 이름을 입력하세요(예제)** 에서 **찾아보기...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-232">Under **Enter the object names to select (examples)**, click **Browse...**.</span></span>  
  
    4.  <span data-ttu-id="3f137-233">**개체 찾아보기** 대화 상자에서 **개체 유형 선택** 대화 상자에서 선택한 유형에 대해 사용 가능한 모든 개체를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-233">In the **Browse for Objects** dialog box, select any of the available objects of the type that you selected in the **Select Object Types** dialog box, and then click **OK**.</span></span>  
  
    5.  <span data-ttu-id="3f137-234">**개체 선택** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-234">In the **Select Objects** dialog box, click **OK**.</span></span>  
  
4.  <span data-ttu-id="3f137-235">**선택한 유형의 모든 개체...** 를 선택한 경우 **개체 유형 선택** 대화 상자에서 다음 개체 유형 중 일부 또는 전부를 선택합니다. **엔드포인트**, **로그인**, **서버**, **가용성 그룹** 및 **서버 역할**.</span><span class="sxs-lookup"><span data-stu-id="3f137-235">If you select **All objects of the types...**, in the **Select Object Types** dialog box, select any or all of the following object types: **Endpoints**, **Logins**, **Servers**, **Availability Groups**, and **Server roles**.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 <span data-ttu-id="3f137-236">**이름**</span><span class="sxs-lookup"><span data-stu-id="3f137-236">**Name**</span></span>  
 <span data-ttu-id="3f137-237">표에 추가된 각 보안 주체 또는 보안 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-237">The name of each principal or securable that is added to the grid.</span></span>  
  
 <span data-ttu-id="3f137-238">**형식**</span><span class="sxs-lookup"><span data-stu-id="3f137-238">**Type**</span></span>  
 <span data-ttu-id="3f137-239">각 항목의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-239">Describes the type of each item.</span></span>  
  
 <span data-ttu-id="3f137-240">**명시적 탭**</span><span class="sxs-lookup"><span data-stu-id="3f137-240">**Explicit Tab**</span></span>  
 <span data-ttu-id="3f137-241">상단 표에서 선택한 보안 개체에 대해 사용 가능한 사용 권한이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-241">Lists the possible permissions for the securable that are selected in the upper grid.</span></span> <span data-ttu-id="3f137-242">모든 명시적 사용 권한에 대해 모든 옵션을 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-242">Not all options are available for all explicit permissions.</span></span>  
  
 <span data-ttu-id="3f137-243">**권한**</span><span class="sxs-lookup"><span data-stu-id="3f137-243">**Permissions**</span></span>  
 <span data-ttu-id="3f137-244">사용 권한의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-244">The name of the permission.</span></span>  
  
 <span data-ttu-id="3f137-245">**Grantor**</span><span class="sxs-lookup"><span data-stu-id="3f137-245">**Grantor**</span></span>  
 <span data-ttu-id="3f137-246">사용 권한을 부여한 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-246">The principal that granted the permission.</span></span>  
  
 <span data-ttu-id="3f137-247">**허용**</span><span class="sxs-lookup"><span data-stu-id="3f137-247">**Grant**</span></span>  
 <span data-ttu-id="3f137-248">로그인에 이 사용 권한을 허용하려면 선택하고</span><span class="sxs-lookup"><span data-stu-id="3f137-248">Select to grant this permission to the login.</span></span> <span data-ttu-id="3f137-249">사용 권한을 해제하려면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-249">Clear to revoke this permission.</span></span>  
  
 <span data-ttu-id="3f137-250">**허용 권한 소유**</span><span class="sxs-lookup"><span data-stu-id="3f137-250">**With Grant**</span></span>  
 <span data-ttu-id="3f137-251">나열된 사용 권한에 대한 WITH GRANT 옵션 상태를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-251">Reflects the state of the WITH GRANT option for the listed permission.</span></span> <span data-ttu-id="3f137-252">이 부분은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-252">This box is read-only.</span></span> <span data-ttu-id="3f137-253">이 사용 권한을 적용하려면 [GRANT](/sql/t-sql/statements/grant-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-253">To apply this permission, use the [GRANT](/sql/t-sql/statements/grant-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="3f137-254">**거부**</span><span class="sxs-lookup"><span data-stu-id="3f137-254">**Deny**</span></span>  
 <span data-ttu-id="3f137-255">로그인에 이 사용 권한을 거부하려면 선택하고</span><span class="sxs-lookup"><span data-stu-id="3f137-255">Select to deny this permission to the login.</span></span> <span data-ttu-id="3f137-256">사용 권한을 해제하려면 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-256">Clear to revoke this permission.</span></span>  
  
### <a name="status"></a><span data-ttu-id="3f137-257">상태</span><span class="sxs-lookup"><span data-stu-id="3f137-257">Status</span></span>  
 <span data-ttu-id="3f137-258">**상태** 페이지에는 선택한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인에 대해 구성할 수 있는 몇 가지 인증 및 권한 부여 옵션이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-258">The **Status** page lists some of the authentication and authorization options that can be configured on the selected [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login.</span></span>  
  
 <span data-ttu-id="3f137-259">이 페이지에서는 다음과 같은 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-259">The following options are available on this page:</span></span>  
  
 <span data-ttu-id="3f137-260">**데이터베이스 엔진 연결 권한**</span><span class="sxs-lookup"><span data-stu-id="3f137-260">**Permission to connect to database engine**</span></span>  
 <span data-ttu-id="3f137-261">이 설정을 사용할 때 사용자는 선택한 로그인을 보안 개체에 대한 권한을 부여하거나 거부할 수 있는 보안 주체로 간주해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-261">When you work with this setting, you should think of the selected login as a principal that can be granted or denied permission on a securable.</span></span>  
  
 <span data-ttu-id="3f137-262">로그인에 CONNECT SQL 권한을 부여하려면 **허용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-262">Select **Grant** to grant CONNECT SQL permission to the login.</span></span> <span data-ttu-id="3f137-263">로그인에 CONNECT SQL을 거부하려면 **거부** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-263">Select **Deny** to deny CONNECT SQL to the login.</span></span>  
  
 <span data-ttu-id="3f137-264">**로그인**</span><span class="sxs-lookup"><span data-stu-id="3f137-264">**Login**</span></span>  
 <span data-ttu-id="3f137-265">이 설정을 사용할 때 사용자는 선택한 로그인을 테이블에 있는 레코드로 간주해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-265">When you work with this setting, you should think of the selected login as a record in a table.</span></span> <span data-ttu-id="3f137-266">여기에 나열된 값의 변경 내용은 레코드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-266">Changes to the values listed here will be applied to the record.</span></span>  
  
 <span data-ttu-id="3f137-267">사용하지 않도록 선택한 로그인은 레코드로 계속 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-267">A login that has been disabled continues to exist as a record.</span></span> <span data-ttu-id="3f137-268">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결하려는 경우 로그인이 인증되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-268">But if it tries to connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the login will not be authenticated.</span></span>  
  
 <span data-ttu-id="3f137-269">이 로그인을 사용하거나 사용하지 않도록 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-269">Select this option to enable or disable this login.</span></span> <span data-ttu-id="3f137-270">이 옵션은 ALTER LOGIN 문에 ENABLE 또는 DISABLE 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-270">This option uses the ALTER LOGIN statement with the either ENABLE or DISABLE option.</span></span>  
  
 <span data-ttu-id="3f137-271">**SQL Server 인증**</span><span class="sxs-lookup"><span data-stu-id="3f137-271">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="3f137-272">**로그인 잠겨 있음** 확인란은 선택한 로그인을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 사용하여 연결하고 로그인이 잠겨 있는 경우에만 사용할 수 있습니다. 이 설정은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-272">The check box **Login is locked out** is only available if the selected login connects using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication and the login has been locked out. This setting is read-only.</span></span> <span data-ttu-id="3f137-273">잠긴 로그인을 잠금 해제하려면 UNLOCK 옵션을 사용하여 ALTER LOGIN을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-273">To unlock a login that is locked out, execute ALTER LOGIN with the UNLOCK option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="3f137-274">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="3f137-274">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-login-using-windows-authentication"></a><span data-ttu-id="3f137-275">Windows 인증을 사용하여 로그인을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3f137-275">To create a login using Windows Authentication</span></span>  
  
1.  <span data-ttu-id="3f137-276">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-276">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3f137-277">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-277">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3f137-278">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-278">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Create a login for SQL Server by specifying a server name and a Windows domain account name.  
  
    CREATE LOGIN [<domainName>\<loginName>] FROM WINDOWS;  
    GO  
  
    ```  
  
#### <a name="to-create-a-login-using-sql-server-authentication"></a><span data-ttu-id="3f137-279">SQL Server 인증을 사용하여 로그인을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3f137-279">To create a login using SQL Server Authentication</span></span>  
  
1.  <span data-ttu-id="3f137-280">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-280">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="3f137-281">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-281">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="3f137-282">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-282">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the user "shcooper" for SQL Server using the security credential "RestrictedFaculty"   
    -- The user login starts with the password "Baz1nga," but that password must be changed after the first login.  
  
    CREATE LOGIN shcooper   
       WITH PASSWORD = 'Baz1nga' MUST_CHANGE,  
       CREDENTIAL = RestrictedFaculty;  
    GO  
  
    ```  
  
 <span data-ttu-id="3f137-283">자세한 내용은 [CREATE LOGIN&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-283">For more information, see [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql).</span></span>  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-login"></a><a name="FollowUp"></a> <span data-ttu-id="3f137-284">후속 작업: 로그인을 만든 후 수행할 단계</span><span class="sxs-lookup"><span data-stu-id="3f137-284">Follow Up: Steps to take after you create a login</span></span>  
 <span data-ttu-id="3f137-285">이와 같이 작성한 로그인은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 수 있지만 유용한 작업을 수행하는 데 필요한 사용 권한은 가지고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-285">After creating a login, the login can connect to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], but does not necessarily have sufficient permission to perform any useful work.</span></span> <span data-ttu-id="3f137-286">다음 목록에서는 일반적인 로그인 동작 관련 내용이 포함된 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f137-286">The following list provides links to common login actions.</span></span>  
  
-   <span data-ttu-id="3f137-287">로그인이 역할에 조인하도록 하려면 [역할 조인](join-a-role.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-287">To have the login join a role, see [Join a Role](join-a-role.md).</span></span>  
  
-   <span data-ttu-id="3f137-288">로그인에 데이터베이스 사용 권한을 부여하려면 [데이터베이스 사용자 만들기](../authentication-access/create-a-database-user.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-288">To authorize a login to use a database, see [Create a Database User](../authentication-access/create-a-database-user.md).</span></span>  
  
-   <span data-ttu-id="3f137-289">로그인에 사용 권한을 부여하려면 [보안 주체에 사용 권한 부여](grant-a-permission-to-a-principal.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f137-289">To grant a permission to a login, see [Grant a Permission to a Principal](grant-a-permission-to-a-principal.md).</span></span>  
  
  
