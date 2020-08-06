---
title: Master Data Services 데이터베이스와 웹 애플리케이션 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ccb25672-f71d-4135-b548-f50eb45d8fa5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 01afde6aea5065a51cb9e7ae5dc4151e9f1e9fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729551"
---
# <a name="associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="a1c26-102">Master Data Services 데이터베이스와 웹 애플리케이션 연결</span><span class="sxs-lookup"><span data-stu-id="a1c26-102">Associate a Master Data Services Database and Web Application</span></span>
  <span data-ttu-id="a1c26-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스와 연결하여 웹 작업에 사용할 데이터베이스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-103">Associate your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database to specify the database to use for web operations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a1c26-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a1c26-104">Prerequisites</span></span>  
  
-   [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="a1c26-105">가 로컬 컴퓨터에 설치되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-105">must be installed on the local computer.</span></span> <span data-ttu-id="a1c26-106">자세한 내용은 [Master Data Services 설치](install-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c26-106">For more information, see [Install Master Data Services](install-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a1c26-107">로컬 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-107">A local [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application must exist.</span></span> <span data-ttu-id="a1c26-108">자세한 내용은 [마스터 데이터 관리자 웹 애플리케이션 만들기&#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c26-108">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="a1c26-109">로컬 또는 원격 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-109">Either a local or remote [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database must exist.</span></span> <span data-ttu-id="a1c26-110">자세한 내용은 [Master Data Services 데이터베이스 만들기](create-a-master-data-services-database.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c26-110">For more information, see [Create a Master Data Services Database](create-a-master-data-services-database.md).</span></span>  
  
### <a name="to-associate-a-master-data-services-database-and-web-application"></a><span data-ttu-id="a1c26-111">Master Data Services 데이터베이스 및 웹 애플리케이션을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="a1c26-111">To associate a Master Data Services database and web application</span></span>  
  
1.  <span data-ttu-id="a1c26-112">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-112">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="a1c26-113">왼쪽 창에서 **웹 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-113">In the left pane, click **Web Configuration**.</span></span>  
  
3.  <span data-ttu-id="a1c26-114">**웹 구성** 페이지의 **웹 애플리케이션**아래에 있는 **웹 사이트** 목록에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션이 포함된 웹 사이트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-114">On the **Web Configuration** page, under **Web application**, from the **Website** list, select the website that contains your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
4.  <span data-ttu-id="a1c26-115">**웹 애플리케이션** 상자에서 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]를 호스팅하는 웹 애플리케이션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-115">In the **Web application** box, select the web application that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
5.  <span data-ttu-id="a1c26-116">**애플리케이션을 데이터베이스에 연결**에서 **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-116">Under **Associate Application with Database**, click **Select**.</span></span> <span data-ttu-id="a1c26-117">**데이터베이스에 연결** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-117">The **Connect to Database** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="a1c26-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스를 호스팅하는 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 의 인스턴스에 대한 연결 정보를 지정하고 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-118">Specify connection information for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that hosts the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database, and click **Connect**.</span></span>  
  
7.  <span data-ttu-id="a1c26-119">**Master Data Services 데이터베이스** 목록에서 웹 애플리케이션을 연결할 데이터베이스를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-119">From the **Master Data Services database** list, select the database you want to associate the web application with and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="a1c26-120">**애플리케이션을 데이터베이스에 연결**에서 인스턴스 및 데이터베이스 정보가 올바른지 확인한 다음 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-120">Under **Associate Application with Database**, verify that the instance and database information are correct, and then click **Apply**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1c26-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a1c26-121">Next Steps</span></span>  
  
-   <span data-ttu-id="a1c26-122">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 서비스에 대한 프로그래밍 방식의 액세스는 웹 애플리케이션을 만들 때 자동으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-122">Programmatic access to [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web services is automatically enabled when the web application is created.</span></span> <span data-ttu-id="a1c26-123">개발자가 서비스 메타데이터에 액세스하여 프로그래밍 방식의 액세스를 위한 프록시 클래스를 쉽게 생성할 수 있도록 하려면 메타데이터 게시를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-123">To let developers access the service metadata to easily generate proxy classes for programmatic access, enable metadata publishing.</span></span> <span data-ttu-id="a1c26-124">자세한 내용은 [Create Master Data Manager Web Service Proxy Classes](../develop/create-master-data-manager-web-service-proxy-classes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c26-124">For more information, see [Create Master Data Manager Web Service Proxy Classes](../develop/create-master-data-manager-web-service-proxy-classes.md).</span></span>  
  
-   <span data-ttu-id="a1c26-125">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에 사용자 및 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-125">Add users and groups to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span> <span data-ttu-id="a1c26-126">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에 대한 액세스 권한이 사용자나 그룹에 부여되지 않은 경우 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 시스템 관리자 자격 증명을 사용하여 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1c26-126">If no users or groups have been granted access to [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], you must open [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] using the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] system administrator credentials.</span></span> <span data-ttu-id="a1c26-127">자세한 내용은 [관리자&#40;Master Data Services&#41;](../administrators-master-data-services.md) 및 [사용자 및 그룹&#40;Master Data Services&#41;](../users-and-groups-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1c26-127">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md) and [Users and Groups &#40;Master Data Services&#41;](../users-and-groups-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c26-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1c26-128">See Also</span></span>  
 <span data-ttu-id="a1c26-129">[MDS(Master Data Services) 설치](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="a1c26-129">[Install Master Data Services](install-master-data-services.md) </span></span>  
 [<span data-ttu-id="a1c26-130">웹 구성 페이지&#40;Master Data Services 구성 마법사&#41;</span><span class="sxs-lookup"><span data-stu-id="a1c26-130">Web Configuration Page &#40;Master Data Services Configuration Manager&#41;</span></span>](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
