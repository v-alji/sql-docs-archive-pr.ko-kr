---
title: 스크립트 태스크 예제 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], examples
- examples [Integration Services]
- SSIS Script task, examples
ms.assetid: b0dd77ee-ee11-4cd9-87aa-61dd67f2fe1c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 920d2ee5cc2e64db1048d10522d9be644794e55b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732735"
---
# <a name="script-task-examples"></a><span data-ttu-id="81c40-102">스크립트 태스크 예</span><span class="sxs-lookup"><span data-stu-id="81c40-102">Script Task Examples</span></span>
  <span data-ttu-id="81c40-103">스크립트 태스크는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 태스크가 충족시키지 않는 거의 모든 요구 사항을 충족시키기 위해 패키지에서 사용할 수 있는 다용도 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-103">The Script task is a multi-purpose tool that you can use in a package to fill almost any requirement that is not met by the tasks included with [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="81c40-104">이 항목에는 사용 가능한 기능 중 몇 가지를 보여 주는 스크립트 태스크 코드 예제가 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-104">This topic lists Script task code samples that demonstrate some of the available functionality.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="81c40-105">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="81c40-105">If you want to create tasks that you can more easily reuse across multiple packages, consider using the code in these Script task samples as the starting point for custom tasks.</span></span> <span data-ttu-id="81c40-106">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81c40-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81c40-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="81c40-107">In This Section</span></span>  
  
### <a name="example-topics"></a><span data-ttu-id="81c40-108">예 항목</span><span class="sxs-lookup"><span data-stu-id="81c40-108">Example Topics</span></span>  
 <span data-ttu-id="81c40-109">이 섹션에는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 스크립트 태스크에 통합할 수 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 클래스의 다양한 용도를 보여 주는 코드 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-109">This section contains code examples that demonstrate various uses of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes that you can incorporate into an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Script task:</span></span>  
  
 [<span data-ttu-id="81c40-110">스크립트 태스크를 사용하여 빈 플랫 파일 검색</span><span class="sxs-lookup"><span data-stu-id="81c40-110">Detecting an Empty Flat File with the Script Task</span></span>](../extending-packages-scripting-task-examples/detecting-an-empty-flat-file-with-the-script-task.md)  
 <span data-ttu-id="81c40-111">플랫 파일을 검사하여 플랫 파일에 데이터 행이 들어 있는지 확인하고 결과를 제어 흐름 분기에 사용할 수 있도록 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-111">Checks a flat file to determine whether it contains rows of data, and saves the result to a variable for use in control flow branching.</span></span>  
  
 [<span data-ttu-id="81c40-112">스크립트 태스크를 사용하여 ForEach 루프에 사용할 목록 수집</span><span class="sxs-lookup"><span data-stu-id="81c40-112">Gathering a List for the ForEach Loop with the Script Task</span></span>](../extending-packages-scripting-task-examples/gathering-a-list-for-the-foreach-loop-with-the-script-task.md)  
 <span data-ttu-id="81c40-113">사용자가 지정한 조건을 만족하는 파일 목록을 수집하고 나중에 Foreach from Variable 열거자에서 사용할 수 있도록 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-113">Gathers a list of files that meet user-specified criteria, and populates a variable for later use by the Foreach from Variable Enumerator.</span></span>  
  
 [<span data-ttu-id="81c40-114">스크립트 태스크를 사용하여 Active Directory 쿼리</span><span class="sxs-lookup"><span data-stu-id="81c40-114">Querying the Active Directory with the Script Task</span></span>](../extending-packages-scripting-task-examples/querying-the-active-directory-with-the-script-task.md)  
 <span data-ttu-id="81c40-115">System.DirectoryServices 네임스페이스의 클래스를 사용하여 Active Directory에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 변수 값을 기준으로 사용자 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-115">Retrieves user information from Active Directory based on the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, by using classes in the System.DirectoryServices namespace.</span></span>  
  
 [<span data-ttu-id="81c40-116">스크립트 태스크를 사용하여 성능 카운터 모니터링</span><span class="sxs-lookup"><span data-stu-id="81c40-116">Monitoring Performance Counters with the Script Task</span></span>](../extending-packages-scripting-task-examples/monitoring-performance-counters-with-the-script-task.md)  
 <span data-ttu-id="81c40-117">System.Diagnostics 네임스페이스의 클래스를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 실행 진행률을 추적하는 데 사용할 수 있는 사용자 지정 성능 카운터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-117">Creates a custom performance counter that can be used to track the execution progress of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package, by using classes in the System.Diagnostics namespace.</span></span>  
  
 [<span data-ttu-id="81c40-118">스크립트 태스크를 사용한 이미지 작업</span><span class="sxs-lookup"><span data-stu-id="81c40-118">Working with Images with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)  
 <span data-ttu-id="81c40-119">System.Drawing 네임스페이스의 클래스를 사용하여 이미지를 JPEG 형식으로 압축하고 이 이미지에서 썸네일 이미지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-119">Compresses images into the JPEG format and creates thumbnail images from them, by using classes in the System.Drawing namespace.</span></span>  
  
 [<span data-ttu-id="81c40-120">스크립트 태스크를 사용하여 설치된 프린터 찾기</span><span class="sxs-lookup"><span data-stu-id="81c40-120">Finding Installed Printers with the Script Task</span></span>](../extending-packages-scripting-task-examples/finding-installed-printers-with-the-script-task.md)  
 <span data-ttu-id="81c40-121">System.Drawing.Printing 네임스페이스의 클래스를 사용하여 설치된 프린터 중 특정 용지 크기를 지원하는 프린터를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-121">Locates installed printers that support a specific paper size, by using classes in the System.Drawing.Printing namespace.</span></span>  
  
 [<span data-ttu-id="81c40-122">스크립트 태스크를 사용하여 HTML 메일 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="81c40-122">Sending an HTML Mail Message with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-an-html-mail-message-with-the-script-task.md)  
 <span data-ttu-id="81c40-123">전자 메일 메시지를 일반 텍스트 형식 대신 HTML 형식으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-123">Sends a mail message in HTML format instead of plain text format.</span></span>  
  
 [<span data-ttu-id="81c40-124">스크립트 태스크를 사용한 Excel 파일 작업</span><span class="sxs-lookup"><span data-stu-id="81c40-124">Working with Excel Files with the Script Task</span></span>](../extending-packages-scripting-task-examples/working-with-excel-files-with-the-script-task.md)  
 <span data-ttu-id="81c40-125">Excel 파일의 워크시트를 나열하고 특정 워크시트가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-125">Lists the worksheets in an Excel file and checks for the existence of a specific worksheet.</span></span>  
  
 [<span data-ttu-id="81c40-126">스크립트 태스크를 사용하여 원격 프라이빗 메시지 큐에 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="81c40-126">Sending to a Remote Private Message Queue with the Script Task</span></span>](../extending-packages-scripting-task-examples/sending-to-a-remote-private-message-queue-with-the-script-task.md)  
 <span data-ttu-id="81c40-127">메시지를 원격 프라이빗 메시지 큐로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-127">Sends a message to a remote private message queue.</span></span>  
  
### <a name="other-examples"></a><span data-ttu-id="81c40-128">기타 예</span><span class="sxs-lookup"><span data-stu-id="81c40-128">Other Examples</span></span>  
 <span data-ttu-id="81c40-129">다음 항목에도 스크립트 태스크에 사용할 수 있는 코드 예가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-129">The following topics also contain code examples for use with the Script task:</span></span>  
  
 [<span data-ttu-id="81c40-130">스크립트 태스크에서 변수 사용</span><span class="sxs-lookup"><span data-stu-id="81c40-130">Using Variables in the Script Task</span></span>](../extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 <span data-ttu-id="81c40-131">다른 변수에 지정된 제한을 초과하는 패키지 변수의 값에 따라 패키지를 계속 실행할지 여부를 사용자가 확인할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-131">Asks the user for confirmation of whether the package should continue to run, based on the value of a package variable that may exceed the limit specified in another variable.</span></span>  
  
 [<span data-ttu-id="81c40-132">스크립트 태스크에서 데이터 원본에 연결</span><span class="sxs-lookup"><span data-stu-id="81c40-132">Connecting to Data Sources in the Script Task</span></span>](../extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 <span data-ttu-id="81c40-133">패키지에 정의된 연결 관리자에서 연결 또는 연결 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-133">Retrieves a connection or connection information from connection managers defined in the package.</span></span>  
  
 [<span data-ttu-id="81c40-134">스크립트 태스크에서 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="81c40-134">Raising Events in the Script Task</span></span>](../extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 <span data-ttu-id="81c40-135">서버의 인터넷 연결 상태에 따라 오류, 경고 또는 정보 메시지를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-135">Raises an error, a warning, or an informational message based on the status of the Internet connection on the server.</span></span>  
  
 [<span data-ttu-id="81c40-136">스크립트 태스크에서 로깅</span><span class="sxs-lookup"><span data-stu-id="81c40-136">Logging in the Script Task</span></span>](../extending-packages-scripting/task/logging-in-the-script-task.md)  
 <span data-ttu-id="81c40-137">태스크에서 처리한 항목 수를 설정된 로그 공급자에 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="81c40-137">Logs the number of items processed by the task to enabled log providers.</span></span>  
  
<span data-ttu-id="81c40-138">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="81c40-138">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="81c40-139">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81c40-139">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="81c40-140">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="81c40-140">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="81c40-141">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="81c40-141">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
