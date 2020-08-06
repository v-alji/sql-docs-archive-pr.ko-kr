---
title: 지도 보고서 지원 계획 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3d1e1774e44ae879b8c01e66289cefd4d42ee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739496"
---
# <a name="plan-for-map-report-support"></a><span data-ttu-id="6a597-102">지도 보고서 지원 계획</span><span class="sxs-lookup"><span data-stu-id="6a597-102">Plan for Map Report Support</span></span>
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]<span data-ttu-id="6a597-103">에서는 공간 데이터 원본을 사용 하는 지도 보고서를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-103">supports map reports that use spatial data sources.</span></span> <span data-ttu-id="6a597-104">공간 데이터는 SQL Server 데이터베이스, ESRI 셰이프 파일 또는 Reporting Services나 보고서 작성기에 설치된 지도 갤러리에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-104">Spatial data can come from SQL Server databases, from ESRI Shapefiles, or from the Map Gallery that is installed with either Reporting Services or Report Builder.</span></span> <span data-ttu-id="6a597-105">지도에 Bing 지도 타일 배경을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-105">A map can also display a background of Bing map tiles.</span></span> <span data-ttu-id="6a597-106">보고서 작성자는 공간 데이터나 Bing 지도 타일을 런타임에 검색되는 동적 스타일 또는 보고서 정의에 포함된 정적 스타일로 지정하는 보고서를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-106">A report author can create a report that specifies spatial data or Bing map tiles as dynamic and retrieved at run time or as static and embedded in the report definition.</span></span>  
  
## <a name="support-for-bing-maps"></a><span data-ttu-id="6a597-107">Bing Maps 지원</span><span class="sxs-lookup"><span data-stu-id="6a597-107">Support for Bing Maps</span></span>  
 <span data-ttu-id="6a597-108">지도는 Bing 지도 타일을 표시하는 배경 계층을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-108">Maps can include a background layer that displays Bing map tiles.</span></span> <span data-ttu-id="6a597-109">지도 타일 계층을 포함하는 게시된 보고서를 보려면 보고서 서버가 Bing Maps 웹 서비스에서 타일을 검색하도록 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-109">To view a published report that has a map tile layer, the report server must be configured to retrieve tiles from Bing Maps Web Services.</span></span> <span data-ttu-id="6a597-110">자세한 내용은 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6a597-110">For more information, see [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).</span></span>  
  
 <span data-ttu-id="6a597-111">보고서 작성자는 각 보고서에서 SSL(Secure Sockets Layer) 연결을 사용하여 타일 서버에서 타일을 검색할지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-111">In each report, report authors can specify whether to use a Secure Sockets Layer (SSL) connection to retrieve tiles from the tile server.</span></span> <span data-ttu-id="6a597-112">이렇게 하려면 타일 계층의 속성 창에서 부울 속성 UseSecureConnection을로 설정 해야 합니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="6a597-112">To do this, in the Properties pane for the tile layer, they must set the Boolean property UseSecureConnection to `true`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6a597-113"> 보고서에서 Bing 지도 타일을 사용하는 방법은 [추가 사용 조건(Additional Terms of Use)](https://go.microsoft.com/fwlink/?LinkId=151371) 및 [개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=151372)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6a597-113">For more information about the use of Bing map tiles in your report, see [Additional Terms of Use](https://go.microsoft.com/fwlink/?LinkId=151371) and [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=151372).</span></span>  
  
## <a name="report-design-recommendations"></a><span data-ttu-id="6a597-114">보고서 디자인 권장 구성</span><span class="sxs-lookup"><span data-stu-id="6a597-114">Report Design Recommendations</span></span>  
 <span data-ttu-id="6a597-115">지도 보고서를 효과적으로 디자인하려면 보고서 작성자가 정적 공간 데이터와 동적 공간 데이터의 장단점을 평가하고 보고서 사용자를 위해 균형점을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-115">Good report design for map reports requires that the report author assess the trade-offs between static and dynamic spatial data and find a balance that serves the report users.</span></span> <span data-ttu-id="6a597-116">포함된 지도 요소를 사용하면 보고서 정의의 크기가 매우 증가할 수 있지만 지도 보고서를 보는 데 필요한 시간을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-116">Embedded map elements can significantly increase the size of the report definition, but reduce the time that is required to view the map report.</span></span> <span data-ttu-id="6a597-117">동적 지도 요소를 사용하면 보고서 정의의 크기는 줄일 수 있지만 지도를 처리하고 보는 데 필요한 시간이 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-117">Dynamic map elements reduce the report definition size but increase the time that is required to process and view the map.</span></span> <span data-ttu-id="6a597-118">보고서 작성자는 이렇게 서로 반대되는 문제점을 고려하여 적절한 균형점을 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-118">The report author must find the right balance between these opposing issues.</span></span>  
  
 <span data-ttu-id="6a597-119">보고서 서버 관리자로서 보고서 정의 크기가 문제가 되면 보고서 정의의 공간 데이터 양을 줄이도록 보고서 디자이너에게 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-119">When report definition size is an issue, as report server administrator, you can encourage report designers to reduce the amount of spatial data in a report definition.</span></span>  
  
 <span data-ttu-id="6a597-120">다음과 같은 경우 지도 요소가 보고서 정의에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-120">Under the following conditions, map elements are embedded in the report definition:</span></span>  
  
-   <span data-ttu-id="6a597-121">보고서를 만들 때 공간 데이터 원본이 로컬 파일 시스템에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-121">When the report is created, the spatial data source is on the local file system.</span></span> <span data-ttu-id="6a597-122">여기에는 로컬에 설치된 ESRI 셰이프 파일 또는 지도 갤러리의 공간 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-122">This includes spatial data from the Map Gallery or ESRI Shapefiles that have been installed locally.</span></span> <span data-ttu-id="6a597-123">기본적으로 지도 마법사와 지도 계층 마법사는 로컬 파일 시스템에 있는 데이터 원본의 공간 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-123">By default, the map wizard and map layer wizard embed spatial data from data sources on the local file system.</span></span>  
  
-   <span data-ttu-id="6a597-124">보고서 작성자가 공간 데이터를 수동으로 보고서에 포함하는 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-124">The report author chooses the option to embed spatial data manually in the report.</span></span>  
  
 <span data-ttu-id="6a597-125">지도를 포함하는 보고서 정의의 크기를 줄이기 위해 보고서 작성자는 다음과 같은 옵션을 하나 이상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-125">To help reduce the size of report definitions that have maps, report authors can use one or more of the following options:</span></span>  
  
-   <span data-ttu-id="6a597-126">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]의 보고서 디자이너에서 공간 데이터 원본, 즉 ESRI 셰이프 파일을 보고서 서버 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-126">From Report Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], add spatial data sources that are ESRI Shapefiles to the report server project.</span></span> <span data-ttu-id="6a597-127">프로젝트를 배포하면 보고서와 함께 ESRI 셰이프 파일이 보고서 서버에 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-127">When you deploy the project, the ESRI Shapefiles are published to the report server in addition to the report.</span></span> <span data-ttu-id="6a597-128">보고서 작성자가 지도 마법사를 실행하면 보고서 서버 프로젝트에서 공간 데이터 원본을 지정할 수 있으며 기본적으로 지도 요소는 보고서 정의에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-128">When the report author runs the Map wizard, they can specify a spatial data source from the Report Server project, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="6a597-129">보고서 작성기를 실행한 후 보고서 서버에서 셰이프 파일을 선택하여 공간 데이터 원본, 즉 ESRI 셰이프 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-129">From Report Builder, add spatial data sources that are ESRI Shapefiles by selecting Shapefiles from the report server.</span></span> <span data-ttu-id="6a597-130">보고서 작성자가 지도 마법사를 실행하면 보고서 서버에서 공간 데이터 원본을 찾아 선택할 수 있으며 기본적으로 지도 요소는 보고서 정의에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-130">When the report author runs the Map wizard, they can browse to and select a spatial data source from the report server, and the map elements are not embedded in the report definitions by default.</span></span>  
  
-   <span data-ttu-id="6a597-131">지도 데이터가 포함되어 있어야 할 경우에는 보고서에 필요한 지도 데이터만 포함되도록 뷰포트 중심 및 확대/축소 수준을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a597-131">When map data must be embedded map data, adjust the viewport center and zoom level to include just the map data that is needed for the report.</span></span>  
  
 <span data-ttu-id="6a597-132">자세한 내용은 [&#40;보고서 작성기 및 SSRS&#41;를 매핑합니다 ](report-design/maps-report-builder-and-ssrs.md).</span><span class="sxs-lookup"><span data-stu-id="6a597-132">For more information, [Maps &#40;Report Builder and SSRS&#41;](report-design/maps-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a597-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a597-133">See Also</span></span>  
 [<span data-ttu-id="6a597-134">보고서 문제 해결: 맵 보고서&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6a597-134">Troubleshoot Reports: Map Reports &#40;Report Builder and SSRS&#41;</span></span>](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
