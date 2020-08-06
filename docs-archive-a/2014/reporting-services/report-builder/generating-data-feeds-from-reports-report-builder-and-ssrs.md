---
title: 보고서에서 데이터 피드 만들기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4e00789f-6967-42e5-b2b4-03181fdb1e2c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7f999560bf3216ea84c672c733539d2cad44a15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648841"
---
# <a name="generating-data-feeds-from-reports-report-builder-and-ssrs"></a><span data-ttu-id="d7178-102">보고서에서 데이터 피드 만들기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="d7178-102">Generating Data Feeds from Reports (Report Builder and SSRS)</span></span>
  <span data-ttu-id="d7178-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom 렌더링 확장 프로그램은 보고서에서 사용할 수 있는 데이터 피드와 보고서의 데이터 영역에서 사용할 수 있는 데이터 피드를 나열하는 Atom 서비스 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-103">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Atom rendering extension generates an Atom service document that lists the data feeds available from a report and the data feeds from the data regions in a report.</span></span> <span data-ttu-id="d7178-104">이 확장 프로그램을 사용하면 보고서에서 생성된 데이터 피드를 사용할 수 있는 애플리케이션을 사용하여 읽을 수 있고 교환할 수 있는 Atom 규격 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-104">You use this extension to generate Atom-compliant data feeds that are readable and exchangeable with applications that can consume data feeds generated from reports.</span></span> <span data-ttu-id="d7178-105">예를 들어 Atom 렌더링 확장 프로그램을 사용 하 여 클라이언트에서 사용할 수 있는 데이터 피드를 생성할 수 있습니다 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d7178-105">For example, you can use the Atom rendering extension to generated data feeds that you can then use in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] client.</span></span>  
  
 <span data-ttu-id="d7178-106">Atom 서비스 문서는 보고서의 각 데이터 영역에 대해 데이터 피드를 하나 이상 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-106">The Atom service document lists at least one data feed for each data region in a report.</span></span> <span data-ttu-id="d7178-107">데이터 영역의 유형과 데이터 영역에 표시되는 데이터에 따라 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 는 데이터 영역에서 여러 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-107">Depending on the type of data region and the data that the data region displays, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] might generate multiple data feeds from a data region.</span></span> <span data-ttu-id="d7178-108">예를 들어 행렬이나 차트는 여러 데이터 피드를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-108">For example, a matrix or chart can provide multiple data feeds.</span></span> <span data-ttu-id="d7178-109">Atom 렌더링 확장 프로그램이 Atom 서비스 문서를 만드는 경우 고유 식별자가 각 데이터 피드에 대해 만들어지며 URL에서 이 식별자를 사용하여 데이터 피드의 내용에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-109">When the Atom rendering extension creates the Atom service document, a unique identifier is created for each data feed and you use the identifier in the URL to access the content of the data feed.</span></span>  
  
 <span data-ttu-id="d7178-110">Atom 렌더링 확장 프로그램이 데이터 피드에 대한 데이터를 생성하는 방식은 CSV(쉼표로 구분된 값) 렌더링 확장이 CSV 파일에 데이터를 렌더링하는 방식과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-110">The way that the Atom rendering extension generates data for a data feed is similar to how the Comma-Separated Value (CSV) rendering extension renders data to a CSV file.</span></span> <span data-ttu-id="d7178-111">CSV 파일과 마찬가지로 데이터 피드는 보고서 데이터의 일반 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-111">Like a CSV file, a data feed is a flattened representation of the report data.</span></span> <span data-ttu-id="d7178-112">예를 들어 그룹 내의 판매량 합계를 계산하는 행 그룹이 있는 테이블은 각 데이터 행에서 합계를 계산하는 작업을 반복하며 별도의 행에 합계만 포함되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-112">For example, a table with a row group that sums the sales within a group repeats the sum in every data row and there is no separate row that contains only the sum.</span></span>  
  
 <span data-ttu-id="d7178-113">보고서 관리자, 보고서 서버 또는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]와 통합된 SharePoint 사이트를 사용하여 Atom 서비스 문서와 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-113">You can generate Atom service documents and data feeds using Report Manager, Report Server, or a SharePoint site that is integrated with [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d7178-114">Atom은 관련 표준의 쌍에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-114">Atom applies to a pair of related standards.</span></span> <span data-ttu-id="d7178-115">Atom 서비스 문서는 RFC 5023 Atom 게시 프로토콜 사양을 따르며 데이터 피드는 RFC 4287 Atom 배포 형식 프로토콜 사양을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-115">The Atom service document conforms to the RFC 5023 Atom publishing protocol specification and the data feeds conform to the RFC 4287 Atom syndication format protocol specification.</span></span>  
  
 <span data-ttu-id="d7178-116">다음 섹션에서는 Atom 렌더링 확장 프로그램을 사용하는 방법에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-116">The following sections provide additional information about how to use the Atom rendering extension:</span></span>  
  
 [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="reports-as-data-feeds"></a><a name="ReportDataAsDataFeeds"></a> <span data-ttu-id="d7178-117">데이터 피드로 보고서 사용</span><span class="sxs-lookup"><span data-stu-id="d7178-117">Reports as Data Feeds</span></span>  
 <span data-ttu-id="d7178-118">프로덕션 보고서를 데이터 피드로 내보내거나 기본 목적이 애플리케이션에 데이터를 제공하는 것인 보고서를 데이터 피드 형태로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-118">You can export a production report as a data feed or you can create a report whose primary purpose is provide data, in the form of data feeds, to applications.</span></span> <span data-ttu-id="d7178-119">보고서를 데이터 피드로 사용하는 것은 클라이언트 데이터 공급자를 통해 데이터에 액세스하기가 쉽지 않은 경우나 데이터 원본의 복잡성을 숨기고 데이터를 더 간단하게 사용하게 하려는 경우 애플리케이션에 데이터를 제공하는 또 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-119">Using reports as a data feed gives you an additional way to provide data to applications when the data is not easy to access through client data providers, or when you prefer to hide the complexity of the data source and make it simpler to use the data.</span></span> <span data-ttu-id="d7178-120">보고서 데이터를 데이터 피드로 사용하는 경우 보고서 관리자, 보안, 예약 및 보고서 스냅샷과 같은 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기능을 사용하여 데이터 피드를 제공하는 보고서를 관리할 수 있다는 추가적인 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-120">Another benefit of using report data as a data feed is that you can use [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] features such as Report Manager, security, scheduling, and report snapshots to manage the reports that provide data feeds.</span></span>  
  
 <span data-ttu-id="d7178-121">Atom 렌더링 확장 프로그램을 최대한 활용하려면 보고서가 데이터 피드로 렌더링되는 방식을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-121">To get the most from the Atom rendering extension, you should understand how the report is rendered into data feeds.</span></span> <span data-ttu-id="d7178-122">기존 보고서를 사용하는 경우 보고서에서 생성할 데이터 피드를 예측할 수 있으면 유용합니다. 데이터 피드로 특별히 사용하기 위해 보고서를 작성하는 경우에는 데이터 피드의 유용성을 최대화하기 위해 데이터를 포함하고 보고서 레이아웃을 조정할 수 있으면 크게 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-122">If you are using existing reports, being able to predict what the data feeds the reports will generate is useful; if you are writing report specifically for use as data feeds, being able to include the data and fine tune the report layout to maximize the usefulness of the data feeds is valuable.</span></span>  
  
 <span data-ttu-id="d7178-123">자세한 내용은 [보고서에서 데이터 피드 생성 &#40;보고서 작성기 및 SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d7178-123">For more information, see [Generate Data Feeds from a Report &#40;Report Builder and SSRS&#41;](generate-data-feeds-from-a-report-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-service-document-atomsvc-file"></a><a name="AtomServiceDocument"></a> <span data-ttu-id="d7178-124">Atom 서비스 문서(.atomsvc 파일)</span><span class="sxs-lookup"><span data-stu-id="d7178-124">Atom Service Document (.atomsvc file)</span></span>  
 <span data-ttu-id="d7178-125">Atom 서비스 문서는 하나 이상의 데이터 피드에 대한 연결을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-125">An Atom service document specifies a connection to one or more data feeds.</span></span> <span data-ttu-id="d7178-126">최소한 연결은 피드를 생성하는 데이터 서비스에 대한 간단한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-126">At a minimum, the connection is a simple URL to the data service that produces the feed.</span></span>  
  
 <span data-ttu-id="d7178-127">Atom 렌더링 확장 프로그램을 사용하여 보고서 데이터를 렌더링하는 경우 Atom 서비스 문서는 보고서에 사용할 수 있는 데이터 피드를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-127">When you render report data by using the Atom rendering extension, the Atom service document lists the data feeds available for a report.</span></span> <span data-ttu-id="d7178-128">이 문서는 보고서의 각 데이터 영역에 대한 데이터 피드를 하나 이상 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-128">The document lists at least one data feed for each data region in the report.</span></span> <span data-ttu-id="d7178-129">테이블과 계기는 각각 데이터 피드를 하나만 생성하지만 행렬, 목록 및 차트는 표시하는 데이터에 따라 여러 데이터 피드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-129">Tables and gauges generate only one data feed each, but matrices, lists, and charts might generated multiple depending on the data they display.</span></span>  
  
 <span data-ttu-id="d7178-130">다음 다이어그램에서는 테이블 두 개와 차트 한 개를 사용하는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-130">The following diagram shows a report that uses two tables and a chart.</span></span>  
  
 <span data-ttu-id="d7178-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="d7178-131">![RS_Atom_TableAndChartDataFeeds](../media/rs-atom-tableandchartdatafeeds.gif "RS_Atom_TableAndChartDataFeeds")</span></span>  
  
 <span data-ttu-id="d7178-132">이 보고서에서 생성된 Atom 서비스 문서는 세 가지 데이터 피드(각 테이블에 대한 데이터 피드와 차트에 대한 데이터 피드)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-132">The Atom service document generated from this report includes three data feeds, one for each table and one for the chart.</span></span>  
  
 <span data-ttu-id="d7178-133">행렬 데이터 영역에는 행렬의 구조에 따라 데이터 피드가 두 개 이상 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-133">The matrix data regions might have more than one data feed, depending on the structure of the matrix.</span></span> <span data-ttu-id="d7178-134">다음 다이어그램에서는 두 가지 데이터 피드를 생성하는 행렬을 사용하는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-134">The following diagram shows a report that uses a matrix that generates two data feeds.</span></span>  
  
 <span data-ttu-id="d7178-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span><span class="sxs-lookup"><span data-stu-id="d7178-135">![RS_Atom_PeerDynamicColumns](../media/rs-atom-peerdynamiccolumns.gif "RS_Atom_PeerDynamicColumns")</span></span>  
  
 <span data-ttu-id="d7178-136">이 보고서에서 생성된 Atom 서비스 문서는 각 동적 피어 열에 대한 데이터 피드 즉, 지역 및 연도의 두 가지 데이터 피드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-136">The Atom service document generated from this report includes two data feeds, one for each of the dynamic peer columns: Territory and Year.</span></span> <span data-ttu-id="d7178-137">다음 다이어그램에서는 각 데이터 피드의 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-137">The following diagram shows the content of each data feed.</span></span>  
  
 <span data-ttu-id="d7178-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span><span class="sxs-lookup"><span data-stu-id="d7178-138">![RS_Atom_PeerDynamicDataFeeds](../media/rs-atom-peerdynamicdatafeeds.gif "RS_Atom_PeerDynamicDataFeeds")</span></span>  
  

  
##  <a name="data-feeds"></a><a name="DataFeeds"></a> <span data-ttu-id="d7178-139">데이터 피드</span><span class="sxs-lookup"><span data-stu-id="d7178-139">Data Feeds</span></span>  
 <span data-ttu-id="d7178-140">데이터 피드는 보고서가 실행될 때마다 다를 수 있는 변수 데이터와 시간이 흐름에 따라 변경되지 않는 일관성 있는 표 형식이 있는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-140">The data feed is an XML file that has a consistent tabular format that does not change over time and variable data that can be different each time the report is run.</span></span> <span data-ttu-id="d7178-141">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 에서 생성하는 데이터 피드는 ADO.NET Data Services에서 생성하는 데이터 피드와 동일한 형식으로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-141">The data feeds generated by [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] are in the same format as those generated by  that ADO.NET Data Services.</span></span>  
  
 <span data-ttu-id="d7178-142">데이터 피드에는 헤더 섹션과 데이터 섹션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-142">A data feed contains two sections: header and data.</span></span> <span data-ttu-id="d7178-143">Atom 사양은 각 섹션에서 요소를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-143">The Atom specification defines the elements in each section.</span></span> <span data-ttu-id="d7178-144">헤더에는 데이터 피드에서 사용할 문자 인코딩 스키마와 같은 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-144">The header includes information such as the character encoding schema to use with the data feeds.</span></span>  
  
### <a name="header-section"></a><span data-ttu-id="d7178-145">헤더 섹션</span><span class="sxs-lookup"><span data-stu-id="d7178-145">Header Section</span></span>  
 <span data-ttu-id="d7178-146">다음 XML 코드에서는 데이터 피드의 헤더 섹션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-146">The following XML code shows the header section of a data feed.</span></span>  
  
 `<?xml version="1.0" encoding="utf-8" standalone="yes"?><feed xmlns:d="https://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="https://schemas.microsoft.com/ado/2007/08/dataservices/metadata" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<title type="text"></title>`  
  
 `<id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166321</id>`  
  
 `<updated>2009-05-08T23:09:58Z</updated>`  
  
### <a name="data-section"></a><span data-ttu-id="d7178-147">데이터 섹션</span><span class="sxs-lookup"><span data-stu-id="d7178-147">Data Section</span></span>  
 <span data-ttu-id="d7178-148">데이터 피드의 데이터 섹션에는 `entry` Atom 렌더링 확장 프로그램에서 생성 하는 일반 행 집합의 각 행에 대 한 <> 요소가 하나씩 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-148">The data section of the data feeds contains one <`entry`> element for each row in the flattened rowset generated by the Atom rendering extension.</span></span>  
  
 <span data-ttu-id="d7178-149">다음 다이어그램에서는 그룹과 합계를 사용하는 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-149">The following diagram shows a report that uses groups and totals.</span></span>  
  
 <span data-ttu-id="d7178-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span><span class="sxs-lookup"><span data-stu-id="d7178-150">![RS_Atom_ProductSalesSummaryCircledValues](../media/rs-atom-productsalessummarycircledvalues.gif "RS_Atom_ProductSalesSummaryCircledValues")</span></span>  
  
 <span data-ttu-id="d7178-151">다음 XML은 `entry` 데이터 피드에 있는 해당 보고서의 <> 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-151">The following XML shows an <`entry`> element from that report in a data feed.</span></span> <span data-ttu-id="d7178-152"><`entry`> 요소에는 그룹의 판매량 및 주문의 합계와 모든 그룹의 판매량 및 주문 합계가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-152">Notice that the <`entry`> element includes the totals of the sales and orders for the group and the totals of sales and orders for all the groups.</span></span> <span data-ttu-id="d7178-153"><`entry`> 요소에는 보고서의 모든 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-153">The <`entry`> element includes all values on the report.</span></span>  
  
 `<entry><id>uuid:1795992c-a6f3-40ec-9243-fbfd0b1a5be3;id=166322</id><title type="text"></title><updated>2009-05-08T23:09:58Z</updated><author /><content type="application/xml"><m:properties>`  
  
 `<d:ProductCategory_Value>Accessories</d:ProductCategory_Value>`  
  
 `<d:OrderYear_Value m:type="Edm.Int32">2001</d:OrderYear_Value>`  
  
 `<d:SumLineTotal_Value m:type="Edm.Decimal">20235.364608</d:SumLineTotal_Value>`  
  
 `<d:SumOrderQty_Value m:type="Edm.Int32">1003</d:SumOrderQty_Value>`  
  
 `<d:SumLineTotal_Total_2_1 m:type="Edm.Decimal">1272072.883926</d:SumLineTotal_Total_2_1>`  
  
 `<d:SumOrderQty_Total_2_1 m:type="Edm.Double">61932</d:SumOrderQty_Total_2_1>`  
  
 `<d:SumLineTotal_Total_2_2 m:type="Edm.Decimal">109846381.399888</d:SumLineTotal_Total_2_2>`  
  
 `<d:SumOrderQty_Total_2_2 m:type="Edm.Double">274914</d:SumOrderQty_Total_2_2></m:properties></content>`  
  
 `</entry>`  
  
### <a name="working-with-data-feeds"></a><span data-ttu-id="d7178-154">데이터 피드 작업</span><span class="sxs-lookup"><span data-stu-id="d7178-154">Working with Data Feeds</span></span>  
 <span data-ttu-id="d7178-155">보고서에서 생성하는 모든 데이터 피드에는 데이터 피드를 생성하는 데이터 영역의 부모 범위에 있는 보고서 항목이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-155">All data feeds generated by the report include the report items that are in scope of the parent of the data region that generate the data feeds.</span></span> <span data-ttu-id="d7178-156">.</span><span class="sxs-lookup"><span data-stu-id="d7178-156">.</span></span> <span data-ttu-id="d7178-157">예를 들어 몇 가지 테이블과 차트가 있는 보고서의 경우</span><span class="sxs-lookup"><span data-stu-id="d7178-157">Imagine a report that has several tables and a chart.</span></span> <span data-ttu-id="d7178-158">보고서 본문의 입력란에서는 각 데이터 영역을 설명하는 텍스트를 제공하고,</span><span class="sxs-lookup"><span data-stu-id="d7178-158">Text boxes in the report body provides descriptive text of each data region.</span></span> <span data-ttu-id="d7178-159">보고서에서 생성하는 모든 데이터 피드의 각 항목에는 이 입력란 값이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-159">Every entry in every data feed that the report generates includes the value of the text box.</span></span> <span data-ttu-id="d7178-160">예를 들어 텍스트가 "Chart displays monthly sales averages by sales region"인 경우 세 데이터 피드는 모두 각 행에서 이 텍스트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-160">For example, if the text is "Chart displays monthly sales averages by sales region", all three data feeds would include this text on each row.</span></span>  
  
 <span data-ttu-id="d7178-161">보고서 레이아웃에 중첩 데이터 영역과 같은 계층적 데이터 관계가 포함된 경우 해당 관계가 보고서 데이터의 일반화된 행 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-161">If the report layout includes hierarchical data relationships, such as nested data regions, those relationships are included in the flattened rowset of report data.</span></span>  
  
 <span data-ttu-id="d7178-162">일반적으로 중첩 데이터 영역의 데이터 행은 특히 중첩 테이블과 행렬에 그룹 및 합계가 포함되는 경우 너비가 넓습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-162">The data rows for nested data regions are typically wide, especially if the nested tables and matrices include groups and totals.</span></span> <span data-ttu-id="d7178-163">보고서를 데이터 피드로 내보내고 데이터 피드를 검토하여 생성된 데이터가 기대한 것인지 확인하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-163">You might find it useful to export the report to a data feed and view the data feed to verify that the data generated is what you expected.</span></span>  
  
 <span data-ttu-id="d7178-164">Atom 렌더링 확장 프로그램이 Atom 서비스 문서를 만드는 경우 고유 식별자가 데이터 피드에 대해 만들어지며 URL에서 이 식별자를 사용하여 데이터 피드의 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-164">When the Atom rendering extension creates the Atom service document, a unique identifier is created for the data feed and you use the identifier in the URL to view the content of the data feed.</span></span> <span data-ttu-id="d7178-165">위에 표시 된 샘플 Atom 서비스 문서에는 URL "이 포함 되어 있습니다 <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1> .</span><span class="sxs-lookup"><span data-stu-id="d7178-165">The sample Atom service document, shown above, includes the URL <http://ServerName/ReportServer?%2fProduct+Sales+Summary&rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=xAx0x1>".</span></span> <span data-ttu-id="d7178-166">이 URL은 보고서(Product Sales Summary), Atom 렌더링 형식(ATOM) 및 데이터 피드의 이름(xAx0x1)을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-166">The URL identifies the report (Product Sales Summary), the Atom rendering format (ATOM), and the name of the data feed (xAx0x1).</span></span>  
  
 <span data-ttu-id="d7178-167">보고서 항목 이름은 기본적으로 보고서 항목의 RDL(Report Definition Language) 요소 이름으로 설정되며 간단하지 않거나 기억하기 쉽지 않은 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-167">Report item names default to the report definition language (RDL) element names of the report items and often they are not intuitive or easy to remember.</span></span> <span data-ttu-id="d7178-168">예를 들어 보고서에 배치된 첫 번째 행렬의 기본 이름은 Tablix 1입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-168">For example, the default name of the first matrix placed in a report is Tablix 1.</span></span> <span data-ttu-id="d7178-169">데이터 피드는 이러한 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-169">The data feeds use these names.</span></span>  
  
 <span data-ttu-id="d7178-170">데이터 피드를 사용하기 쉽게 만들려면 데이터 영역의 DataElementName 속성을 사용하여 친숙한 이름을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-170">To make the data feed easier to work with, you can use the DataElementName property of the data region to provide friendly names.</span></span> <span data-ttu-id="d7178-171">DataElementName에 대 한 값을 제공 하는 경우 데이터 피드 하위 요소는 `d` 기본 데이터 영역 이름 대신 <> 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-171">If you provide a value for DataElementName the data feed subelement <`d`> will use is it instead of the default data region name.</span></span> <span data-ttu-id="d7178-172">예를 들어 데이터 영역의 기본 이름이 Tablix1 및 DataElementName set SalesByTerritoryYear 인 경우 `d` 데이터 피드의 <>는 SalesByTerritoryYear를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-172">For example, if the default name of a data regions is Tablix1 and DataElementName set SalesByTerritoryYear then the <`d`> in the data feed uses SalesByTerritoryYear.</span></span> <span data-ttu-id="d7178-173">데이터 영역에 위에서 설명한 행렬 보고서와 같은 두 가지 데이터 피드가 있는 경우 데이터 피드에서 사용되는 이름은 SalesByTerritoryYear _Territory 및 SalesByTerritoryYear _Year입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-173">If the data regions has two data feeds like the matrix report described above, the names used in the data feeds are SalesByTerritoryYear _Territory and SalesByTerritoryYear _Year.</span></span>  
  
 <span data-ttu-id="d7178-174">보고서에 표시된 데이터와 데이터 피드의 데이터를 비교하는 경우 몇 가지 차이점을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-174">If you compare the data shown on the report and the data in the data feed, you might notice some differences.</span></span> <span data-ttu-id="d7178-175">보고서에는 형식이 지정된 숫자 및 시간/날짜 데이터가 표시되는 경우가 많지만 데이터 피드에는 형식이 지정되지 않은 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-175">Reports often shows formatted numeric and time/date data whereas the data feed contains unformatted data.</span></span>  
  
 <span data-ttu-id="d7178-176">데이터 피드는 .atom 파일 이름 확장명으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-176">A data feed is saved with the .atom file name extension.</span></span> <span data-ttu-id="d7178-177">메모장 또는 XML 편집기와 같은 텍스트 또는 XML 편집기를 사용하여 파일 구조와 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-177">You can use a text or XML editor such as Notepad or XML Editor to view the file structure and content.</span></span>  
  

  
##  <a name="flattening-report-data"></a><a name="FlatteningReportData"></a> <span data-ttu-id="d7178-178">보고서 데이터 일반화</span><span class="sxs-lookup"><span data-stu-id="d7178-178">Flattening Report Data</span></span>  
 <span data-ttu-id="d7178-179">Atom 렌더러는 XML 형식의 일반화된 행 집합으로 보고서 데이터를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-179">The Atom renderer provides report data as flattened rowsets in an XML format.</span></span> <span data-ttu-id="d7178-180">데이터 테이블을 일반화하기 위한 규칙은 몇 가지 예외를 제외하고 CSV 렌더러의 규칙과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-180">The rules for flattening data tables are the same to those of the CSV renderer with a few exceptions:</span></span>  
  
-   <span data-ttu-id="d7178-181">범위의 항목은 세부 수준으로 일반화됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-181">Items in scope are flattened to the detail level.</span></span> <span data-ttu-id="d7178-182">CSV 렌더러와 달리 최상위 수준의 입력란은 데이터 피드에 작성된 각 항목에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-182">Unlike the CSV renderer, the text boxes at the top level appear in each entry written to the data feed.</span></span>  
  
-   <span data-ttu-id="d7178-183">보고서 매개 변수 값은 출력의 각 행에서 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-183">Report parameter values are rendered on each row of the output.</span></span>  
  
 <span data-ttu-id="d7178-184">계층적 데이터와 그룹화된 데이터를 Atom 규격 형식으로 표현하려면 일반화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-184">Hierarchical and grouped data must be flattened in order to be represented in the Atom-compliant format.</span></span> <span data-ttu-id="d7178-185">렌더링 확장 프로그램은 보고서를 데이터 영역 내부의 중첩된 그룹을 표현하는 트리 구조로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-185">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="d7178-186">보고서는 다음과 같이 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-186">To flatten the report:</span></span>  
  
-   <span data-ttu-id="d7178-187">행 계층 구조가 열 계층 구조보다 먼저 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-187">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="d7178-188">행 계층 구조의 멤버가 열 계층 구조의 멤버보다 먼저 데이터 피드로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-188">Members of the row hierarchy are rendered to the data feed before members of the column hierarchy.</span></span>  
  
-   <span data-ttu-id="d7178-189">열은 본문의 입력란이 왼쪽에서 오른쪽, 위쪽에서 아래쪽으로 정렬되고 그 다음에 데이터 영역이 왼쪽에서 오른쪽, 위쪽에서 아래쪽으로 정렬되는 방식으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-189">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="d7178-190">데이터 영역 내에서 열은 모퉁이 멤버, 행 계층 구조 멤버, 열 계층 구조 멤버, 셀 순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-190">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="d7178-191">피어 데이터 영역은 공통 데이터 영역 또는 동적 상위 항목을 공유하는 데이터 영역 또는 동적 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-191">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="d7178-192">피어 데이터는 결합된 트리의 분기에 의해 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-192">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="d7178-193">자세한 내용은 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7178-193">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="atom-rendering-rules"></a><a name="AtomRendering"></a> <span data-ttu-id="d7178-194">Atom 렌더링 규칙</span><span class="sxs-lookup"><span data-stu-id="d7178-194">Atom Rendering Rules</span></span>  
 <span data-ttu-id="d7178-195">Atom 렌더링 확장 프로그램은 데이터 피드를 렌더링할 때 다음 정보를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-195">The Atom rendering extension ignores the following information when rendering a data feed:</span></span>  
  
-   <span data-ttu-id="d7178-196">서식 및 레이아웃</span><span class="sxs-lookup"><span data-stu-id="d7178-196">Formatting and layout</span></span>  
  
-   <span data-ttu-id="d7178-197">페이지 머리글</span><span class="sxs-lookup"><span data-stu-id="d7178-197">Page header</span></span>  
  
-   <span data-ttu-id="d7178-198">페이지 바닥글</span><span class="sxs-lookup"><span data-stu-id="d7178-198">Page footer</span></span>  
  
-   <span data-ttu-id="d7178-199">사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="d7178-199">Custom report items</span></span>  
  
-   <span data-ttu-id="d7178-200">사각형</span><span class="sxs-lookup"><span data-stu-id="d7178-200">Rectangles</span></span>  
  
-   <span data-ttu-id="d7178-201">선</span><span class="sxs-lookup"><span data-stu-id="d7178-201">Lines</span></span>  
  
-   <span data-ttu-id="d7178-202">이미지</span><span class="sxs-lookup"><span data-stu-id="d7178-202">Images</span></span>  
  
-   <span data-ttu-id="d7178-203">자동 부분합</span><span class="sxs-lookup"><span data-stu-id="d7178-203">Automatic subtotals</span></span>  
  
 <span data-ttu-id="d7178-204">나머지 보고서 항목은 위쪽에서 아래쪽으로 정렬된 다음 왼쪽에서 오른쪽으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-204">The remaining report items are sorted, from top to bottom, and then left to right.</span></span> <span data-ttu-id="d7178-205">그런 다음 각 항목이 열로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-205">Each item is then rendered to a column.</span></span> <span data-ttu-id="d7178-206">보고서에 목록이나 테이블과 같은 중첩된 데이터 항목이 있는 경우 부모 항목이 각 행에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-206">If the report has nested data items like lists or tables, the parent items are repeated on each row.</span></span>  
  
 <span data-ttu-id="d7178-207">다음 표는 보고서 항목이 렌더링될 때의 모양을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-207">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="d7178-208">항목</span><span class="sxs-lookup"><span data-stu-id="d7178-208">Item</span></span>|<span data-ttu-id="d7178-209">렌더링 동작</span><span class="sxs-lookup"><span data-stu-id="d7178-209">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="d7178-210">표</span><span class="sxs-lookup"><span data-stu-id="d7178-210">Table</span></span>|<span data-ttu-id="d7178-211">테이블을 확장하고 최하위 수준에서 각 행과 열에 대한 행과 열을 만들어 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-211">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="d7178-212">부분합 행과 열에는 열 머리글이나 행 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-212">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="d7178-213">드릴스루 보고서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-213">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="d7178-214">행렬</span><span class="sxs-lookup"><span data-stu-id="d7178-214">Matrix</span></span>|<span data-ttu-id="d7178-215">행렬을 확장하고 최하위 수준에서 각 행과 열에 행과 열을 만들어 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-215">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="d7178-216">부분합 행과 열에는 열 머리글이나 행 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-216">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="d7178-217">목록</span><span class="sxs-lookup"><span data-stu-id="d7178-217">List</span></span>|<span data-ttu-id="d7178-218">목록의 각 정보 행이나 인스턴스에 대해 레코드를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-218">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="d7178-219">하위 보고서</span><span class="sxs-lookup"><span data-stu-id="d7178-219">Subreport</span></span>|<span data-ttu-id="d7178-220">내용의 각 인스턴스에 대해 부모 항목이 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-220">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="d7178-221">차트</span><span class="sxs-lookup"><span data-stu-id="d7178-221">Chart</span></span>|<span data-ttu-id="d7178-222">각 차트 값에 대한 모든 차트 레이블을 사용하여 레코드를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-222">Renders a record with all chart labels for each chart value.</span></span> <span data-ttu-id="d7178-223">계층 구조에서 계열 및 범주의 레이블은 결합되어 차트 값에 대한 행에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-223">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="d7178-224">데이터 막대</span><span class="sxs-lookup"><span data-stu-id="d7178-224">Data bar</span></span>|<span data-ttu-id="d7178-225">차트와 같이 렌더링하며</span><span class="sxs-lookup"><span data-stu-id="d7178-225">Renders like a chart.</span></span> <span data-ttu-id="d7178-226">대개 계층이나 레이블을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-226">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="d7178-227">스파크라인</span><span class="sxs-lookup"><span data-stu-id="d7178-227">Sparkline</span></span>|<span data-ttu-id="d7178-228">차트와 같이 렌더링하며</span><span class="sxs-lookup"><span data-stu-id="d7178-228">Renders like a chart.</span></span> <span data-ttu-id="d7178-229">대개 계층이나 레이블을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-229">Typically, a sparkline does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="d7178-230">계기</span><span class="sxs-lookup"><span data-stu-id="d7178-230">Gauge</span></span>|<span data-ttu-id="d7178-231">선형 눈금의 최소값과 최대값, 범위의 시작 값과 끝 값, 포인터의 값을 사용하여 한 레코드로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-231">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="d7178-232">표시기</span><span class="sxs-lookup"><span data-stu-id="d7178-232">Indicator</span></span>|<span data-ttu-id="d7178-233">활성 상태 이름, 사용 가능한 상태 및 데이터 값을 포함하는 단일 레코드로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-233">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="d7178-234">맵</span><span class="sxs-lookup"><span data-stu-id="d7178-234">Map</span></span>|<span data-ttu-id="d7178-235">각 지도 데이터 영역에 대한 데이터 피드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-235">Generates a data feed for each map data region.</span></span> <span data-ttu-id="d7178-236">여러 지도 계층에서 동일한 데이터 영역을 사용하는 경우 데이터 피드에는 모든 지도 계층이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-236">If multiple map layers use the same data region, the data feed includes all of them.</span></span> <span data-ttu-id="d7178-237">데이터 피드에는 지도 계층의 각 지도 멤버에 대한 레이블과 값이 있는 레코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-237">The data feed includes a record with the labels and values for each map member of the map layer.</span></span>|  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="d7178-238">장치 정보 설정</span><span class="sxs-lookup"><span data-stu-id="d7178-238">Device Information Settings</span></span>  
 <span data-ttu-id="d7178-239">사용할 인코딩 스키마를 비롯하여 이 렌더러의 기본 설정을 일부 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7178-239">You can change some default settings for this renderer, including the encoding schema to use.</span></span> <span data-ttu-id="d7178-240">자세한 내용은 [ATOM Device Information Settings](../atom-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7178-240">For more information, see [ATOM Device Information Settings](../atom-device-information-settings.md).</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="d7178-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7178-241">See Also</span></span>  
 <span data-ttu-id="d7178-242">[CSV 파일로 내보내기 &#40;보고서 작성기 및 SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="d7178-242">[Exporting to a CSV File &#40;Report Builder and SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="d7178-243">보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기</span><span class="sxs-lookup"><span data-stu-id="d7178-243">Exporting Reports &#40;Report Builder and SSRS&#41;</span></span>](export-reports-report-builder-and-ssrs.md)  
  
  
