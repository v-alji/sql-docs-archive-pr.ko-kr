---
title: SQL Server 2014로 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server
ms.assetid: 5064e35b-b70d-4a0b-a9e9-fff04162f9d2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 857bbd6d7269b7675653b11a9d7c0acd07927f62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730887"
---
# <a name="upgrade-to-sql-server-2014"></a><span data-ttu-id="78440-102">SQL Server 2014로 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-102">Upgrade to SQL Server 2014</span></span>
  <span data-ttu-id="78440-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]또는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 인스턴스를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78440-103">You can upgrade instances of, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="78440-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램을 실행하여 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]로 업그레이드하기 전에 [SQL Server 2014 업그레이드 기술 가이드](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) (PDF 다운로드), 이 섹션의 업그레이드 프로세스에 대한 항목 및 [SQL Server 2014 릴리스 정보](https://go.microsoft.com/fwlink/?LinkID=296445)를 읽고 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78440-104">Before running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], check out the [SQL Server 2014 Upgrade Technical Guide](https://download.microsoft.com/download/7/1/5/715BDFA7-51B6-4D7B-AF17-61E78C7E538F/SQL_Server_2014_Upgrade_technical_guide.pdf) (PDF download), review the topics about the upgrade process in this section, and read the [SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78440-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="78440-105">In This Section</span></span>  
 <span data-ttu-id="78440-106">이 단원에는 다음 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78440-106">This section contains the following topics:</span></span>  
  
-   [<span data-ttu-id="78440-107">지원되는 버전 및 에디션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-107">Supported Version and Edition Upgrades</span></span>](supported-version-and-edition-upgrades.md)  
  
-   [<span data-ttu-id="78440-108">업그레이드 관리자를 사용하여 업그레이드 준비</span><span class="sxs-lookup"><span data-stu-id="78440-108">Use Upgrade Advisor to Prepare for Upgrades</span></span>](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="78440-109">Distributed Replay Utility를 사용하여 업그레이드 준비</span><span class="sxs-lookup"><span data-stu-id="78440-109">Use the Distributed Replay Utility to Prepare for Upgrades</span></span>](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)  
  
-   [<span data-ttu-id="78440-110">Analysis Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-110">Upgrade Analysis Services</span></span>](upgrade-analysis-services.md)  
  
-   [<span data-ttu-id="78440-111">데이터베이스 엔진 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-111">Upgrade Database Engine</span></span>](upgrade-database-engine.md)  
  
-   [<span data-ttu-id="78440-112">Data Quality Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-112">Upgrade Data Quality Services</span></span>](upgrade-data-quality-services.md)  
  
-   [<span data-ttu-id="78440-113">Integration Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-113">Upgrade Integration Services</span></span>](../../integration-services/install-windows/upgrade-integration-services.md)  
  
-   [<span data-ttu-id="78440-114">Master Data Services 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-114">Upgrade Master Data Services</span></span>](upgrade-master-data-services.md)  
  
-   [<span data-ttu-id="78440-115">SharePoint용 PowerPivot 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-115">Upgrade PowerPivot for SharePoint</span></span>](upgrade-power-pivot-for-sharepoint.md)  
  
-   [<span data-ttu-id="78440-116">복제된 데이터베이스 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-116">Upgrade Replicated Databases</span></span>](../../database-engine/install-windows/upgrade-replicated-databases.md)  
  
-   [<span data-ttu-id="78440-117">Reporting Services 업그레이드 및 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="78440-117">Upgrade and Migrate Reporting Services</span></span>](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
  
-   [<span data-ttu-id="78440-118">SQL Server 관리 도구 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-118">Upgrade SQL Server Management Tools</span></span>](upgrade-sql-server-management-tools.md)  
  
-   [<span data-ttu-id="78440-119">방법 도움말 항목 업그레이드</span><span class="sxs-lookup"><span data-stu-id="78440-119">Upgrade How-to Topics</span></span>](../../../2014/sql-server/install/upgrade-how-to-topics.md)  
  
## <a name="see-also"></a><span data-ttu-id="78440-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="78440-120">See Also</span></span>  
 <span data-ttu-id="78440-121">[데이터베이스 엔진 업그레이드](upgrade-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="78440-121">[Upgrade Database Engine](upgrade-database-engine.md) </span></span>  
 <span data-ttu-id="78440-122">[Analysis Services 업그레이드](upgrade-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="78440-122">[Upgrade Analysis Services](upgrade-analysis-services.md) </span></span>  
 <span data-ttu-id="78440-123">[Reporting Services 업그레이드 및 마이그레이션](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="78440-123">[Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md) </span></span>  
 <span data-ttu-id="78440-124">[Integration Services 업그레이드](../../integration-services/install-windows/upgrade-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="78440-124">[Upgrade Integration Services](../../integration-services/install-windows/upgrade-integration-services.md) </span></span>  
 <span data-ttu-id="78440-125">[복제된 데이터베이스 업그레이드](../../database-engine/install-windows/upgrade-replicated-databases.md) </span><span class="sxs-lookup"><span data-stu-id="78440-125">[Upgrade Replicated Databases](../../database-engine/install-windows/upgrade-replicated-databases.md) </span></span>  
 <span data-ttu-id="78440-126">[Master Data Services 업그레이드](upgrade-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="78440-126">[Upgrade Master Data Services](upgrade-master-data-services.md) </span></span>  
 <span data-ttu-id="78440-127">[SQL Server 2012 모범 사례 분석기](https://www.microsoft.com/download/details.aspx?id=29302) </span><span class="sxs-lookup"><span data-stu-id="78440-127">[SQL Server 2012 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=29302) </span></span>  
 <span data-ttu-id="78440-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span><span class="sxs-lookup"><span data-stu-id="78440-128">[SQL Server 2008 R2 Best Practices Analyzer](https://www.microsoft.com/download/details.aspx?id=436) </span></span>  
 [<span data-ttu-id="78440-129">이전 버전과의 호환성</span><span class="sxs-lookup"><span data-stu-id="78440-129">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
