---
title: 운영자 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 75bea1c5c5fabff7ce55fe07a5181baa8f99e0fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646810"
---
# <a name="delete-an-operator"></a><span data-ttu-id="b46f6-102">Delete an Operator</span><span class="sxs-lookup"><span data-stu-id="b46f6-102">Delete an Operator</span></span>
  <span data-ttu-id="b46f6-103">이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는을 사용 하 여에서 에이전트 경고 알림을 더 이상 수신 하지 않도록 운영자를 제거 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b46f6-103">This topic describes how to remove an operator so they no longer receive [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b46f6-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b46f6-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b46f6-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b46f6-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b46f6-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b46f6-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="b46f6-107">보안</span><span class="sxs-lookup"><span data-stu-id="b46f6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b46f6-108">**운영자를 삭제하려면:**</span><span class="sxs-lookup"><span data-stu-id="b46f6-108">**To delete an operator, using:**</span></span>  
  
     [<span data-ttu-id="b46f6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b46f6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b46f6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b46f6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b46f6-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b46f6-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="b46f6-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="b46f6-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="b46f6-113">운영자가 제거되면 그 운영자와 연관된 알림도 모두 함께 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-113">When an operator is removed, all the notifications associated with the operator are also removed.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b46f6-114">보안</span><span class="sxs-lookup"><span data-stu-id="b46f6-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b46f6-115">권한</span><span class="sxs-lookup"><span data-stu-id="b46f6-115">Permissions</span></span>  
 <span data-ttu-id="b46f6-116">**sysadmin** 고정 서버 역할의 멤버는 운영자를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-116">Members of the **sysadmin** fixed server role can delete operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b46f6-117">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b46f6-117">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="b46f6-118">운영자를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b46f6-118">To delete an operator</span></span>  
  
1.  <span data-ttu-id="b46f6-119">**개체 탐색기**에서 더하기 기호를 클릭하여 삭제할 운영자가 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-119">In **Object Explorer**, click the plus sign to expand the server that contains the operator you want to delete.</span></span>  
  
2.  <span data-ttu-id="b46f6-120">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-120">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b46f6-121">더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-121">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="b46f6-122">삭제할 운영자를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-122">Right-click the operator that you want to delete and select **Delete**.</span></span>  
  
5.  <span data-ttu-id="b46f6-123">**개체 삭제** 대화 상자에서 올바른 운영자를 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-123">In the **Delete Object** dialog box, make sure that the correct operator is selected, and then click **OK**.</span></span> <span data-ttu-id="b46f6-124">삭제한 운영자에게 전송된 경고와 작업을 다른 운영자가 받도록 하려면 **재할당 대상** 을 선택하고 목록에서 운영자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-124">If you want another operator to receive the alerts and jobs sent to the deleted operator, check **Reassign to** and select an operator in the list.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b46f6-125">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b46f6-125">Using Transact-SQL</span></span>  
  
#### <a name="to-delete-an-operator"></a><span data-ttu-id="b46f6-126">운영자를 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="b46f6-126">To delete an operator</span></span>  
  
1.  <span data-ttu-id="b46f6-127">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-127">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b46f6-128">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-128">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b46f6-129">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b46f6-129">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs sent to that operator to 'Fran??ois Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'Fran??ois Ajenstat';  
    GO  
    ```  
  
 <span data-ttu-id="b46f6-130">자세한 내용은 [sp_delete_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b46f6-130">For more information, see [sp_delete_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-operator-transact-sql).</span></span>  
  
  
