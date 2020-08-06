---
title: Analysis Services DDL 실행 태스크 편집기 (DDL 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d207afe666e582c44f1014a6c80f4f4984fd5410
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648519"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a><span data-ttu-id="ee69f-102">Analysis Services DDL 실행 태스크 편집기(DDL 페이지)</span><span class="sxs-lookup"><span data-stu-id="ee69f-102">Analysis Services Execute DDL Task Editor (DDL Page)</span></span>
  <span data-ttu-id="ee69f-103">**Analysis Services DDL 실행 태스크 편집기** 대화 상자의 **DDL** 페이지를 사용하여 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트 또는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 데이터베이스에 대한 연결을 지정하고 DDL(데이터 정의 언어) 문의 원본에 대한 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-103">Use the **DDL** page of the **Analysis Services Execute DDL Task Editor** dialog box to specify a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database and to provide information about the source of data definition language (DDL) statements.</span></span>  
  
 <span data-ttu-id="ee69f-104">이 태스크에 대한 자세한 내용은 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee69f-104">To learn about this task, see [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="ee69f-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="ee69f-105">Static Options</span></span>  
 <span data-ttu-id="ee69f-106">**연결**</span><span class="sxs-lookup"><span data-stu-id="ee69f-106">**Connection**</span></span>  
 <span data-ttu-id="ee69f-107">목록에서 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 프로젝트 또는 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 연결 관리자를 선택하거나 \<**New connection...**>을 클릭한 다음, **Analysis Services 연결 관리자 추가** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-107">Select an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project or an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] connection manager in the list, or click \<**New connection...**> and use the **Add Analysis Services Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="ee69f-108">**관련 항목:** [Analysis Services 연결 관리자 추가 대화 상자 UI 참조](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services 연결 관리자](connection-manager/analysis-services-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="ee69f-108">**Related Topics:** [Add Analysis Services Connection Manager Dialog Box UI Reference](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services Connection Manager](connection-manager/analysis-services-connection-manager.md)</span></span>  
  
 <span data-ttu-id="ee69f-109">**SourceType**</span><span class="sxs-lookup"><span data-stu-id="ee69f-109">**SourceType**</span></span>  
 <span data-ttu-id="ee69f-110">DDL 문의 원본 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-110">Specify the source type of the DDL statements.</span></span> <span data-ttu-id="ee69f-111">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-111">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="ee69f-112">값</span><span class="sxs-lookup"><span data-stu-id="ee69f-112">Value</span></span>|<span data-ttu-id="ee69f-113">Description</span><span class="sxs-lookup"><span data-stu-id="ee69f-113">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee69f-114">**직접 입력**</span><span class="sxs-lookup"><span data-stu-id="ee69f-114">**Direct Input**</span></span>|<span data-ttu-id="ee69f-115">원본을 **SourceDirect** 입력란에 저장된 DDL 문으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-115">Set the source to the DDL statement stored in the **SourceDirect** text box.</span></span> <span data-ttu-id="ee69f-116">이 값을 선택하면 다음 섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-116">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="ee69f-117">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="ee69f-117">**File Connection**</span></span>|<span data-ttu-id="ee69f-118">원본을 DDL 문이 포함된 파일로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-118">Set the source to a file that contains the DDL statement.</span></span> <span data-ttu-id="ee69f-119">이 값을 선택하면 다음 섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-119">Selecting this value displays the dynamic options in the following section.</span></span>|  
|<span data-ttu-id="ee69f-120">**변수**</span><span class="sxs-lookup"><span data-stu-id="ee69f-120">**Variable**</span></span>|<span data-ttu-id="ee69f-121">원본을 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-121">Set the source to a variable.</span></span> <span data-ttu-id="ee69f-122">이 값을 선택하면 다음 섹션에 동적 옵션이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-122">Selecting this value displays the dynamic options in the following section.</span></span>|  
  
## <a name="dynamic-options"></a><span data-ttu-id="ee69f-123">동적 옵션</span><span class="sxs-lookup"><span data-stu-id="ee69f-123">Dynamic Options</span></span>  
  
### <a name="sourcetype--direct-input"></a><span data-ttu-id="ee69f-124">SourceType = 직접 입력</span><span class="sxs-lookup"><span data-stu-id="ee69f-124">SourceType = Direct Input</span></span>  
 <span data-ttu-id="ee69f-125">**원본**</span><span class="sxs-lookup"><span data-stu-id="ee69f-125">**Source**</span></span>  
 <span data-ttu-id="ee69f-126">DDL 문을 입력하거나 줄임표 **(...)** 를 클릭한 다음, **DDL 문** 대화 상자에 명령문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-126">Type the DDL statements or click the ellipsis **(...)** and then type the statements in the **DDL Statements** dialog box.</span></span>  
  
### <a name="sourcetype--file-connection"></a><span data-ttu-id="ee69f-127">SourceType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="ee69f-127">SourceType = File Connection</span></span>  
 <span data-ttu-id="ee69f-128">**원본**</span><span class="sxs-lookup"><span data-stu-id="ee69f-128">**Source**</span></span>  
 <span data-ttu-id="ee69f-129">목록에서 파일 연결을 선택하거나 \<**New connection...**>을 클릭한 다음, **파일 연결 관리자** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-129">Select a File connection in the list, or click \<**New connection...**> and use the **File Connection Manager** dialog box to create a new connection.</span></span>  
  
 <span data-ttu-id="ee69f-130">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="ee69f-130">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
### <a name="sourcetype--variable"></a><span data-ttu-id="ee69f-131">SourceType = 변수</span><span class="sxs-lookup"><span data-stu-id="ee69f-131">SourceType = Variable</span></span>  
 <span data-ttu-id="ee69f-132">**원본**</span><span class="sxs-lookup"><span data-stu-id="ee69f-132">**Source**</span></span>  
 <span data-ttu-id="ee69f-133">목록에서 변수를 선택하거나 \<**New variable...**>를 클릭한 다음, **변수 추가** 대화 상자를 사용하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee69f-133">Select a variable in the list, or click \<**New variable...**> and use the **Add Variable** dialog box to create a new variable.</span></span>  
  
 <span data-ttu-id="ee69f-134">**관련 항목:** [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)</span><span class="sxs-lookup"><span data-stu-id="ee69f-134">**Related Topics:** [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee69f-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee69f-135">See Also</span></span>  
 <span data-ttu-id="ee69f-136">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ee69f-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ee69f-137">[Analysis Services DDL 실행 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ee69f-137">[Analysis Services Execute DDL Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="ee69f-138">[식 페이지](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="ee69f-138">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="ee69f-139">[제어 흐름](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ee69f-139">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="ee69f-140">[Analysis Services 스크립팅 언어 &#40;,&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span><span class="sxs-lookup"><span data-stu-id="ee69f-140">[Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span></span>  
 [<span data-ttu-id="ee69f-141">XMLA&#40;XML for Analysis&#41; 참조</span><span class="sxs-lookup"><span data-stu-id="ee69f-141">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
