---
title: HTTP 연결 관리자 편집기 (서버 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2349766b11b28ff258496dc966d554d49c7657b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647120"
---
# <a name="http-connection-manager-editor-server-page"></a><span data-ttu-id="67487-102">HTTP 연결 관리자 편집기(서버 페이지)</span><span class="sxs-lookup"><span data-stu-id="67487-102">HTTP Connection Manager Editor (Server Page)</span></span>
  <span data-ttu-id="67487-103">**HTTP 연결 관리자 편집기** 대화 상자의 **서버** 탭에서 URL이나 보안 자격 증명 등의 속성을 지정하여 HTTP 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67487-103">Use the **Server** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager by specifying properties such as the URL and security credentials.</span></span> <span data-ttu-id="67487-104">HTTP 연결을 사용하면 패키지에서 HTTP를 통해 웹 서버에 액세스하고 파일을 보내거나 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67487-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="67487-105">HTTP 연결 관리자를 구성했으면 연결을 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67487-105">After configuring the HTTP Connection Manager, you can also test the connection.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="67487-106">HTTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="67487-106">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="67487-107">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67487-107">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="67487-108">HTTP 연결 관리자에 대한 자세한 내용은 [HTTP Connection Manager](connection-manager/http-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67487-108">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="67487-109">HTTP 연결 관리자의 일반적인 사용 시나리오에 대한 자세한 내용은 [Web Service Task](control-flow/web-service-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="67487-109">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="67487-110">옵션</span><span class="sxs-lookup"><span data-stu-id="67487-110">Options</span></span>  
 <span data-ttu-id="67487-111">**서버 URL**</span><span class="sxs-lookup"><span data-stu-id="67487-111">**Server URL**</span></span>  
 <span data-ttu-id="67487-112">서버의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-112">Type the URL for the server.</span></span>  
  
 <span data-ttu-id="67487-113">**웹 서비스 태스크 편집기** 의 **일반** 페이지에 있는 **WSDL 다운로드** 단추를 사용하여 WSDL 파일을 다운로드하려면 WSDL 파일의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-113">If you plan to use the **Download WSDL** button on the **General** page of the **Web Service Task Editor** to download a WSDL file, type the URL for the WSDL file.</span></span> <span data-ttu-id="67487-114">이 URL은 "?wsdl"로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="67487-114">This URL ends with "?wsdl".</span></span>  
  
 <span data-ttu-id="67487-115">**자격 증명 사용**</span><span class="sxs-lookup"><span data-stu-id="67487-115">**Use credentials**</span></span>  
 <span data-ttu-id="67487-116">HTTP 연결 관리자에서 사용자의 보안 자격 증명을 인증에 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-116">Specify whether you want the HTTP Connection Manager to use the user's security credentials for authentication.</span></span>  
  
 <span data-ttu-id="67487-117">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="67487-117">**User name**</span></span>  
 <span data-ttu-id="67487-118">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-118">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="67487-119">**암호**</span><span class="sxs-lookup"><span data-stu-id="67487-119">**Password**</span></span>  
 <span data-ttu-id="67487-120">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-120">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="67487-121">**도메인**</span><span class="sxs-lookup"><span data-stu-id="67487-121">**Domain**</span></span>  
 <span data-ttu-id="67487-122">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-122">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="67487-123">**클라이언트 인증서 사용**</span><span class="sxs-lookup"><span data-stu-id="67487-123">**Use client certificate**</span></span>  
 <span data-ttu-id="67487-124">HTTP 연결 관리자에서 클라이언트 인증서를 인증에 사용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-124">Specify whether you want the HTTP Connection Manager to use a client certificate for authentication.</span></span>  
  
 <span data-ttu-id="67487-125">**MSSQLSERVER에 대한 프로토콜 속성**</span><span class="sxs-lookup"><span data-stu-id="67487-125">**Certificate**</span></span>  
 <span data-ttu-id="67487-126">**인증서 선택** 대화 상자를 사용하여 목록에서 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-126">Select a certificate from the list by using the **Select Certificate** dialog box.</span></span> <span data-ttu-id="67487-127">입력란에 해당 인증서와 연결된 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="67487-127">The text box displays the name associated with this certificate.</span></span>  
  
 <span data-ttu-id="67487-128">**제한 시간(초)**</span><span class="sxs-lookup"><span data-stu-id="67487-128">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="67487-129">웹 서버에 연결하기 위한 제한 시간을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-129">Provide a time-out for connecting to the Web server.</span></span> <span data-ttu-id="67487-130">이 속성의 기본값은 30초입니다.</span><span class="sxs-lookup"><span data-stu-id="67487-130">The default value of this property is 30 seconds.</span></span>  
  
 <span data-ttu-id="67487-131">**청크 크기(KB)**</span><span class="sxs-lookup"><span data-stu-id="67487-131">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="67487-132">데이터를 쓰기 위한 청크 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-132">Provide a chunk size for writing data.</span></span>  
  
 <span data-ttu-id="67487-133">**연결 테스트**</span><span class="sxs-lookup"><span data-stu-id="67487-133">**Test Connection**</span></span>  
 <span data-ttu-id="67487-134">HTTP 연결 관리자를 구성했으면 **연결 테스트**를 클릭하여 연결이 실행 가능한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="67487-134">After configuring the HTTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67487-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67487-135">See Also</span></span>  
 <span data-ttu-id="67487-136">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="67487-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="67487-137">HTTP 연결 관리자 편집기&#40;프록시 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="67487-137">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)  
  
  
