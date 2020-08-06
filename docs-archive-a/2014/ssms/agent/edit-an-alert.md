---
title: 경고 편집 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], modifying
- modifying alerts
ms.assetid: f518e528-cc8f-446a-b37d-98505b86e430
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1eae606b3c2ca4c18d088e650e774986d4e31387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651992"
---
# <a name="edit-an-alert"></a><span data-ttu-id="29349-102">Edit an Alert</span><span class="sxs-lookup"><span data-stu-id="29349-102">Edit an Alert</span></span>
  <span data-ttu-id="29349-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 경고를 편집 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="29349-103">This topic describes how to edit a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="29349-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="29349-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="29349-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="29349-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="29349-106">보안</span><span class="sxs-lookup"><span data-stu-id="29349-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="29349-107">**다음을 사용하여 경고를 편집합니다.**</span><span class="sxs-lookup"><span data-stu-id="29349-107">**To edit an alert, using:**</span></span>  
  
     [<span data-ttu-id="29349-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="29349-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="29349-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="29349-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="29349-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="29349-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="29349-111">보안</span><span class="sxs-lookup"><span data-stu-id="29349-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="29349-112">권한</span><span class="sxs-lookup"><span data-stu-id="29349-112">Permissions</span></span>  
 <span data-ttu-id="29349-113">기본적으로 **sysadmin** 고정 서버 역할의 멤버가 경고의 정보를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29349-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="29349-114">다른 사용자는 **msdb** 데이터베이스의 **SQLAgentOperatorRole** 고정 데이터베이스 역할을 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="29349-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="29349-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="29349-116">경고를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="29349-116">To edit an alert</span></span>  
  
1.  <span data-ttu-id="29349-117">**개체 탐색기** 에서 더하기 기호를 클릭하여 편집하려는 경고가 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-117">In **Object Explorer,** click the plus sign to expand the server containing the alert you want to edit.</span></span>  
  
2.  <span data-ttu-id="29349-118">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="29349-119">더하기 기호를 클릭하여 **경고** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="29349-120">편집할 경고를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-120">Right-click the alert you want to edit and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="29349-121">**일반**, **응답**및 **옵션** 페이지에서 경고 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-121">Update the alert properties on the **General**, **Response**, and **Options** pages.</span></span>  
  
6.  <span data-ttu-id="29349-122">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-122">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="29349-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="29349-123">Using Transact-SQL</span></span>  
  
#### <a name="to-edit-an-alert"></a><span data-ttu-id="29349-124">경고를 편집하려면</span><span class="sxs-lookup"><span data-stu-id="29349-124">To edit an alert</span></span>  
  
1.  <span data-ttu-id="29349-125">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="29349-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="29349-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="29349-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="29349-128">자세한 내용은 [sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="29349-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
