---
title: 마스터 데이터 관리자 웹 애플리케이션의 보안 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f2ee807c2cd474542f701226d08427ade8279e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738499"
---
# <a name="secure-a-master-data-manager-web-application"></a><span data-ttu-id="96b92-102">마스터 데이터 관리자 웹 애플리케이션의 보안 설정</span><span class="sxs-lookup"><span data-stu-id="96b92-102">Secure a Master Data Manager Web Application</span></span>
  <span data-ttu-id="96b92-103">HTTPS를 사용하여 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-103">You can secure the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with HTTPS.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="96b92-104">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션은 HTTP 또는 HTTPS 중 하나를 사용할 수 있지만 둘 다 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-104">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application can use either HTTP or HTTPS, but not both.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="96b92-105">전제 조건</span><span class="sxs-lookup"><span data-stu-id="96b92-105">Prerequisites</span></span>  
 <span data-ttu-id="96b92-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="96b92-106">To perform the procedure:</span></span>  
  
-   <span data-ttu-id="96b92-107">사용자가 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 가 설치된 웹 서버의 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-107">You must be an administrator on the web server where [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="96b92-108">MDS가 웹 서버에 설치되어 있으며 웹 애플리케이션이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-108">MDS must be installed on the web server, and a web application must exist.</span></span> <span data-ttu-id="96b92-109">자세한 내용은 [MDS(Master Data Services) 설치](install-master-data-services.md) 및 [마스터 데이터 관리자 웹 애플리케이션 만들기&#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96b92-109">For more information, see [Install Master Data Services](install-master-data-services.md) and [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a><span data-ttu-id="96b92-110">HTTPS를 사용하여 마스터 데이터 관리자 웹 애플리케이션의 보안을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="96b92-110">To secure the Master Data Manager web application with HTTPS</span></span>  
  
1.  <span data-ttu-id="96b92-111">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션이 HTTP로 올바르게 구성되어 있는지 확인한 후 IIS에서 인증서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-111">After you have confirmed that the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application is configured correctly with HTTP, create a certificate in IIS.</span></span> <span data-ttu-id="96b92-112">자세한 내용은 [IIS 7에서 서버 인증서 구성](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="96b92-112">For more information, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).</span></span>  
  
2.  <span data-ttu-id="96b92-113">**연결** 창의 **사이트**에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 호스팅하는 사이트를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-113">In the **Connections** pane, under **Sites**, click the site that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
3.  <span data-ttu-id="96b92-114">**작업** 창에서 **바인딩**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-114">In the **Actions** pane, click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="96b92-115">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-115">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="96b92-116">목록에서 **https**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-116">From the list, select **https**.</span></span>  
  
6.  <span data-ttu-id="96b92-117">SSL 인증서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-117">Select the SSL certificate.</span></span>  
  
7.  <span data-ttu-id="96b92-118">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-118">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="96b92-119">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-119">Optional.</span></span> <span data-ttu-id="96b92-120">사용자가 HTTPS를 통해서만 사이트에 액세스할 수 있도록 HTTP를 제거하려면 목록에서 **http**가 포함된 행을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-120">To remove HTTP so that users can access the site with HTTPS only, from the list, click the row with **http**.</span></span> <span data-ttu-id="96b92-121">**제거** 를 클릭하고 확인 대화 상자에서 **예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-121">Click **Remove** and on the confirmation dialog box, click **Yes**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="96b92-122">HTTP를 제거한 후 basicHttp 및 wsHttpBinding 구성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-122">You must change basicHttp and wsHttpBinding configurations after removing HTTP.</span></span>  
  
9. <span data-ttu-id="96b92-123">**사이트 바인딩** 대화 상자를 닫으려면 **닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-123">To close the **Site Bindings** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="96b92-124">이제 *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication에서 web.config 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-124">Now open the web.config file from *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.</span></span>  
  
11. <span data-ttu-id="96b92-125">`<security mode="Message">` 라는 문자열을 찾아 `<security mode="Transport">`로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-125">Find the string `<security mode="Message">` and change it to `<security mode="Transport">`.</span></span>  
  
12. <span data-ttu-id="96b92-126">파일을 저장하고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-126">Save and close the file.</span></span> <span data-ttu-id="96b92-127">오류가 발생하는 경우 UAC를 사용하기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-127">If you get an error, it could be because you have UAC enabled.</span></span> <span data-ttu-id="96b92-128">자세한 내용은 [사용자 계정 컨트롤 해제](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="96b92-128">For more information, see [Turn off User Account Control](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx).</span></span> <span data-ttu-id="96b92-129">이제 사용자가 HTTPS를 사용하여 사이트에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96b92-129">Users should now be able to use HTTPS to access the site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b92-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="96b92-130">See Also</span></span>  
 [<span data-ttu-id="96b92-131">마스터 데이터 관리자 웹 애플리케이션 만들기&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="96b92-131">Create a Master Data Manager Web Application &#40;Master Data Services&#41;</span></span>](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
