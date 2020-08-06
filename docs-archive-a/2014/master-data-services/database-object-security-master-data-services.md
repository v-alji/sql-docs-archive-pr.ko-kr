---
title: 데이터베이스 개체 보안(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9713f615a190beee5054ee55471e0db387a8a9e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728424"
---
# <a name="database-object-security-master-data-services"></a><span data-ttu-id="62daf-102">데이터베이스 개체 보안(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="62daf-102">Database Object Security (Master Data Services)</span></span>
  <span data-ttu-id="62daf-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 데이터는 여러 데이터베이스 테이블에 저장되고 뷰에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-103">In the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, data is stored in multiple database tables and is visible in views.</span></span> <span data-ttu-id="62daf-104">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 보안을 설정한 정보는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 액세스할 수 있는 사용자가 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-104">Information that you might have secured in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="62daf-105">특히 직원 급여 정보가 Employee 모델에 포함되거나 회사 재무 정보가 Account 모델에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-105">Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model.</span></span> <span data-ttu-id="62daf-106">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 사용자 인터페이스에서 이러한 모델에 대한 사용자 액세스를 거부할 수 있지만 데이터베이스에 액세스할 수 있는 사용자는 이 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-106">You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface, but users with access to the database can view this data.</span></span>  
  
 <span data-ttu-id="62daf-107">데이터베이스 개체에 대한 사용 권한을 부여하여 특정 데이터를 사용할 수 있는 사용자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-107">You can grant permissions to database objects to make specific data available to users.</span></span> <span data-ttu-id="62daf-108">권한 부여 방법에 대한 자세한 내용은 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-108">For more information on granting permissions, see [GRANT Object Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-object-permissions-transact-sql).</span></span> <span data-ttu-id="62daf-109">SQL Server 보안 설정 방법은 [Securing SQL Server](../relational-databases/security/securing-sql-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="62daf-109">For more information about securing SQL server, see [Securing SQL Server](../relational-databases/security/securing-sql-server.md).</span></span>  
  
 <span data-ttu-id="62daf-110">다음 태스크를 수행하려면 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 대한 액세스 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-110">The following tasks require access to the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   [<span data-ttu-id="62daf-111">데이터 준비</span><span class="sxs-lookup"><span data-stu-id="62daf-111">Staging Data</span></span>](#Staging)  
  
-   [<span data-ttu-id="62daf-112">비즈니스 규칙에 대해 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="62daf-112">Validating Data Against Business Rules</span></span>](#rules)  
  
-   [<span data-ttu-id="62daf-113">버전 삭제</span><span class="sxs-lookup"><span data-stu-id="62daf-113">Deleting Versions</span></span>](#Versions)  
  
-   [<span data-ttu-id="62daf-114">계층 멤버 권한 즉시 적용</span><span class="sxs-lookup"><span data-stu-id="62daf-114">Immediately Applying Hierarchy Member Permissions</span></span>](#Hierarchy)  
  
-   [<span data-ttu-id="62daf-115">시스템 관리자 계정 변경</span><span class="sxs-lookup"><span data-stu-id="62daf-115">Changing the System Administrator Account</span></span>](#SysAdmin)  
  
-   [<span data-ttu-id="62daf-116">시스템 설정 구성</span><span class="sxs-lookup"><span data-stu-id="62daf-116">Configuring System Settings</span></span>](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> <span data-ttu-id="62daf-117">데이터 준비</span><span class="sxs-lookup"><span data-stu-id="62daf-117">Staging Data</span></span>  
 <span data-ttu-id="62daf-118">다음 표에서 각 보안 개체에는 이름의 일부로 "이름"이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-118">In the following table, each securable has "name" as part of the name.</span></span> <span data-ttu-id="62daf-119">이것은 엔터티를 만들 때 지정된 준비 테이블의 이름을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-119">This indicates the name of the staging table that is specified when an entity is created.</span></span> <span data-ttu-id="62daf-120">자세한 내용은 [데이터 가져오기 &#40;MDS(Master Data Services)](overview-importing-data-from-tables-master-data-services.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="62daf-120">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)</span></span>  
  
|<span data-ttu-id="62daf-121">작업</span><span class="sxs-lookup"><span data-stu-id="62daf-121">Action</span></span>|<span data-ttu-id="62daf-122">보안 개체</span><span class="sxs-lookup"><span data-stu-id="62daf-122">Securables</span></span>|<span data-ttu-id="62daf-123">사용 권한</span><span class="sxs-lookup"><span data-stu-id="62daf-123">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="62daf-124">리프 멤버 및 해당 속성을 준비 테이블에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-124">Load leaf members and their attributes into the staging table.</span></span>|<span data-ttu-id="62daf-125">stg.name_Leaf</span><span class="sxs-lookup"><span data-stu-id="62daf-125">stg.name_Leaf</span></span>|<span data-ttu-id="62daf-126">필수: INSERT</span><span class="sxs-lookup"><span data-stu-id="62daf-126">Required: INSERT</span></span><br /><br /> <span data-ttu-id="62daf-127">선택 사항: SELECT 및 UPDATE</span><span class="sxs-lookup"><span data-stu-id="62daf-127">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="62daf-128">리프 준비 테이블의 데이터를 해당 MDS 데이터 집합 테이블에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-128">Load the data from the Leaf staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="62daf-129">stg.udp_name_Leaf</span><span class="sxs-lookup"><span data-stu-id="62daf-129">stg.udp_name_Leaf</span></span>|<span data-ttu-id="62daf-130">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-130">EXECUTE</span></span>|  
|<span data-ttu-id="62daf-131">리프 통합 멤버 및 해당 속성을 준비 테이블에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-131">Load consolidated members and their attributes into the staging table.</span></span>|<span data-ttu-id="62daf-132">stg.name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="62daf-132">stg.name_Consolidated</span></span>|<span data-ttu-id="62daf-133">필수: INSERT</span><span class="sxs-lookup"><span data-stu-id="62daf-133">Required: INSERT</span></span><br /><br /> <span data-ttu-id="62daf-134">선택 사항: SELECT 및 UPDATE</span><span class="sxs-lookup"><span data-stu-id="62daf-134">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="62daf-135">통합 준비 테이블의 데이터를 해당 MDS 데이터 집합 테이블에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-135">Load the data from the Consolidated staging table into the appropriate MDS database tables.</span></span>|<span data-ttu-id="62daf-136">stg.udp_name_Consolidated</span><span class="sxs-lookup"><span data-stu-id="62daf-136">stg.udp_name_Consolidated</span></span>|<span data-ttu-id="62daf-137">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-137">EXECUTE</span></span>|  
|<span data-ttu-id="62daf-138">명시적 계층의 리프 및 통합 멤버의 관계를 준비 테이블에 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-138">Load leaf and consolidated members' relationships to each other in an explicit hierarchy into the staging table.</span></span>|<span data-ttu-id="62daf-139">stg.name_Relationship</span><span class="sxs-lookup"><span data-stu-id="62daf-139">stg.name_Relationship</span></span>|<span data-ttu-id="62daf-140">필수: INSERT</span><span class="sxs-lookup"><span data-stu-id="62daf-140">Required: INSERT</span></span><br /><br /> <span data-ttu-id="62daf-141">선택 사항: SELECT 및 UPDATE</span><span class="sxs-lookup"><span data-stu-id="62daf-141">Optional: SELECT and UPDATE</span></span>|  
|<span data-ttu-id="62daf-142">관계 준비 테이블의 데이터를 해당 MDS 테이블에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-142">Load the data from the Relationship staging table into the appropriate MDS tables.</span></span>|<span data-ttu-id="62daf-143">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="62daf-143">stg.udp_name_Relationship</span></span>|<span data-ttu-id="62daf-144">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-144">EXECUTE</span></span>|  
|<span data-ttu-id="62daf-145">준비 테이블의 데이터를 MDS 데이터 집합 테이블에 삽입하는 동안 발생한 오류를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-145">View errors that occurred when data from the staging tables was being inserted into the MDS database tables.</span></span>|<span data-ttu-id="62daf-146">stg.udp_name_Relationship</span><span class="sxs-lookup"><span data-stu-id="62daf-146">stg.udp_name_Relationship</span></span>|<span data-ttu-id="62daf-147">SELECT</span><span class="sxs-lookup"><span data-stu-id="62daf-147">SELECT</span></span>|  
  
 <span data-ttu-id="62daf-148">자세한 내용은 [데이터 가져오기&#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-148">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a><span data-ttu-id="62daf-149">비즈니스 규칙에 대해 데이터 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="62daf-149">Validating Data Against Business Rules</span></span>  
  
|<span data-ttu-id="62daf-150">작업</span><span class="sxs-lookup"><span data-stu-id="62daf-150">Action</span></span>|<span data-ttu-id="62daf-151">보안 개체</span><span class="sxs-lookup"><span data-stu-id="62daf-151">Securable</span></span>|<span data-ttu-id="62daf-152">사용 권한</span><span class="sxs-lookup"><span data-stu-id="62daf-152">Permissions</span></span>|  
|------------|---------------|-----------------|  
|<span data-ttu-id="62daf-153">비즈니스 규칙에 대해 데이터 버전의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-153">Validate a version of data against business rules</span></span>|<span data-ttu-id="62daf-154">mdm.udpValidateModel</span><span class="sxs-lookup"><span data-stu-id="62daf-154">mdm.udpValidateModel</span></span>|<span data-ttu-id="62daf-155">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-155">EXECUTE</span></span>|  
  
 <span data-ttu-id="62daf-156">자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-156">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../../2014/master-data-services/validation-stored-procedure-master-data-services.md).</span></span>  
  
##  <a name="deleting-versions"></a><a name="Versions"></a><span data-ttu-id="62daf-157">버전 삭제</span><span class="sxs-lookup"><span data-stu-id="62daf-157">Deleting Versions</span></span>  
  
|<span data-ttu-id="62daf-158">작업</span><span class="sxs-lookup"><span data-stu-id="62daf-158">Action</span></span>|<span data-ttu-id="62daf-159">보안 개체</span><span class="sxs-lookup"><span data-stu-id="62daf-159">Securables</span></span>|<span data-ttu-id="62daf-160">사용 권한</span><span class="sxs-lookup"><span data-stu-id="62daf-160">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="62daf-161">삭제할 버전의 ID 확인</span><span class="sxs-lookup"><span data-stu-id="62daf-161">Determine the ID of the version you want to delete</span></span>|<span data-ttu-id="62daf-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span><span class="sxs-lookup"><span data-stu-id="62daf-162">mdm.viw_SYSTEM_SCHEMA_VERSION</span></span>|<span data-ttu-id="62daf-163">SELECT</span><span class="sxs-lookup"><span data-stu-id="62daf-163">SELECT</span></span>|  
|<span data-ttu-id="62daf-164">모델의 버전 삭제</span><span class="sxs-lookup"><span data-stu-id="62daf-164">Delete a version of a model</span></span>|<span data-ttu-id="62daf-165">mdm.udpVersionDelete</span><span class="sxs-lookup"><span data-stu-id="62daf-165">mdm.udpVersionDelete</span></span>|<span data-ttu-id="62daf-166">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-166">EXECUTE</span></span>|  
  
 <span data-ttu-id="62daf-167">자세한 내용은 [버전 삭제&#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-167">For more information, see [Delete a Version &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-version-master-data-services.md).</span></span>  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a><span data-ttu-id="62daf-168">계층 멤버 권한 즉시 적용</span><span class="sxs-lookup"><span data-stu-id="62daf-168">Immediately Applying Hierarchy Member Permissions</span></span>  
  
|<span data-ttu-id="62daf-169">작업</span><span class="sxs-lookup"><span data-stu-id="62daf-169">Action</span></span>|<span data-ttu-id="62daf-170">보안 개체</span><span class="sxs-lookup"><span data-stu-id="62daf-170">Securables</span></span>|<span data-ttu-id="62daf-171">사용 권한</span><span class="sxs-lookup"><span data-stu-id="62daf-171">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="62daf-172">멤버 권한 즉시 적용</span><span class="sxs-lookup"><span data-stu-id="62daf-172">Immediately apply member permissions</span></span>|<span data-ttu-id="62daf-173">mdm.udpSecurityMemberProcessRebuildModel</span><span class="sxs-lookup"><span data-stu-id="62daf-173">mdm.udpSecurityMemberProcessRebuildModel</span></span>|<span data-ttu-id="62daf-174">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-174">EXECUTE</span></span>|  
  
 <span data-ttu-id="62daf-175">자세한 내용은 [멤버 권한 즉시 적용&#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-175">For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
##  <a name="changing-the-system-administrator-account"></a><a name="SysAdmin"></a><span data-ttu-id="62daf-176">시스템 관리자 계정 변경</span><span class="sxs-lookup"><span data-stu-id="62daf-176">Changing the System Administrator Account</span></span>  
  
|<span data-ttu-id="62daf-177">작업</span><span class="sxs-lookup"><span data-stu-id="62daf-177">Action</span></span>|<span data-ttu-id="62daf-178">보안 개체</span><span class="sxs-lookup"><span data-stu-id="62daf-178">Securables</span></span>|<span data-ttu-id="62daf-179">사용 권한</span><span class="sxs-lookup"><span data-stu-id="62daf-179">Permissions</span></span>|  
|------------|----------------|-----------------|  
|<span data-ttu-id="62daf-180">새 관리자의 SID 확인</span><span class="sxs-lookup"><span data-stu-id="62daf-180">Determine the SID of the new administrator</span></span>|<span data-ttu-id="62daf-181">mdm.tblUser</span><span class="sxs-lookup"><span data-stu-id="62daf-181">mdm.tblUser</span></span>|<span data-ttu-id="62daf-182">SELECT</span><span class="sxs-lookup"><span data-stu-id="62daf-182">SELECT</span></span>|  
|<span data-ttu-id="62daf-183">시스템 관리자 계정 변경</span><span class="sxs-lookup"><span data-stu-id="62daf-183">Change the system administrator account</span></span>|<span data-ttu-id="62daf-184">mdm.udpSecuritySetAdministrator</span><span class="sxs-lookup"><span data-stu-id="62daf-184">mdm.udpSecuritySetAdministrator</span></span>|<span data-ttu-id="62daf-185">CREATE 문을 실행하기 전에</span><span class="sxs-lookup"><span data-stu-id="62daf-185">EXECUTE</span></span>|  
  
 <span data-ttu-id="62daf-186">자세한 내용은 [MDS(Master Data Services)&#41;&#40;시스템 관리자 계정 변경 ](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-186">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a><span data-ttu-id="62daf-187">시스템 설정 구성</span><span class="sxs-lookup"><span data-stu-id="62daf-187">Configuring System Settings</span></span>  
 <span data-ttu-id="62daf-188">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에는 동작을 제어하기 위해 구성할 수 있는 시스템 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-188">There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="62daf-189">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 이러한 설정을 조정할 수 있으며, UPDATE 권한이 있는 경우에는 mdm.tblSystemSetting 데이터베이스 테이블에서 이러한 설정을 직접 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62daf-189">You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table.</span></span> <span data-ttu-id="62daf-190">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62daf-190">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62daf-191">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62daf-191">See Also</span></span>  
 [<span data-ttu-id="62daf-192">보안&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="62daf-192">Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/security-master-data-services.md)  
  
  
