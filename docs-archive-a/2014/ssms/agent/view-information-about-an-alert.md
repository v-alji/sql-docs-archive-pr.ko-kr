---
title: 경고에 대한 정보 보기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ee72512a507299e71f13fee689709a9403bb04e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649317"
---
# <a name="view-information-about-an-alert"></a><span data-ttu-id="b68e4-102">View Information About an Alert</span><span class="sxs-lookup"><span data-stu-id="b68e4-102">View Information About an Alert</span></span>
  <span data-ttu-id="b68e4-103">이 항목 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 또는을 사용 하 여에서 에이전트 경고에 대 한 정보를 보는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b68e4-103">This topic describes how to view information about [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="b68e4-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="b68e4-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b68e4-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="b68e4-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b68e4-106">보안</span><span class="sxs-lookup"><span data-stu-id="b68e4-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="b68e4-107">**다음을 사용하여 경고에 대한 정보를 봅니다.**</span><span class="sxs-lookup"><span data-stu-id="b68e4-107">**To view information about an alert, using:**</span></span>  
  
     [<span data-ttu-id="b68e4-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b68e4-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b68e4-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b68e4-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b68e4-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="b68e4-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="b68e4-111">보안</span><span class="sxs-lookup"><span data-stu-id="b68e4-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="b68e4-112">권한</span><span class="sxs-lookup"><span data-stu-id="b68e4-112">Permissions</span></span>  
 <span data-ttu-id="b68e4-113">기본적으로 **sysadmin** 고정 서버 역할의 멤버가 경고의 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-113">By default, members of the **sysadmin** fixed server role can view information about an alert.</span></span> <span data-ttu-id="b68e4-114">다른 사용자는 **msdb** 데이터베이스의 **SQLAgentOperatorRole** 고정 데이터베이스 역할을 부여 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-114">Other users must be granted the **SQLAgentOperatorRole** fixed database role in the **msdb** database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b68e4-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="b68e4-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="b68e4-116">경고에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="b68e4-116">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="b68e4-117">**개체 탐색기** 에서 더하기 기호를 클릭하여 경고에 대한 정보를 보려는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-117">In **Object Explorer,** click the plus sign to expand the server where you want to view information about an alert.</span></span>  
  
2.  <span data-ttu-id="b68e4-118">더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-118">Click the plus sign to expand **SQL Server Agent**.</span></span>  
  
3.  <span data-ttu-id="b68e4-119">더하기 기호를 클릭하여 **경고** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-119">Click the plus sign to expand the **Alerts** folder.</span></span>  
  
4.  <span data-ttu-id="b68e4-120">보려는 정보가 포함된 경고를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-120">Right-click the alert that has the information you want to view and select **Properties**.</span></span>  
  
     <span data-ttu-id="b68e4-121">_Alert_name_**경고 속성** 대화 상자에 포함 된 사용 가능한 옵션에 대 한 자세한 내용은 다음을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b68e4-121">For more information on the available options contained in the _alert_name_**alert properties** dialog box, see:</span></span>  
  
    -   [<span data-ttu-id="b68e4-122">경고 속성-새 경고 &#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b68e4-122">Alert Properties-New Alert &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [<span data-ttu-id="b68e4-123">경고 속성-새 경고 &#40;응답 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b68e4-123">Alert Properties-New Alert &#40;Response Page&#41;</span></span>](alert-properties-new-alert-response-page.md)  
  
    -   [<span data-ttu-id="b68e4-124">경고 속성: 새 경고 &#40;옵션 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b68e4-124">Alert Properties: New Alert &#40;Options Page&#41;</span></span>](alert-properties-new-alert-options-page.md)  
  
    -   [<span data-ttu-id="b68e4-125">경고 속성&#40;기록 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b68e4-125">Alert Properties &#40;History Page&#41;</span></span>](alert-properties-history-page.md)  
  
5.  <span data-ttu-id="b68e4-126">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-126">When finished, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b68e4-127">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="b68e4-127">Using Transact-SQL</span></span>  
  
#### <a name="to-view-information-about-an-alert"></a><span data-ttu-id="b68e4-128">경고에 대한 정보를 보려면</span><span class="sxs-lookup"><span data-stu-id="b68e4-128">To view information about an alert</span></span>  
  
1.  <span data-ttu-id="b68e4-129">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-129">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="b68e4-130">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-130">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="b68e4-131">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b68e4-131">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 <span data-ttu-id="b68e4-132">자세한 내용은 [sp_help_alert &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b68e4-132">For more information, see [sp_help_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).</span></span>  
  
  
