---
title: 파일 시스템 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e893f667c2a32fbc667c375dc57647d1aff1b806
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741136"
---
# <a name="file-system-task-editor-general-page"></a><span data-ttu-id="af2bc-102">파일 시스템 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="af2bc-102">File System Task Editor (General Page)</span></span>
  <span data-ttu-id="af2bc-103">**파일 시스템 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 태스크가 수행하는 파일 시스템 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-103">Use the **General** page of the **File System Task Editor** dialog to configure the file system operation that the task performs.</span></span>  
  
 <span data-ttu-id="af2bc-104">이 태스크에 대한 자세한 내용은 [File System Task](control-flow/file-system-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="af2bc-104">To learn about this task, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="af2bc-105">SourceConnection 및 DestinationConnection 속성을 설정하여 원본 및 대상 연결 관리자를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-105">You must specify a source and destination connection manager by setting the SourceConnection and DestinationConnection properties.</span></span> <span data-ttu-id="af2bc-106">태스크에서 원본 또는 대상으로 사용하는 파일을 가리키는 파일 연결 관리자의 이름을 입력하거나 파일 경로가 변수에 저장되어 있는 경우 변수 이름을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-106">You can either provide the names of File connection managers that point to the files that the task uses as a source or destination, or if the paths of the files are stored in variables, you can provide the names of the variables.</span></span> <span data-ttu-id="af2bc-107">변수를 사용하여 파일 경로를 저장하려면 먼저 원본 연결을 위한 IsSourcePathVariable 옵션 및 대상 연결을 위한 IsDestinationPatheVariable 옵션을 **True**로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-107">To use variables to store the file paths, you must set first set the IsSourcePathVariable option for the source connection and the IsDestinationPatheVariable option for the destination connection to **True**.</span></span> <span data-ttu-id="af2bc-108">그런 다음 기존 시스템 또는 사용자 정의 변수를 사용하도록 선택하거나 새로운 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-108">You can then choose the existing system or user-defined variables to use, or you can create new variables.</span></span> <span data-ttu-id="af2bc-109">**변수 추가** 대화 상자에서 변수의 범위를 구성하고 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-109">In the **Add Variable** dialog box, you can configure and specify the scope of the variables.</span></span> <span data-ttu-id="af2bc-110">변수의 범위는 파일 시스템 태스크 또는 부모 컨테이너여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-110">The scope must be the File System task or a parent container.</span></span> <span data-ttu-id="af2bc-111">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md) 및 [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2bc-111">For more information see, [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af2bc-112">및 속성에 대해 선택한 변수를 재정의 `SourceConnection` 하려면 `DestinationConnection` **Source** 및 **Destination** 속성에 대 한 식을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-112">To override the variables you selected for the `SourceConnection` and `DestinationConnection` properties, enter an expression for the **Source** and **Destination** properties.</span></span> <span data-ttu-id="af2bc-113">**파일 시스템 태스크 편집기** 의 **식**페이지에 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-113">You enter expressions on the **Expressions** page of the **File System Task Editor**.</span></span> <span data-ttu-id="af2bc-114">예를 들어 태스크에서 대상으로 사용하는 파일 경로를 설정하기 위해 특정 조건에서 변수 A를 사용하고 다른 조건에서는 변수 B를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-114">For example, to set the path of the files that the task uses as a destination, you may want to use variable A under certain conditions and use variable B under other conditions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af2bc-115">파일 시스템 태스크는 단일 파일 또는 디렉터리에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-115">The File System task operates on a single file or directory.</span></span> <span data-ttu-id="af2bc-116">따라서 이 태스크는 와일드카드 문자를 사용하여 여러 파일 또는 디렉터리에서 동일한 작업을 수행하도록 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-116">Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files or directories.</span></span> <span data-ttu-id="af2bc-117">파일 시스템 태스크가 여러 파일이나 디렉터리에서 작업을 반복하게 하려면 파일 시스템 태스크를 Foreach 루프 컨테이너에 넣으십시오.</span><span class="sxs-lookup"><span data-stu-id="af2bc-117">To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container.</span></span> <span data-ttu-id="af2bc-118">자세한 내용은 [File System Task](control-flow/file-system-task.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2bc-118">For more information, see [File System Task](control-flow/file-system-task.md).</span></span>  
  
 <span data-ttu-id="af2bc-119">식을 사용하여 다른 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-119">You can use expressions to use different variables for the</span></span>  
  
## <a name="options"></a><span data-ttu-id="af2bc-120">옵션</span><span class="sxs-lookup"><span data-stu-id="af2bc-120">Options</span></span>  
 <span data-ttu-id="af2bc-121">**IsDestinationPathVariable**</span><span class="sxs-lookup"><span data-stu-id="af2bc-121">**IsDestinationPathVariable**</span></span>  
 <span data-ttu-id="af2bc-122">대상 경로가 변수에 저장되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-122">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="af2bc-123">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-123">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="af2bc-124">값</span><span class="sxs-lookup"><span data-stu-id="af2bc-124">Value</span></span>|<span data-ttu-id="af2bc-125">Description</span><span class="sxs-lookup"><span data-stu-id="af2bc-125">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af2bc-126">**True**</span><span class="sxs-lookup"><span data-stu-id="af2bc-126">**True**</span></span>|<span data-ttu-id="af2bc-127">대상 경로가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-127">The destination path is stored in a variable.</span></span> <span data-ttu-id="af2bc-128">이 값을 선택하면 동적 옵션 **DestinationVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-128">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
|<span data-ttu-id="af2bc-129">**False**</span><span class="sxs-lookup"><span data-stu-id="af2bc-129">**False**</span></span>|<span data-ttu-id="af2bc-130">파일 연결 관리자에서 대상 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-130">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="af2bc-131">이 값을 선택 하면 동적 옵션가 표시 됩니다 `DestinationConnection` .</span><span class="sxs-lookup"><span data-stu-id="af2bc-131">Selecting this value displays the dynamic option, `DestinationConnection`.</span></span>|  
  
 <span data-ttu-id="af2bc-132">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="af2bc-132">**OverwriteDestination**</span></span>  
 <span data-ttu-id="af2bc-133">작업이 대상 디렉터리에 있는 파일을 덮어쓸 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-133">Specify whether the operation can overwrite files in the destination directory.</span></span>  
  
 <span data-ttu-id="af2bc-134">**이름**</span><span class="sxs-lookup"><span data-stu-id="af2bc-134">**Name**</span></span>  
 <span data-ttu-id="af2bc-135">파일 시스템 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-135">Provide a unique name for the File System task.</span></span> <span data-ttu-id="af2bc-136">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-136">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af2bc-137">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-137">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="af2bc-138">**설명**</span><span class="sxs-lookup"><span data-stu-id="af2bc-138">**Description**</span></span>  
 <span data-ttu-id="af2bc-139">파일 시스템 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-139">Type a description of the File System task.</span></span>  
  
 <span data-ttu-id="af2bc-140">**연산**</span><span class="sxs-lookup"><span data-stu-id="af2bc-140">**Operation**</span></span>  
 <span data-ttu-id="af2bc-141">수행할 파일 시스템 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-141">Select the file-system operation to perform.</span></span> <span data-ttu-id="af2bc-142">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-142">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="af2bc-143">값</span><span class="sxs-lookup"><span data-stu-id="af2bc-143">Value</span></span>|<span data-ttu-id="af2bc-144">Description</span><span class="sxs-lookup"><span data-stu-id="af2bc-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="af2bc-145">**디렉터리 복사**</span><span class="sxs-lookup"><span data-stu-id="af2bc-145">**Copy directory**</span></span>|<span data-ttu-id="af2bc-146">디렉터리를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-146">Copy a directory.</span></span> <span data-ttu-id="af2bc-147">이 값을 선택하면 원본 및 대상에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-147">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="af2bc-148">**파일 복사**</span><span class="sxs-lookup"><span data-stu-id="af2bc-148">**Copy file**</span></span>|<span data-ttu-id="af2bc-149">파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-149">Copy a file.</span></span> <span data-ttu-id="af2bc-150">이 값을 선택하면 원본 및 대상에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-150">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="af2bc-151">**디렉터리 만들기**</span><span class="sxs-lookup"><span data-stu-id="af2bc-151">**Create directory**</span></span>|<span data-ttu-id="af2bc-152">디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="af2bc-152">Create a directory.</span></span> <span data-ttu-id="af2bc-153">이 값을 선택하면 원본 및 대상 디렉터리에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-153">Selecting this value displays the dynamic options for a source and a destination directory.</span></span>|  
|<span data-ttu-id="af2bc-154">**디렉터리 삭제**</span><span class="sxs-lookup"><span data-stu-id="af2bc-154">**Delete directory**</span></span>|<span data-ttu-id="af2bc-155">디렉터리를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-155">Delete a directory.</span></span> <span data-ttu-id="af2bc-156">이 값을 선택하면 원본에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-156">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="af2bc-157">**디렉터리 내용 삭제**</span><span class="sxs-lookup"><span data-stu-id="af2bc-157">**Delete directory content**</span></span>|<span data-ttu-id="af2bc-158">디렉터리의 내용을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-158">Delete the content of a directory.</span></span> <span data-ttu-id="af2bc-159">이 값을 선택하면 원본에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-159">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="af2bc-160">**파일 삭제**</span><span class="sxs-lookup"><span data-stu-id="af2bc-160">**Delete file**</span></span>|<span data-ttu-id="af2bc-161">파일을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-161">Delete a file.</span></span> <span data-ttu-id="af2bc-162">이 값을 선택하면 원본에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-162">Selecting this value displays the dynamic options for a source.</span></span>|  
|<span data-ttu-id="af2bc-163">**디렉터리 이동**</span><span class="sxs-lookup"><span data-stu-id="af2bc-163">**Move directory**</span></span>|<span data-ttu-id="af2bc-164">디렉터리를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-164">Move a directory.</span></span> <span data-ttu-id="af2bc-165">이 값을 선택하면 원본 및 대상에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-165">Selecting this value displays the dynamic options for a source and destination.</span></span>|  
|<span data-ttu-id="af2bc-166">**파일 이동**</span><span class="sxs-lookup"><span data-stu-id="af2bc-166">**Move file**</span></span>|<span data-ttu-id="af2bc-167">파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-167">Move a file.</span></span> <span data-ttu-id="af2bc-168">이 값을 선택하면 원본 및 대상에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-168">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="af2bc-169">참고: 파일을 이동할 때 대상으로 제공한 디렉터리 경로에 파일 이름을 포함 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="af2bc-169">Note: When moving a file, do not include a file name in the directory path that you provide as the destination.</span></span>|  
|<span data-ttu-id="af2bc-170">**파일 이름 바꾸기**</span><span class="sxs-lookup"><span data-stu-id="af2bc-170">**Rename file**</span></span>|<span data-ttu-id="af2bc-171">파일 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-171">Rename a file.</span></span> <span data-ttu-id="af2bc-172">이 값을 선택하면 원본 및 대상에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-172">Selecting this value displays the dynamic options for a source and destination.</span></span><br /><br /> <span data-ttu-id="af2bc-173">참고: 파일 이름을 바꿀 때 대상에 대해 제공한 디렉터리 경로에 새 파일 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-173">Note: When renaming a file, include the new file name in the directory path that you provide for the destination.</span></span>|  
|<span data-ttu-id="af2bc-174">**특성 설정**</span><span class="sxs-lookup"><span data-stu-id="af2bc-174">**Set attributes**</span></span>|<span data-ttu-id="af2bc-175">파일 또는 디렉터리의 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-175">Set the attributes of a file or directory.</span></span> <span data-ttu-id="af2bc-176">이 값을 선택하면 원본 및 작업에 대한 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-176">Selecting this value displays the dynamic options for a source and operation.</span></span>|  
  
 `IsSourcePathVariable`  
 <span data-ttu-id="af2bc-177">대상 경로가 변수에 저장되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-177">Indicate whether the destination path is stored in a variable.</span></span> <span data-ttu-id="af2bc-178">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-178">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="af2bc-179">값</span><span class="sxs-lookup"><span data-stu-id="af2bc-179">Value</span></span>||  
|-----------|-|  
|<span data-ttu-id="af2bc-180">**True**</span><span class="sxs-lookup"><span data-stu-id="af2bc-180">**True**</span></span>|<span data-ttu-id="af2bc-181">대상 경로가 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-181">The destination path is stored in a variable.</span></span> <span data-ttu-id="af2bc-182">이 값을 선택하면 동적 옵션 **SourceVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-182">Selecting this value displays the dynamic option, **SourceVariable**.</span></span>|  
|<span data-ttu-id="af2bc-183">**False**</span><span class="sxs-lookup"><span data-stu-id="af2bc-183">**False**</span></span>|<span data-ttu-id="af2bc-184">파일 연결 관리자에서 대상 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-184">The destination path is specified in a File connection manager.</span></span> <span data-ttu-id="af2bc-185">이 값을 선택하면 동적 옵션 **DestinationVariable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-185">Selecting this value displays the dynamic option, **DestinationVariable**.</span></span>|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a><span data-ttu-id="af2bc-186">IsDestinationPathVariable 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="af2bc-186">IsDestinationPathVariable Dynamic Options</span></span>  
  
### <a name="isdestinationpathvariable--true"></a><span data-ttu-id="af2bc-187">IsDestinationPathVariable = True</span><span class="sxs-lookup"><span data-stu-id="af2bc-187">IsDestinationPathVariable = True</span></span>  
 <span data-ttu-id="af2bc-188">**DestinationVariable**</span><span class="sxs-lookup"><span data-stu-id="af2bc-188">**DestinationVariable**</span></span>  
 <span data-ttu-id="af2bc-189">목록에서 변수 이름을 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-189">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="af2bc-190">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="af2bc-190">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="isdestinationpathvariable--false"></a><span data-ttu-id="af2bc-191">IsDestinationPathVariable = False</span><span class="sxs-lookup"><span data-stu-id="af2bc-191">IsDestinationPathVariable = False</span></span>  
 `DestinationConnection`  
 <span data-ttu-id="af2bc-192">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-192">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="af2bc-193">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="af2bc-193">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="issourcepathvariable-dynamic-options"></a><span data-ttu-id="af2bc-194">IsSourcePathVariable 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="af2bc-194">IsSourcePathVariable Dynamic Options</span></span>  
  
### <a name="issourcepathvariable--true"></a><span data-ttu-id="af2bc-195">IsSourcePathVariable = True</span><span class="sxs-lookup"><span data-stu-id="af2bc-195">IsSourcePathVariable = True</span></span>  
 <span data-ttu-id="af2bc-196">**SourceVariable**</span><span class="sxs-lookup"><span data-stu-id="af2bc-196">**SourceVariable**</span></span>  
 <span data-ttu-id="af2bc-197">목록에서 변수 이름을 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-197">Select the variable name in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="af2bc-198">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="af2bc-198">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="issourcepathvariable--false"></a><span data-ttu-id="af2bc-199">IsSourcePathVariable = False</span><span class="sxs-lookup"><span data-stu-id="af2bc-199">IsSourcePathVariable = False</span></span>  
 `SourceConnection`  
 <span data-ttu-id="af2bc-200">목록에서 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-200">Select a File connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="af2bc-201">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="af2bc-201">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
## <a name="operation-dynamic-options"></a><span data-ttu-id="af2bc-202">Operation 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="af2bc-202">Operation Dynamic Options</span></span>  
  
### <a name="operation--set-attributes"></a><span data-ttu-id="af2bc-203">Operation = 특성 설정</span><span class="sxs-lookup"><span data-stu-id="af2bc-203">Operation = Set Attributes</span></span>  
 <span data-ttu-id="af2bc-204">**숨김**</span><span class="sxs-lookup"><span data-stu-id="af2bc-204">**Hidden**</span></span>  
 <span data-ttu-id="af2bc-205">파일 또는 디렉터리의 표시 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-205">Indicate whether the file or directory is visible.</span></span>  
  
 <span data-ttu-id="af2bc-206">**읽기 전용**</span><span class="sxs-lookup"><span data-stu-id="af2bc-206">**ReadOnly**</span></span>  
 <span data-ttu-id="af2bc-207">파일이 읽기 전용인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-207">Indicate whether the file is read-only.</span></span>  
  
 <span data-ttu-id="af2bc-208">**보관**</span><span class="sxs-lookup"><span data-stu-id="af2bc-208">**Archive**</span></span>  
 <span data-ttu-id="af2bc-209">파일 또는 디렉터리가 보관될 준비가 되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-209">Indicate whether the file or directory is ready for archiving.</span></span>  
  
 <span data-ttu-id="af2bc-210">**시스템**</span><span class="sxs-lookup"><span data-stu-id="af2bc-210">**System**</span></span>  
 <span data-ttu-id="af2bc-211">파일이 운영 체제 파일인지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-211">Indicate whether the file is an operating system file.</span></span>  
  
### <a name="operation--create-directory"></a><span data-ttu-id="af2bc-212">Operation = 디렉터리 만들기</span><span class="sxs-lookup"><span data-stu-id="af2bc-212">Operation = Create directory</span></span>  
 `UseDirectoryIfExists`  
 <span data-ttu-id="af2bc-213">**디렉터리 만들기** 작업이 새 디렉터리를 만들지 않고 지정된 이름의 기존 디렉터리를 사용하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="af2bc-213">Indicates whether the **Create directory** operation uses an existing directory with the specified name instead of creating a new directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2bc-214">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af2bc-214">See Also</span></span>  
 <span data-ttu-id="af2bc-215">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="af2bc-215">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="af2bc-216">식 페이지</span><span class="sxs-lookup"><span data-stu-id="af2bc-216">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
