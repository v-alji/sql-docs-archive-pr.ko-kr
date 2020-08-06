---
title: 데이터베이스 전송 태스크 편집기 (데이터베이스 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.database.f1
helpviewer_keywords:
- Transfer Database Task Editor
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df4452e28a32463a7825e9c64cfd053f98c53ee8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727283"
---
# <a name="transfer-database-task-editor-databases-page"></a><span data-ttu-id="64a98-102">데이터베이스 전송 태스크 편집기(데이터베이스 페이지)</span><span class="sxs-lookup"><span data-stu-id="64a98-102">Transfer Database Task Editor (Databases Page)</span></span>
  <span data-ttu-id="64a98-103">**데이터베이스 전송 태스크 편집기** 대화 상자의 **데이터베이스** 페이지를 사용하여 데이터베이스 전송 태스크와 관련된 원본 및 대상 데이터베이스의 속성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-103">Use the **Databases** page of the **Transfer Database Task Editor** dialog box to specify properties for the source and destination databases involved in the Transfer Database task.</span></span> <span data-ttu-id="64a98-104">데이터베이스 전송 태스크에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]의 두 인스턴스 간에 복사 또는 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-104">The Transfer Database task copies or moves a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database between two instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="64a98-105">동일한 서버 내에서 데이터베이스를 복사하는 데도 전송 태스크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-105">This task can also be used to copy a database within the same server.</span></span> <span data-ttu-id="64a98-106">이 태스크에 대한 자세한 내용은 [데이터베이스 전송 태스크](control-flow/transfer-database-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64a98-106">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="64a98-107">옵션</span><span class="sxs-lookup"><span data-stu-id="64a98-107">Options</span></span>  
 <span data-ttu-id="64a98-108">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="64a98-108">**SourceConnection**</span></span>  
 <span data-ttu-id="64a98-109">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 원본 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="64a98-110">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="64a98-110">**DestinationConnection**</span></span>  
 <span data-ttu-id="64a98-111">목록에서 SMO 연결 관리자를 선택하거나, **\<New connection...>** 을 클릭하여 대상 서버에 대한 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-111">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="64a98-112">**DestinationDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="64a98-112">**DestinationDatabaseName**</span></span>  
 <span data-ttu-id="64a98-113">대상 서버에 있는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-113">Specify the name of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database on the destination server.</span></span>  
  
 <span data-ttu-id="64a98-114">이 필드를 원본 데이터베이스 이름으로 자동으로 채우려면 먼저 **SourceConnection** 및 **SourceDatabaseName** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-114">To automatically populate this field with the source database name, specify the **SourceConnection** and **SourceDatabaseName** first.</span></span>  
  
 <span data-ttu-id="64a98-115">대상 서버에 있는 데이터베이스의 이름을 바꾸려면 이 필드에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-115">To rename the database on the destination server, type the new name in this field.</span></span>  
  
 <span data-ttu-id="64a98-116">**DestinationDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="64a98-116">**DestinationDatabaseFiles**</span></span>  
 <span data-ttu-id="64a98-117">대상 서버에 있는 데이터베이스 파일의 이름 및 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-117">Specifies the names and locations of the database files on the destination server.</span></span>  
  
 <span data-ttu-id="64a98-118">이 필드를 원본 데이터베이스 파일 이름 및 위치로 자동으로 채우려면 먼저 **SourceConnection**, **SourceDatabaseName**및 **SourceDatabaseFiles** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-118">To automatically populate this field with the source database file names and locations, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first.</span></span>  
  
 <span data-ttu-id="64a98-119">데이터베이스 파일의 이름을 바꾸거나 대상 서버에 새 위치를 지정하려면 이 필드를 원본 데이터베이스 정보로 채운 다음 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-119">To rename the database files or to specify the new locations on the destination server, populate this field with the source database information, and then click the browse button.</span></span> <span data-ttu-id="64a98-120">**대상 데이터베이스 파일** 대화 상자에서 **대상 파일**, **대상 폴더**또는 **네트워크 파일 공유**를 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-120">In the **Destination database files** dialog box, edit the **Destination File**, **Destination Folder**, or **Network File Share**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="64a98-121">찾아보기 단추를 사용하여 데이터베이스 파일을 찾으면 해당 파일 위치가 로컬 드라이브 표기법을 사용하여 입력됩니다(예: c:\\).</span><span class="sxs-lookup"><span data-stu-id="64a98-121">If you locate the database files by using the browse button, the file location is entered using the local drive notation: for example, c:\\.</span></span> <span data-ttu-id="64a98-122">이는 컴퓨터 이름 및 공유 이름과 함께 네트워크 공유 표기법으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-122">You must replace this with the network share notation, including the computer name and share name.</span></span> <span data-ttu-id="64a98-123">기본 관리 공유를 사용하는 경우 $ 표기법을 사용하고 공유에 대한 관리 액세스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-123">If the default administrative share is used, you must use the $ notation, and have administrative access to the share.</span></span>  
  
 <span data-ttu-id="64a98-124">**DestinationOverwrite**</span><span class="sxs-lookup"><span data-stu-id="64a98-124">**DestinationOverwrite**</span></span>  
 <span data-ttu-id="64a98-125">대상 서버에 있는 데이터베이스를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-125">Specify whether the database on the destination server can be overwritten.</span></span>  
  
 <span data-ttu-id="64a98-126">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-126">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="64a98-127">값</span><span class="sxs-lookup"><span data-stu-id="64a98-127">Value</span></span>|<span data-ttu-id="64a98-128">Description</span><span class="sxs-lookup"><span data-stu-id="64a98-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64a98-129">**True**</span><span class="sxs-lookup"><span data-stu-id="64a98-129">**True**</span></span>|<span data-ttu-id="64a98-130">대상 서버 데이터베이스를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-130">Overwrite destination server database.</span></span>|  
|<span data-ttu-id="64a98-131">**False**</span><span class="sxs-lookup"><span data-stu-id="64a98-131">**False**</span></span>|<span data-ttu-id="64a98-132">대상 서버 데이터베이스를 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-132">Do not overwrite destination server database.</span></span>|  
  
> [!CAUTION]  
>  <span data-ttu-id="64a98-133">**DestinationOverwrite** 에 대해 **True**를 지정하면 대상 서버 데이터베이스의 데이터를 덮어쓰며 이로 인해 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-133">The data in the destination server database will be overwritten if you specify **True** for **DestinationOverwrite**, which may result in data loss.</span></span> <span data-ttu-id="64a98-134">이를 방지하려면 데이터베이스 전송 태스크를 실행하기 전에 대상 서버 데이터베이스를 다른 위치에 백업합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-134">To avoid this, back up the destination server database to another location before executing the Transfer Database task.</span></span>  
  
 <span data-ttu-id="64a98-135">**동작**</span><span class="sxs-lookup"><span data-stu-id="64a98-135">**Action**</span></span>  
 <span data-ttu-id="64a98-136">데이터베이스를 대상 서버로 복사하려면 **Copy** , 이동하려면 **Move** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-136">Specify whether the task will **Copy** or **Move** the database to the destination server.</span></span>  
  
 <span data-ttu-id="64a98-137">**메서드**</span><span class="sxs-lookup"><span data-stu-id="64a98-137">**Method**</span></span>  
 <span data-ttu-id="64a98-138">원본 서버의 데이터베이스가 온라인 모드에 있을 때 태스크를 실행할지, 아니면 오프라인 모드에 있을 때 실행할지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-138">Specify whether the task will be executed while the database on the source server is in online or offline mode.</span></span>  
  
 <span data-ttu-id="64a98-139">오프라인 모드를 사용하여 데이터베이스를 전송하려면 패키지를 실행하는 사용자가 **sysadmin** 고정 서버 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-139">To transfer a database using offline mode, the user that runs the package must be a member of the **sysadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="64a98-140">온라인 모드를 사용하여 데이터베이스를 전송하려면 패키지를 실행하는 사용자가 **sysadmin** 고정 서버 역할의 멤버이거나 선택한 데이터베이스의 데이터베이스 소유자(**dbo**)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-140">To transfer a database using the online mode, the user that runs the package must be a member of the **sysadmin** fixed server role, or the database owner (**dbo**) of the selected database.</span></span>  
  
 <span data-ttu-id="64a98-141">**SourceDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="64a98-141">**SourceDatabaseName**</span></span>  
 <span data-ttu-id="64a98-142">복사 또는 이동할 데이터베이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-142">Select the name of the database to be copied or moved.</span></span>  
  
 <span data-ttu-id="64a98-143">**SourceDatabaseFiles**</span><span class="sxs-lookup"><span data-stu-id="64a98-143">**SourceDatabaseFiles**</span></span>  
 <span data-ttu-id="64a98-144">데이터베이스 파일을 선택하려면 찾아보기 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-144">Click the browse button to select the database files.</span></span>  
  
 <span data-ttu-id="64a98-145">**ReattachSourceDatabase**</span><span class="sxs-lookup"><span data-stu-id="64a98-145">**ReattachSourceDatabase**</span></span>  
 <span data-ttu-id="64a98-146">오류 발생 시 원본 데이터베이스를 다시 연결할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-146">Specify whether the task will attempt to reattach the source database if a failure occurs.</span></span>  
  
 <span data-ttu-id="64a98-147">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-147">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="64a98-148">값</span><span class="sxs-lookup"><span data-stu-id="64a98-148">Value</span></span>|<span data-ttu-id="64a98-149">Description</span><span class="sxs-lookup"><span data-stu-id="64a98-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="64a98-150">**True**</span><span class="sxs-lookup"><span data-stu-id="64a98-150">**True**</span></span>|<span data-ttu-id="64a98-151">원본 데이터베이스를 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-151">Reattach source database.</span></span>|  
|<span data-ttu-id="64a98-152">**False**</span><span class="sxs-lookup"><span data-stu-id="64a98-152">**False**</span></span>|<span data-ttu-id="64a98-153">원본 데이터베이스를 다시 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64a98-153">Do not reattach source database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64a98-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="64a98-154">See Also</span></span>  
 <span data-ttu-id="64a98-155">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="64a98-155">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="64a98-156">[Integration Services 태스크](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="64a98-156">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="64a98-157">[데이터베이스 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="64a98-157">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="64a98-158">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="64a98-158">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="64a98-159">SMO 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="64a98-159">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
