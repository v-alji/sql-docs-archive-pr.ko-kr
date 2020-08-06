---
title: FTP 태스크 편집기 (파일 전송 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8094051e93c4165be6ae186bde394f9271d60669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648443"
---
# <a name="ftp-task-editor-file-transfer-page"></a><span data-ttu-id="713b2-102">FTP 태스크 편집기(파일 전송 페이지)</span><span class="sxs-lookup"><span data-stu-id="713b2-102">FTP Task Editor (File Transfer Page)</span></span>
  <span data-ttu-id="713b2-103">**FTP 태스크 편집기** 대화 상자의 **파일 전송** 페이지를 사용하여 태스크에서 수행할 FTP 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-103">Use the **File Transfer** page of the **FTP Task Editor** dialog box to configure the FTP operation that the task performs.</span></span>  
  
 <span data-ttu-id="713b2-104">이 태스크에 대한 자세한 내용은 [FTP 태스크](control-flow/ftp-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="713b2-104">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="713b2-105">옵션</span><span class="sxs-lookup"><span data-stu-id="713b2-105">Options</span></span>  
 <span data-ttu-id="713b2-106">**IsRemotePathVariable**</span><span class="sxs-lookup"><span data-stu-id="713b2-106">**IsRemotePathVariable**</span></span>  
 <span data-ttu-id="713b2-107">원격 경로가 변수에 저장되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-107">Indicate whether the remote path is stored in a variable.</span></span> <span data-ttu-id="713b2-108">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="713b2-109">값</span><span class="sxs-lookup"><span data-stu-id="713b2-109">Value</span></span>|<span data-ttu-id="713b2-110">Description</span><span class="sxs-lookup"><span data-stu-id="713b2-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="713b2-111">**True**</span><span class="sxs-lookup"><span data-stu-id="713b2-111">**True**</span></span>|<span data-ttu-id="713b2-112">대상 경로가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-112">The destination path is stored in a variable.</span></span> <span data-ttu-id="713b2-113">이 값을 선택하면 동적 옵션 **RemoteVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-113">Selecting the value displays the dynamic option, **RemoteVariable**.</span></span>|  
|<span data-ttu-id="713b2-114">**False**</span><span class="sxs-lookup"><span data-stu-id="713b2-114">**False**</span></span>|<span data-ttu-id="713b2-115">파일 연결 관리자에서 대상 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-115">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="713b2-116">이 값을 선택하면 동적 옵션 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-116">Selecting the value displays the dynamic option, **RemotePath**.</span></span>|  
  
 <span data-ttu-id="713b2-117">**OverwriteFileAtDestination**</span><span class="sxs-lookup"><span data-stu-id="713b2-117">**OverwriteFileAtDestination**</span></span>  
 <span data-ttu-id="713b2-118">대상 파일을 덮어쓸 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-118">Specify whether a file at the destination can be overwritten.</span></span>  
  
 <span data-ttu-id="713b2-119">**IsLocalPathVariable**</span><span class="sxs-lookup"><span data-stu-id="713b2-119">**IsLocalPathVariable**</span></span>  
 <span data-ttu-id="713b2-120">로컬 경로가 변수에 저장되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-120">Indicate whether the local path is stored in a variable.</span></span> <span data-ttu-id="713b2-121">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-121">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="713b2-122">값</span><span class="sxs-lookup"><span data-stu-id="713b2-122">Value</span></span>|<span data-ttu-id="713b2-123">Description</span><span class="sxs-lookup"><span data-stu-id="713b2-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="713b2-124">**True**</span><span class="sxs-lookup"><span data-stu-id="713b2-124">**True**</span></span>|<span data-ttu-id="713b2-125">대상 경로가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-125">The destination path is stored in a variable.</span></span> <span data-ttu-id="713b2-126">이 값을 선택하면 동적 옵션 **LocalVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-126">Selecting the value displays the dynamic option, **LocalVariable**.</span></span>|  
|<span data-ttu-id="713b2-127">**False**</span><span class="sxs-lookup"><span data-stu-id="713b2-127">**False**</span></span>|<span data-ttu-id="713b2-128">파일 연결 관리자에서 대상 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-128">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="713b2-129">이 값을 선택하면 동적 옵션 **LocalPath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-129">Selecting the value displays the dynamic option, **LocalPath**.</span></span>|  
  
 <span data-ttu-id="713b2-130">**연산**</span><span class="sxs-lookup"><span data-stu-id="713b2-130">**Operation**</span></span>  
 <span data-ttu-id="713b2-131">수행할 FTP 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-131">Select the FTP operation to perform.</span></span> <span data-ttu-id="713b2-132">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="713b2-133">값</span><span class="sxs-lookup"><span data-stu-id="713b2-133">Value</span></span>|<span data-ttu-id="713b2-134">Description</span><span class="sxs-lookup"><span data-stu-id="713b2-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="713b2-135">**파일 보내기**</span><span class="sxs-lookup"><span data-stu-id="713b2-135">**Send files**</span></span>|<span data-ttu-id="713b2-136">파일을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-136">Send files.</span></span> <span data-ttu-id="713b2-137">이 값을 선택하면 동적 옵션 **LocalVariable**, **LocalPathRemoteVariable** 및 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-137">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="713b2-138">**파일 받기**</span><span class="sxs-lookup"><span data-stu-id="713b2-138">**Receive files**</span></span>|<span data-ttu-id="713b2-139">파일을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-139">Receive files.</span></span> <span data-ttu-id="713b2-140">이 값을 선택하면 동적 옵션 **LocalVariable**, **LocalPathRemoteVariable** 및 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-140">Selecting this value displays the dynamic options, **LocalVariable**, **LocalPathRemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="713b2-141">**로컬 디렉터리 만들기**</span><span class="sxs-lookup"><span data-stu-id="713b2-141">**Create local directory**</span></span>|<span data-ttu-id="713b2-142">로컬 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-142">Create a local directory.</span></span> <span data-ttu-id="713b2-143">이 값을 선택하면 동적 옵션 **LocalVariable** 및 **LocalPath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-143">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="713b2-144">**원격 디렉터리 만들기**</span><span class="sxs-lookup"><span data-stu-id="713b2-144">**Create remote directory**</span></span>|<span data-ttu-id="713b2-145">원격 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-145">Create a remote directory.</span></span> <span data-ttu-id="713b2-146">이 값을 선택하면 동적 옵션 **RemoteVariable** 및 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-146">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotelPath**.</span></span>|  
|<span data-ttu-id="713b2-147">**로컬 디렉터리 제거**</span><span class="sxs-lookup"><span data-stu-id="713b2-147">**Remove local directory**</span></span>|<span data-ttu-id="713b2-148">로컬 디렉터리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-148">Removes a local directory.</span></span> <span data-ttu-id="713b2-149">이 값을 선택하면 동적 옵션 **LocalVariable** 및 **LocalPath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-149">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="713b2-150">**원격 디렉터리 제거**</span><span class="sxs-lookup"><span data-stu-id="713b2-150">**Remove remote directory**</span></span>|<span data-ttu-id="713b2-151">원격 디렉터리를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-151">Remove a remote directory.</span></span> <span data-ttu-id="713b2-152">이 값을 선택하면 동적 옵션 **RemoteVariable** 및 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-152">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
|<span data-ttu-id="713b2-153">**로컬 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="713b2-153">**Delete local files**</span></span>|<span data-ttu-id="713b2-154">로컬 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-154">Delete local files.</span></span> <span data-ttu-id="713b2-155">이 값을 선택하면 동적 옵션 **LocalVariable** 및 **LocalPath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-155">Selecting this value displays the dynamic options, **LocalVariable** and **LocalPath**.</span></span>|  
|<span data-ttu-id="713b2-156">**원격 파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="713b2-156">**Delete remote files**</span></span>|<span data-ttu-id="713b2-157">원격 파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-157">Delete remote files.</span></span> <span data-ttu-id="713b2-158">이 값을 선택하면 동적 옵션 **RemoteVariable** 및 **RemotePath**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-158">Selecting this value displays the dynamic options, **RemoteVariable** and **RemotePath**.</span></span>|  
  
 <span data-ttu-id="713b2-159">**IsTransferASCII**</span><span class="sxs-lookup"><span data-stu-id="713b2-159">**IsTransferASCII**</span></span>  
 <span data-ttu-id="713b2-160">원격 FTP 서버와 파일을 주고 받을 때 ASCII 모드로 파일을 전송할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-160">Indicate whether files transferred to and from the remote FTP server should be transferred in ASCII mode.</span></span>  
  
## <a name="isremotepathvariable-dynamic-options"></a><span data-ttu-id="713b2-161">IsRemotePathVariable 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="713b2-161">IsRemotePathVariable Dynamic Options</span></span>  
  
### <a name="isremotepathvariable--true"></a><span data-ttu-id="713b2-162">IsRemotePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="713b2-162">IsRemotePathVariable = True</span></span>  
 <span data-ttu-id="713b2-163">**RemoteVariable**</span><span class="sxs-lookup"><span data-stu-id="713b2-163">**RemoteVariable**</span></span>  
 <span data-ttu-id="713b2-164">기존 사용자 정의 변수를 선택하거나 \<**New variable...**>를 클릭하여 사용자 정의 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-164">Select an existing user-defined variable, or click \<**New variable...**> to create a user-defined variable.</span></span>  
  
 <span data-ttu-id="713b2-165">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), 변수 추가</span><span class="sxs-lookup"><span data-stu-id="713b2-165">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="isremotepathvariable--false"></a><span data-ttu-id="713b2-166">IsRemotePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="713b2-166">IsRemotePathVariable = False</span></span>  
 <span data-ttu-id="713b2-167">**RemotePath**</span><span class="sxs-lookup"><span data-stu-id="713b2-167">**RemotePath**</span></span>  
 <span data-ttu-id="713b2-168">기존 FTP 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-168">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="713b2-169">**관련 항목:** [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="713b2-169">**Related Topics:** [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
## <a name="islocalpathvariable-dynamic-options"></a><span data-ttu-id="713b2-170">IsLocalPathVariable 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="713b2-170">IsLocalPathVariable Dynamic Options</span></span>  
  
### <a name="islocalpathvariable--true"></a><span data-ttu-id="713b2-171">IsLocalPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="713b2-171">IsLocalPathVariable = True</span></span>  
 <span data-ttu-id="713b2-172">**LocalVariable**</span><span class="sxs-lookup"><span data-stu-id="713b2-172">**LocalVariable**</span></span>  
 <span data-ttu-id="713b2-173">기존 사용자 정의 변수를 선택하거나 \<**New variable...**>를 클릭하여 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-173">Select an existing user-defined variable, or click \<**New variable...**> to create a variable.</span></span>  
  
 <span data-ttu-id="713b2-174">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), 변수 추가</span><span class="sxs-lookup"><span data-stu-id="713b2-174">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), Add Variable</span></span>  
  
### <a name="islocalpathvariable--false"></a><span data-ttu-id="713b2-175">IsLocalPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="713b2-175">IsLocalPathVariable = False</span></span>  
 <span data-ttu-id="713b2-176">**LocalPath**</span><span class="sxs-lookup"><span data-stu-id="713b2-176">**LocalPath**</span></span>  
 <span data-ttu-id="713b2-177">기존 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="713b2-177">Select an existing File connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
 <span data-ttu-id="713b2-178">**관련 항목**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="713b2-178">**Related Topics**: [Flat File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713b2-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="713b2-179">See Also</span></span>  
 <span data-ttu-id="713b2-180">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="713b2-180">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="713b2-181">[FTP 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="713b2-181">[FTP Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="713b2-182">식 페이지</span><span class="sxs-lookup"><span data-stu-id="713b2-182">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
