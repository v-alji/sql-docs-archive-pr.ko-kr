---
title: 보안 주체에게 사용 권한 부여 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Grant permission to a principal
ms.assetid: 4107389d-05b6-4aa3-9fa8-95b40cdf05dc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4256d62bdeac2d79c51e5f3792c991e0e3b15096
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741735"
---
# <a name="grant-a-permission-to-a-principal"></a><span data-ttu-id="a24bf-102">보안 주체에게 사용 권한 부여</span><span class="sxs-lookup"><span data-stu-id="a24bf-102">Grant a Permission to a Principal</span></span>
  <span data-ttu-id="a24bf-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 보안 주체에 권한을 부여하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-103">This topic describes how to grant permission to a principal in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="a24bf-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="a24bf-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a24bf-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="a24bf-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a24bf-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a24bf-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a24bf-107">보안</span><span class="sxs-lookup"><span data-stu-id="a24bf-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a24bf-108">**다음을 사용하여 보안 주체에 대한 사용 권한을 부여합니다.**</span><span class="sxs-lookup"><span data-stu-id="a24bf-108">**To grant permission to a principal, using:**</span></span>  
  
     [<span data-ttu-id="a24bf-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a24bf-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a24bf-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a24bf-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a24bf-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="a24bf-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a24bf-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="a24bf-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="a24bf-113">사용 권한을 보다 쉽게 관리할 수 있도록 다음과 같은 최선의 구현 방법을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="a24bf-113">Consider the following best practices that can make managing permissions easier.</span></span>  
  
-   <span data-ttu-id="a24bf-114">개별 로그인 또는 사용자 대신 역할에 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-114">Grant permission to roles, instead of individual logins or users.</span></span> <span data-ttu-id="a24bf-115">사용자가 바뀌는 경우 떠나는 사용자를 역할에서 제거하고 새 사용자를 역할에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-115">When one individual is replaced by another, remove the departing individual from the role and add the new individual to the role.</span></span> <span data-ttu-id="a24bf-116">새로운 사용자는 해당 역할에 연결된 많은 사용 권한을 자동으로 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-116">The many permissions that might be associated with the role will automatically be available to the new individual.</span></span> <span data-ttu-id="a24bf-117">조직 내 여러 사람에게 동일한 사용 권한이 필요한 경우 각 사람을 역할에 추가함으로써 동일한 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-117">If several people in an organization require the same permissions, adding each of them to the role will grant them the same permissions.</span></span>  
  
-   <span data-ttu-id="a24bf-118">유사한 보안 개체(테이블, 뷰 및 프로시저)를 스키마가 소유하도록 구성한 후 해당 스키마에 대한 사용 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-118">Configure similar securables (tables, views, and procedures) to be owned by a schema, then grant permissions to the schema.</span></span> <span data-ttu-id="a24bf-119">예를 들어 급여 스키마는 여러 테이블, 뷰 및 저장 프로시저를 소유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-119">For example, the payroll schema might own several tables, views, and stored procedures.</span></span> <span data-ttu-id="a24bf-120">스키마에 액세스 권한을 부여하면 급여 기능을 수행하는 데 필요한 모든 사용 권한을 동시에 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-120">By granting access to the schema, all the necessary permissions to perform the payroll function can be granted at the same time.</span></span> <span data-ttu-id="a24bf-121">사용 권한을 부여받을 수 있는 보안 개체에 대한 자세한 내용은 [Securables](../securables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24bf-121">For more information about what securables can be granted permissions, see [Securables](../securables.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a24bf-122">보안</span><span class="sxs-lookup"><span data-stu-id="a24bf-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a24bf-123">권한</span><span class="sxs-lookup"><span data-stu-id="a24bf-123">Permissions</span></span>  
 <span data-ttu-id="a24bf-124">사용 권한을 부여한 사용자 또는 AS 옵션으로 지정한 보안 주체에게 GRANT OPTION을 통한 사용 권한이 있거나 부여할 사용 권한을 포함하는 상위 사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-124">The grantor (or the principal specified with the AS option) must have either the permission itself with GRANT OPTION or a higher permission that implies the permission being granted.</span></span> <span data-ttu-id="a24bf-125">**sysadmin** 고정 서버 역할의 멤버는 모든 사용 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-125">Members of the **sysadmin** fixed server role can grant any permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a24bf-126">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="a24bf-126">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="a24bf-127">보안 주체에 사용 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="a24bf-127">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="a24bf-128">개체 탐색기에서 사용 권한을 부여하려는 개체가 포함된 데이터베이스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-128">In Object Explorer, expand the database that contains the object to which you want to grant permissions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a24bf-129">이러한 단계는 특히 저장 프로시저에 대한 권한 부여를 처리하지만 비슷한 단계에서도 다른 보안 개체뿐만 아니라 테이블, 뷰, 함수 및 어셈블리에 사용 권한을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-129">These steps deal specifically with granting permissions to a stored procedure, but you can use similar steps to add permissions to tables, views, functions, and assemblies, as well as other securables.</span></span> <span data-ttu-id="a24bf-130">자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24bf-130">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)</span></span>  
  
2.  <span data-ttu-id="a24bf-131">**프로그래밍 기능** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-131">Expand the **Programmability** folder.</span></span>  
  
3.  <span data-ttu-id="a24bf-132">**저장 프로시저** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-132">Expand the **Stored Procedures** folder.</span></span>  
  
4.  <span data-ttu-id="a24bf-133">저장 프로시저를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-133">Right-click a stored procedure and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="a24bf-134">**저장 프로시저 속성-**_stored_procedure_name_ 대화 상자의 페이지 선택 아래에서 **사용 권한**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-134">In the **Stored Procedure Properties -**_stored_procedure_name_ dialog box, under select a page, select **Permissions**.</span></span> <span data-ttu-id="a24bf-135">이 페이지에서는 저장 프로시저에 사용자 또는 역할을 추가하고 해당 사용자 또는 역할이 포함할 사용 권한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-135">Use this page to add users or roles to the stored procedure and specify the permissions those users or roles have.</span></span>  
  
6.  <span data-ttu-id="a24bf-136">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-136">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a24bf-137">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="a24bf-137">Using Transact-SQL</span></span>  
  
#### <a name="to-grant-permission-to-a-principal"></a><span data-ttu-id="a24bf-138">보안 주체에 사용 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="a24bf-138">To grant permission to a principal</span></span>  
  
1.  <span data-ttu-id="a24bf-139">**개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-139">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a24bf-140">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-140">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a24bf-141">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a24bf-141">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- Grants EXECUTE permission on stored procedure HumanResources.uspUpdateEmployeeHireInfo to an application role called Recruiting11.   
    USE AdventureWorks2012;  
    GO  
    GRANT EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
        TO Recruiting11;  
    GO  
    ```  
  
 <span data-ttu-id="a24bf-142">자세한 내용은 [GRANT&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) 및 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a24bf-142">For more information, see [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) and [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24bf-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a24bf-143">See Also</span></span>  
 [<span data-ttu-id="a24bf-144">보안 주체&#40;데이터베이스 엔진&#41;</span><span class="sxs-lookup"><span data-stu-id="a24bf-144">Principals &#40;Database Engine&#41;</span></span>](principals-database-engine.md)  
  
  
