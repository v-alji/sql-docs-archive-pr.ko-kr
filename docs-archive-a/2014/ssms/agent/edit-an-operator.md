---
title: 운영자 편집 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45ffb520e240dfd97002060370ff6dcf7c60d083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639229"
---
# <a name="edit-an-operator"></a><span data-ttu-id="1ea02-102">운영자 편집</span><span class="sxs-lookup"><span data-stu-id="1ea02-102">Edit an Operator</span></span>
  <span data-ttu-id="1ea02-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 알림 메시지 수신을 위한 운영자의 응답 가능 여부와 전자 메일, 호출기 및 Net Send 주소를 편집하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-103">This topic describes how to edit an operators' availability for receiving notifications and their e-mail, pager, and net send addresses in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1ea02-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1ea02-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1ea02-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1ea02-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1ea02-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1ea02-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1ea02-107">보안</span><span class="sxs-lookup"><span data-stu-id="1ea02-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1ea02-108">**다음을 사용하여 운영자를 편집합니다.**</span><span class="sxs-lookup"><span data-stu-id="1ea02-108">**To edit an operator, using:**</span></span>  
  
     [<span data-ttu-id="1ea02-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1ea02-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1ea02-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ea02-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ea02-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1ea02-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1ea02-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1ea02-112">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="1ea02-113">**이후 버전에서는** 에이전트에서 호출기 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net send [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]옵션이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-113">The Pager and **net send** options will be removed from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in a future version of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ea02-114">새 개발 작업에서는 이 기능을 사용하지 말고, 현재 이 기능을 사용하는 애플리케이션은 수정하세요.</span><span class="sxs-lookup"><span data-stu-id="1ea02-114">Avoid using these features in new development work, and plan to modify applications that currently use these features.</span></span>  
  
-   <span data-ttu-id="1ea02-115">SQL Server 에이전트는 데이터베이스 메일을 사용하여 운영자에게 전자 메일 및 호출기 알림을 보내도록 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-115">Note that SQL Server Agent must be configured to use Database Mail to send e-mail and pager notifications to operators.</span></span> <span data-ttu-id="1ea02-116">자세한 내용은 [경고를 운영자에게 할당](assign-alerts-to-an-operator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ea02-116">For more information, see [Assign Alerts to an Operator](assign-alerts-to-an-operator.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="1ea02-117">는 작업 구조를 만들고 관리할 수 있는 바람직한 방법을 제공하는데 이는 그래픽을 사용하여 쉽게 작업을 관리할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-117">provides an easy, graphical way to manage jobs, and is the recommended way to create and manage the job infrastructure.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ea02-118">보안</span><span class="sxs-lookup"><span data-stu-id="1ea02-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ea02-119">권한</span><span class="sxs-lookup"><span data-stu-id="1ea02-119">Permissions</span></span>  
 <span data-ttu-id="1ea02-120">**sysadmin** 고정 서버 역할의 멤버만이 운영자를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-120">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1ea02-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1ea02-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="1ea02-122">운영자를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="1ea02-122">To edit an operator</span></span>  
  
1.  <span data-ttu-id="1ea02-123">**개체 탐색기**에서 더하기 기호를 클릭하여 편집하려는 운영자가 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-123">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to edit.</span></span>  
  
2.  <span data-ttu-id="1ea02-124">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-124">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1ea02-125">더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-125">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="1ea02-126">편집하려는 운영자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-126">Right-click the operator that you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="1ea02-127">_Operator_name_**속성** 대화 상자에 포함 된 사용 가능한 옵션에 대 한 자세한 내용은 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ea02-127">For more information on the available options contained in the _operator_name_**Properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="1ea02-128">운영자 속성 및 새 운영자 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea02-128">Operator Properties and New Operator &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="1ea02-129">운영자 속성: 새 운영자 &#40;알림 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea02-129">Operator Properties: New Operator &#40;Notifications Page&#41;</span></span>](operator-properties-new-operator-notifications-page.md)  
  
    -   [<span data-ttu-id="1ea02-130">운영자 속성&#40;기록 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea02-130">Operator Properties &#40;History Page&#41;</span></span>](operator-properties-history-page.md)  
  
5.  <span data-ttu-id="1ea02-131">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-131">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1ea02-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1ea02-132">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-operator"></a><span data-ttu-id="1ea02-133">운영자를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="1ea02-133">To edit an operator</span></span>  
  
1.  <span data-ttu-id="1ea02-134">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-134">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ea02-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-135">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1ea02-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ea02-136">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.) when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 1,  
        @email_address = N'fran??oisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
 <span data-ttu-id="1ea02-137">자세한 내용은 [sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1ea02-137">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
