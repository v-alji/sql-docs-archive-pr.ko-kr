---
title: 마스터 데이터 관리자 웹 서비스에 대한 프록시 클래스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4f25d749f829357f6541f14073e654bade27215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661690"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a><span data-ttu-id="273b8-102">마스터 데이터 관리자 웹 서비스에 대한 프록시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="273b8-102">Create Master Data Manager Web Service Proxy Classes</span></span>
  <span data-ttu-id="273b8-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 서비스를 사용하면 사용자의 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 사이트에 액세스할 수 있는 모든 컴퓨터에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 의 기능을 프로그래밍 방식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service lets you make programmatic use of the features of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from any computer that can access your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site.</span></span> <span data-ttu-id="273b8-104">웹 서비스에 액세스하기 위한 코드를 작성하려면 먼저 프록시 클래스를 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-104">Before you can start writing code to access the web service, you must generate proxy classes.</span></span> <span data-ttu-id="273b8-105">웹 서비스 작업을 수행하는 데 사용되는 주요 프록시 클래스는 <xref:Microsoft.MasterDataServices.ServiceClient> 인터페이스를 구현하는 <xref:Microsoft.MasterDataServices.IService> 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-105">The main proxy class you use to perform web service operations is the <xref:Microsoft.MasterDataServices.ServiceClient> class, which implements the <xref:Microsoft.MasterDataServices.IService> interface.</span></span>  
  
## <a name="enable-web-service-metadata-publishing"></a><span data-ttu-id="273b8-106">웹 서비스 메타데이터 게시 활성화</span><span class="sxs-lookup"><span data-stu-id="273b8-106">Enable Web Service Metadata Publishing</span></span>  
 <span data-ttu-id="273b8-107">프록시 클래스를 생성하려면 먼저 웹 서비스 메타데이터 게시를 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-107">Before you can generate proxy classes, you must enable web service metadata publishing.</span></span> <span data-ttu-id="273b8-108">이렇게 하려면 다음 단계를 수행하십시오.</span><span class="sxs-lookup"><span data-stu-id="273b8-108">Follow these steps to do this:</span></span>  
  
1.  <span data-ttu-id="273b8-109">텍스트 편집기에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-109">Open the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config file in a text editor.</span></span> <span data-ttu-id="273b8-110">이 파일은 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 설치 경로의 WebApplication 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-110">This file is in the WebApplication folder of the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installation path.</span></span>  
  
2.  <span data-ttu-id="273b8-111">`mdsWsHttpBehavior`에서 섹션을 찾습니다 **\<serviceBehaviors>** .</span><span class="sxs-lookup"><span data-stu-id="273b8-111">Find the `mdsWsHttpBehavior` section under **\<serviceBehaviors>**.</span></span> <span data-ttu-id="273b8-112">요소에 대해 **\<serviceMetadata>** `httpGetEnabled` 를로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-112">For the **\<serviceMetadata>** element, set `httpGetEnabled` to `true`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="273b8-113">SSL(Secure Sockets Layer)을 통해 웹 서비스를 사용하도록 설정하려면 web.config 파일의 `httpsGetEnabled` 섹션에서 `true`를 `mdsWsHttpBehavior`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-113">If you want to enable Web services over Secure Sockets Layer (SSL), set `httpsGetEnabled` to `true` in the `mdsWsHttpBehavior` section of the web.config file.</span></span> <span data-ttu-id="273b8-114">또한 `mdsWsHTTPBinding`을 SSL에 대해 구성되도록 변경하고 SSL 이외의 섹션을 주석으로 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-114">You also need to change `mdsWsHTTPBinding` so that it is configured for SSL, as well, and comment out the non-SSL section.</span></span>  
  
3.  <span data-ttu-id="273b8-115">파일의 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-115">Save changes to the file.</span></span>  
  
4.  <span data-ttu-id="273b8-116">다음과 같은 서비스 URL로 이동하여 메타데이터 게시를 테스트합니다(예: http://yourserver/MDS/service/service.svc).</span><span class="sxs-lookup"><span data-stu-id="273b8-116">Test metadata publishing by browsing to the service URL, for example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="273b8-117">메타데이터 게시가 활성화된 경우 "서비스를 만들었습니다."로</span><span class="sxs-lookup"><span data-stu-id="273b8-117">If metadata publishing is enabled, a page is displayed that begins with</span></span>   
    <span data-ttu-id="273b8-118">시작하는 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-118">"You have created a service."</span></span>  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a><span data-ttu-id="273b8-119">Visual Studio를 사용하여 프록시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="273b8-119">Creating Proxy Classes by Using Visual Studio</span></span>  
 <span data-ttu-id="273b8-120">Visual Studio 2010이 설치된 경우 프로젝트에 **서비스 참조**를 추가하면 가장 간단하게 프록시 클래스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-120">If you have Visual Studio 2010 installed, the simplest way to generate proxy classes is to add a **Service Reference** to your project.</span></span> <span data-ttu-id="273b8-121">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 URL에 /service/service.svc를 추가하면 서비스 참조의 주소가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-121">The address of the service reference is the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, appended with /service/service.svc.</span></span> <span data-ttu-id="273b8-122">예를 들면 http://yourserver/MDS/service/service.svc와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-122">For example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="273b8-123">자세한 내용은 [방법: 서비스 참조 추가, 업데이트 또는 제거](https://go.microsoft.com/fwlink/?LinkId=221167)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="273b8-123">For more information, see [How to: Add, Update, or Remove a Service Reference](https://go.microsoft.com/fwlink/?LinkId=221167).</span></span>  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a><span data-ttu-id="273b8-124">Svcutil.exe를 사용하여 프록시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="273b8-124">Creating Proxy Classes by Using Svcutil.exe</span></span>  
 <span data-ttu-id="273b8-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 컴퓨터에 Svcutil.exe를 설치 하려면 또는 Windows SDK 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-125">You must have either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK installed in order to have Svcutil.exe on your computer.</span></span> <span data-ttu-id="273b8-126">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 사용하는 경우에는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령 프롬프트를 사용하여 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-126">If you use [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], you must use the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] command prompt to run the command.</span></span> <span data-ttu-id="273b8-127">자세한 내용은 [ServiceModel Metadata 유틸리티 도구(Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) 및 [서비스 메타데이터에서 WCF 클라이언트 생성](https://go.microsoft.com/fwlink/?LinkId=164821)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="273b8-127">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) and [Generating a WCF Client from Service Metadata](https://go.microsoft.com/fwlink/?LinkId=164821).</span></span>  
  
 <span data-ttu-id="273b8-128">Svcutil.exe를 사용하여 C# 프록시 클래스 집합을 만들려면 다음과 같은 명령을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="273b8-128">To create a set of C# proxy classes by using Svcutil.exe, use a command such as the following:</span></span>  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 <span data-ttu-id="273b8-129">위치:</span><span class="sxs-lookup"><span data-stu-id="273b8-129">Where:</span></span>  
  
-   <span data-ttu-id="273b8-130">*servername*:*port*는 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]를 호스팅하는 컴퓨터의 이름과 포트 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-130">*servername*:*port* are the computer name and port number of the computer that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="273b8-131">*virtual_path*는 인터넷 정보 서비스(IIS)에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]의 가상 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-131">*virtual_path* is the virtual path of [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in Internet Information Services (IIS).</span></span>  
  
-   <span data-ttu-id="273b8-132">*proxy_name*은 생성된 프록시 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="273b8-132">*proxy_name* is the name for the generated proxy file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273b8-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="273b8-133">See Also</span></span>  
 [<span data-ttu-id="273b8-134">범주별로 분류한 웹 서비스 작업&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="273b8-134">Categorized Web Service Operations &#40;Master Data Services&#41;</span></span>](categorized-web-service-operations-master-data-services.md)  
  
  
