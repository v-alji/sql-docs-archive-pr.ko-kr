---
title: default full-text language 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646642"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a><span data-ttu-id="51b09-102">default full-text language 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="51b09-102">Configure the default full-text language Server Configuration Option</span></span>
  <span data-ttu-id="51b09-103">이 항목에서는 또는을 사용 하 `default full-text language` 여에서 서버 구성 옵션을 구성 하는 방법에 대해 설명 합니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="51b09-103">This topic describes how to configure the `default full-text language` server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="51b09-104">`default full-text language`옵션은 전체 텍스트 인덱스에 대 한 기본 언어 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-104">The `default full-text language` option specifies a default language value for full-text indexes.</span></span> <span data-ttu-id="51b09-105">언어 분석은 전체 텍스트 인덱싱된 모든 데이터에 대해 수행되고 해당 데이터 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-105">Linguistic analysis is performed on all data that is full-text indexed and is dependent on the language of the data.</span></span> <span data-ttu-id="51b09-106">이 옵션의 기본값은 서버의 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-106">The default value of this option is the language of the server.</span></span> <span data-ttu-id="51b09-107">의 지역화 된 버전에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `default full-text language` 적절 한 일치 항목이 있는 경우 설치 프로그램에서 옵션을 서버 언어로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-107">For a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup sets the `default full-text language` option to the language of the server if an appropriate match exists.</span></span> <span data-ttu-id="51b09-108">지역화되지 않은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전의 경우 `default full-text language` 옵션이 영어입니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-108">For a non-localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the `default full-text language` option is English.</span></span>  
  
 <span data-ttu-id="51b09-109">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="51b09-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="51b09-110">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="51b09-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="51b09-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="51b09-111">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="51b09-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="51b09-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="51b09-113">보안</span><span class="sxs-lookup"><span data-stu-id="51b09-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="51b09-114">**기본 전체 텍스트 언어 옵션을 구성하려면:**</span><span class="sxs-lookup"><span data-stu-id="51b09-114">**To configure the default full-text language option, using:**</span></span>  
  
     [<span data-ttu-id="51b09-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="51b09-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="51b09-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="51b09-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="51b09-117">**후속 작업:**  [기본 전체 텍스트 언어 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="51b09-117">**Follow Up:**  [After you configure the default full-text language option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="51b09-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="51b09-118">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="51b09-119">제한 사항</span><span class="sxs-lookup"><span data-stu-id="51b09-119">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="51b09-120">옵션 값은 `default full-text language` 전체 텍스트 인덱스에 사용 됩니다 .이 옵션은 전체 텍스트 인덱스 만들기 또는 ALTER 전체 텍스트 인덱스 문에 language **language_term** 옵션을 통해 지정 된 언어가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-120">The value of the `default full-text language` option is used in a full-text index when no language is specified for a column through the LANGUAGE **language_term** option in the CREATE FULLTEXT INDEX or ALTER FULLTEXT INDEX statements.</span></span> <span data-ttu-id="51b09-121">기본 전체 텍스트 언어가 지원되지 않거나 언어 분석 패키지를 사용할 수 없으면 CREATE 또는 ALTER 작업이 실패하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 지정된 언어가 올바르지 않다는 내용의 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-121">If the default full-text language is not supported or the linguistic analysis package is not available, the CREATE or ALTER operation will fail and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will return an error message stating that the language specified is not valid.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="51b09-122">권장 사항</span><span class="sxs-lookup"><span data-stu-id="51b09-122">Recommendations</span></span>  
  
-   <span data-ttu-id="51b09-123">이 옵션은 고급 옵션으로, 숙련된 데이터베이스 관리자나 공인된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기술 지원 담당자만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-123">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="51b09-124">옵션에는 `default full-text language` LCID 값이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-124">The `default full-text language` option requires an LCID value.</span></span> <span data-ttu-id="51b09-125">지원되는 LCID 및 해당 관련 언어 목록을 보려면 [sys.fulltext_languages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)서버 구성 옵션을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-125">For a list of supported LCIDs and their related languages, see [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).</span></span> <span data-ttu-id="51b09-126">ISV(Independent Software Vendor) 등에서 제공하는 다른 언어를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-126">Other languages may also be available from independent software vendors, for example.</span></span> <span data-ttu-id="51b09-127">특정 언어를 찾을 수 없으면 전체 텍스트 검색 엔진에서 주 언어로 자동 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-127">If no specific language dialect is found, the Full-Text Engine will automatically switch to the primary language.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="51b09-128">보안</span><span class="sxs-lookup"><span data-stu-id="51b09-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="51b09-129">권한</span><span class="sxs-lookup"><span data-stu-id="51b09-129">Permissions</span></span>  
 <span data-ttu-id="51b09-130">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-130">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="51b09-131">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-131">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="51b09-132">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-132">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="51b09-133">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="51b09-133">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="51b09-134">기본 전체 텍스트 언어 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="51b09-134">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="51b09-135">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-135">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="51b09-136">**고급** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-136">Click the **Advanced** node.</span></span>  
  
3.  <span data-ttu-id="51b09-137">기타의 **기본 전체 텍스트 언어** 를 사용하여 전체 텍스트가 인덱싱된 열의 기본 언어 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-137">Under Miscellaneous, use **Default Full Text Language** to specify a default language value for full-text indexed columns.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="51b09-138">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="51b09-138">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-default-full-text-language-option"></a><span data-ttu-id="51b09-139">기본 전체 텍스트 언어 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="51b09-139">To configure the default full-text language option</span></span>  
  
1.  <span data-ttu-id="51b09-140">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-140">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="51b09-141">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-141">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="51b09-142">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-142">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="51b09-143">다음 예제에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 사용하여 `default full-text` 옵션의 값을 Dutch(`1043`)로 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-143">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `default full-text` option to Dutch (`1043`).</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="51b09-144">자세한 내용은 [서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md)서버 구성 옵션을 보거나 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-144">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a> <span data-ttu-id="51b09-145">후속 작업: 기본 전체 텍스트 언어 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="51b09-145">Follow Up: After you configure the default full-text language option</span></span>  
 <span data-ttu-id="51b09-146">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="51b09-146">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b09-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51b09-147">See Also</span></span>  
 <span data-ttu-id="51b09-148">[sys.fulltext_languages&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51b09-148">[sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) </span></span>  
 <span data-ttu-id="51b09-149">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51b09-149">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="51b09-150">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="51b09-150">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="51b09-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51b09-151">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="51b09-152">[CREATE FULLTEXT INDEX&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="51b09-152">[CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql) </span></span>  
 [<span data-ttu-id="51b09-153">ALTER FULLTEXT INDEX&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="51b09-153">ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
