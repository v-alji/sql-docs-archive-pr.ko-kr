---
title: XML 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.xmltask.general.f1
helpviewer_keywords:
- XML Task Editor
ms.assetid: b9622c48-3243-4408-a1de-9ba20e32ff70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f73681a818d80c4e8b2755086e653e5c7e682f01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736495"
---
# <a name="xml-task-editor-general-page"></a><span data-ttu-id="14e5e-102">XML 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="14e5e-102">XML Task Editor (General Page)</span></span>
  <span data-ttu-id="14e5e-103">**XML 태스크 편집기** 대화 상자의 **일반** 노드를 사용하여 작업 유형을 지정하고 작업을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-103">Use the **General Node** of the **XML Task Editor** dialog box to specify the operation type and configure the operation.</span></span>  
  
 <span data-ttu-id="14e5e-104">이 태스크에 대한 자세한 내용은 [XML Task](control-flow/xml-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14e5e-104">To learn about this task, see [XML Task](control-flow/xml-task.md).</span></span> <span data-ttu-id="14e5e-105">XML 문서 및 데이터 작업 방법은 MSDN Library의 "[.NET Framework에 XML 적용(Employing XML in the .NET Framework)](https://go.microsoft.com/fwlink/?LinkId=56214)"을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14e5e-105">For information about working with XML documents and data, see "[Employing XML in the .NET Framework](https://go.microsoft.com/fwlink/?LinkId=56214)" in the MSDN Library.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="14e5e-106">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="14e5e-106">Static Options</span></span>  
 <span data-ttu-id="14e5e-107">**OperationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-107">**OperationType**</span></span>  
 <span data-ttu-id="14e5e-108">목록에서 작업 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-108">Select the operation type from the list.</span></span> <span data-ttu-id="14e5e-109">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-109">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-110">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-110">Value</span></span>|<span data-ttu-id="14e5e-111">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-111">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-112">**유효성 검사**</span><span class="sxs-lookup"><span data-stu-id="14e5e-112">**Validate**</span></span>|<span data-ttu-id="14e5e-113">DTD(문서 유형 정의) 또는 XSD(XML 스키마 정의) 스키마와 비교하여 XML 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-113">Validates the XML document against a Document Type Definition (DTD) or XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="14e5e-114">이 옵션을 선택하면 아래의 **Validate**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-114">Selecting this option displays the dynamic options in section, **Validate**.</span></span>|  
|<span data-ttu-id="14e5e-115">**XSLT**</span><span class="sxs-lookup"><span data-stu-id="14e5e-115">**XSLT**</span></span>|<span data-ttu-id="14e5e-116">XML 문서에 대해 XSL 변환을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-116">Performs XSL transformations on XML documents.</span></span> <span data-ttu-id="14e5e-117">이 옵션을 선택하면 아래의 **XSLT**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-117">Selecting this option displays the dynamic options in section, **XSLT**.</span></span>|  
|<span data-ttu-id="14e5e-118">**XPATH**</span><span class="sxs-lookup"><span data-stu-id="14e5e-118">**XPATH**</span></span>|<span data-ttu-id="14e5e-119">XPath 쿼리 및 계산을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-119">Performs XPath queries and evaluations.</span></span> <span data-ttu-id="14e5e-120">이 옵션을 선택하면 아래의 **XPATH**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-120">Selecting this option displays the dynamic options in section, **XPATH**.</span></span>|  
|<span data-ttu-id="14e5e-121">**병합**</span><span class="sxs-lookup"><span data-stu-id="14e5e-121">**Merge**</span></span>|<span data-ttu-id="14e5e-122">두 개의 XML 문서를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-122">Merges two XML documents.</span></span> <span data-ttu-id="14e5e-123">이 옵션을 선택하면 아래의 **Merge**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-123">Selecting this option displays the dynamic options in section, **Merge**.</span></span>|  
|<span data-ttu-id="14e5e-124">**Diff**</span><span class="sxs-lookup"><span data-stu-id="14e5e-124">**Diff**</span></span>|<span data-ttu-id="14e5e-125">두 개의 XML 문서를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-125">Compares two XML documents.</span></span> <span data-ttu-id="14e5e-126">이 옵션을 선택하면 아래의 **Diff**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-126">Selecting this option displays the dynamic options in section, **Diff**.</span></span>|  
|<span data-ttu-id="14e5e-127">**Patch**</span><span class="sxs-lookup"><span data-stu-id="14e5e-127">**Patch**</span></span>|<span data-ttu-id="14e5e-128">비교 작업의 출력을 적용하여 새 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-128">Applies the output from the Diff operation to create a new document.</span></span> <span data-ttu-id="14e5e-129">이 옵션을 선택하면 아래의 **Patch**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-129">Selecting this option displays the dynamic options in section, **Patch**.</span></span>|  
  
 <span data-ttu-id="14e5e-130">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-130">**SourceType**</span></span>  
 <span data-ttu-id="14e5e-131">XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-131">Select the source type of the XML document.</span></span> <span data-ttu-id="14e5e-132">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-132">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-133">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-133">Value</span></span>|<span data-ttu-id="14e5e-134">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-135">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-135">**Direct input**</span></span>|<span data-ttu-id="14e5e-136">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-136">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-137">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-137">**File connection**</span></span>|<span data-ttu-id="14e5e-138">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-138">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-139">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-139">**Variable**</span></span>|<span data-ttu-id="14e5e-140">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-140">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-141">**원본**</span><span class="sxs-lookup"><span data-stu-id="14e5e-141">**Source**</span></span>  
 <span data-ttu-id="14e5e-142">**Source**를 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(…)** 를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-142">If **Source** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-143">**Source**를 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-143">If **Source** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-144">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-144">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-145">**Source**를 **변수**로 설정한 경우 기존 변수를 선택하거나 **\<New variable...>** 를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-145">If **Source** is set to **Variable**, select an existing variable, or click **\<New variable...>** to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-146">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-146">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
## <a name="operationtype-dynamic-options"></a><span data-ttu-id="14e5e-147">OperationType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="14e5e-147">OperationType Dynamic Options</span></span>  
  
### <a name="operationtype--validate"></a><span data-ttu-id="14e5e-148">OperationType = Validate</span><span class="sxs-lookup"><span data-stu-id="14e5e-148">OperationType = Validate</span></span>  
 <span data-ttu-id="14e5e-149">유효성 검사 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-149">Specify options for the Validate operation.</span></span>  
  
 <span data-ttu-id="14e5e-150">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-150">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-151">XML 태스크가 유효성 검사 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-151">Specify whether the XML task saves the output of the Validate operation.</span></span>  
  
 <span data-ttu-id="14e5e-152">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-152">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-153">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-153">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-154">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-154">**Destination**</span></span>  
 <span data-ttu-id="14e5e-155">기존 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-155">Select an existing File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-156">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-156">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-157">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-157">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-158">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-158">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-159">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-159">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-160">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-160">Value</span></span>|<span data-ttu-id="14e5e-161">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-161">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-162">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-162">**File connection**</span></span>|<span data-ttu-id="14e5e-163">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-163">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-164">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-164">**Variable**</span></span>|<span data-ttu-id="14e5e-165">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-165">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-166">**ValidationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-166">**ValidationType**</span></span>  
 <span data-ttu-id="14e5e-167">유효성 검사 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-167">Select the validation type.</span></span> <span data-ttu-id="14e5e-168">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-168">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-169">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-169">Value</span></span>|<span data-ttu-id="14e5e-170">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-170">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-171">**DTD**</span><span class="sxs-lookup"><span data-stu-id="14e5e-171">**DTD**</span></span>|<span data-ttu-id="14e5e-172">DTD(문서 유형 정의)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-172">Use a Document Type Definition (DTD).</span></span>|  
|<span data-ttu-id="14e5e-173">**XSD**</span><span class="sxs-lookup"><span data-stu-id="14e5e-173">**XSD**</span></span>|<span data-ttu-id="14e5e-174">XSD(XML 스키마 정의) 스키마를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-174">Use an XML Schema definition (XSD) schema.</span></span> <span data-ttu-id="14e5e-175">이 옵션을 선택하면 아래의 **ValidationType**섹션에 설명된 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-175">Selecting this option displays the dynamic options in section, **ValidationType**.</span></span>|  
  
 <span data-ttu-id="14e5e-176">**FailOnValidationFail**</span><span class="sxs-lookup"><span data-stu-id="14e5e-176">**FailOnValidationFail**</span></span>  
 <span data-ttu-id="14e5e-177">문서의 유효성 검사에 실패하는 경우 작업이 실패할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-177">Specify whether the operation fails if the document fails to validate.</span></span>  
  
 <span data-ttu-id="14e5e-178">**ValidationDetails**</span><span class="sxs-lookup"><span data-stu-id="14e5e-178">**ValidationDetails**</span></span>  
 <span data-ttu-id="14e5e-179">이 속성의 값이 true일 때 풍부한 오류 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-179">Provides rich error output when the value of this property is true.</span></span> <span data-ttu-id="14e5e-180">자세한 내용은 [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="14e5e-180">For more info, see [Validate XML with the XML Task](control-flow/validate-xml-with-the-xml-task.md).</span></span>  
  
### <a name="validationtype-dynamic-options"></a><span data-ttu-id="14e5e-181">ValidationType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="14e5e-181">ValidationType Dynamic Options</span></span>  
  
#### <a name="validationtype--xsd"></a><span data-ttu-id="14e5e-182">ValidationType = XSD</span><span class="sxs-lookup"><span data-stu-id="14e5e-182">ValidationType = XSD</span></span>  
 <span data-ttu-id="14e5e-183">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-183">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-184">두 번째 XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-184">Select the source type of the second XML document.</span></span> <span data-ttu-id="14e5e-185">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-185">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-186">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-186">Value</span></span>|<span data-ttu-id="14e5e-187">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-187">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-188">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-188">**Direct input**</span></span>|<span data-ttu-id="14e5e-189">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-189">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-190">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-190">**File connection**</span></span>|<span data-ttu-id="14e5e-191">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-191">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-192">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-192">**Variable**</span></span>|<span data-ttu-id="14e5e-193">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-193">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-194">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-194">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-195">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-195">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-196">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-196">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-197">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-197">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-198">**XPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-198">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-199">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-199">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xslt"></a><span data-ttu-id="14e5e-200">OperationType = XSLT</span><span class="sxs-lookup"><span data-stu-id="14e5e-200">OperationType = XSLT</span></span>  
 <span data-ttu-id="14e5e-201">XSLT 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-201">Specify options for the XSLT operation.</span></span>  
  
 <span data-ttu-id="14e5e-202">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-202">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-203">XML 태스크가 XSLT 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-203">Specify whether the XML task saves the output of the XSLT operation.</span></span>  
  
 <span data-ttu-id="14e5e-204">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-204">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-205">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-205">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-206">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-206">**Destination**</span></span>  
 <span data-ttu-id="14e5e-207">**DestinationType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-207">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-208">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-208">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-209">**DestinationType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-209">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-210">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-210">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-211">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-211">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-212">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-212">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-213">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-213">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-214">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-214">Value</span></span>|<span data-ttu-id="14e5e-215">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-215">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-216">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-216">**File connection**</span></span>|<span data-ttu-id="14e5e-217">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-217">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-218">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-218">**Variable**</span></span>|<span data-ttu-id="14e5e-219">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-219">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-220">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-220">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-221">두 번째 XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-221">Select the source type of the second XML document.</span></span> <span data-ttu-id="14e5e-222">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-222">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-223">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-223">Value</span></span>|<span data-ttu-id="14e5e-224">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-225">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-225">**Direct input**</span></span>|<span data-ttu-id="14e5e-226">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-226">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-227">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-227">**File connection**</span></span>|<span data-ttu-id="14e5e-228">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-228">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-229">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-229">**Variable**</span></span>|<span data-ttu-id="14e5e-230">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-230">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-231">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-231">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-232">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-232">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-233">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-233">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-234">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-234">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-235">**XPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-235">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-236">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-236">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
### <a name="operationtype--xpath"></a><span data-ttu-id="14e5e-237">OperationType = XPATH</span><span class="sxs-lookup"><span data-stu-id="14e5e-237">OperationType = XPATH</span></span>  
 <span data-ttu-id="14e5e-238">XPath 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-238">Specify options for the XPath operation.</span></span>  
  
 <span data-ttu-id="14e5e-239">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-239">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-240">XML 태스크가 XPath 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-240">Specify whether the XML task saves the output of the XPath operation.</span></span>  
  
 <span data-ttu-id="14e5e-241">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-241">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-242">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-242">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-243">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-243">**Destination**</span></span>  
 <span data-ttu-id="14e5e-244">**DestinationType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-244">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-245">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-245">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-246">**DestinationType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-246">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-247">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-247">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-248">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-248">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-249">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-249">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-250">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-250">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-251">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-251">Value</span></span>|<span data-ttu-id="14e5e-252">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-252">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-253">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-253">**File connection**</span></span>|<span data-ttu-id="14e5e-254">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-254">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-255">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-255">**Variable**</span></span>|<span data-ttu-id="14e5e-256">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-256">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-257">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-257">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-258">두 번째 XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-258">Select the source type of the second XML document.</span></span> <span data-ttu-id="14e5e-259">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-259">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-260">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-260">Value</span></span>|<span data-ttu-id="14e5e-261">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-261">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-262">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-262">**Direct input**</span></span>|<span data-ttu-id="14e5e-263">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-263">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-264">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-264">**File connection**</span></span>|<span data-ttu-id="14e5e-265">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-265">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-266">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-266">**Variable**</span></span>|<span data-ttu-id="14e5e-267">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-267">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-268">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-268">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-269">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-269">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-270">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-270">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-271">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-271">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-272">**XPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-272">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-273">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-273">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-274">**PutResultInOneNode**</span><span class="sxs-lookup"><span data-stu-id="14e5e-274">**PutResultInOneNode**</span></span>  
 <span data-ttu-id="14e5e-275">결과를 단일 노드에 쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-275">Specify whether the result is written to a single node.</span></span>  
  
 <span data-ttu-id="14e5e-276">**XPathOperation**</span><span class="sxs-lookup"><span data-stu-id="14e5e-276">**XPathOperation**</span></span>  
 <span data-ttu-id="14e5e-277">XPath 결과 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-277">Select the XPath result type.</span></span> <span data-ttu-id="14e5e-278">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-278">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-279">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-279">Value</span></span>|<span data-ttu-id="14e5e-280">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-280">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-281">**Evaluation**</span><span class="sxs-lookup"><span data-stu-id="14e5e-281">**Evaluation**</span></span>|<span data-ttu-id="14e5e-282">XPath 함수의 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-282">Returns the results of an XPath function.</span></span>|  
|<span data-ttu-id="14e5e-283">**노드 목록**</span><span class="sxs-lookup"><span data-stu-id="14e5e-283">**Node list**</span></span>|<span data-ttu-id="14e5e-284">선택한 노드를 XML 조각으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-284">Return the selected nodes as an XML fragment.</span></span>|  
|<span data-ttu-id="14e5e-285">**값**</span><span class="sxs-lookup"><span data-stu-id="14e5e-285">**Values**</span></span>|<span data-ttu-id="14e5e-286">선택한 모든 노드의 내부 텍스트 값을 연결 문자열로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-286">Return the inner text value of all selected nodes, concatenated into a string.</span></span>|  
  
### <a name="operationtype--merge"></a><span data-ttu-id="14e5e-287">OperationType = Merge</span><span class="sxs-lookup"><span data-stu-id="14e5e-287">OperationType = Merge</span></span>  
 <span data-ttu-id="14e5e-288">병합 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-288">Specify options for the Merge operation.</span></span>  
  
 <span data-ttu-id="14e5e-289">**XPathStringSourceType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-289">**XPathStringSourceType**</span></span>  
 <span data-ttu-id="14e5e-290">XML 문서의 원본 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-290">Select the source type of the XML document.</span></span> <span data-ttu-id="14e5e-291">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-291">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-292">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-292">Value</span></span>|<span data-ttu-id="14e5e-293">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-293">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-294">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-294">**Direct input**</span></span>|<span data-ttu-id="14e5e-295">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-295">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-296">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-296">**File connection**</span></span>|<span data-ttu-id="14e5e-297">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-297">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-298">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-298">**Variable**</span></span>|<span data-ttu-id="14e5e-299">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-299">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-300">**XPathStringSource**</span><span class="sxs-lookup"><span data-stu-id="14e5e-300">**XPathStringSource**</span></span>  
 <span data-ttu-id="14e5e-301">**XPathStringSourceType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-301">If **XPathStringSourceType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-302">**XPathStringSourceType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-302">If **XPathStringSourceType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-303">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-303">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-304">**XPathStringSourceType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-304">If **XPathStringSourceType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-305">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-305">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
 <span data-ttu-id="14e5e-306">XPath 문을 사용하여 원본 문서의 병합 위치를 식별하는 경우 이 문은 단일 노드를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-306">When you use an XPath statement to identify the merge location in the source document, this statement is expected to return a single node.</span></span> <span data-ttu-id="14e5e-307">여러 노드가 반환되는 경우에는 첫 번째 노드만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-307">If the statement returns multiple nodes, only the first node is used.</span></span> <span data-ttu-id="14e5e-308">두 번째 문서의 내용은 XPath 쿼리에서 반환하는 첫 번째 노드 아래에 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-308">The contents of the second document are merged under the first node that the XPath query returns.</span></span>  
  
 <span data-ttu-id="14e5e-309">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-309">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-310">XML 태스크가 병합 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-310">Specify whether the XML task saves the output of the Merge operation.</span></span>  
  
 <span data-ttu-id="14e5e-311">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-311">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-312">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-312">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-313">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-313">**Destination**</span></span>  
 <span data-ttu-id="14e5e-314">**DestinationType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-314">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-315">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-315">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-316">**DestinationType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-316">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-317">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-317">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-318">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-318">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-319">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-319">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-320">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-320">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-321">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-321">Value</span></span>|<span data-ttu-id="14e5e-322">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-322">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-323">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-323">**File connection**</span></span>|<span data-ttu-id="14e5e-324">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-324">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-325">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-325">**Variable**</span></span>|<span data-ttu-id="14e5e-326">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-326">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-327">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-327">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-328">두 번째 XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-328">Select the destination type of the second XML document.</span></span> <span data-ttu-id="14e5e-329">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-329">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-330">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-330">Value</span></span>|<span data-ttu-id="14e5e-331">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-331">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-332">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-332">**Direct input**</span></span>|<span data-ttu-id="14e5e-333">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-333">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-334">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-334">**File connection**</span></span>|<span data-ttu-id="14e5e-335">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-335">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-336">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-336">**Variable**</span></span>|<span data-ttu-id="14e5e-337">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-337">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-338">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-338">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-339">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-339">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-340">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-340">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-341">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-341">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-342">**SecondOperandType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-342">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-343">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-343">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--diff"></a><span data-ttu-id="14e5e-344">OperationType = Diff</span><span class="sxs-lookup"><span data-stu-id="14e5e-344">OperationType = Diff</span></span>  
 <span data-ttu-id="14e5e-345">비교 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-345">Specify options for the Diff operation.</span></span>  
  
 <span data-ttu-id="14e5e-346">**DiffAlgorithm**</span><span class="sxs-lookup"><span data-stu-id="14e5e-346">**DiffAlgorithm**</span></span>  
 <span data-ttu-id="14e5e-347">문서를 비교할 때 사용할 비교 알고리즘을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-347">Select the Diff algorithm to use when comparing documents.</span></span> <span data-ttu-id="14e5e-348">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-348">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-349">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-349">Value</span></span>|<span data-ttu-id="14e5e-350">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-350">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-351">**자동**</span><span class="sxs-lookup"><span data-stu-id="14e5e-351">**Auto**</span></span>|<span data-ttu-id="14e5e-352">XML 태스크에서 처리 속도가 빠른 알고리즘을 사용할 것인지 아니면 정확도가 높은 알고리즘을 사용할 것인지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-352">Let the XML task determine whether to use the fast or precise algorithm.</span></span>|  
|<span data-ttu-id="14e5e-353">**빠름**</span><span class="sxs-lookup"><span data-stu-id="14e5e-353">**Fast**</span></span>|<span data-ttu-id="14e5e-354">빠르지만 정확도가 떨어지는 비교 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-354">Use a fast, but less precise Diff algorithm.</span></span>|  
|<span data-ttu-id="14e5e-355">**정확**</span><span class="sxs-lookup"><span data-stu-id="14e5e-355">**Precise**</span></span>|<span data-ttu-id="14e5e-356">정확한 비교 알고리즘을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-356">Use a precise Diff algorithm.</span></span>|  
  
 <span data-ttu-id="14e5e-357">**DiffOptions**</span><span class="sxs-lookup"><span data-stu-id="14e5e-357">**Diff Options**</span></span>  
 <span data-ttu-id="14e5e-358">비교 작업에 적용할 비교 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-358">Set the Diff options to apply to the Diff operation.</span></span> <span data-ttu-id="14e5e-359">옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-359">The options are listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-360">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-360">Value</span></span>|<span data-ttu-id="14e5e-361">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-361">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-362">**IgnoreXMLDeclaration**</span><span class="sxs-lookup"><span data-stu-id="14e5e-362">**IgnoreXMLDeclaration**</span></span>|<span data-ttu-id="14e5e-363">XML 선언을 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-363">Specify whether to compare the XML declaration.</span></span>|  
|<span data-ttu-id="14e5e-364">**IgnoreDTD**</span><span class="sxs-lookup"><span data-stu-id="14e5e-364">**IgnoreDTD**</span></span>|<span data-ttu-id="14e5e-365">DTD(문서 유형 정의)를 무시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-365">Specify whether to ignore the document type definition (DTD).</span></span>|  
|<span data-ttu-id="14e5e-366">**IgnoreWhiteSpaces**</span><span class="sxs-lookup"><span data-stu-id="14e5e-366">**IgnoreWhite Spaces**</span></span>|<span data-ttu-id="14e5e-367">문서 비교 시 공백 양의 차이를 무시할 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-367">Specify whether to ignore differences in the amount of white space when comparing documents.</span></span>|  
|<span data-ttu-id="14e5e-368">**IgnoreNamespaces**</span><span class="sxs-lookup"><span data-stu-id="14e5e-368">**IgnoreNamespaces**</span></span>|<span data-ttu-id="14e5e-369">요소의 네임스페이스 URI(Uniform Resource Identifier)와 해당 요소의 특성 이름을 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-369">Specify whether to compare the namespace uniform resource identifier (URI) of an element and its attribute names.</span></span><br /><br /> <span data-ttu-id="14e5e-370">참고: 이 옵션을 `True`로 설정하는 경우 로컬 이름은 같지만 네임스페이스가 다른 두 요소를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-370">Note: If this option is set to `True`, two elements that have the same local name but different namespaces are considered identical.</span></span>|  
|<span data-ttu-id="14e5e-371">**IgnoreProcessingInstructions**</span><span class="sxs-lookup"><span data-stu-id="14e5e-371">**IgnoreProcessingInstructions**</span></span>|<span data-ttu-id="14e5e-372">처리 명령을 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-372">Specify whether to compare processing instructions.</span></span>|  
|<span data-ttu-id="14e5e-373">**IgnoreOrderOfChildElements**</span><span class="sxs-lookup"><span data-stu-id="14e5e-373">**IgnoreOrderOf ChildElements**</span></span>|<span data-ttu-id="14e5e-374">자식 요소의 순서를 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-374">Specify whether to compare the order of child elements.</span></span><br /><br /> <span data-ttu-id="14e5e-375">참고: 이 옵션을 `True`로 설정하는 경우 형제 목록에서의 위치만 다른 여러 자식 요소를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-375">Note: If this option is set to `True`, child elements that differ only in their position in a list of siblings are considered identical.</span></span>|  
|<span data-ttu-id="14e5e-376">**IgnoreComments**</span><span class="sxs-lookup"><span data-stu-id="14e5e-376">**IgnoreComments**</span></span>|<span data-ttu-id="14e5e-377">주석 노드를 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-377">Specify whether to compare comment nodes.</span></span>|  
|<span data-ttu-id="14e5e-378">**IgnorePrefixes**</span><span class="sxs-lookup"><span data-stu-id="14e5e-378">**IgnorePrefixes**</span></span>|<span data-ttu-id="14e5e-379">요소와 특성 이름의 접두사를 비교할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-379">Specify whether to compare prefixes of element and attribute names.</span></span><br /><br /> <span data-ttu-id="14e5e-380">참고: 이 옵션을 `True`로 설정하는 경우 로컬 이름은 같지만 네임스페이스 URI 및 접두사가 다른 두 요소를 동일한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-380">Note: If you set this option to `True`, two elements that have the same local name, but different namespace URIs and prefixes, are considered identical.</span></span>|  
  
 <span data-ttu-id="14e5e-381">**FailOnDifference**</span><span class="sxs-lookup"><span data-stu-id="14e5e-381">**FailOnDifference**</span></span>  
 <span data-ttu-id="14e5e-382">비교 작업이 실패할 경우 태스크가 실패할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-382">Specify whether the task fails if the Diff operation fails.</span></span>  
  
 <span data-ttu-id="14e5e-383">**SaveDiffGram**</span><span class="sxs-lookup"><span data-stu-id="14e5e-383">**SaveDiffGram**</span></span>  
 <span data-ttu-id="14e5e-384">비교 결과인 DiffGram 문서를 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-384">Specify whether to save the comparison result, a DiffGram document.</span></span>  
  
 <span data-ttu-id="14e5e-385">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-385">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-386">XML 태스크가 비교 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-386">Specify whether the XML task saves the output of the Diff operation.</span></span>  
  
 <span data-ttu-id="14e5e-387">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-387">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-388">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-388">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-389">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-389">**Destination**</span></span>  
 <span data-ttu-id="14e5e-390">**DestinationType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-390">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-391">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-391">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-392">**DestinationType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-392">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-393">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-393">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-394">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-394">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-395">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-395">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-396">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-396">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-397">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-397">Value</span></span>|<span data-ttu-id="14e5e-398">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-398">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-399">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-399">**File connection**</span></span>|<span data-ttu-id="14e5e-400">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-400">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-401">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-401">**Variable**</span></span>|<span data-ttu-id="14e5e-402">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-402">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-403">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-403">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-404">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-404">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-405">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-405">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-406">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-406">Value</span></span>|<span data-ttu-id="14e5e-407">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-407">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-408">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-408">**Direct input**</span></span>|<span data-ttu-id="14e5e-409">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-409">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-410">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-410">**File connection**</span></span>|<span data-ttu-id="14e5e-411">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-411">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-412">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-412">**Variable**</span></span>|<span data-ttu-id="14e5e-413">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-413">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-414">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-414">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-415">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-415">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-416">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-416">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-417">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-417">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-418">**SecondOperandType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-418">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-419">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-419">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
### <a name="operationtype--patch"></a><span data-ttu-id="14e5e-420">OperationType = Patch</span><span class="sxs-lookup"><span data-stu-id="14e5e-420">OperationType = Patch</span></span>  
 <span data-ttu-id="14e5e-421">패치 작업에 대한 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-421">Specify options for the Patch operation.</span></span>  
  
 <span data-ttu-id="14e5e-422">**SaveOperationResult**</span><span class="sxs-lookup"><span data-stu-id="14e5e-422">**SaveOperationResult**</span></span>  
 <span data-ttu-id="14e5e-423">XML 태스크가 패치 작업의 출력을 저장할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-423">Specify whether the XML task saves the output of the Patch operation.</span></span>  
  
 <span data-ttu-id="14e5e-424">**OverwriteDestination**</span><span class="sxs-lookup"><span data-stu-id="14e5e-424">**OverwriteDestination**</span></span>  
 <span data-ttu-id="14e5e-425">대상 파일 또는 변수를 덮어쓸지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-425">Specify whether to overwrite the destination file or variable.</span></span>  
  
 <span data-ttu-id="14e5e-426">**대상**</span><span class="sxs-lookup"><span data-stu-id="14e5e-426">**Destination**</span></span>  
 <span data-ttu-id="14e5e-427">**DestinationType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-427">If **DestinationType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-428">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-428">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-429">**DestinationType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-429">If **DestinationType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-430">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-430">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md).</span></span>  
  
 <span data-ttu-id="14e5e-431">**DestinationType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-431">**DestinationType**</span></span>  
 <span data-ttu-id="14e5e-432">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-432">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-433">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-433">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-434">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-434">Value</span></span>|<span data-ttu-id="14e5e-435">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-435">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-436">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-436">**File connection**</span></span>|<span data-ttu-id="14e5e-437">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-437">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-438">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-438">**Variable**</span></span>|<span data-ttu-id="14e5e-439">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-439">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-440">**SecondOperandType**</span><span class="sxs-lookup"><span data-stu-id="14e5e-440">**SecondOperandType**</span></span>  
 <span data-ttu-id="14e5e-441">XML 문서의 대상 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-441">Select the destination type of the XML document.</span></span> <span data-ttu-id="14e5e-442">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-442">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="14e5e-443">값</span><span class="sxs-lookup"><span data-stu-id="14e5e-443">Value</span></span>|<span data-ttu-id="14e5e-444">Description</span><span class="sxs-lookup"><span data-stu-id="14e5e-444">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14e5e-445">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="14e5e-445">**Direct input**</span></span>|<span data-ttu-id="14e5e-446">원본을 XML 문서로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-446">Set the source to an XML document.</span></span>|  
|<span data-ttu-id="14e5e-447">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="14e5e-447">**File connection**</span></span>|<span data-ttu-id="14e5e-448">XML 문서가 포함된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-448">Select a file that contains the XML document.</span></span>|  
|<span data-ttu-id="14e5e-449">**변수**</span><span class="sxs-lookup"><span data-stu-id="14e5e-449">**Variable**</span></span>|<span data-ttu-id="14e5e-450">원본을 XML 문서가 포함된 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-450">Set the source to a variable that contains the XML document.</span></span>|  
  
 <span data-ttu-id="14e5e-451">**SecondOperand**</span><span class="sxs-lookup"><span data-stu-id="14e5e-451">**SecondOperand**</span></span>  
 <span data-ttu-id="14e5e-452">**SecondOperandType**을 **직접 입력**으로 설정한 경우 XML 코드를 입력하거나 줄임표 단추 **(...)** 를 클릭하고 **문서 원본 편집기** 대화 상자를 사용하여 XML을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-452">If **SecondOperandType** is set to **Direct input**, provide the XML code or click the ellipsis button **(...)** and then provide the XML by using the **Document Source Editor** dialog box.</span></span>  
  
 <span data-ttu-id="14e5e-453">**SecondOperandType**을 **파일 연결**로 설정한 경우 파일 연결 관리자를 선택하거나 \<**New connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-453">If **SecondOperandType** is set to **File connection**, select a File connection manager, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="14e5e-454">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-454">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="14e5e-455">**SecondOperandType**을 **변수**로 설정한 경우 기존 변수를 선택하거나 \<**New variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14e5e-455">If **SecondOperandType** is set to **Variable**, select an existing variable, or click \<**New variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="14e5e-456">**관련 항목**: [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="14e5e-456">**Related Topics**: [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e5e-457">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14e5e-457">See Also</span></span>  
 <span data-ttu-id="14e5e-458">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="14e5e-458">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="14e5e-459">식 페이지</span><span class="sxs-lookup"><span data-stu-id="14e5e-459">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
