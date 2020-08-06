---
title: 데이터베이스 전송 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.f1
helpviewer_keywords:
- Transfer Database task [Integration Services]
ms.assetid: b9a2e460-cdbc-458f-8df8-06b8b2de3d67
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85123eaff3e274bb4a96908ea99aef02c328ba23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638930"
---
# <a name="transfer-database-task"></a><span data-ttu-id="eed1c-102">데이터베이스 전송 태스크</span><span class="sxs-lookup"><span data-stu-id="eed1c-102">Transfer Database Task</span></span>
  <span data-ttu-id="eed1c-103">데이터베이스 전송 태스크는 두 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 간에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]데이터베이스를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-103">The Transfer Database task transfers a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="eed1c-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 개체를 복사하여 전송하는 다른 태스크와 달리 데이터베이스 전송 태스크는 데이터베이스를 복사 또는 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-104">In contrast to the other tasks that only transfer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objects by copying them, the Transfer Database task can either copy or move a database.</span></span> <span data-ttu-id="eed1c-105">동일한 서버 내에서 데이터베이스를 복사하는 데도 전송 태스크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-105">This task can also be used to copy a database within the same server.</span></span>  
  
## <a name="offline-and-online-modes"></a><span data-ttu-id="eed1c-106">오프라인 및 온라인 모드</span><span class="sxs-lookup"><span data-stu-id="eed1c-106">Offline and Online Modes</span></span>  
 <span data-ttu-id="eed1c-107">온라인 또는 오프라인 모드에서 데이터베이스를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-107">The database can be transferred by using online or offline mode.</span></span> <span data-ttu-id="eed1c-108">온라인 모드를 사용하는 경우 데이터베이스는 연결된 상태를 유지하며 데이터베이스 개체를 복사하는 SMO(SQL Management Object)를 통해 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-108">When you use online mode, the database remains attached and it is transferred by using SQL Management Object (SMO) to copy the database objects.</span></span> <span data-ttu-id="eed1c-109">오프라인 모드를 사용하는 경우 데이터베이스가 분리된 상태로 데이터베이스 파일을 복사 또는 이동하며 성공적으로 전송을 완료한 다음 대상에 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-109">When you use offline mode, the database is detached, the database files are copied or moved, and the database is attached at the destination after the transfer finishes successfully.</span></span> <span data-ttu-id="eed1c-110">데이터베이스를 복사하면 복사가 완료될 때 자동으로 원본에 다시 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-110">If the database is copied, it is automatically reattached at the source if the copy is successful.</span></span> <span data-ttu-id="eed1c-111">오프라인 모드에서는 좀 더 빠르게 데이터베이스를 복사할 수 있지만 전송하는 동안 데이터베이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-111">In offline mode, the database is copied more quickly, but the database is unavailable to users during the transfer.</span></span>  
  
 <span data-ttu-id="eed1c-112">오프라인 모드를 사용하려면 데이터베이스 파일을 가진 대상 서버 및 원본 서버에 네트워크 파일 공유를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-112">Offline mode requires that you specify the network file shares on the source and destination servers that contain the database files.</span></span> <span data-ttu-id="eed1c-113">폴더를 공유하여 사용자가 액세스할 수 있는 경우 \\\computername\Program Files\myfolder\\구문을 사용하여 네트워크 공유를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-113">If the folder is shared and can be accessed by the user, you can reference the network share using the syntax \\\computername\Program Files\myfolder\\.</span></span> <span data-ttu-id="eed1c-114">그렇지 않으면 \\\computername\c$\Program Files\myfolder\\구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-114">Otherwise, you must use the syntax \\\computername\c$\Program Files\myfolder\\.</span></span> <span data-ttu-id="eed1c-115">두 번째 구문을 사용하려면 원본 및 대상 네트워크 공유에 대한 쓰기 액세스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-115">To use the latter syntax, the user must have write access to the source and destination network shares.</span></span>  
  
## <a name="transfer-of-databases-between-versions-of-sql-server"></a><span data-ttu-id="eed1c-116">SQL Server 버전 간 데이터베이스 전송</span><span class="sxs-lookup"><span data-stu-id="eed1c-116">Transfer of Databases Between Versions of SQL Server</span></span>  
 <span data-ttu-id="eed1c-117">데이터베이스 전송 태스크는 여러 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전의 인스턴스 간에 데이터베이스를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-117">The Transfer Database task can transfer a database between instances of different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span>  
  
## <a name="events"></a><span data-ttu-id="eed1c-118">이벤트</span><span class="sxs-lookup"><span data-stu-id="eed1c-118">Events</span></span>  
 <span data-ttu-id="eed1c-119">데이터베이스 전송 태스크는 오류 메시지 전송의 진행 상황은 보고하지 않으며 0% 및 100% 완료만 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-119">The Transfer Database task does not report incremental progress of the error message transfer; it reports only 0% and 100 % completion.</span></span>  
  
## <a name="execution-value"></a><span data-ttu-id="eed1c-120">실행 값</span><span class="sxs-lookup"><span data-stu-id="eed1c-120">Execution Value</span></span>  
 <span data-ttu-id="eed1c-121">다른 전송 태스크와 달리 데이터베이스 전송 태스크는 한 개의 데이터베이스만 전송할 수 있으므로 태스크의 `ExecutionValue` 속성에 정의된 실행 값은 1을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-121">The execution value, defined in the `ExecutionValue` property of the task, returns the value 1, because in contrast to other transfer tasks, the Transfer Database task can transfer only one database.</span></span>  
  
 <span data-ttu-id="eed1c-122">데이터베이스 전송 태스크의 `ExecValueVariable` 속성에 사용자 정의 변수를 할당하면 패키지 내의 다른 개체에서 오류 메시지 전송에 대한 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-122">By assigning a user-defined variable to the `ExecValueVariable` property of the Transfer Database task, information about the error message transfer can be made available to other objects in the package.</span></span> <span data-ttu-id="eed1c-123">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eed1c-123">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Use Variables in Packages](../use-variables-in-packages.md).</span></span>  
  
## <a name="log-entries"></a><span data-ttu-id="eed1c-124">로그 항목</span><span class="sxs-lookup"><span data-stu-id="eed1c-124">Log Entries</span></span>  
 <span data-ttu-id="eed1c-125">데이터베이스 전송 태스크는 다음 사용자 지정 로그 항목을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-125">The Transfer Database task includes the following custom log entries:</span></span>  
  
-   <span data-ttu-id="eed1c-126">SourceSQLServer    이 로그 항목은 원본 서버의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-126">SourceSQLServer    This log entry lists the name of the source server.</span></span>  
  
-   <span data-ttu-id="eed1c-127">DestSQLServer    이 로그 항목은 대상 서버의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-127">DestSQLServer    This log entry lists the name of the destination server.</span></span>  
  
-   <span data-ttu-id="eed1c-128">SourceDB    이 로그 항목은 전송된 데이터베이스의 이름을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-128">SourceDB    This log entry lists the name of the database that is transferred.</span></span>  
  
 <span data-ttu-id="eed1c-129">또한 대상 데이터베이스를 덮어쓰는 경우 `OnInformation` 이벤트에 대한 로그 항목이 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-129">In addition, a log entry for the `OnInformation` event is written when the destination database is overwritten.</span></span>  
  
## <a name="security-and-permissions"></a><span data-ttu-id="eed1c-130">보안 및 사용 권한</span><span class="sxs-lookup"><span data-stu-id="eed1c-130">Security and Permissions</span></span>  
 <span data-ttu-id="eed1c-131">오프라인 모드를 사용해 데이터베이스를 전송하려면 패키지를 실행하는 사용자가 sysadmin 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-131">To transfer a database using offline mode, the user who runs the package must be a member of the sysadmin server role.</span></span>  
  
 <span data-ttu-id="eed1c-132">온라인 모드를 사용해 데이터베이스를 전송하려면 패키지를 실행하는 사용자가 sysadmin 서버 역할의 멤버이거나 선택한 데이터베이스의 데이터베이스 소유자(dbo)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-132">To transfer a database using online mode, the user who runs the package must be a member of the sysadmin server role or the database owner (dbo) of the selected database.</span></span>  
  
## <a name="configuration-of-the-transfer-database-task"></a><span data-ttu-id="eed1c-133">데이터베이스 전송 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="eed1c-133">Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="eed1c-134">데이터베이스 전송이 실패하는 경우 태스크가 원본 데이터베이스에 다시 연결할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-134">You can specify whether the task tries to reattach the source database if the database transfer fails.</span></span>  
  
 <span data-ttu-id="eed1c-135">동일한 이름의 대상 데이터베이스를 덮어쓰고 대상 데이터베이스를 대체할 수 있도록 데이터베이스 전송 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-135">The Transfer Database task can also be configured to permit overwriting a destination database that has the same name, replacing the destination database.</span></span>  
  
 <span data-ttu-id="eed1c-136">전송 과정의 일부로 원본 데이터베이스의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-136">The source database can also be renamed as part of the transfer process.</span></span> <span data-ttu-id="eed1c-137">대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 이미 같은 이름의 데이터베이스가 있는 경우 원본 데이터베이스의 이름을 변경하여 데이터베이스를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-137">If you want to transfer a database to a destination instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that already contains a database that has the same name, renaming the source database allows the database to be transferred.</span></span> <span data-ttu-id="eed1c-138">그러나 같은 이름의 데이터베이스 파일이 대상에 있는 경우에는 태스크가 실패하므로 데이터베이스 파일의 이름은 반드시 달라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-138">However, the database file names must also be different; if database files that have the same names already exist at the destination, the task fails.</span></span>  
  
 <span data-ttu-id="eed1c-139">데이터베이스를 복사할 경우 데이터베이스는 대상 서버에 있는 **model** 데이터베이스의 크기보다 작을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-139">When you copy a database, the database cannot be smaller than the size of the **model** database on the destination server.</span></span> <span data-ttu-id="eed1c-140">복사할 데이터베이스의 크기를 늘리거나 **model**의 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-140">You can either increase the size of the database to copy, or reduce the size of **model**.</span></span>  
  
 <span data-ttu-id="eed1c-141">데이터베이스 전송 태스크는 런타임에 한 개 또는 두 개의 SMO 연결 관리자를 사용해 원본 서버 및 대상 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-141">At run time, the Transfer Database task connects to the source and destination servers by using one or two SMO connection managers.</span></span> <span data-ttu-id="eed1c-142">동일한 서버에 데이터베이스 복사본을 만드는 경우 하나의 SMO 연결 관리자만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-142">When you create a copy of a database on the same server, only one SMO connection manager is required.</span></span> <span data-ttu-id="eed1c-143">SMO 연결 관리자는 데이터베이스 전송 태스크와 별도로 구성된 후 데이터베이스 전송 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-143">The SMO connection managers are configured separately from the Transfer Database task, and then are referenced in the Transfer Database task.</span></span> <span data-ttu-id="eed1c-144">SMO 연결 관리자는 태스크가 서버에 액세스할 때 사용할 서버 및 인증 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-144">The SMO connection managers specify the server and the authentication mode to use when the task accesses the server.</span></span> <span data-ttu-id="eed1c-145">자세한 내용은 [SMO Connection Manager](../connection-manager/smo-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eed1c-145">For more information, see [SMO Connection Manager](../connection-manager/smo-connection-manager.md).</span></span>  
  
 <span data-ttu-id="eed1c-146">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed1c-146">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="eed1c-147">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="eed1c-147">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="eed1c-148">데이터베이스 전송 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eed1c-148">Transfer Database Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="eed1c-149">데이터베이스 전송 태스크 편집기&#40;데이터베이스 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eed1c-149">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../transfer-database-task-editor-databases-page.md)  
  
-   [<span data-ttu-id="eed1c-150">식 페이지</span><span class="sxs-lookup"><span data-stu-id="eed1c-150">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="eed1c-151">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="eed1c-151">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="eed1c-152">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="eed1c-152">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-transfer-database-task"></a><span data-ttu-id="eed1c-153">데이터베이스 전송 태스크의 프로그래밍 방식 구성</span><span class="sxs-lookup"><span data-stu-id="eed1c-153">Programmatic Configuration of the Transfer Database Task</span></span>  
 <span data-ttu-id="eed1c-154">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="eed1c-154">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferDatabaseTask.TransferDatabaseTask>  
  
  
