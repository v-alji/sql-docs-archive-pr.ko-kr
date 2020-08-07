---
title: 연결된 서버 만들기(SQL Server 데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 11/20/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.linkedserver.properties.general.f1
- sql12.swb.linkedserver.properties.security.f1
- sql12.swb.linkedserver.properties.provider.f1
- sql12.swb.linkedserver.properties.options.f1
helpviewer_keywords:
- linked servers [SQL Server], creating
ms.assetid: 3228065d-de8f-4ece-a9b1-e06d3dca9310
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6b28468db1024a9789364e5b6e5c115cba71fa9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730675"
---
# <a name="create-linked-servers-sql-server-database-engine"></a><span data-ttu-id="166a9-102">연결된 서버 만들기(SQL Server 데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="166a9-102">Create Linked Servers (SQL Server Database Engine)</span></span>
  <span data-ttu-id="166a9-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 연결된 서버를 만들고 다른 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 데이터에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-103">This topic shows how to create a linked server and access data from another [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="166a9-104">연결된 서버를 만들면 여러 원본의 데이터로 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-104">By creating a linked server,  you can work with data from multiple sources.</span></span> <span data-ttu-id="166a9-105">연결된 서버는 반드시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다른 인스턴스일 필요는 없지만 이것이 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-105">The linked server does not have to be another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but that is a common scenario.</span></span>  
  
##  <a name="background"></a><a name="Background"></a> <span data-ttu-id="166a9-106">배경</span><span class="sxs-lookup"><span data-stu-id="166a9-106">Background</span></span>  
 <span data-ttu-id="166a9-107">연결된 서버를 만들면 OLE DB 데이터 원본과 유형이 다른 분산 쿼리에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-107">A linked server allows for access to distributed, heterogeneous queries against OLE DB data sources.</span></span> <span data-ttu-id="166a9-108">연결된 서버를 만든 후 이 서버에 대해 분산 쿼리를 실행할 수 있으며 쿼리로 둘 이상의 데이터 원본의 테이블을 조인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-108">After a linked server is created, distributed queries can be run against this server, and queries can join tables from more than one data source.</span></span> <span data-ttu-id="166a9-109">연결된 서버를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스로 정의한 경우에는 원격 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-109">If the linked server is defined as an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], remote stored procedures can be executed.</span></span>  
  
 <span data-ttu-id="166a9-110">연결된 서버의 기능 및 필수 인수는 크게 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-110">The capabilities and required arguments of the linked server can vary significantly.</span></span> <span data-ttu-id="166a9-111">이 항목의 예에서는 일반적인 예제를 제공하지만 모든 옵션에 대해 설명하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-111">The examples in this topic provide a typical example but all options are not described.</span></span> <span data-ttu-id="166a9-112">자세한 내용은 [sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)의 데이터에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-112">For more information, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="166a9-113">보안</span><span class="sxs-lookup"><span data-stu-id="166a9-113">Security</span></span>  
  
### <a name="permissions"></a><span data-ttu-id="166a9-114">사용 권한</span><span class="sxs-lookup"><span data-stu-id="166a9-114">Permissions</span></span>  
 <span data-ttu-id="166a9-115">문을 사용 하는 경우 [!INCLUDE[tsql](../../includes/tsql-md.md)] `ALTER ANY LINKED SERVER` 서버에 대 한 사용 권한 또는 **setupadmin** 고정 서버 역할의 멤버 자격이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-115">When using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, requires `ALTER ANY LINKED SERVER` permission on the server or membership in the **setupadmin** fixed server role.</span></span> <span data-ttu-id="166a9-116">을 사용 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 하 `CONTROL SERVER` 는 경우 **sysadmin** 고정 서버 역할의 권한 또는 멤버 자격이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-116">When using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] requires `CONTROL SERVER` permission or membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="how-to-create-a-linked-server"></a><a name="Procedures"></a> <span data-ttu-id="166a9-117">방법: 연결된 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="166a9-117">How to Create a Linked Server</span></span>  
 <span data-ttu-id="166a9-118">다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-118">You can use any of the following:</span></span>  
  
-   [<span data-ttu-id="166a9-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="166a9-119">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   [<span data-ttu-id="166a9-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="166a9-120">Transact-SQL</span></span>](#TsqlProcedure)  
  
###  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="166a9-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="166a9-121">Using SQL Server Management Studio</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-sql-server-management-studio"></a><span data-ttu-id="166a9-122">SQL Server Management Studio를 사용하여 SQL Server의 다른 인스턴스에 연결된 서버를 만들려면</span><span class="sxs-lookup"><span data-stu-id="166a9-122">To create a linked server to another instance of SQL Server Using SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="166a9-123">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 열고 **서버 개체**를 확장한 다음 **연결된 서버**를 마우스 오른쪽 단추로 클릭하고 **새 연결된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-123">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open Object Explorer, expand **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
2.  <span data-ttu-id="166a9-124">**일반** 페이지의 **연결된 서버** 상자에 연결하려는 **SQL Server** 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-124">On the **General** page, in the **Linked server** box, type the name of the instance of **SQL Server** that you area linking to.</span></span>  
  
     <span data-ttu-id="166a9-125">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="166a9-125">**SQL Server**</span></span>  
     <span data-ttu-id="166a9-126">연결된 서버를 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-126">Identify the linked server as an instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="166a9-127">이 방법을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결된 서버를 정의하는 경우 **연결된 서버** 에 지정된 이름은 서버의 네트워크 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-127">If you use this method of defining a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] linked server, the name specified in **Linked server** must be the network name of the server.</span></span> <span data-ttu-id="166a9-128">또한 서버에서 검색된 모든 테이블은 연결된 서버에 로그인할 수 있도록 정의된 기본 데이터베이스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-128">Also, any tables retrieved from the server are from the default database defined for the login on the linked server.</span></span>  
  
     <span data-ttu-id="166a9-129">**기타 데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="166a9-129">**Other data source**</span></span>  
     <span data-ttu-id="166a9-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]이외의 OLE DB 서버 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-130">Specify an OLE DB server type other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="166a9-131">이 옵션을 클릭하면 그 아래의 옵션이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-131">Clicking this option activates the options below it.</span></span>  
  
     <span data-ttu-id="166a9-132">**공급자**</span><span class="sxs-lookup"><span data-stu-id="166a9-132">**Provider**</span></span>  
     <span data-ttu-id="166a9-133">목록 상자에서 OLE DB 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-133">Select an OLE DB data source from the list box.</span></span> <span data-ttu-id="166a9-134">OLE DB 공급자는 레지스트리에 지정된 PROGID로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-134">The OLE DB provider is registered with the given PROGID in the registry.</span></span>  
  
     <span data-ttu-id="166a9-135">**제품 이름**</span><span class="sxs-lookup"><span data-stu-id="166a9-135">**Product name**</span></span>  
     <span data-ttu-id="166a9-136">연결된 서버로 추가할 OLE DB 데이터 원본의 제품 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-136">Type the product name of the OLE DB data source to add as a linked server.</span></span>  
  
     <span data-ttu-id="166a9-137">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="166a9-137">**Data source**</span></span>  
     <span data-ttu-id="166a9-138">OLE DB 공급자가 해석할 데이터 원본 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-138">Type the name of the data source as interpreted by the OLE DB provider.</span></span> <span data-ttu-id="166a9-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결하는 경우에는 인스턴스 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-139">If you are connecting to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], provide the instance name.</span></span>  
  
     <span data-ttu-id="166a9-140">**공급자 문자열**</span><span class="sxs-lookup"><span data-stu-id="166a9-140">**Provider string**</span></span>  
     <span data-ttu-id="166a9-141">데이터 원본에 해당하는 OLE DB 공급자의 고유한 PROGID(프로그래밍 ID)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-141">Type the unique programmatic identifier (PROGID) of the OLE DB provider that corresponds to the data source.</span></span> <span data-ttu-id="166a9-142">올바른 공급자 문자열의 예는 [sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)의 데이터에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-142">For examples of valid provider strings, see [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span>  
  
     <span data-ttu-id="166a9-143">**위치**</span><span class="sxs-lookup"><span data-stu-id="166a9-143">**Location**</span></span>  
     <span data-ttu-id="166a9-144">OLE DB 공급자가 해석할 데이터베이스 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-144">Type the location of the database as interpreted by the OLE DB provider.</span></span>  
  
     <span data-ttu-id="166a9-145">**카탈로그**</span><span class="sxs-lookup"><span data-stu-id="166a9-145">**Catalog**</span></span>  
     <span data-ttu-id="166a9-146">OLE DB 공급자에 연결할 때 사용할 카탈로그 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-146">Type the name of the catalog to use when making a connection to the OLE DB provider.</span></span>  
  
     <span data-ttu-id="166a9-147">연결된 서버와의 연결을 테스트하려면 개체 탐색기에서 연결된 서버를 마우스 오른쪽 단추로 클릭한 다음 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-147">To test the ability to connect to a linked server, in Object Explorer, right-click the linked server and then click **Test Connection**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="166a9-148">**SQL Server** 인스턴스가 기본 인스턴스인 경우 **SQL Server**인스턴스를 호스팅하는 컴퓨터의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-148">If the instance of **SQL Server** is the default instance, enter the name of the computer that hosts the instance of **SQL Server**.</span></span> <span data-ttu-id="166a9-149">**SQL Server** 가 명명된 인스턴스인 경우 **Accounting\SQLExpress**와 같이 컴퓨터의 이름과 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-149">If the **SQL Server** is a named instance, enter the name of the computer and the name of the instance, such as **Accounting\SQLExpress**.</span></span>  
  
3.  <span data-ttu-id="166a9-150">**서버 유형** 영역에서 연결된 서버가 **SQL Server**의 다른 인스턴스임을 나타내도록 **SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-150">In the **Server type** area, select **SQL Server** to indicate that the linked server is another instance of **SQL Server**.</span></span>  
  
4.  <span data-ttu-id="166a9-151">**보안** 페이지에서 원본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결을 연결된 서버에 연결할 때 사용할 보안 컨텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-151">On the **Security** page, specify the security context that will be used when the original [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connects to the linked server.</span></span> <span data-ttu-id="166a9-152">사용자가 도메인 로그인을 사용하여 연결하는 도메인 환경에서는 **로그인의 현재 보안 컨텍스트를 사용하여 연결**을 선택하는 것이 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-152">In a domain environment where users are connecting by using their domain logins, selecting **Be made using the login's current security context** is often the best choice.</span></span> <span data-ttu-id="166a9-153">사용자가 **SQL Server** 로그인을 사용하여 원본 **SQL Server** 에 연결하는 경우에는 **다음 보안 컨텍스트를 사용하여 연결**을 선택한 다음 연결된 서버에서 인증하기 위해 필요한 자격 증명을 제공하는 것이 이상적입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-153">When users connect to the original **SQL Server** by using a **SQL Server** login, the best choice is often to select **By using this security context**, and then providing the necessary credentials to authenticate at the linked server.</span></span>  
  
     <span data-ttu-id="166a9-154">**로컬 로그인**</span><span class="sxs-lookup"><span data-stu-id="166a9-154">**Local login**</span></span>  
     <span data-ttu-id="166a9-155">연결된 서버에 연결할 수 있는 로컬 로그인을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-155">Specify the local login that can connect to the linked server.</span></span> <span data-ttu-id="166a9-156">로컬 로그인은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하는 로그인이나 Windows 인증 로그인 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-156">The local login can be either a login using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication or a Windows Authentication login.</span></span> <span data-ttu-id="166a9-157">이 목록을 사용하여 특정 로그인에 대한 연결을 제한하거나 일부 로그인이 다른 로그인으로 연결하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-157">Use this list to restrict the connection to specific logins, or to allow some logins to connect as a different login.</span></span>  
  
     <span data-ttu-id="166a9-158">**Impersonate**</span><span class="sxs-lookup"><span data-stu-id="166a9-158">**Impersonate**</span></span>  
     <span data-ttu-id="166a9-159">사용자 이름과 암호를 로컬 로그인에서 연결된 서버로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-159">Pass the username and password from the local login to the linked server.</span></span> <span data-ttu-id="166a9-160">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증의 경우 이름과 암호가 완전히 동일한 로그인이 원격 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-160">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, a login with the exact same name and password must exist on the remote server.</span></span> <span data-ttu-id="166a9-161">Windows 로그인의 경우 로그인이 연결된 서버에서 유효한 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-161">For Windows logins, the login must be a valid login on the linked server.</span></span>  
  
     <span data-ttu-id="166a9-162">가장을 사용하려면 구성이 위임 요구 사항을 만족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-162">To use impersonation, the configuration must meet the requirement for delegation.</span></span>  
  
     <span data-ttu-id="166a9-163">**원격 사용자**</span><span class="sxs-lookup"><span data-stu-id="166a9-163">**Remote User**</span></span>  
     <span data-ttu-id="166a9-164">원격 사용자를 사용하여 **로컬 로그인**에 정의되어 있지 않은 사용자를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-164">Use the remote user to map users not defined in **Local login**.</span></span> <span data-ttu-id="166a9-165">**원격 사용자** 는 원격 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-165">The **Remote User** must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
     <span data-ttu-id="166a9-166">**원격 암호**</span><span class="sxs-lookup"><span data-stu-id="166a9-166">**Remote Password**</span></span>  
     <span data-ttu-id="166a9-167">원격 사용자의 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-167">Specify the password of the Remote User.</span></span>  
  
     <span data-ttu-id="166a9-168">**추가**</span><span class="sxs-lookup"><span data-stu-id="166a9-168">**Add**</span></span>  
     <span data-ttu-id="166a9-169">새 로컬 로그인을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-169">Add a new local login.</span></span>  
  
     <span data-ttu-id="166a9-170">**제거**</span><span class="sxs-lookup"><span data-stu-id="166a9-170">**Remove**</span></span>  
     <span data-ttu-id="166a9-171">기존 로컬 로그인을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-171">Remove an existing local login.</span></span>  
  
     <span data-ttu-id="166a9-172">**연결 안 함**</span><span class="sxs-lookup"><span data-stu-id="166a9-172">**Not be made**</span></span>  
     <span data-ttu-id="166a9-173">목록에 정의되어 있지 않은 로그인의 경우 연결하지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-173">Specify that a connection will not be made for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="166a9-174">**보안 컨텍스트 없이 연결**</span><span class="sxs-lookup"><span data-stu-id="166a9-174">**Be made without using a security context**</span></span>  
     <span data-ttu-id="166a9-175">목록에 정의되어 있지 않은 로그인의 경우 보안 컨텍스트를 사용하지 않고 연결하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-175">Specify that a connection will be made without using a security context for logins not defined in the list.</span></span>  
  
     <span data-ttu-id="166a9-176">**로그인의 현재 보안 컨텍스트를 사용하여 연결**</span><span class="sxs-lookup"><span data-stu-id="166a9-176">**Be made using the login's current security context**</span></span>  
     <span data-ttu-id="166a9-177">목록에 정의되어 있지 않은 로그인의 경우 로그인의 현재 보안 컨텍스트를 사용하여 연결하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-177">Specify that a connection will be made using the current security context of the login for logins not defined in the list.</span></span> <span data-ttu-id="166a9-178">Windows 인증을 사용하여 로컬 서버에 연결한 경우 원격 서버에 연결하는 데 해당 Windows 자격 증명이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-178">If connected to the local server using Windows Authentication, your windows credentials will be used to connect to the remote server.</span></span> <span data-ttu-id="166a9-179">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 로컬 서버에 연결한 경우 원격 서버에 연결하는 데 로그인 이름 및 암호가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-179">If connected to the local server using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, login name and password will be used to connect to the remote server.</span></span> <span data-ttu-id="166a9-180">이 경우 이름과 암호가 완전히 동일한 로그인이 원격 서버에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-180">In this case a login with the exact same name and password must exist on the remote server.</span></span>  
  
     <span data-ttu-id="166a9-181">**다음 보안 컨텍스트를 사용하여 연결**</span><span class="sxs-lookup"><span data-stu-id="166a9-181">**Be made using this security context**</span></span>  
     <span data-ttu-id="166a9-182">목록에 정의되어 있지 않은 로그인의 경우 **원격 로그인** 및 **암호** 상자에서 지정한 로그인과 암호를 사용하여 연결하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-182">Specify that a connection will be made using the login and password specified in the **Remote login** and **With password** boxes for logins not defined in the list.</span></span> <span data-ttu-id="166a9-183">원격 로그인은 원격 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-183">The remote login must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login on the remote server.</span></span>  
  
5.  <span data-ttu-id="166a9-184">필요에 따라 서버 옵션을 보거나 지정하려면 **서버 옵션**  페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-184">Optionally, to view or specify server options, click the **Server Options**  page.</span></span>  
  
     <span data-ttu-id="166a9-185">**데이터 정렬 호환**</span><span class="sxs-lookup"><span data-stu-id="166a9-185">**Collation Compatible**</span></span>  
     <span data-ttu-id="166a9-186">연결된 서버에 대한 분산 쿼리 실행에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-186">Affects Distributed Query execution against linked servers.</span></span> <span data-ttu-id="166a9-187">이 옵션을 true로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 연결된 서버의 모든 문자에 대한 문자 집합 및 데이터 정렬 시퀀스(또는 정렬 순서)가 로컬 서버와 호환된다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-187">If this option is set to true, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assumes that all characters in the linked server are compatible with the local server, with regard to character set and collation sequence (or sort order).</span></span> <span data-ttu-id="166a9-188">이렇게 함으로써 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 문자 열에 관한 비교를 공급자에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-188">This enables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to send comparisons on character columns to the provider.</span></span> <span data-ttu-id="166a9-189">이 옵션을 설정하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 항상 문자 열에 관한 비교를 로컬로 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-189">If this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] always evaluates comparisons on character columns locally.</span></span>  
  
     <span data-ttu-id="166a9-190">이 옵션은 연결된 서버에 해당되는 데이터 원본이 로컬 서버와 동일한 문자 집합 및 정렬 순서를 갖고 있는 것이 확실한 경우에만 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-190">This option should be set only if it is certain that the data source corresponding to the linked server has the same character set and sort order as the local server.</span></span>  
  
     <span data-ttu-id="166a9-191">**데이터 액세스**</span><span class="sxs-lookup"><span data-stu-id="166a9-191">**Data Access**</span></span>  
     <span data-ttu-id="166a9-192">분산 쿼리 액세스에 대해 연결된 서버의 사용 여부를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-192">Enables and disables a linked server for distributed query access.</span></span>  
  
     <span data-ttu-id="166a9-193">**RPC**</span><span class="sxs-lookup"><span data-stu-id="166a9-193">**RPC**</span></span>  
     <span data-ttu-id="166a9-194">지정된 서버에서 RPC를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-194">Enables RPC from the specified server.</span></span>  
  
     <span data-ttu-id="166a9-195">**RPC 내보내기**</span><span class="sxs-lookup"><span data-stu-id="166a9-195">**RPC Out**</span></span>  
     <span data-ttu-id="166a9-196">지정된 서버에 RPC를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-196">Enables RPC to the specified server.</span></span>  
  
     <span data-ttu-id="166a9-197">**원격 데이터 정렬 사용**</span><span class="sxs-lookup"><span data-stu-id="166a9-197">**Use Remote Collation**</span></span>  
     <span data-ttu-id="166a9-198">원격 열의 데이터 정렬을 사용할지 로컬 서버의 데이터 정렬을 사용할지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-198">Determines whether the collation of a remote column or of a local server will be used.</span></span>  
  
     <span data-ttu-id="166a9-199">true로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 원본에 대해서는 원격 열의 데이터 정렬이 사용되고[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 아닌 데이터 원본에 대해서는 데이터 정렬 이름에 지정된 데이터 정렬이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-199">If true, the collation of remote columns is used for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources, and the collation specified in collation name is used for non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data sources.</span></span>  
  
     <span data-ttu-id="166a9-200">false로 설정하면 분산 쿼리에서 항상 로컬 서버의 기본 데이터 정렬을 사용하는 반면에 데이터 정렬 이름 및 원격 열의 데이터 정렬은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-200">If false, distributed queries will always use the default collation of the local server, while collation name and the collation of remote columns are ignored.</span></span> <span data-ttu-id="166a9-201">기본값은 false입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-201">The default is false.</span></span>  
  
     <span data-ttu-id="166a9-202">**데이터 정렬 이름**</span><span class="sxs-lookup"><span data-stu-id="166a9-202">**Collation Name**</span></span>  
     <span data-ttu-id="166a9-203">원격 데이터 정렬 사용이 true이고 데이터 원본이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 원본이 아닌 경우에 원격 데이터 원본에서 사용하는 데이터 정렬의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-203">Specifies the name of the collation used by the remote data source if use remote collation is true and the data source is not a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span> <span data-ttu-id="166a9-204">이름은 반드시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 지원하는 데이터 정렬 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-204">The name must be one of the collations supported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="166a9-205">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 아닌 OLE DB 데이터 원본에 액세스할 때 해당 데이터 정렬이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 정렬 중 하나와 일치하면 이 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="166a9-205">Use this option when accessing an OLE DB data source other than [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but whose collation matches one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="166a9-206">연결된 서버는 반드시 해당 서버의 모든 열에 대해 사용할 단일 데이터 정렬을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-206">The linked server must support a single collation to be used for all columns in that server.</span></span> <span data-ttu-id="166a9-207">연결된 서버에서 단일 데이터 원본 내에 여러 데이터 정렬을 지원하거나 연결된 서버의 데이터 정렬이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 정렬 중 하나와 일치하는지 확인할 수 없는 경우에는 이 옵션을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-207">Do not set this option if the linked server supports multiple collations within a single data source, or if the linked server's collation cannot be determined to match one of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span>  
  
     <span data-ttu-id="166a9-208">**연결 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="166a9-208">**Connection Timeout**</span></span>  
     <span data-ttu-id="166a9-209">연결된 서버에 연결하는 제한 시간 값(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-209">Time-out value in seconds for connecting to a linked server.</span></span>  
  
     <span data-ttu-id="166a9-210">0으로 설정하면 **sp_configure** 의 기본값인 [원격 로그인 제한 시간](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) 옵션 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-210">If 0, use the **sp_configure** default [remote login timeout](../../database-engine/configure-windows/configure-the-remote-login-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="166a9-211">**쿼리 시간 제한**</span><span class="sxs-lookup"><span data-stu-id="166a9-211">**Query Timeout**</span></span>  
     <span data-ttu-id="166a9-212">연결된 서버에 대한 쿼리의 제한 시간 값(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-212">Time-out value in seconds for queries against a linked server.</span></span>  
  
     <span data-ttu-id="166a9-213">0으로 설정하면 **sp_configure** 의 기본값인 [원격 쿼리 제한 시간](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) 옵션 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-213">If 0, use the **sp_configure** default [remote query timeout](../../database-engine/configure-windows/configure-the-remote-query-timeout-server-configuration-option.md) option value.</span></span>  
  
     <span data-ttu-id="166a9-214">**RPC에 대한 분산 트랜잭션 승격 설정**</span><span class="sxs-lookup"><span data-stu-id="166a9-214">**Enable Promotion of Distributed Transactions**</span></span>  
     <span data-ttu-id="166a9-215">이 옵션을 사용하여 MS DTC( [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator) 트랜잭션을 통해 서버 간 프로시저 동작을 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-215">Use this option to protect the actions of a server-to-server procedure through a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) transaction.</span></span> <span data-ttu-id="166a9-216">이 옵션이 TRUE인 경우 원격 저장 프로시저를 호출하면 분산 트랜잭션이 시작되고 MS DTC를 사용하여 이 트랜잭션을 참여시킵니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-216">When this option is TRUE, calling a remote stored procedure starts a distributed transaction and enlists the transaction with MS DTC.</span></span> <span data-ttu-id="166a9-217">자세한 내용은 [sp_serveroption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)의 데이터에 액세스하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-217">For more information, see [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql).</span></span>  
  
6.  <span data-ttu-id="166a9-218">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-218">Click **OK**.</span></span>  
  
##### <a name="to-view-the-provider-options"></a><span data-ttu-id="166a9-219">공급자 옵션을 보려면</span><span class="sxs-lookup"><span data-stu-id="166a9-219">To view the provider options</span></span>  
  
-   <span data-ttu-id="166a9-220">공급자를 사용할 수 있도록 설정하는 옵션을 보려면 **공급자 옵션** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-220">To view the options that the provider makes available, click the **Providers Options** page.</span></span>  
  
     <span data-ttu-id="166a9-221">공급자마다 사용 가능한 옵션은 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-221">All providers do not have the same options available.</span></span> <span data-ttu-id="166a9-222">예를 들어 일부 데이터 형식에는 사용 가능한 인덱스가 있지만 사용 가능한 인덱스가 없는 데이터 형식도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-222">For example, some types of data have indexes available and some might not.</span></span> <span data-ttu-id="166a9-223">이 대화 상자를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서의 공급자 기능을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-223">Use this dialog box to help [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] understand the capabilities of the provider.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="166a9-224">에서는 몇 가지 일반 데이터 공급자를 설치하는데, 데이터를 공급하는 제품이 변경되는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 설치한 공급자가 모든 최신 기능을 지원하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-224">installs some common data providers, however when the product providing the data changes, the provider installed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] might not support all the newest features.</span></span> <span data-ttu-id="166a9-225">데이터를 공급하는 제품 기능에 대한 가장 유용한 정보는 해당 제품 설명서에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-225">The best source of information about the capabilities of the product providing the data is the documentation for that product.</span></span>  
  
     <span data-ttu-id="166a9-226">**동적 매개 변수**</span><span class="sxs-lookup"><span data-stu-id="166a9-226">**Dynamic parameter**</span></span>  
     <span data-ttu-id="166a9-227">공급자에서 매개 변수가 있는 쿼리에 대해 '?' 매개 변수 표식 구문을 허용한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-227">Indicates that the provider allows '?' parameter marker syntax for parameterized queries.</span></span> <span data-ttu-id="166a9-228">이 옵션은 공급자가 **ICommandWithParameters** 인터페이스를 지원하고 '?'를 매개 변수 표식으로 지원하는 경우에만 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-228">Set this option only if the provider supports the **ICommandWithParameters** interface and supports a '?' as the parameter marker.</span></span> <span data-ttu-id="166a9-229">이 옵션을 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 공급자에 대해 매개 변수가 있는 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-229">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to execute parameterized queries against the provider.</span></span> <span data-ttu-id="166a9-230">공급자에 대해 매개 변수가 있는 쿼리를 실행할 수 있는 기능으로 인해 특정 쿼리의 경우 성능이 향상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-230">The ability to execute parameterized queries against the provider can result in better performance for certain queries.</span></span>  
  
     <span data-ttu-id="166a9-231">**중첩 쿼리**</span><span class="sxs-lookup"><span data-stu-id="166a9-231">**Nested queries**</span></span>  
     <span data-ttu-id="166a9-232">공급자가 FROM 절의  `SELECT` 중첩문을 허용함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-232">Indicates that the provider allows nested  `SELECT` statements in the FROM clause.</span></span> <span data-ttu-id="166a9-233">이 옵션을 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 FROM 절의 SELECT 중첩문을 요청하는 공급자에게 특정 쿼리를 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-233">Setting this option allows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to delegate certain queries to the provider that require nesting SELECT statements in the FROM clause.</span></span>  
  
     <span data-ttu-id="166a9-234">**0 수준만**</span><span class="sxs-lookup"><span data-stu-id="166a9-234">**Level zero only**</span></span>  
     <span data-ttu-id="166a9-235">공급자에 대해 수준 0 OLE DB 인터페이스만 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-235">Only level 0 OLE DB interfaces are invoked against the provider.</span></span>  
  
     <span data-ttu-id="166a9-236">**Inprocess 허용**</span><span class="sxs-lookup"><span data-stu-id="166a9-236">**Allow inprocess**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="166a9-237">에서 공급자가 in-process 서버로 인스턴스화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-237">allows the provider to be instantiated as an in-process server.</span></span> <span data-ttu-id="166a9-238">이 옵션을 설정하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 외부에서 공급자를 인스턴스화하는 것이 기본 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-238">When this option is not set, the default behavior is to instantiate the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process.</span></span> <span data-ttu-id="166a9-239">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 외부에서 공급자를 인스턴스화하면 공급자 오류로부터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스를 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-239">Instantiating the provider outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process protects the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process from errors in the provider.</span></span> <span data-ttu-id="166a9-240">공급자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 외부에서 인스턴스화되면 긴 열(`text`, `ntext` 또는 `image`)을 참조하는 업데이트나 삽입은 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-240">When the provider is instantiated outside the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] process, updates or inserts referencing long columns (`text`, `ntext`, or `image`) are not allowed.</span></span>  
  
     <span data-ttu-id="166a9-241">**트랜잭션되지 않은 업데이트**</span><span class="sxs-lookup"><span data-stu-id="166a9-241">**Non transacted updates**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="166a9-242">**ITransactionLocal** 를 사용할 수 없는 경우에도 업데이트를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-242">allows updates, even if **ITransactionLocal** is not available.</span></span> <span data-ttu-id="166a9-243">이 옵션을 사용하면 공급자가 트랜잭션을 지원하지 않으므로 공급자에 대한 업데이트를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-243">If this option is enabled, updates against the provider are not recoverable, because the provider does not support transactions.</span></span>  
  
     <span data-ttu-id="166a9-244">**액세스 경로인 인덱스**</span><span class="sxs-lookup"><span data-stu-id="166a9-244">**Index as access path**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="166a9-245">에서 공급자 인덱스를 사용하여 데이터를 인출하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-245">attempts to use indexes of the provider to fetch data.</span></span> <span data-ttu-id="166a9-246">기본적으로 인덱스는 메타데이터에만 사용되며 열리지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-246">By default, indexes are used only for metadata and are never opened</span></span>  
  
     <span data-ttu-id="166a9-247">**임시 액세스 허용 안 함**</span><span class="sxs-lookup"><span data-stu-id="166a9-247">**Disallow ad hoc access**</span></span>  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="166a9-248">에서 OLE DB 공급자에 대해 OPENROWSET 및 OPENDATASOURCE 함수를 통한 임시 액세스를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-248">does not allow ad hoc access through the OPENROWSET and OPENDATASOURCE functions against the OLE DB provider.</span></span> <span data-ttu-id="166a9-249">이 옵션을 설정하지 않은 경우에도 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 임시 액세스를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-249">When this option is not set, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also does not allow ad hoc access.</span></span>  
  
     <span data-ttu-id="166a9-250">**'LIKE' 연산자를 지원합니다.**</span><span class="sxs-lookup"><span data-stu-id="166a9-250">**Supports 'Like' operator**</span></span>  
     <span data-ttu-id="166a9-251">공급자가 LIKE 키워드를 사용하는 쿼리를 지원한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-251">Indicates that the provider supports queries using the LIKE key word.</span></span>  
  
###  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="166a9-252">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="166a9-252">Using Transact-SQL</span></span>  
 <span data-ttu-id="166a9-253">[!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 연결된 서버를 만들려면 [sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) 및 [sp_addlinkedsrvlogin&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-253">To create a linked server by using [!INCLUDE[tsql](../../includes/tsql-md.md)], use the [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) and [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql) statements.</span></span>  
  
##### <a name="to-create-a-linked-server-to-another-instance-of-sql-server-using-transact-sql"></a><span data-ttu-id="166a9-254">Transact-SQL을 사용하여 SQL Server의 다른 인스턴스에 연결된 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="166a9-254">To create a linked server to another instance of SQL Server using Transact-SQL</span></span>  
  
1.  <span data-ttu-id="166a9-255">쿼리 편집기에서 다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 명령을 입력하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 명명된 `SRVR002\ACCTG`인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-255">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] command to link to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named `SRVR002\ACCTG`:</span></span>  
  
    ```sql  
    USE [master]  
    GO  
    EXEC master.dbo.sp_addlinkedserver   
        @server = N'SRVR002\ACCTG',   
        @srvproduct=N'SQL Server' ;  
    GO  
  
    ```  
  
2.  <span data-ttu-id="166a9-256">다음 코드를 실행하여 연결된 서버에서 연결된 서버를 사용하는 로그인의 도메인 자격 증명을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-256">Execute the following code to configure the linked server to use the domain credentials of the login that is using the linked server.</span></span>  
  
    ```sql  
    EXEC master.dbo.sp_addlinkedsrvlogin   
        @rmtsrvname = N'SRVR002\ACCTG',   
        @locallogin = NULL ,   
        @useself = N'True' ;  
    GO  
  
    ```  
  
##  <a name="follow-up-steps-to-take-after-you-create-a-linked-server"></a><a name="FollowUp"></a> <span data-ttu-id="166a9-257">추가 작업: 연결된 서버를 만든 후 수행할 단계</span><span class="sxs-lookup"><span data-stu-id="166a9-257">Follow Up: Steps to take after you create a linked server</span></span>  
  
#### <a name="to-test-the-linked-server"></a><span data-ttu-id="166a9-258">연결된 서버 테스트</span><span class="sxs-lookup"><span data-stu-id="166a9-258">To test the linked server</span></span>  
  
-   <span data-ttu-id="166a9-259">다음 코드를 실행하여 연결된 서버에 대한 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-259">Execute the following code to test the connection to the linked server.</span></span> <span data-ttu-id="166a9-260">이 예에서는 연결된 서버의 데이터베이스 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-260">This example the returns the names of the databases on the linked server.</span></span>  
  
    ```sql  
    SELECT name FROM [SRVR002\ACCTG].master.sys.databases ;  
    GO  
  
    ```  
  
#### <a name="writing-a-query-that-joins-tables-from-a-linked-server"></a><span data-ttu-id="166a9-261">연결된 서버의 테이블을 조인하는 쿼리 작성</span><span class="sxs-lookup"><span data-stu-id="166a9-261">Writing a query that joins tables from a linked server</span></span>  
  
-   <span data-ttu-id="166a9-262">네 부분으로 이루어진 이름을 사용하여 연결된 서버의 개체를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-262">Use four-part names to refer to an object on a linked server.</span></span> <span data-ttu-id="166a9-263">다음 코드를 실행하면 로컬 서버의 모든 로그인 및 연결된 서버에서 이와 일치하는 로그인의 목록이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-263">Execute the following code to return a list of all logins on the local server and their matching logins on the linked server.</span></span>  
  
    ```sql  
    SELECT local.name AS LocalLogins, linked.name AS LinkedLogins  
    FROM master.sys.server_principals AS local  
    LEFT JOIN [SRVR002\ACCTG].master.sys.server_principals AS linked  
        ON local.name = linked.name ;  
    GO  
    ```  
  
     <span data-ttu-id="166a9-264">연결된 서버에 대해 NULL이 반환되면 로그인이 연결된 서버에 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-264">When NULL is returned for the linked server login it indicates that the login does not exist on the linked server.</span></span> <span data-ttu-id="166a9-265">이러한 로그인은 연결된 서버가 다른 보안 컨텍스트를 통과시키거나 연결된 서버가 익명 연결을 허용하도록 구성되어야 연결된 서버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="166a9-265">These logins will not be able to use the linked server unless the linked server is configured to pass a different security context or the linked server accepts anonymous connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166a9-266">참고 항목</span><span class="sxs-lookup"><span data-stu-id="166a9-266">See Also</span></span>  
 <span data-ttu-id="166a9-267">[연결된 서버&#40;데이터베이스 엔진&#41;](linked-servers-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="166a9-267">[Linked Servers &#40;Database Engine&#41;](linked-servers-database-engine.md) </span></span>  
 <span data-ttu-id="166a9-268">[sp_addlinkedserver&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="166a9-268">[sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) </span></span>  
 [<span data-ttu-id="166a9-269">sp_serveroption&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="166a9-269">sp_serveroption &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
