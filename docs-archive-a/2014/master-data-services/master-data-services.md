---
title: MDS(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 87d8c588c3893a5aadf950a60681ec60d50309de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651751"
---
# <a name="master-data-services"></a><span data-ttu-id="2a981-102">Master Data Services</span><span class="sxs-lookup"><span data-stu-id="2a981-102">Master Data Services</span></span>
  <span data-ttu-id="2a981-103">MDS([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] )는 마스터 데이터 관리용 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] solution for master data management.</span></span> <span data-ttu-id="2a981-104">MDM(마스터 데이터 관리)은 조직에서 유지 가능한 마스터 목록을 컴파일할 목적으로 비트랜잭션 데이터 목록을 검색 및 정의하기 위해 수행하는 작업을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-104">Master data management (MDM) describes the efforts made by an organization to discover and define non-transactional lists of data, with the goal of compiling maintainable master lists.</span></span> <span data-ttu-id="2a981-105">MDM 프로젝트에는 일반적으로 MDM 기술 구현과 함께 내부 비즈니스 프로세스의 평가 및 재구성 과정이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-105">An MDM project generally includes an evaluation and restructuring of internal business processes along with the implementation of MDM technology.</span></span> <span data-ttu-id="2a981-106">성공적인 MDM 솔루션의 결과로 분석 가능한 신뢰할 수 있는 중앙 집중식 데이터를 얻게 되므로 비즈니스 의사 결정의 효율성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-106">The result of a successful MDM solution is reliable, centralized data that can be analyzed, resulting in better business decisions.</span></span>

 <span data-ttu-id="2a981-107">적절한 교육을 통해 모든 비즈니스 사용자는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 솔루션을 구현할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-107">With the right training, most business users should be able to implement a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] solution.</span></span> <span data-ttu-id="2a981-108">또한 MDS를 사용하여 고객, 제품 또는 계정 목록 관리뿐 아니라 모든 도메인도 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-108">In addition, you can use MDS to manage any domain; it's not specific to managing lists of customers, products, or accounts.</span></span> <span data-ttu-id="2a981-109">MDS를 처음 설치 하는 경우에는 모든 도메인에 대 한 구조를 포함 하지 않습니다 .이에 대 한 모델을 만들어 필요한 도메인을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-109">When MDS is first installed, it does not include the structure for any domains-you define the domains you need by creating models for them.</span></span>

 <span data-ttu-id="2a981-110">기타 Master Data Services 기능에는 계층, 세부적인 보안, 트랜잭션, 데이터 버전 관리, 비즈니스 규칙 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-110">Other Master Data Services features include hierarchies, granular security, transactions, data versioning, and business rules.</span></span>

 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="2a981-111">에는 다음 구성 요소와 도구가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-111">includes the following components and tools:</span></span>

-   [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="2a981-112">- [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스 및 웹 애플리케이션을 만들고 구성하는 데 사용하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-112">, a tool you use to create and configure [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] databases and web applications.</span></span>

-   [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] <span data-ttu-id="2a981-113">- 모델 또는 비즈니스 규칙 만들기와 같은 관리 작업을 수행하는 데 사용하며 데이터를 업데이트하기 위해 액세스하는 웹 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-113">, a web application you use to perform administrative tasks (like creating a model or business rule), and that users access to update data.</span></span>

-   <span data-ttu-id="2a981-114">MDSModelDeploy.exe - 다른 환경에 배포할 모델 개체와 데이터 패키지를 만드는 데 사용하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-114">MDSModelDeploy.exe, a tool you use to create packages of your model objects and data so you can deploy them to other environments.</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="2a981-115">웹 서비스 - 개발자가 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에 대한 사용자 지정 솔루션을 확장하거나 개발하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-115">web service, which developers can use to extend or develop custom solutions for [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].</span></span>

-   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]<span data-ttu-id="2a981-116">- [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 데이터를 관리 하 고 새 엔터티 및 특성을 만드는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a981-116">[!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], which you use to manage data and create new entities and attributes.</span></span>

 <span data-ttu-id="2a981-117">MDS 리소스에 대 한 요약은 [SQL Server Master Data Services 포털](https://go.microsoft.com/fwlink/?LinkID=214272)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2a981-117">For a summary of MDS resources, see the [SQL Server Master Data Services Portal](https://go.microsoft.com/fwlink/?LinkID=214272).</span></span>

|||
|-|-|
|<span data-ttu-id="2a981-118">**영역별 내용 찾아보기**</span><span class="sxs-lookup"><span data-stu-id="2a981-118">**Browse Content by Area**</span></span><br /> <span data-ttu-id="2a981-119">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [MDS(Master Data Services) 개요](master-data-services-overview-mds.md)</span><span class="sxs-lookup"><span data-stu-id="2a981-119">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Overview](master-data-services-overview-mds.md)</span></span><br /><br /> <span data-ttu-id="2a981-120">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [MDS(Master Data Services) 기능 및 작업](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="2a981-120">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Master Data Services Features and Tasks](../../2014/master-data-services/master-data-services-features-and-tasks.md)</span></span><br /><br /> <span data-ttu-id="2a981-121">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [기술 참조 (MDS(Master Data Services))](technical-reference-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="2a981-121">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Technical Reference (Master Data Services)](technical-reference-master-data-services.md)</span></span><br /><br /> <span data-ttu-id="2a981-122">![작은 파일 폴더 아이콘](../../2014/integration-services/media/filefolder-small.gif "작은 파일 폴더 아이콘") [개발자 가이드 (MDS(Master Data Services))](develop/master-data-services-developer-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="2a981-122">![Small File Folder Icon](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Developer's Guide (Master Data Services)](develop/master-data-services-developer-documentation.md)</span></span>||


