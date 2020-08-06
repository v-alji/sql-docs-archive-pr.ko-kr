---
title: 작업 범주 정보 나열 | Microsoft 문서
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 924e2b064980b2ea7068230610414262995da1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735848"
---
# <a name="list-job-category-information"></a><span data-ttu-id="7ec8f-102">작업 범주 정보 나열</span><span class="sxs-lookup"><span data-stu-id="7ec8f-102">List Job Category Information</span></span>
  <span data-ttu-id="7ec8f-103">또는 SQL Server 관리 개체를 사용 하 여에서 작업 범주 정보를 나열 하는 방법 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] 입니다.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-103">How to list job category information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  

  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="7ec8f-104">보안</span><span class="sxs-lookup"><span data-stu-id="7ec8f-104">Security</span></span>  
 <span data-ttu-id="7ec8f-105">자세한 내용은 [SQL Server 에이전트 보안 구현](implement-sql-server-agent-security.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-105">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="7ec8f-106">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="7ec8f-106">Using Transact-SQL</span></span>  
  
#### <a name="to-list-job-category-information"></a><span data-ttu-id="7ec8f-107">작업 범주 정보를 나열하려면</span><span class="sxs-lookup"><span data-stu-id="7ec8f-107">To list job category information</span></span>  
  
1.  <span data-ttu-id="7ec8f-108">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-108">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="7ec8f-109">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-109">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="7ec8f-110">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-110">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 <span data-ttu-id="7ec8f-111">자세한 내용은 [sp_help_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-111">For more information, see [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).</span></span>  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="7ec8f-112">SQL Server 관리 개체 사용</span><span class="sxs-lookup"><span data-stu-id="7ec8f-112">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="7ec8f-113">**작업 범주 정보를 나열하려면**</span><span class="sxs-lookup"><span data-stu-id="7ec8f-113">**To list job category information**</span></span>  
  
 <span data-ttu-id="7ec8f-114">Visual Basic, Visual C#, PowerShell 등 선택한 프로그래밍 언어를 사용하여 `JobCategory` 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-114">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell..</span></span> <span data-ttu-id="7ec8f-115">자세한 내용은 [SQL Server 관리 개체 &#40;SMO&#41; 프로그래밍 가이드](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ec8f-115">For more information, see [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).</span></span>  
