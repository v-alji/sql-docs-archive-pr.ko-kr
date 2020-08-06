---
title: MDS(Master Data Services) |에 대 한 데이터베이스 및 웹 사이트 설정 Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: da797bc6f9838a2baab6cc440cc7d778a7a6e186
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661216"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a><span data-ttu-id="82f21-102">Master Data Services에 대한 데이터베이스 및 웹 사이트 설정</span><span class="sxs-lookup"><span data-stu-id="82f21-102">Set up the Database and Website for Master Data Services</span></span>
  <span data-ttu-id="82f21-103">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 를 사용하여 MDS( [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] )에 대한 데이터베이스 및 웹 사이트 설정</span><span class="sxs-lookup"><span data-stu-id="82f21-103">Use the [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to set up the database and website for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)</span></span>  
  
 <span data-ttu-id="82f21-104">데이터베이스 및 웹 사이트를 설정하려면 다음 작업을 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="82f21-104">To set up the database and website, complete the following tasks.</span></span>  
  
1.  <span data-ttu-id="82f21-105">에서 **데이터베이스 구성** 페이지를 사용 하 여 데이터베이스를 만듭니다 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="82f21-105">Create a database using the **Database Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="82f21-106">자세한 내용은 [데이터베이스 구성 페이지 &#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) 및 [데이터베이스 만들기 마법사 &#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82f21-106">For information, see [Database Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) and [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
2.  <span data-ttu-id="82f21-107">새 웹 사이트를 만들거나, 기본 웹 사이트를 선택 하거나,의 **웹 구성** 페이지를 사용 하 여 다른 기존 웹 사이트를 선택 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f21-107">Create a new website, select the default website, or select another existing website, using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span> <span data-ttu-id="82f21-108">그런 다음 선택했거나 만든 웹 애플리케이션과 MDS 데이터베이스를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82f21-108">Then associate the MDS database with the web application you select or create.</span></span>  
  
     <span data-ttu-id="82f21-109">자세한 내용은 [웹 구성 페이지 &#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 및 웹 [사이트 만들기 대화 상자 &#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82f21-109">For information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Create Website Dialog Box &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md).</span></span>  
  
3.  <span data-ttu-id="82f21-110">필드 에서 **웹 구성** 페이지를 사용 하 여 Data Quality Services와의 통합을 사용 하도록 설정 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="82f21-110">(Optional) Enable integration with Data Quality Services using the **Web Configuration** page in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].</span></span>  
  
     <span data-ttu-id="82f21-111">자세한 내용은 [웹 구성 페이지 &#40;Master Data Services 구성 관리자&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) 및 [MDS(Master Data Services)와 Data Quality Services 통합 사용](install-windows/enable-data-quality-services-integration-with-master-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82f21-111">For more information, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) and [Enable Data Quality Services Integration with Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).</span></span>  
  
 <span data-ttu-id="82f21-112">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 를 사용하여 MDS 데이터베이스와 연결된 웹 애플리케이션 및 서비스에 대한 설정을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82f21-112">You can also use [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] to specify settings for the web applications and services associated with the MDS database.</span></span> <span data-ttu-id="82f21-113">예를 들어 데이터를 로드하는 빈도나 유효성 검사 메일을 전송하는 빈도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82f21-113">For example, you can specify how frequently data is loaded or how often validation emails are sent.</span></span> <span data-ttu-id="82f21-114">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82f21-114">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f21-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82f21-115">See Also</span></span>  
 <span data-ttu-id="82f21-116">[MDS(Master Data Services) 데이터베이스](../../2014/master-data-services/master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="82f21-116">[Master Data Services Database](../../2014/master-data-services/master-data-services-database.md) </span></span>  
 [<span data-ttu-id="82f21-117">마스터 데이터 관리자 웹 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="82f21-117">Master Data Manager Web Application</span></span>](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
