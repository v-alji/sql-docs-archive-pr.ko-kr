---
title: Master Data Services 데이터베이스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], about the database
- database [Master Data Services]
ms.assetid: 5f590cc1-6ec2-4b8c-a598-03de0f6051a0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7e4bae180dfb7c9051d5445a689c44978ef73bfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652170"
---
# <a name="master-data-services-database"></a><span data-ttu-id="6f233-102">Master Data Services 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="6f233-102">Master Data Services Database</span></span>
  <span data-ttu-id="6f233-103">Master Data Services 데이터베이스에는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템에 대한 모든 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-103">The database contains all of the information for the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span> <span data-ttu-id="6f233-104">이 데이터베이스는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 배포의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-104">It is central to a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span> <span data-ttu-id="6f233-105">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스의 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-105">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database:</span></span>  
  
-   <span data-ttu-id="6f233-106">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 시스템에 필요한 설정, 데이터베이스 개체 및 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-106">Stores the settings, database objects, and data required by the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system.</span></span>  
  
-   <span data-ttu-id="6f233-107">원본 시스템의 데이터를 처리하는 데 사용되는 준비 테이블을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-107">Contains staging tables that are used to process data from source systems.</span></span>  
  
-   <span data-ttu-id="6f233-108">원본 시스템의 마스터 데이터를 저장할 수 있는 스키마 및 데이터베이스 개체를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-108">Provides a schema and database objects to store master data from source systems.</span></span>  
  
-   <span data-ttu-id="6f233-109">비즈니스 규칙 유효성 검사 및 전자 메일 알림을 포함하여 버전 관리 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-109">Supports versioning functionality, including business rule validation and e-mail notifications.</span></span>  
  
-   <span data-ttu-id="6f233-110">데이터베이스에서 데이터를 검색해야 하는 구독 시스템에 뷰를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f233-110">Provides views for subscribing systems that need to retrieve data from the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f233-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6f233-111">In This Section</span></span>  
  
-   [<span data-ttu-id="6f233-112">리프 멤버 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f233-112">Leaf Member Staging Table &#40;Master Data Services&#41;</span></span>](leaf-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6f233-113">통합 멤버 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f233-113">Consolidated Member Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6f233-114">관계 준비 테이블&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f233-114">Relationship Staging Table &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/relationship-staging-table-master-data-services.md)  
  
-   [<span data-ttu-id="6f233-115">준비 프로세스 오류&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f233-115">Staging Process Errors &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/staging-process-errors-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f233-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f233-116">See Also</span></span>  
 <span data-ttu-id="6f233-117">[MDS(Master Data Services) 데이터베이스 만들기](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="6f233-117">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 <span data-ttu-id="6f233-118">[데이터베이스 개체 보안 &#40;MDS(Master Data Services)&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6f233-118">[Database Object Security &#40;Master Data Services&#41;](../../2014/master-data-services/database-object-security-master-data-services.md) </span></span>  
 [<span data-ttu-id="6f233-119">데이터베이스 로그인, 사용자 및 역할&#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6f233-119">Database Logins, Users, and Roles &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/database-logins-users-and-roles-master-data-services.md)  
  
  
