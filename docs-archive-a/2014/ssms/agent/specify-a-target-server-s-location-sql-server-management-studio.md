---
title: 대상 서버&#39;s 위치 지정 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], location
ms.assetid: 511ff311-21f5-4f2f-839f-b4deee26ec98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 938528ab78f0f457cde69d8fd4d5432cc14a79b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653102"
---
# <a name="specify-a-target-server39s-location-sql-server-management-studio"></a><span data-ttu-id="ef4ec-102">대상 서버 위치 지정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="ef4ec-102">Specify a Target Server&#39;s Location (SQL Server Management Studio)</span></span>
  <span data-ttu-id="ef4ec-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 다중 서버 관리 구성에서 대상 서버의 위치를 지정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-103">This topic describes how to specify the location of a target server in a multiserver administration configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="ef4ec-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="ef4ec-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="ef4ec-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="ef4ec-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="ef4ec-106">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ef4ec-106">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="ef4ec-107">보안</span><span class="sxs-lookup"><span data-stu-id="ef4ec-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="ef4ec-108">**다음을 사용하여 대상 서버의 위치를 지정합니다.**</span><span class="sxs-lookup"><span data-stu-id="ef4ec-108">**To specify a target server's location, using:**</span></span>  
  
     [<span data-ttu-id="ef4ec-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="ef4ec-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="ef4ec-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="ef4ec-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ef4ec-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="ef4ec-111">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="ef4ec-112">제한 사항</span><span class="sxs-lookup"><span data-stu-id="ef4ec-112">Limitations and Restrictions</span></span>  
 <span data-ttu-id="ef4ec-113">이 동작을 수행하면 레지스트리가 편집됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-113">Performing this action edits the registry.</span></span> <span data-ttu-id="ef4ec-114">레지스트리를 잘못 변경하면 시스템에 심각한 구성 문제를 일으키기 때문에 레지스트리를 수동으로 편집하는 것은 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-114">Manual editing of the registry is not recommended because inappropriate or incorrect changes can cause serious configuration problems for your system.</span></span> <span data-ttu-id="ef4ec-115">숙련된 사용자만 레지스트리 편집기 프로그램을 사용하여 레지스트리를 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-115">Therefore, only experienced users should use the Registry Editor program to edit the registry.</span></span> <span data-ttu-id="ef4ec-116">자세한 내용은 Microsoft Windows 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-116">For more information, see the Microsoft Windows documentation.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ef4ec-117">보안</span><span class="sxs-lookup"><span data-stu-id="ef4ec-117">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ef4ec-118">권한</span><span class="sxs-lookup"><span data-stu-id="ef4ec-118">Permissions</span></span>  
 <span data-ttu-id="ef4ec-119">**sysadmin** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-119">Requires membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="ef4ec-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="ef4ec-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="ef4ec-121">대상 서버의 위치를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ef4ec-121">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="ef4ec-122">**개체 탐색기**에서 더하기 기호를 클릭하여 대상 서버 위치를 지정하려는 마스터 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-122">In **Object Explorer**, click the plus sign to expand the master server on which you want to specify a target server's location.</span></span>  
  
2.  <span data-ttu-id="ef4ec-123">**SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭하고 **다중 서버 관리**를 가리킨 다음 **대상 서버 관리**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-123">Right-click **SQL Server Agent**, point to **Multi Server Administration**, and select **Manage Target Servers**.</span></span>  
  
3.  <span data-ttu-id="ef4ec-124">대상 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-124">Right-click a target server and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="ef4ec-125">**위치** 상자에 서버의 위치를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-125">In the **Location** box, enter a location for the server, and then click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="ef4ec-126">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="ef4ec-126">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-target-servers-location"></a><span data-ttu-id="ef4ec-127">대상 서버의 위치를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="ef4ec-127">To specify a target server's location</span></span>  
  
1.  <span data-ttu-id="ef4ec-128">**개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-128">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="ef4ec-129">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-129">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="ef4ec-130">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-130">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```  
    USE msdb ;  
    GO  
    -- enlists the current server into the AdventureWorks1 master server.   
    -- The location for the current server is Building 21, Room 309, Rack 5  
    EXEC dbo.sp_msx_enlist N'AdventureWorks2012',   
        N'Building 21, Room 309, Rack 5' ;  
    GO  
    ```  
  
 <span data-ttu-id="ef4ec-131">자세한 내용은 [sp_msx_enlist &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef4ec-131">For more information, see [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).</span></span>  
  
  
