---
title: HTTP 연결 관리자 편집기 (프록시 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8269dbbeb226ffa3f56c226e1a416d99c1e3f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647125"
---
# <a name="http-connection-manager-editor-proxy-page"></a><span data-ttu-id="d8946-102">HTTP 연결 관리자 편집기(프록시 페이지)</span><span class="sxs-lookup"><span data-stu-id="d8946-102">HTTP Connection Manager Editor (Proxy Page)</span></span>
  <span data-ttu-id="d8946-103">**HTTP 연결 관리자 편집기** 대화 상자의 **프록시** 탭을 사용하여 프록시 서버를 사용하도록 HTTP 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-103">Use the **Proxy** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager to use a proxy server.</span></span> <span data-ttu-id="d8946-104">HTTP 연결을 사용하면 패키지에서 HTTP를 통해 웹 서버에 액세스하고 파일을 보내거나 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span>  
  
 <span data-ttu-id="d8946-105">HTTP 연결 관리자에 대한 자세한 내용은 [HTTP Connection Manager](connection-manager/http-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8946-105">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="d8946-106">HTTP 연결 관리자의 일반적인 사용 시나리오에 대한 자세한 내용은 [Web Service Task](control-flow/web-service-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d8946-106">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d8946-107">옵션</span><span class="sxs-lookup"><span data-stu-id="d8946-107">Options</span></span>  
 <span data-ttu-id="d8946-108">**프록시 사용**</span><span class="sxs-lookup"><span data-stu-id="d8946-108">**Use proxy**</span></span>  
 <span data-ttu-id="d8946-109">HTTP 연결 관리자에서 프록시 서버를 통해 연결하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-109">Specify whether you want the HTTP Connection Manager to connect through a proxy server.</span></span>  
  
 <span data-ttu-id="d8946-110">**프록시 URL**</span><span class="sxs-lookup"><span data-stu-id="d8946-110">**Proxy URL**</span></span>  
 <span data-ttu-id="d8946-111">프록시 서버의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-111">Type the URL for the proxy server.</span></span>  
  
 <span data-ttu-id="d8946-112">**로컬에서 프록시 사용 안 함**</span><span class="sxs-lookup"><span data-stu-id="d8946-112">**Bypass proxy on local**</span></span>  
 <span data-ttu-id="d8946-113">HTTP 연결 관리자에서 로컬 주소에 대해 프록시 서버를 사용하지 않도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-113">Specify whether you want the HTTP Connection Manager to bypass the proxy server for local addresses.</span></span>  
  
 <span data-ttu-id="d8946-114">**자격 증명 사용**</span><span class="sxs-lookup"><span data-stu-id="d8946-114">**Use credentials**</span></span>  
 <span data-ttu-id="d8946-115">HTTP 연결 관리자에서 프록시 서버에 보안 자격 증명을 사용하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-115">Specify whether you want the HTTP Connection Manager to use security credentials for the proxy server.</span></span>  
  
 <span data-ttu-id="d8946-116">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="d8946-116">**User name**</span></span>  
 <span data-ttu-id="d8946-117">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-117">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="d8946-118">**암호**</span><span class="sxs-lookup"><span data-stu-id="d8946-118">**Password**</span></span>  
 <span data-ttu-id="d8946-119">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-119">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="d8946-120">**도메인**</span><span class="sxs-lookup"><span data-stu-id="d8946-120">**Domain**</span></span>  
 <span data-ttu-id="d8946-121">HTTP 연결 관리자에서 자격 증명을 사용하는 경우에는 사용자 이름, 암호 및 도메인을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-121">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="d8946-122">**프록시 무시 목록**</span><span class="sxs-lookup"><span data-stu-id="d8946-122">**Proxy bypass list**</span></span>  
 <span data-ttu-id="d8946-123">프록시 서버를 사용하지 않도록 지정할 주소 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-123">The list of addresses for which  you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="d8946-124">**추가**</span><span class="sxs-lookup"><span data-stu-id="d8946-124">**Add**</span></span>  
 <span data-ttu-id="d8946-125">프록시 서버를 사용하지 않도록 할 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-125">Type an address for which you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="d8946-126">**제거**</span><span class="sxs-lookup"><span data-stu-id="d8946-126">**Remove**</span></span>  
 <span data-ttu-id="d8946-127">주소를 선택한 다음 **제거**를 클릭하여 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="d8946-127">Select an address, and then remove it by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8946-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8946-128">See Also</span></span>  
 <span data-ttu-id="d8946-129">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d8946-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="d8946-130">HTTP 연결 관리자 편집기&#40;서버 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="d8946-130">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
  
