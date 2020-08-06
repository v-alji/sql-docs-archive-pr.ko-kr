---
title: SharePoint 모드의 Reporting Services에 대 한 하드웨어 및 소프트웨어 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a4fc19b2871d7d5731649c61a8d5231d7e3479dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660317"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="6934b-102">SharePoint 모드의 Reporting Services에 대한 하드웨어 및 소프트웨어 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6934b-102">Hardware and Software Requirements for Reporting Services in SharePoint Mode</span></span>

  <span data-ttu-id="6934b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에서 실행 하기 위한 필수 구성 요소, 하드웨어 요구 사항 및 설치 고려 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-103">This topic describes prerequisites, hardware requirements, and installation considerations for [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode.</span></span> <span data-ttu-id="6934b-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 모드에는 SharePoint 서버가 필요하기 때문에 대부분의 요구 사항은 SharePoint 환경을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-104">Because [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode requires a SharePoint server, most of the requirements are based on the SharePoint environment.</span></span> <span data-ttu-id="6934b-105">기본 모드 보고서 서버의 경우 하드웨어가 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]실행에 필요한 최소 하드웨어 및 소프트웨어 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-105">For native mode report servers, your hardware should meet minimum hardware and software requirements for running [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="6934b-106">자세한 내용은 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6934b-106">For more information, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   [<span data-ttu-id="6934b-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6934b-107">Prerequisites</span></span>](#bkmk_prereq)  
  
-   [<span data-ttu-id="6934b-108">보고서 서버 데이터베이스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6934b-108">Report Server Database Requirements</span></span>](#bkmk_report_server_database)  
  
-   [<span data-ttu-id="6934b-109">Power View 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6934b-109">Power View Requirements</span></span>](#bkmk_powerview)  
  
-   [<span data-ttu-id="6934b-110">추가 정보</span><span class="sxs-lookup"><span data-stu-id="6934b-110">More Information</span></span>](#bkmk_more_information)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> <span data-ttu-id="6934b-111">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6934b-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="6934b-112">로컬 설치의 경우 SharePoint 및 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치 중 로그인된 계정은 로컬 운영 체제의 administrators 그룹의 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-112">For local installations, the account logged in during installation of SharePoint and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] needs to be a member of the administrators group in the local operating system.</span></span> <span data-ttu-id="6934b-113">설치 계정이 SharePoint 팜 관리자 그룹의 구성원이 될 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-113">The setup account does not need to be a member of the SharePoint farm administrators group.</span></span>  
  
     <span data-ttu-id="6934b-114">자세한 내용은 [SharePoint 2013에서의 계정 권한 및 보안 설정](https://technet.microsoft.com/library/cc678863.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6934b-114">For more information, see [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).</span></span>  
  
-   <span data-ttu-id="6934b-115">SharePoint 모드로 실행 중인 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에는 SharePoint Server가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] running in SharePoint mode requires SharePoint Server.</span></span> <span data-ttu-id="6934b-116">SharePoint 요구 사항 및 구성에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6934b-116">For more information about SharePoint requirements and configurations, see the following:</span></span>  
  
    -   <span data-ttu-id="6934b-117">[하드웨어 및 소프트웨어 요구 사항 (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span><span class="sxs-lookup"><span data-stu-id="6934b-117">[Hardware and software requirements (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)</span></span>  
  
    -   [<span data-ttu-id="6934b-118">SharePoint Server 2013의 용량 관리 및 크기 조정</span><span class="sxs-lookup"><span data-stu-id="6934b-118">Capacity management and sizing for SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [<span data-ttu-id="6934b-119">비즈니스 인텔리전스에 대한 소프트웨어 요구 사항(SharePoint 2013)</span><span class="sxs-lookup"><span data-stu-id="6934b-119">Software requirements for business intelligence (SharePoint 2013)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   <span data-ttu-id="6934b-120">[하드웨어 및 소프트웨어 요구 사항(SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="6934b-120">[Hardware and software requirements (SharePoint Server 2010)](https://technet.microsoft.com/library/cc262485\(v=office.14\))</span></span>  
  
    -   <span data-ttu-id="6934b-121">[SharePoint Server 2010의 용량 관리 및 크기 조정](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span><span class="sxs-lookup"><span data-stu-id="6934b-121">[Capacity management and sizing for SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))</span></span>  
  
-   <span data-ttu-id="6934b-122">기존 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 설치를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]으로 업그레이드하거나 업데이트하려는 경우 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)실행에 필요한 최소 하드웨어 및 소프트웨어 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-122">If you want to upgrade or update existing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint installation with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], see [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).</span></span>  
  
-   <span data-ttu-id="6934b-123">**SharePoint 2013 관리** 서비스를 Windows Server Manager에서 시작했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-123">Verify the **SharePoint 2013 Administration** service is started in Windows Server Manager.</span></span>  
  
###  <a name="report-server-database-requirements"></a><a name="bkmk_report_server_database"></a> <span data-ttu-id="6934b-124">보고서 서버 데이터베이스 요구 사항</span><span class="sxs-lookup"><span data-stu-id="6934b-124">Report Server Database Requirements</span></span>  
  
-   <span data-ttu-id="6934b-125">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 와 SharePoint 제품 및 기술은 모두 SQL Server 관계형 데이터베이스를 사용하여 애플리케이션 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-125">Both [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] and SharePoint products and technologies use SQL Server relational databases to store application data.</span></span>  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]<span data-ttu-id="6934b-126">를 사용하려면 호환되는 SQL Server 버전의 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-126">requires an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] of a compatible SQL Server edition.</span></span> <span data-ttu-id="6934b-127">하드웨어 및 소프트웨어 요구 사항에 대한 자세한 내용은 [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6934b-127">For more information on hardware and software requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="6934b-128">SharePoint 제품에서는 기존 데이터베이스 인스턴스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-128">SharePoint products can use an existing database instance.</span></span> <span data-ttu-id="6934b-129">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 인스턴스가 설치되지 않은 경우 SharePoint 제품 설치 프로그램은 SharePoint 애플리케이션 데이터베이스에 대해 SQL Server Express Edition을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-129">If an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] is not installed, the SharePoint Products Setup program installs SQL Server Express Edition for the SharePoint application databases.</span></span>  
  
-   <span data-ttu-id="6934b-130">보고서 서버 인스턴스는 SQL Server Express Edition을 데이터베이스로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-130">The report server instance cannot use the SQL Server Express Edition for its database.</span></span> <span data-ttu-id="6934b-131">그러나 SharePoint 제품에 의해 설치된 SQL Server Express Edition 인스턴스는 다른 데이터베이스 엔진 버전과 함께 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-131">However, the SQL Server Express Edition instance installed by the SharePoint product can exist side-by-side with other Database Engine editions.</span></span>  
  
##  <a name="sscrescent-requirements"></a><a name="bkmk_powerview"></a><span data-ttu-id="6934b-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]요구 사항</span><span class="sxs-lookup"><span data-stu-id="6934b-132">[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Requirements</span></span>

 <span data-ttu-id="6934b-133">Office.Microsoft.com에서 최신 [Power View 설명서](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6934b-133">Review the most up-to-date [Power View documentation](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) on Office.Microsoft.com.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]<span data-ttu-id="6934b-134">는 Microsoft Excel 2013의 기능이며, Microsoft SharePoint Server 2010 및 2013 Enterprise Edition용 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services 추가 기능의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="6934b-134">is a feature of Microsoft Excel 2013, and is part of the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services add-in for Microsoft SharePoint Server 2010 and 2013 Enterprise Editions.</span></span>  
  
##  <a name="more-information"></a><a name="bkmk_more_information"></a> <span data-ttu-id="6934b-135">자세한 정보</span><span class="sxs-lookup"><span data-stu-id="6934b-135">More Information</span></span>

 <span data-ttu-id="6934b-136">SharePoint 변경 내용에 대 한 자세한 내용은 [sharepoint 2010에서 sharepoint 2013로 변경](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) ()을 참조 하세요 https://technet.microsoft.com/library/ff607742(office.15).aspx) .</span><span class="sxs-lookup"><span data-stu-id="6934b-136">For information on SharePoint changes, see [Changes from SharePoint 2010 to SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).</span></span>  
  
 <span data-ttu-id="6934b-137">[SQL Server 2014 릴리스 정보](https://go.microsoft.com/fwlink/?LinkID=296445)</span><span class="sxs-lookup"><span data-stu-id="6934b-137">[SQL Server 2014 Release Notes](https://go.microsoft.com/fwlink/?LinkID=296445).</span></span>  
  
