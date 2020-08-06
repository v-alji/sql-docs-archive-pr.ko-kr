---
title: OLE DB 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdestadapter.connection.f1
helpviewer_keywords:
- OLE DB Destination Editor
ms.assetid: ae2200c6-8ba0-49b7-b01a-53425b84d2ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7217380d664ac5d20cf1ba7b437924ee3460841b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647756"
---
# <a name="ole-db-destination-editor-connection-manager-page"></a><span data-ttu-id="dc046-102">OLE DB 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="dc046-102">OLE DB Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="dc046-103">**OLE DB 대상 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 대상에 대한 OLE DB 연결을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-103">Use the **Connection Manager** page of the **OLE DB Destination Editor** dialog box to select the OLE DB connection for the destination.</span></span> <span data-ttu-id="dc046-104">이 페이지를 사용하면 데이터베이스에서 테이블이나 뷰를 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-104">This page also lets you select a table or view from the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-105">`CommandTimeout`OLE DB 대상의 속성은 **OLE DB 대상 편집기**에서 사용할 수 없지만 **고급 편집기**를 사용 하 여 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-105">The `CommandTimeout` property of the OLE DB destination is not available in the **OLE DB Destination Editor**, but can be set by using the **Advanced Editor**.</span></span> <span data-ttu-id="dc046-106">또한 특정 빠른 로드 옵션은 **고급 편집기**에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-106">In addition, certain fast load options are available only in the **Advanced Editor**.</span></span> <span data-ttu-id="dc046-107">이러한 속성에 대한 자세한 내용은 [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)의 OLE DB 대상 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-107">For more information on these properties, see the OLE DB Destination section of [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md).</span></span>  
  
 <span data-ttu-id="dc046-108">OLE DB 대상에 대한 자세한 내용은 [OLE DB Destination](data-flow/ole-db-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-108">To learn more about the OLE DB destination, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="dc046-109">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="dc046-109">Static Options</span></span>  
 <span data-ttu-id="dc046-110">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="dc046-110">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="dc046-111">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-111">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="dc046-112">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="dc046-112">**New**</span></span>  
 <span data-ttu-id="dc046-113">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-113">Create a new connection manager by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="dc046-114">**데이터 액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="dc046-114">**Data access mode**</span></span>  
 <span data-ttu-id="dc046-115">대상으로 데이터를 로드하는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-115">Specify the method for loading data into the destination.</span></span> <span data-ttu-id="dc046-116">DBCS(더블바이트 문자 집합) 데이터는 빠른 로드 옵션 중 하나를 사용하여 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-116">Loading double-byte character set (DBCS) data requires use of one of the fast load options.</span></span> <span data-ttu-id="dc046-117">대량 삽입에 최적화된 빠른 로드 데이터 액세스 모드에 대한 자세한 내용은 [OLE DB Destination](data-flow/ole-db-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-117">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>  
  
|<span data-ttu-id="dc046-118">옵션</span><span class="sxs-lookup"><span data-stu-id="dc046-118">Option</span></span>|<span data-ttu-id="dc046-119">Description</span><span class="sxs-lookup"><span data-stu-id="dc046-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dc046-120">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="dc046-120">Table or view</span></span>|<span data-ttu-id="dc046-121">OLE DB 대상의 테이블 또는 뷰로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-121">Load data into a table or view in the OLE DB destination.</span></span>|  
|<span data-ttu-id="dc046-122">테이블 또는 뷰 - 빠른 로드</span><span class="sxs-lookup"><span data-stu-id="dc046-122">Table or view - fast load</span></span>|<span data-ttu-id="dc046-123">빠른 로드 옵션을 사용하여 OLE DB 대상의 테이블 또는 뷰로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-123">Load data into a table or view in the OLE DB destination and use the fast load option.</span></span> <span data-ttu-id="dc046-124">대량 삽입에 최적화된 빠른 로드 데이터 액세스 모드에 대한 자세한 내용은 [OLE DB Destination](data-flow/ole-db-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-124">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="dc046-125">테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="dc046-125">Table name or view name variable</span></span>|<span data-ttu-id="dc046-126">변수에 테이블 또는 뷰 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-126">Specify the table or view name in a variable.</span></span><br /><br /> <span data-ttu-id="dc046-127">**관련 정보**: [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)</span><span class="sxs-lookup"><span data-stu-id="dc046-127">**Related information**: [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md)</span></span>|  
|<span data-ttu-id="dc046-128">테이블 이름 또는 뷰 이름 변수 - 빠른 로드</span><span class="sxs-lookup"><span data-stu-id="dc046-128">Table name or view name variable - fast load</span></span>|<span data-ttu-id="dc046-129">변수에 테이블 이름 또는 뷰 이름을 지정하고 빠른 로드 옵션을 사용하여 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-129">Specify the table or view name in a variable, and use the fast load option to load the data.</span></span> <span data-ttu-id="dc046-130">대량 삽입에 최적화된 빠른 로드 데이터 액세스 모드에 대한 자세한 내용은 [OLE DB Destination](data-flow/ole-db-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-130">For more information about the fast load data access modes, which are optimized for bulk inserts, see [OLE DB Destination](data-flow/ole-db-destination.md).</span></span>|  
|<span data-ttu-id="dc046-131">SQL 명령</span><span class="sxs-lookup"><span data-stu-id="dc046-131">SQL command</span></span>|<span data-ttu-id="dc046-132">SQL 쿼리를 사용하여 OLE DB 대상으로 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-132">Load data into the OLE DB destination by using a SQL query.</span></span>|  
  
 <span data-ttu-id="dc046-133">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="dc046-133">**Preview**</span></span>  
 <span data-ttu-id="dc046-134">**쿼리 결과 미리 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-134">Preview results by using the **Preview Query Results** dialog box.</span></span> <span data-ttu-id="dc046-135">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-135">Preview can display up to 200 rows.</span></span>  
  
## <a name="data-access-mode-dynamic-options"></a><span data-ttu-id="dc046-136">데이터 액세스 모드 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="dc046-136">Data Access Mode Dynamic Options</span></span>  
 <span data-ttu-id="dc046-137">각 **데이터 액세스 모드** 설정은 해당 설정에 따라 동적 옵션 집합이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-137">Each of the settings for **Data access mode** displays a dynamic set of options specific to that setting.</span></span> <span data-ttu-id="dc046-138">다음 섹션에서는 각 **데이터 액세스 모드** 설정에 따라 사용할 수 있는 동적 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-138">The following sections describe each of the dynamic options available for each **Data access mode** setting.</span></span>  
  
### <a name="data-access-mode--table-or-view"></a><span data-ttu-id="dc046-139">데이터 액세스 모드 = 테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="dc046-139">Data access mode = Table or view</span></span>  
 <span data-ttu-id="dc046-140">**테이블 또는 뷰 이름**</span><span class="sxs-lookup"><span data-stu-id="dc046-140">**Name of the table or the view**</span></span>  
 <span data-ttu-id="dc046-141">데이터 원본의 사용 가능한 테이블 또는 뷰 목록에서 테이블 또는 뷰 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-141">Select the name of the table or view from a list of those available in the data source.</span></span>  
  
 <span data-ttu-id="dc046-142">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="dc046-142">**New**</span></span>  
 <span data-ttu-id="dc046-143">**테이블 만들기** 대화 상자를 사용하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-143">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-144">**새로 만들기**를 클릭하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-144">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="dc046-145">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-145">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="dc046-146">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-146">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="dc046-147">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-147">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="dc046-148">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc046-148">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
### <a name="data-access-mode--table-or-view---fast-load"></a><span data-ttu-id="dc046-149">데이터 액세스 모드 = 테이블 또는 뷰 - 빠른 로드</span><span class="sxs-lookup"><span data-stu-id="dc046-149">Data access mode = Table or view - fast load</span></span>  
 <span data-ttu-id="dc046-150">**테이블 또는 뷰 이름**</span><span class="sxs-lookup"><span data-stu-id="dc046-150">**Name of the table or view**</span></span>  
 <span data-ttu-id="dc046-151">이 목록을 사용하여 데이터베이스에서 테이블 또는 뷰를 선택하거나 **새로 만들기**를 클릭하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-151">Select a table or view from the database by using this list, or create a new table by clicking **New**.</span></span>  
  
 <span data-ttu-id="dc046-152">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="dc046-152">**New**</span></span>  
 <span data-ttu-id="dc046-153">**테이블 만들기** 대화 상자를 사용하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-153">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-154">**새로 만들기**를 클릭하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-154">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="dc046-155">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-155">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="dc046-156">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-156">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="dc046-157">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-157">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="dc046-158">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc046-158">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="dc046-159">**ID 유지**</span><span class="sxs-lookup"><span data-stu-id="dc046-159">**Keep identity**</span></span>  
 <span data-ttu-id="dc046-160">데이터를 로드할 때 ID 값을 복사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-160">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="dc046-161">이 속성은 빠른 로드 옵션을 사용할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-161">This property is available only with the fast load option.</span></span> <span data-ttu-id="dc046-162">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-162">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-163">**Null 유지**</span><span class="sxs-lookup"><span data-stu-id="dc046-163">**Keep nulls**</span></span>  
 <span data-ttu-id="dc046-164">데이터를 로드할 때 Null 값을 복사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-164">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="dc046-165">이 속성은 빠른 로드 옵션을 사용할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-165">This property is available only with the fast load option.</span></span> <span data-ttu-id="dc046-166">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-166">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-167">**테이블 잠금**</span><span class="sxs-lookup"><span data-stu-id="dc046-167">**Table lock**</span></span>  
 <span data-ttu-id="dc046-168">로드하는 동안 테이블 잠금을 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-168">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="dc046-169">이 속성의 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-169">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="dc046-170">**CHECK 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="dc046-170">**Check constraints**</span></span>  
 <span data-ttu-id="dc046-171">대상에서 데이터를 로드할 때 제약 조건을 검사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-171">Specify whether the destination checks constraints when it loads data.</span></span> <span data-ttu-id="dc046-172">이 속성의 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-172">The default value of this property is `true`.</span></span>  
  
 <span data-ttu-id="dc046-173">**일괄 처리당 행 수**</span><span class="sxs-lookup"><span data-stu-id="dc046-173">**Rows per batch**</span></span>  
 <span data-ttu-id="dc046-174">일괄 처리의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-174">Specify the number of rows in a batch.</span></span> <span data-ttu-id="dc046-175">이 속성의 기본값은 값이 할당되지 않음을 나타내는 **-1**입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-175">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-176">이 속성에 사용자 지정 값을 할당하지 않으려면 **OLE DB 대상 편집기** 에서 해당 입력란의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-176">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="dc046-177">**최대 삽입 커밋 크기**</span><span class="sxs-lookup"><span data-stu-id="dc046-177">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="dc046-178">OLE DB 대상에서 빠른 로드 작업을 수행하는 동안 커밋을 시도하는 일괄 처리 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-178">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="dc046-179">값이 **0** 이면 모든 행이 처리된 다음 모든 데이터가 단일 일괄 처리로 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-179">The value of **0** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-180">OLE DB 대상 및 다른 데이터 흐름 구성 요소에서 동일한 원본 테이블을 업데이트하는 경우 값 **0** 을 지정하면 실행 중인 패키지가 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-180">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="dc046-181">패키지가 중지하지 않도록 하려면 **최대 삽입 커밋 크기** 옵션을 **2147483647**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-181">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
 <span data-ttu-id="dc046-182">이 속성에 값을 지정하면 대상에서 (1) **최대 삽입 커밋 크기**보다 작은 일괄 처리의 행이나 (2) 현재 처리 중인 버퍼에 남아 있는 행이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-182">If you provide a value for this property, the destination commits rows in batches that are the smaller of (a) the **Maximum insert commit size**, or (b) the remaining rows in the buffer that is currently being processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-183">대상에서 제약 조건에 맞지 않아 오류가 발생하면 **최대 삽입 커밋 크기** 에 의해 정의된 행에 대한 전체 일괄 처리가 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-183">Any constraint failure at the destination causes the entire batch of rows defined by **Maximum insert commit size** to fail.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable"></a><span data-ttu-id="dc046-184">데이터 액세스 모드 = 테이블 이름 또는 뷰 이름 변수</span><span class="sxs-lookup"><span data-stu-id="dc046-184">Data access mode = Table name or view name variable</span></span>  
 <span data-ttu-id="dc046-185">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="dc046-185">**Variable name**</span></span>  
 <span data-ttu-id="dc046-186">테이블 또는 뷰 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-186">Select the variable that contains the name of the table or view.</span></span>  
  
### <a name="data-access-mode--table-name-or-view-name-variable---fast-load"></a><span data-ttu-id="dc046-187">데이터 액세스 모드 = 테이블 이름 또는 뷰 이름 변수 - 빠른 로드</span><span class="sxs-lookup"><span data-stu-id="dc046-187">Data Access Mode = Table name or view name variable - fast load)</span></span>  
 <span data-ttu-id="dc046-188">**변수 이름**</span><span class="sxs-lookup"><span data-stu-id="dc046-188">**Variable name**</span></span>  
 <span data-ttu-id="dc046-189">테이블 또는 뷰 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-189">Select the variable that contains the name of the table or view.</span></span>  
  
 <span data-ttu-id="dc046-190">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="dc046-190">**New**</span></span>  
 <span data-ttu-id="dc046-191">**테이블 만들기** 대화 상자를 사용하여 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-191">Create a new table by using the **Create Table** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-192">**새로 만들기**를 클릭하면 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 연결된 데이터 원본에 따라 기본 CREATE TABLE 문을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-192">When you click **New**, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] generates a default CREATE TABLE statement based on the connected data source.</span></span> <span data-ttu-id="dc046-193">원본 테이블에 선언된 FILESTREAM 특성이 포함된 열이 있어도 기본 CREATE TABLE 문은 FILESTREAM 특성을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-193">This default CREATE TABLE statement will not include the FILESTREAM attribute even if the source table includes a column with the FILESTREAM attribute declared.</span></span> <span data-ttu-id="dc046-194">FILESTREAM 특성이 포함된 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 구성 요소를 실행하려면 먼저 대상 데이터베이스에서 FILESTREAM 스토리지를 구현하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-194">To run an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] component with the FILESTREAM attribute, first implement FILESTREAM storage on the destination database.</span></span> <span data-ttu-id="dc046-195">그런 다음 **테이블 만들기** 대화 상자에서 FILESTREAM 특성을 CREATE TABLE 문에 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-195">Then, add the FILESTREAM attribute to the CREATE TABLE statement in the **Create Table** dialog box.</span></span> <span data-ttu-id="dc046-196">자세한 내용은 [Blob&#40;Binary Large Object&#41; 데이터&#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc046-196">For more information, see [Binary Large Object &#40;Blob&#41; Data &#40;SQL Server&#41;](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="dc046-197">**ID 유지**</span><span class="sxs-lookup"><span data-stu-id="dc046-197">**Keep identity**</span></span>  
 <span data-ttu-id="dc046-198">데이터를 로드할 때 ID 값을 복사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-198">Specify whether to copy identity values when data is loaded.</span></span> <span data-ttu-id="dc046-199">이 속성은 빠른 로드 옵션을 사용할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-199">This property is available only with the fast load option.</span></span> <span data-ttu-id="dc046-200">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-200">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-201">**Null 유지**</span><span class="sxs-lookup"><span data-stu-id="dc046-201">**Keep nulls**</span></span>  
 <span data-ttu-id="dc046-202">데이터를 로드할 때 Null 값을 복사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-202">Specify whether to copy null values when data is loaded.</span></span> <span data-ttu-id="dc046-203">이 속성은 빠른 로드 옵션을 사용할 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-203">This property is available only with the fast load option.</span></span> <span data-ttu-id="dc046-204">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-204">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-205">**테이블 잠금**</span><span class="sxs-lookup"><span data-stu-id="dc046-205">**Table lock**</span></span>  
 <span data-ttu-id="dc046-206">로드하는 동안 테이블 잠금을 설정할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-206">Specify whether the table is locked during the load.</span></span> <span data-ttu-id="dc046-207">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-207">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-208">**CHECK 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="dc046-208">**Check constraints**</span></span>  
 <span data-ttu-id="dc046-209">태스크에서 제약 조건을 검사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-209">Specify whether the task checks constraints.</span></span> <span data-ttu-id="dc046-210">이 속성의 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-210">The default value of this property is `false`.</span></span>  
  
 <span data-ttu-id="dc046-211">**일괄 처리당 행 수**</span><span class="sxs-lookup"><span data-stu-id="dc046-211">**Rows per batch**</span></span>  
 <span data-ttu-id="dc046-212">일괄 처리의 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-212">Specify the number of rows in a batch.</span></span> <span data-ttu-id="dc046-213">이 속성의 기본값은 값이 할당되지 않음을 나타내는 **-1**입니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-213">The default value of this property is **-1**, which indicates that no value has been assigned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-214">이 속성에 사용자 지정 값을 할당하지 않으려면 **OLE DB 대상 편집기** 에서 해당 입력란의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-214">Clear the text box in the **OLE DB Destination Editor** to indicate that you do not want to assign a custom value for this property.</span></span>  
  
 <span data-ttu-id="dc046-215">**최대 삽입 커밋 크기**</span><span class="sxs-lookup"><span data-stu-id="dc046-215">**Maximum insert commit size**</span></span>  
 <span data-ttu-id="dc046-216">OLE DB 대상에서 빠른 로드 작업을 수행하는 동안 커밋을 시도하는 일괄 처리 크기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-216">Specify the batch size that the OLE DB destination tries to commit during fast load operations.</span></span> <span data-ttu-id="dc046-217">기본값은 **2147483647** 이며 이 경우 모든 행이 처리된 다음 모든 데이터가 단일 일괄 처리로 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-217">The default value of **2147483647** indicates that all data is committed in a single batch after all rows have been processed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-218">OLE DB 대상 및 다른 데이터 흐름 구성 요소에서 동일한 원본 테이블을 업데이트하는 경우 값 **0** 을 지정하면 실행 중인 패키지가 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-218">A value of **0** might cause the running package to stop responding if the OLE DB destination and another data flow component are updating the same source table.</span></span> <span data-ttu-id="dc046-219">패키지가 중지하지 않도록 하려면 **최대 삽입 커밋 크기** 옵션을 **2147483647**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-219">To prevent the package from stopping, set the **Maximum insert commit size** option to **2147483647**.</span></span>  
  
### <a name="data-access-mode--sql-command"></a><span data-ttu-id="dc046-220">데이터 액세스 모드 = SQL 명령</span><span class="sxs-lookup"><span data-stu-id="dc046-220">Data access mode = SQL command</span></span>  
 <span data-ttu-id="dc046-221">**SQL 명령 텍스트**</span><span class="sxs-lookup"><span data-stu-id="dc046-221">**SQL command text**</span></span>  
 <span data-ttu-id="dc046-222">SQL 쿼리 텍스트를 입력하고 **쿼리 작성**을 클릭하여 쿼리를 작성하거나 **찾아보기**를 클릭하여 쿼리 텍스트가 포함된 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-222">Enter the text of a SQL query, build the query by clicking **Build Query**, or locate the file that contains the query text by clicking **Browse**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc046-223">OLE DB 대상은 매개 변수를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-223">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="dc046-224">매개 변수가 있는 INSERT 문을 실행해야 하는 경우 OLE DB 명령 변환을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="dc046-224">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="dc046-225">자세한 내용은 [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc046-225">For more information, see [OLE DB Command Transformation](data-flow/transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="dc046-226">**쿼리 작성**</span><span class="sxs-lookup"><span data-stu-id="dc046-226">**Build query**</span></span>  
 <span data-ttu-id="dc046-227">**쿼리 작성기** 대화 상자를 사용하여 시각적으로 SQL 쿼리를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-227">Use the **Query Builder** dialog box to construct the SQL query visually.</span></span>  
  
 <span data-ttu-id="dc046-228">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="dc046-228">**Browse**</span></span>  
 <span data-ttu-id="dc046-229">**열기** 대화 상자를 사용하여 SQL 쿼리 텍스트가 포함된 파일을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-229">Use the **Open** dialog box to locate the file that contains the text of the SQL query.</span></span>  
  
 <span data-ttu-id="dc046-230">**쿼리 구문 분석**</span><span class="sxs-lookup"><span data-stu-id="dc046-230">**Parse query**</span></span>  
 <span data-ttu-id="dc046-231">쿼리 텍스트의 구문을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dc046-231">Verify the syntax of the query text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc046-232">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dc046-232">See Also</span></span>  
 <span data-ttu-id="dc046-233">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="dc046-233">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="dc046-234">[OLE DB 대상 편집기 &#40;매핑 페이지&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="dc046-234">[OLE DB Destination Editor &#40;Mappings Page&#41;](../../2014/integration-services/ole-db-destination-editor-mappings-page.md) </span></span>  
 <span data-ttu-id="dc046-235">[대상 편집기 &#40;오류 출력 페이지를 OLE DB&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="dc046-235">[OLE DB Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ole-db-destination-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="dc046-236">OLE DB 대상을 사용하여 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="dc046-236">Load Data by Using the OLE DB Destination</span></span>](data-flow/load-data-by-using-the-ole-db-destination.md)  
  
  
