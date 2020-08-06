---
title: SQL Server 개체 전송 태스크 편집기 (개체 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjects.objects.f1
helpviewer_keywords:
- Transfer SQL Server Objects Task Editor
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7038939b02d17b2449a374be51f7f9fa42eae7d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734276"
---
# <a name="transfer-sql-server-objects-task-editor-objects-page"></a><span data-ttu-id="3aca0-102">SQL Server 개체 전송 태스크 편집기(개체 페이지)</span><span class="sxs-lookup"><span data-stu-id="3aca0-102">Transfer SQL Server Objects Task Editor (Objects Page)</span></span>
  <span data-ttu-id="3aca0-103">**SQL Server 개체 전송 태스크 편집기** 대화 상자의 **개체** 페이지를 사용하여 하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 한 인스턴스에서 다른 인스턴스로 복사하기 위한 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-103">Use the **Objects** page of the **Transfer SQL Server Objects Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="3aca0-104">테이블, 뷰, 저장 프로시저 및 사용자 정의 함수와 같은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-104">Tables, views, stored procedures, and user-defined functions are a few examples of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects that you can copy.</span></span> <span data-ttu-id="3aca0-105">이 태스크에 대한 자세한 내용은 [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3aca0-105">For more information about this task, see [Transfer SQL Server Objects Task](control-flow/transfer-sql-server-objects-task.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aca0-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체 전송 태스크를 만드는 사용자에게는 원본 서버 개체를 복사용으로 선택하기 위한 충분한 권한이 있어야 하며 해당 개체를 전송할 대상 서버 데이터베이스에 대한 액세스 권한도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-106">The user who creates the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task must have sufficient permissions on the source server objects to select them for copying, and permission to access the destination server database where the objects will be transferred.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="3aca0-107">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="3aca0-107">Static Options</span></span>  
 <span data-ttu-id="3aca0-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="3aca0-108">**SourceConnection**</span></span>  
 <span data-ttu-id="3aca0-109">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="3aca0-110">**SourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="3aca0-110">**SourceDatabase**</span></span>  
 <span data-ttu-id="3aca0-111">복사할 개체를 가져올 원본 서버의 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-111">Select a database on the source server from which objects will be copied.</span></span>  
  
 <span data-ttu-id="3aca0-112">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="3aca0-112">**DestinationConnection**</span></span>  
 <span data-ttu-id="3aca0-113">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-113">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="3aca0-114">**DestinationDatabase**</span><span class="sxs-lookup"><span data-stu-id="3aca0-114">**DestinationDatabase**</span></span>  
 <span data-ttu-id="3aca0-115">개체를 복사해 넣을 대상 서버의 데이터베이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-115">Select a database on the destination server to which objects will be copied.</span></span>  
  
 <span data-ttu-id="3aca0-116">**DropObjectsFirst**</span><span class="sxs-lookup"><span data-stu-id="3aca0-116">**DropObjectsFirst**</span></span>  
 <span data-ttu-id="3aca0-117">복사하기 전에 먼저 대상 서버에서 선택한 개체를 삭제할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-117">Select whether the selected objects will be dropped first on the destination server before copying.</span></span>  
  
 <span data-ttu-id="3aca0-118">**IncludeExtendedProperties**</span><span class="sxs-lookup"><span data-stu-id="3aca0-118">**IncludeExtendedProperties**</span></span>  
 <span data-ttu-id="3aca0-119">개체를 원본 서버에서 대상 서버로 복사할 때 확장 속성을 포함시킬지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-119">Select whether extended properties will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="3aca0-120">**CopyData**</span><span class="sxs-lookup"><span data-stu-id="3aca0-120">**CopyData**</span></span>  
 <span data-ttu-id="3aca0-121">개체를 원본 서버에서 대상 서버로 복사할 때 데이터를 포함시킬지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-121">Select whether data will be included when objects are copied from the source to the destination server.</span></span>  
  
 <span data-ttu-id="3aca0-122">**ExistingData**</span><span class="sxs-lookup"><span data-stu-id="3aca0-122">**ExistingData**</span></span>  
 <span data-ttu-id="3aca0-123">데이터를 대상 서버로 복사하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-123">Specify how data will be copied to the destination server.</span></span> <span data-ttu-id="3aca0-124">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-124">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="3aca0-125">값</span><span class="sxs-lookup"><span data-stu-id="3aca0-125">Value</span></span>|<span data-ttu-id="3aca0-126">Description</span><span class="sxs-lookup"><span data-stu-id="3aca0-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3aca0-127">**바꾸기**</span><span class="sxs-lookup"><span data-stu-id="3aca0-127">**Replace**</span></span>|<span data-ttu-id="3aca0-128">대상 서버의 데이터를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-128">Data on the destination server will be overwritten.</span></span>|  
|<span data-ttu-id="3aca0-129">**Append**</span><span class="sxs-lookup"><span data-stu-id="3aca0-129">**Append**</span></span>|<span data-ttu-id="3aca0-130">원본 서버에서 복사한 데이터를 대상 서버의 기존 데이터에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-130">Data copied from the source server will be appended to existing data on the destination server.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="3aca0-131">**ExistingData** 옵션은 **CopyData** 를 **True**로 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-131">The **ExistingData** option is only available when **CopyData** is set to **True**.</span></span>  
  
 <span data-ttu-id="3aca0-132">**CopySchema**</span><span class="sxs-lookup"><span data-stu-id="3aca0-132">**CopySchema**</span></span>  
 <span data-ttu-id="3aca0-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체 전송 태스크를 수행하는 동안 스키마를 복사할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-133">Select whether the schema is copied during the Transfer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Objects task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aca0-134">**CopySchema** 는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-134">**CopySchema** is only available for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-135">**UseCollation**</span><span class="sxs-lookup"><span data-stu-id="3aca0-135">**UseCollation**</span></span>  
 <span data-ttu-id="3aca0-136">개체 전송에 원본 서버에서 지정한 데이터 정렬을 포함시킬지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-136">Select whether the transfer of objects should include the collation specified on the source server.</span></span>  
  
 <span data-ttu-id="3aca0-137">**IncludeDependentObjects**</span><span class="sxs-lookup"><span data-stu-id="3aca0-137">**IncludeDependentObjects**</span></span>  
 <span data-ttu-id="3aca0-138">선택한 개체를 복사하면 이 개체에 종속된 다른 개체도 함께 복사되도록 할지 여부를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-138">Select whether copying the selected objects will cascade to include other objects that depend on the objects selected for copying.</span></span>  
  
 <span data-ttu-id="3aca0-139">**CopyAllObjects**</span><span class="sxs-lookup"><span data-stu-id="3aca0-139">**CopyAllObjects**</span></span>  
 <span data-ttu-id="3aca0-140">지정한 원본 데이터베이스의 모든 개체를 복사할지, 아니면 선택한 개체만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-140">Select whether the task will copy all objects in the specified source database or only selected objects.</span></span>  <span data-ttu-id="3aca0-141">이 옵션을 False로 설정하면 전송할 개체를 선택할 수 있고 **CopyAllObjects**섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-141">Setting this option to False gives you the option to select the objects to transfer, and displays the dynamic options in the section, **CopyAllObjects**.</span></span>  
  
 <span data-ttu-id="3aca0-142">**ObjectsToCopy**</span><span class="sxs-lookup"><span data-stu-id="3aca0-142">**ObjectsToCopy**</span></span>  
 <span data-ttu-id="3aca0-143">원본 데이터베이스에서 대상 데이터베이스로 복사할 개체를 지정하려면 **ObjectsToCopy** 를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-143">Expand **ObjectsToCopy** to specify which objects should be copied from the source database to the destination database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aca0-144">**ObjectsToCopy** 는 **CopyAllObjects** 를 **False**로 설정한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-144">**ObjectsToCopy** is only available when **CopyAllObjects** is set to **False**.</span></span>  
  
 <span data-ttu-id="3aca0-145">다음 유형의 개체를 복사하는 옵션은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-145">The options to copy the following types of objects are supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="3aca0-146">어셈블리</span><span class="sxs-lookup"><span data-stu-id="3aca0-146">Assemblies</span></span>  
  
 <span data-ttu-id="3aca0-147">파티션 함수</span><span class="sxs-lookup"><span data-stu-id="3aca0-147">Partition functions</span></span>  
  
 <span data-ttu-id="3aca0-148">파티션 구성표</span><span class="sxs-lookup"><span data-stu-id="3aca0-148">Partition schemes</span></span>  
  
 <span data-ttu-id="3aca0-149">스키마</span><span class="sxs-lookup"><span data-stu-id="3aca0-149">Schemas</span></span>  
  
 <span data-ttu-id="3aca0-150">사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="3aca0-150">User-defined aggregates</span></span>  
  
 <span data-ttu-id="3aca0-151">사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="3aca0-151">User-defined types</span></span>  
  
 <span data-ttu-id="3aca0-152">XML 스키마 컬렉션</span><span class="sxs-lookup"><span data-stu-id="3aca0-152">XML schema collections</span></span>  
  
 <span data-ttu-id="3aca0-153">**CopyDatabaseUsers**</span><span class="sxs-lookup"><span data-stu-id="3aca0-153">**CopyDatabaseUsers**</span></span>  
 <span data-ttu-id="3aca0-154">데이터베이스 사용자를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-154">Specify whether database users should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-155">**CopyDatabaseRoles**</span><span class="sxs-lookup"><span data-stu-id="3aca0-155">**CopyDatabaseRoles**</span></span>  
 <span data-ttu-id="3aca0-156">데이터베이스 역할을 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-156">Specify whether database roles should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-157">**CopySqlServerLogins**</span><span class="sxs-lookup"><span data-stu-id="3aca0-157">**CopySqlServerLogins**</span></span>  
 <span data-ttu-id="3aca0-158">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로그인을 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-158">Specify whether [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-159">**CopyObjectLevelPermissions**</span><span class="sxs-lookup"><span data-stu-id="3aca0-159">**CopyObjectLevelPermissions**</span></span>  
 <span data-ttu-id="3aca0-160">개체 수준 사용 권한을 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-160">Specify whether object-level permissions should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-161">**CopyIndexes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-161">**CopyIndexes**</span></span>  
 <span data-ttu-id="3aca0-162">인덱스를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-162">Specify whether indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-163">**CopyTriggers**</span><span class="sxs-lookup"><span data-stu-id="3aca0-163">**CopyTriggers**</span></span>  
 <span data-ttu-id="3aca0-164">트리거를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-164">Specify whether triggers should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-165">**CopyFullTextIndexes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-165">**CopyFullTextIndexes**</span></span>  
 <span data-ttu-id="3aca0-166">전체 텍스트 인덱스를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-166">Specify whether full-text indexes should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-167">**CopyPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="3aca0-167">**CopyPrimaryKeys**</span></span>  
 <span data-ttu-id="3aca0-168">기본 키를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-168">Specify whether primary keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-169">**CopyForeignKeys**</span><span class="sxs-lookup"><span data-stu-id="3aca0-169">**CopyForeignKeys**</span></span>  
 <span data-ttu-id="3aca0-170">외래 키를 전송에 포함시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-170">Specify whether foreign keys should be included in the transfer.</span></span>  
  
 <span data-ttu-id="3aca0-171">**GenerateScriptsInUnicode**</span><span class="sxs-lookup"><span data-stu-id="3aca0-171">**GenerateScriptsInUnicode**</span></span>  
 <span data-ttu-id="3aca0-172">생성된 전송 스크립트가 유니코드 형식인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-172">Specify whether the generated transfer scripts are in Unicode format.</span></span>  
  
## <a name="dynamic-options"></a><span data-ttu-id="3aca0-173">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="3aca0-173">Dynamic Options</span></span>  
  
### <a name="copyallobjects--false"></a><span data-ttu-id="3aca0-174">CopyAllObjects = False</span><span class="sxs-lookup"><span data-stu-id="3aca0-174">CopyAllObjects = False</span></span>  
 <span data-ttu-id="3aca0-175">**CopyAllTables**</span><span class="sxs-lookup"><span data-stu-id="3aca0-175">**CopyAllTables**</span></span>  
 <span data-ttu-id="3aca0-176">지정한 원본 데이터베이스의 모든 테이블을 복사할지, 아니면 선택한 테이블만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-176">Select whether the task will copy all tables in the specified source database or only the selected tables.</span></span>  
  
 <span data-ttu-id="3aca0-177">**TablesList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-177">**TablesList**</span></span>  
 <span data-ttu-id="3aca0-178">**테이블 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-178">Click to open the **Select Tables** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-179">**CopyAllViews**</span><span class="sxs-lookup"><span data-stu-id="3aca0-179">**CopyAllViews**</span></span>  
 <span data-ttu-id="3aca0-180">지정한 원본 데이터베이스의 모든 뷰를 복사할지, 아니면 선택한 뷰만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-180">Select whether the task will copy all views in the specified source database or only the selected views.</span></span>  
  
 <span data-ttu-id="3aca0-181">**ViewsList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-181">**ViewsList**</span></span>  
 <span data-ttu-id="3aca0-182">**뷰 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-182">Click to open the **Select Views** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-183">**CopyAllStoredProcedures**</span><span class="sxs-lookup"><span data-stu-id="3aca0-183">**CopyAllStoredProcedures**</span></span>  
 <span data-ttu-id="3aca0-184">지정한 원본 데이터베이스의 모든 사용자 정의 저장 프로시저를 복사할지, 아니면 선택한 프로시저만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-184">Select whether the task will copy all user-defined stored procedures in the specified source database or only the selected procedures.</span></span>  
  
 <span data-ttu-id="3aca0-185">**StoredProceduresList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-185">**StoredProceduresList**</span></span>  
 <span data-ttu-id="3aca0-186">**저장 프로시저 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-186">Click to open the **Select Stored Procedures** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-187">**CopyAllUserDefinedFunctions**</span><span class="sxs-lookup"><span data-stu-id="3aca0-187">**CopyAllUserDefinedFunctions**</span></span>  
 <span data-ttu-id="3aca0-188">지정한 원본 데이터베이스의 모든 사용자 정의 함수를 복사할지, 아니면 선택한 UDF만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-188">Select whether the task will copy all user-defined functions in the specified source database or only the selected UDFs.</span></span>  
  
 <span data-ttu-id="3aca0-189">**UserDefinedFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-189">**UserDefinedFunctionsList**</span></span>  
 <span data-ttu-id="3aca0-190">**사용자 정의 함수 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-190">Click to open the **Select User Defined Functions** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-191">**CopyAllDefaults**</span><span class="sxs-lookup"><span data-stu-id="3aca0-191">**CopyAllDefaults**</span></span>  
 <span data-ttu-id="3aca0-192">지정한 원본 데이터베이스의 모든 기본값을 복사할지, 아니면 선택한 기본값만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-192">Select whether the task will copy all defaults in the specified source database or only the selected defaults.</span></span>  
  
 <span data-ttu-id="3aca0-193">**DefaultsList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-193">**DefaultsList**</span></span>  
 <span data-ttu-id="3aca0-194">**기본값 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-194">Click to open the **Select Defaults** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-195">**CopyAllUserDefinedDataTypes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-195">**CopyAllUserDefinedDataTypes**</span></span>  
 <span data-ttu-id="3aca0-196">지정한 원본 데이터베이스의 모든 사용자 정의 데이터 형식을 복사할지, 아니면 선택한 사용자 정의 데이터 형식만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-196">Select whether the task will copy all user-defined data types in the specified source database or only the selected user-defined data types.</span></span>  
  
 <span data-ttu-id="3aca0-197">**UserDefinedDataTypesList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-197">**UserDefinedDataTypesList**</span></span>  
 <span data-ttu-id="3aca0-198">**사용자 정의 데이터 형식 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-198">Click to open the **Select User-Defined Data Types** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-199">**CopyAllPartitionFunctions**</span><span class="sxs-lookup"><span data-stu-id="3aca0-199">**CopyAllPartitionFunctions**</span></span>  
 <span data-ttu-id="3aca0-200">지정한 원본 데이터베이스의 모든 사용자 정의 파티션 함수를 복사할지, 아니면 선택한 파티션 함수만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-200">Select whether the task will copy all user-defined partition functions in the specified source database or only the selected partition functions.</span></span> <span data-ttu-id="3aca0-201">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-201">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-202">**PartitionFunctionsList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-202">**PartitionFunctionsList**</span></span>  
 <span data-ttu-id="3aca0-203">**파티션 함수 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-203">Click to open the **Select Partition Functions** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-204">**CopyAllPartitionSchemes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-204">**CopyAllPartitionSchemes**</span></span>  
 <span data-ttu-id="3aca0-205">지정한 원본 데이터베이스의 모든 파티션 구성표를 복사할지, 아니면 선택한 파티션 구성표만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-205">Select whether the task will copy all partition schemes in the specified source database or only the selected partition schemes.</span></span> <span data-ttu-id="3aca0-206">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-206">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-207">**PartitionSchemesList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-207">**PartitionSchemesList**</span></span>  
 <span data-ttu-id="3aca0-208">**파티션 구성표 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-208">Click to open the **Select Partition Schemes** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-209">**CopyAllSchemas**</span><span class="sxs-lookup"><span data-stu-id="3aca0-209">**CopyAllSchemas**</span></span>  
 <span data-ttu-id="3aca0-210">지정한 원본 데이터베이스의 모든 스키마를 복사할지, 아니면 선택한 스키마만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-210">Select whether the task will copy all schemas in the specified source database or only the selected schemas.</span></span> <span data-ttu-id="3aca0-211">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-211">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-212">**SchemasList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-212">**SchemasList**</span></span>  
 <span data-ttu-id="3aca0-213">**스키마 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-213">Click to open the **Select Schemas** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-214">**CopyAllSqlAssemblies**</span><span class="sxs-lookup"><span data-stu-id="3aca0-214">**CopyAllSqlAssemblies**</span></span>  
 <span data-ttu-id="3aca0-215">지정한 원본 데이터베이스의 모든 SQL 어셈블리를 복사할지, 아니면 선택한 SQL 어셈블리만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-215">Select whether the task will copy all SQL assemblies in the specified source database or only the selected SQL assemblies.</span></span> <span data-ttu-id="3aca0-216">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-216">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-217">**SqlAssembliesList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-217">**SqlAssembliesList**</span></span>  
 <span data-ttu-id="3aca0-218">**SQL 어셈블리 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-218">Click to open the **Select SQL Assemblies** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-219">**CopyAllUserDefinedAggregates**</span><span class="sxs-lookup"><span data-stu-id="3aca0-219">**CopyAllUserDefinedAggregates**</span></span>  
 <span data-ttu-id="3aca0-220">지정한 원본 데이터베이스의 모든 사용자 정의 집계를 복사할지, 아니면 선택한 사용자 정의 집계만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-220">Select whether the task will copy all user-defined aggregates in the specified source database or only the selected user-defined aggregates.</span></span> <span data-ttu-id="3aca0-221">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-221">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-222">**UserDefinedAggregatesList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-222">**UserDefinedAggregatesList**</span></span>  
 <span data-ttu-id="3aca0-223">**사용자 정의 집계 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-223">Click to open the **Select User-Defined Aggregates** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-224">**CopyAllUserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-224">**CopyAllUserDefinedTypes**</span></span>  
 <span data-ttu-id="3aca0-225">지정한 원본 데이터베이스의 모든 사용자 정의 유형을 복사할지, 아니면 선택한 UDT만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-225">Select whether the task will copy all user-defined types in the specified source database or only the selected UDTs.</span></span> <span data-ttu-id="3aca0-226">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-226">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-227">**UserDefinedTypes**</span><span class="sxs-lookup"><span data-stu-id="3aca0-227">**UserDefinedTypes**</span></span>  
 <span data-ttu-id="3aca0-228">**사용자 정의 유형 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-228">Click to open the **Select User-Defined Types** dialog box.</span></span>  
  
 <span data-ttu-id="3aca0-229">**CopyAllXmlSchemaCollections**</span><span class="sxs-lookup"><span data-stu-id="3aca0-229">**CopyAllXmlSchemaCollections**</span></span>  
 <span data-ttu-id="3aca0-230">지정한 원본 데이터베이스의 모든 XML 스키마 컬렉션을 복사할지, 아니면 선택한 XML 스키마 컬렉션만 복사할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-230">Select whether the task will copy all XML Schema collections in the specified source database or only the selected XML schema collections.</span></span> <span data-ttu-id="3aca0-231">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-231">Supported only on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3aca0-232">**XmlSchemaCollectionsList**</span><span class="sxs-lookup"><span data-stu-id="3aca0-232">**XmlSchemaCollectionsList**</span></span>  
 <span data-ttu-id="3aca0-233">**XML 스키마 컬렉션 선택** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3aca0-233">Click to open the **Select XML Schema Collections** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aca0-234">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aca0-234">See Also</span></span>  
 <span data-ttu-id="3aca0-235">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3aca0-235">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="3aca0-236">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="3aca0-236">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="3aca0-237">[SQL Server 개체 전송 태스크 편집기&#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="3aca0-237">[Transfer SQL Server Objects Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="3aca0-238">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="3aca0-238">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="3aca0-239">[대량 가져오기 또는 대량 내보내기를 위한 데이터 형식&#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3aca0-239">[Data Formats for Bulk Import or Bulk Export &#40;SQL Server&#41;](../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md) </span></span>  
 [<span data-ttu-id="3aca0-240">SQL Server 설치에 대한 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3aca0-240">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
