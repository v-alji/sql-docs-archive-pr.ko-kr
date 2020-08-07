---
title: 경고 비활성화 또는 다시 활성화 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], reactivating
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- alerts [SQL Server], disabling
- reactivating alerts
- removing alerts
ms.assetid: 4cb37dc6-1134-405d-8590-58b44dcf63b2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3eec4ea7288f4847c0e9b861d80f23eb9c9ddba8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734923"
---
# <a name="disable-or-reactivate-an-alert"></a><span data-ttu-id="61ee3-102">Disable or Reactivate an Alert</span><span class="sxs-lookup"><span data-stu-id="61ee3-102">Disable or Reactivate an Alert</span></span>
  <span data-ttu-id="61ee3-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 경고를 비활성화 하거나 다시 활성화 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="61ee3-103">This topic describes how to disable or reactivate a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="61ee3-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="61ee3-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="61ee3-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="61ee3-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="61ee3-106">보안</span><span class="sxs-lookup"><span data-stu-id="61ee3-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="61ee3-107">**다음을 사용하여 경고를 비활성화하거나 다시 활성화합니다.**</span><span class="sxs-lookup"><span data-stu-id="61ee3-107">**To disable or reactivate an alert, using:**</span></span>  
  
     [<span data-ttu-id="61ee3-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="61ee3-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="61ee3-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="61ee3-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="61ee3-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="61ee3-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="61ee3-111">보안</span><span class="sxs-lookup"><span data-stu-id="61ee3-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="61ee3-112">권한</span><span class="sxs-lookup"><span data-stu-id="61ee3-112">Permissions</span></span>  
 <span data-ttu-id="61ee3-113">기본적으로 **sysadmin** 고정 서버 역할의 멤버가 경고의 정보를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-113">By default, members of the **sysadmin** fixed server role can edit information in an alert.</span></span> <span data-ttu-id="61ee3-114">다른 사용자는 **msdb** 데이터베이스의 **SQLAgentOperatorRole** 고정 데이터베이스 역할을 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="61ee3-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="61ee3-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="61ee3-116">경고를 비활성화하거나 다시 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="61ee3-116">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="61ee3-117">**개체 탐색기**에서 더하기 기호를 클릭하여 비활성화하거나 다시 활성화하려는 경고가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-117">In **Object Explorer**, click the plus sign to expand server that contains the alert you wish to disable or reactivate.</span></span>  
  
2.  <span data-ttu-id="61ee3-118">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="61ee3-119">더하기 기호를 클릭하여 **경고** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="61ee3-120">활성화하려는 경고를 마우스 오른쪽 단추로 클릭하고 **사용** 을 선택합니다. 경고를 비활성화하려면 비활성화하려는 경고를 마우스 오른쪽 단추로 클릭하고 **사용 안 함**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-120">Right-click the alert you wish to enable and select **Enable** To disable an alert, right-click the alert you want to disable and select **Disable**.</span></span>  
  
5.  <span data-ttu-id="61ee3-121">프로세스의 상태를 나타내는 **경고 비활성화** 또는 **경고 활성화** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-121">The **Disable Alert** or **Enable Alert** dialog box displays showing the status of the process.</span></span> <span data-ttu-id="61ee3-122">완료되면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-122">When finished, click **Close**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="61ee3-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="61ee3-123">Using Transact-SQL</span></span>  
  
#### <a name="to-disable-or-reactivate-an-alert"></a><span data-ttu-id="61ee3-124">경고를 비활성화하거나 다시 활성화하려면</span><span class="sxs-lookup"><span data-stu-id="61ee3-124">To disable or reactivate an alert</span></span>  
  
1.  <span data-ttu-id="61ee3-125">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-125">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="61ee3-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-126">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="61ee3-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="61ee3-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- changes the enabled setting of Test Alert to 0  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_alert  
        @name = N'Test Alert',  
        @enabled = 0 ;  
    GO  
    ```  
  
 <span data-ttu-id="61ee3-128">자세한 내용은 [sp_update_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="61ee3-128">For more information, see [sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql).</span></span>  
  
  
