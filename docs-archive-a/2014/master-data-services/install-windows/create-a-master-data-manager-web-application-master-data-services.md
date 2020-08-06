---
title: 마스터 데이터 관리자 웹 애플리케이션 만들기(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 241d46d7-8008-47f6-bebd-0dfff1cc856a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fd81188b499850397aa8ffd2e40cfcb91c648288
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647716"
---
# <a name="create-a-master-data-manager-web-application-master-data-services"></a><span data-ttu-id="368f8-102">마스터 데이터 관리자 웹 애플리케이션 만들기(Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="368f8-102">Create a Master Data Manager Web Application (Master Data Services)</span></span>
  <span data-ttu-id="368f8-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션은 마스터 데이터 작업을 하는 사용자 및 MDS를 구성하고 관리하는 관리자를 위한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application provides an interface for users to work with master data and for administrators to configure and administer MDS.</span></span>  
  
 <span data-ttu-id="368f8-104">웹 애플리케이션은 항상 웹 사이트에 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-104">A web application must always be contained by a website.</span></span> <span data-ttu-id="368f8-105">웹 애플리케이션을 만들려면 다음 중 하나를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-105">To create a web application, you must either:</span></span>  
  
-   <span data-ttu-id="368f8-106">기본 웹 사이트를 사용하고 웹 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-106">Use the Default website and then create the web application,</span></span>  
  
-   <span data-ttu-id="368f8-107">기존 웹 사이트를 사용하고 웹 애플리케이션을 만듭니다. 또는</span><span class="sxs-lookup"><span data-stu-id="368f8-107">Use an existing website and then create the web application, or</span></span>  
  
-   <span data-ttu-id="368f8-108">웹 애플리케이션을 자동으로 만드는 새 웹 사이트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-108">Create a new website, which automatically creates a web application.</span></span>  
  
 <span data-ttu-id="368f8-109">웹 애플리케이션을 만든 후 이를 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-109">After you create the web application, you associate it with the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="368f8-110">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="368f8-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="368f8-111">웹 애플리케이션을 호스트하는 컴퓨터의 요구 사항에 대한 자세한 내용은 [웹 애플리케이션 요구 사항&#40;Master Data Services&#41;](web-application-requirements-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-111">For information about the requirements for the computer that hosts the web application, see [Web Application Requirements &#40;Master Data Services&#41;](web-application-requirements-master-data-services.md).</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="368f8-112">새 웹 사이트에서 마스터 데이터 관리자 웹 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="368f8-112">To create a Master Data Manager web application in a new website</span></span>  
 <span data-ttu-id="368f8-113">새 웹 사이트를 만들면 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션이 루트 웹 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-113">When you create a new website, the root web application is the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="368f8-114">또한 웹 애플리케이션이 새 애플리케이션 풀에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-114">The web application is also added to a new application pool.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="368f8-115">이 절차를 따르는 경우 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 가상 경로 및 별칭을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-115">If you follow this procedure, you cannot specify a virtual path and alias of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> <span data-ttu-id="368f8-116">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에 대한 가상 경로 및 별칭을 지정하려면 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션으로 이미 구성되지 않은 기존 웹 사이트에서 웹 애플리케이션을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-116">If you want to specify a virtual path and alias for [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must create a web application in an existing website that is not already configured as a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
 <span data-ttu-id="368f8-117">또한 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 에서는 HTTP 바인딩만 사용하여 사이트를 만드는 것이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-117">Additionally, [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] supports creating sites with HTTP bindings only.</span></span> <span data-ttu-id="368f8-118">HTTPS 바인딩을 추가하려면 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] 에서 새 사이트 및 애플리케이션을 만듭니다. 자세한 내용은 [마스터 데이터 관리자 웹 애플리케이션의 보안 설정](secure-a-master-data-manager-web-application.md) 을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-118">To add an HTTPS binding, create a new site and application in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] and then see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md) for more information.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-a-new-website"></a><span data-ttu-id="368f8-119">새 웹 사이트에서 마스터 데이터 관리자 웹 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="368f8-119">To create a Master Data Manager web application in a new website</span></span>  
  
1.  <span data-ttu-id="368f8-120">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-120">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="368f8-121">왼쪽 창에서 **웹 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-121">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="368f8-122">**웹 구성** 페이지의 웹 사이트 목록에서 **새 웹 사이트 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-122">On the **Web Configuration** page, in the Website list, select **Create new website**.</span></span>  
  
4.  <span data-ttu-id="368f8-123">**웹 사이트 만들기** 대화 상자에서 새 웹 사이트에 대한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-123">On the **Create Website** dialog box, specify information for a new website.</span></span> <span data-ttu-id="368f8-124">대화 상자의 UI(사용자 인터페이스) 옵션에 대한 자세한 내용은 [웹 사이트 만들기 대화 상자&#40;Master Data Services 구성 관리자&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-124">For more information about the user interface (UI) options in the dialog box, see [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
5.  <span data-ttu-id="368f8-125">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-125">Click **OK**.</span></span>  
  
## <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="368f8-126">기존 웹 사이트에서 마스터 데이터 관리자 웹 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="368f8-126">To create a Master Data Manager web application in an existing website</span></span>  
 <span data-ttu-id="368f8-127">기존 웹 사이트에서 웹 애플리케이션을 만드는 경우 웹 애플리케이션의 가상 경로 및 별칭을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-127">When you create a web application in an existing website, you can choose the virtual path and alias of the web application.</span></span> <span data-ttu-id="368f8-128">이 웹 애플리케이션은 새 애플리케이션 풀에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-128">The web application is added to a new application pool.</span></span>  
  
#### <a name="to-create-a-master-data-manager-web-application-in-an-existing-website"></a><span data-ttu-id="368f8-129">기존 웹 사이트에서 마스터 데이터 관리자 웹 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="368f8-129">To create a Master Data Manager web application in an existing website</span></span>  
  
1.  <span data-ttu-id="368f8-130">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-130">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="368f8-131">왼쪽 창에서 **웹 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-131">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="368f8-132">**웹 구성** 페이지의 **웹 사이트** 목록에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 만들려는 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-132">On the **Web Configuration** page, from the **Website** list, select the website in which you want to create the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="368f8-133">**애플리케이션 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-133">Click **Create Application**.</span></span>  
  
5.  <span data-ttu-id="368f8-134">**웹 애플리케이션 만들기** 대화 상자에서 새 웹 애플리케이션에 대한 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-134">On the **Create Web Application** dialog box, specify information for a new web application.</span></span> <span data-ttu-id="368f8-135">대화 상자의 UI(사용자 인터페이스) 옵션에 대한 자세한 내용은 [웹 애플리케이션 만들기 대화 상자&#40;Master Data Services 구성 관리자&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-135">For more information about the user interface (UI) options in the dialog box, see [Create Web Application Dialog Box &#40;Master Data Services Configuration Manager&#41;](../create-web-application-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
6.  <span data-ttu-id="368f8-136">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-136">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="368f8-137">다음 단계</span><span class="sxs-lookup"><span data-stu-id="368f8-137">Next Steps</span></span>  
  
-   <span data-ttu-id="368f8-138">웹 애플리케이션을 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-138">Associate the web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="368f8-139">자세한 내용은 [Master Data Services 데이터베이스와 웹 애플리케이션 연결](associate-a-master-data-services-database-and-web-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-139">For more information, see [Associate a Master Data Services Database and Web Application](associate-a-master-data-services-database-and-web-application.md).</span></span>  
  
-   <span data-ttu-id="368f8-140">필요에 따라 SSL(Secure Sockets Layer)을 사용하여 콘텐츠를 암호화하려는 경우 HTTPS 바인딩을 사용하도록 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 호스트하는 웹 사이트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-140">Optionally, configure the website that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to use an HTTPS binding if you want to encrypt content by using Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="368f8-141">IIS 관리자와 같은 IIS(인터넷 정보 서비스) 도구를 사용하여 웹 서버에 대한 서버 인증서를 구성하고 사이트에 대한 HTTPS 바인딩 및 SSL 설정을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="368f8-141">You must use an Internet Information Services (IIS) tool, such as IIS Manager, to configure the server certificate for the web server, and to configure an HTTPS binding and the SSL settings for the site.</span></span> <span data-ttu-id="368f8-142">자세한 내용은 [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="368f8-142">For more information, see [Secure a Master Data Manager Web Application](secure-a-master-data-manager-web-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368f8-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="368f8-143">See Also</span></span>  
 [<span data-ttu-id="368f8-144">MDS(Master Data Services) 설치</span><span class="sxs-lookup"><span data-stu-id="368f8-144">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
