---
title: 유틸리티 제어 지점 제거(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fe4ebb9de3f7644b4cff5c7dbfb34e50be7e8993
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661098"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a><span data-ttu-id="bc313-102">유틸리티 제어 지점 제거(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="bc313-102">Remove a Utility Control Point (SQL Server Utility)</span></span>
  <span data-ttu-id="bc313-103">이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 인스턴스로부터 [!INCLUDE[tsql](../../includes/tsql-md.md)]UCP(유틸리티 제어 지점)를 제거하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-103">This topic describes how to remove a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utility control point (UCP) from the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="bc313-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bc313-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bc313-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bc313-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bc313-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bc313-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="bc313-107">보안</span><span class="sxs-lookup"><span data-stu-id="bc313-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bc313-108">**다음을 사용하여 유틸리티 제어 지점을 제거합니다.**</span><span class="sxs-lookup"><span data-stu-id="bc313-108">**To remove a Utility Control Point, using:**</span></span>  
  
     [<span data-ttu-id="bc313-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bc313-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bc313-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bc313-110">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="bc313-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="bc313-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="bc313-112">이 절차를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유틸리티에서 UCP를 제거하기 전에 다음 요구 사항을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="bc313-112">Before you use this procedure to remove the UCP from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, note the following requirements.</span></span> <span data-ttu-id="bc313-113">저장 프로시저는 작업의 일부로 필수 구성 요소 검사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-113">The stored procedure will run prerequisite checks as part of the operation.</span></span>  
  
-   <span data-ttu-id="bc313-114">이 절차를 실행하기 전에 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스를 UCP에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-114">Before you run this procedure, all managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed from the UCP.</span></span> <span data-ttu-id="bc313-115">즉, UCP가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 관리되는 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-115">Note that the UCP is a managed instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bc313-116">자세한 내용은 [SQL Server 유틸리티에서 SQL Server 인스턴스 제거](remove-an-instance-of-sql-server-from-the-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc313-116">From more information, see [Remove an Instance of SQL Server from the SQL Server Utility](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).</span></span>  
  
-   <span data-ttu-id="bc313-117">UCP에 해당하는 컴퓨터에서 이 절차를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-117">This procedure must be run on a computer that is a UCP.</span></span>  
  
-   <span data-ttu-id="bc313-118">UCP가 제거된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 유틸리티 이외의 데이터 컬렉션 집합이 있는 경우 UMDW 데이터베이스(sysutility_mdw)는 이 절차로 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-118">If the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where the UCP was removed has a non-Utility data collection set, the UMDW database (sysutility_mdw) will not be dropped by the procedure.</span></span> <span data-ttu-id="bc313-119">이런 경우 UCP를 다시 만들기 전에 UMDW 데이터베이스(sysutility_mdw)를 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-119">If this is the case, the UMDW database (sysutility_mdw) must be dropped manually before the UCP can be created again.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bc313-120">보안</span><span class="sxs-lookup"><span data-stu-id="bc313-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bc313-121">권한</span><span class="sxs-lookup"><span data-stu-id="bc313-121">Permissions</span></span>  
 <span data-ttu-id="bc313-122">UCP를 만들 때 필요한 권한인 `sysadmin` 권한의 사용자가 이 절차를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-122">This procedure must be run by a user with `sysadmin` permissions; the same permissions required to create a UCP.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bc313-123">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bc313-123">Using Transact-SQL</span></span>  
  
#### <a name="to-remove-a-utility-control-point"></a><span data-ttu-id="bc313-124">유틸리티 제어 지점을 제거하려면</span><span class="sxs-lookup"><span data-stu-id="bc313-124">To remove a Utility Control Point</span></span>  
  
1.  <span data-ttu-id="bc313-125">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="bc313-126">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="bc313-127">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bc313-127">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc313-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc313-128">See Also</span></span>  
 <span data-ttu-id="bc313-129">[SQL Server 유틸리티 기능 및 태스크](sql-server-utility-features-and-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="bc313-129">[SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md) </span></span>  
 <span data-ttu-id="bc313-130">[유틸리티 탐색기를 사용하여 SQL Server 유틸리티 관리](use-utility-explorer-to-manage-the-sql-server-utility.md) </span><span class="sxs-lookup"><span data-stu-id="bc313-130">[Use Utility Explorer to Manage the SQL Server Utility](use-utility-explorer-to-manage-the-sql-server-utility.md) </span></span>  
 [<span data-ttu-id="bc313-131">SQL Server 유틸리티 문제 해결</span><span class="sxs-lookup"><span data-stu-id="bc313-131">Troubleshoot the SQL Server Utility</span></span>](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
