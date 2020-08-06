---
title: 데이터베이스 사용자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 97fc758c754f5fc8803e988d55147670fc3ff45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730383"
---
# <a name="create-a-database-user"></a><span data-ttu-id="b0470-102">데이터베이스 사용자 만들기</span><span class="sxs-lookup"><span data-stu-id="b0470-102">Create a Database User</span></span>
  <span data-ttu-id="b0470-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 로그인에 매핑되는 데이터베이스 사용자를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-103">This topic describes how to create a database user mapped to a login in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b0470-104">데이터베이스 사용자는 데이터베이스 연결 시의 로그인 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-104">The database user is the identity of the login when it is connected to a database.</span></span> <span data-ttu-id="b0470-105">데이터베이스 사용자는 원하는 경우 로그인과 같은 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-105">The database user can use the same name as the login, but that is not required.</span></span> <span data-ttu-id="b0470-106">이 항목에서는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 로그인이 이미 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-106">This topic assumes that a login already exists in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b0470-107">로그인을 만드는 방법에 대 한 자세한 내용은 [로그인 만들기](create-a-login.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b0470-107">For information about how to create a login, see [Create a Login](create-a-login.md).</span></span>  
  
 <span data-ttu-id="b0470-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b0470-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b0470-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b0470-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b0470-110">배경</span><span class="sxs-lookup"><span data-stu-id="b0470-110">Background</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b0470-111">보안</span><span class="sxs-lookup"><span data-stu-id="b0470-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b0470-112">**다음을 사용하여 데이터베이스를 만들려면:**</span><span class="sxs-lookup"><span data-stu-id="b0470-112">**To create a database user, using:**</span></span>  
  
     [<span data-ttu-id="b0470-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b0470-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b0470-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b0470-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b0470-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b0470-115">Before You Begin</span></span>  
  
###  <a name="background"></a><a name="Restrictions"></a> <span data-ttu-id="b0470-116">배경</span><span class="sxs-lookup"><span data-stu-id="b0470-116">Background</span></span>  
 <span data-ttu-id="b0470-117">사용자는 데이터베이스 수준의 보안 주체입니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-117">A user is a database level security principal.</span></span> <span data-ttu-id="b0470-118">데이터베이스에 연결하려면 로그인을 데이터베이스 사용자로 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-118">Logins must be mapped to a database user to connect to a database.</span></span> <span data-ttu-id="b0470-119">로그인을 다른 데이터베이스에 다른 사용자로 매핑할 수 있지만 각 데이터베이스에서 한 명의 사용자로만 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-119">A login can be mapped to different databases as different users but can only be mapped as one user in each database.</span></span> <span data-ttu-id="b0470-120">부분적으로 포함된 데이터베이스에서는 로그인을 포함하지 않는 사용자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-120">In a partially contained database, a user can be created that does not have a login.</span></span> <span data-ttu-id="b0470-121">포함된 데이터베이스 사용자에 대한 자세한 내용은 [CREATE USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0470-121">For more information about contained database users, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span> <span data-ttu-id="b0470-122">데이터베이스에서 게스트 사용자가 설정된 경우 데이터베이스 사용자에 매핑되지 않은 로그인이 게스트 사용자로 데이터베이스에 진입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-122">If the guest user in a database is enabled, a login that is not mapped to a database user can enter the database as the guest user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b0470-123">게스트 사용자는 보통 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-123">The guest user is ordinarily disabled.</span></span> <span data-ttu-id="b0470-124">반드시 필요한 경우가 아니면 게스트 사용자를 사용하도록 설정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b0470-124">Do not enable the guest user unless it is necessary.</span></span>  
  
 <span data-ttu-id="b0470-125">보안 주체는 사용 권한을 사용자에게 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-125">As a security principal, permissions can be granted to users.</span></span> <span data-ttu-id="b0470-126">사용자의 범위는 데이터베이스입니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-126">The scope of a user is the database.</span></span> <span data-ttu-id="b0470-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에서 특정 데이터베이스에 연결하려면 로그인을 데이터베이스 사용자에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-127">To connect to a specific database on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a login must be mapped to a database user.</span></span> <span data-ttu-id="b0470-128">이 경우 로그인이 아니라 데이터베이스 내의 사용 권한이 데이터베이스 사용자에게 부여되며 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-128">Permissions inside the database are granted and denied to the database user, not the login.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b0470-129">보안</span><span class="sxs-lookup"><span data-stu-id="b0470-129">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b0470-130">권한</span><span class="sxs-lookup"><span data-stu-id="b0470-130">Permissions</span></span>  
 <span data-ttu-id="b0470-131">데이터베이스에 대한 `ALTER ANY USER` 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-131">Requires `ALTER ANY USER` permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b0470-132">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b0470-132">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-database-user"></a><span data-ttu-id="b0470-133">데이터베이스 사용자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b0470-133">To create a database user</span></span>  
  
1.  <span data-ttu-id="b0470-134">개체 탐색기에서 **데이터베이스** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-134">In Object Explorer, expand the **Databases** folder.</span></span>  
  
2.  <span data-ttu-id="b0470-135">새 데이터베이스 사용자를 만들 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-135">Expand the database in which to create the new database user.</span></span>  
  
3.  <span data-ttu-id="b0470-136">**보안** 폴더를 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 가리킨 후 **사용자...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-136">Right-click the **Security** folder, point to **New**, and select **User...**.</span></span>  
  
4.  <span data-ttu-id="b0470-137">**데이터베이스 사용자-신규** 대화 상자의 **일반** 페이지에 있는 **사용자 유형** 목록에서 로그인을 사용 하는 **sql 사용자**, 로그인을 사용 **하지 않는 sql 사용자**, **인증서에 매핑된**사용자, **비대칭 키에 매핑된 사용자**또는 **Windows 사용자**의 사용자 유형 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-137">In the **Database User - New** dialog box, on the **General** page, select one of the following user types from the **User type** list: **SQL user with login**, **SQL user without login**, **User mapped to a certificate**, **User mapped to an asymmetric key**, or **Windows user**.</span></span>  
  
5.  <span data-ttu-id="b0470-138">**사용자 이름** 상자에 새 사용자의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-138">In the **User name** box, enter a name for the new user.</span></span> <span data-ttu-id="b0470-139">**사용자 유형** 목록에서 **Windows 사용자**를 선택한 경우 줄임표 **(…)** 를 클릭하여 **사용자 또는 그룹 선택** 대화 상자를 열 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-139">If you have chosen **Windows user** from the **User type** list, you can also click the ellipsis **(...)** to open the **Select User or Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="b0470-140">**로그인 이름** 상자에 사용자의 로그인을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-140">In the **Login name** box, enter the login for the user.</span></span> <span data-ttu-id="b0470-141">또는 줄임표 **(...)** 를 클릭하여 **로그인 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-141">Alternately, click the ellipsis **(...)** to open the **Select Login** dialog box.</span></span> <span data-ttu-id="b0470-142">**로그인 이름** 은 **사용자 유형** 목록에서 **로그인을 사용하는 SQL 사용자** 또는 **Windows 사용자** 를 선택한 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-142">**Login name** is available if you select either **SQL user with login** or **Windows user** from the **User type** list.</span></span>  
  
7.  <span data-ttu-id="b0470-143">**기본 스키마** 상자에서 이 사용자가 만든 개체를 소유할 스키마를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-143">In the **Default schema** box, specifies the schema that will own objects created by this user.</span></span> <span data-ttu-id="b0470-144">또는 줄임표 **(...)** 를 클릭하여 **스키마 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-144">Alternately, click the ellipsis **(...)** to open the **Select Schema** dialog box.</span></span> <span data-ttu-id="b0470-145">**기본 스키마** 는 **사용자 유형**목록에서 **로그인을 사용하는 SQL 사용자**, **로그인을 사용하지 않는 SQL 사용자** 또는 **Windows 사용자** 를 선택한 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-145">**Default schema** is available if you select either **SQL user with login**, **SQL user without login**, or **Windows user** from the **User type** list.</span></span>  
  
8.  <span data-ttu-id="b0470-146">**인증서 이름** 상자에 데이터베이스 사용자에 대해 사용할 인증서를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-146">In the **Certificate name** box, enter the certificate to be used for the database user.</span></span> <span data-ttu-id="b0470-147">또는 줄임표 **(...)** 를 클릭하여 **인증서 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-147">Alternately, click the ellipsis **(...)** to open the **Select Certificate** dialog box.</span></span> <span data-ttu-id="b0470-148">**인증서 이름** 은 **사용자 유형** 목록에서 **인증서에 매핑된 사용자** 를 선택한 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-148">**Certificate name** is available if you select **User mapped to a certificate** from the **User type** list.</span></span>  
  
9. <span data-ttu-id="b0470-149">**비대칭 키 이름**  상자에 데이터베이스 사용자에 대해 사용할 키를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-149">In the **Asymmetric key name**  box, enter the key to be used for the database user.</span></span> <span data-ttu-id="b0470-150">또는 줄임표 **(...)** 를 클릭하여 **비대칭 키 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-150">Alternately, click the ellipsis **(...)** to open the **Select Asymmetric Key** dialog box.</span></span> <span data-ttu-id="b0470-151">**비대칭 키 이름** 은 **사용자 유형** 목록에서 **비대칭 키에 매핑된 사용자** 를 선택한 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-151">**Asymmetric key name** is available if you select **User mapped to an asymmetric key** from the **User type** list.</span></span>  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a><span data-ttu-id="b0470-152">추가 옵션</span><span class="sxs-lookup"><span data-stu-id="b0470-152">Additional Options</span></span>  
 <span data-ttu-id="b0470-153">**데이터베이스 사용자 - 신규** 대화 상자에서는 다음 네 가지 추가 페이지에 대한 옵션도 제공합니다. **소유한 스키마**, **멤버 자격**, **보안 개체** 및 **확장 속성**의 네 가지 추가 페이지에 대한 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-153">The **Database User - New** dialog box also offers options on four additional pages: **Owned Schemas**, **Membership**, **Securables**, and **Extended Properties**.</span></span>  
  
-   <span data-ttu-id="b0470-154">**소유한 스키마** 페이지에는 새 데이터베이스 사용자가 소유할 수 있는 모든 가능한 스키마가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-154">The **Owned Schemas** page lists all possible schemas that can be owned by the new database user.</span></span> <span data-ttu-id="b0470-155">데이터베이스 사용자로부터 스키마를 추가하거나 제거하려면 **이 사용자가 소유한 스키마**아래에서 스키마 옆에 있는 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-155">To add schemas to or remove them from a database user, under **Schemas owned by this user**, select or clear the check boxes next to the schemas.</span></span>  
  
-   <span data-ttu-id="b0470-156">**멤버 자격** 페이지에는 새 데이터베이스 사용자가 소유할 수 있는 모든 가능한 데이터베이스 멤버 자격 역할이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-156">The **Membership** page lists all possible database membership roles that can be owned by the new database user.</span></span> <span data-ttu-id="b0470-157">데이터베이스 사용자로부터 역할을 추가하거나 제거하려면 **데이터베이스 역할 멤버 자격**아래에서 역할 옆에 있는 확인란을 선택하거나 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-157">To add roles to or remove them from a database user, under **Database role membership**, select or clear the check boxes next to the roles.</span></span>  
  
-   <span data-ttu-id="b0470-158">**보안 개체** 페이지에는 사용 가능한 모든 보안 개체와 이러한 보안 개체에서 로그인에 부여할 수 있는 권한이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-158">The **Securables** page lists all possible securables and the permissions on those securables that can be granted to the login.</span></span>  
  
-   <span data-ttu-id="b0470-159">**확장 속성** 페이지에서는 데이터베이스 사용자에 사용자 지정 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-159">The **Extended properties** page allows you to add custom properties to database users.</span></span> <span data-ttu-id="b0470-160">이 페이지에서는 다음과 같은 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-160">The following options are available on this page.</span></span>  
  
     <span data-ttu-id="b0470-161">**Database**</span><span class="sxs-lookup"><span data-stu-id="b0470-161">**Database**</span></span>  
     <span data-ttu-id="b0470-162">선택한 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-162">Displays the name of the selected database.</span></span> <span data-ttu-id="b0470-163">이 필드는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-163">This field is read-only.</span></span>  
  
     <span data-ttu-id="b0470-164">**데이터 정렬**</span><span class="sxs-lookup"><span data-stu-id="b0470-164">**Collation**</span></span>  
     <span data-ttu-id="b0470-165">선택한 데이터베이스에 사용된 데이터 정렬을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-165">Displays the collation used for the selected database.</span></span> <span data-ttu-id="b0470-166">이 필드는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-166">This field is read-only.</span></span>  
  
     <span data-ttu-id="b0470-167">**속성**</span><span class="sxs-lookup"><span data-stu-id="b0470-167">**Properties**</span></span>  
     <span data-ttu-id="b0470-168">개체의 확장 속성을 확인하거나 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-168">View or specify the extended properties for the object.</span></span> <span data-ttu-id="b0470-169">각 확장 속성은 개체에 연결된 메타데이터의 이름/값 쌍으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-169">Each extended property consists of a name/value pair of metadata associated with the object.</span></span>  
  
     <span data-ttu-id="b0470-170">**줄임표(...)**</span><span class="sxs-lookup"><span data-stu-id="b0470-170">**Ellipsis (...)**</span></span>  
     <span data-ttu-id="b0470-171">**확장 속성 값** 대화 상자를 열려면 **값** 뒤에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-171">Click the ellipsis **(...)** after **Value** to open the **Value for Extended Property** dialog box.</span></span> <span data-ttu-id="b0470-172">더 큰 범위에서 확장 속성 값을 입력하거나 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-172">Type or view the value of the extended property in this larger location.</span></span> <span data-ttu-id="b0470-173">자세한 내용은 [확장 속성 값 대화 상자](../../databases/value-for-extended-property-dialog-box.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b0470-173">For more information, see [Value for Extended Property Dialog Box](../../databases/value-for-extended-property-dialog-box.md).</span></span>  
  
     <span data-ttu-id="b0470-174">**Delete**</span><span class="sxs-lookup"><span data-stu-id="b0470-174">**Delete**</span></span>  
     <span data-ttu-id="b0470-175">선택한 확장 속성을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-175">Removes the selected extended property.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b0470-176">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b0470-176">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-database-user"></a><span data-ttu-id="b0470-177">데이터베이스 사용자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b0470-177">To create a database user</span></span>  
  
1.  <span data-ttu-id="b0470-178">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-178">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b0470-179">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-179">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b0470-180">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b0470-180">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 <span data-ttu-id="b0470-181">자세한 내용은 [CREATE USER&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0470-181">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0470-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0470-182">See Also</span></span>  
 [<span data-ttu-id="b0470-183">보안 주체&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="b0470-183">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
