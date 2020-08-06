---
title: 경고 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- alerts [SQL Server], deleting
- deleting alerts
- canceling alerts
- dropping alerts
- disabling alerts
- removing alerts
ms.assetid: c982b208-e2d1-4d34-8cee-940b9baf6586
author: stevestein
ms.author: sstein
ms.openlocfilehash: 15fdae19b150a5a06a32e91ec1947a0acfa5f900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653105"
---
# <a name="delete-an-alert"></a><span data-ttu-id="1ec5e-102">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="1ec5e-102">Delete an Alert</span></span>
  <span data-ttu-id="1ec5e-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 경고를 삭제 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1ec5e-103">This topic describes how to delete [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="1ec5e-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="1ec5e-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="1ec5e-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="1ec5e-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1ec5e-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1ec5e-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1ec5e-107">보안</span><span class="sxs-lookup"><span data-stu-id="1ec5e-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1ec5e-108">**다음을 사용하여 경고를 삭제합니다.**</span><span class="sxs-lookup"><span data-stu-id="1ec5e-108">**To delete an alert, using:**</span></span>  
  
     [<span data-ttu-id="1ec5e-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1ec5e-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1ec5e-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1ec5e-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1ec5e-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="1ec5e-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1ec5e-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="1ec5e-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1ec5e-113">경고를 제거하면 해당 경고와 연관된 모든 알림도 함께 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-113">Removing an alert also removes any notifications associated with the alert.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1ec5e-114">보안</span><span class="sxs-lookup"><span data-stu-id="1ec5e-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1ec5e-115">권한</span><span class="sxs-lookup"><span data-stu-id="1ec5e-115">Permissions</span></span>  
 <span data-ttu-id="1ec5e-116">기본적으로 **sysadmin** 고정 서버 역할의 멤버만 경고를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-116">By default, only members of the **sysadmin** fixed server role can delete alerts.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1ec5e-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="1ec5e-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="1ec5e-118">경고를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1ec5e-118">To delete an alert</span></span>  
  
1.  <span data-ttu-id="1ec5e-119">**개체 탐색기** 에서 더하기 기호를 클릭하여 삭제하려는 SQL Server 에이전트 경고가 포함된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-119">In **Object Explorer,** click the plus sign to expand the server that contains the SQL Server Agent alert that you want to delete.</span></span>  
  
2.  <span data-ttu-id="1ec5e-120">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="1ec5e-121">더하기 기호를 클릭하여 **경고** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-121">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="1ec5e-122">삭제할 경고를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-122">Right-click the alert you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="1ec5e-123">**개체 삭제** 대화 상자에서 올바른 경고를 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-123">In the **Delete Object** dialog box, confirm that the correct alert is selected and click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1ec5e-124">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="1ec5e-124">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-alert"></a><span data-ttu-id="1ec5e-125">경고를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="1ec5e-125">To delete an alert</span></span>  
  
1.  <span data-ttu-id="1ec5e-126">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-126">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ec5e-127">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-127">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="1ec5e-128">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-128">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes the SQL Server Agent alert called 'Test Alert.'  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_delete_alert  
       @name = N'Test Alert' ;  
    GO  
    ```  
  
 <span data-ttu-id="1ec5e-129">자세한 내용은[sp_delete_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1ec5e-129">For more information, see s[sp_delete_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-alert-transact-sql).</span></span>  
  
  
