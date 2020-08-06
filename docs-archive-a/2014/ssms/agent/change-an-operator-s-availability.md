---
title: 운영자의 응답 가능 여부 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- reactivating operators
- removing operators
- deleting operators
- available operators [SQL Server]
- dropping operators
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
- disabling operators
- operators (users) [Database Engine], changing availability with Management Studio
ms.assetid: 10d58b92-b67b-47e2-af9c-9f9fd6968bba
author: stevestein
ms.author: sstein
ms.openlocfilehash: fb369ea6a2d1edf1ed8f4377b627fb1ba7339a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660855"
---
# <a name="change-an-operator39s-availability"></a><span data-ttu-id="031c7-102">운영자의 응답 가능 여부 변경</span><span class="sxs-lookup"><span data-stu-id="031c7-102">Change an Operator&#39;s Availability</span></span>
  <span data-ttu-id="031c7-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 운영자의 경고 알림 수신 일정을 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-103">This topic describes how to change an operator's schedule for receiving alert notifications in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="031c7-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="031c7-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="031c7-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="031c7-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="031c7-106">보안</span><span class="sxs-lookup"><span data-stu-id="031c7-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="031c7-107">**운영자의 응답 가능 여부를 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="031c7-107">**To change an operator's availability, using:**</span></span>  
  
     [<span data-ttu-id="031c7-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="031c7-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="031c7-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="031c7-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="031c7-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="031c7-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="031c7-111">보안</span><span class="sxs-lookup"><span data-stu-id="031c7-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="031c7-112">권한</span><span class="sxs-lookup"><span data-stu-id="031c7-112">Permissions</span></span>  
 <span data-ttu-id="031c7-113">**sysadmin** 고정 서버 역할의 멤버만이 운영자를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-113">Only members of the **sysadmin** fixed server role can edit operators.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="031c7-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="031c7-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="031c7-115">운영자의 응답 가능 여부를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="031c7-115">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="031c7-116">**개체 탐색기**에서 더하기 기호를 클릭하여 사용하거나 사용하지 않도록 설정할 운영자가 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-116">In **Object Explorer**, click the plus sign to expand server that contains the operator that you want to enable or disable.</span></span>  
  
2.  <span data-ttu-id="031c7-117">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-117">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="031c7-118">더하기 기호를 클릭하여 **운영자** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-118">Click the plus sign to expand the **Operators** folder.</span></span>  
  
4.  <span data-ttu-id="031c7-119">사용하거나 사용하지 않도록 설정할 운영자를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음 **일반** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-119">Right-click the operator that you want to enable or disable and select **Properties**, then click the **General** tab.</span></span>  
  
5.  <span data-ttu-id="031c7-120">_Operator_name_**속성** 대화 상자에서 **사용** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-120">In the _operator_name_**Properties** dialog box, select or clear the **Enabled** check box.</span></span>  
  
6.  <span data-ttu-id="031c7-121">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-121">Click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="031c7-122">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="031c7-122">Using Transact-SQL</span></span>  
  
#### <a name="to-change-an-operators-availability"></a><span data-ttu-id="031c7-123">운영자의 응답 가능 여부를 변경하려면</span><span class="sxs-lookup"><span data-stu-id="031c7-123">To change an operator's availability</span></span>  
  
1.  <span data-ttu-id="031c7-124">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-124">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="031c7-125">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-125">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="031c7-126">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="031c7-126">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- disables the 'Fran??ois Ajenstat' operator  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'Fran??ois Ajenstat',  
        @enabled = 0;  
    GO  
    ```  
  
 <span data-ttu-id="031c7-127">자세한 내용은 [sp_update_operator &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="031c7-127">For more information, see [sp_update_operator &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-operator-transact-sql).</span></span>  
  
  
