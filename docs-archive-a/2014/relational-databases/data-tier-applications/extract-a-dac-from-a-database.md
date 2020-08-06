---
title: 데이터베이스에서 DAC 추출 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.extractdacwizard.buildandsave.f1
- sql12.swb.extractdacwizard.setdacproperties.f1
- sql12.swb.extractdacwizard.validationandsummary.f1
- sql12.swb.extractdacwizard.introduction.f1
- sql12.swb.extractdacwizard.selectdatapage.f1
helpviewer_keywords:
- extract DAC
- How to [DAC], extract
- data-tier application [SQL Server], extract
- wizard [DAC], extract
ms.assetid: ae52a723-91c4-43fd-bcc7-f8de1d1f90e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd024af9c201563773e20bae7e5fded1985abbe1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660634"
---
# <a name="extract-a-dac-from-a-database"></a><span data-ttu-id="6e902-102">데이터베이스에서 DAC 추출</span><span class="sxs-lookup"><span data-stu-id="6e902-102">Extract a DAC From a Database</span></span>
  <span data-ttu-id="6e902-103">**데이터 계층 애플리케이션 추출 마법사** 나 Windows PowerShell 스크립트를 사용하여 기존 SQL Server 데이터베이스에서 DAC(데이터 계층 애플리케이션) 패키지를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-103">Use either the **Extract Data-tier Application Wizard** or a Windows PowerShell script to extract a data-tier application (DAC) package from an existing SQL Server database.</span></span> <span data-ttu-id="6e902-104">추출이 끝나면 데이터베이스 개체의 정의 및 이와 관련된 인스턴스 수준 요소를 포함하는 DAC 패키지 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-104">The extraction process creates a DAC package file that contains definitions of the database objects and their related instance-level elements.</span></span> <span data-ttu-id="6e902-105">예를 들어 DAC 패키지 파일에는 데이터베이스 테이블, 저장 프로시저, 뷰, 사용자, 그리고 데이터베이스 사용자에 매핑되는 로그인이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-105">For example, a DAC package file contains the database tables, stored procedures, views, and users, along with the logins that map to the database users.</span></span>  
  
-   <span data-ttu-id="6e902-106">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="6e902-106">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="6e902-107">**DAC를 추출 하려면**[데이터 계층 응용 프로그램 추출 마법사](#UsingDACExtractWizard), [PowerShell](#ExtractDACPowerShell) 을 사용 합니다.  </span><span class="sxs-lookup"><span data-stu-id="6e902-107">**To extract a DAC, using:**  [The Extract Data-tier Application Wizard](#UsingDACExtractWizard), [PowerShell](#ExtractDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="6e902-108">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6e902-108">Before You Begin</span></span>  
 <span data-ttu-id="6e902-109">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]또는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 서비스 팩 4 이상의 인스턴스에 있는 데이터베이스에서 DAC를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-109">You can extract a DAC from databases residing on instances of [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 4 or later.</span></span> <span data-ttu-id="6e902-110">DAC에서 배포된 데이터베이스에 대해 추출 프로세스를 실행하는 경우 데이터베이스에서 개체 정의만 추출됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-110">If the extraction process is run against a database that was deployed from a DAC, only the definitions of the objects in the database are extracted.</span></span> <span data-ttu-id="6e902-111">프로세스는에 등록 된 DAC `msdb` (의**master** )를 참조 하지 않습니다 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6e902-111">The process does not reference the DAC registered in `msdb` (**master** in [!INCLUDE[ssSDS](../../includes/sssds-md.md)]).</span></span> <span data-ttu-id="6e902-112">추출 프로세스에서는 데이터베이스 엔진의 현재 인스턴스에 DAC 정의를 등록하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-112">The extraction process does not register the DAC definition in the current instance of the Database Engine.</span></span> <span data-ttu-id="6e902-113">DAC를 등록하는 방법은 [Register a Database As a DAC](register-a-database-as-a-dac.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e902-113">For more information about registering a DAC, see [Register a Database As a DAC](register-a-database-as-a-dac.md).</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="6e902-114">제한 사항</span><span class="sxs-lookup"><span data-stu-id="6e902-114">Limitations and Restrictions</span></span>  
 <span data-ttu-id="6e902-115">[!INCLUDE[ssSDS](../../includes/sssds-md.md)]또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4(서비스 팩 4) 이상에서만 데이터베이스에서 DAC를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-115">A DAC can only be extracted from a database in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) or later.</span></span> <span data-ttu-id="6e902-116">DAC 또는 포함된 사용자가 지원하지 않는 개체가 데이터베이스에 있는 경우 DAC를 추출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-116">You cannot extract a DAC if the database has objects that are not supported in a DAC, or contained users.</span></span> <span data-ttu-id="6e902-117">DAC에서 지원되는 개체 유형에 대한 자세한 내용은 [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e902-117">For more information about the types of objects supported in a DAC, see [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6e902-118">권한</span><span class="sxs-lookup"><span data-stu-id="6e902-118">Permissions</span></span>  
 <span data-ttu-id="6e902-119">DAC를 추출하려면 **sys.sql_expression_dependencies**에 대한 SELECT 권한뿐만 아니라 최소한 ALTER ANY LOGIN 및 데이터베이스 범위 VIEW DEFINITION 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-119">Extracting a DAC requires at least ALTER ANY LOGIN and database scope VIEW DEFINITION permissions, as well as SELECT permissions on **sys.sql_expression_dependencies**.</span></span> <span data-ttu-id="6e902-120">DAC를 추출하려면 securityadmin 고정 서버 역할의 멤버이면서 DAC를 추출하는 데이터베이스의 database_owner 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-120">Extracting a DAC can be done by members of the securityadmin fixed server role who are also members of the database_owner fixed database role in the database from which the DAC is extracted.</span></span> <span data-ttu-id="6e902-121">sysadmin 고정 서버 역할의 멤버 또는 기본 제공 SQL Server 시스템 관리자 계정인 **sa** 도 DAC를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-121">Members of the sysadmin fixed server role or the built-in SQL Server system administrator account named **sa** can also extract a DAC.</span></span>  
  
##  <a name="using-the-extract-data-tier-application-wizard"></a><a name="UsingDACExtractWizard"></a> <span data-ttu-id="6e902-122">데이터 계층 애플리케이션 추출 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="6e902-122">Using the Extract Data-tier Application Wizard</span></span>  
 <span data-ttu-id="6e902-123">**마법사를 사용하여 DAC를 추출하려면**</span><span class="sxs-lookup"><span data-stu-id="6e902-123">**To Extract a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="6e902-124">**개체 탐색기**에서 DAC를 추출할 데이터베이스가 포함된 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-124">In **Object Explorer**, expand the node for the instance containing the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="6e902-125">**데이터베이스** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-125">Expand the **Databases** node.</span></span>  
  
3.  <span data-ttu-id="6e902-126">DAC를 추출할 데이터베이스의 노드를 마우스 오른쪽 단추로 클릭 하 고 **태스크**를 가리킨 다음 **데이터 계층 응용 프로그램 추출** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-126">Right-click the node for the database from which the DAC is to be extracted, point to **Tasks**, and then select **Extract Data-tier Application...**</span></span>  
  
4.  <span data-ttu-id="6e902-127">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-127">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="6e902-128">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-128">Introduction Page</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="6e902-129">데이터 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-129">Select Data Page</span></span>](#SelectData)  
  
    3.  [<span data-ttu-id="6e902-130">속성 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-130">Set Properties Page</span></span>](#SetProperties)  
  
    4.  [<span data-ttu-id="6e902-131">유효성 검사 및 요약 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-131">Validation and Summary Page</span></span>](#ValidateSummary)  
  
    5.  [<span data-ttu-id="6e902-132">패키지 빌드 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-132">Build Package Page</span></span>](#BuildPackage)  
  
###  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="6e902-133">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-133">Introduction Page</span></span>  
 <span data-ttu-id="6e902-134">이 페이지에서는 데이터 계층 애플리케이션을 추출하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-134">This page describes the steps for extracting a data-tier application.</span></span>  
  
 <span data-ttu-id="6e902-135">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="6e902-135">**Do not show this page again.**</span></span> <span data-ttu-id="6e902-136">- 앞으로 이 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-136">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="6e902-137">**다음 >** - **방법 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-137">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="6e902-138">**취소** - 데이터 계층 애플리케이션을 데이터베이스에서 추출하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-138">**Cancel** - Ends the wizard without extracting a data-tier application from the database.</span></span>  
  
###  <a name="select-data-page"></a><a name="SelectData"></a><span data-ttu-id="6e902-139">데이터 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-139">Select Data Page</span></span>  
 <span data-ttu-id="6e902-140">마법사의 이 페이지를 사용하여 DAC(데이터 계층 애플리케이션) 패키지 파일에 포함할 참조 데이터를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-140">Use this page of the wizard to select the reference data that you want to include in your data-tier application (DAC) package file.</span></span> <span data-ttu-id="6e902-141">DAC 패키지에 데이터를 포함하는 것은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-141">Including data in your DAC package is optional.</span></span> <span data-ttu-id="6e902-142">지원되는 모든 데이터베이스 개체 및 데이터베이스와 관련된 인스턴스 개체의 스키마는 DAC 패키지에 미리 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-142">The DAC package will already include the schema of all supported database objects and instance objects related to your database.</span></span>  
  
 <span data-ttu-id="6e902-143">최대 10MB의 참조 데이터를 DAC 패키지 파일에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-143">You can include up to 10 MB of reference data in your DAC package file.</span></span> <span data-ttu-id="6e902-144">그러나 DAC에 테이블을 포함하려는 경우 테이블에 **image** 또는 **varchar(max)** 와 같은 BLOB(Binary Large Object) 데이터 형식을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-144">However, for tables to be included in the DAC, they may not contain binary large object (BLOB) data types such as **image** or **varchar(max)**.</span></span> <span data-ttu-id="6e902-145">다른 데이터베이스로 전송하기 위해 많은 양의 데이터를 추출하려는 경우 SQL Server Integration Services, 대량 복사 유틸리티 또는 다른 여러 데이터 마이그레이션 방법 중 하나를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="6e902-145">To extract larger amounts of data for transferring to another database, use SQL Server Integration Services, the bulk copy utility, or one of many other data migration techniques.</span></span>  
  
 <span data-ttu-id="6e902-146">**데이터베이스 테이블** - DAC 패키지에 포함할 데이터가 포함된 데이터베이스 테이블 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-146">**Database table** - Select the check box next to the database tables which contain the data that you want to include in your DAC package.</span></span> <span data-ttu-id="6e902-147">10,000개 이하의 행이 포함된 테이블을 10개까지 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-147">You can select up to ten tables that have 10,000 rows or less.</span></span>  
  
###  <a name="set-properties-page"></a><a name="SetProperties"></a> <span data-ttu-id="6e902-148">속성 설정 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-148">Set Properties Page</span></span>  
 <span data-ttu-id="6e902-149">이 마법사 페이지를 사용하여 DAC(데이터 계층 애플리케이션)를 기술할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-149">Use this page of the wizard to describe the data-tier application (DAC).</span></span> <span data-ttu-id="6e902-150">이러한 속성은 DAC를 식별하는 데 사용되고 다른 DAC와 구별하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-150">These properties are used to identify the DAC and help distinguish it from others.</span></span>  
  
 <span data-ttu-id="6e902-151">**이름** - 이 이름은 DAC를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-151">**Name** - This name identifies the DAC.</span></span> <span data-ttu-id="6e902-152">DAC 이름은 DAC 패키지 파일의 이름과 다를 수 있으며 애플리케이션 특징을 기술해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-152">It can be different than the name of the DAC package file and should describe your application.</span></span> <span data-ttu-id="6e902-153">예를 들어 데이터베이스가 재무 애플리케이션에 사용되는 경우 DAC Finance라는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-153">For example, if the database is used for a finance application, you may wish to name the DAC Finance.</span></span>  
  
 <span data-ttu-id="6e902-154">**버전(xx.xx.xx.xx 사용, x는 숫자)** - DAC의 버전을 식별하는 숫자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-154">**Version (use xx.xx.xx.xx, where x is a number)** - A numeric value that identifies the version of the DAC.</span></span> <span data-ttu-id="6e902-155">DAC 버전은 Visual Studio에서 개발자가 작업 중인 DAC의 버전을 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-155">The DAC version is used in Visual Studio to identify the version of the DAC that developers are working on.</span></span> <span data-ttu-id="6e902-156">DAC를 배포 하는 경우 버전은 데이터베이스에 저장 되 `msdb` 고 나중에의 **데이터 계층 응용 프로그램** 노드에서 볼 수 있습니다 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6e902-156">When deploying a DAC, the version is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6e902-157">**설명:** - 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-157">**Description:** - Optional.</span></span> <span data-ttu-id="6e902-158">DAC에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-158">Describes the DAC.</span></span> <span data-ttu-id="6e902-159">DAC를 배포할 때 설명은 데이터베이스에 저장 `msdb` 되며 나중에의 **데이터 계층 응용 프로그램** 노드에서 볼 수 있습니다 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6e902-159">When deploying a DAC, the description is stored in the `msdb` database and can later be viewed under the **Data-tier Applications** node in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
 <span data-ttu-id="6e902-160">**DAC 패키지 파일에 저장(파일 이름에 .dacpac 확장명 포함):** - DAC를 확장명이 .dacpac인 DAC 패키지 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-160">**Save to DAC package file (include .dacpac extension with file name):** - Saves the DAC to a DAC package file, with a .dacpac extension.</span></span> <span data-ttu-id="6e902-161">파일의 이름과 위치를 지정하려면 **찾아보기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-161">Click the **Browse** button to specify a name and location for the file.</span></span>  
  
 <span data-ttu-id="6e902-162">**기존 파일 덮어쓰기** - 이름이 같은 파일이 이미 있을 경우 DAC 패키지 파일을 바꾸려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-162">**Overwrite existing file** - Select this check box to replace the DAC package file if one already exists with the same name.</span></span>  
  
###  <a name="validation-and-summary-page"></a><a name="ValidateSummary"></a> <span data-ttu-id="6e902-163">유효성 검사 및 요약 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-163">Validation and Summary Page</span></span>  
 <span data-ttu-id="6e902-164">이 페이지에서 마법사는 모든 데이터베이스 개체가 DAC(데이터 계층 애플리케이션)에 의해 지원되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-164">On this page, the wizard validates that all database objects are supported by a data-tier application (DAC).</span></span> <span data-ttu-id="6e902-165">또한 데이터베이스 개체 간의 종속성도 검사하여 DAC에 성공적으로 포함될 수 있는 개체 집합을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-165">It also checks dependencies across database objects to determine the set of objects that can be successfully included in the DAC.</span></span> <span data-ttu-id="6e902-166">그런 다음 유효성 검사 보고서를 표시하고 이 마법사에서 선택한 옵션을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-166">After that, it displays the validation report and summarizes the options that you have selected in this wizard.</span></span> <span data-ttu-id="6e902-167">옵션을 변경하려면 **이전**을 클릭하고,</span><span class="sxs-lookup"><span data-stu-id="6e902-167">To change an option, click **Previous**.</span></span> <span data-ttu-id="6e902-168">DAC 추출을 시작하려면 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-168">To begin extracting a DAC, click **Next**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e902-169">DAC에서 지원하지 않는 개체가 하나 이상 있으면 **다음** 단추가 비활성화되고 추출 프로세스를 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-169">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process may not continue.</span></span> <span data-ttu-id="6e902-170">이 경우에는 지원되지 않는 개체를 제거하고 이 마법사를 다시 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-170">In such cases, it is recommended to remove the non-supported objects and then run this wizard again.</span></span>  
  
 <span data-ttu-id="6e902-171">**요약** - 선택한 옵션에 대한 요약 정보가 **DAC 속성**아래에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-171">**Summary** - A summary of the options you have selected are listed under **DAC properties**.</span></span> <span data-ttu-id="6e902-172">유효성 검사 결과는 **DAC 개체**아래에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-172">The results of the validation are listed under **DAC objects**.</span></span> <span data-ttu-id="6e902-173">유효성 검사 결과는 다음과 같은 세 가지 유형으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-173">There are three types of results from the validation:</span></span>  
  
-   <span data-ttu-id="6e902-174">**DAC에서 지원되는 개체**: 여기에 나열되는 개체 및 개체 종속성은 지원되며 DAC에 성공적으로 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-174">**Objects included in DAC successfully**: these objects and their dependencies are supported, and can be included in the DAC successfully.</span></span>  
  
-   <span data-ttu-id="6e902-175">**DAC에서 지원되지만 경고가 있는 개체**: 여기에 나열되는 개체는 지원되지만 DAC에서 지원하지 않는 다른 개체에 종속되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-175">**Objects included in DAC with warnings**: these objects are supported, but depend on other objects that are not supported in a DAC.</span></span>  
  
-   <span data-ttu-id="6e902-176">**DAC에서 지원되지 않는 개체**: 여기에 나열되는 개체는 지원되지 않으므로 DAC를 추출하기 전에 데이터베이스에서 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-176">**Objects not included in DAC**: these objects are not supported and must be removed from the database before successfully extracting a DAC.</span></span>  
  
 <span data-ttu-id="6e902-177">유효성 프로세스에서는 여러 수준의 종속성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-177">The validation process checks multiple levels of dependencies.</span></span> <span data-ttu-id="6e902-178">예를 들어 지원되지 않는 CLR 데이터 형식을 사용하는 테이블에 종속된 저장 프로시저는 **DAC에서 지원되지만 경고가 있는 개체**아래에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-178">For example, if a stored procedure depends on a table that uses the unsupported CLR data type, the stored procedure will be listed under **Objects included in DAC with warnings**.</span></span>  
  
 <span data-ttu-id="6e902-179">DAC에서 지원하지 않는 개체가 하나 이상 있으면 **다음** 단추가 비활성화되고 추출 프로세스를 계속할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-179">If one or more objects are not supported by a DAC, then the **Next** button is disabled and the extraction process will not continue.</span></span> <span data-ttu-id="6e902-180">이 경우에는 지원되지 않는 개체를 제거하고 이 마법사를 다시 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-180">In such cases, it is recommended to remove the objects that are not supported and then run this wizard again.</span></span>  
  
 <span data-ttu-id="6e902-181">**보고서 저장** - 요약에서 **DAC 개체** 노드 아래의 모든 개체를 나열하는 HTML 기반 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-181">**Save Report** - Enables you to save an HTML-based file that lists all of the objects under the **DAC Objects** node in the summary.</span></span> <span data-ttu-id="6e902-182">이 보고서는 DAC에서 일부 데이터베이스 개체가 지원되지 않는 경우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-182">This report can be useful when some of your database objects are not supported in a DAC.</span></span> <span data-ttu-id="6e902-183">DAC를 다시 추출하기 전에 이 보고서를 사용하여 지원되지 않는 개체를 변경하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-183">Use the report to change or remove objects that are not supported, before trying to extract the DAC again.</span></span>  
  
###  <a name="build-package-page"></a><a name="BuildPackage"></a><span data-ttu-id="6e902-184">패키지 빌드 페이지</span><span class="sxs-lookup"><span data-stu-id="6e902-184">Build Package Page</span></span>  
 <span data-ttu-id="6e902-185">이 페이지를 사용하여 마법사에서 DAC(데이터 계층 애플리케이션)를 추출할 때 진행률을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-185">Use this page to monitor the progress of the wizard as it extracts the data-tier application (DAC).</span></span>  
  
 <span data-ttu-id="6e902-186">**동작** - **DAC 패키지 파일 만들기 및 저장** 동작을 수행하는 동안 마법사는 SQL Server 데이터베이스에서 DAC를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-186">**Action** - During the **Create and save DAC package file** action, the wizard extracts a DAC from your SQL Server database.</span></span> <span data-ttu-id="6e902-187">그런 다음 메모리에 DAC 패키지가 만들어지고 사용자가 지정한 위치에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-187">Then, a DAC package is created in memory and saved to the location you specified.</span></span> <span data-ttu-id="6e902-188">해당 단계의 결과를 확인하려면 **결과** 열의 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-188">Click on the links in the **Result** column to see the outcome of the corresponding step.</span></span>  
  
 <span data-ttu-id="6e902-189">**보고서 저장** - 마법사의 진행률 결과를 파일로 저장하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-189">**Save Report** - Click to save the results of the wizard's progress to a file.</span></span>  
  
 <span data-ttu-id="6e902-190">**마침** - 처리가 완료된 후에나 오류가 발생한 경우 마법사를 닫으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-190">**Finish** - Click to close the wizard after processing has completed, or if an error occurs.</span></span>  
  
##  <a name="extract-a-dac-using-powershell"></a><a name="ExtractDACPowerShell"></a><span data-ttu-id="6e902-191">PowerShell을 사용 하 여 DAC 추출</span><span class="sxs-lookup"><span data-stu-id="6e902-191">Extract a DAC Using PowerShell</span></span>  
 <span data-ttu-id="6e902-192">**PowerShell 스크립트에서 Extract() 메서드를 사용하여 데이터베이스에서 DAC를 추출하려면**</span><span class="sxs-lookup"><span data-stu-id="6e902-192">**To extract a DAC from a database using the Extract() method in a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="6e902-193">SMO Server 개체를 만든 후 이 개체를 DAC를 추출할 데이터베이스를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-193">Create a SMO Server object and set it to the instance that contains the database from which the DAC is to be extracted.</span></span>  
  
2.  <span data-ttu-id="6e902-194">데이터베이스의 이름을 지정하는 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-194">Add a variable that specifies the name of the database.</span></span>  
  
3.  <span data-ttu-id="6e902-195">DAC에 대한 메타데이터(예: DAC 이름, 버전 및 설명)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-195">Specify the metadata for the DAC, such as the DAC name, version, and description.</span></span>  
  
4.  <span data-ttu-id="6e902-196">추출한 DAC 패키지 파일의 경로와 파일 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-196">Specify the path and file name for the extracted DAC package file.</span></span>  
  
5.  <span data-ttu-id="6e902-197">위에서 지정한 정보를 사용하여 Extract 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-197">Run the Extract method with the information specified above.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="6e902-198">예제(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="6e902-198">Example (PowerShell)</span></span>  
 <span data-ttu-id="6e902-199">다음 예에서는 MyDB 데이터베이스에서 MyApplication이라는 DAC를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="6e902-199">The following example extracts a DAC named MyApplication from a database named MyDB.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to extract to a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Specify the location and name for the extracted DAC package.  
$dacpacPath = "C:\MyDACs\MyApplication.dacpac"  
  
## Extract the DAC.  
$extractionunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$extractionunit.Description = $description  
$extractionunit.Extract($dacpacPath)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e902-200">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e902-200">See Also</span></span>  
 [<span data-ttu-id="6e902-201">데이터 계층 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="6e902-201">Data-tier Applications</span></span>](data-tier-applications.md)  
