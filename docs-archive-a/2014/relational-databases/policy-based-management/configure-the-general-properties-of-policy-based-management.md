---
title: 정책 기반 관리의 일반 속성 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.PolicyManagement.f1
helpviewer_keywords:
- Policy-Based Management, configure properties
ms.assetid: 6d1e0e37-29ea-408a-a055-384984d884be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a2efb37fafa29bcb043dedbcfa8719d0092b1c77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731523"
---
# <a name="configure-the-general-properties-of-policy-based-management"></a><span data-ttu-id="72167-102">정책 기반 관리의 일반 속성 구성</span><span class="sxs-lookup"><span data-stu-id="72167-102">Configure the General Properties of Policy-Based Management</span></span>
  <span data-ttu-id="72167-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 정책 기반 관리에 대한 속성을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-103">This topic describes how to configure the properties for Policy-Based Management in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="72167-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="72167-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="72167-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="72167-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="72167-106">보안</span><span class="sxs-lookup"><span data-stu-id="72167-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="72167-107">**다음을 사용하여 정책 기반 관리를 구성하려면**</span><span class="sxs-lookup"><span data-stu-id="72167-107">**To configure Policy-Based Management, using:**</span></span>  
  
     [<span data-ttu-id="72167-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="72167-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="72167-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="72167-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="72167-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="72167-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="72167-111">보안</span><span class="sxs-lookup"><span data-stu-id="72167-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="72167-112">권한</span><span class="sxs-lookup"><span data-stu-id="72167-112">Permissions</span></span>  
 <span data-ttu-id="72167-113">PolicyAdministratorRole 고정 데이터베이스 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-113">Requires membership in the PolicyAdministratorRole fixed database role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="72167-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="72167-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="72167-115">정책 기반 관리를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="72167-115">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="72167-116">**개체 탐색기**에서 더하기 기호를 클릭하여 정책 기반 관리 속성을 구성하려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-116">In **Object Explorer**, click the plus sign to expand the server where you want to configure Policy-Based Management properties.</span></span>  
  
2.  <span data-ttu-id="72167-117">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-117">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="72167-118">**정책 관리자** 를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-118">Right-click **Policy Management** and select **Properties**.</span></span>  
  
     <span data-ttu-id="72167-119">다음 옵션은 **정책 관리 속성** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72167-119">The following options are available in **Policy Management Properties** dialog box.</span></span>  
  
     <span data-ttu-id="72167-120">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="72167-120">**Enabled**</span></span>  
     <span data-ttu-id="72167-121">정책 기반 관리 사용 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-121">Specifies whether Policy-Based Management is enabled.</span></span>  
  
     <span data-ttu-id="72167-122">**HistoryRetentionInDays**</span><span class="sxs-lookup"><span data-stu-id="72167-122">**HistoryRetentionInDays**</span></span>  
     <span data-ttu-id="72167-123">정책 평가 기록을 보관할 일 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-123">Specifies the number of days that policy evaluation history should be retained.</span></span> <span data-ttu-id="72167-124">이 값이 0(기본값)이면 기록이 자동으로 제거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="72167-124">If this value is 0 (the default), the history will not be automatically removed.</span></span>  
  
     <span data-ttu-id="72167-125">**LogOnSuccess**</span><span class="sxs-lookup"><span data-stu-id="72167-125">**LogOnSuccess**</span></span>  
     <span data-ttu-id="72167-126">정책 기반 관리에서 성공한 정책 평가를 기록할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-126">Specifies whether Policy-Based Management logs successful policy evaluations.</span></span>  
  
    -   <span data-ttu-id="72167-127">이 값이 false(기본값)이면 실패한 정책 평가만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="72167-127">When this value is false (the default), only failed policy evaluations are logged.</span></span>  
  
    -   <span data-ttu-id="72167-128">이 값이 true이면 성공한 정책 평가와 실패한 정책 평가가 모두 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="72167-128">When this value is true, both successful and failed policy evaluations are logged.</span></span>  
  
4.  <span data-ttu-id="72167-129">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-129">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="72167-130">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="72167-130">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-policy-based-management"></a><span data-ttu-id="72167-131">정책 기반 관리를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="72167-131">To configure Policy-Based Management</span></span>  
  
1.  <span data-ttu-id="72167-132">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-132">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="72167-133">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-133">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="72167-134">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72167-134">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- enables Policy-Based Management   
    USE msdb;  
    GO  
    EXEC dbo.sp_syspolicy_configure   
         @name = N'Enabled',   
         @value = 1;  
    GO  
    ```  
  
 <span data-ttu-id="72167-135">자세한 내용은 [sp_syspolicy_configure&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72167-135">For more information, see [sp_syspolicy_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-syspolicy-configure-transact-sql).</span></span>  
  
  
