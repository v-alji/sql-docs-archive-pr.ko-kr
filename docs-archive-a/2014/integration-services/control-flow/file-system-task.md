---
title: 파일 시스템 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.f1
helpviewer_keywords:
- File System task [Integration Services]
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3ce3d31ceb720704fb61c33043a4c7319607caff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638957"
---
# <a name="file-system-task"></a><span data-ttu-id="045cf-102">파일 시스템 태스크</span><span class="sxs-lookup"><span data-stu-id="045cf-102">File System Task</span></span>
  <span data-ttu-id="045cf-103">파일 시스템 태스크는 파일 시스템의 파일 및 디렉터리에 대해 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-103">The File System task performs operations on files and directories in the file system.</span></span> <span data-ttu-id="045cf-104">예를 들어 파일 시스템 태스크를 사용하면 패키지가 디렉터리와 파일을 만들거나 이동 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-104">For example, by using the File System task, a package can create, move, or delete directories and files.</span></span> <span data-ttu-id="045cf-105">파일 시스템 태스크를 사용하여 파일과 디렉터리의 특성을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-105">You can also use the File System task to set attributes on files and directories.</span></span> <span data-ttu-id="045cf-106">예를 들어 파일 시스템 태스크는 파일에 숨김 또는 읽기 전용 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-106">For example, the File System task can make files hidden or read-only.</span></span>  
  
 <span data-ttu-id="045cf-107">모든 파일 시스템 태스크는 파일이나 디렉터리일 수 있는 원본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-107">All File System task operations use a source, which can be a file or a directory.</span></span> <span data-ttu-id="045cf-108">예를 들어 태스크에서 복사한 파일이나 삭제한 디렉터리가 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-108">For example, the file that the task copies or the directory it deletes is a source.</span></span> <span data-ttu-id="045cf-109">파일 연결 관리자를 사용하여 디렉터리 또는 파일을 가리키거나 원본 경로가 포함된 변수 이름을 제공하여 원본을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-109">The source can be specified by using a File connection manager that points to the directory or file or by providing the name of a variable that contains the source path.</span></span> <span data-ttu-id="045cf-110">자세한 내용은 [파일 연결 관리자](../connection-manager/file-connection-manager.md) 및 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045cf-110">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="045cf-111">파일과 디렉터리를 복사 및 이동하는 작업과 파일 이름을 바꾸는 작업은 대상과 원본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-111">The operations that copy and move file and directories and rename files use a destination and a source.</span></span> <span data-ttu-id="045cf-112">대상은 파일 연결 관리자나 변수를 사용하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-112">The destination is specified by using a File connection manager or a variable.</span></span> <span data-ttu-id="045cf-113">대상 파일과 디렉터리의 덮어쓰기를 허용하도록 파일 시스템 태스크를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-113">File system task operations can be configured to permit overwriting of destination files and directories.</span></span> <span data-ttu-id="045cf-114">지정된 이름을 가진 디렉터리가 이미 존재할 경우 실패하는 대신에 해당 디렉터리를 사용하도록 새 디렉터리를 만드는 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-114">The operation that creates a new directory can be configured to use an existing directory that has the specified name instead of failing when the directory already exists.</span></span>  
  
## <a name="predefined-file-system-operations"></a><span data-ttu-id="045cf-115">미리 정의된 파일 시스템 작업</span><span class="sxs-lookup"><span data-stu-id="045cf-115">Predefined File System Operations</span></span>  
 <span data-ttu-id="045cf-116">파일 시스템 태스크에는 미리 정의된 작업 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-116">The File System task includes a predefined set of operations.</span></span> <span data-ttu-id="045cf-117">다음 표에서는 이러한 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-117">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="045cf-118">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="045cf-118">Operation</span></span>|<span data-ttu-id="045cf-119">Description</span><span class="sxs-lookup"><span data-stu-id="045cf-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="045cf-120">디렉터리 복사</span><span class="sxs-lookup"><span data-stu-id="045cf-120">Copy directory</span></span>|<span data-ttu-id="045cf-121">폴더를 다른 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-121">Copies a folder from one location to another.</span></span>|  
|<span data-ttu-id="045cf-122">파일 복사</span><span class="sxs-lookup"><span data-stu-id="045cf-122">Copy file</span></span>|<span data-ttu-id="045cf-123">파일을 다른 위치에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-123">Copies a file from one location to another.</span></span>|  
|<span data-ttu-id="045cf-124">디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="045cf-124">Create directory</span></span>|<span data-ttu-id="045cf-125">지정한 위치에 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-125">Creates a folder in a specified location.</span></span>|  
|<span data-ttu-id="045cf-126">디렉터리 삭제</span><span class="sxs-lookup"><span data-stu-id="045cf-126">Delete directory</span></span>|<span data-ttu-id="045cf-127">지정한 위치의 폴더를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-127">Deletes a folder in a specified location.</span></span>|  
|<span data-ttu-id="045cf-128">디렉터리 내용 삭제</span><span class="sxs-lookup"><span data-stu-id="045cf-128">Delete directory content</span></span>|<span data-ttu-id="045cf-129">폴더에 있는 모든 파일과 폴더를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-129">Deletes all files and folders in a folder.</span></span>|  
|<span data-ttu-id="045cf-130">파일 삭제</span><span class="sxs-lookup"><span data-stu-id="045cf-130">Delete file</span></span>|<span data-ttu-id="045cf-131">지정한 위치의 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-131">Deletes a file in a specified location.</span></span>|  
|<span data-ttu-id="045cf-132">디렉터리 이동</span><span class="sxs-lookup"><span data-stu-id="045cf-132">Move directory</span></span>|<span data-ttu-id="045cf-133">폴더를 다른 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-133">Moves a folder from one location to another.</span></span>|  
|<span data-ttu-id="045cf-134">파일 이동</span><span class="sxs-lookup"><span data-stu-id="045cf-134">Move file</span></span>|<span data-ttu-id="045cf-135">파일을 다른 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-135">Moves a file from one location to another.</span></span>|  
|<span data-ttu-id="045cf-136">파일 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="045cf-136">Rename file</span></span>|<span data-ttu-id="045cf-137">지정한 위치의 파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-137">Renames a file in a specified location.</span></span>|  
|<span data-ttu-id="045cf-138">특성 설정</span><span class="sxs-lookup"><span data-stu-id="045cf-138">Set attributes</span></span>|<span data-ttu-id="045cf-139">파일과 폴더의 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-139">Sets attributes on files and folders.</span></span> <span data-ttu-id="045cf-140">특성에는 보관, 숨김, 보통, 읽기 전용, 시스템 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-140">Attributes include Archive, Hidden, Normal, ReadOnly, and System.</span></span> <span data-ttu-id="045cf-141">보통은 특성이 없는 것이며 다른 특성과 조합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-141">Normal is the lack of attributes, and it cannot be combined with other attributes.</span></span> <span data-ttu-id="045cf-142">다른 모든 특성은 조합하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-142">All other attributes can be used in combination.</span></span>|  
  
 <span data-ttu-id="045cf-143">파일 시스템 태스크는 단일 파일 또는 디렉터리에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-143">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="045cf-144">따라서 이 태스크는 와일드카드 문자를 사용하여 여러 파일에 대해 동일한 작업을 수행하는 것을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-144">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files.</span></span> <span data-ttu-id="045cf-145">파일 시스템 태스크가 여러 파일이나 디렉터리에 대한 작업을 반복하게 하려면 다음 단계에 따라 파일 시스템 태스크를 Foreach 루프 컨테이너에 넣으십시오.</span><span class="sxs-lookup"><span data-stu-id="045cf-145">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container, as described in the following steps:</span></span>  
  
-   <span data-ttu-id="045cf-146">**Foreach 루프 컨테이너 구성** Foreach 루프 편집기의 **컬렉션** 페이지에서 열거자를 **Foreach File 열거자** 로 설정하고 와일드카드 식을 **파일**에 대한 열거자 구성으로 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="045cf-146">**Configure the Foreach Loop container** On the **Collection** page of the Foreach Loop Editor, set the enumerator to **Foreach File Enumerator** and enter the wildcard expression as the enumerator configuration for **Files**.</span></span> <span data-ttu-id="045cf-147">Foreach 루프 편집기의 **변수 매핑** 페이지에서 파일 시스템 태스크에 파일 이름을 한 번에 한 개씩 전달하는 데 사용할 변수를 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-147">On the **Variable Mappings** page of the Foreach Loop Editor, map a variable that you want to use to pass the file names one at a time to the File System task.</span></span>  
  
-   <span data-ttu-id="045cf-148">**파일 시스템 태스크 추가 및 구성** 파일 시스템 태스크를 Foreach 루프 컨테이너에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-148">**Add and configure a File System task** Add a File System task to the Foreach Loop container.</span></span> <span data-ttu-id="045cf-149">파일 시스템 태스크 편집기의 **일반** 페이지에서 **SourceVariable** 또는 **DestinationVariable** 속성을 Foreach 루프 컨테이너에 정의된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-149">On the **General** page of the File System Task Editor, set the **SourceVariable** or **DestinationVariable** property to the variable that you defined in the Foreach Loop container.</span></span>  
  
## <a name="custom-log-entries-available-on-the-file-system-task"></a><span data-ttu-id="045cf-150">파일 시스템 태스크에 사용할 수 있는 사용자 지정 로그 항목</span><span class="sxs-lookup"><span data-stu-id="045cf-150">Custom Log Entries Available on the File System Task</span></span>  
 <span data-ttu-id="045cf-151">다음 표에서는 파일 시스템 태스크에 대한 사용자 지정 로그 항목을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-151">The following table describes the custom log entry for the File System task.</span></span> <span data-ttu-id="045cf-152">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045cf-152">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="045cf-153">로그 항목</span><span class="sxs-lookup"><span data-stu-id="045cf-153">Log entry</span></span>|<span data-ttu-id="045cf-154">Description</span><span class="sxs-lookup"><span data-stu-id="045cf-154">Description</span></span>|  
|---------------|-----------------|  
|`FileSystemOperation`|<span data-ttu-id="045cf-155">태스크에서 수행하는 작업을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-155">Reports the operation that the task performs.</span></span> <span data-ttu-id="045cf-156">이 로그 항목은 파일 시스템 작업이 시작될 때 기록되며 원본 및 대상에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-156">The log entry is written when the file system operation starts and includes information about the source and destination.</span></span>|  
  
## <a name="configuring-the-file-system-task"></a><span data-ttu-id="045cf-157">파일 시스템 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="045cf-157">Configuring the File System Task</span></span>  
 <span data-ttu-id="045cf-158">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-158">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="045cf-159">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="045cf-159">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   [<span data-ttu-id="045cf-160">파일 시스템 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="045cf-160">File System Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="045cf-161">식 페이지</span><span class="sxs-lookup"><span data-stu-id="045cf-161">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="045cf-162">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="045cf-162">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="045cf-163">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="045cf-163">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
 <span data-ttu-id="045cf-164">프로그래밍 방식으로 이러한 속성을 설정하는 방법은 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="045cf-164">For more information about how to set these properties programmatically, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask>  
  
## <a name="related-tasks"></a><span data-ttu-id="045cf-165">관련 작업</span><span class="sxs-lookup"><span data-stu-id="045cf-165">Related Tasks</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="045cf-166">에는 데이터 파일을 다운로드 및 업로드하고 서버의 디렉터리를 관리하는 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045cf-166">includes a task that downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="045cf-167">자세한 내용은 [FTP Task](ftp-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045cf-167">For more information, see [FTP Task](ftp-task.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045cf-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="045cf-168">See Also</span></span>  
 <span data-ttu-id="045cf-169">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="045cf-169">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="045cf-170">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="045cf-170">Control Flow</span></span>](control-flow.md)  
  
  
