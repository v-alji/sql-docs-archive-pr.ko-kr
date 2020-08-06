---
title: PowerPivot 데이터 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 83dc82da-91fb-4e47-91a8-0e0db67339b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8faeec7b2e12871467b93f136360e9a68a0e5acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659663"
---
# <a name="powerpivot-data-access"></a><span data-ttu-id="895e8-102">PowerPivot 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="895e8-102">PowerPivot Data Access</span></span>
  <span data-ttu-id="895e8-103">이 항목에서는 Sharepoint 라이브러리에 게시되는 PowerPivot 통합 문서에서 데이터를 검색하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-103">This topic describes the ways in which data is retrieved from a PowerPivot workbook that is published to a SharePoint library.</span></span>  
  
 <span data-ttu-id="895e8-104">PowerPivot 데이터는 Excel 통합 문서 내에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-104">PowerPivot data is stored inside an Excel workbook.</span></span> <span data-ttu-id="895e8-105">연결 문자열은 SharePoint 사이트에 있는 통합 문서에 대한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-105">The connection string is a URL to a workbook on a SharePoint site.</span></span>  
  
 <span data-ttu-id="895e8-106">PowerPivot 데이터는 주로 데이터가 포함된 통합 문서에서 피벗 테이블 및 피벗 차트의 데이터로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-106">PowerPivot data is most often used by the workbook that contains it, as the data behind PivotTables and PivotCharts.</span></span> <span data-ttu-id="895e8-107">PowerPivot 데이터를 외부 데이터 원본으로 사용할 수도 있습니다. 그러면 통합 문서, 대시보드 또는 보고서에서 SharePoint의 개별 Excel 파일(.xlsx)에 연결하여 나중에 사용할 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-107">Alternatively, PowerPivot data can also be used as an external data source, where a workbook, dashboard, or report connects to a separate Excel (.xlsx) file in SharePoint and retrieves the data for subsequent use.</span></span> <span data-ttu-id="895e8-108">일반적으로 PowerPivot 데이터를 사용하는 클라이언트 도구는 Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], 기타 Reporting Services 보고서 및 PerformancePoint입니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-108">Client tools that typically use PowerPivot data are Excel, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], other Reporting Services reports, and PerformancePoint.</span></span>  
  
 <span data-ttu-id="895e8-109">데스크톱에서는 PowerPivot 추가 기능에서 AMO 및 ADOMD.NET을 사용하여 클라이언트 작업 영역에서 PowerPivot 데이터를 생성, 처리 및 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-109">On the desktop, the PowerPivot add-in uses AMO and ADOMD.NET to create, process, and query the PowerPivot data in the client workspace.</span></span>  
  
 <span data-ttu-id="895e8-110">SharePoint 팜에서는 Excel 서비스에서 로컬 MSOLAP OLE DB Provider를 사용하여 PowerPivot 데이터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-110">On a SharePoint farm, Excel Services uses the local MSOLAP OLE DB provider to connect to PowerPivot data.</span></span> <span data-ttu-id="895e8-111">공급자는 팜의 SharePoint용 PowerPivot 서버에 연결 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-111">The provider sends the connection request to a PowerPivot for SharePoint server in the farm.</span></span> <span data-ttu-id="895e8-112">서버는 데이터를 로드하고 쿼리를 실행한 다음 결과 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-112">That server loads the data, runs the query, and returns the result set.</span></span>  
  
##  <a name="querying-powerpivot-data-in-sharepoint"></a><a name="queryproc"></a><span data-ttu-id="895e8-113">SharePoint에서 PowerPivot 데이터 쿼리</span><span class="sxs-lookup"><span data-stu-id="895e8-113">Querying PowerPivot Data in SharePoint</span></span>  
 <span data-ttu-id="895e8-114">SharePoint 라이브러리에서 PowerPivot 통합 문서를 볼 때 통합 문서 내에 있는 PowerPivot 데이터는 팜 내의 Analysis Services 서버 인스턴스에서 별도로 검색, 추출 및 처리됩니다. 반면 Excel 서비스는 표시 계층을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-114">When you view a PowerPivot workbook from a SharePoint library, the PowerPivot data that is inside the workbook is detected, extracted, and processed separately on Analysis Services server instances within the farm, while Excel Services renders the presentation layer.</span></span> <span data-ttu-id="895e8-115">브라우저 창이나 PowerPivot 추가 기능이 있는 Excel 2010 데스크톱 애플리케이션에서 완전히 처리된 통합 문서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-115">You can view the fully-processed workbook in a browser window or in an Excel 2010 desktop application that has the PowerPivot add-in.</span></span>  
  
 <span data-ttu-id="895e8-116">다음 다이어그램에서는 쿼리 처리에 대한 요청이 팜을 통해 이동하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-116">The following diagram shows how a request for query processing moves through the farm.</span></span> <span data-ttu-id="895e8-117">PowerPivot 데이터는 Excel 2010 통합 문서의 일부이므로 사용자가 SharePoint 라이브러리에서 Excel 통합 문서를 열고 PowerPivot 데이터가 포함된 피벗 테이블이나 피벗 차트와 상호 작용하면 쿼리 처리 요청이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-117">Because PowerPivot data is part of an Excel 2010 workbook, a request for query processing occurs when a user opens an Excel workbook from a SharePoint library and interacts with a PivotTable or PivotChart that contains PowerPivot data.</span></span>  
  
 <span data-ttu-id="895e8-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span><span class="sxs-lookup"><span data-stu-id="895e8-118">![GMNI_DataProcReq](../media/gmni-dataprocreq.gif "GMNI_DataProcReq")</span></span>  
  
 <span data-ttu-id="895e8-119">Excel 서비스와 PowerPivot for SharePoint 구성 요소는 동일한 통합 문서 파일(.xlsx)의 서로 다른 부분을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-119">Excel Services and PowerPivot for SharePoint components process different parts of the same workbook (.xlsx) file.</span></span> <span data-ttu-id="895e8-120">Excel 서비스는 팜의 PowerPivot 서버에서 PowerPivot 데이터 및 처리 요청을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-120">Excel Services detects PowerPivot data and requests processing from a PowerPivot server in the farm.</span></span> <span data-ttu-id="895e8-121">PowerPivot 서버는 콘텐츠 라이브러리의 통합 문서에서 데이터를 추출하고 데이터를 로드하는 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 인스턴스에 요청을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-121">The PowerPivot server allocates the request to an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance, which extracts the data from the workbook in the content library and loads the data.</span></span> <span data-ttu-id="895e8-122">메모리에 저장되어 있는 데이터는 렌더링된 통합 문서에 다시 병합되고 브라우저 창에서 표시하기 위해 Excel 웹 액세스로 다시 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-122">Data that is stored in memory is merged back into the rendered workbook, and passed back to Excel Web Access for presentation in a browser window.</span></span>  
  
 <span data-ttu-id="895e8-123">PowerPivot 통합 문서의 모든 데이터가 PowerPivot for SharePoint에 의해 처리되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-123">Not all data in a PowerPivot workbook is handled by PowerPivot for SharePoint.</span></span> <span data-ttu-id="895e8-124">Excel 서비스는 워크시트의 테이블 및 셀 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-124">Excel Services processes tables and cell data in a worksheet.</span></span> <span data-ttu-id="895e8-125">PowerPivot 데이터에 대한 피벗 테이블, 피벗 차트 및 슬라이서만이 SharePoint용 PowerPivot에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="895e8-125">Only PivotTables, PivotCharts, and Slicers that go against PowerPivot data are handled by the PowerPivot for SharePoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895e8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="895e8-126">See Also</span></span>  
 <span data-ttu-id="895e8-127">[Analysis Services에 연결](../instances/connect-to-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="895e8-127">[Connect to Analysis Services](../instances/connect-to-analysis-services.md) </span></span>  
 [<span data-ttu-id="895e8-128">테이블 형식 모델 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="895e8-128">Tabular Model Data Access</span></span>](../tabular-models/tabular-model-data-access.md)  
  
  
