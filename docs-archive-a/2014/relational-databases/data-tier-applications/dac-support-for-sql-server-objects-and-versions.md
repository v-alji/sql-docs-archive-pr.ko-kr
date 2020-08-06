---
title: SQL Server 개체 및 버전에 대한 DAC 지원 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- data-tier application [SQL Server], supported objects
- objects [SQL Server], data-tier applications
ms.assetid: b1b78ded-16c0-4d69-8657-ec57925e68fd
author: stevestein
ms.author: sstein
ms.openlocfilehash: fa1ea498f603992ce2a62b51d95e74e0f9a9c584
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659455"
---
# <a name="dac-support-for-sql-server-objects-and-versions"></a><span data-ttu-id="6e5d7-102">SQL Server 개체 및 버전에 대한 DAC 지원</span><span class="sxs-lookup"><span data-stu-id="6e5d7-102">DAC Support For SQL Server Objects and Versions</span></span>
  <span data-ttu-id="6e5d7-103">DAC(데이터 계층 애플리케이션)는 가장 일반적으로 사용되는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 개체를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-103">A data-tier application (DAC) supports the most commonly used [!INCLUDE[ssDE](../../includes/ssde-md.md)] objects.</span></span>  
  
 <span data-ttu-id="6e5d7-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6e5d7-104">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="6e5d7-105">지원되는 SQL Server 개체</span><span class="sxs-lookup"><span data-stu-id="6e5d7-105">Supported SQL Server Objects</span></span>](#SupportedObjects)  
  
-   [<span data-ttu-id="6e5d7-106">각 SQL Server 버전에서 지원되는 데이터 계층 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="6e5d7-106">Data-tier Application Support by the Versions of SQL Server</span></span>](#SupportByVersion)  
  
-   [<span data-ttu-id="6e5d7-107">데이터 배포 제한 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d7-107">Data Deployment Limitations</span></span>](#DeploymentLimitations)  
  
-   [<span data-ttu-id="6e5d7-108">배포 작업에 대한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d7-108">Additional Considerations for Deployment Actions</span></span>](#Considerations)  
  
##  <a name="supported-sql-server-objects"></a><a name="SupportedObjects"></a><span data-ttu-id="6e5d7-109">지원 되는 SQL Server 개체</span><span class="sxs-lookup"><span data-stu-id="6e5d7-109">Supported SQL Server Objects</span></span>  
 <span data-ttu-id="6e5d7-110">작성 또는 편집 중인 데이터 계층 애플리케이션에서는 지원되는 개체만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-110">Only supported objects can be specified in a data-tier application as it is being authored or edited.</span></span> <span data-ttu-id="6e5d7-111">DAC를 지원하지 않는 개체가 포함된 기존 데이터베이스에서 DAC를 추출하거나 등록하거나 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-111">You cannot extract, register, or import a DAC from an existing database that contains objects that are not supported in a DAC.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6e5d7-112">에서는 DAC에서 다음 개체를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-112">supports the following objects in a DAC.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e5d7-113">DATABASE ROLE</span><span class="sxs-lookup"><span data-stu-id="6e5d7-113">DATABASE ROLE</span></span>|<span data-ttu-id="6e5d7-114">FUNCTION: 인라인 테이블 반환</span><span class="sxs-lookup"><span data-stu-id="6e5d7-114">FUNCTION: Inline Table-valued</span></span>|  
|<span data-ttu-id="6e5d7-115">FUNCTION: 다중 문 테이블 반환</span><span class="sxs-lookup"><span data-stu-id="6e5d7-115">FUNCTION: Multistatement Table-valued</span></span>|<span data-ttu-id="6e5d7-116">FUNCTION: 스칼라</span><span class="sxs-lookup"><span data-stu-id="6e5d7-116">FUNCTION: Scalar</span></span>|  
|<span data-ttu-id="6e5d7-117">INDEX: 클러스터형</span><span class="sxs-lookup"><span data-stu-id="6e5d7-117">INDEX: Clustered</span></span>|<span data-ttu-id="6e5d7-118">인덱스: 비클러스터형</span><span class="sxs-lookup"><span data-stu-id="6e5d7-118">INDEX: Nonclustered</span></span>|  
|<span data-ttu-id="6e5d7-119">INDEX: 공간</span><span class="sxs-lookup"><span data-stu-id="6e5d7-119">INDEX: Spacial</span></span>|<span data-ttu-id="6e5d7-120">INDEX: 고유</span><span class="sxs-lookup"><span data-stu-id="6e5d7-120">INDEX: Unique</span></span>|  
|<span data-ttu-id="6e5d7-121">LOGIN</span><span class="sxs-lookup"><span data-stu-id="6e5d7-121">LOGIN</span></span>|<span data-ttu-id="6e5d7-122">사용 권한</span><span class="sxs-lookup"><span data-stu-id="6e5d7-122">Permissions</span></span>|  
|<span data-ttu-id="6e5d7-123">역할 멤버 자격</span><span class="sxs-lookup"><span data-stu-id="6e5d7-123">Role Memberships</span></span>|<span data-ttu-id="6e5d7-124">SCHEMA</span><span class="sxs-lookup"><span data-stu-id="6e5d7-124">SCHEMA</span></span>|  
|<span data-ttu-id="6e5d7-125">통계</span><span class="sxs-lookup"><span data-stu-id="6e5d7-125">Statistics</span></span>|<span data-ttu-id="6e5d7-126">STORED PROCEDURE: Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6e5d7-126">STORED PROCEDURE: Transact-SQL</span></span>|  
|<span data-ttu-id="6e5d7-127">동의어</span><span class="sxs-lookup"><span data-stu-id="6e5d7-127">Synonyms</span></span>|<span data-ttu-id="6e5d7-128">TABLE: CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-128">TABLE: Check Constraint</span></span>|  
|<span data-ttu-id="6e5d7-129">TABLE: 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="6e5d7-129">TABLE: Collation</span></span>|<span data-ttu-id="6e5d7-130">TABLE: 계산 열을 포함하는 열</span><span class="sxs-lookup"><span data-stu-id="6e5d7-130">TABLE: Column, including computed columns</span></span>|  
|<span data-ttu-id="6e5d7-131">TABLE: DEFAULT 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-131">TABLE: Constraint, Default</span></span>|<span data-ttu-id="6e5d7-132">TABLE: FOREIGN KEY 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-132">TABLE: Constraint, Foreign Key</span></span>|  
|<span data-ttu-id="6e5d7-133">TABLE: INDEX 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-133">TABLE: Constraint, Index</span></span>|<span data-ttu-id="6e5d7-134">TABLE: PRIMARY KEY 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-134">TABLE: Constraint, Primary Key</span></span>|  
|<span data-ttu-id="6e5d7-135">TABLE: UNIQUE 제약 조건</span><span class="sxs-lookup"><span data-stu-id="6e5d7-135">TABLE: Constraint, Unique</span></span>|<span data-ttu-id="6e5d7-136">TRIGGER: DML</span><span class="sxs-lookup"><span data-stu-id="6e5d7-136">TRIGGER: DML</span></span>|  
|<span data-ttu-id="6e5d7-137">TYPE: HIERARCHYID, GEOMETRY, GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="6e5d7-137">TYPE: HIERARCHYID, GEOMETRY, GEOGRAPHY</span></span>|<span data-ttu-id="6e5d7-138">TYPE: 사용자 정의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="6e5d7-138">TYPE: User-defined Data Type</span></span>|  
|<span data-ttu-id="6e5d7-139">TYPE: 사용자 정의 테이블 형식</span><span class="sxs-lookup"><span data-stu-id="6e5d7-139">TYPE: User-defined Table Type</span></span>|<span data-ttu-id="6e5d7-140">USER</span><span class="sxs-lookup"><span data-stu-id="6e5d7-140">USER</span></span>|  
|<span data-ttu-id="6e5d7-141">VIEW</span><span class="sxs-lookup"><span data-stu-id="6e5d7-141">VIEW</span></span>||  
  
##  <a name="data-tier-application-support-by-the-versions-of-sql-server"></a><a name="SupportByVersion"></a><span data-ttu-id="6e5d7-142">SQL Server 버전의 데이터 계층 응용 프로그램 지원</span><span class="sxs-lookup"><span data-stu-id="6e5d7-142">Data-tier Application Support by the Versions of SQL Server</span></span>  
 <span data-ttu-id="6e5d7-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전마다 DAC 작업에 대해 지원되는 수준이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-143">The versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have different levels of support for DAC operations.</span></span> <span data-ttu-id="6e5d7-144">한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에서 지원되는 모든 DAC 작업은 해당 제품의 모든 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-144">All of the DAC operations supported by a version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported by all editions of that version.</span></span>  
  
 <span data-ttu-id="6e5d7-145">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에서 지원하는 DAC 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-145">Instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] support the following DAC operations:</span></span>  
  
-   <span data-ttu-id="6e5d7-146">내보내기 및 추출은 지원되는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-146">Export and extract are supported on all supported versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="6e5d7-147">[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 와 모든 버전의 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]및 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]에서는 모든 작업이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-147">All operations are supported on [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] and all versions of [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].</span></span>  
  
-   <span data-ttu-id="6e5d7-148">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2(서비스 팩 2) 이상과 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 이상에서는 모든 작업이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-148">All operations are supported on [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Service Pack 2 (SP2) or later, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP4 or later.</span></span>  
  
 <span data-ttu-id="6e5d7-149">DAC Framework는 DAC 패키지 및 내보내기 파일을 작성하고 처리하는 클라이언트 쪽 도구를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-149">The DAC Framework comprises the client-side tools for building and processing DAC packages and export files.</span></span> <span data-ttu-id="6e5d7-150">DAC Framework는 다음과 같은 제품에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-150">The following products include the DAC Framework</span></span>  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] <span data-ttu-id="6e5d7-151">및 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 에는 모든 DAC 작업을 지원하는 DAC Framework 3.0이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-151">and [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] includes DAC Framework 3.0, which supports all DAC operations.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="6e5d7-152">SP1 및 Visual Studio 2010 SP1에는 내보내기와 가져오기를 제외한 모든 DAC 작업을 지원하는 DAC Framework 1.1이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-152">SP1 and Visual Studio 2010 SP1 included DAC Framework 1.1, which supports all DAC operations except export and import.</span></span>  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] <span data-ttu-id="6e5d7-153">및 Visual Studio 2010에는 내보내기, 가져오기 및 전체 업그레이드를 제외한 모든 DAC 작업을 지원하는 DAC Framework 1.0이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-153">and Visual Studio 2010 included DAC Framework 1.0, which supports all DAC operations except export, import, and in-place upgrade.</span></span>  
  
-   <span data-ttu-id="6e5d7-154">이전 버전 SQL Server 또는 Visual Studio의 클라이언트 도구는 DAC 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-154">The client tools from earlier versions of SQL Server or Visual Studio do not support DAC operations.</span></span>  
  
 <span data-ttu-id="6e5d7-155">DAC Framework 버전 중 하나로 작성한 DAC 패키지 또는 내보내기 파일은 이전 버전의 DAC Framework에서 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-155">A DAC package or export file built with one version of the DAC Framework cannot be processed by an earlier version of the DAC Framework.</span></span> <span data-ttu-id="6e5d7-156">예를 들어 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 클라이언트 도구를 사용하여 추출한 DAC 패키지는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 클라이언트 도구를 사용하여 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-156">For example, a DAC package extracted using the [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] client tools cannot be deployed using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools.</span></span>  
  
 <span data-ttu-id="6e5d7-157">하위 버전의 DAC Framework에서 작성한 DAC 패키지 또는 내보내기 파일은 상위 버전의 DAC Framework에서 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-157">A DAC package or export file built with one version of the DAC Framework can be processed by any later version of the DAC Framework.</span></span> <span data-ttu-id="6e5d7-158">예를 들어 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 클라이언트 도구를 사용하여 추출한 DAC 패키지는 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 이상의 클라이언트 도구를 사용하여 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-158">For example, a DAC package extracted using the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] client tools can be deployed using either the [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] SP1 or higher client tools.</span></span>  
  
##  <a name="data-deployment-limitations"></a><a name="DeploymentLimitations"></a><span data-ttu-id="6e5d7-159">데이터 배포 제한 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d7-159">Data Deployment Limitations</span></span>  
 <span data-ttu-id="6e5d7-160">SQL Server 2012 SP1에서 DAC Framework 데이터 배포 엔진의 정확도 제한 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-160">Note these fidelity limitations in the DAC Framework data deployment engine in SQL Server 2012 SP1.</span></span> <span data-ttu-id="6e5d7-161">제한 사항은 .dacpac 파일 배포 또는 게시, .bacpac 파일 가져오기 등의 DAC Framework 작업에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-161">The limitations apply to the following DAC Framework actions: deploy or publish a .dacpac file, and import a .bacpac file.</span></span>  
  
1.  <span data-ttu-id="6e5d7-162">sql_variant 열 내에서 특정 조건 및 기본 형식의 메타데이터 손실</span><span class="sxs-lookup"><span data-stu-id="6e5d7-162">Loss of metadata for certain conditions and base types within sql_variant columns.</span></span> <span data-ttu-id="6e5d7-163">영향을 받는 경우 다음 메시지와 함께 경고가 나타납니다.  **DAC Framework에서 배포될 때 sql_variant 열 내에 사용된 특정 데이터 형식의 특정 속성은 유지되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="6e5d7-163">In the affected cases, you will see a warning with the following message:  **Certain properties on certain data types used within a sql_variant column are not preserved when deployed by the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="6e5d7-164">MONEY, SMALLMONEY, NUMERIC, DECIMAL 기본 형식: 전체 자릿수는 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-164">MONEY, SMALLMONEY, NUMERIC, DECIMAL base types:  Precision is not preserved.</span></span>  
  
        -   <span data-ttu-id="6e5d7-165">전체 자릿수가 38인 DECIMAL/NUMERIC 기본 형식: “TotalBytes” sql_variant 메타데이터는 항상 21로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-165">DECIMAL/NUMERIC base types with precision 38:  the "TotalBytes" sql_variant metadata is always set to 21.</span></span>  
  
    -   <span data-ttu-id="6e5d7-166">모든 텍스트 기본 형식: 데이터베이스 기본 데이터 정렬은 모든 텍스트에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-166">All text base types:  The database default collation is applied for all text.</span></span>  
  
    -   <span data-ttu-id="6e5d7-167">BINARY 기본 형식: 최대 길이 속성은 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-167">BINARY base types:  Max length property is not preserved.</span></span>  
  
    -   <span data-ttu-id="6e5d7-168">TIME, DATETIMEOFFSET 기본 형식: 전체 자릿수는 항상 7로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-168">TIME, DATETIMEOFFSET base types:  Precision is always set to 7.</span></span>  
  
2.  <span data-ttu-id="6e5d7-169">Sql_variant 열 내의 데이터 손실</span><span class="sxs-lookup"><span data-stu-id="6e5d7-169">Loss of data within sql_variant columns.</span></span> <span data-ttu-id="6e5d7-170">영향을 받는 경우 다음 메시지와 함께 경고가 나타납니다.  **소수 자릿수가 3보다 큰 sql_variant DATETIME2 열의 값이 DAC Framework에서 배포되면 데이터가 손실됩니다. 배포하는 동안 DATETIME2 값은 소수 자릿수가 3과 같도록 제한됩니다.**</span><span class="sxs-lookup"><span data-stu-id="6e5d7-170">In the affected case, you will see a warning with the following message:  **There will be data loss when a value in a sql_variant DATETIME2 column with scale greater than 3 is deployed by the DAC Framework. The DATETIME2 value is limited to a scale equal to 3 during deployment.**</span></span>  
  
    -   <span data-ttu-id="6e5d7-171">소수 자릿수가 3보다 큰 DATETIME2 기본 형식: 소수 자릿수는 3으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-171">DATETIME2 base type with scale greater than 3:  scale is limited to equal 3.</span></span>  
  
3.  <span data-ttu-id="6e5d7-172">Sql_variant 열 내에서 다음 조건에 대한 배포 작업은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-172">Deployment operation fails for the following conditions within sql_variant columns.</span></span> <span data-ttu-id="6e5d7-173">영향을 받는 경우 다음 메시지와 함께 대화 상자가 나타납니다.  **DAC Framework의 데이터 제한으로 인해 작업을 수행하지 못했습니다.**</span><span class="sxs-lookup"><span data-stu-id="6e5d7-173">In the affected cases, you will see a dialog with the following message:  **Operation failed due to data limitations in the DAC Framework.**</span></span>  
  
    -   <span data-ttu-id="6e5d7-174">DATETIME2, SMALLDATETIME 및 DATE 기본 형식: 값이 DATETIME 외 범위인 경우(예: 연도가 1753 미만인 경우)</span><span class="sxs-lookup"><span data-stu-id="6e5d7-174">DATETIME2, SMALLDATETIME and DATE base types:  If the value is outside of DATETIME range - for example, the year is less than 1753.</span></span>  
  
    -   <span data-ttu-id="6e5d7-175">DECIMAL, NUMERIC 기본 형식: 값의 전체 자릿수가 28보다 큰 경우</span><span class="sxs-lookup"><span data-stu-id="6e5d7-175">DECIMAL, NUMERIC base type:  when precision of the value is greater than 28.</span></span>  
  
##  <a name="additional-considerations-for-deployment-actions"></a><a name="Considerations"></a><span data-ttu-id="6e5d7-176">배포 작업에 대 한 추가 고려 사항</span><span class="sxs-lookup"><span data-stu-id="6e5d7-176">Additional Considerations for Deployment Actions</span></span>  
 <span data-ttu-id="6e5d7-177">DAC Framework 데이터 배포 작업에 대한 다음 고려 사항에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-177">Note the following considerations for DAC Framework data deployment actions:</span></span>  
  
-   <span data-ttu-id="6e5d7-178">DAC 프레임 워크를 사용 하 여 데이터베이스에서 패키지를 만들기 위한 **추출/내보내기** 작업-예를 들어 .dacpac 파일 추출, bacpac 파일 내보내기-이러한 제한이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-178">**Extract/Export** - On actions that use the DAC Framework to create a package from a database - for example, extract a .dacpac file, export a .bacpac file - these limitations do not apply.</span></span> <span data-ttu-id="6e5d7-179">패키지의 데이터는 원본 데이터베이스에서 데이터의 전체 정확도 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-179">The data in the package is a full-fidelity representation of the data in the source database.</span></span> <span data-ttu-id="6e5d7-180">패키지에 이러한 조건 중 하나라도 있는 경우 추출/내보내기 로그에는 위에서 설명한 메시지를 통한 문제 요약이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-180">If any of these conditions are present in the package, the extract/export log will contain a summary of the issues via the messages noted above.</span></span> <span data-ttu-id="6e5d7-181">이것은 그들이 만든 패키지의 잠재적인 데이터 배포 문제에 대해 사용자에게 경고하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-181">This is to warn the user of potential data deployment issues with the package they created.</span></span> <span data-ttu-id="6e5d7-182">사용자는 로그에서 다음과 같은 요약 메시지를 확인할 수도 있습니다.  **이러한 제한은 데이터 형식 및 DAC Framework에서 만든 DAC 패키지에 저장된 값의 정확도에 영향을 미치지 않고, DAC 패키지를 데이터베이스에 배포한 결과 발생한 데이터 유형 및 값에만 적용됩니다. 영향 받는 데이터 및 이 제한을 해결하는 방법은** [다음 항목](https://go.microsoft.com/fwlink/?LinkId=267086)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-182">The user will also see the following summary message in the log:  **These limitations do not affect the fidelity of the data types and values stored in the DAC package created by the DAC Framework; they only apply to the data types and values resulting from deploying a DAC package to a database. For more information about the data that is affected and how to work around this limitation, see** [this topic](https://go.microsoft.com/fwlink/?LinkId=267086).</span></span>  
  
-   <span data-ttu-id="6e5d7-183">**배포/게시/가져오기** - DAC Framework를 사용하여 패키지를 데이터베이스에 배포하는 작업(예: .dacpac 파일 배포 또는 게시, .bacpac 파일 가져오기 등)에서는 이러한 제한이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-183">**Deploy/Publish/Import** - On actions that use the DAC Framework to deploy a package to a database, like to deploy or publish a .dacpac file, and import a .bacpac file, these limitations do apply.</span></span> <span data-ttu-id="6e5d7-184">대상 데이터베이스를 만드는 데이터에 패키지에 있는 데이터의 전체 정확도 표현이 포함되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-184">The data that results in the target database may not contain a full-fidelity representation of the data in the package.</span></span> <span data-ttu-id="6e5d7-185">배포/가져오기 로그에는 문제가 발생한 모든 인스턴스에 대해 위에서 언급한 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-185">The Deploy/Import log will contain a message, noted above, for every instance the issue is encountered.</span></span> <span data-ttu-id="6e5d7-186">오류로 인해 작업은 차단되지만(위의 범주 3 참조) 다른 경고와 함께 계속됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-186">The operation will be blocked by errors - see category 3 above - but will proceed with the other warnings.</span></span>  
  
     <span data-ttu-id="6e5d7-187">이 시나리오에서 영향을 받는 데이터와 배포/게시/가져오기 작업에 대한 이 제한 사항을 해결하는 방법은 [다음 항목](https://go.microsoft.com/fwlink/?LinkId=267087)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-187">For more information about the data that is affected in this scenario and how to work around this limitation for deploy/publish/import actions, see [this topic](https://go.microsoft.com/fwlink/?LinkId=267087).</span></span>  
  
-   <span data-ttu-id="6e5d7-188">**해결 방법** -추출 및 내보내기 작업을 수행 하면 전체 충실도 BCP 데이터 파일이 .dacpac 또는 bacpac 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-188">**Workarounds** - Extract and export operations will write full-fidelity BCP data files into the .dacpac or .bacpac files.</span></span> <span data-ttu-id="6e5d7-189">제한 사항을 피하려면 SQL Server BCP.exe 명령 줄 유틸리티를 사용하여 DAC 패키지에서 대상 데이터베이스로 전체 정확도 데이터를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="6e5d7-189">To avoid limitations, use the SQL Server BCP.exe command line utility to deploy full-fidelity data to a target database from a DAC package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5d7-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e5d7-190">See Also</span></span>  
 [<span data-ttu-id="6e5d7-191">데이터 계층 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="6e5d7-191">Data-tier Applications</span></span>](data-tier-applications.md)  
  
  
