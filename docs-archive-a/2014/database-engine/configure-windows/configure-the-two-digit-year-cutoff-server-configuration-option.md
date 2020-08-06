---
title: two digit year cutoff 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- two digit year cutoff option
- four-digit years [SQL Server]
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c31c1d87c8b743132dd90d495f73ef711dc1f813
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649162"
---
# <a name="configure-the-two-digit-year-cutoff-server-configuration-option"></a><span data-ttu-id="831ac-102">two digit year cutoff 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="831ac-102">Configure the two digit year cutoff Server Configuration Option</span></span>
  <span data-ttu-id="831ac-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 두 자리 연도 구분 [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-103">This topic describes how to configure the **two digit year cutoff** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="831ac-104">**두 자리 연도 구분** 옵션은 두 자리 연도를 네 자리 연도로 해석할 구분 연도를 1753부터 9999까지의 정수 중에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-104">The **two digit year cutoff** option specifies an integer from 1753 to 9999 that represents the cutoff year for interpreting two-digit years as four-digit years.</span></span> <span data-ttu-id="831ac-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 시간 범위는 1950-2049입니다. 즉, 구분 연도가 2049년임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-105">The default time span for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is 1950-2049, which represents a cutoff year of 2049.</span></span> <span data-ttu-id="831ac-106">따라서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 두 자리 숫자 49를 2049년으로, 두 자리 숫자 50을 1950년으로, 두 자리 숫자 99를 1999년으로 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-106">This means that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets a two-digit year of 49 as 2049, a two-digit year of 50 as 1950, and a two-digit year of 99 as 1999.</span></span> <span data-ttu-id="831ac-107">이전 버전과의 호환성을 위해 기본값 설정을 그대로 두세요.</span><span class="sxs-lookup"><span data-stu-id="831ac-107">To maintain backward compatibility, leave the setting at the default value.</span></span>  
  
 <span data-ttu-id="831ac-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="831ac-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="831ac-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="831ac-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="831ac-110">권장 사항</span><span class="sxs-lookup"><span data-stu-id="831ac-110">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="831ac-111">보안</span><span class="sxs-lookup"><span data-stu-id="831ac-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="831ac-112">**두 자리 연도 구분 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="831ac-112">**To configure the two digit year cutoff option, using:**</span></span>  
  
     [<span data-ttu-id="831ac-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="831ac-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="831ac-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="831ac-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="831ac-115">**후속 작업:**  [두 자리 연도 구분 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="831ac-115">**Follow Up:**  [After you configure the two digit year cutoff option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="831ac-116">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="831ac-116">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="831ac-117">권장 사항</span><span class="sxs-lookup"><span data-stu-id="831ac-117">Recommendations</span></span>  
  
-   <span data-ttu-id="831ac-118">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-118">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="831ac-119">OLE 자동화 개체는 2030을 두 자리 구분 연도로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-119">OLE Automation objects use 2030 as the two-digit cutoff year.</span></span> <span data-ttu-id="831ac-120">**두 자리 연도 구분** 옵션을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 클라이언트 애플리케이션 간 날짜 값의 일관성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-120">You can use the **two digit year cutoff** option to provide consistency in date values between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and client applications.</span></span> <span data-ttu-id="831ac-121">그러나 날짜를 명확하게 구분하려면 데이터에 네 자리 연도를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="831ac-121">However, to avoid ambiguity with dates, use four-digit years in your data.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="831ac-122">보안</span><span class="sxs-lookup"><span data-stu-id="831ac-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="831ac-123">권한</span><span class="sxs-lookup"><span data-stu-id="831ac-123">Permissions</span></span>  
 <span data-ttu-id="831ac-124">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-124">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="831ac-125">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-125">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="831ac-126">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-126">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="831ac-127">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="831ac-127">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="831ac-128">두 자리 연도 구분 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="831ac-128">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="831ac-129">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-129">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="831ac-130">**기타 서버 설정** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-130">Click the **Misc server settings** node.</span></span>  
  
3.  <span data-ttu-id="831ac-131">**두 자리 연도 지원**의 **두 자리 연도를** **다음 연도로 해석** 입력란에 시간 범위의 끝 연도에 해당하는 값을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-131">Under **Two digit year support**, in the **When a two digit year is entered**, **interpret it as a year between** box, type or select a value that is the ending year of the time span.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="831ac-132">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="831ac-132">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-two-digit-year-cutoff-option"></a><span data-ttu-id="831ac-133">두 자리 연도 구분 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="831ac-133">To configure the two digit year cutoff option</span></span>  
  
1.  <span data-ttu-id="831ac-134">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="831ac-135">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="831ac-136">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-136">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="831ac-137">다음 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `two digit year cutoff` 옵션의 값을 `2030`(으)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-137">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `two digit year cutoff` option to `2030`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="831ac-138">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-138">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-two-digit-year-cutoff-option"></a><a name="FollowUp"></a> <span data-ttu-id="831ac-139">후속 작업: 두 자리 연도 구분 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="831ac-139">Follow Up: After you configure the two digit year cutoff option</span></span>  
 <span data-ttu-id="831ac-140">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="831ac-140">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="831ac-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="831ac-141">See Also</span></span>  
 <span data-ttu-id="831ac-142">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="831ac-142">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="831ac-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="831ac-143">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="831ac-144">RECONFIGURE&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="831ac-144">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
