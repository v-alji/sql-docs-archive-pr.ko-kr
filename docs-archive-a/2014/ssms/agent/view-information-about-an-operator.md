---
title: 운영자에 대한 정보 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- viewing operators
- operators (users) [Database Engine], viewing with Management Studio
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- displaying operators
ms.assetid: 92c82cdf-f704-444e-9539-82aea7fe6fb7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 680b90401f800a9c435bdae33b8e55385541cc4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649314"
---
# <a name="view-information-about-an-operator"></a><span data-ttu-id="8bded-102">View Information About an Operator</span><span class="sxs-lookup"><span data-stu-id="8bded-102">View Information About an Operator</span></span>
  <span data-ttu-id="8bded-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 운영자에 대 한 정보를 보는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8bded-103">This topic describes how to view information about a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operator in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8bded-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8bded-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8bded-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8bded-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8bded-106">보안</span><span class="sxs-lookup"><span data-stu-id="8bded-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8bded-107">**다음을 사용하여 운영자에 대한 정보를 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="8bded-107">**To view information about an operator, using:**</span></span>  
  
     [<span data-ttu-id="8bded-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8bded-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8bded-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8bded-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8bded-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8bded-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8bded-111">보안</span><span class="sxs-lookup"><span data-stu-id="8bded-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8bded-112">권한</span><span class="sxs-lookup"><span data-stu-id="8bded-112">Permissions</span></span>  
 <span data-ttu-id="8bded-113">기본적으로 **sysadmin** 고정 서버 역할의 멤버는 이 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-113">By default, members of the **sysadmin** fixed server role can execute this stored procedure.</span></span> <span data-ttu-id="8bded-114">다른 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **데이터베이스의 다음** 에이전트 고정 데이터베이스 역할 중 하나를 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-114">Other users must be granted one of the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent fixed database roles in the **msdb** database:</span></span>  
  
-   <span data-ttu-id="8bded-115">**SQLAgentUserRole**</span><span class="sxs-lookup"><span data-stu-id="8bded-115">**SQLAgentUserRole**</span></span>  
  
-   <span data-ttu-id="8bded-116">**SQLAgentReaderRole**</span><span class="sxs-lookup"><span data-stu-id="8bded-116">**SQLAgentReaderRole**</span></span>  
  
-   <span data-ttu-id="8bded-117">**SQLAgentOperatorRole**</span><span class="sxs-lookup"><span data-stu-id="8bded-117">**SQLAgentOperatorRole**</span></span>  
  
 <span data-ttu-id="8bded-118">이러한 역할의 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 고정 데이터베이스 역할](sql-server-agent-fixed-database-roles.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8bded-118">For details about the permissions of these roles, see [SQL Server Agent Fixed Database Roles](sql-server-agent-fixed-database-roles.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8bded-119">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8bded-119">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="8bded-120">운영자에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="8bded-120">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="8bded-121">**개체 탐색기**에서 더하기 기호를 클릭하여 보려는 운영자가 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-121">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to view.</span></span>  
  
2.  <span data-ttu-id="8bded-122">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-122">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="8bded-123">더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-123">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="8bded-124">보려는 운영자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-124">Right-click the operator that you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="8bded-125">_Operator_name_**속성** 대화 상자에 포함 된 사용 가능한 옵션에 대 한 자세한 내용은 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8bded-125">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="8bded-126">운영자 속성 및 새 운영자 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8bded-126">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="8bded-127">운영자 속성: 새 운영자 &#40;알림 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8bded-127">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="8bded-128">운영자 속성&#40;기록 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="8bded-128">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="8bded-129">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8bded-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8bded-130">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-operator"></a><span data-ttu-id="8bded-131">운영자에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="8bded-131">To view information about an operator</span></span>  
  
1.  <span data-ttu-id="8bded-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="8bded-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="8bded-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8bded-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about operator Fran??ois Ajenstat   
    -- This example assumes that the operator exists.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_operator  
        @operator_name = N'Fran??ois Ajenstat' ;  
    GO  
    ```  
  
 <span data-ttu-id="8bded-135">자세한 내용은 [sp_help_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8bded-135">For more information, see [sp_help_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-operator-transact-sql).</span></span>  
  
  
