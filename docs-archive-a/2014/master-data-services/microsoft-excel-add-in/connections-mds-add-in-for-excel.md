---
title: 연결(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d4dc41afc6dd59cade9e75475c7cb914d14a8937
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638884"
---
# <a name="connections-mds-add-in-for-excel"></a><span data-ttu-id="cd4fd-102">연결(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="cd4fd-102">Connections (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="cd4fd-103">데이터를 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에 다운로드하려면 먼저 연결을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-103">To download data in to the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must first create a connection.</span></span> <span data-ttu-id="cd4fd-104">연결은 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 웹 서비스가 연결할 MDS 데이터베이스를 확인하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-104">A connection is how the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web service knows which MDS database to connect to.</span></span>  
  
 <span data-ttu-id="cd4fd-105">연결 문자열은 일반적으로 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 URL입니다(예: http://contoso/mds).</span><span class="sxs-lookup"><span data-stu-id="cd4fd-105">The connection string is usually the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
 <span data-ttu-id="cd4fd-106">Excel을 시작할 때마다 MDS 저장소에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-106">Each time you start Excel, you must connect to an MDS repository.</span></span> <span data-ttu-id="cd4fd-107">이에 대한 유일한 예외는 활성 스프레드시트에 이미 MDS 관리 데이터가 포함된 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-107">The only exception is when the active spreadsheet already contains MDS-managed data.</span></span> <span data-ttu-id="cd4fd-108">이 경우 사용자가 새로 고치거나 시트의 데이터를 게시할 때마다 연결이 자동으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-108">In this case, a connection is automatically made each time you refresh or publish data in the sheet.</span></span>  
  
 <span data-ttu-id="cd4fd-109">여러 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-109">You can create multiple connections.</span></span> <span data-ttu-id="cd4fd-110">가장 최근에 액세스한 연결은 기본값으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-110">The most recently-accessed connection is considered the default.</span></span>  
  
 <span data-ttu-id="cd4fd-111">여러 사용자가 동시에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-111">Multiple users can be connected at the same time.</span></span> <span data-ttu-id="cd4fd-112">하지만 여러 사용자가 동일한 데이터를 게시하려고 시도하면 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-112">However, conflicts can arise when multiple users attempt to publish the same data.</span></span> <span data-ttu-id="cd4fd-113">자세한 내용은 [Excel용 MDS 추가 기능&#41;&#40;게시 데이터 ](overview-importing-data-from-excel-mds-add-in-for-excel.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-113">For more information, see [Publishing Data &#40;MDS Add-in for Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md).</span></span>  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a><span data-ttu-id="cd4fd-114">자동으로 연결 및 자주 사용되는 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="cd4fd-114">Connect Automatically and Load Frequently-Used Data</span></span>  
 <span data-ttu-id="cd4fd-115">항상 동일한 서버에 연결하고 동일한 데이터 집합을 로드하려는 경우 연결 및 필터 정보를 포함하는 바로 가기 쿼리 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-115">If you want to always connect to the same server and load the same set of data, you can create shortcut query files, which contain connection and filter information.</span></span> <span data-ttu-id="cd4fd-116">쿼리 파일에 대한 자세한 내용은 [바로 가기 쿼리 파일&#40;Excel용 MDS 추가 기능&#41;](shortcut-query-files-mds-add-in-for-excel.md)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-116">For more information about query files, see [Shortcut Query Files &#40;MDS Add-in for Excel&#41;](shortcut-query-files-mds-add-in-for-excel.md).</span></span>  
  
## <a name="data-quality-services"></a><span data-ttu-id="cd4fd-117">데이터베이스 엔진 서비스</span><span class="sxs-lookup"><span data-stu-id="cd4fd-117">Data Quality Services</span></span>  
 <span data-ttu-id="cd4fd-118">[!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 에는 데이터를 MDS 저장소에 게시하기 전에 일치하는지 확인할 수 있게 해주는 Data Quality Services 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-118">The [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] has Data Quality Services functionality to help you match data before publishing it to the MDS repository.</span></span> <span data-ttu-id="cd4fd-119">연결을 설정할 때는 DQS 데이터베이스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 동일 인스턴스에 MDS 데이터베이스로 설치된 경우 리본 메뉴에 DQS 단추를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-119">When you make a connection, if a DQS database is installed on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] as the MDS database, you will be able to view DQS buttons on the ribbon.</span></span> <span data-ttu-id="cd4fd-120">DQS_Main 데이터베이스가 인스턴스에 없으면 이러한 단추가 표시되지 않으며 데이터 품질 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-120">If the DQS_Main database does not exist on the instance, these buttons are not displayed and data quality functionality is not available.</span></span>  
  
## <a name="troubleshooting-connections"></a><span data-ttu-id="cd4fd-121">연결 문제 해결</span><span class="sxs-lookup"><span data-stu-id="cd4fd-121">Troubleshooting Connections</span></span>  
 <span data-ttu-id="cd4fd-122">MDS에 연결 하는 경우 문제가 발생 하면 [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) 문제 해결 팁을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-122">When you connect to MDS, if you encounter any issues see [https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx](https://social.technet.microsoft.com/wiki/contents/articles/4520.aspx) for troubleshooting tips.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="cd4fd-123">관련 작업</span><span class="sxs-lookup"><span data-stu-id="cd4fd-123">Related Tasks</span></span>  
  
|<span data-ttu-id="cd4fd-124">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="cd4fd-124">Task Description</span></span>|<span data-ttu-id="cd4fd-125">항목</span><span class="sxs-lookup"><span data-stu-id="cd4fd-125">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="cd4fd-126">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] 데이터베이스에 대한 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-126">Create a connection to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database.</span></span>|[<span data-ttu-id="cd4fd-127">MDS 리포지토리에 연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="cd4fd-127">Connect to an MDS Repository &#40;MDS Add-in for Excel&#41;</span></span>](connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|<span data-ttu-id="cd4fd-128">MDS 데이터를 Excel로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-128">Load MDS data into Excel.</span></span>|[<span data-ttu-id="cd4fd-129">MDS에서 Excel로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="cd4fd-129">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)|  
|<span data-ttu-id="cd4fd-130">MDS 데이터를 Excel에 로드하기 전에 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="cd4fd-130">Filter MDS data before you load it into Excel.</span></span>|[<span data-ttu-id="cd4fd-131">&#40;Excel용 MDS 추가 기능를 로드 하기 전에 데이터를 필터링&#41;</span><span class="sxs-lookup"><span data-stu-id="cd4fd-131">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="cd4fd-132">관련 내용</span><span class="sxs-lookup"><span data-stu-id="cd4fd-132">Related Content</span></span>  
  
-   [<span data-ttu-id="cd4fd-133">데이터 &#40;Excel용 MDS 추가 기능&#41;로드</span><span class="sxs-lookup"><span data-stu-id="cd4fd-133">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="cd4fd-134">바로 가기 쿼리 파일&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="cd4fd-134">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="cd4fd-135">Microsoft Excel용 Master Data Services 추가 기능</span><span class="sxs-lookup"><span data-stu-id="cd4fd-135">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
