---
title: 마스터 서버에서 대상 서버 제거 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2b17703fa87f5c0d3e7146a1660ac1ca7c7c1d81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731367"
---
# <a name="defect-a-target-server-from-a-master-server"></a><span data-ttu-id="ae84b-102">마스터 서버에서 대상 서버 제거</span><span class="sxs-lookup"><span data-stu-id="ae84b-102">Defect a Target Server from a Master Server</span></span>
  <span data-ttu-id="ae84b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] 또는 SMO(SQL Server 관리 개체)를 사용하여 마스터 서버에서 대상 서버를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-103">This topic describes how to defect a target server from a master server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="ae84b-104">이 프로시저를 대상 서버에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-104">Run this procedure from the target server.</span></span>  
  
 <span data-ttu-id="ae84b-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ae84b-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ae84b-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ae84b-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ae84b-107">보안</span><span class="sxs-lookup"><span data-stu-id="ae84b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ae84b-108">**대상 서버를 제거하려면:**</span><span class="sxs-lookup"><span data-stu-id="ae84b-108">**To defect a target server, using:**</span></span>  
  
     [<span data-ttu-id="ae84b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ae84b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ae84b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ae84b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="ae84b-111">SMO</span><span class="sxs-lookup"><span data-stu-id="ae84b-111">SMO</span></span>](#PowerShellProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ae84b-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ae84b-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ae84b-113">보안</span><span class="sxs-lookup"><span data-stu-id="ae84b-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ae84b-114">권한</span><span class="sxs-lookup"><span data-stu-id="ae84b-114">Permissions</span></span>  
 <span data-ttu-id="ae84b-115">이 저장 프로시저를 실행하려면 사용자가 `sysadmin` 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-115">To execute this stored procedure, a user must be a member of the `sysadmin` fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ae84b-116">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ae84b-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="ae84b-117">마스터 서버에서 대상 서버를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="ae84b-117">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="ae84b-118">**개체 탐색기**에서 대상 서버로 구성된 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-118">In **Object Explorer**, expand a server that is configured as a target server.</span></span>  
  
2.  <span data-ttu-id="ae84b-119">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-119">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and then click **Defect**.</span></span>  
  
3.  <span data-ttu-id="ae84b-120">**예** 를 클릭하여 마스터 서버에서 이 대상 서버를 제거할 것을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-120">Click **Yes** to confirm that you want to defect this target server from a master server.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ae84b-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ae84b-121">Using Transact-SQL</span></span>  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a><span data-ttu-id="ae84b-122">마스터 서버에서 대상 서버를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="ae84b-122">To defect a target server from a master server</span></span>  
  
1.  <span data-ttu-id="ae84b-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-123">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ae84b-124">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-124">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ae84b-125">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-125">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```sql
sp_msx_defect ;  
```  
  
 <span data-ttu-id="ae84b-126">자세한 내용은 [sp_msx_defect &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae84b-126">For more information, see [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-objects-smo"></a><a name="PowerShellProcedure"></a><span data-ttu-id="ae84b-127">SQL Server 관리 개체 사용 (SMO)</span><span class="sxs-lookup"><span data-stu-id="ae84b-127">Using SQL Server Management Objects (SMO)</span></span>  
 <span data-ttu-id="ae84b-128">`MsxDefect Method`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ae84b-128">Use the `MsxDefect Method`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae84b-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae84b-129">See Also</span></span>  
 <span data-ttu-id="ae84b-130">[다중 서버 환경 만들기](create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="ae84b-130">[Create a Multiserver Environment](create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="ae84b-131">[기업 내 관리 자동화](automated-administration-across-an-enterprise.md) </span><span class="sxs-lookup"><span data-stu-id="ae84b-131">[Automated Administration Across an Enterprise](automated-administration-across-an-enterprise.md) </span></span>  
 [<span data-ttu-id="ae84b-132">마스터 서버에서 여러 대상 서버 제거</span><span class="sxs-lookup"><span data-stu-id="ae84b-132">Defect Multiple Target Servers from a Master Server</span></span>](defect-multiple-target-servers-from-a-master-server.md)  
