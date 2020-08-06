---
title: user options 서버 구성 옵션 구성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- global default for all users [SQL Server]
- users [SQL Server], global defaults
- user options option [SQL Server]
ms.assetid: cfed8f86-6bcf-4b90-88eb-9656e22d5dc5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7ee40d0f6de532b93ce9d8075b609c80f09df7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740425"
---
# <a name="configure-the-user-options-server-configuration-option"></a><span data-ttu-id="2392d-102">user options 서버 구성 옵션 구성</span><span class="sxs-lookup"><span data-stu-id="2392d-102">Configure the user options Server Configuration Option</span></span>
  <span data-ttu-id="2392d-103">이 항목에서는 **또는** 을 사용하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] user options [!INCLUDE[tsql](../../includes/tsql-md.md)]서버 구성 옵션을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-103">This topic describes how to configure the **user options** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="2392d-104">**user options** 옵션은 모든 사용자에 대한 전역 기본값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-104">The **user options** option specifies global defaults for all users.</span></span> <span data-ttu-id="2392d-105">기본 쿼리 처리 옵션 목록은 사용자의 작업 세션 기간에 대해 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-105">A list of default query processing options is established for the duration of a user's work session.</span></span> <span data-ttu-id="2392d-106">**user options** 옵션을 사용하면 서버의 기본 설정이 적합하지 않은 경우 SET 옵션의 기본값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-106">The **user options** option allows you to change the default values of the SET options (if the server's default settings are not appropriate).</span></span>  
  
 <span data-ttu-id="2392d-107">사용자는 SET 문을 사용하여 이 기본값을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-107">A user can override these defaults by using the SET statement.</span></span> <span data-ttu-id="2392d-108">새로운 로그인에 대해 **user options** 를 동적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-108">You can configure **user options** dynamically for new logins.</span></span> <span data-ttu-id="2392d-109">**user options**설정을 변경하고 나면 새 로그인이 새 설정을 사용합니다. 현재 로그인에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-109">After you change the setting of **user options**, new login sessions use the new setting; current login sessions are not affected.</span></span>  
  
 <span data-ttu-id="2392d-110">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="2392d-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2392d-111">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="2392d-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2392d-112">권장 사항</span><span class="sxs-lookup"><span data-stu-id="2392d-112">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="2392d-113">보안</span><span class="sxs-lookup"><span data-stu-id="2392d-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="2392d-114">**다음을 사용하여 user options 구성 옵션을 구성합니다.**</span><span class="sxs-lookup"><span data-stu-id="2392d-114">**To configure the user options configuration option, using:**</span></span>  
  
     [<span data-ttu-id="2392d-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2392d-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2392d-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2392d-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="2392d-117">**후속 작업:**  [user options 구성 옵션을 구성한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="2392d-117">**Follow Up:**  [After you configure the user options configuration option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2392d-118">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="2392d-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2392d-119">권장 사항</span><span class="sxs-lookup"><span data-stu-id="2392d-119">Recommendations</span></span>  
  
-   <span data-ttu-id="2392d-120">다음 표에서는 **user options**에 따른 구성 값을 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-120">The following table lists and describes the configuration values for **user options**.</span></span> <span data-ttu-id="2392d-121">모든 구성 값은 서로 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-121">Not all configuration values are compatible with each other.</span></span> <span data-ttu-id="2392d-122">예를 들어 ANSI_NULL_DFLT_ON 및 ANSI_NULL_DFLT_OFF는 동시에 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-122">For example, ANSI_NULL_DFLT_ON and ANSI_NULL_DFLT_OFF cannot be set at the same time.</span></span>  
  
    |<span data-ttu-id="2392d-123">값</span><span class="sxs-lookup"><span data-stu-id="2392d-123">Value</span></span>|<span data-ttu-id="2392d-124">구성</span><span class="sxs-lookup"><span data-stu-id="2392d-124">Configuration</span></span>|<span data-ttu-id="2392d-125">Description</span><span class="sxs-lookup"><span data-stu-id="2392d-125">Description</span></span>|  
    |-----------|-------------------|-----------------|  
    |<span data-ttu-id="2392d-126">1</span><span class="sxs-lookup"><span data-stu-id="2392d-126">1</span></span>|<span data-ttu-id="2392d-127">DISABLE_DEF_CNST_CHK</span><span class="sxs-lookup"><span data-stu-id="2392d-127">DISABLE_DEF_CNST_CHK</span></span>|<span data-ttu-id="2392d-128">중간 또는 지연된 제약 조건 검사를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-128">Controls interim or deferred constraint checking.</span></span>|  
    |<span data-ttu-id="2392d-129">2</span><span class="sxs-lookup"><span data-stu-id="2392d-129">2</span></span>|<span data-ttu-id="2392d-130">IMPLICIT_TRANSACTIONS</span><span class="sxs-lookup"><span data-stu-id="2392d-130">IMPLICIT_TRANSACTIONS</span></span>|<span data-ttu-id="2392d-131">dblib 네트워크 라이브러리 연결의 경우 문 실행 시 트랜잭션을 암시적으로 시작할지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-131">For dblib network library connections, controls whether a transaction is started implicitly when a statement is executed.</span></span> <span data-ttu-id="2392d-132">IMPLICIT_TRANSACTIONS 설정은 ODBC 또는 OLEDB 연결에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-132">The IMPLICIT_TRANSACTIONS setting has no effect on ODBC or OLEDB connections.</span></span>|  
    |<span data-ttu-id="2392d-133">4</span><span class="sxs-lookup"><span data-stu-id="2392d-133">4</span></span>|<span data-ttu-id="2392d-134">CURSOR_CLOSE_ON_COMMIT</span><span class="sxs-lookup"><span data-stu-id="2392d-134">CURSOR_CLOSE_ON_COMMIT</span></span>|<span data-ttu-id="2392d-135">커밋 작업 수행 후 커서의 동작을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-135">Controls behavior of cursors after a commit operation has been performed.</span></span>|  
    |<span data-ttu-id="2392d-136">8</span><span class="sxs-lookup"><span data-stu-id="2392d-136">8</span></span>|<span data-ttu-id="2392d-137">ANSI_WARNINGS</span><span class="sxs-lookup"><span data-stu-id="2392d-137">ANSI_WARNINGS</span></span>|<span data-ttu-id="2392d-138">집계 경고의 잘림과 NULL을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-138">Controls truncation and NULL in aggregate warnings.</span></span>|  
    |<span data-ttu-id="2392d-139">16</span><span class="sxs-lookup"><span data-stu-id="2392d-139">16</span></span>|<span data-ttu-id="2392d-140">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="2392d-140">ANSI_PADDING</span></span>|<span data-ttu-id="2392d-141">고정 길이 변수의 패딩을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-141">Controls padding of fixed-length variables.</span></span>|  
    |<span data-ttu-id="2392d-142">32</span><span class="sxs-lookup"><span data-stu-id="2392d-142">32</span></span>|<span data-ttu-id="2392d-143">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="2392d-143">ANSI_NULLS</span></span>|<span data-ttu-id="2392d-144">동등 연산자 사용 시 NULL 처리를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-144">Controls NULL handling when using equality operators.</span></span>|  
    |<span data-ttu-id="2392d-145">64</span><span class="sxs-lookup"><span data-stu-id="2392d-145">64</span></span>|<span data-ttu-id="2392d-146">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="2392d-146">ARITHABORT</span></span>|<span data-ttu-id="2392d-147">쿼리 실행 중 오버플로 또는 0으로 나누기 오류가 발생하면 쿼리를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-147">Terminates a query when an overflow or divide-by-zero error occurs during query execution.</span></span>|  
    |<span data-ttu-id="2392d-148">128</span><span class="sxs-lookup"><span data-stu-id="2392d-148">128</span></span>|<span data-ttu-id="2392d-149">ARITHIGNORE</span><span class="sxs-lookup"><span data-stu-id="2392d-149">ARITHIGNORE</span></span>|<span data-ttu-id="2392d-150">쿼리 실행 중 오버플로 또는 0으로 나누기 오류가 발생하면 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-150">Returns NULL when an overflow or divide-by-zero error occurs during a query.</span></span>|  
    |<span data-ttu-id="2392d-151">256</span><span class="sxs-lookup"><span data-stu-id="2392d-151">256</span></span>|<span data-ttu-id="2392d-152">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="2392d-152">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="2392d-153">식을 평가할 때 큰따옴표와 작은따옴표를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-153">Differentiates between single and double quotation marks when evaluating an expression.</span></span>|  
    |<span data-ttu-id="2392d-154">512</span><span class="sxs-lookup"><span data-stu-id="2392d-154">512</span></span>|<span data-ttu-id="2392d-155">NOCOUNT</span><span class="sxs-lookup"><span data-stu-id="2392d-155">NOCOUNT</span></span>|<span data-ttu-id="2392d-156">영향 받는 행 수를 지정하는 각 문의 끝에 반환되는 메시지를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-156">Turns off the message returned at the end of each statement that states how many rows were affected.</span></span>|  
    |<span data-ttu-id="2392d-157">1024</span><span class="sxs-lookup"><span data-stu-id="2392d-157">1024</span></span>|<span data-ttu-id="2392d-158">ANSI_NULL_DFLT_ON</span><span class="sxs-lookup"><span data-stu-id="2392d-158">ANSI_NULL_DFLT_ON</span></span>|<span data-ttu-id="2392d-159">세션에서 Null 허용에 대해 ANSI 호환성을 사용할 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-159">Alters the session's behavior to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="2392d-160">명시적 Null 허용 없이 정의된 새 열은 Null을 허용하도록 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-160">New columns defined without explicit nullability are defined to allow nulls.</span></span>|  
    |<span data-ttu-id="2392d-161">2048</span><span class="sxs-lookup"><span data-stu-id="2392d-161">2048</span></span>|<span data-ttu-id="2392d-162">ANSI_NULL_DFLT_OFF</span><span class="sxs-lookup"><span data-stu-id="2392d-162">ANSI_NULL_DFLT_OFF</span></span>|<span data-ttu-id="2392d-163">세션이 null 허용에 대해 ANSI 호환성을 사용하지 않을 때 경고합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-163">Alters the session's behavior not to use ANSI compatibility for nullability.</span></span> <span data-ttu-id="2392d-164">명시적인 NULL 허용 없이 정의된 새 열은 NULL을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-164">New columns defined without explicit nullability do not allow nulls.</span></span>|  
    |<span data-ttu-id="2392d-165">4096</span><span class="sxs-lookup"><span data-stu-id="2392d-165">4096</span></span>|<span data-ttu-id="2392d-166">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="2392d-166">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="2392d-167">문자열이 있는 NULL 값을 연결할 때 NULL을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-167">Returns NULL when concatenating a NULL value with a string.</span></span>|  
    |<span data-ttu-id="2392d-168">8192</span><span class="sxs-lookup"><span data-stu-id="2392d-168">8192</span></span>|<span data-ttu-id="2392d-169">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="2392d-169">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="2392d-170">식의 전체 자릿수가 떨어지면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-170">Generates an error when a loss of precision occurs in an expression.</span></span>|  
    |<span data-ttu-id="2392d-171">16384</span><span class="sxs-lookup"><span data-stu-id="2392d-171">16384</span></span>|<span data-ttu-id="2392d-172">XACT_ABORT</span><span class="sxs-lookup"><span data-stu-id="2392d-172">XACT_ABORT</span></span>|<span data-ttu-id="2392d-173">Transact-SQL 문이 런타임 오류를 일으키면 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-173">Rolls back a transaction if a Transact-SQL statement raises a run-time error.</span></span>|  
  
-   <span data-ttu-id="2392d-174">**user options**의 비트 위치는 @@OPTIONS의 비트 위치와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-174">The bit positions in **user options** are identical to those in @@OPTIONS.</span></span> <span data-ttu-id="2392d-175">각 연결에는 구성 환경을 나타내는 @@OPTIONS 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-175">Each connection has its own @@OPTIONS function, which represents the configuration environment.</span></span> <span data-ttu-id="2392d-176">\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 로그인하면 현재 **user options** 값을 @@OPTIONS에 할당하는 기본 환경이 사용자에게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-176">When logging in to an instance of \ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a user receives a default environment that assigns the current **user options** value to @@OPTIONS.</span></span> <span data-ttu-id="2392d-177">**user options**에 대한 SET 문을 실행하면 세션의 @@OPTIONS 함수에 해당하는 값에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-177">Executing SET statements for **user options** affects the corresponding value in the session's @@OPTIONS function.</span></span> <span data-ttu-id="2392d-178">이 설정이 변경된 이후에 만들어진 모든 연결은 새 값을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-178">All connections created after this setting is changed receive the new value.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="2392d-179">보안</span><span class="sxs-lookup"><span data-stu-id="2392d-179">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="2392d-180">권한</span><span class="sxs-lookup"><span data-stu-id="2392d-180">Permissions</span></span>  
 <span data-ttu-id="2392d-181">매개 변수 없이 또는 첫 번째 매개 변수만 사용하여 **sp_configure** 를 실행할 수 있는 권한은 기본적으로 모든 사용자에게 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-181">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="2392d-182">구성 옵션을 변경하거나 RECONFIGURE 문을 실행하는 두 매개 변수를 사용하여 **sp_configure** 를 실행하려면 사용자에게 ALTER SETTINGS 서버 수준 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-182">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="2392d-183">**sysadmin** 및 **serveradmin** 고정 서버 역할은 ALTER SETTINGS 권한을 암시적으로 보유하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-183">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2392d-184">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="2392d-184">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="2392d-185">user options 구성 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2392d-185">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="2392d-186">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-186">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="2392d-187">**연결** 노드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-187">Click the **Connections** node.</span></span>  
  
3.  <span data-ttu-id="2392d-188">**기본 연결 옵션** 상자에서 하나 이상의 특성을 선택하여 연결된 모든 사용자의 기본 쿼리 처리 옵션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-188">In the **Default connection options** box, select one or more attributes to configure the default query-processing options for all connected users.</span></span>  
  
     <span data-ttu-id="2392d-189">기본적으로 사용자 옵션은 구성되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-189">By default, no user options are configured.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2392d-190">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="2392d-190">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-user-options-configuration-option"></a><span data-ttu-id="2392d-191">user options 구성 옵션을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2392d-191">To configure the user options configuration option</span></span>  
  
1.  <span data-ttu-id="2392d-192">[!INCLUDE[ssDE](../../includes/ssde-md.md)]에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-192">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="2392d-193">표준 도구 모음에서 **새 쿼리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-193">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="2392d-194">다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-194">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="2392d-195">이 예에서는 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 를 통해 ANSI_WARNINGS 서버 옵션에 대한 설정을 변경하기 위해 `user options` 으로 설정하여 제한 시간을 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-195">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the `user options` to change the setting for the ANSI_WARNINGS server option.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'user options', 8 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
##  <a name="follow-up-after-you-configure-the-user-options-configuration-option"></a><a name="FollowUp"></a> <span data-ttu-id="2392d-196">후속 작업: user options 구성 옵션을 구성한 후</span><span class="sxs-lookup"><span data-stu-id="2392d-196">Follow Up: After you configure the user options configuration option</span></span>  
 <span data-ttu-id="2392d-197">이 설정은 서버를 다시 시작하지 않아도 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2392d-197">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2392d-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2392d-198">See Also</span></span>  
 <span data-ttu-id="2392d-199">[RECONFIGURE&#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2392d-199">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2392d-200">[서버 구성 옵션&#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2392d-200">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="2392d-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2392d-201">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="2392d-202">SET 문&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2392d-202">SET Statements &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-statements-transact-sql)  
  
  
