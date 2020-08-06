---
title: Master Data Services 데이터베이스 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 8373bb35-f0f9-4c3c-a53c-dfaa2ce567ac
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ee90ac5d02489da3b411b12389e949ff3136287
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647715"
---
# <a name="create-a-master-data-services-database"></a><span data-ttu-id="b72a4-102">Master Data Services 데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="b72a4-102">Create a Master Data Services Database</span></span>
  <span data-ttu-id="b72a4-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 애플리케이션 및 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 서비스를 지원할 새 데이터베이스가 필요한 경우 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-103">Create a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database when you need a new database to support the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application and [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b72a4-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b72a4-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="b72a4-105">데이터베이스를 호스트하는 컴퓨터의 요구 사항에 대한 자세한 내용은 [데이터베이스 요구 사항&#40;Master Data Services&#41;](database-requirements-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b72a4-105">For information about the requirements for the computer that hosts the database, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
### <a name="to-create-a-master-data-services-database"></a><span data-ttu-id="b72a4-106">Master Data Services 데이터베이스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b72a4-106">To create a Master Data Services database</span></span>  
  
1.  <span data-ttu-id="b72a4-107">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-107">Open [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].</span></span>  
  
2.  <span data-ttu-id="b72a4-108">왼쪽 창에서 **데이터베이스 구성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-108">In the left pane, click **Database Configuration**.</span></span>  
  
3.  <span data-ttu-id="b72a4-109">**데이터베이스 구성** 페이지에서 **데이터베이스 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-109">On the **Database Configuration** page, click **Create Database**.</span></span>  
  
4.  <span data-ttu-id="b72a4-110">**데이터베이스 만들기** 마법사를 완료하여 데이터베이스를 만들고 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-110">Complete the **Create Database** wizard to create and configure the database.</span></span> <span data-ttu-id="b72a4-111">마법사의 UI(사용자 인터페이스) 옵션에 대한 자세한 내용은 [데이터베이스 만들기 마법사&#40;Master Data Services 구성 관리자&#41;](../create-database-wizard-master-data-services-configuration-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b72a4-111">For information about the user interface (UI) options in the wizard, see [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../create-database-wizard-master-data-services-configuration-manager.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b72a4-112">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b72a4-112">Next Steps</span></span>  
  
-   <span data-ttu-id="b72a4-113">데이터베이스 및 웹 애플리케이션에 대한 시스템 설정을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-113">Configure system settings for the database and web application.</span></span> <span data-ttu-id="b72a4-114">자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../system-settings-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b72a4-114">For more information, see [System Settings &#40;Master Data Services&#41;](../system-settings-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b72a4-115">이 데이터베이스와 연결할 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-115">Create a [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application to associate with this database.</span></span> <span data-ttu-id="b72a4-116">자세한 내용은 [마스터 데이터 관리자 웹 애플리케이션 만들기&#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b72a4-116">For more information, see [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b72a4-117">데이터베이스 및 트랜잭션 로그를 백업하도록 유지 관리 계획을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b72a4-117">Configure a maintenance plan to back up the database and transaction logs.</span></span> <span data-ttu-id="b72a4-118">자세한 내용은 [데이터베이스 요구 사항&#40;Master Data Services&#41;](database-requirements-master-data-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b72a4-118">For more information, see [Database Requirements &#40;Master Data Services&#41;](database-requirements-master-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72a4-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b72a4-119">See Also</span></span>  
 [<span data-ttu-id="b72a4-120">MDS(Master Data Services) 설치</span><span class="sxs-lookup"><span data-stu-id="b72a4-120">Install Master Data Services</span></span>](install-master-data-services.md)  
  
  
