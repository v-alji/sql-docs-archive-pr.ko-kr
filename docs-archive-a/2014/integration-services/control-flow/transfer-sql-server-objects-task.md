---
title: SQL Server 개체 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfersqlserverobjectstask.f1
helpviewer_keywords:
- Transfer SQL Server Objects task [Integration Services]
ms.assetid: fe86d6e5-e415-406c-88f3-dc3ef71bd5f0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 281acb189e8f4dcfde9dc7ad1d2a74525236d28d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638919"
---
# <a name="transfer-sql-server-objects-task"></a><span data-ttu-id="11221-102">SQL Server 개체 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="11221-102">Transfer SQL Server Objects Task</span></span>
  <span data-ttu-id="11221-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 간에 한 가지 이상 유형의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]데이터베이스 개체를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-103">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers one or more types of objects in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="11221-104">예를 들어 이 태스크로 테이블 및 저장 프로시저를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-104">For example, the task can copy tables and stored procedures.</span></span> <span data-ttu-id="11221-105">원본으로 사용하는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전에 따라 복사할 수 있는 개체 유형이 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="11221-105">Depending on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is used as a source, different types of objects are available to copy.</span></span> <span data-ttu-id="11221-106">예를 들어 스키마 및 사용자 정의 집계는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에만 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-106">For example, only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database includes schemas and user-defined aggregates.</span></span>  
  
## <a name="objects-to-transfer"></a><span data-ttu-id="11221-107">전송할 개체</span><span class="sxs-lookup"><span data-stu-id="11221-107">Objects to Transfer</span></span>  
 <span data-ttu-id="11221-108">전송되는 개체에 대한 사용 권한과 함께 지정된 데이터베이스의 서버 역할, 역할 및 사용자를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-108">Server roles, roles, and users from the specified database can be copied, as well as the permissions for the transferred objects.</span></span> <span data-ttu-id="11221-109">개체와 관련된 사용자, 역할 및 사용 권한을 복사하면 전송되는 개체를 대상 서버에서 즉시 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-109">By copying the associated users, roles, and permissions together with the objects, you can make the transferred objects immediately operable on the destination server.</span></span>  
  
 <span data-ttu-id="11221-110">다음 표에서는 복사할 수 있는 개체 유형을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-110">The following table lists the type of objects that can be copied.</span></span>  
  
|<span data-ttu-id="11221-111">Object</span><span class="sxs-lookup"><span data-stu-id="11221-111">Object</span></span>|  
|------------|  
|<span data-ttu-id="11221-112">테이블</span><span class="sxs-lookup"><span data-stu-id="11221-112">Tables</span></span>|  
|<span data-ttu-id="11221-113">뷰</span><span class="sxs-lookup"><span data-stu-id="11221-113">Views</span></span>|  
|<span data-ttu-id="11221-114">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="11221-114">Stored Procedures</span></span>|  
|<span data-ttu-id="11221-115">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="11221-115">User-Defined Functions</span></span>|  
|<span data-ttu-id="11221-116">기본값</span><span class="sxs-lookup"><span data-stu-id="11221-116">Defaults</span></span>|  
|<span data-ttu-id="11221-117">사용자 정의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="11221-117">User-Defined Data Types</span></span>|  
|<span data-ttu-id="11221-118">파티션 함수</span><span class="sxs-lookup"><span data-stu-id="11221-118">Partition Functions</span></span>|  
|<span data-ttu-id="11221-119">파티션 구성표</span><span class="sxs-lookup"><span data-stu-id="11221-119">Partition Schemes</span></span>|  
|<span data-ttu-id="11221-120">스키마</span><span class="sxs-lookup"><span data-stu-id="11221-120">Schemas</span></span>|  
|<span data-ttu-id="11221-121">어셈블리</span><span class="sxs-lookup"><span data-stu-id="11221-121">Assemblies</span></span>|  
|<span data-ttu-id="11221-122">사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="11221-122">User-Defined Aggregates</span></span>|  
|<span data-ttu-id="11221-123">사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="11221-123">User-Defined Types</span></span>|  
|<span data-ttu-id="11221-124">XML 스키마 컬렉션</span><span class="sxs-lookup"><span data-stu-id="11221-124">XML Schema Collection</span></span>|  
  
 <span data-ttu-id="11221-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 생성된 UDT(사용자 정의 형식)은 CLR(공용 언어 런타임) 어셈블리에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-125">User-defined types (UDTs) that were created in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] have dependencies on common language runtime (CLR) assemblies.</span></span> <span data-ttu-id="11221-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 기능을 사용하여 UDT를 전송할 경우 종속 개체를 전송하도록 태스크를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-126">If you use the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to transfer UDTs, you must also configure the task to transfer dependent objects.</span></span> <span data-ttu-id="11221-127">종속 개체를 전송하려면 `IncludeDependentObjects` 속성을 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-127">To transfer dependent objects, set the `IncludeDependentObjects` property to `True`.</span></span>  
  
### <a name="table-options"></a><span data-ttu-id="11221-128">테이블 옵션</span><span class="sxs-lookup"><span data-stu-id="11221-128">Table Options</span></span>  
 <span data-ttu-id="11221-129">테이블을 복사하는 경우 복사 작업에 포함시킬 테이블 관련 항목의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-129">When copying tables, you can indicate the types of table-related items to include in the copy process.</span></span> <span data-ttu-id="11221-130">다음 유형의 항목을 관련 테이블과 함께 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-130">The following types of items can be copied together with the related table:</span></span>  
  
-   <span data-ttu-id="11221-131">인덱스</span><span class="sxs-lookup"><span data-stu-id="11221-131">Indexes</span></span>  
  
-   <span data-ttu-id="11221-132">트리거</span><span class="sxs-lookup"><span data-stu-id="11221-132">Triggers</span></span>  
  
-   <span data-ttu-id="11221-133">전체 텍스트 인덱스</span><span class="sxs-lookup"><span data-stu-id="11221-133">Full-text indexes</span></span>  
  
-   <span data-ttu-id="11221-134">기본 키</span><span class="sxs-lookup"><span data-stu-id="11221-134">Primary keys</span></span>  
  
-   <span data-ttu-id="11221-135">외래 키</span><span class="sxs-lookup"><span data-stu-id="11221-135">Foreign keys</span></span>  
  
 <span data-ttu-id="11221-136">태스크가 생성하는 스크립트가 유니코드 형식인지도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-136">You can also indicate whether the script that the task generates is in Unicode format.</span></span>  
  
## <a name="destination-options"></a><span data-ttu-id="11221-137">대상 옵션</span><span class="sxs-lookup"><span data-stu-id="11221-137">Destination Options</span></span>  
 <span data-ttu-id="11221-138">전송할 때 스키마 이름, 데이터, 전송되는 개체의 확장 속성 및 종속 개체를 포함하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-138">You can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="11221-139">데이터를 복사할 때는 기존 데이터를 교체 또는 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-139">If data is copied, it can replace or append existing data.</span></span>  
  
 <span data-ttu-id="11221-140">일부 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-140">Some options apply only to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="11221-141">예를 들어 스키마는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-141">For example, only [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports schemas.</span></span>  
  
## <a name="security-options"></a><span data-ttu-id="11221-142">보안 옵션</span><span class="sxs-lookup"><span data-stu-id="11221-142">Security Options</span></span>  
 <span data-ttu-id="11221-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크에는 원본의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스 수준 사용자 및 역할, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인, 전송되는 개체에 대한 사용 권한을 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-143">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database-level users and roles from the source, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] logins, and the permissions for transferred objects.</span></span> <span data-ttu-id="11221-144">예를 들어 전송되는 테이블에 대한 사용 권한을 전송에 포함시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-144">For example, the transfer can include the permissions on the transferred tables.</span></span>  
  
## <a name="transfer-objects-between-instances-of-sql-server"></a><span data-ttu-id="11221-145">SQL Server 인스턴스 간 개체 전송</span><span class="sxs-lookup"><span data-stu-id="11221-145">Transfer Objects Between Instances of SQL Server</span></span>  
 <span data-ttu-id="11221-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 및 대상을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-146">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task supports a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source and destination.</span></span>  
  
## <a name="events"></a><span data-ttu-id="11221-147">이벤트</span><span class="sxs-lookup"><span data-stu-id="11221-147">Events</span></span>  
 <span data-ttu-id="11221-148">태스크는 전송되는 개체에 대해 보고하는 정보 이벤트를 발생시키며 개체를 덮어쓰는 경우 경고 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="11221-148">The task raises an information event that reports the object transferred and a warning event when an object is overwritten.</span></span> <span data-ttu-id="11221-149">데이터베이스 테이블 잘림과 같은 동작에서도 정보 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-149">An information event is also raised for actions such as the truncation of database tables.</span></span>  
  
 <span data-ttu-id="11221-150">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크는 개체를 전송하는 진행 과정은 보고하지 않으며 0% 및 100% 완료만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-150">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task does not report incremental progress of the object transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="11221-151">실행 값</span><span class="sxs-lookup"><span data-stu-id="11221-151">Execution Value</span></span>  
 <span data-ttu-id="11221-152">태스크의 `ExecutionValue` 속성에 저장된 실행 값은 전송된 개체 수를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-152">The execution value, stored in the `ExecutionValue` property of the task, returns the number of objects transferred.</span></span> <span data-ttu-id="11221-153">SQL Server 개체 전송 태스크의 `ExecValueVariable` 속성에 사용자 정의 변수를 할당하면 패키지의 다른 개체에서 개체 전송에 대한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-153">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer SQL Server Objects task, information about the object transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="11221-154">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="11221-154">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="11221-155">로그 항목</span><span class="sxs-lookup"><span data-stu-id="11221-155">Log Entries</span></span>  
 <span data-ttu-id="11221-156">SQL Server 개체 전송 태스크에는 다음 사용자 지정 로그 항목이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-156">The Transfer SQL Server Objects task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="11221-157">TransferSqlServerObjectsTaskStartTransferringObjects   이 로그 항목에서는 전송이 시작되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-157">TransferSqlServerObjectsTaskStartTransferringObjects   This log entry reports that the transfer has started.</span></span> <span data-ttu-id="11221-158">로그 항목에 시작 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-158">The log entry includes the start time.</span></span>  
  
-   <span data-ttu-id="11221-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    이 로그 항목에서는 전송이 완료되었음을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-159">TransferSqlServerObjectsTaskFinishedTransferringObjects    This log entry reports that the transfer has completed.</span></span> <span data-ttu-id="11221-160">로그 항목에 종료 시간이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-160">The log entry includes the end time.</span></span>  
  
 <span data-ttu-id="11221-161">또한 `OnInformation` 이벤트에 대한 로그 항목에서는 전송하도록 선택한 개체 유형의 개체 수, 전송된 개체의 수 및 테이블로 데이터 전송 시 테이블 잘림과 같은 동작을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-161">In addition, a log entry for an `OnInformation` event reports the number of objects of the object types that have been selected for transfer, the number of objects that were transferred, and actions such as the truncation of tables when data is transferred with tables.</span></span> <span data-ttu-id="11221-162">대상에서 덮어쓴 개체마다 `OnWarning` 이벤트에 대한 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-162">A log entry for the `OnWarning` event is written for each object on the destination that is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="11221-163">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="11221-163">Security and Permissions</span></span>  
 <span data-ttu-id="11221-164">사용자는 원본 서버에서 개체를 검색하는 권한 및 대상 서버에서 개체를 삭제하고 만드는 권한이 필요하며 무엇보다도 지정된 데이터베이스 및 데이터베이스 개체에 대한 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-164">The user must have permission to browse objects on the source server, and must have permission to drop and create objects on the destination server; moreover, the user must have access to the specified database and database objects.</span></span>  
  
## <a name="configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="11221-165">SQL Server 개체 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="11221-165">Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="11221-166">모든 개체, 한 유형의 모든 개체 또는 한 유형의 지정된 개체만 전송하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-166">The Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task can be configured to transfer all objects, all objects of a type, or only specified objects of a type.</span></span> <span data-ttu-id="11221-167">예를 들어 AdventureWorks 데이터베이스에서 선택한 테이블만 복사하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-167">For example, you can choose to copy only selected tables in the AdventureWorks database.</span></span>  
  
 <span data-ttu-id="11221-168">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크가 테이블을 전송하는 경우 테이블과 함께 복사할 테이블 관련 개체 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-168">If the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task transfers tables, you can specify the types of table-related objects to copy with the tables.</span></span> <span data-ttu-id="11221-169">예를 들어 테이블과 함께 복사할 기본 키를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-169">For example, you can specify that primary keys are copied with tables.</span></span>  
  
 <span data-ttu-id="11221-170">전송할 때 스키마 이름, 데이터, 전송된 개체의 확장 속성 및 종속 개체를 포함하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크를 구성하여 전송되는 개체의 기능을 더욱 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-170">To further enhance functionality of transferred objects, you can configure the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task to include schema names, data, extended properties of transferred objects, and dependent objects in the transfer.</span></span> <span data-ttu-id="11221-171">데이터 복사할 때 기존 데이터를 교체할지 또는 추가할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-171">When copying data, you can specify whether to replace or append existing data.</span></span>  
  
 <span data-ttu-id="11221-172">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크는 런타임에 두 개의 SMO 연결 관리자를 사용하여 원본 서버 및 대상 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-172">At run time, the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task connects to the source and destination servers by using two SMO connection managers.</span></span> <span data-ttu-id="11221-173">SMO 연결 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크와 별도로 구성된 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="11221-173">The SMO connection managers are configured separately from the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task, and then referenced in the Transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objects task.</span></span> <span data-ttu-id="11221-174">SMO 연결 관리자는 액세스할 서버 및 사용할 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11221-174">The SMO connection managers specify the server and the authentication mode to use when accessing the server.</span></span> <span data-ttu-id="11221-175">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="11221-175">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="11221-176">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11221-176">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="11221-177">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="11221-177">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="11221-178">SQL Server 개체 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="11221-178">Transfer SQL Server Objects Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="11221-179">SQL Server 개체 전송 태스크 편집기&#40;개체 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="11221-179">Transfer SQL Server Objects Task Editor &#40;Objects Page&#41;</span></span>](../transfer-sql-server-objects-task-editor-objects-page.md)  
  
-   [<span data-ttu-id="11221-180">식 페이지</span><span class="sxs-lookup"><span data-stu-id="11221-180">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="11221-181">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="11221-181">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="11221-182">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="11221-182">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-sql-server-objects-task"></a><span data-ttu-id="11221-183">SQL Server 개체 전송 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="11221-183">Programmatic Configuration of the Transfer SQL Server Objects Task</span></span>  
 <span data-ttu-id="11221-184">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="11221-184">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferSqlServerObjectsTask.TransferSqlServerObjectsTask>  
  
  
