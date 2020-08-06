---
title: FTP 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.f1
helpviewer_keywords:
- FTP task [Integration Services]
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 63ec58c1bff9894d0aa73112686c4b1fe9421b98
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638950"
---
# <a name="ftp-task"></a><span data-ttu-id="19705-102">FTP 태스크</span><span class="sxs-lookup"><span data-stu-id="19705-102">FTP Task</span></span>
  <span data-ttu-id="19705-103">FTP 태스크는 데이터 파일을 다운로드 및 업로드하고 서버의 디렉터리를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-103">The FTP task downloads and uploads data files and manages directories on servers.</span></span> <span data-ttu-id="19705-104">예를 들어 패키지는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 워크플로의 일부로 원격 서버 또는 인터넷 위치에서 데이터 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-104">For example, a package can download data files from a remote server or an Internet location as part of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package workflow.</span></span> <span data-ttu-id="19705-105">FTP 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-105">You can use the FTP task for the following purposes:</span></span>  
  
-   <span data-ttu-id="19705-106">데이터를 이동하고 변환을 데이터에 적용하기 전이나 후에 디렉터리 및 데이터 파일을 다른 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-106">Copying directories and data files from one directory to another, before or after moving data, and applying transformations to the data.</span></span>  
  
-   <span data-ttu-id="19705-107">원본 FTP 위치에 로그인하고 파일 또는 패키지를 대상 디렉터리로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-107">Logging in to a source FTP location and copying files or packages to a destination directory.</span></span>  
  
-   <span data-ttu-id="19705-108">데이터베이스에 데이터를 로드하기 전에 FTP 위치에서 파일을 다운로드하고 열 데이터에 변환을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-108">Downloading files from an FTP location and applying transformations to column data before loading the data into a database.</span></span>  
  
 <span data-ttu-id="19705-109">런타임 시 FTP 태스크는 FTP 연결 관리자를 사용하여 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-109">At run time, the FTP task connects to a server by using an FTP connection manager.</span></span> <span data-ttu-id="19705-110">FTP 연결 관리자는 FTP 태스크와 별도로 구성된 후 FTP 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="19705-110">The FTP connection manager is configured separately from the FTP task, and then is referenced in the FTP task.</span></span> <span data-ttu-id="19705-111">FTP 연결 관리자에는 서버 설정, FTP 서버 액세스를 위한 자격 증명, 제한 시간 및 서버 연결 다시 시도 횟수와 같은 옵션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-111">The FTP connection manager includes the server settings, the credentials for accessing the FTP server, and options such as the time-out and the number of retries for connecting to the server.</span></span> <span data-ttu-id="19705-112">자세한 내용은 [FTP 연결 관리자](../connection-manager/ftp-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19705-112">For more information, see [FTP Connection Manager](../connection-manager/ftp-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="19705-113">FTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="19705-113">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="19705-114">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-114">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="19705-115">로컬 파일이나 로컬 디렉터리에 액세스할 때 FTP 태스크는 파일 연결 관리자 또는 변수에 저장된 경로 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-115">When accessing a local file or a local directory, the FTP task uses a File connection manager or path information stored in a variable.</span></span> <span data-ttu-id="19705-116">반면 원격 파일이나 원격 디렉터리에 액세스할 때는 직접 지정된 원격 서버의 경로, FTP 연결 관리자에 지정된 경로 또는 변수에 저장된 경로 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-116">In contrast, when accessing a remote file or a remote directory, the FTP task uses a directly specified path on the remote server, as specified in the FTP connection manager, or path information stored in a variable.</span></span> <span data-ttu-id="19705-117">자세한 내용은 [파일 연결 관리자](../connection-manager/file-connection-manager.md) 및 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19705-117">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="19705-118">이는 FTP 태스크에서 여러 개의 파일을 받고 여러 개의 원격 파일을 삭제할 수 있다는 것을 의미합니다. 그러나 파일 연결 관리자는 하나의 파일만 액세스할 수 있기 때문에 연결 관리자를 사용할 경우 하나의 파일만 보내고 하나의 로컬 파일만 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-118">This means that the FTP task can receive multiple files and delete multiple remote files; but the task can send only one file and delete only one local file if it uses a connection manager, because a File connection manager can access only one file.</span></span> <span data-ttu-id="19705-119">여러 개의 로컬 파일에 액세스하려면 FTP 태스크에 변수를 사용하여 경로 정보를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-119">To access multiple local files, the FTP task must use a variable to provide the path information.</span></span> <span data-ttu-id="19705-120">예를 들어 "C:\Test\\*.txt"가 포함된 변수는 Test 디렉터리에서 .txt 확장명을 가진 모든 파일 삭제 또는 보내기를 지원하는 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-120">For example, a variable that contains "C:\Test\\*.txt" provides a path that supports deleting or sending all the files that have a .txt extension in the Test directory.</span></span>  
  
 <span data-ttu-id="19705-121">여러 개의 파일을 보내고 여러 개의 로컬 파일 및 디렉터리에 액세스하려면 Foreach 루프에 태스크를 포함하여 FTP 태스크를 여러 번 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-121">To send multiple files and access multiple local files and directories, you can also execute the FTP task multiple times by including the task in a Foreach Loop.</span></span> <span data-ttu-id="19705-122">Foreach 루프는 For Each File 열거자를 사용하여 디렉터리의 모든 파일을 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-122">The Foreach Loop can enumerate across files in a directory using the For Each File enumerator.</span></span> <span data-ttu-id="19705-123">자세한 내용은 [Foreach 루프 컨테이너](foreach-loop-container.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="19705-123">For more information, see [Foreach Loop Container](foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="19705-124">FTP 태스크는 경로에서 *?*</span><span class="sxs-lookup"><span data-stu-id="19705-124">The FTP task supports the *?*</span></span> <span data-ttu-id="19705-125">및 *\** 와일드카드 문자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-125">and *\** wildcard characters in paths.</span></span> <span data-ttu-id="19705-126">와일드카드 문자를 사용하면 태스크가 여러 개의 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-126">This lets the task access multiple files.</span></span> <span data-ttu-id="19705-127">그러나 와일드카드 문자는 파일 이름을 지정하는 경로 부분에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-127">However, you can use wildcard characters only in the part of the path that specifies the file name.</span></span> <span data-ttu-id="19705-128">예를 들어 C:\MyDirectory\\*.txt는 유효한 경로지만 C:\\\*\MyText.txt는 유효한 경로가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="19705-128">For example, C:\MyDirectory\\*.txt is a valid path, but C:\\\*\MyText.txt is not.</span></span>  
  
 <span data-ttu-id="19705-129">작업 실패 시 파일 시스템 태스크를 중지하거나 ASCII 모드로 파일을 전송하도록 FTP 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-129">The FTP operations can be configured to stop the File System task when the operation fails, or to transfer files in ASCII mode.</span></span> <span data-ttu-id="19705-130">파일 복사본을 보내고 받는 작업은 대상 파일과 디렉터리를 덮어쓰도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-130">The operations that send and receive files copy can be configured to overwrite destination files and directories.</span></span>  
  
## <a name="predefined-ftp-operations"></a><span data-ttu-id="19705-131">미리 정의된 FTP 작업</span><span class="sxs-lookup"><span data-stu-id="19705-131">Predefined FTP Operations</span></span>  
 <span data-ttu-id="19705-132">FTP 태스크에는 미리 정의된 작업 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-132">The FTP task includes a predefined set of operations.</span></span> <span data-ttu-id="19705-133">다음 표에서는 이러한 작업을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-133">The following table describes these operations.</span></span>  
  
|<span data-ttu-id="19705-134">작업(Operation)</span><span class="sxs-lookup"><span data-stu-id="19705-134">Operation</span></span>|<span data-ttu-id="19705-135">Description</span><span class="sxs-lookup"><span data-stu-id="19705-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19705-136">파일 보내기</span><span class="sxs-lookup"><span data-stu-id="19705-136">Send files</span></span>|<span data-ttu-id="19705-137">로컬 컴퓨터의 파일을 FTP 서버로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="19705-137">Sends a file from the local computer to the FTP server.</span></span>|  
|<span data-ttu-id="19705-138">파일 받기</span><span class="sxs-lookup"><span data-stu-id="19705-138">Receive files</span></span>|<span data-ttu-id="19705-139">FTP 서버의 파일을 로컬 컴퓨터에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-139">Saves a file from the FTP server to the local computer.</span></span>|  
|<span data-ttu-id="19705-140">로컬 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="19705-140">Create local directory</span></span>|<span data-ttu-id="19705-141">로컬 컴퓨터에 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19705-141">Creates a folder on the local computer.</span></span>|  
|<span data-ttu-id="19705-142">원격 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="19705-142">Create remote directory</span></span>|<span data-ttu-id="19705-143">FTP 서버에 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19705-143">Creates a folder on the FTP server.</span></span>|  
|<span data-ttu-id="19705-144">로컬 디렉터리 제거</span><span class="sxs-lookup"><span data-stu-id="19705-144">Remove local directory</span></span>|<span data-ttu-id="19705-145">로컬 컴퓨터의 폴더를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-145">Deletes a folder on the local computer.</span></span>|  
|<span data-ttu-id="19705-146">원격 디렉터리 제거</span><span class="sxs-lookup"><span data-stu-id="19705-146">Remove remote directory</span></span>|<span data-ttu-id="19705-147">FTP 서버의 폴더를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-147">Deletes a folder on the FTP server.</span></span>|  
|<span data-ttu-id="19705-148">로컬 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="19705-148">Delete local files</span></span>|<span data-ttu-id="19705-149">로컬 컴퓨터의 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-149">Deletes a file on the local computer.</span></span>|  
|<span data-ttu-id="19705-150">원격 파일 삭제</span><span class="sxs-lookup"><span data-stu-id="19705-150">Delete remote files</span></span>|<span data-ttu-id="19705-151">FTP 서버의 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-151">Deletes a file on the FTP server.</span></span>|  
  
## <a name="custom-log-entries-available-on-the-ftp-task"></a><span data-ttu-id="19705-152">FTP 태스크에 사용할 수 있는 사용자 지정 로그 항목</span><span class="sxs-lookup"><span data-stu-id="19705-152">Custom Log Entries Available on the FTP Task</span></span>  
 <span data-ttu-id="19705-153">다음 표에서는 FTP 태스크에 대한 사용자 지정 로그 항목을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-153">The following table lists the custom log entries for the FTP task.</span></span> <span data-ttu-id="19705-154">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19705-154">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="19705-155">로그 항목</span><span class="sxs-lookup"><span data-stu-id="19705-155">Log entry</span></span>|<span data-ttu-id="19705-156">Description</span><span class="sxs-lookup"><span data-stu-id="19705-156">Description</span></span>|  
|---------------|-----------------|  
|`FTPConnectingToServer`|<span data-ttu-id="19705-157">태스크에서 FTP 서버에 대한 연결을 시작했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="19705-157">Indicates that the task initiated a connection to the FTP server.</span></span>|  
|`FTPOperation`|<span data-ttu-id="19705-158">태스크에서 수행하는 FTP 작업의 시작 부분과 유형을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="19705-158">Reports the beginning of and the type of FTP operation that the task performs.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="19705-159">관련 작업</span><span class="sxs-lookup"><span data-stu-id="19705-159">Related Tasks</span></span>  
 <span data-ttu-id="19705-160">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19705-160">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="19705-161">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법에 대한 자세한 내용은 [태스크 또는 컨테이너의 속성 설정](../set-the-properties-of-a-task-or-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19705-161">For information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="19705-162">이러한 속성을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="19705-162">For more information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19705-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19705-163">See Also</span></span>  
 <span data-ttu-id="19705-164">[FTP 태스크 편집기 &#40;일반 페이지&#41;](../general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="19705-164">[FTP Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="19705-165">[FTP 태스크 편집기 &#40;파일 전송 페이지&#41;](../ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="19705-165">[FTP Task Editor &#40;File Transfer Page&#41;](../ftp-task-editor-file-transfer-page.md) </span></span>  
 <span data-ttu-id="19705-166">[Integration Services 태스크](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="19705-166">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 [<span data-ttu-id="19705-167">제어 흐름</span><span class="sxs-lookup"><span data-stu-id="19705-167">Control Flow</span></span>](control-flow.md)  
  
  
