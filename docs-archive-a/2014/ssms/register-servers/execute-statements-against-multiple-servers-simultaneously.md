---
title: 여러 서버에 대해 동시에 문 실행
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b94775029a1501d3e894d84ef4a027fc1595dc10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733436"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a><span data-ttu-id="570cc-102">여러 서버에 대해 동시에 문 실행(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="570cc-102">Execute Statements Against Multiple Servers Simultaneously (SQL Server Management Studio)</span></span>
  <span data-ttu-id="570cc-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 로컬 서버 그룹 또는 중앙 관리 서버와 하나 이상의 서버 그룹 및 그룹 내의 하나 이상의 등록된 서버를 만든 다음 전체 그룹을 쿼리하여 여러 서버를 동시에 쿼리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-103">This topic describes how to query multiple servers at the same time in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], by creating a local server group, or a Central Management Server and one or more server groups, and one or more registered servers within the groups, and then querying the complete group.</span></span> <span data-ttu-id="570cc-104">쿼리에서 반환되는 결과는 단일 결과 창으로 결합되거나 별도의 결과 창에 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-104">The results that are returned by the query can be combined into a single results pane, or can be returned in separate results panes.</span></span> <span data-ttu-id="570cc-105">결과 집합에는 각 서버에 대한 쿼리에서 사용하는 서버 이름 및 로그인에 대한 추가 열이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-105">The results set can include additional columns for the server name and the login that is used by the query on each server.</span></span> <span data-ttu-id="570cc-106">중앙 관리 서버와 하위 서버는 Windows 인증을 사용해서만 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-106">Central Management Servers and subordinate servers can be registered by using only Windows Authentication.</span></span> <span data-ttu-id="570cc-107">Windows 인증 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하여 로컬 서버 그룹의 서버를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-107">Servers in local server groups can be registered by using Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="570cc-108">다음 절차를 실행하기 전에 중앙 관리 서버 및 서버 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-108">Before you execute the following procedures, create a Central Management Server and server groups.</span></span> <span data-ttu-id="570cc-109">자세한 내용은 [중앙 관리 서버 및 서버 그룹 만들기&#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="570cc-109">For more information, see [Create a Central Management Server and Server Group &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).</span></span>  
  
 <span data-ttu-id="570cc-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="570cc-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="570cc-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="570cc-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="570cc-112">보안</span><span class="sxs-lookup"><span data-stu-id="570cc-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="570cc-113">**여러 서버에 대해 문을 실행하려면:**</span><span class="sxs-lookup"><span data-stu-id="570cc-113">**To execute statements against multiple servers, using:**</span></span>  
  
     [<span data-ttu-id="570cc-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="570cc-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="570cc-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="570cc-115">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="570cc-116">보안</span><span class="sxs-lookup"><span data-stu-id="570cc-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="570cc-117">권한</span><span class="sxs-lookup"><span data-stu-id="570cc-117">Permissions</span></span>  
 <span data-ttu-id="570cc-118">중앙 관리 서버에서 유지 관리하는 연결은 Windows 인증을 사용하여 사용자 컨텍스트에서 실행되기 때문에 등록된 서버에 대한 유효 사용 권한이 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-118">Because the connections maintained by a Central Management Server execute in the context of the user, by using Windows Authentication, the effective permissions on the registered servers might vary.</span></span> <span data-ttu-id="570cc-119">예를 들어 사용자가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A 인스턴스에서는 sysadmin 고정 서버 역할의 멤버이지만 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B 인스턴스에서는 제한된 사용 권한을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-119">For example, the user might be a member of the sysadmin fixed server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, but have limited permissions on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="570cc-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="570cc-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a><span data-ttu-id="570cc-121">여러 구성 대상에 대해 동시에 문을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="570cc-121">To execute statements against multiple configuration targets simultaneously</span></span>  
  
1.  <span data-ttu-id="570cc-122">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **등록된 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-122">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Registered Servers**.</span></span>  
  
2.  <span data-ttu-id="570cc-123">중앙 관리 서버를 확장하고 서버 그룹을 마우스 오른쪽 단추로 클릭하고 **연결**을 가리킨 다음 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-123">Expand a Central Management Server, right-click a server group, point to **Connect**, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="570cc-124">쿼리 편집기에서 다음과 같은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 입력하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-124">In Query Editor, type and execute a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, such as the following:</span></span>  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     <span data-ttu-id="570cc-125">기본적으로 결과 창이 서버 그룹에 있는 모든 서버의 쿼리 결과를 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-125">By default, the results pane will combine the query results from all the servers in the server group.</span></span>  
  
#### <a name="to-change-the-multiserver-results-options"></a><span data-ttu-id="570cc-126">다중 서버 결과 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="570cc-126">To change the multiserver results options</span></span>  
  
1.  <span data-ttu-id="570cc-127">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 **도구** 메뉴에서 **옵션**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-127">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="570cc-128">**쿼리 결과**를 확장하고 **SQL Server**를 확장한 다음 **다중 서버 결과**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-128">Expand **Query Results**, expand **SQL Server**, and then click **Multiserver Results**.</span></span>  
  
3.  <span data-ttu-id="570cc-129">**다중 서버 결과** 페이지에서 원하는 옵션 설정을 지정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="570cc-129">On the **Multiserver Results** page, specify the option settings that you want, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570cc-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="570cc-130">See Also</span></span>  
 [<span data-ttu-id="570cc-131">중앙 관리 서버를 사용 하 여 여러 서버 관리</span><span class="sxs-lookup"><span data-stu-id="570cc-131">Administer Multiple Servers Using Central Management Servers</span></span>](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
