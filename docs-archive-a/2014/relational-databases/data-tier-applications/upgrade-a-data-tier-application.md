---
title: 데이터 계층 애플리케이션 업그레이드 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.upgradedacwizard.reviewpolicy.f1
- sql12.swb.upgradedacwizard.selectoptions.f1
- sql12.swb.upgradedacwizard.selectpackage.f1
- sql12.swb.upgradedacwizard.reviewplan.f1
- sql12.swb.upgradedacwizard.checkdrift.f1
- sql12.swb.upgradedacwizard.summary.f1
- sql12.swb.upgradedacwizard.upgradedac.f1
- sql12.swb.upgradedacwizard.introduction.f1
helpviewer_keywords:
- upgrade DAC
- data-tier application [SQL Server], upgrade
- wizard [DAC], upgrade
- How to [DAC], upgrade
ms.assetid: c117df94-f02b-403f-9383-ec5b3ac3763c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0e597d02af28a16539b50ff76503059278ef7a03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660633"
---
# <a name="upgrade-a-data-tier-application"></a><span data-ttu-id="824d8-102">데이터 계층 애플리케이션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="824d8-102">Upgrade a Data-tier Application</span></span>
  <span data-ttu-id="824d8-103">데이터 계층 애플리케이션 업그레이드 마법사 또는 Windows PowerShell 스크립트를 사용하여 현재 배포된 DAC(데이터 계층 애플리케이션)의 스키마와 속성을 새 DAC 버전에 정의된 스키마와 속성과 일치하도록 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-103">Use either the Upgrade Data-tier Application Wizard or a Windows PowerShell script to change the schema and properties of a currently deployed data-tier application (DAC) to match the schema and properties defined in a new version of the DAC.</span></span>  
  
-   <span data-ttu-id="824d8-104">**시작하기 전 주의 사항:**  [DAC 업그레이드 옵션 선택](#ChoseDACUpgOptions), [제한 사항](#LimitationsRestrictions), [필수 구성 요소](#Prerequisites), [보안](#Security), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="824d8-104">**Before you begin:**  [Choosing DAC Upgrade Options](#ChoseDACUpgOptions), [Limitations and Restrictions](#LimitationsRestrictions), [Prerequisites](#Prerequisites), [Security](#Security), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="824d8-105">**DAC를 업그레이드하려면 다음을 사용합니다.**  [데이터 계층 애플리케이션 업그레이드 마법사](#UsingDACUpgradeWizard), [PowerShell](#UpgradeDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="824d8-105">**To upgrade a DAC, using:**  [The Upgrade Data-tier Application Wizard](#UsingDACUpgradeWizard), [PowerShell](#UpgradeDACPowerShell)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="824d8-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="824d8-106">Before You Begin</span></span>  
 <span data-ttu-id="824d8-107">DAC 업그레이드는 기존 데이터베이스의 스키마를 새 DAC 버전에 정의된 스키마와 일치하도록 변경하는 전체 업그레이드 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-107">A DAC upgrade is an in-place process that alters the schema of the existing database to match the schema defined in a new version of the DAC.</span></span> <span data-ttu-id="824d8-108">새 버전의 DTS가 DAC 패키지 파일에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-108">The new version of the DAC is supplied in a DAC package file.</span></span> <span data-ttu-id="824d8-109">DAC 패키지를 만드는 방법은 [데이터 계층 애플리케이션](data-tier-applications.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824d8-109">For more information about creating a DAC package, see [Data-tier Applications](data-tier-applications.md).</span></span>  
  
###  <a name="choosing-dac-upgrade-options"></a><a name="ChoseDACUpgOptions"></a> <span data-ttu-id="824d8-110">DAC 업그레이드 옵션 선택</span><span class="sxs-lookup"><span data-stu-id="824d8-110">Choosing DAC Upgrade Options</span></span>  
 <span data-ttu-id="824d8-111">전체 업그레이드에는 4가지 업그레이드 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-111">There are four upgrade options for an in-place upgrade:</span></span>  
  
-   <span data-ttu-id="824d8-112">**데이터 손실 무시** -이면 `True` 일부 작업으로 인해 데이터가 손실 되더라도 업그레이드가 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-112">**Ignore Data Loss** - If `True`, the upgrade will proceed even if some of the operations result in the loss of data.</span></span> <span data-ttu-id="824d8-113">`False`인 경우 이러한 작업은 업그레이드를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-113">If `False`, these operations will terminate the upgrade.</span></span> <span data-ttu-id="824d8-114">예를 들어, 현재 데이터베이스의 테이블이 새로운 DAC의 스키마에 제공되지 않는 경우 `True`가 지정되면 테이블이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-114">For example, if a table in the current database is not present in the schema of the new DAC, the table will be dropped if `True` is specified.</span></span> <span data-ttu-id="824d8-115">기본 설정은 `True`입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-115">The default setting is `True`.</span></span>  
  
-   <span data-ttu-id="824d8-116">**변경 시 차단** -이면 `True` 데이터베이스 스키마가 이전 DAC에 정의 된 스키마와 다른 경우 업그레이드가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-116">**Block on Changes** - If `True`, the upgrade is terminated if the database schema is different than that defined in the previous DAC.</span></span> <span data-ttu-id="824d8-117">`False`인 경우 변경이 감지되어도 업그레이드가 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-117">If `False`, the upgrade continues even if changes are detected.</span></span> <span data-ttu-id="824d8-118">기본 설정은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-118">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="824d8-119">**오류 발생 시 롤백** -인 경우 `True` 업그레이드가 트랜잭션에 포함 되 고 오류가 발생 하면 롤백이 시도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-119">**Rollback on Failure** - If `True`, the upgrade is enclosed in a transaction, and if errors are encountered a rollback will be attempted.</span></span> <span data-ttu-id="824d8-120">`False`인 경우 변경이 되면 모든 변경 내용이 커밋되고 오류가 발생하면 데이터베이스의 이전 백업을 복원해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-120">If `False`, all changes are committed as they are made and if errors occur you may have to restore a previous backup of the database.</span></span> <span data-ttu-id="824d8-121">기본 설정은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-121">The default setting is `False`.</span></span>  
  
-   <span data-ttu-id="824d8-122">**정책 유효성 검사 건너뛰기** -인 경우 `True` DAC 서버 선택 정책이 평가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-122">**Skip Policy Validation** - If `True`, the DAC server selection policy is not evaluated.</span></span> <span data-ttu-id="824d8-123">`False`인 경우 정책이 평가되고 유효성 검사 오류가 있으면 업그레이드가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-123">If `False`, the policy is evaluated and the upgrade terminates if there is a validation error.</span></span> <span data-ttu-id="824d8-124">기본 설정은 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-124">The default setting is `False`.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="824d8-125">제한 사항</span><span class="sxs-lookup"><span data-stu-id="824d8-125">Limitations and Restrictions</span></span>  
 <span data-ttu-id="824d8-126">DAC 업그레이드는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4(서비스 팩 4) 이상에서만 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-126">DAC uprades can only be performed in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="824d8-127">필수 조건</span><span class="sxs-lookup"><span data-stu-id="824d8-127">Prerequisites</span></span>  
 <span data-ttu-id="824d8-128">업그레이드를 시작하기 전에 전체 데이터베이스 백업을 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-128">It is prudent to take a full database backup before starting the upgrade.</span></span> <span data-ttu-id="824d8-129">업그레이드할 때 오류가 발생하여 모든 변경 내용을 롤백할 수 없는 경우 백업을 복원해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-129">If an upgrade encounters an error and cannot roll back all of its changes, you may need to restore the backup.</span></span>  
  
 <span data-ttu-id="824d8-130">업그레이드를 시작하기 전에 DAC 패키지 및 업그레이드 동작의 유효성을 검사하기 위해 취해야 하는 조치는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-130">Before starting the upgrade, there are several actions that you should take to validate the DAC package and the upgrade actions.</span></span> <span data-ttu-id="824d8-131">이러한 검사를 수행하는 방법은 [Validate a DAC Package](validate-a-dac-package.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824d8-131">For more information about how to perform these checks, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
-   <span data-ttu-id="824d8-132">출처를 알 수 없거나 신뢰할 수 없는 DAC 패키지를 사용하여 업그레이드하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-132">We recommend that you do not upgrade by using a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="824d8-133">이러한 패키지에 포함된 악성 코드가 의도하지 않은 Transact-SQL 코드를 실행하거나 스키마를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-133">Such packages could contain malicious code that might execute unintended Transact-SQL code or cause errors by modifying the schema.</span></span> <span data-ttu-id="824d8-134">출처를 알 수 없거나 신뢰할 수 없는 패키지를 사용하려면 먼저 DAC의 압축을 풀고 저장 프로시저나 다른 사용자 정의 코드와 같은 코드를 검사하세요.</span><span class="sxs-lookup"><span data-stu-id="824d8-134">Before you use a package from an unknown or untrusted source, unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
-   <span data-ttu-id="824d8-135">마지막 버전의 DAC가 배포된 후 현재 데이터베이스가 변경된 경우 일부 변경 사항으로 인해 업그레이드가 성공적으로 완료되지 못하거나 업그레이드에 의해 일부 변경 사항이 제거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-135">If changes have been made to the current database after the last version of the DAC was deployed, some of the changes may prevent the successful completion of the upgrade, or be removed by the upgrade.</span></span> <span data-ttu-id="824d8-136">먼저 데이터베이스의 변경 내용에 대한 보고서를 생성하고 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-136">You should first generate and review a report of any such changes made in the database.</span></span>  
  
-   <span data-ttu-id="824d8-137">업그레이드가 수행할 스키마 변경 목록을 생성하고 목록에서 문제가 있는지 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-137">It is prudent to generate a list of the schema changes the upgrade will perform, and review the list for any problems.</span></span>  
  
 <span data-ttu-id="824d8-138">DAC 패키지의 애플리케이션 이름이 현재 배포된 DAC의 애플리케이션 이름과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-138">The application name in the DAC package must match the application name of the currently deployed DAC.</span></span> <span data-ttu-id="824d8-139">예를 들어 현재 DAC의 애플리케이션 이름이 **GeneralLedger**이면 마찬가지로 애플리케이션 이름이 **GeneralLedger**인 DAC 패키지를 사용해야 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-139">For example, if the current DAC has an application name of **GeneralLedger**, you can only upgrade by using a DAC package that also has an application name of **GeneralLedger**.</span></span>  
  
 <span data-ttu-id="824d8-140">모든 수정 사항을 기록할 수 있는 충분한 트랜잭션 로그 공간이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-140">Ensure there is enough transaction log space available to log all of the modifications.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="824d8-141">보안</span><span class="sxs-lookup"><span data-stu-id="824d8-141">Security</span></span>  
 <span data-ttu-id="824d8-142">보안을 개선하기 위해 SQL Server 인증 로그인은 암호 없이 DAC 패키지에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-142">To improve security, SQL Server Authentication logins are stored in a DAC package without a password.</span></span> <span data-ttu-id="824d8-143">패키지가 배포 또는 업그레이드되면 생성된 암호와 함께 비활성 로그인이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-143">When the package is deployed or upgraded, the login is created as a disabled login with a generated password.</span></span> <span data-ttu-id="824d8-144">로그인을 활성화하려면 ALTER ANY LOGIN 권한이 있는 로그인을 사용하여 로그인하고 ALTER LOGIN을 사용하여 로그인을 활성화하여 사용자에게 알려 줄 수 있는 새 암호를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-144">To enable the logins, log in using a login that has ALTER ANY LOGIN permission and use ALTER LOGIN to enable the login and assign a new password that can be communicated to the user.</span></span> <span data-ttu-id="824d8-145">Windows 인증 로그인의 경우 암호가 SQL Server에서 관리되지 않으므로 이 과정이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-145">This is not needed for Windows Authentication logins because their passwords are not managed by SQL Server.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="824d8-146">권한</span><span class="sxs-lookup"><span data-stu-id="824d8-146">Permissions</span></span>  
 <span data-ttu-id="824d8-147">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버를 통하거나 **dbcreator** 고정 서버 역할에 포함되고 ALTER ANY LOGIN 권한이 있는 로그인을 통해서만 DAC를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-147">A DAC can only be upgraded by members of the **sysadmin** or **serveradmin** fixed server roles, or by logins that are in the **dbcreator** fixed server role and have ALTER ANY LOGIN permissions.</span></span> <span data-ttu-id="824d8-148">로그인은 기존 데이터베이스의 소유자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-148">The login must be the owner of the existing database.</span></span> <span data-ttu-id="824d8-149">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **라는 기본 제공** 시스템 관리자 계정도 DAC를 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-149">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also upgrade a DAC.</span></span>  
  
##  <a name="using-the-upgrade-data-tier-application-wizard"></a><a name="UsingDACUpgradeWizard"></a> <span data-ttu-id="824d8-150">데이터 계층 애플리케이션 업그레이드 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="824d8-150">Using the Upgrade Data-tier Application Wizard</span></span>  
 <span data-ttu-id="824d8-151">**마법사를 사용하여 DAC를 업그레이드하려면**</span><span class="sxs-lookup"><span data-stu-id="824d8-151">**To Upgrade a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="824d8-152">**개체 탐색기**에서 업그레이드할 DAC가 포함된 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-152">In **Object Explorer**, expand the node for the instance containing the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="824d8-153">**관리** 노드, **데이터 계층 애플리케이션** 노드를 차례로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-153">Expand the **Management** node, and then expand the **Data-tier Applications** node.</span></span>  
  
3.  <span data-ttu-id="824d8-154">업그레이드할 DAC에 대한 노드를 마우스 오른쪽 단추로 클릭한 다음, **데이터 계층 애플리케이션 업그레이드...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-154">Right-click the node for the DAC to be upgraded, and then select **Upgrade Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="824d8-155">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-155">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="824d8-156">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-156">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="824d8-157">패키지 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-157">Select Package Page</span></span>](#Select_dac_package)  
  
    3.  [<span data-ttu-id="824d8-158">정책 검토 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-158">Review Policy Page</span></span>](#Review_policy)  
  
    4.  [<span data-ttu-id="824d8-159">변경 내용 검색 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-159">Detect Change Page</span></span>](#Detect_change)  
  
    5.  [<span data-ttu-id="824d8-160">업그레이드 계획 검토</span><span class="sxs-lookup"><span data-stu-id="824d8-160">Review the Upgrade Plan</span></span>](#ReviewUpgPlan)  
  
    6.  [<span data-ttu-id="824d8-161">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-161">Summary Page</span></span>](#Summary)  
  
    7.  [<span data-ttu-id="824d8-162">DAC 업그레이드 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-162">Upgrade DAC Page</span></span>](#Upgrade)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="824d8-163">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-163">Introduction Page</span></span>  
 <span data-ttu-id="824d8-164">이 페이지에서는 데이터 계층 애플리케이션을 업그레이드하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-164">This page describes the steps for upgrading a data-tier application.</span></span>  
  
 <span data-ttu-id="824d8-165">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="824d8-165">**Do not show this page again.**</span></span> <span data-ttu-id="824d8-166">- 앞으로 이 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-166">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="824d8-167">**다음 >** - **패키지 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-167">**Next >** - Proceeds to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="824d8-168">**취소** - DAC를 업그레이드하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-168">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="select-package-page"></a><a name="Select_dac_package"></a> <span data-ttu-id="824d8-169">패키지 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-169">Select Package Page</span></span>  
 <span data-ttu-id="824d8-170">이 페이지를 사용하여 데이터 계층 애플리케이션의 새 버전을 포함하는 DAC 패키지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-170">Use this page to specify the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="824d8-171">이 페이지는 두 가지 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-171">The page transitions through two states.</span></span>  
  
### <a name="select-the-dac-package"></a><span data-ttu-id="824d8-172">DAC 패키지 선택</span><span class="sxs-lookup"><span data-stu-id="824d8-172">Select the DAC Package</span></span>  
 <span data-ttu-id="824d8-173">이 페이지의 초기 상태를 사용하여 배포할 DAC 패키지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-173">Use the initial state of the page to choose the DAC package to deploy.</span></span> <span data-ttu-id="824d8-174">DAC 패키지는 유효한 DAC 패키지 파일이어야 하며 확장자가 .dacpac여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-174">The DAC package must be a valid DAC package file and must have a .dacpac extension.</span></span> <span data-ttu-id="824d8-175">DAC 패키지의 DAC 애플리케이션 이름이 현재 DAC의 애플리케이션 이름과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-175">The DAC application name in the DAC package must be the same as the application name of the current DAC.</span></span>  
  
 <span data-ttu-id="824d8-176">**DAC 패키지** - 새 버전의 데이터 계층 애플리케이션이 포함된 DAC 패키지의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-176">**DAC Package** - Specify the path and file name of the DAC package that contains the new version of the data-tier application.</span></span> <span data-ttu-id="824d8-177">입력란 오른쪽의 **찾아보기** 단추를 선택하여 DAC 패키지의 위치를 찾아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-177">You can select the **Browse** button at the right of the box to browse to the location of the DAC package.</span></span>  
  
 <span data-ttu-id="824d8-178">**애플리케이션 이름** - DAC를 만들거나 데이터베이스에서 추출할 때 할당된 DAC 애플리케이션 이름을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-178">**Application Name** - A read-only box that displays the DAC application name assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="824d8-179">**버전** - DAC를 만들거나 데이터베이스에서 추출할 때 할당된 버전을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-179">**Version** - A read-only box that displays the version assigned when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="824d8-180">**설명** - DAC를 만들거나 데이터베이스에서 추출할 때 작성된 설명을 표시하는 읽기 전용 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-180">**Description** - A read-only box that displays the description written when the DAC was authored or extracted from a database.</span></span>  
  
 <span data-ttu-id="824d8-181">\*\* \< 이전\*\* - **소개** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-181">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="824d8-182">**다음 >** - 선택한 파일이 유효한 DAC 패키지인지 마법사에서 확인하는 동안 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-182">**Next >** - Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span>  
  
 <span data-ttu-id="824d8-183">**취소** - DAC를 업그레이드하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-183">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
### <a name="validating-the-dac-package"></a><span data-ttu-id="824d8-184">DAC 패키지 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="824d8-184">Validating the DAC Package</span></span>  
 <span data-ttu-id="824d8-185">선택한 파일이 유효한 DAC 패키지인지 마법사에서 확인하는 동안 진행률 표시줄이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-185">Displays a progress bar as the wizard confirms that the selected file is a valid DAC package.</span></span> <span data-ttu-id="824d8-186">DAC 패키지의 유효성이 확인되면 마법사는 **정책 검토** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-186">If the DAC package is validated, the wizard proceeds to the **Review Policy** page.</span></span> <span data-ttu-id="824d8-187">파일이 유효한 DAC 패키지가 아닌 경우 마법사는 **DAC 패키지 선택** 페이지에서 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-187">If the file is not a valid DAC package, the wizard remains on the **Select DAC Package** page.</span></span> <span data-ttu-id="824d8-188">이 경우 다른 유효한 DAC 패키지를 선택하거나 마법사를 취소하고 새 DAC 패키지를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-188">Either select another valid DAC package or cancel the wizard and generate a new DAC package.</span></span>  
  
 <span data-ttu-id="824d8-189">**DAC 내용의 유효성을 검사하고 있습니다** - 유효성 검사의 현재 상태를 보고하는 진행률 표시줄입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-189">**Validating the contents of the DAC** - The progress bar that reports the current status of the validation process.</span></span>  
  
 <span data-ttu-id="824d8-190">\*\* \< 이전\*\* - **패키지 선택** 페이지의 초기 상태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-190">**\< Previous** - Returns to the initial state of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="824d8-191">**다음 >** - **패키지 선택** 페이지의 최종 버전으로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-191">**Next >** - Proceeds to the final version of the **Select Package** page.</span></span>  
  
 <span data-ttu-id="824d8-192">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-192">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-policy-page"></a><a name="Review_policy"></a> <span data-ttu-id="824d8-193">정책 검토 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-193">Review Policy Page</span></span>  
 <span data-ttu-id="824d8-194">DAC에 정책이 있는 경우 이 페이지를 사용하여 DAC 서버 선택 정책을 평가한 결과를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-194">Use this page to review the results of evaluating the DAC server selection policy, if the DAC has a policy.</span></span> <span data-ttu-id="824d8-195">DAC 서버 선택 정책은 선택적이며 Microsoft Visual Studio에서 DAC를 작성하면 여기에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-195">The DAC server selection policy is optional, and is assigned to a DAC authored in Microsoft Visual Studio.</span></span> <span data-ttu-id="824d8-196">정책에서는 서버 선택 정책 패싯을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스가 DAC를 호스팅하기 위해 충족해야 하는 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-196">The policy uses the server selection policy facets to specify conditions an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] should meet to host the DAC.</span></span>  
  
 <span data-ttu-id="824d8-197">**정책 조건의 평가 결과** - DAC 서버 선택 정책의 조건에 대한 평가가 성공했는지 보여 주는 읽기 전용 보고서입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-197">**Evaluation results of policy conditions** - A read-only report showing whether the evaluations of the conditions in the DAC server selection policy succeeded.</span></span> <span data-ttu-id="824d8-198">각 조건을 평가한 결과가 별도의 행에 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-198">The results of evaluating each condition are reported on a separate line.</span></span>  
  
 <span data-ttu-id="824d8-199">**정책 위반을 무시합니다.** - 정책 조건이 한 개 이상 실패하더라도 배포를 진행하려면 이 확인란을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-199">**Ignore policy violations** - Use this check box to proceed with the upgrade if one or more of the policy conditions failed.</span></span> <span data-ttu-id="824d8-200">실패한 모든 조건이 DAC 작동에 영향을 주지 않는 것이 확실한 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-200">Only select this option if you are sure that all of the conditions which failed will not prevent the successful operation of the DAC.</span></span>  
  
 <span data-ttu-id="824d8-201">\*\* \< 이전\*\* - **패키지 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-201">**\< Previous** - Returns to the **Select Package** page.</span></span>  
  
 <span data-ttu-id="824d8-202">**다음 >** - **변경 내용 검색** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-202">**Next >** - Proceeds to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="824d8-203">**취소** - DAC를 업그레이드하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-203">**Cancel** - Terminates the wizard without upgrading the DAC.</span></span>  
  
##  <a name="detect-change-page"></a><a name="Detect_change"></a> <span data-ttu-id="824d8-204">변경 내용 검색 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-204">Detect Change Page</span></span>  
 <span data-ttu-id="824d8-205">이 페이지를 사용하여 **msdb**의 DAC 메타데이터에 저장된 스키마 정의와 스키마가 다른 데이터베이스 변경 내용에 대해 마법사가 확인한 결과를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-205">Use this page reports the results of the wizards check for changes made to the database that make it's schema different than the schema definition stored in the DAC metadata in **msdb**.</span></span> <span data-ttu-id="824d8-206">예를 들어 DAC를 배포한 후에 CREATE, ALTER 또는 DROP 문을 사용하여 데이터베이스에 개체를 추가, 변경 또는 제거했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-206">For example, if CREATE, ALTER, or DROP statements have been used to add, change, or remove objects from the database after the DAC was originally deployed.</span></span> <span data-ttu-id="824d8-207">페이지에 먼저 진행률 표시줄이 표시된 다음 보고서의 분석 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-207">The page first displays a progress bar, and then reports the results of the analysis.</span></span>  
  
 <span data-ttu-id="824d8-208">**변경 내용을 검색하고 있습니다. 몇 분 정도 걸릴 수 있습니다.** - 마법사가 데이터베이스의 현재 스키마와 DAC 정의의 개체 간의 차이를 분석하는 동안 진행률 표시줄을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-208">**Detecting change, this may take a few minutes** - Displays a progress bar as the wizard checks for differences between the current schema of the database and the objects in the DAC definition.</span></span>  
  
 <span data-ttu-id="824d8-209">**변경 내용 검색 결과:** - 분석이 완료되었음을 나타내고 아래에 결과를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-209">**Change detection results:** - Indicates that the analysis has completed and the results are reported below.</span></span>  
  
 <span data-ttu-id="824d8-210">**데이터베이스 DatabaseName이 변경되지 않았습니다.** - 마법사가 데이터베이스에 정의된 개체와 DAC 정의의 해당 항목 간에 차이를 검색하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-210">**The database DatabaseName has not changed** - The wizard detected no differences in the objects defined in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="824d8-211">**데이터베이스 DatabaseName이 변경되었습니다.** - 마법사가 데이터베이스에 정의된 개체와 DAC 정의의 해당 항목 간에 차이를 검색했습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-211">**The database DatabaseName has changed** - The wizard detected changes between the objects in the database and their counterparts in the DAC definition.</span></span>  
  
 <span data-ttu-id="824d8-212">**변경 내용이 손실되더라도 계속합니다.** - 현재 데이터베이스의 개체나 데이터 일부가 새 데이터베이스에 누락될 수 있음을 이해하고 업그레이드를 계속하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-212">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="824d8-213">변경 내용 보고서를 분석했으며 새 데이터베이스에 필요한 개체나 데이터를 수동으로 전송하는 데 필요한 단계를 이해하는 경우에만 이 단추를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-213">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="824d8-214">확실하지 않은 경우에는 **보고서 저장** 단추를 클릭하여 보고서를 저장하고 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-214">If you are not sure, click the **Save Report** button to save the change report, then click **Cancel**.</span></span> <span data-ttu-id="824d8-215">보고서를 분석하고 업그레이드 완료 후에 필요한 개체와 데이터를 전송하는 방법을 계획한 다음 마법사를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-215">Analyze the report, plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="824d8-216">**보고서 저장** - 마법사가 데이터베이스의 개체와 DAC 정의의 해당 항목 간에 검색한 변경 내용에 대한 보고서를 저장하려면 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-216">**Save Report** - Click the button to save a report of the changes the wizard detected between the objects in the database and their counterparts in the DAC definition.</span></span> <span data-ttu-id="824d8-217">그런 다음 보고서를 검토하여 업그레이드 완료 후에 보고서에 나열된 개체 일부나 전부를 새 데이터베이스에 통합하기 위한 동작을 수행해야 하는지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-217">You can then review the report to determine if you need to take actions after the upgrade completes to incorporate some or all of the objects listed in the report into the new database.</span></span>  
  
 <span data-ttu-id="824d8-218">\*\* \< 이전\*\* - **DAC 패키지 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-218">**\< Previous** - Returns to the **Select DAC Package** page.</span></span>  
  
 <span data-ttu-id="824d8-219">**다음 >** - **옵션** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-219">**Next >** - Proceeds to the **Options** page.</span></span>  
  
 <span data-ttu-id="824d8-220">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-220">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
## <a name="options-page"></a><span data-ttu-id="824d8-221">옵션 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-221">Options Page</span></span>  
 <span data-ttu-id="824d8-222">이 페이지를 사용하여 업그레이드에 대한 실패 시 롤백 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-222">Use this page to select the rollback on failure option for the upgrade.</span></span>  
  
 <span data-ttu-id="824d8-223">**오류 발생 시 롤백** - 오류가 발생할 경우에 마법사에서 롤백을 시도할 수 있는 트랜잭션에 업그레이드를 포함하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-223">**Rollback on failure** - Select this option to enclose the upgrade in a transaction which the wizard can attempt to roll back if errors occur.</span></span> <span data-ttu-id="824d8-224">이 옵션에 대한 자세한 내용은 [DAC 업그레이드 옵션 선택](#ChoseDACUpgOptions)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="824d8-224">For more information about the option, see [Choosing DAC Upgrade Options](#ChoseDACUpgOptions).</span></span>  
  
 <span data-ttu-id="824d8-225">**기본값 복원** - 기본 설정인 false로 옵션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-225">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="824d8-226">\*\* \< 이전\*\* - **변경 내용 검색** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-226">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="824d8-227">**다음>** - **업그레이드 계획 검토** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-227">**Next >** - Proceeds to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="824d8-228">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-228">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="review-the-upgrade-plan-page"></a><a name="ReviewUpgPlan"></a> <span data-ttu-id="824d8-229">업그레이드 계획 검토 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-229">Review the Upgrade Plan Page</span></span>  
 <span data-ttu-id="824d8-230">이 페이지를 사용하여 업그레이드 프로세스에서 수행할 동작을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-230">Use this page to do review the actions that will be taken by the upgrade process.</span></span> <span data-ttu-id="824d8-231">업그레이드가 문제를 만들지 않을 거라고 확신하는 경우에만 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-231">Only proceed when you are confident the upgrade will not create problems.</span></span>  
  
 <span data-ttu-id="824d8-232">**DAC를 업그레이드하는 데 사용되는 동작은 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="824d8-232">**The following actions will be used to upgrade the DAC.**</span></span> <span data-ttu-id="824d8-233">- 표시된 정보를 검토하여 수행할 동작이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-233">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="824d8-234">**동작** 열에서는 Transact-SQL 문과 같은 동작을 표시하고 업그레이드를 수행하기 위해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-234">The **Action** column displays the actions, such as Transact-SQL statements, that will be run to perform the upgrade.</span></span> <span data-ttu-id="824d8-235">연결된 동작으로 인해 데이터가 삭제될 수 있는 경우 **데이터 손실** 열에 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-235">The **Data Loss** column will contain a warning if the associated action could delete data.</span></span>  
  
 <span data-ttu-id="824d8-236">**새로 고침** – 동작 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-236">**Refresh** - refreshes the action list.</span></span>  
  
 <span data-ttu-id="824d8-237">**동작 보고서 저장** – 동작 창의 콘텐츠를 HTML 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-237">**Save Action Report** - saves the contents of the action window to an HTML file.</span></span>  
  
 <span data-ttu-id="824d8-238">**변경 내용이 손실되더라도 계속합니다.** - 현재 데이터베이스의 개체나 데이터 일부가 새 데이터베이스에 누락될 수 있음을 이해하고 업그레이드를 계속하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-238">**Proceed despite possible loss of changes** - Specifies that you understand some of the objects or data in the current database will not be present in the new database, and that you are willing to proceed with the upgrade.</span></span> <span data-ttu-id="824d8-239">변경 내용 보고서를 분석했으며 새 데이터베이스에 필요한 개체나 데이터를 수동으로 전송하는 데 필요한 단계를 이해하는 경우에만 이 단추를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-239">You should select this button only if you have analyzed the change report and understand the steps you must perform to manually transfer any objects or data required in the new database.</span></span> <span data-ttu-id="824d8-240">확실하지 않은 경우에는 **동작 보고서 저장** 단추를 클릭하여 변경 보고서를 저장하고 **스크립트 저장** 단추로 Transact-SQL 스크립트를 저장한 다음 **취소**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-240">If you are not sure, click the **Save Action Report** button to save the change report and the **Save Scripts** button to save the Transact-SQL script, then click **Cancel**.</span></span> <span data-ttu-id="824d8-241">보고서와 스크립트를 분석하고 업그레이드를 완료하고 마법사를 다시 시작한 이후에 필요한 개체와 데이터를 전송하는 방법을 계획합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-241">Analyze the report and script, and then plan how to transfer any required objects and data after the upgrade completes, then restart the wizard.</span></span>  
  
 <span data-ttu-id="824d8-242">**스크립트 저장** - 텍스트 파일로 업그레이드를 수행하는 데 사용될 Transact-SQL 문을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-242">**Save Scripts** - saves the Transact-SQL statements that will be used to perform the upgrade to a text file.</span></span>  
  
 <span data-ttu-id="824d8-243">**기본값 복원** - 기본 설정인 false로 옵션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-243">**Restore Defaults** - Returns the option to its default setting of false.</span></span>  
  
 <span data-ttu-id="824d8-244">\*\* \< 이전\*\* - **변경 내용 검색** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-244">**\< Previous** - Returns to the **Detect Change** page.</span></span>  
  
 <span data-ttu-id="824d8-245">**다음 >** - **요약** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-245">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="824d8-246">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-246">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="824d8-247">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-247">Summary Page</span></span>  
 <span data-ttu-id="824d8-248">이 페이지에서는 DAC를 업그레이드할 때 마법사에서 수행할 동작을 최종적으로 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-248">Use this page to do a final review of the actions the wizard will take when upgrading the DAC.</span></span>  
  
 <span data-ttu-id="824d8-249">**DAC를 업그레이드하는 데 사용되는 설정은 다음과 같습니다.**</span><span class="sxs-lookup"><span data-stu-id="824d8-249">**The following settings will be used to upgrade your DAC.**</span></span> <span data-ttu-id="824d8-250">- 표시된 정보를 검토하여 수행할 동작이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-250">- Review the information displayed to ensure the actions taken will be correct.</span></span> <span data-ttu-id="824d8-251">창에는 업그레이드하도록 선택한 DAC, 새 버전의 DAC를 포함하는 DAC 패키지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-251">The window displays the DAC you selected to be upgraded, and the DAC package containing the new version of the DAC.</span></span> <span data-ttu-id="824d8-252">창에는 데이터베이스의 현재 버전이 현재 DAC 정의와 동일한지 또는 데이터베이스가 변경되었는지도 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-252">The window also displays whether the current version of the database is the same as the current DAC definition, or if the database has changed.</span></span>  
  
 <span data-ttu-id="824d8-253">\*\* \< 이전\*\* - **업그레이드 계획 검토** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-253">**\< Previous** - Returns you to the **Review the Upgrade Plan** page.</span></span>  
  
 <span data-ttu-id="824d8-254">**다음 >** - DAC를 배포하고 **DAC 업그레이드** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-254">**Next >** - Deploys the DAC and displays the results in the **Upgrade DAC** page.</span></span>  
  
 <span data-ttu-id="824d8-255">**취소** - DAC를 배포하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-255">**Cancel** - Terminates the wizard without deploying the DAC.</span></span>  
  
##  <a name="upgrade-dac-page"></a><a name="Upgrade"></a> <span data-ttu-id="824d8-256">DAC 업그레이드 페이지</span><span class="sxs-lookup"><span data-stu-id="824d8-256">Upgrade DAC Page</span></span>  
 <span data-ttu-id="824d8-257">이 페이지에서는 업그레이드 작업의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-257">This page reports the success or failure of the upgrade operation.</span></span>  
  
 <span data-ttu-id="824d8-258">**DAC를 업그레이드하고 있습니다.** - DAC를 업그레이드하기 위해 수행한 각 동작의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-258">**Upgrading the DAC** - Reports the success or failure of each action taken to upgrade the DAC.</span></span> <span data-ttu-id="824d8-259">정보를 검토하여 각 동작의 성공 또는 실패를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-259">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="824d8-260">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-260">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="824d8-261">링크를 선택하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-261">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="824d8-262">**보고서 저장** - 업그레이드 보고서를 HTML 파일로 저장하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-262">**Save Report** - Select this button to save the upgrade report to an HTML file.</span></span> <span data-ttu-id="824d8-263">파일은 모든 동작에서 생성된 모든 오류를 비롯하여 각 동작의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-263">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="824d8-264">기본 폴더는 Windows 계정의 Documents 폴더 아래의 SQL Server Management Studio\DAC Packages 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-264">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="824d8-265">**마침** - 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-265">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="using-powershell"></a><a name="UpgradeDACPowerShell"></a> <span data-ttu-id="824d8-266">PowerShell 사용</span><span class="sxs-lookup"><span data-stu-id="824d8-266">Using PowerShell</span></span>  
 <span data-ttu-id="824d8-267">**PowerShell 스크립트에서 IncrementalUpgrade() 메서드를 사용하여 DAC를 업그레이드하려면**</span><span class="sxs-lookup"><span data-stu-id="824d8-267">**To upgrade a DAC using the IncrementalUpgrade() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="824d8-268">SMO Server 개체를 만든 다음 업그레이드할 DAC를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-268">Create a SMO Server object and set it to the instance that contains the DAC to be upgraded.</span></span>  
  
2.  <span data-ttu-id="824d8-269">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-269">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="824d8-270">`System.IO.File`을 사용하여 DAC 패키지 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-270">Use `System.IO.File` to load the DAC package file.</span></span>  
  
4.  <span data-ttu-id="824d8-271">`add_DacActionStarted` 및 `add_DacActionFinished`를 사용하여 DAC 업그레이드 이벤트에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-271">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
5.  <span data-ttu-id="824d8-272">`DacUpgradeOptions`를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-272">Set the `DacUpgradeOptions`.</span></span>  
  
6.  <span data-ttu-id="824d8-273">`IncrementalUpgrade` 메서드를 사용하여 DAC를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-273">Use the `IncrementalUpgrade` method to upgrade the DAC.</span></span>  
  
7.  <span data-ttu-id="824d8-274">DAC 패키지 파일을 읽는 데 사용되는 파일 스트림을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-274">Close the file stream used to read the DAC package file.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="824d8-275">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="824d8-275">Example (PowerShell)</span></span>  
 <span data-ttu-id="824d8-276">다음 예에서는 MyApplicationVNext.dacpac 패키지의 새 DAC 버전을 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)]의 기본 인스턴스에서 MyApplicaiton이라는 DAC를 업그레이드합니다.</span><span class="sxs-lookup"><span data-stu-id="824d8-276">The following example upgrades a DAC named MyApplication on a default instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], using a new DAC version in a MyApplicationVNext.dacpac package.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Load the DAC package file.  
$dacpacPath = "C:\MyDACs\MyApplicationVNext.dacpac"  
$fileStream = [System.IO.File]::Open($dacpacPath,[System.IO.FileMode]::OpenOrCreate)  
$dacType = [Microsoft.SqlServer.Management.Dac.DacType]::Load($fileStream)  
  
## Subscribe to the DAC upgrade events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Upgrade the DAC and close the package.  
$dacName  = "MyApplication"  
  
## Set the upgrade options.  
$upgradeProperties = New-Object Microsoft.SqlServer.Management.Dac.DacUpgradeOptions  
$upgradeProperties.blockonchanges = $true  
$upgradeProperties.ignoredataloss = $false  
$upgradeProperties.rollbackonfailure = $true  
$ upgradeProperties.skippolicyvalidation = $false  
  
## Upgrade the DAC  
$dacstore.IncrementalUpgrade($dacName, $dacType, $upgradeProperties)  
## Close the package file.  
$fileStream.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="824d8-277">참고 항목</span><span class="sxs-lookup"><span data-stu-id="824d8-277">See Also</span></span>  
 <span data-ttu-id="824d8-278">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="824d8-278">[Data-tier Applications](data-tier-applications.md) </span></span>  
 [<span data-ttu-id="824d8-279">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="824d8-279">SQL Server PowerShell</span></span>](../../powershell/sql-server-powershell.md)  
