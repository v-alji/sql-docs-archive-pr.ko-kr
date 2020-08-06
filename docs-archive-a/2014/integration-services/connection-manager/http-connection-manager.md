---
title: HTTP 연결 관리자 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10c9f0778faa25aff8db4ad54ecaa8d3ccc5b359
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740198"
---
# <a name="http-connection-manager"></a><span data-ttu-id="eb85a-102">HTTP 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="eb85a-102">HTTP Connection Manager</span></span>
  <span data-ttu-id="eb85a-103">HTTP 연결을 사용하면 패키지에서 HTTP를 통해 웹 서버에 액세스하고 파일을 보내거나 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-103">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="eb85a-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에 포함된 웹 서비스 태스크에서는 이 연결 관리자가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-104">The Web Service task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="eb85a-105">패키지에 HTTP 연결 관리자를 추가하면 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 런타임에 HTTP 연결로 확인되는 연결 관리자를 만들고, 연결 관리자 속성을 설정하며, 연결 관리자를 패키지의 `Connections` 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-105">When you add an HTTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an HTTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="eb85a-106">연결 관리자의 `ConnectionManagerType` 속성이 `HTTP.`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-106">The `ConnectionManagerType` property of the connection manager is set to `HTTP.`</span></span>  
  
 <span data-ttu-id="eb85a-107">다음과 같은 방법으로 HTTP 연결 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-107">You can configure the HTTP connection manager the following ways:</span></span>  
  
-   <span data-ttu-id="eb85a-108">자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-108">Use credentials.</span></span> <span data-ttu-id="eb85a-109">연결 관리자에서 자격 증명이 사용되는 경우 해당 속성에는 사용자 이름, 암호 및 도메인이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-109">If the connection manager uses credentials, its properties include the user name, password, and domain.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eb85a-110">HTTP 연결 관리자는 익명 인증과 기본 인증만 지원하며</span><span class="sxs-lookup"><span data-stu-id="eb85a-110">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="eb85a-111">Windows 인증은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="eb85a-112">클라이언트 인증서를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-112">Use a client certificate.</span></span> <span data-ttu-id="eb85a-113">연결 관리자에서 클라이언트 인증서가 사용되는 경우 해당 속성에는 인증서 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-113">If the connection manager uses a client certificate, its properties include the certificate name.</span></span>  
  
-   <span data-ttu-id="eb85a-114">서버 연결에 대한 제한 시간 값과 데이터 기록에 대한 청크 크기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-114">Provide a time-out for connecting to the server and a chunk size for writing data.</span></span>  
  
-   <span data-ttu-id="eb85a-115">프록시 서버를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-115">Use a proxy server.</span></span> <span data-ttu-id="eb85a-116">자격 증명을 사용하고 프록시 서버 대신 로컬 주소를 사용하도록 프록시 서버를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-116">The proxy server can also be configured to use credentials and to bypass the proxy server and use local addresses instead.</span></span>  
  
## <a name="configuration-of-the-http-connection-manager"></a><span data-ttu-id="eb85a-117">HTTP 연결 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="eb85a-117">Configuration of the HTTP Connection Manager</span></span>  
 <span data-ttu-id="eb85a-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb85a-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="eb85a-119">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="eb85a-119">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="eb85a-120">HTTP 연결 관리자 편집기&#40;서버 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eb85a-120">HTTP Connection Manager Editor &#40;Server Page&#41;</span></span>](../http-connection-manager-editor-server-page.md)  
  
-   [<span data-ttu-id="eb85a-121">HTTP 연결 관리자 편집기&#40;프록시 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="eb85a-121">HTTP Connection Manager Editor &#40;Proxy Page&#41;</span></span>](../http-connection-manager-editor-proxy-page.md)  
  
 <span data-ttu-id="eb85a-122">연결 관리자를 프로그래밍 방식으로 구성하는 방법에 대한 자세한 내용은 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eb85a-122">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb85a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb85a-123">See Also</span></span>  
 <span data-ttu-id="eb85a-124">[웹 서비스 태스크](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="eb85a-124">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="eb85a-125">Integration Services&#40;SSIS&#41; 연결</span><span class="sxs-lookup"><span data-stu-id="eb85a-125">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
