---
title: SQL Server 데이터베이스 엔진 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 93e3d7a749fe6be47cc84d43509a6f378476b2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732904"
---
# <a name="about-the-sql-server-database-engine"></a><span data-ttu-id="8ac17-102">SQL Server 데이터베이스 엔진 정보</span><span class="sxs-lookup"><span data-stu-id="8ac17-102">About the SQL Server Database Engine</span></span>
  <span data-ttu-id="8ac17-103">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 요소는 데이터 저장, 처리 및 보안 유지를 위한 핵심 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-103">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] component of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="8ac17-104">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 기업에서 수요가 높아지고 있는 대부분의 데이터 소비형 애플리케이션의 요구 사항을 만족시키기 위해 액세스 제어 및 빠른 트랜잭션 처리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-104">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] provides controlled access and rapid transaction processing to meet the requirements of the most demanding data consuming applications in your enterprise.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8ac17-105">는 한 대의 컴퓨터에서 최대 50개의 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-105">supports up to 50 instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] on a single computer.</span></span> <span data-ttu-id="8ac17-106">일반적인 설치를 만들려면 설치 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [마법사에서 SQL Server 2014 설치 &#40;설치&#41;](install-sql-server-from-the-installation-wizard-setup.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ac17-106">To create a typical [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation, see [Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](install-sql-server-from-the-installation-wizard-setup.md).</span></span>  
  
 <span data-ttu-id="8ac17-107">**중요** 로컬 설치의 경우 관리자로 설치 프로그램을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-107">**Important** For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="8ac17-108">원격 공유로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치하는 경우 원격 공유에 대한 읽기 및 실행 권한이 있는 도메인 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-108">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
 <span data-ttu-id="8ac17-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사의 설치할 구성 요소 페이지에서** 데이터베이스 엔진 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 선택하면 다음 기능이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-109">The following features are installed when you select **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine** on the Components to Install page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard:</span></span>  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   <span data-ttu-id="8ac17-110">복제 - 선택적 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-110">Replication - is an optional component</span></span>  
  
-   <span data-ttu-id="8ac17-111">전체 텍스트 검색 - 선택적 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-111">Full-Text Search - is an optional component</span></span>  
  
-   <span data-ttu-id="8ac17-112">Data Quality Services - 선택적 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-112">Data Quality Services - is an optional component</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ac17-113">이 릴리스에서는 설치 중에 **Data Quality Services** 확인란을 선택해도 DQS(Data Quality Services) 서버가 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-113">In this release, selecting the **Data Quality Services** check box in setup does not install the Data Quality Services (DQS) server.</span></span> <span data-ttu-id="8ac17-114">DQS 서버를 설치하려면 추가적인 사후 설치 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-114">You will have to perform additional steps post installation to install DQS server.</span></span> <span data-ttu-id="8ac17-115">자세한 내용은 [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ac17-115">For more information, see [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).</span></span>  
  
 <span data-ttu-id="8ac17-116">일반적인 여러 사용자 시나리오에서 다음과 같은 추가 기능이 옵션으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-116">The following additional features are options for many typical user scenarios:</span></span>  
  
-   <span data-ttu-id="8ac17-117">Data Quality 클라이언트</span><span class="sxs-lookup"><span data-stu-id="8ac17-117">Data Quality Client</span></span>  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   <span data-ttu-id="8ac17-118">연결 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8ac17-118">Connectivity components</span></span>  
  
-   <span data-ttu-id="8ac17-119">프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="8ac17-119">Programming models</span></span>  
  
-   <span data-ttu-id="8ac17-120">관리 도구</span><span class="sxs-lookup"><span data-stu-id="8ac17-120">Management tools</span></span>  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   <span data-ttu-id="8ac17-121">설명서 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8ac17-121">Documentation components</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ac17-122">기본적으로 예제 데이터베이스와 예제 코드는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 일부로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ac17-122">By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="8ac17-123">예제 데이터베이스와 예제 코드를 설치하려면 [CodePlex 웹 사이트](https://go.microsoft.com/fwlink/?LinkId=87843)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ac17-123">To install sample databases and sample code, see the [CodePlex Web site](https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac17-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ac17-124">See Also</span></span>  
 <span data-ttu-id="8ac17-125">[SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="8ac17-125">[Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="8ac17-126">[SQL Server 2014의 버전 및 구성 요소](../../sql-server/editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="8ac17-126">[Editions and Components of SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="8ac17-127">[SQL Server 설치 계획](../../sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="8ac17-127">[Planning a SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 <span data-ttu-id="8ac17-128">[고가용성 솔루션&#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8ac17-128">[High Availability Solutions &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md) </span></span>  
 [<span data-ttu-id="8ac17-129">설치 마법사 &#40;사용 하 여 SQL Server 2014로 업그레이드&#41;</span><span class="sxs-lookup"><span data-stu-id="8ac17-129">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
