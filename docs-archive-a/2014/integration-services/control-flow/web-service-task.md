---
title: 웹 서비스 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a2f719a6fb0076a3bb286865199a9cf6a008d32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647795"
---
# <a name="web-service-task"></a><span data-ttu-id="b1428-102">웹 서비스 태스크</span><span class="sxs-lookup"><span data-stu-id="b1428-102">Web Service Task</span></span>
  <span data-ttu-id="b1428-103">웹 서비스 태스크는 웹 서비스 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-103">The Web Service task executes a Web service method.</span></span> <span data-ttu-id="b1428-104">웹 서비스 태스크는 다음 용도로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-104">You can use the Web Service task for the following purposes:</span></span>  
  
-   <span data-ttu-id="b1428-105">웹 서비스 메서드에서 반환되는 값을 변수에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-105">Writing to a variable the values that a Web service method returns.</span></span> <span data-ttu-id="b1428-106">예를 들어 웹 서비스 메서드로부터 그 날의 최고 기온을 가져온 다음 이 값을 사용하여 열 값을 설정하는 식에 사용된 변수를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-106">For example, you could obtain the highest temperature of the day from a Web service method, and then use that value to update a variable that is used in an expression that sets a column value.</span></span>  
  
-   <span data-ttu-id="b1428-107">웹 서비스 메서드에서 반환되는 값을 파일에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-107">Writing to a file the values that a Web service method returns.</span></span> <span data-ttu-id="b1428-108">예를 들어 잠재 고객 목록을 파일에 기록하고 패키지에서 이 파일을 데이터 원본으로 사용하여 데이터베이스에 파일을 기록하기 전에 데이터를 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-108">For example, a list of potential customers can be written to a file and the file then used as a data source in a package that cleans the data before it is written to a database.</span></span>  
  
## <a name="wsdl-file"></a><span data-ttu-id="b1428-109">WSDL 파일</span><span class="sxs-lookup"><span data-stu-id="b1428-109">WSDL File</span></span>  
 <span data-ttu-id="b1428-110">웹 서비스 태스크는 HTTP 연결 관리자를 사용하여 웹 서비스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-110">The Web Service task uses an HTTP connection manager to connect to the Web service.</span></span> <span data-ttu-id="b1428-111">HTTP 연결 관리자는 웹 서비스 태스크와 별도로 구성되고 태스크에서 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-111">The HTTP connection manager is configured separately from the Web Service task, and is referenced in the task.</span></span> <span data-ttu-id="b1428-112">HTTP 연결 관리자는 서버 URL과 같은 서버 프록시 설정, 웹 서비스 서버 액세스를 위한 자격 증명 및 제한 시간 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-112">The HTTP connection manager specifies the server proxy settings such as the server URL, credentials for accessing the Web services server, and time-out length.</span></span> <span data-ttu-id="b1428-113">자세한 내용은 [HTTP 연결 관리자](../connection-manager/http-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1428-113">For more information, see [HTTP Connection Manager](../connection-manager/http-connection-manager.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b1428-114">HTTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="b1428-114">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="b1428-115">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-115">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="b1428-116">HTTP 연결 관리자는 웹 사이트 또는 WSDL(Web Service Description Language) 파일로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-116">The HTTP connection manager can point to a Web site or to a Web Service Description Language (WSDL) file.</span></span> <span data-ttu-id="b1428-117">WSDL 파일로 연결하는 HTTP 연결 관리자의 URL에는 `?WSDL` 매개 변수가 포함됩니다(예: `http://MyServer/MyWebService/MyPage.asmx?WSDL`).</span><span class="sxs-lookup"><span data-stu-id="b1428-117">The URL of the HTTP connection manager that points to a WSDL file includes the `?WSDL` parameter: for example, `http://MyServer/MyWebService/MyPage.asmx?WSDL`.</span></span>  
  
 <span data-ttu-id="b1428-118">**디자이너에서 제공하는** 웹 서비스 태스크 편집기 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 대화 상자를 사용하여 웹 서비스 태스크를 구성하려면 WSDL 파일을 로컬에서 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-118">The WSDL file must be available locally to configure the Web Service task using the **Web Service Task Editor** dialog box that [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides.</span></span>  
  
-   <span data-ttu-id="b1428-119">HTTP 연결 관리자가 웹 사이트로 연결하는 경우 WSDL 파일을 로컬 컴퓨터로 수동으로 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-119">If the HTTP connection manager points to a Web site, the WSDL file must be copied manually to a local computer.</span></span>  
  
-   <span data-ttu-id="b1428-120">HTTP 연결 관리자가 WSDL 파일로 연결하는 경우 웹 서비스 태스크에서 웹 사이트의 파일을 로컬 파일로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-120">If the HTTP connection manager points to a WSDL file, the file can be downloaded from the Web site to a local file by the Web Service task.</span></span>  
  
 <span data-ttu-id="b1428-121">WSDL 파일에는 웹 서비스에서 제공하는 메서드, 메서드에 필요한 입력 매개 변수, 메서드가 반환하는 응답 및 웹 서비스와 통신하는 방법이 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-121">The WSDL file lists the methods that the Web service offers, the input parameters that the methods require, the responses that the methods return, and how to communicate with the Web service.</span></span>  
  
 <span data-ttu-id="b1428-122">메서드에서 입력 매개 변수가 사용되는 경우 웹 서비스 태스크에는 매개 변수 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-122">If the method uses input parameters, the Web Service task requires parameter values.</span></span> <span data-ttu-id="b1428-123">예를 들어 자신의 신장을 기준으로 구입할 스키의 길이를 보여 주는 웹 서비스 메서드에서는 입력 매개 변수로 자신의 신장을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-123">For example, a Web service method that recommends the length of skis you should purchase based on your height requires that your height be submitted in an input parameter.</span></span> <span data-ttu-id="b1428-124">매개 변수 값은 태스크 내에 정의된 문자열이나 태스크 또는 부모 컨테이너의 범위에 정의된 변수에서 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-124">The parameter values can be provided either by strings that are defined in the task, or by variables defined in the scope of the task or a parent container.</span></span> <span data-ttu-id="b1428-125">변수를 사용할 경우에는 패키지 구성 또는 스크립트를 사용하여 매개 변수 값을 동적으로 업데이트할 수 있는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-125">The advantage of using variables is that they let you dynamically update the parameter values by using package configurations or scripts.</span></span> <span data-ttu-id="b1428-126">자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md) 및 [패키지 구성](../package-configurations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1428-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) and [Package Configurations](../package-configurations.md).</span></span>  
  
 <span data-ttu-id="b1428-127">여러 웹 서비스 메서드에서는 입력 매개 변수가 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-127">Many Web service methods do not use input parameters.</span></span> <span data-ttu-id="b1428-128">예를 들어 현재 달에 태어난 대통령의 이름을 가져오는 웹 서비스 메서드의 경우에는 웹 서비스가 로컬에서 현재 달을 논리적으로 확인할 수 있기 때문에 입력 매개 변수가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-128">For example, a Web service method that gets the names of presidents who were born in the current month would not require an input parameter because the Web service can determine the current month locally.</span></span>  
  
 <span data-ttu-id="b1428-129">웹 서비스 메서드의 결과는 변수나 파일로 기록될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-129">The results of the Web service method can be written to a variable or to a file.</span></span> <span data-ttu-id="b1428-130">파일 연결 관리자를 사용하면 결과를 기록할 파일을 지정하거나 변수 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-130">You use the File connection manager either to specify the file or to provide the name of the variable to write the results to.</span></span> <span data-ttu-id="b1428-131">자세한 내용은 [파일 연결 관리자](../connection-manager/file-connection-manager.md) 및 [Integration Services&#40;SSIS&#41; 변수](../integration-services-ssis-variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1428-131">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a><span data-ttu-id="b1428-132">웹 서비스 태스크에 사용할 수 있는 사용자 지정 로깅 메시지</span><span class="sxs-lookup"><span data-stu-id="b1428-132">Custom Logging Messages Available on the Web Service Task</span></span>  
 <span data-ttu-id="b1428-133">다음 표에서는 웹 서비스 태스크에 사용할 수 있는 사용자 지정 로그 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-133">The following table lists the custom log entries that you can enable for the Web Service task.</span></span> <span data-ttu-id="b1428-134">자세한 내용은 [Integration Services&#40;SSIS&#41; 로깅](../performance/integration-services-ssis-logging.md) 및 [로깅할 메시지 사용자 지정](../custom-messages-for-logging.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1428-134">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="b1428-135">로그 항목</span><span class="sxs-lookup"><span data-stu-id="b1428-135">Log entry</span></span>|<span data-ttu-id="b1428-136">Description</span><span class="sxs-lookup"><span data-stu-id="b1428-136">Description</span></span>|  
|---------------|-----------------|  
|`WSTaskBegin`|<span data-ttu-id="b1428-137">태스크에서 웹 서비스 액세스를 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-137">The task began to access a Web service.</span></span>|  
|`WSTaskEnd`|<span data-ttu-id="b1428-138">태스크에서 웹 서비스 메서드를 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-138">The task completed a Web service method.</span></span>|  
|`WSTaskInfo`|<span data-ttu-id="b1428-139">태스크에 대한 설명 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-139">Descriptive information about the task.</span></span>|  
  
## <a name="configuration-of-the-web-service-task"></a><span data-ttu-id="b1428-140">웹 서비스 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="b1428-140">Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="b1428-141">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1428-141">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b1428-142">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1428-142">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b1428-143">웹 서비스 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1428-143">Web Service Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="b1428-144">웹 서비스 태스크 편집기&#40;입력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1428-144">Web Service Task Editor &#40;Input Page&#41;</span></span>](../web-service-task-editor-input-page.md)  
  
-   [<span data-ttu-id="b1428-145">웹 서비스 태스크 편집기&#40;출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1428-145">Web Service Task Editor &#40;Output Page&#41;</span></span>](../web-service-task-editor-output-page.md)  
  
-   [<span data-ttu-id="b1428-146">식 페이지</span><span class="sxs-lookup"><span data-stu-id="b1428-146">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="b1428-147">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1428-147">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="b1428-148">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="b1428-148">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a><span data-ttu-id="b1428-149">프로그래밍 방식으로 웹 서비스 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="b1428-149">Programmatic Configuration of the Web Service Task</span></span>  
 <span data-ttu-id="b1428-150">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1428-150">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a><span data-ttu-id="b1428-151">관련 내용</span><span class="sxs-lookup"><span data-stu-id="b1428-151">Related Content</span></span>  
 <span data-ttu-id="b1428-152">MSDN Library의 비디오 - [방법: 웹 서비스 태스크를 사용하여 웹 서비스 호출(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=259642)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1428-152">Video, [How to: Call a Web Service by Using the Web Service Task (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=259642), on technet.microsoft.com.</span></span>  
  
 <span data-ttu-id="b1428-153">[SSIS 패키지를 통해 웹 서비스를 사용 하는 방법](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/)</span><span class="sxs-lookup"><span data-stu-id="b1428-153">[How To Consume Web Service Through SSIS Package](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/).</span></span>  
  
  
