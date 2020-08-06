---
title: DAC로 데이터베이스 등록 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4e8061362d013dbfbd6cbaba47d0f2cb4d8e83b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661147"
---
# <a name="register-a-database-as-a-dac"></a><span data-ttu-id="71500-102">DAC로 데이터베이스 등록</span><span class="sxs-lookup"><span data-stu-id="71500-102">Register a Database As a DAC</span></span>
  <span data-ttu-id="71500-103">**데이터 계층 응용 프로그램 등록 마법사** 또는 Windows PowerShell 스크립트를 사용 하 여 기존 데이터베이스의 개체를 설명 하는 dac (데이터 계층 응용 프로그램) 정의를 작성 하 고 `msdb` 시스템 데이터베이스 (의**master** )에 dac 정의를 등록할 수 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-103">Use either the **Register Data-tier Application Wizard** or a Windows PowerShell script to build a data-tier application (DAC) definition that describes the objects in an existing database, and register the DAC definition in the `msdb` system database (**master** in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]).</span></span>  
  
-   <span data-ttu-id="71500-104">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="71500-104">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="71500-105">**DAC를 업그레이드하려면 다음을 사용합니다.**  [데이터 계층 애플리케이션 등록 마법사](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="71500-105">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="71500-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="71500-106">Before You Begin</span></span>  
 <span data-ttu-id="71500-107">등록 프로세스에서는 데이터베이스의 개체를 정의하는 DAC 정의를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="71500-107">The registration process creates a DAC definition that defines the objects in the database.</span></span> <span data-ttu-id="71500-108">DAC 정의와 데이터베이스의 결합으로 DAC 인스턴스가 형성됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-108">The combination of the DAC definition and the database form a DAC instance.</span></span> <span data-ttu-id="71500-109">DAC를 데이터베이스 엔진의 관리되는 인스턴스에 DAC로 등록할 경우 등록된 DAC는 유틸리티 컬렉션 집합이 인스턴스에서 유틸리티 제어 지점으로 다음에 전송될 때 SQL Server 유틸리티에 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-109">If you register a database as a DAC on a managed instance of the Database Engine, the registered DAC will be incorporated into the SQL Server Utility the next time the utility collection set is sent from the instance to the Utility Control Point.</span></span> <span data-ttu-id="71500-110">그러면 DAC가 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **유틸리티 탐색기**의 **배포된 데이터 계층 애플리케이션 노드**에 표시되고 **배포된 데이터 계층 애플리케이션** 세부 정보 페이지에 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-110">The DAC will then be present in the **Deployed Data-tier Applications** node of the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Utility Explorer** and reported in the **Deployed Data-tier Applications** details page.</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="71500-111">제한 사항</span><span class="sxs-lookup"><span data-stu-id="71500-111">Limitations and Restrictions</span></span>  
 <span data-ttu-id="71500-112">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4(서비스 팩 4) 이상의 데이터베이스에서만 DAC 등록을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-112">DAC registration can only be performed on a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="71500-113">DAC가 데이터베이스에 이미 등록된 경우에는 DAC 등록을 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-113">DAC registration cannot be performed if a DAC is already registered for the database.</span></span> <span data-ttu-id="71500-114">예를 들어 데이터베이스가 DAC를 배포하는 방식으로 만들어진 경우 **데이터 계층 애플리케이션 등록 마법사**를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-114">For example, if the database was created by deploying a DAC, you cannot run the **Register Data-tier Application Wizard**.</span></span>  
  
 <span data-ttu-id="71500-115">DAC 또는 포함된 사용자가 지원하지 않는 개체가 데이터베이스에 있는 경우 DAC를 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-115">You cannot register a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="71500-116">DAC에서 지원되는 개체 유형에 대한 자세한 내용은 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71500-116">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="71500-117">권한</span><span class="sxs-lookup"><span data-stu-id="71500-117">Permissions</span></span>  
 <span data-ttu-id="71500-118">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 DAC를 등록하려면 하나 이상의 ALTER ANY LOGIN과 데이터베이스 범위 VIEW DEFINITION 권한, **sys.sql_expression_dependencies**에 대한 SELECT 권한 및 **dbcreator** 고정 서버 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-118">Registering a DAC in an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, SELECT permissions on **sys.sql_expression_dependencies**, and membership in the **dbcreator** fixed server role.</span></span> <span data-ttu-id="71500-119">**sysadmin** 고정 서버 역할의 멤버 또는 기본 제공 SQL Server 시스템 관리자 계정인 **sa** 도 DAC를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-119">Members of the **sysadmin** fixed server role or the built-in SQL Server system administrator account named **sa** can also register a DAC.</span></span> <span data-ttu-id="71500-120">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 로그인이 없는 DAC를 등록하려면 **dbmanager** 또는 **serveradmin** 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-120">Registering a DAC that does not contain logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **dbmanager** or **serveradmin** roles.</span></span> <span data-ttu-id="71500-121">[!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 로그인이 있는 DAC를 등록하려면 **loginmanager** 또는 **serveradmin** 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-121">Registering a DAC that contains logins in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requires membership in the **loginmanager** or **serveradmin** roles.</span></span>  
  
##  <a name="using-the-register-data-tier-application-wizard"></a><a name="UsingRegisterDACWizard"></a> <span data-ttu-id="71500-122">데이터 계층 애플리케이션 등록 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="71500-122">Using the Register Data-tier Application Wizard</span></span>  
 <span data-ttu-id="71500-123">**마법사를 사용하여 DAC를 등록하려면**</span><span class="sxs-lookup"><span data-stu-id="71500-123">**To Register a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="71500-124">**개체 탐색기**에서 DAC로 등록할 데이터베이스가 포함된 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-124">In **Object Explorer**, expand the node for the instance containing the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="71500-125">**데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="71500-126">등록할 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **태스크**를 가리킨 다음, **데이터 계층 애플리케이션으로 등록...** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-126">Right-click the database to be registered, point to **Tasks**, and then select **Register As Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="71500-127">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="71500-128">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="71500-129">속성 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-129">Set Properties Page</span></span>](#Set_properties)  
  
    3.  [<span data-ttu-id="71500-130">유효성 검사 및 요약 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-130">Validation and Summary Page</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="71500-131">DAC 등록 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-131">Register DAC Page</span></span>](#Register)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="71500-132">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-132">Introduction Page</span></span>  
 <span data-ttu-id="71500-133">이 페이지에서는 데이터 계층 애플리케이션을 등록하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-133">This page describes the steps for registering a data-tier application.</span></span>  
  
 <span data-ttu-id="71500-134">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="71500-134">**Do not show this page again.**</span></span> <span data-ttu-id="71500-135">- 앞으로 이 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-135">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="71500-136">**다음 >** - **속성 설정** 페이지로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-136">**Next >** - Proceeds to the **Set Properties** page.</span></span>  
  
 <span data-ttu-id="71500-137">**취소** - DAC를 등록하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-137">**Cancel** - Terminates the wizard without registering a DAC.</span></span>  
  
##  <a name="set-properties-page"></a><a name="Set_properties"></a> <span data-ttu-id="71500-138">속성 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-138">Set Properties Page</span></span>  
 <span data-ttu-id="71500-139">이 페이지를 사용하여 애플리케이션 이름 및 버전과 같은 DAC 수준 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-139">Use this page to specify DAC-level properties such as the application name and version.</span></span>  
  
 <span data-ttu-id="71500-140">**애플리케이션 이름.**</span><span class="sxs-lookup"><span data-stu-id="71500-140">**Application name.**</span></span> <span data-ttu-id="71500-141">- DAC 정의를 식별하는 데 사용되는 이름을 지정하는 문자열입니다. 이 필드는 데이터베이스 이름으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="71500-141">- A string that specifies the name used to identify the DAC definition, the field is been populated with the database name.</span></span>  
  
 <span data-ttu-id="71500-142">**버전.**</span><span class="sxs-lookup"><span data-stu-id="71500-142">**Version.**</span></span> <span data-ttu-id="71500-143">- DAC의 버전을 식별하는 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-143">- A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="71500-144">DAC 버전은 Visual Studio에서 개발자가 작업 중인 DAC의 버전을 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-144">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="71500-145">DAC를 배포 하는 경우 버전은 데이터베이스에 저장 되 `msdb` 고 나중에의 **데이터 계층 응용 프로그램** 노드에서 볼 수 있습니다 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71500-145">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="71500-146">**설명**</span><span class="sxs-lookup"><span data-stu-id="71500-146">**Description.**</span></span> <span data-ttu-id="71500-147">- 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-147">- Optional.</span></span> <span data-ttu-id="71500-148">DAC의 용도를 설명하는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-148">Text that explains the purpose of the DAC.</span></span> <span data-ttu-id="71500-149">DAC를 배포할 때 설명은 데이터베이스에 저장 `msdb` 되며 나중에의 **데이터 계층 응용 프로그램** 노드에서 볼 수 있습니다 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71500-149">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="71500-150">\*\* \< 이전\*\* - **소개** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="71500-150">**\< Previous** - Returns you to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="71500-151">**다음 >** - 데이터베이스의 개체로 DAC를 작성할 수 있는지 확인하고 **유효성 검사 및 요약** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-151">**Next >** - Verifies that a DAC can be built from the objects in the database, and displays the results in the **Validation and Summary** page.</span></span>  
  
 <span data-ttu-id="71500-152">**취소** - DAC를 등록하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-152">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="validation-and-summary-page"></a><a name="Summary"></a> <span data-ttu-id="71500-153">유효성 검사 및 요약 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-153">Validation and Summary Page</span></span>  
 <span data-ttu-id="71500-154">이 페이지를 사용하여 DAC를 등록할 때 마법사가 수행할 동작을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-154">Use this page to review the actions the wizard will take when registering the DAC.</span></span> <span data-ttu-id="71500-155">이 페이지는 데이터베이스의 개체로 DAC를 작성할 수 있는지 확인할 때 세 가지 상태로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-155">The page transitions through three states as it verifies that a DAC can be built from the objects in the database.</span></span>  
  
### <a name="retrieving-objects"></a><span data-ttu-id="71500-156">개체 검색</span><span class="sxs-lookup"><span data-stu-id="71500-156">Retrieving Objects</span></span>  
 <span data-ttu-id="71500-157">**데이터베이스 및 서버 개체 검색**</span><span class="sxs-lookup"><span data-stu-id="71500-157">**Retrieving database and server objects.**</span></span> <span data-ttu-id="71500-158">- 마법사가 데이터베이스의 모든 필요한 개체 및 데이터베이스 엔진의 인스턴스를 검색할 때 진행률 표시줄을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-158">- Displays a progress bar as the wizard retrieves all of the required objects from the database and the instance of the Database Engine.</span></span>  
  
 <span data-ttu-id="71500-159">\*\* \< 이전\*\* -항목을 변경 하기 위한 **속성 설정** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="71500-159">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="71500-160">**다음 >** - DAC를 등록하고 **DAC 등록** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-160">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="71500-161">**취소** - DAC를 등록하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-161">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="validating-objects"></a><span data-ttu-id="71500-162">개체 유효성 확인</span><span class="sxs-lookup"><span data-stu-id="71500-162">Validating Objects</span></span>  
 <span data-ttu-id="71500-163">**검사 중**: _SchemaName_ **.**</span><span class="sxs-lookup"><span data-stu-id="71500-163">**Checking**  _SchemaName_ **.**</span></span> <span data-ttu-id="71500-164">_ObjectName_ **.**</span><span class="sxs-lookup"><span data-stu-id="71500-164">_ObjectName_ **.**</span></span> <span data-ttu-id="71500-165">- 마법사가 검색된 개체의 종속성을 확인하고 모두 DAC에 유효한 개체인지 확인할 때 진행률 표시줄을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-165">- Displays a progress bar as the wizard verifies the dependencies of the retrieved objects, and verifies that they are all valid objects for a DAC.</span></span> <span data-ttu-id="71500-166">_SchemaName_ **.** _ObjectName_ 은 현재 확인 중인 개체가 무엇인지 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-166">_SchemaName_**.**_ObjectName_ identify which object is currently being verified.</span></span>  
  
 <span data-ttu-id="71500-167">\*\* \< 이전\*\* -항목을 변경 하기 위한 **속성 설정** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="71500-167">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="71500-168">**다음 >** - DAC를 등록하고 **DAC 등록** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-168">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="71500-169">**취소** - DAC를 등록하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-169">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
### <a name="summary"></a><span data-ttu-id="71500-170">요약</span><span class="sxs-lookup"><span data-stu-id="71500-170">Summary</span></span>  
 <span data-ttu-id="71500-171">**다음 설정이 DAC를 등록하는 데 사용됩니다.**</span><span class="sxs-lookup"><span data-stu-id="71500-171">**The following setting will be used to register your DAC.**</span></span> <span data-ttu-id="71500-172">- DAC에 포함될 속성 및 개체에 대한 보고서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-172">- Displays a report of the properties and objects that will be included in the DAC.</span></span>  
  
 <span data-ttu-id="71500-173">**보고서 저장** - 유효성 검사 보고서의 복사본을 HTML 파일로 저장하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-173">**Save Report** - Select this button to save a copy of the validation report to an HTML file.</span></span> <span data-ttu-id="71500-174">기본 폴더는 Windows 계정의 Documents 폴더에 있는 **SQL Server Management Studio\DAC Packages** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-174">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span>  
  
 <span data-ttu-id="71500-175">\*\* \< 이전\*\* -항목을 변경 하기 위한 **속성 설정** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="71500-175">**\< Previous** - Returns you to the **Set Properties** page to change your entries.</span></span>  
  
 <span data-ttu-id="71500-176">**다음 >** - DAC를 등록하고 **DAC 등록** 페이지에 결과를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-176">**Next >** - Registers the DAC and displays the results in the **Register DAC** page.</span></span>  
  
 <span data-ttu-id="71500-177">**취소** - DAC를 등록하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-177">**Cancel** - Terminates the wizard without registering the DAC.</span></span>  
  
##  <a name="register-dac-page"></a><a name="Register"></a> <span data-ttu-id="71500-178">DAC 등록 페이지</span><span class="sxs-lookup"><span data-stu-id="71500-178">Register DAC Page</span></span>  
 <span data-ttu-id="71500-179">이 페이지에서는 등록의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-179">This page reports the success or failure of the registration.</span></span>  
  
 <span data-ttu-id="71500-180">**DAC 등록** - DAC를 등록하기 위해 수행한 각 동작의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-180">**Registering the DAC** - Reports the success or failure of each action taken to register the DAC.</span></span> <span data-ttu-id="71500-181">정보를 검토하여 각 동작의 성공 또는 실패를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-181">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="71500-182">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71500-182">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="71500-183">링크를 선택하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="71500-183">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="71500-184">**보고서 저장** - 등록 보고서를 HTML 파일로 저장하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-184">**Save Report** - Select this button to save the registration report to an HTML file.</span></span> <span data-ttu-id="71500-185">파일은 모든 동작에서 생성된 모든 오류를 비롯하여 각 동작의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-185">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="71500-186">기본 폴더는 Windows 계정의 Documents 폴더에 있는 **SQL Server Management Studio\DAC Packages** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-186">The default folder is a **SQL Server Management Studio\DAC Packages** folder in the Documents folder of your Windows account.</span></span> <span data-ttu-id="71500-187">파일 이름은 \<DACPackageName>_RegisterDACReport_yyyymmdd.html 형식입니다. 여기서 \<*DACPackageName*>은 배포되는 패키지의 이름이고, *yyyy* = 현재 연도, *mm* = 현재 월, *dd* = 현재 날짜입니다.</span><span class="sxs-lookup"><span data-stu-id="71500-187">The file name is in the format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, where \<*DACPackageName*> is the name of the package being deployed, *yyyy* = the current year, *mm* = the current month, and *dd* = the current day.</span></span>  
  
 <span data-ttu-id="71500-188">**마침** - 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-188">**Finish** - Terminates the wizard.</span></span>  
  
##  <a name="register-a-dac-using-powershell"></a><a name="RegisterDACPowerShell"></a> <span data-ttu-id="71500-189">PowerShell을 사용하여 DAC 등록</span><span class="sxs-lookup"><span data-stu-id="71500-189">Register a DAC Using PowerShell</span></span>  
 <span data-ttu-id="71500-190">**PowerShell 스크립트에서 Register() 메서드를 사용하여 데이터베이스를 DAC로 등록하려면**</span><span class="sxs-lookup"><span data-stu-id="71500-190">**To register a database as a DAC using the Register() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="71500-191">SMO Server 개체를 만든 후 이 개체를 DAC로 등록할 데이터베이스를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-191">Create a SMO Server object and set it to the instance that contains the database to be registered as a DAC.</span></span>  
  
2.  <span data-ttu-id="71500-192">데이터베이스의 이름을 지정하는 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-192">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="71500-193">DAC에 대한 메타데이터(예: DAC 이름, 버전 및 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-193">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="71500-194">위에서 지정한 정보로 Register 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-194">Run the Register method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="71500-195">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="71500-195">Example (PowerShell)</span></span>  
 <span data-ttu-id="71500-196">다음 예에서는 MyDB라는 데이터베이스를 DAC로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="71500-196">The following example registers a database named MyDB as a DAC.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a><span data-ttu-id="71500-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71500-197">See Also</span></span>  
 [<span data-ttu-id="71500-198">데이터 계층 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="71500-198">Data-tier Applications</span></span>](data-tier-applications.md)  
