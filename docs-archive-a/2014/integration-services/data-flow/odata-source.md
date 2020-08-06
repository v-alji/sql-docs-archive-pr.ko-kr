---
title: OData 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741139"
---
# <a name="odata-source"></a><span data-ttu-id="5696d-102">OData 원본</span><span class="sxs-lookup"><span data-stu-id="5696d-102">OData Source</span></span>
  <span data-ttu-id="5696d-103">SSIS 패키지의 OData 원본 구성 요소를 사용하여 Open Data Protocol(OData) 서비스에서 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-103">You use the OData Source component in an SSIS package to consume data from Open Data Protocol (OData) services.</span></span> <span data-ttu-id="5696d-104">이 구성 요소는 OData v2 및 v3 프로토콜뿐만 아니라 ATOM 및 JSON 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-104">The component supports the OData v2 and v3 protocols, as well as the ATOM and JSON data formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5696d-105">OData 원본을 사용하여 SharePoint 목록에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-105">The OData Source can be used to read from SharePoint lists.</span></span> <span data-ttu-id="5696d-106">SharePoint 서버의 모든 목록을 보려면 다음 URL을 사용 합니다. http:// \<server> /_vti_bin/listdata.svc.</span><span class="sxs-lookup"><span data-stu-id="5696d-106">To see all lists on your SharePoint server, use the following URL: http://\<server>/_vti_bin/ListData.svc.</span></span> <span data-ttu-id="5696d-107">SharePoint URL 규칙에 대한 자세한 내용은 [SharePoint Foundation REST 인터페이스](https://msdn.microsoft.com/library/ff521587.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="5696d-107">For more information about SharePoint URL conventions, see [SharePoint Foundation REST Interface](https://msdn.microsoft.com/library/ff521587.aspx).</span></span>  
  
## <a name="odata-format"></a><span data-ttu-id="5696d-108">OData 형식</span><span class="sxs-lookup"><span data-stu-id="5696d-108">OData Format</span></span>  
 <span data-ttu-id="5696d-109">대부분의 OData 서비스는 여러 형식으로 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-109">Most OData services return results in multiple formats.</span></span> <span data-ttu-id="5696d-110">$format 쿼리 옵션을 사용하여 결과 집합의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-110">You can specify the format of the result set by using the $format query option.</span></span> <span data-ttu-id="5696d-111">JSON 및 JSON Light와 같은 형식은 ATOM/XML보다 효율적이며 많은 양의 데이터를 전송하는 경우 더 나은 성능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-111">Formats such as JSON and JSON Light are more efficient than ATOM/XML, and may give you better performance when transferring large amounts of data.</span></span> <span data-ttu-id="5696d-112">다음 표에서는 샘플 테스트의 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-112">The following table provides results from sample tests.</span></span> <span data-ttu-id="5696d-113">표에 나와 있듯이 ATOM에서 JSON으로 전환하는 경우 성능이 30-53% 향상되었고, ATOM에서 새로운 JSON Light 형식(WCF Data Services 5.1에서 사용 가능)으로 전환하는 경우에는 성능이 67% 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-113">As you can see, there was a 30-53% performance gain when switching from ATOM to JSON and 67% performance gain when switching from ATOM to the new JSON light format (available in WCF Data Services 5.1).</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="5696d-114">행</span><span class="sxs-lookup"><span data-stu-id="5696d-114">Rows</span></span>|<span data-ttu-id="5696d-115">ATOM</span><span class="sxs-lookup"><span data-stu-id="5696d-115">ATOM</span></span>|<span data-ttu-id="5696d-116">JSON</span><span class="sxs-lookup"><span data-stu-id="5696d-116">JSON</span></span>|<span data-ttu-id="5696d-117">JSON(Light)</span><span class="sxs-lookup"><span data-stu-id="5696d-117">JSON (Light)</span></span>|  
|<span data-ttu-id="5696d-118">10000</span><span class="sxs-lookup"><span data-stu-id="5696d-118">10000</span></span>|<span data-ttu-id="5696d-119">113초</span><span class="sxs-lookup"><span data-stu-id="5696d-119">113 seconds</span></span>|<span data-ttu-id="5696d-120">74초</span><span class="sxs-lookup"><span data-stu-id="5696d-120">74 seconds</span></span>|<span data-ttu-id="5696d-121">68초</span><span class="sxs-lookup"><span data-stu-id="5696d-121">68 seconds</span></span>|  
|<span data-ttu-id="5696d-122">1000000</span><span class="sxs-lookup"><span data-stu-id="5696d-122">1000000</span></span>|<span data-ttu-id="5696d-123">1110초</span><span class="sxs-lookup"><span data-stu-id="5696d-123">1110 seconds</span></span>|<span data-ttu-id="5696d-124">853초</span><span class="sxs-lookup"><span data-stu-id="5696d-124">853 seconds</span></span>|<span data-ttu-id="5696d-125">665초</span><span class="sxs-lookup"><span data-stu-id="5696d-125">665 seconds</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="5696d-126">SSIS OData 원본은 ODataLib 5.5.0을 사용하여 OData 피드를 구문 분석하며 이 라이브러리에서 지원하는 모든 형식을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5696d-126">The SSIS OData Source uses ODataLib 5.5.0 to parse OData feeds and it can read all formats supported by this library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5696d-127">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5696d-127">In This Section</span></span>  
  
-   [<span data-ttu-id="5696d-128">OData 원본 구성 요소 설치 및 제거</span><span class="sxs-lookup"><span data-stu-id="5696d-128">Install and Uninstall OData Source Component</span></span>](../install-and-uninstall-odata-source-component.md)  
  
-   [<span data-ttu-id="5696d-129">자습서: OData 원본 &#91;SSIS&#93;사용</span><span class="sxs-lookup"><span data-stu-id="5696d-129">Tutorial: Using the OData Source &#91;SSIS&#93;</span></span>](tutorial-using-the-odata-source.md)  
  
-   [<span data-ttu-id="5696d-130">런타임에 OData 원본 쿼리 수정</span><span class="sxs-lookup"><span data-stu-id="5696d-130">Modify OData Source Query at Runtime</span></span>](modify-odata-source-query-at-runtime.md)  
  
-   [<span data-ttu-id="5696d-131">OData 원본 편집기&#40;연결 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="5696d-131">OData Source Editor &#40;Connection Page&#41;</span></span>](../odata-source-editor-connection-page.md)  
  
-   [<span data-ttu-id="5696d-132">OData 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="5696d-132">OData Source Editor &#40;Columns Page&#41;</span></span>](../odata-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="5696d-133">OData 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="5696d-133">OData Source Editor &#40;Error Output Page&#41;</span></span>](../odata-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="5696d-134">OData 원본 속성</span><span class="sxs-lookup"><span data-stu-id="5696d-134">OData Source Properties</span></span>](odata-source-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="5696d-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5696d-135">See Also</span></span>  
 [<span data-ttu-id="5696d-136">OData 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="5696d-136">OData Connection Manager</span></span>](../connection-manager/odata-connection-manager.md)  
  
  
