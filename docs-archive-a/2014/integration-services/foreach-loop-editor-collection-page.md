---
title: Foreach 루프 편집기 (컬렉션 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 08/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.collection.f1
ms.assetid: 95a19dde-61ca-4d9b-aa3d-131fa4264296
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a90ce0c8971c57ef90b502cfde298605a73c253d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743372"
---
# <a name="foreach-loop-editor-collection-page"></a><span data-ttu-id="50cf5-102">Foreach 루프 편집기(컬렉션 페이지)</span><span class="sxs-lookup"><span data-stu-id="50cf5-102">Foreach Loop Editor (Collection Page)</span></span>
  <span data-ttu-id="50cf5-103">**Foreach 루프 편집기** 대화 상자의 **컬렉션** 페이지를 사용하여 열거자 유형을 지정하고 열거자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-103">Use the **Collection** pageof the **Foreach Loop Editor** dialog box to specify the enumerator type and configure the enumerator.</span></span>  
  
 <span data-ttu-id="50cf5-104">Foreach 루프 컨테이너와 이를 구성하는 방법은 [Foreach 루프 컨테이너](control-flow/foreach-loop-container.md) 및 [Foreach 루프 컨테이너 구성](../../2014/integration-services/configure-a-foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50cf5-104">To learn about the Foreach Loop container and how to configure it, see [Foreach Loop Container](control-flow/foreach-loop-container.md) and [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="50cf5-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="50cf5-105">Static Options</span></span>  
 <span data-ttu-id="50cf5-106">**Enumerator**</span><span class="sxs-lookup"><span data-stu-id="50cf5-106">**Enumerator**</span></span>  
 <span data-ttu-id="50cf5-107">목록에서 열거자 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-107">Select the enumerator type from the list.</span></span> <span data-ttu-id="50cf5-108">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="50cf5-109">값</span><span class="sxs-lookup"><span data-stu-id="50cf5-109">Value</span></span>|<span data-ttu-id="50cf5-110">Description</span><span class="sxs-lookup"><span data-stu-id="50cf5-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50cf5-111">**Foreach File 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-111">**Foreach File Enumerator**</span></span>|<span data-ttu-id="50cf5-112">파일을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-112">Enumerate files.</span></span> <span data-ttu-id="50cf5-113">이 값을 선택하면 아래의 **Foreach File 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-113">Selecting this value displays the dynamic options in the section, **Foreach File Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-114">**Foreach Item 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-114">**Foreach Item Enumerator**</span></span>|<span data-ttu-id="50cf5-115">항목의 값을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-115">Enumerate values in an item.</span></span> <span data-ttu-id="50cf5-116">이 값을 선택하면 아래의 **Foreach Item 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-116">Selecting this value displays the dynamic options in the section, **Foreach Item Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-117">**Foreach ADO 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-117">**Foreach ADO Enumerator**</span></span>|<span data-ttu-id="50cf5-118">테이블 또는 테이블의 행을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-118">Enumerate tables or rows in tables.</span></span> <span data-ttu-id="50cf5-119">이 값을 선택하면 아래의 **Foreach ADO 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-119">Selecting this value displays the dynamic options in the section, **Foreach ADO Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-120">**Foreach ADO.NET 스키마 행 집합 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-120">**Foreach ADO.NET Schema Rowset Enumerator**</span></span>|<span data-ttu-id="50cf5-121">스키마를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-121">Enumerate a schema.</span></span> <span data-ttu-id="50cf5-122">이 값을 선택하면 아래의 **Foreach ADO.NET 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-122">Selecting this value displays the dynamic options in the section, **Foreach ADO.NET Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-123">**Foreach From Variable 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-123">**Foreach From Variable Enumerator**</span></span>|<span data-ttu-id="50cf5-124">변수의 값을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-124">Enumerate the value in a variable.</span></span> <span data-ttu-id="50cf5-125">이 값을 선택하면 아래의 **Foreach From Variable 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-125">Selecting this value displays the dynamic options in the section, **Foreach From Variable Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-126">**Foreach Nodelist 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-126">**Foreach Nodelist Enumerator**</span></span>|<span data-ttu-id="50cf5-127">XML 문서의 노드를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-127">Enumerate nodes in an XML document.</span></span> <span data-ttu-id="50cf5-128">이 값을 선택하면 아래의 **Foreach Nodelist 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-128">Selecting this value displays the dynamic options in the section, **Foreach Nodelist Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-129">**Foreach SMO 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-129">**Foreach SMO Enumerator**</span></span>|<span data-ttu-id="50cf5-130">SMO 개체를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-130">Enumerate a SMO object.</span></span> <span data-ttu-id="50cf5-131">이 값을 선택하면 아래의 **Foreach SMO 열거자**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-131">Selecting this value displays the dynamic options in the section, **Foreach SMO Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-132">**Foreach Azure Blob 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-132">**Foreach Azure Blob Enumerator**</span></span>|<span data-ttu-id="50cf5-133">지정된 Blob 위치에 있는 Blob 파일을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-133">Enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="50cf5-134">이 값을 선택하면 **Foreach Azure Blob 열거자**섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-134">Selecting this value displays the dynamic options in the section, **Foreach Azure Blob Enumerator**.</span></span>|  
|<span data-ttu-id="50cf5-135">**Foreach ADLS File 열거자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-135">**Foreach ADLS File Enumerator**</span></span>|<span data-ttu-id="50cf5-136">필터를 사용 하 여 ADLS에서 파일을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-136">Enumerate files on ADLS with filters.</span></span> <span data-ttu-id="50cf5-137">이 값을 선택하면 **Foreach ADLS File 열거자**섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-137">Selecting this value displays the dynamic options in the section, **Foreach ADLS File Enumerator**.</span></span>|
  
 <span data-ttu-id="50cf5-138">**식**</span><span class="sxs-lookup"><span data-stu-id="50cf5-138">**Expressions**</span></span>  
 <span data-ttu-id="50cf5-139">기존 속성 식 목록을 보려면 **식** 을 클릭 또는 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-139">Click or expand **Expressions** to view the list of existing property expressions.</span></span> <span data-ttu-id="50cf5-140">줄임표 단추 **(...)** 를 클릭하여 열거자 속성에 대한 속성 식을 추가하거나 기존 속성 식을 편집 및 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-140">Click the ellipsis button **(...)** to add a property expression for an enumerator property, or edit and evaluate an existing property expression.</span></span>  
  
 <span data-ttu-id="50cf5-141">**관련 항목:**  [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md), [속성 식 편집기](expressions/property-expressions-editor.md), [식 작성기](expressions/expression-builder.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-141">**Related Topics:**  [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md), [Property Expressions Editor](expressions/property-expressions-editor.md), [Expression Builder](expressions/expression-builder.md)</span></span>  
  
## <a name="enumerator-dynamic-options"></a><span data-ttu-id="50cf5-142">Enumerator 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="50cf5-142">Enumerator Dynamic Options</span></span>  
  
### <a name="enumerator--foreach-file-enumerator"></a><span data-ttu-id="50cf5-143">Enumerator = Foreach File 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-143">Enumerator = Foreach File Enumerator</span></span>  
 <span data-ttu-id="50cf5-144">폴더의 파일을 열거하는 데 Foreach File 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-144">You use the Foreach File enumerator to enumerate files in a folder.</span></span> <span data-ttu-id="50cf5-145">예를 들어 Foreach 루프가 SQL 실행 태스크를 포함하는 경우 Foreach File 열거자를 사용하여 SQL 실행 태스크에서 실행하는 SQL 문을 포함하는 파일을 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-145">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach File enumerator to enumerate files that contain SQL statements that the Execute SQL task runs.</span></span> <span data-ttu-id="50cf5-146">하위 폴더를 포함하도록 열거자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-146">The enumerator can be configured to include subfolders.</span></span>  
  
 <span data-ttu-id="50cf5-147">루프의 외부 프로세스 또는 태스크에서는 루프가 실행되는 동안 파일을 추가, 삭제하거나 파일 이름을 바꾸기 때문에 Foreach File 열거자가 열거하는 폴더 및 하위 폴더의 내용이 루프가 실행되는 동안 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-147">The content of the folders and subfolders that the Foreach File enumerator enumerates might change while the loop is executing because external processes or tasks in the loop add, rename, or delete files while the loop is executing.</span></span> <span data-ttu-id="50cf5-148">즉, 다음과 같은 예기치 않은 상황이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-148">This means that a number of unexpected situations may occur:</span></span>  
  
-   <span data-ttu-id="50cf5-149">파일을 삭제한 경우 Foreach 루프의 특정 태스크에서 후속 태스크에 사용되는 파일과 다른 파일 집합에 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-149">If files are deleted, one task in the Foreach Loop may perform work on a different set of files than the files used by subsequent tasks.</span></span>  
  
-   <span data-ttu-id="50cf5-150">파일 이름이 바뀌어 외부 프로세스에서 이름이 바뀐 파일을 대체하기 위해 자동으로 파일을 추가한 경우 Foreach 루프가 같은 파일 내용에 대해 작업을 두 번 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-150">If files are renamed and an external process automatically adds files to replace the renamed files, the Foreach Loop might perform work twice on the same file content.</span></span>  
  
-   <span data-ttu-id="50cf5-151">파일을 추가한 경우 Foreach 루프가 작업을 수행한 파일을 확인하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-151">If files are added, it may be difficult to determine for which files the Foreach Loop performed work.</span></span>  
  
 <span data-ttu-id="50cf5-152">**폴더**</span><span class="sxs-lookup"><span data-stu-id="50cf5-152">**Folder**</span></span>  
 <span data-ttu-id="50cf5-153">열거할 루트 폴더의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-153">Provide the path of the root folder to enumerate.</span></span>  
  
 <span data-ttu-id="50cf5-154">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="50cf5-154">**Browse**</span></span>  
 <span data-ttu-id="50cf5-155">루트 폴더를 찾으려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-155">Browse to locate the root folder.</span></span>  
  
 <span data-ttu-id="50cf5-156">**파일**</span><span class="sxs-lookup"><span data-stu-id="50cf5-156">**Files**</span></span>  
 <span data-ttu-id="50cf5-157">열거할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-157">Specify the files to enumerate.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50cf5-158">와일드카드 문자(\*)를 사용하여 컬렉션에 포함할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-158">Use wildcard characters (\*) to specify the files to include in the collection.</span></span> <span data-ttu-id="50cf5-159">예를 들어 이름에 “abc”가 포함된 파일을 포함하려면 \*abc\* 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-159">For example, to include files with names that contain "abc", use the following filter: \*abc\*.</span></span>  
>   
>  <span data-ttu-id="50cf5-160">파일 이름 확장명을 지정하면 열거자는 동일한 확장명에 추가 문자가 포함된 파일도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-160">When you specify a file name extension, the enumerator also returns files that have the same extension with additional characters appended.</span></span> <span data-ttu-id="50cf5-161">이 동작은 이전 버전과의 호환성을 위해 8.3 파일 이름도 비교하는 운영 체제의 **dir** 명령줄 동작과 같습니다. 이 열거자 동작으로 인해 예기치 못한 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-161">(This is the same behavior as that of the **dir** command in the operating system, which also compares 8.3 file names for backward compatibility.) This behavior of the enumerator could cause unexpected results.</span></span> <span data-ttu-id="50cf5-162">예를 들어 Excel 2003 파일만 열거하기 위해 "\*.xls"를 지정하면</span><span class="sxs-lookup"><span data-stu-id="50cf5-162">For example, you want to enumerate only Excel 2003 files, and you specify "\*.xls".</span></span> <span data-ttu-id="50cf5-163">열거자는 Excel 2007 파일도 반환합니다. 이는 Excel 2007 파일의 확장명이 ".xlsx"이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-163">However, the enumerator will also return Excel 2007 files because those files have the extension, ".xlsx".</span></span>  
>   
>  <span data-ttu-id="50cf5-164">식을 사용하여 컬렉션에 포함할 파일을 지정할 수 있습니다. **컬렉션** 페이지에서 **식**을 확장하고 **FileSpec** 속성을 선택한 다음, 줄임표 단추(...)를 클릭하여 속성 식을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-164">You can use an expression to specify the files to include in a collection, by expanding **Expressions** on the **Collection** page, selecting the **FileSpec** property, and then clicking the ellipsis button (...) to add the property expression.</span></span> <span data-ttu-id="50cf5-165">지정 된 파일을 동적으로 선택 하는 방법에 대 한 자세한 내용은 [SSIS-동적으로 파일 마스크 설정: FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50cf5-165">For more information about dynamically selecting specified files, see [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span></span>  
  
 <span data-ttu-id="50cf5-166">**정규화된 이름**</span><span class="sxs-lookup"><span data-stu-id="50cf5-166">**Fully qualified**</span></span>  
 <span data-ttu-id="50cf5-167">파일 이름의 정규화된 경로를 검색하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-167">Select to retrieve the fully qualified path of file names.</span></span> <span data-ttu-id="50cf5-168">파일 옵션에서 와일드카드 문자를 지정한 경우 반환된 정규화된 경로가 필터와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-168">If wildcard characters are specified in the Files option, then the fully-qualified paths that are returned match the filter.</span></span>  
  
 <span data-ttu-id="50cf5-169">**이름만**</span><span class="sxs-lookup"><span data-stu-id="50cf5-169">**Name only**</span></span>  
 <span data-ttu-id="50cf5-170">파일 이름만 검색하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-170">Select to retrieve only the file names.</span></span> <span data-ttu-id="50cf5-171">파일 옵션에서 와일드카드 문자를 지정하지 않은 경우 반환된 파일 이름이 필터와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-171">If wildcard characters are specified in the Files option, then the file names returned match the filter.</span></span>  
  
 <span data-ttu-id="50cf5-172">**이름 및 확장명**</span><span class="sxs-lookup"><span data-stu-id="50cf5-172">**Name and extension**</span></span>  
 <span data-ttu-id="50cf5-173">파일 이름 및 해당 파일 이름 확장명을 검색하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-173">Select to retrieve the file names and their file name extensions.</span></span> <span data-ttu-id="50cf5-174">파일 옵션에서 와일드카드 문자를 지정한 경우 반환된 파일의 이름과 확장명이 필터와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-174">If wildcard characters are specified in the Files option, then the name and extension of files returned match the filter.</span></span>  
  
 <span data-ttu-id="50cf5-175">**하위 폴더 포함**</span><span class="sxs-lookup"><span data-stu-id="50cf5-175">**Traverse Subfolders**</span></span>  
 <span data-ttu-id="50cf5-176">열거에 하위 폴더를 포함하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-176">Select to include the subfolders in the enumeration.</span></span>  
  
### <a name="enumerator--foreach-item-enumerator"></a><span data-ttu-id="50cf5-177">Enumerator = Foreach Item 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-177">Enumerator = Foreach Item Enumerator</span></span>  
 <span data-ttu-id="50cf5-178">컬렉션의 항목을 열거하는 데 Foreach Item 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-178">You use the Foreach Item enumerator to enumerate items in a collection.</span></span> <span data-ttu-id="50cf5-179">열 및 열 값을 지정하여 컬렉션의 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-179">You define the items in the collection by specifying columns and column values.</span></span> <span data-ttu-id="50cf5-180">행의 열은 항목을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-180">The columns in a row define an item.</span></span> <span data-ttu-id="50cf5-181">예를 들어 프로세스 실행 태스크에서 실행하는 실행 파일과 해당 태스크에서 사용하는 작업 디렉터리를 지정하는 항목에는 두 개의 열, 즉 실행 파일의 이름을 나열하는 열과 작업 디렉터리를 나열하는 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-181">For example, an item that specifies the executables that an Execute Process task runs and the working directory that the task uses has two columns, one that lists the names of executables and one that lists the working directory.</span></span> <span data-ttu-id="50cf5-182">행 수는 루프가 반복되는 횟수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-182">The number of rows determines the number of times that the loop is repeated.</span></span> <span data-ttu-id="50cf5-183">테이블에 10개의 행이 있는 경우 루프는 10번 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-183">If the table has 10 rows, the loop repeats 10 times.</span></span>  
  
 <span data-ttu-id="50cf5-184">프로세스 실행 태스크의 속성을 업데이트하려면 열의 인덱스를 사용하여 변수를 항목 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-184">To update the properties of the Execute Process task, you map variables to item columns by using the index of the column.</span></span> <span data-ttu-id="50cf5-185">인덱스 값은 열거자 항목에 정의된 첫 번째 열에 0, 두 번째 열에 1과 같이 열에 순서대로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-185">The first column defined in the enumerator item has the index value 0, the second column 1, and so on.</span></span> <span data-ttu-id="50cf5-186">변수 값은 루프가 반복될 때마다 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-186">The variable values are updated with each repeat of the loop.</span></span> <span data-ttu-id="50cf5-187">그런 다음 프로세스 실행 태스크의 `Executable` 및 `WorkingDirectory` 속성은 이러한 변수를 사용하는 속성 식으로 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-187">The `Executable` and `WorkingDirectory` properties of the Execute Process task can then be updated by property expressions that use these variables.</span></span>  
  
 <span data-ttu-id="50cf5-188">**For Each Item 컬렉션에 항목 정의**</span><span class="sxs-lookup"><span data-stu-id="50cf5-188">**Define the items in the For Each Item collection**</span></span>  
 <span data-ttu-id="50cf5-189">테이블의 각 열에 대한 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-189">Provide a value for each column in the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50cf5-190">행 열에 값을 입력하면 새 행이 해당 테이블에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-190">A new row is automatically added to the table after you enter values in row columns.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50cf5-191">입력한 값이 열 데이터 형식과 호환되지 않으면 텍스트가 빨간색으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-191">If the values provided are not compatible with the column data type, the text is colored red.</span></span>  
  
 <span data-ttu-id="50cf5-192">**열 데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="50cf5-192">**Column data type**</span></span>  
 <span data-ttu-id="50cf5-193">활성 열의 데이터 형식을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-193">Lists the data type of the active column.</span></span>  
  
 <span data-ttu-id="50cf5-194">**제거**</span><span class="sxs-lookup"><span data-stu-id="50cf5-194">**Remove**</span></span>  
 <span data-ttu-id="50cf5-195">목록에서 항목을 제거하려면 항목을 선택하고 **제거** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-195">Select an item, and then click **Remove** to remove it from the list.</span></span>  
  
 <span data-ttu-id="50cf5-196">**열**</span><span class="sxs-lookup"><span data-stu-id="50cf5-196">**Columns**</span></span>  
 <span data-ttu-id="50cf5-197">항목에 있는 열의 데이터 형식을 구성하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-197">Click to configure the data type of the columns in the item.</span></span>  
  
 <span data-ttu-id="50cf5-198">**관련 항목:** [For Each Item 열 대화 상자 UI 참조](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-198">**Related Topics:** [For Each Item Columns Dialog Box UI Reference](../../2014/integration-services/for-each-item-columns-dialog-box-ui-reference.md)</span></span>  
  
### <a name="enumerator--foreach-ado-enumerator"></a><span data-ttu-id="50cf5-199">Enumerator = Foreach ADO 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-199">Enumerator = Foreach ADO Enumerator</span></span>  
 <span data-ttu-id="50cf5-200">변수에 저장된 ADO 또는 ADO.NET 개체의 행이나 테이블을 열거하는 데 Foreach ADO 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-200">You use the Foreach ADO enumerator to enumerate rows or tables in an ADO or ADO.NET object that is stored in a variable.</span></span> <span data-ttu-id="50cf5-201">예를 들어 Foreach 루프가 변수에 데이터 세트를 기록하는 스크립트 태스크를 포함하는 경우 Foreach ADO 열거자를 사용하여 데이터 세트의 행을 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-201">For example, if the Foreach Loop includes a Script task that writes a dataset to a variable, you can use the Foreach ADO enumerator to enumerate the rows in the dataset.</span></span> <span data-ttu-id="50cf5-202">변수가 ADO.NET 데이터 세트를 포함하는 경우 여러 테이블의 행을 열거하거나 테이블을 열거하도록 열거자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-202">If the variable contains an ADO.NET dataset, the enumerator can be configured to enumerate rows in multiple tables or to enumerate tables.</span></span>  
  
 <span data-ttu-id="50cf5-203">**ADO 개체 원본 변수**</span><span class="sxs-lookup"><span data-stu-id="50cf5-203">**ADO object source variable**</span></span>  
 <span data-ttu-id="50cf5-204">목록에서 사용자 정의 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-204">Select a user-defined variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50cf5-205">변수에 Object 데이터 형식이 있어야 합니다. 그렇지 않으면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-205">The variable must have the Object data type, otherwise an error occurs.</span></span>  
  
 <span data-ttu-id="50cf5-206">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-206">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="50cf5-207">**첫 번째 테이블의 행**</span><span class="sxs-lookup"><span data-stu-id="50cf5-207">**Rows in first table**</span></span>  
 <span data-ttu-id="50cf5-208">첫 번째 테이블의 행만 열거하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-208">Select to enumerate only rows in the first table.</span></span>  
  
 <span data-ttu-id="50cf5-209">**모든 테이블의 행(ADO.NET 데이터 세트에만 해당)**</span><span class="sxs-lookup"><span data-stu-id="50cf5-209">**Rows in all tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="50cf5-210">모든 테이블의 행을 열거하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-210">Select to enumerate rows in all tables.</span></span> <span data-ttu-id="50cf5-211">이 옵션은 열거할 모든 개체가 같은 ADO.NET 데이터 세트의 멤버인 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-211">This option is available only if the objects to enumerate are all members of the same ADO.NET dataset.</span></span>  
  
 <span data-ttu-id="50cf5-212">**모든 테이블(ADO.NET 데이터 세트에만 해당)**</span><span class="sxs-lookup"><span data-stu-id="50cf5-212">**All tables (ADO.NET dataset only)**</span></span>  
 <span data-ttu-id="50cf5-213">테이블만 열거하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-213">Select to enumerate tables only.</span></span>  
  
### <a name="enumerator--foreach-adonet-schema-rowset-enumerator"></a><span data-ttu-id="50cf5-214">Enumerator = Foreach ADO.NET 스키마 행 집합 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-214">Enumerator = Foreach ADO.NET Schema Rowset Enumerator</span></span>  
 <span data-ttu-id="50cf5-215">지정한 데이터 원본에 대한 스키마를 열거하는 데 Foreach ADO.NET 스키마 행 집합 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-215">You use the Foreach ADO.NET Schema Rowset enumerator to enumerate a schema for a specified data source.</span></span> <span data-ttu-id="50cf5-216">예를 들어 Foreach 루프가 SQL 실행 태스크를 포함하는 경우 Foreach ADO.NET 스키마 행 집합 열거자를 사용하여 **AdventureWorks** 데이터베이스의 열과 같은 스키마를 열거하고 SQL 실행 태스크를 사용하여 스키마 사용 권한을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-216">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach ADO.NET Schema Rowset enumerator to enumerate schemas such as the columns in the **AdventureWorks** database, and the Execute SQL task to get the schema permissions.</span></span>  
  
 <span data-ttu-id="50cf5-217">**연결**</span><span class="sxs-lookup"><span data-stu-id="50cf5-217">**Connection**</span></span>  
 <span data-ttu-id="50cf5-218">목록에서 ADO.NET 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 ADO.NET 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-218">Select an ADO.NET connection manager in the list, or click \<**New connection...**> to create a new ADO.NET connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="50cf5-219">ADO.NET 연결 관리자는 OLE DB용 .NET 공급자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-219">The ADO.NET connection manager must use a .NET provider for OLE DB.</span></span> <span data-ttu-id="50cf5-220">SQL Server에 연결하는 경우 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 연결 관리자 **대화 상자의** OleDb용 .NET 공급자 **섹션에 나열된** Native Client를 공급자로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-220">If connecting to SQL Server, the recommended provider to use is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, listed in the **.Net Providers for OleDb** section of the **Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="50cf5-221">**관련 항목:** [ADO 연결 관리자](connection-manager/ado-connection-manager.md), [ADO.NET 연결 관리자 구성](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-221">**Related Topics:** [ADO Connection Manager](connection-manager/ado-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="50cf5-222">**스키마**</span><span class="sxs-lookup"><span data-stu-id="50cf5-222">**Schema**</span></span>  
 <span data-ttu-id="50cf5-223">열거할 스키마를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-223">Select the schema to enumerate.</span></span>  
  
 <span data-ttu-id="50cf5-224">**제한 설정**</span><span class="sxs-lookup"><span data-stu-id="50cf5-224">**Set Restrictions**</span></span>  
 <span data-ttu-id="50cf5-225">지정한 스키마에 적용할 제한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-225">Set the restrictions to apply to the specified schema.</span></span>  
  
 <span data-ttu-id="50cf5-226">**관련 항목:** [스키마 제한 대화 상자](../../2014/integration-services/schema-restrictions-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-226">**Related Topics:** [Schema Restrictions Dialog Box](../../2014/integration-services/schema-restrictions-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-from-variable-enumerator"></a><span data-ttu-id="50cf5-227">Enumerator = Foreach From Variable 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-227">Enumerator = Foreach From Variable Enumerator</span></span>  
 <span data-ttu-id="50cf5-228">지정한 변수의 열거 가능한 개체를 열거하는 데 Foreach From Variable 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-228">You use the Foreach From Variable enumerator to enumerate the enumerable objects in the specified variable.</span></span> <span data-ttu-id="50cf5-229">예를 들어 Foreach 루프가 쿼리를 실행하여 변수에 결과를 저장하는 SQL 실행 태스크를 포함하는 경우 Foreach From Variable 열거자를 사용하여 쿼리 결과를 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-229">For example, if the Foreach Loop includes an Execute SQL task that runs a query and stores the result in a variable, you can use the Foreach From Variable enumerator to enumerate the query results.</span></span>  
  
 <span data-ttu-id="50cf5-230">**변수**</span><span class="sxs-lookup"><span data-stu-id="50cf5-230">**Variable**</span></span>  
 <span data-ttu-id="50cf5-231">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-231">Select a variable in the list, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="50cf5-232">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-232">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="enumerator--foreach-nodelist-enumerator"></a><span data-ttu-id="50cf5-233">Enumerator = Foreach NodeList 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-233">Enumerator = Foreach NodeList Enumerator</span></span>  
 <span data-ttu-id="50cf5-234">XML 파일에 XPath 식을 적용한 결과 생성된 XML 노드 집합을 열거하는 데 Foreach Nodelist 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-234">You use the Foreach Nodelist enumerator to enumerate the set of XML nodes that results from applying an XPath expression to an XML file.</span></span> <span data-ttu-id="50cf5-235">예를 들어 Foreach 루프가 스크립트 태스크를 포함하는 경우 Foreach NodeList 열거자를 사용하여 XPath 식 조건에 부합하는 값을 XML 파일에서 스크립트 태스크로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-235">For example, if the Foreach Loop includes a Script task, you can use the Foreach NodeList enumerator to pass a value that meets the XPath expression criteria from the XML file to the Script task.</span></span>  
  
 <span data-ttu-id="50cf5-236">XML 파일에 적용되는 XPath 식은 OuterXPathString 속성에 저장되는 외부 XPath 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-236">The XPath expression that applies to the XML file is the outer XPath operation, stored in the OuterXPathString property.</span></span> <span data-ttu-id="50cf5-237">XPath 열거형 형식이로 설정 된 경우 `ElementCollection` Foreach NodeList 열거자는 InnerXPathString 속성에 저장 된 내부 XPath 식을 요소 컬렉션에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-237">If the XPath enumeration type is set to `ElementCollection`, the Foreach NodeList enumerator can apply an inner XPath expression, stored in the InnerXPathString property, to a collection of element.</span></span>  
  
 <span data-ttu-id="50cf5-238">XML 문서 및 데이터 작업 방법은 MSDN Library의 "[.NET Framework에 XML 적용(Employing XML in the .NET Framework)](https://go.microsoft.com/fwlink/?LinkId=56214)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="50cf5-238">To learn more about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
 <span data-ttu-id="50cf5-239">**DocumentSourceType**</span><span class="sxs-lookup"><span data-stu-id="50cf5-239">**DocumentSourceType**</span></span>  
 <span data-ttu-id="50cf5-240">XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-240">Select the source type of the XML document.</span></span> <span data-ttu-id="50cf5-241">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-241">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="50cf5-242">값</span><span class="sxs-lookup"><span data-stu-id="50cf5-242">Value</span></span>|<span data-ttu-id="50cf5-243">Description</span><span class="sxs-lookup"><span data-stu-id="50cf5-243">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50cf5-244">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="50cf5-244">**Direct input**</span></span>|<span data-ttu-id="50cf5-245">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-245">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="50cf5-246">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="50cf5-246">**File connection**</span></span>|<span data-ttu-id="50cf5-247">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-247">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="50cf5-248">**변수**</span><span class="sxs-lookup"><span data-stu-id="50cf5-248">**Variable**</span></span>|<span data-ttu-id="50cf5-249">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-249">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="50cf5-250">**DocumentSource**</span><span class="sxs-lookup"><span data-stu-id="50cf5-250">**DocumentSource**</span></span>  
 <span data-ttu-id="50cf5-251">**DocumentSourceType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표(...) 단추를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-251">If **DocumentSourceType** is set to **Direct input**, provide the XML code, or click the ellipsis (...) button to provide XML by using the **Document Source Edito**r dialog box.</span></span>  
  
 <span data-ttu-id="50cf5-252">**DocumentSourceType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-252">If **DocumentSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="50cf5-253">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-253">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="50cf5-254">**DocumentSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-254">If **DocumentSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="50cf5-255">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-255">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="50cf5-256">**EnumerationType**</span><span class="sxs-lookup"><span data-stu-id="50cf5-256">**EnumerationType**</span></span>  
 <span data-ttu-id="50cf5-257">목록에서 열거 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-257">Select an enumeration type from the list.</span></span> <span data-ttu-id="50cf5-258">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-258">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="50cf5-259">값</span><span class="sxs-lookup"><span data-stu-id="50cf5-259">Value</span></span>|<span data-ttu-id="50cf5-260">Description</span><span class="sxs-lookup"><span data-stu-id="50cf5-260">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50cf5-261">**Navigator**</span><span class="sxs-lookup"><span data-stu-id="50cf5-261">**Navigator**</span></span>|<span data-ttu-id="50cf5-262">XPathNavigator를 사용하여 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-262">Enumerate using an XPathNavigator.</span></span>|  
|<span data-ttu-id="50cf5-263">**Node**</span><span class="sxs-lookup"><span data-stu-id="50cf5-263">**Node**</span></span>|<span data-ttu-id="50cf5-264">XPath 작업에서 반환한 노드를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-264">Enumerate nodes returned by an XPath operation.</span></span>|  
|<span data-ttu-id="50cf5-265">**NodeText**</span><span class="sxs-lookup"><span data-stu-id="50cf5-265">**NodeText**</span></span>|<span data-ttu-id="50cf5-266">XPath 작업에서 반환한 텍스트 노드를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-266">Enumerate text nodes returned by an XPath operation.</span></span>|  
|`ElementCollection`|<span data-ttu-id="50cf5-267">XPath 작업에서 반환한 요소 노드를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-267">Enumerates element nodes returned by an XPath operation.</span></span>|  
  
 <span data-ttu-id="50cf5-268">**OuterXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="50cf5-268">**OuterXPathStringSourceType**</span></span>  
 <span data-ttu-id="50cf5-269">XPath 문자열의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-269">Select the source type of the XPath string.</span></span> <span data-ttu-id="50cf5-270">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-270">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="50cf5-271">값</span><span class="sxs-lookup"><span data-stu-id="50cf5-271">Value</span></span>|<span data-ttu-id="50cf5-272">Description</span><span class="sxs-lookup"><span data-stu-id="50cf5-272">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50cf5-273">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="50cf5-273">**Direct input**</span></span>|<span data-ttu-id="50cf5-274">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-274">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="50cf5-275">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="50cf5-275">**File connection**</span></span>|<span data-ttu-id="50cf5-276">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-276">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="50cf5-277">**변수**</span><span class="sxs-lookup"><span data-stu-id="50cf5-277">**Variable**</span></span>|<span data-ttu-id="50cf5-278">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-278">Set the source to a variable that contains the XML document.</span></span>|  
  
 `OuterXPathString`  
 <span data-ttu-id="50cf5-279">**OuterXPathStringSourceType**을 **직접 입력**으로 설정한 경우 XPath 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-279">If **OuterXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="50cf5-280">**OuterXPathStringSourceType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-280">If **OuterXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="50cf5-281">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-281">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="50cf5-282">**OuterXPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-282">If **OuterXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="50cf5-283">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-283">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="50cf5-284">**InnerElementType**</span><span class="sxs-lookup"><span data-stu-id="50cf5-284">**InnerElementType**</span></span>  
 <span data-ttu-id="50cf5-285">**EnumerationType** 가로 설정 된 경우 `ElementCollection` 목록에서 내부 요소의 유형을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-285">If **EnumerationType** is set to `ElementCollection`, select the type of inner element in the list.</span></span>  
  
 <span data-ttu-id="50cf5-286">**InnerXPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="50cf5-286">**InnerXPathStringSourceType**</span></span>  
 <span data-ttu-id="50cf5-287">내부 XPath 문자열의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-287">Select the source type of the inner XPath string.</span></span> <span data-ttu-id="50cf5-288">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-288">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="50cf5-289">값</span><span class="sxs-lookup"><span data-stu-id="50cf5-289">Value</span></span>|<span data-ttu-id="50cf5-290">Description</span><span class="sxs-lookup"><span data-stu-id="50cf5-290">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50cf5-291">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="50cf5-291">**Direct input**</span></span>|<span data-ttu-id="50cf5-292">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-292">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="50cf5-293">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="50cf5-293">**File connection**</span></span>|<span data-ttu-id="50cf5-294">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-294">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="50cf5-295">**변수**</span><span class="sxs-lookup"><span data-stu-id="50cf5-295">**Variable**</span></span>|<span data-ttu-id="50cf5-296">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-296">Set the source to a variable that contains the XML document.</span></span>|  
  
 `InnerXPathString`  
 <span data-ttu-id="50cf5-297">**InnerXPathStringSourceType**을 **직접 입력**으로 설정한 경우 XPath 문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-297">If **InnerXPathStringSourceType** is set to **Direct input**, provide the XPath string.</span></span>  
  
 <span data-ttu-id="50cf5-298">**InnerXPathStringSourceType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-298">If **InnerXPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="50cf5-299">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-299">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="50cf5-300">**InnerXPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-300">If **InnerXPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="50cf5-301">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-301">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="enumerator--foreach-smo-enumerator"></a><span data-ttu-id="50cf5-302">Enumerator = Foreach SMO 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-302">Enumerator = Foreach SMO Enumerator</span></span>  
 <span data-ttu-id="50cf5-303">SMO(SQL Server Management Objects) 개체를 열거하는 데 Foreach SMO 열거자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-303">You use the Foreach SMO enumerator to enumerate SQL Server Management Object (SMO) objects.</span></span> <span data-ttu-id="50cf5-304">예를 들어 Foreach 루프가 SQL 실행 태스크를 포함하는 경우 Foreach SMO 열거자를 사용하여 **AdventureWorks** 데이터베이스의 테이블을 열거하고 각 테이블의 행 수를 계산하는 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-304">For example, if the Foreach Loop includes an Execute SQL task, you can use the Foreach SMO enumerator to enumerate the tables in the **AdventureWorks** database and run queries that counts the number of rows in each table.</span></span>  
  
 <span data-ttu-id="50cf5-305">**연결**</span><span class="sxs-lookup"><span data-stu-id="50cf5-305">**Connection**</span></span>  
 <span data-ttu-id="50cf5-306">기존 ADO.NET 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-306">Select an existing ADO.NET connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="50cf5-307">관련 항목: [ADO.NET 연결 관리자](connection-manager/ado-net-connection-manager.md), [ADO.NET 연결 관리자 구성](configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-307">Related Topics: [ADO.NET Connection Manager](connection-manager/ado-net-connection-manager.md), [Configure ADO.NET Connection Manager](configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="50cf5-308">**열거**</span><span class="sxs-lookup"><span data-stu-id="50cf5-308">**Enumerate**</span></span>  
 <span data-ttu-id="50cf5-309">열거할 SMO 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-309">Specify the SMO object to enumerate.</span></span>  
  
 <span data-ttu-id="50cf5-310">**찾아보기**</span><span class="sxs-lookup"><span data-stu-id="50cf5-310">**Browse**</span></span>  
 <span data-ttu-id="50cf5-311">SMO 열거를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-311">Select the SMO enumeration.</span></span>  
  
 <span data-ttu-id="50cf5-312">**관련 항목:** [SMO 열거 선택 대화 상자](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="50cf5-312">**Related Topics:** [Select SMO Enumeration Dialog Box](../../2014/integration-services/select-smo-enumeration-dialog-box.md)</span></span>  
  
### <a name="enumerator--foreach-azure-blob-enumerator"></a><span data-ttu-id="50cf5-313">열거자 = Foreach Azure Blob 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-313">Enumerator = Foreach Azure Blob Enumerator</span></span>  
 <span data-ttu-id="50cf5-314">**Azure Blob 열거자**를 사용하면 SSIS 패키지에서 지정된 Blob 위치에 있는 Blob 파일을 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-314">The  **Azure Blob Enumerator**r enables an SSIS package to enumerate blob files in the specified blob location.</span></span> <span data-ttu-id="50cf5-315">열거된 Blob 파일의 이름을 변수에 저장하여 Foreach 루프 컨테이너 내의 작업에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-315">The name of enumerated blob file can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>  
  
 <span data-ttu-id="50cf5-316">**Azure Storage 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="50cf5-316">**Azure storage connection manager**</span></span>  
 <span data-ttu-id="50cf5-317">기존 Azure Storage 연결 관리자를 선택하거나 Azure Storage 계정을 참조하는 연결 관리자 하나를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-317">Select an existing Azure Storage Connection Manager or create a new one that refers to an Azure Storage Account.</span></span>  
  
 <span data-ttu-id="50cf5-318">관련 항목: [Azure Storage 연결 관리자](connection-manager/azure-storage-connection-manager.md).</span><span class="sxs-lookup"><span data-stu-id="50cf5-318">Related Topics: [Azure Storage Connection Manager](connection-manager/azure-storage-connection-manager.md).</span></span>  
  
 <span data-ttu-id="50cf5-319">**Blob 컨테이너 이름**</span><span class="sxs-lookup"><span data-stu-id="50cf5-319">**Blob container name**</span></span>  
 <span data-ttu-id="50cf5-320">열거할 Blob 파일을 포함하는 Blob 컨테이너의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-320">Specify the name of the blob container that contains the blob files to be enumerated..</span></span>  
  
 <span data-ttu-id="50cf5-321">**Blob 디렉터리**</span><span class="sxs-lookup"><span data-stu-id="50cf5-321">**Blob directory**</span></span>  
 <span data-ttu-id="50cf5-322">열거할 Blob 파일을 포함하는 Blob 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-322">Specify the specify the blob directory that contains the blob files to be enumerated.</span></span> <span data-ttu-id="50cf5-323">blob 디렉터리는 가상 계층 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-323">The blob directory is a virtual hierarchical structure.</span></span>  
  
 <span data-ttu-id="50cf5-324">**Blob 이름 필터**</span><span class="sxs-lookup"><span data-stu-id="50cf5-324">**Blob name filter**</span></span>  
 <span data-ttu-id="50cf5-325">특정 이름 패턴의 파일을 열거하려면 이름 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-325">Specify a name filter to enumerate files with a certain name pattern.</span></span> <span data-ttu-id="50cf5-326">예를 들어</span><span class="sxs-lookup"><span data-stu-id="50cf5-326">E.g.</span></span> <span data-ttu-id="50cf5-327">MySheet\*.xls\* 는 MySheet001.xls 및 MySheetABC.xlsx와 같은 파일을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-327">MySheet\*.xls\* will include files such as MySheet001.xls and MySheetABC.xlsx.</span></span>  
  
 <span data-ttu-id="50cf5-328">**Blob 시간 범위 시작/끝 필터**</span><span class="sxs-lookup"><span data-stu-id="50cf5-328">**Blob time range from/to filter**</span></span>  
 <span data-ttu-id="50cf5-329">시간 범위 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-329">Specify a time range filter.</span></span> <span data-ttu-id="50cf5-330">**TimeRangeFrom** 에서 **TimeRangeTo** 사이에 수정된 파일이 열거됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-330">Files modified after **TimeRangeFrom** and before **TimeRangeTo** will be enumerated.</span></span>  
### <a name="enumerator--foreach-adls-file-enumerator"></a><span data-ttu-id="50cf5-331"> 열거자 = Foreach ADLS File 열거자</span><span class="sxs-lookup"><span data-stu-id="50cf5-331">Enumerator = Foreach ADLS File Enumerator</span></span>  
<span data-ttu-id="50cf5-332">**ADLS File 열거자** 를 사용 하면 SSIS 패키지에서 ADLS의 파일을 필터로 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-332">The **ADLS File Enumerator** enables an SSIS package to enumerate files on ADLS with filters.</span></span> <span data-ttu-id="50cf5-333">슬래시 ( `/` )-앞에 열거 된 파일의 전체 경로를 변수에 저장 하 고 Foreach 루프 컨테이너 내의 태스크에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-333">The slash (`/`)-prefixed full path of enumerated files can be stored in a variable and used in tasks inside the Foreach Loop Container.</span></span>
  
<span data-ttu-id="50cf5-334">**AzureDataLakeConnection**</span><span class="sxs-lookup"><span data-stu-id="50cf5-334">**AzureDataLakeConnection**</span></span>  
<span data-ttu-id="50cf5-335">Azure Data Lake 연결 관리자를 지정하거나 ADLS 계정을 참조하는 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-335">Specifies an Azure Data Lake connection manager, or creates a new one that refers to an ADLS account.</span></span>   
  
<span data-ttu-id="50cf5-336">**AzureDataLakeDirectory**</span><span class="sxs-lookup"><span data-stu-id="50cf5-336">**AzureDataLakeDirectory**</span></span>  
<span data-ttu-id="50cf5-337">검색할 ADLS 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-337">Specifies the ADLS directory to search.</span></span>
  
<span data-ttu-id="50cf5-338">**FileNamePattern**</span><span class="sxs-lookup"><span data-stu-id="50cf5-338">**FileNamePattern**</span></span>  
<span data-ttu-id="50cf5-339">파일 이름 필터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-339">Specifies a file name filter.</span></span> <span data-ttu-id="50cf5-340">지정 된 패턴과 일치 하는 이름을 가진 파일만 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-340">Only files whose name matches the specified pattern will be enumerated.</span></span> <span data-ttu-id="50cf5-341">와일드카드 `*` 및 `?`가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-341">Wildcards `*` and `?` are supported.</span></span> 
  
<span data-ttu-id="50cf5-342">**SearchRecursively**</span><span class="sxs-lookup"><span data-stu-id="50cf5-342">**SearchRecursively**</span></span>  
<span data-ttu-id="50cf5-343">지정된 디렉터리 내에서 재귀적으로 검색할 것인지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50cf5-343">Specifies whether to search recursively within the specified directory.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="50cf5-344">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="50cf5-344">External Resources</span></span>  
  
-   <span data-ttu-id="50cf5-345">bidn.com의 블로그 항목 - [각 노드 목록 열거자에 대한 SSIS](https://go.microsoft.com/fwlink/?LinkId=220671)</span><span class="sxs-lookup"><span data-stu-id="50cf5-345">Blog entry, [SSIS For Each Node List Enumerator](https://go.microsoft.com/fwlink/?LinkId=220671), on bidn.com.</span></span>  
  
-   <span data-ttu-id="50cf5-346">블로그 항목, [SSIS-동적으로 파일 마스크 설정: FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html)</span><span class="sxs-lookup"><span data-stu-id="50cf5-346">Blog entry, [SSIS-Dynamically set File Mask : FileSpec](https://rajsudeep.blogspot.com/2010/09/ssisdynamically-set-file-mask-filespec.html).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cf5-347">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50cf5-347">See Also</span></span>  
 <span data-ttu-id="50cf5-348">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="50cf5-348">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="50cf5-349">[Foreach 루프 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="50cf5-349">[Foreach Loop Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="50cf5-350">[Foreach 루프 편집기 &#40;변수 매핑 페이지&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span><span class="sxs-lookup"><span data-stu-id="50cf5-350">[Foreach Loop Editor &#40;Variable Mappings Page&#41;](../../2014/integration-services/foreach-loop-editor-variable-mappings-page.md) </span></span>  
 <span data-ttu-id="50cf5-351">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="50cf5-351">[Expressions Page](expressions/expressions-page.md) </span></span>  
 [<span data-ttu-id="50cf5-352">For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="50cf5-352">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
