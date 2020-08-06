---
title: 웹 서비스 태스크 편집기 (출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ad034ae78a096ebe5998ac2c3d2573fe7c3bfd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660030"
---
# <a name="web-service-task-editor-output-page"></a><span data-ttu-id="f39d2-102">웹 서비스 태스크 편집기(출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="f39d2-102">Web Service Task Editor (Output Page)</span></span>
  <span data-ttu-id="f39d2-103">**웹 서비스 태스크 편집기** 대화 상자의 **출력** 페이지를 사용하여 웹 메서드에서 반환하는 결과를 저장할 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-103">Use the **Output** page of the **Web Service Task Editor** dialog box to specify where to store the result returned by the Web method.</span></span>  
  
 <span data-ttu-id="f39d2-104">이 태스크에 대한 자세한 내용은 [웹 서비스 태스크](control-flow/web-service-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f39d2-104">To learn about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="f39d2-105">정적 옵션</span><span class="sxs-lookup"><span data-stu-id="f39d2-105">Static Options</span></span>  
 <span data-ttu-id="f39d2-106">**OutputType**</span><span class="sxs-lookup"><span data-stu-id="f39d2-106">**OutputType**</span></span>  
 <span data-ttu-id="f39d2-107">결과를 저장할 때 사용할 스토리지 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-107">Select the storage type to use when storing the results.</span></span> <span data-ttu-id="f39d2-108">이 속성의 옵션은 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-108">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="f39d2-109">값</span><span class="sxs-lookup"><span data-stu-id="f39d2-109">Value</span></span>|<span data-ttu-id="f39d2-110">Description</span><span class="sxs-lookup"><span data-stu-id="f39d2-110">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f39d2-111">**파일 연결**</span><span class="sxs-lookup"><span data-stu-id="f39d2-111">**File Connection**</span></span>|<span data-ttu-id="f39d2-112">결과를 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-112">Store the results in a file.</span></span> <span data-ttu-id="f39d2-113">이 값을 선택하면 동적 옵션 **File**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-113">Selecting this value displays the dynamic option, **File**.</span></span>|  
|<span data-ttu-id="f39d2-114">**변수**</span><span class="sxs-lookup"><span data-stu-id="f39d2-114">**Variable**</span></span>|<span data-ttu-id="f39d2-115">결과를 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-115">Store the results in a variable.</span></span> <span data-ttu-id="f39d2-116">이 값을 선택하면 동적 옵션 **Variable**이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-116">Selecting this value displays the dynamic option, **Variable**.</span></span>|  
  
## <a name="outputtype-dynamic-options"></a><span data-ttu-id="f39d2-117">OutputType 동적 옵션</span><span class="sxs-lookup"><span data-stu-id="f39d2-117">OutputType Dynamic Options</span></span>  
  
### <a name="outputtype--file-connection"></a><span data-ttu-id="f39d2-118">OutputType = 파일 연결</span><span class="sxs-lookup"><span data-stu-id="f39d2-118">OutputType = File Connection</span></span>  
 <span data-ttu-id="f39d2-119">**최근에 사용한 파일**</span><span class="sxs-lookup"><span data-stu-id="f39d2-119">**File**</span></span>  
 <span data-ttu-id="f39d2-120">목록에서 파일 연결 관리자를 선택하거나 \<**New Connection...**>을 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-120">Select a File connection manager in the list or click \<**New Connection...**> to create a new connection manager.</span></span>  
  
 <span data-ttu-id="f39d2-121">**관련 항목:** [파일 연결 관리자](connection-manager/file-connection-manager.md), [파일 연결 관리자 편집기](../../2014/integration-services/file-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="f39d2-121">**Related Topics:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)</span></span>  
  
### <a name="outputtype--variable"></a><span data-ttu-id="f39d2-122">OutputType = 변수</span><span class="sxs-lookup"><span data-stu-id="f39d2-122">OutputType = Variable</span></span>  
 <span data-ttu-id="f39d2-123">**변수**</span><span class="sxs-lookup"><span data-stu-id="f39d2-123">**Variable**</span></span>  
 <span data-ttu-id="f39d2-124">목록에서 변수를 선택하거나 \<**New Variable...**>를 클릭하여 새 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f39d2-124">Select a variable in the list or click \<**New Variable...**> to create a new variable.</span></span>  
  
 <span data-ttu-id="f39d2-125">**관련 항목:**  [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md), [변수 추가](../../2014/integration-services/add-variable.md)</span><span class="sxs-lookup"><span data-stu-id="f39d2-125">**Related Topics:**  [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md), [Add Variable](../../2014/integration-services/add-variable.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f39d2-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f39d2-126">See Also</span></span>  
 <span data-ttu-id="f39d2-127">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="f39d2-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="f39d2-128">[웹 서비스 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="f39d2-128">[Web Service Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="f39d2-129">[웹 서비스 태스크 편집기 &#40;입력 페이지&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="f39d2-129">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 [<span data-ttu-id="f39d2-130">식 페이지</span><span class="sxs-lookup"><span data-stu-id="f39d2-130">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
