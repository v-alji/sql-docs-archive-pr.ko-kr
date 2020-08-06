---
title: '2 단원: 웹 참조 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 02ca614cb042211ac468246c3003efaa5f2e8fb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733384"
---
# <a name="lesson-2-adding-a-web-reference"></a><span data-ttu-id="72714-102">2단원: 웹 참조 추가</span><span class="sxs-lookup"><span data-stu-id="72714-102">Lesson 2: Adding a Web Reference</span></span>
  <span data-ttu-id="72714-103">웹 서비스 검색은 클라이언트에서 웹 서비스를 찾고 해당 서비스에 대한 설명을 얻는 과정입니다.</span><span class="sxs-lookup"><span data-stu-id="72714-103">Web service discovery is the process by which a client locates a Web service and obtains its service description.</span></span> <span data-ttu-id="72714-104">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 웹 서비스 검색 과정에는 미리 결정된 알고리즘을 따르는 웹 사이트를 질의하는 과정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="72714-104">The process of Web service discovery in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] involves interrogating a Web site following a predetermined algorithm.</span></span> <span data-ttu-id="72714-105">이러한 과정의 목적은 WSDL(웹 서비스 설명 언어)을 사용하는 XML 문서인 서비스 설명을 찾는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="72714-105">The goal of the process is to locate the service description, which is an XML document that uses the Web Services Description Language (WSDL).</span></span>  
  
 <span data-ttu-id="72714-106">서비스 설명은 사용할 수 있는 서비스 및 이러한 서비스와 상호 작용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-106">The service description describes what services are available and how to interact with those services.</span></span> <span data-ttu-id="72714-107">서비스 설명이 없으면 웹 서비스와 프로그래밍 방식으로 상호 작용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="72714-107">Without a service description, it is impossible to programmatically interact with a Web service.</span></span>  
  
 <span data-ttu-id="72714-108">사용자의 애플리케이션에는 웹 서비스와 통신하기 위한 방법과 실행할 때 웹 서비스를 찾을 수 있는 방법이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-108">Your application must have a means to communicate with the Web service and to locate it at run time.</span></span> <span data-ttu-id="72714-109">웹 서비스에 대한 웹 참조를 프로젝트에 추가하면 웹 서비스와 상호 작용하고 웹 서비스의 로컬 표시를 제공하는 프록시 클래스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72714-109">Adding a Web reference to your project for the Web service does this by generating a proxy class that interfaces with the Web service and provides a local representation of the Web service.</span></span> <span data-ttu-id="72714-110">자세한 내용은 설명서의 "방법: XML 웹 서비스 프록시 생성"을 참조 하세요 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="72714-110">For more information, see "How to: Generate an XML Web Service Proxy" in your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] documentation.</span></span>  
  
### <a name="to-add-a-web-reference"></a><span data-ttu-id="72714-111">웹 참조를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="72714-111">To add a Web reference</span></span>  
  
1.  <span data-ttu-id="72714-112">**프로젝트** 메뉴에서 **서비스 참조 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-112">On the **Project** menu, click **Add Service Reference**.</span></span>  
  
2.  <span data-ttu-id="72714-113">**서비스 참조 추가** 대화 상자에서 **고급**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-113">In the **Add Service Reference** dialog box, click **Advanced**.</span></span>  
  
3.  <span data-ttu-id="72714-114">**서비스 참조 설정** 대화 상자에서 **웹 참조 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-114">In the **Service Reference Settings** dialog box, click **Add Web Reference**.</span></span>  
  
4.  <span data-ttu-id="72714-115">**웹 참조 추가** 대화 상자의 **Url** 상자에 보고서 서버 웹 서비스에 대 한 서비스 설명 (예:)을 가져올 url을 입력 합니다 http://localhost/reportserver/reportservice2010.asmx .</span><span class="sxs-lookup"><span data-stu-id="72714-115">In the **URL** box of the **Add Web Reference** dialog box, type the URL to obtain the service description of the Report Server Web service, such as http://localhost/reportserver/reportservice2010.asmx.</span></span> <span data-ttu-id="72714-116">그런 다음 **이동** 단추를 클릭 하 여 웹 서비스에 대 한 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-116">Then click the **Go** button to retrieve information about the Web service.</span></span>  
  
     <span data-ttu-id="72714-117">\- 또는 -</span><span class="sxs-lookup"><span data-stu-id="72714-117">\- or -</span></span>  
  
     <span data-ttu-id="72714-118">보고서 서버 웹 서비스가 로컬 컴퓨터에 있으면 브라우저 창에서 **로컬 컴퓨터의 웹 서비스** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-118">If the Report Server Web service exists on the local machine, click the **Web services on the local machine** link in the browser pane.</span></span> <span data-ttu-id="72714-119">그런 다음 나타나는 목록에서 ReportService2010 웹 서비스에 대한 링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-119">Then click the link for the ReportService2010 Web service from the list provided.</span></span>  
  
5.  <span data-ttu-id="72714-120">웹 참조 **이름** 상자에서이 웹 참조에 사용할 네임 스페이스인 ReportService2010에 대 한 웹 참조 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="72714-120">In the **Web reference name** box, rename the Web reference to ReportService2010, which is the namespace you will use for this Web reference.</span></span>  
  
6.  <span data-ttu-id="72714-121">**참조 추가** 를 클릭 하 여 대상 웹 서비스에 대 한 웹 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-121">Click **Add Reference** to add a Web reference for the target Web service.</span></span>  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]<span data-ttu-id="72714-122">는 서비스 설명을 다운로드하고 사용자 애플리케이션과 보고서 서버 웹 서비스 간에 상호 작용할 프록시 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-122">downloads the service description and generates a proxy class to interface between your application and the Report Server Web service.</span></span> <span data-ttu-id="72714-123">웹 참조가 작동할 수 있도록 <xref:System.Web.Services> 네임스페이스에 대한 참조도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-123">You will also need to add a reference to the <xref:System.Web.Services> namespace for your Web reference to work.</span></span>  
  
7.  <span data-ttu-id="72714-124">프로젝트 메뉴에서 **참조 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-124">On the Project menu, click **Add Reference**.</span></span>  
  
8.  <span data-ttu-id="72714-125">**참조 추가** 대화 상자의 **.NET** 탭에서 **System.Web.Services**를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="72714-125">In the **Add Reference** dialog box, in the **.NET** tab, select **System.Web.Services**, then click **OK**.</span></span>  
  
 <span data-ttu-id="72714-126">자세한 내용은 [SOAP API 액세스](../reporting-services/report-server-web-service/accessing-the-soap-api.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="72714-126">For more information, see [Accessing the SOAP API](../reporting-services/report-server-web-service/accessing-the-soap-api.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72714-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72714-127">See Also</span></span>  
 <span data-ttu-id="72714-128">[보고서 서버 웹 서비스](../reporting-services/report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="72714-128">[Report Server Web Service](../reporting-services/report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="72714-129">[3 단원: 웹 서비스 액세스](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="72714-129">[Lesson 3: Accessing the Web Service](../../2014/tutorials/lesson-3-accessing-the-web-service.md) </span></span>  
 [<span data-ttu-id="72714-130">Visual Basic 또는 Visual C&#35; &#40;SSRS 자습서를 사용 하 여 보고서 서버 웹 서비스에 액세스&#41;</span><span class="sxs-lookup"><span data-stu-id="72714-130">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
