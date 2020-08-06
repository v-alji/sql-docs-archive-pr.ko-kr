---
title: 웹 서비스 태스크 편집기 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dbacf2a2a867ab01039678ff4f43eebac839c11a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660035"
---
# <a name="web-service-task-editor-general-page"></a><span data-ttu-id="d62ad-102">웹 서비스 태스크 편집기(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="d62ad-102">Web Service Task Editor (General Page)</span></span>
  <span data-ttu-id="d62ad-103">**웹 서비스 태스크 편집기** 대화 상자의 **일반** 페이지를 사용하여 HTTP 연결 관리자를 지정하고, 웹 서비스 태스크에 사용하는 WSDL(웹 서비스 기술 언어) 파일의 위치를 지정하고, 웹 서비스 태스크를 설명하고, WSDL 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-103">Use the **General** page of the **Web Services Task Editor** dialog box to specify an HTTP connection manager, specify the location of the Web Services Description Language (WSDL) file the Web Service task uses, describe the Web Services task, and download the WSDL file.</span></span>  
  
 <span data-ttu-id="d62ad-104">이 태스크에 대한 자세한 내용은 [웹 서비스 태스크](control-flow/web-service-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d62ad-104">For more information about this task, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d62ad-105">옵션</span><span class="sxs-lookup"><span data-stu-id="d62ad-105">Options</span></span>  
 <span data-ttu-id="d62ad-106">**HTTPConnection**</span><span class="sxs-lookup"><span data-stu-id="d62ad-106">**HTTPConnection**</span></span>  
 <span data-ttu-id="d62ad-107">목록에서 연결 관리자를 선택하거나 \<**New connection...**>를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-107">Select a connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d62ad-108">HTTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="d62ad-108">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="d62ad-109">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-109">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="d62ad-110">**관련 항목:**  [HTTP 연결 관리자](connection-manager/http-connection-manager.md), [HTTP 연결 관리자 편집기&#40;서버 페이지&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="d62ad-110">**Related Topics:**  [HTTP Connection Manager](connection-manager/http-connection-manager.md), [HTTP Connection Manager Editor &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span></span>  
  
 <span data-ttu-id="d62ad-111">**WSDLFile**</span><span class="sxs-lookup"><span data-stu-id="d62ad-111">**WSDLFile**</span></span>  
 <span data-ttu-id="d62ad-112">컴퓨터에 로컬인 WSDL 파일의 정규화된 경로를 입력하거나 찾아보기 단추 **(...)** 를 클릭하여 이 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-112">Type the fully qualified path of a WSDL file that is local to the computer, or click the browse button **(...)** and locate this file.</span></span>  
  
 <span data-ttu-id="d62ad-113">WSDL 파일을 컴퓨터에 이미 수동으로 다운로드한 경우에는 이 파일을 선택하고,</span><span class="sxs-lookup"><span data-stu-id="d62ad-113">If you have already manually downloaded the WSDL file to the computer, select this file.</span></span> <span data-ttu-id="d62ad-114">WSDL 파일을 아직 다운로드하지 않은 경우에는 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-114">However, if the WSDL file has not yet been downloaded, follow these steps:</span></span>  
  
-   <span data-ttu-id="d62ad-115">파일 이름 확장명이 ".wsdl"인 빈 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-115">Create an empty file that has the ".wsdl" file name extension.</span></span>  
  
-   <span data-ttu-id="d62ad-116">**WSDLFile** 옵션으로 이 빈 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-116">Select this empty file for the **WSDLFile** option.</span></span>  
  
-   <span data-ttu-id="d62ad-117">**OverwriteWSDLFile** 의 값을로 설정 `True` 하 여 빈 파일을 실제 WSDL 파일로 덮어쓸 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-117">Set the value of **OverwriteWSDLFile** to `True` to enable the empty file to be overwritten with the actual WSDL file.</span></span>  
  
-   <span data-ttu-id="d62ad-118">**WSDL 다운로드** 를 클릭하여 실제 WSDL 파일을 다운로드하고 빈 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-118">Click **Download WSDL** to download the actual WSDL file and overwrite the empty file.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d62ad-119">**WSDL 다운로드** 옵션은 **WSDLFile** 상자에 기존 로컬 파일의 이름을 입력할 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-119">The **Download WSDL** option is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
 <span data-ttu-id="d62ad-120">**OverwriteWSDLFile**</span><span class="sxs-lookup"><span data-stu-id="d62ad-120">**OverwriteWSDLFile**</span></span>  
 <span data-ttu-id="d62ad-121">웹 서비스 태스크에 대한 WSDL 파일을 덮어쓸지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-121">Indicate whether the WSDL file for the Web Service task can be overwritten.</span></span>  
  
 <span data-ttu-id="d62ad-122">**Wsdl 다운로드** 단추를 사용 하 여 wsdl 파일을 다운로드 하려는 경우이 값을로 설정 `True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-122">If you intend to download the WSDL file by using the **Download WSDL** button, set this value to `True`.</span></span>  
  
 <span data-ttu-id="d62ad-123">**이름**</span><span class="sxs-lookup"><span data-stu-id="d62ad-123">**Name**</span></span>  
 <span data-ttu-id="d62ad-124">웹 서비스 태스크에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-124">Provide a unique name for the Web Service task.</span></span> <span data-ttu-id="d62ad-125">이 이름은 태스크 아이콘에서 레이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-125">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d62ad-126">태스크 이름은 패키지 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-126">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="d62ad-127">**설명**</span><span class="sxs-lookup"><span data-stu-id="d62ad-127">**Description**</span></span>  
 <span data-ttu-id="d62ad-128">웹 서비스 태스크에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-128">Type a description of the Web Service task.</span></span>  
  
 <span data-ttu-id="d62ad-129">**WSDL 다운로드**</span><span class="sxs-lookup"><span data-stu-id="d62ad-129">**Download WSDL**</span></span>  
 <span data-ttu-id="d62ad-130">WSDL 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-130">Download the WSDL file.</span></span>  
  
 <span data-ttu-id="d62ad-131">이 단추는 **WSDLFile** 상자에 기존 로컬 파일의 이름을 입력할 때까지 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d62ad-131">This button is not enabled until you provide the name of an existing local file in the **WSDLFile** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62ad-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d62ad-132">See Also</span></span>  
 <span data-ttu-id="d62ad-133">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d62ad-133">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="d62ad-134">[웹 서비스 태스크 편집기 &#40;입력 페이지&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span><span class="sxs-lookup"><span data-stu-id="d62ad-134">[Web Service Task Editor &#40;Input Page&#41;](../../2014/integration-services/web-service-task-editor-input-page.md) </span></span>  
 <span data-ttu-id="d62ad-135">[웹 서비스 태스크 편집기 &#40;출력 페이지&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="d62ad-135">[Web Service Task Editor &#40;Output Page&#41;](../../2014/integration-services/web-service-task-editor-output-page.md) </span></span>  
 [<span data-ttu-id="d62ad-136">식 페이지</span><span class="sxs-lookup"><span data-stu-id="d62ad-136">Expressions Page</span></span>](expressions/expressions-page.md)  
  
  
