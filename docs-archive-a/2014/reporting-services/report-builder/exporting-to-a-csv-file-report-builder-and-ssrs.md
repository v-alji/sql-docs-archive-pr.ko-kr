---
title: CSV 파일로 내보내기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 68ec746e-8c82-47f5-8c3d-dbe403a441e5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 635d5904acf6e616378f5423bfbaf4cf5390fa9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639371"
---
# <a name="exporting-to-a-csv-file-report-builder-and-ssrs"></a><span data-ttu-id="3af85-102">CSV 파일로 내보내기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="3af85-102">Exporting to a CSV File (Report Builder and SSRS)</span></span>
  <span data-ttu-id="3af85-103">CSV(쉼표로 구분된 값) 렌더링 확장 프로그램은 보고서의 데이터를 결합하여 읽기 쉽고 많은 애플리케이션과 교환할 수 있는 표준화된 일반 텍스트 형식으로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-103">The Comma-Separated Value (CSV) rendering extension renders reports as a flattened representation of data from a report in a standardized, plain-text format that is easily readable and exchangeable with many applications.</span></span>  
  
 <span data-ttu-id="3af85-104">CSV 렌더링 확장 프로그램에서는 필드와 행을 구분하기 위해 문자열 구분 기호를 사용하는데 이 문자열 구분 기호는 쉼표 이외의 문자로 구성 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-104">The CSV rendering extension uses a string character delimiter to separate fields and rows, with the string character delimiter configurable to be a character other than a comma.</span></span> <span data-ttu-id="3af85-105">결과 파일은 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 과 같은 스프레드시트 프로그램에서 열거나 다른 프로그램의 가져오기 형식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-105">The resulting file can be opened in a spreadsheet program like [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] or used as an import format for other programs.</span></span> <span data-ttu-id="3af85-106">내보낸 보고서는 .csv 파일이 되며 `text/csv` MIME 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-106">The exported report becomes a .csv file, and returns a MIME type of `text/csv`.</span></span>  
  
 <span data-ttu-id="3af85-107">[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]의 차트, 데이터 막대, 스파크라인, 계기 및 표시기와 관련된 데이터를 사용하려면 보고서를 CSV 파일로 내보낸 다음 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel에서 이 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-107">If you want to work with data related to charts, data bars, sparklines, gauges, and indicators in [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)], export the report to a CSV file, and then open the file in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="csv-rendering"></a><a name="CSVRendering"></a><span data-ttu-id="3af85-108">CSV 렌더링</span><span class="sxs-lookup"><span data-stu-id="3af85-108">CSV Rendering</span></span>  
 <span data-ttu-id="3af85-109">기본 설정을 사용하여 렌더링된 CSV 보고서는 다음과 같은 특징을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-109">When rendered using the default settings, a CSV report has the following characteristics:</span></span>  
  
-   <span data-ttu-id="3af85-110">기본 필드 구분 기호 문자열은 쉼표(,)입니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-110">The default field delimiter string is a comma (,).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3af85-111">디바이스 정보 설정을 변경하여 필드 구분 기호를 TAB을 비롯한 임의의 문자로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-111">You can change the field delimiter to any character that you want, including TAB, by changing the device information settings.</span></span> <span data-ttu-id="3af85-112">자세한 내용은 [CSV Device Information Settings](../csv-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3af85-112">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
-   <span data-ttu-id="3af85-113">레코드 구분 기호 문자열은 캐리지 리턴 및 줄 바꿈 ( \<cr> \<lf> )입니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-113">The record delimiter string is the carriage return and line feed (\<cr>\<lf>).</span></span>  
  
-   <span data-ttu-id="3af85-114">텍스트 한정자 문자열은 인용 부호(")입니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-114">The text qualifier string is a quotation mark (").</span></span>  
  
     <span data-ttu-id="3af85-115">CSV 렌더러는 일부 텍스트 문자열 주위에만 한정자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-115">The CSV renderer does not add qualifiers around all text strings.</span></span> <span data-ttu-id="3af85-116">텍스트 한정자는 값에 구분 기호 문자가 포함되어 있거나 값에 줄 바꿈이 있을 때만 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-116">Text qualifiers are added only when the value contains the delimiter character or when the value has a line break.</span></span>  
  
-   <span data-ttu-id="3af85-117">텍스트에 포함 구분 기호 문자열이나 한정자 문자열이 포함되어 있는 경우 텍스트 한정자는 텍스트 양 끝에 놓이며 포함 한정자 문자열은 중복됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-117">If the text contains an embedded delimiter string or qualifier string, the text qualifier is placed around the text, and the embedded qualifier strings are doubled.</span></span>  
  
-   <span data-ttu-id="3af85-118">서식 및 레이아웃은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-118">Formatting and layout are ignored.</span></span>  
  
 <span data-ttu-id="3af85-119">렌더링하는 동안 다음 항목은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-119">The following items are ignored during rendering:</span></span>  
  
-   <span data-ttu-id="3af85-120">페이지 머리글</span><span class="sxs-lookup"><span data-stu-id="3af85-120">Page header</span></span>  
  
-   <span data-ttu-id="3af85-121">페이지 바닥글</span><span class="sxs-lookup"><span data-stu-id="3af85-121">Page footer</span></span>  
  
-   <span data-ttu-id="3af85-122">사용자 지정 보고서 항목</span><span class="sxs-lookup"><span data-stu-id="3af85-122">Custom report items</span></span>  
  
-   <span data-ttu-id="3af85-123">줄</span><span class="sxs-lookup"><span data-stu-id="3af85-123">Line</span></span>  
  
-   <span data-ttu-id="3af85-124">이미지</span><span class="sxs-lookup"><span data-stu-id="3af85-124">Image</span></span>  
  
-   <span data-ttu-id="3af85-125">사각형</span><span class="sxs-lookup"><span data-stu-id="3af85-125">Rectangle</span></span>  
  
-   <span data-ttu-id="3af85-126">자동 부분합</span><span class="sxs-lookup"><span data-stu-id="3af85-126">Automatic subtotals</span></span>  
  
 <span data-ttu-id="3af85-127">나머지 보고서 항목은 위쪽에서 아래쪽으로 정렬된 다음 왼쪽에서 오른쪽으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-127">The remaining report items are sorted, from top to bottom, then left to right.</span></span> <span data-ttu-id="3af85-128">그런 다음 각 항목이 열로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-128">Each item is then rendered to a column.</span></span> <span data-ttu-id="3af85-129">보고서에 목록이나 테이블과 같은 중첩된 데이터 항목이 있는 경우 부모 항목이 각 레코드에서 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-129">If the report has nested data items like lists or tables, the parent items are repeated in each record.</span></span>  
  
 <span data-ttu-id="3af85-130">다음 표는 보고서 항목이 렌더링될 때의 모양을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-130">The following table indicates the appearance of report items when rendered:</span></span>  
  
|<span data-ttu-id="3af85-131">항목</span><span class="sxs-lookup"><span data-stu-id="3af85-131">Item</span></span>|<span data-ttu-id="3af85-132">렌더링 동작</span><span class="sxs-lookup"><span data-stu-id="3af85-132">Rendering behavior</span></span>|  
|----------|------------------------|  
|<span data-ttu-id="3af85-133">텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="3af85-133">Text box</span></span>|<span data-ttu-id="3af85-134">입력란의 내용을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-134">Renders the contents of the text box.</span></span> <span data-ttu-id="3af85-135">기본 모드에서는 항목의 서식 속성에 따라 항목의 서식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-135">In default mode, items are formatted based on the item's formatting properties.</span></span> <span data-ttu-id="3af85-136">규격 모드에서는 서식이 디바이스 정보 설정에 의해 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-136">In compliant mode, formatting can be changed by device information settings.</span></span> <span data-ttu-id="3af85-137">CSV 렌더링 모드에 대한 자세한 정보는 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="3af85-137">For more information about CSV rendering modes, see below.</span></span>|  
|<span data-ttu-id="3af85-138">표</span><span class="sxs-lookup"><span data-stu-id="3af85-138">Table</span></span>|<span data-ttu-id="3af85-139">테이블을 확장하고 최하위 수준에서 각 행과 열에 대한 행과 열을 만들어 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-139">Renders by expanding the table and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="3af85-140">부분합 행과 열에는 열 머리글이나 행 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-140">Subtotal rows and columns do not have column or row headings.</span></span> <span data-ttu-id="3af85-141">드릴스루 보고서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-141">Drillthrough reports are not supported.</span></span>|  
|<span data-ttu-id="3af85-142">행렬</span><span class="sxs-lookup"><span data-stu-id="3af85-142">Matrix</span></span>|<span data-ttu-id="3af85-143">행렬을 확장하고 최하위 수준에서 각 행과 열에 행과 열을 만들어 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-143">Renders by expanding the matrix and creating a row and column for each row and column at the lowest level of detail.</span></span> <span data-ttu-id="3af85-144">부분합 행과 열에는 열 머리글이나 행 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-144">Subtotal rows and columns do not have column or row headings.</span></span>|  
|<span data-ttu-id="3af85-145">목록</span><span class="sxs-lookup"><span data-stu-id="3af85-145">List</span></span>|<span data-ttu-id="3af85-146">목록의 각 정보 행이나 인스턴스에 대해 레코드를 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-146">Renders a record for each detail row or instance in the list.</span></span>|  
|<span data-ttu-id="3af85-147">하위 보고서</span><span class="sxs-lookup"><span data-stu-id="3af85-147">Subreport</span></span>|<span data-ttu-id="3af85-148">내용의 각 인스턴스에 대해 부모 항목이 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-148">The parent item is repeated for each instance of the contents.</span></span>|  
|<span data-ttu-id="3af85-149">차트</span><span class="sxs-lookup"><span data-stu-id="3af85-149">Chart</span></span>|<span data-ttu-id="3af85-150">각 차트 값에 대한 행과 멤버 레이블을 만들어 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-150">Renders by creating a row for each chart value and member labels.</span></span> <span data-ttu-id="3af85-151">계층 구조에서 계열 및 범주의 레이블은 결합되어 차트 값에 대한 행에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-151">Labels from series and categories in hierarchies are flattened and included in the row for a chart value.</span></span>|  
|<span data-ttu-id="3af85-152">데이터 막대</span><span class="sxs-lookup"><span data-stu-id="3af85-152">Data bar</span></span>|<span data-ttu-id="3af85-153">차트와 같이 렌더링하며</span><span class="sxs-lookup"><span data-stu-id="3af85-153">Renders like a chart.</span></span> <span data-ttu-id="3af85-154">대개 계층이나 레이블을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-154">Typically, a data bar does not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="3af85-155">스파크라인</span><span class="sxs-lookup"><span data-stu-id="3af85-155">Sparkline</span></span>|<span data-ttu-id="3af85-156">차트와 같이 렌더링하며</span><span class="sxs-lookup"><span data-stu-id="3af85-156">Renders like a chart.</span></span> <span data-ttu-id="3af85-157">대개 스파크라인은 계층이나 레이블을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-157">Typically, a sparkline does not  do not include hierarchies or labels.</span></span>|  
|<span data-ttu-id="3af85-158">계기</span><span class="sxs-lookup"><span data-stu-id="3af85-158">Gauge</span></span>|<span data-ttu-id="3af85-159">선형 눈금의 최소값과 최대값, 범위의 시작 값과 끝 값, 포인터의 값을 사용하여 한 레코드로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-159">Renders as a single record with the minimum and maximum values of the linear scale, start and end values of the range, and the value of the pointer.</span></span>|  
|<span data-ttu-id="3af85-160">표시기</span><span class="sxs-lookup"><span data-stu-id="3af85-160">Indicator</span></span>|<span data-ttu-id="3af85-161">활성 상태 이름, 사용 가능한 상태 및 데이터 값을 포함하는 단일 레코드로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-161">Renders as a single record with the active state name, available states, and the data value.</span></span>|  
|<span data-ttu-id="3af85-162">맵</span><span class="sxs-lookup"><span data-stu-id="3af85-162">Map</span></span>|<span data-ttu-id="3af85-163">지도 계층의 각 지도 멤버에 대한 레이블과 값을 사용하여 행을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-163">Renders a row with the labels and values for each map member of a map layer.</span></span><br /><br /> <span data-ttu-id="3af85-164">지도에 여러 계층이 있는 경우 행의 값은 지도 계층에서 사용하는 지도 데이터 영역이 동일한지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-164">If the map has multiple layers the values in the rows varies depending on whether the map layers use the same or different map data regions.</span></span> <span data-ttu-id="3af85-165">여러 지도 계층에서 동일한 데이터 영역을 사용하는 경우 행에는 모든 계층의 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-165">If multiple map layers use the same data region, the rows contain data from all layers.</span></span>|  
  
### <a name="hierarchical-and-grouped-data"></a><span data-ttu-id="3af85-166">계층적 데이터 및 그룹화된 데이터</span><span class="sxs-lookup"><span data-stu-id="3af85-166">Hierarchical and Grouped Data</span></span>  
 <span data-ttu-id="3af85-167">계층적 데이터와 그룹화된 데이터를 CSV 형식으로 표현하려면 결합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-167">Hierarchical and grouped data must be flattened in order to be represented in the CSV format.</span></span>  
  
 <span data-ttu-id="3af85-168">렌더링 확장 프로그램은 보고서를 데이터 영역 내부의 중첩된 그룹을 표현하는 트리 구조로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-168">The rendering extension flattens the report into a tree structure that represents the nested groups within the data region.</span></span> <span data-ttu-id="3af85-169">보고서는 다음과 같이 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-169">To flatten the report:</span></span>  
  
-   <span data-ttu-id="3af85-170">행 계층 구조가 열 계층 구조보다 먼저 결합됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-170">A row hierarchy is flattened before a column hierarchy.</span></span>  
  
-   <span data-ttu-id="3af85-171">열은 본문의 입력란이 왼쪽에서 오른쪽, 위쪽에서 아래쪽으로 정렬되고 그 다음에 데이터 영역이 왼쪽에서 오른쪽, 위쪽에서 아래쪽으로 정렬되는 방식으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-171">Columns are ordered as follows: text boxes in body order left-to-right, top-to-bottom followed by data regions ordered left-to-right, top-to-bottom.</span></span>  
  
-   <span data-ttu-id="3af85-172">데이터 영역 내에서 열은 모퉁이 멤버, 행 계층 구조 멤버, 열 계층 구조 멤버, 셀 순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-172">Within a data region, the columns are ordered as follows: corner members, row hierarchy members, column hierarchy members, and then cells.</span></span>  
  
-   <span data-ttu-id="3af85-173">피어 데이터 영역은 공통 데이터 영역 또는 동적 상위 항목을 공유하는 데이터 영역 또는 동적 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-173">Peer data regions are data regions or dynamic groups that share a common data region or dynamic ancestor.</span></span> <span data-ttu-id="3af85-174">피어 데이터는 결합된 트리의 분기에 의해 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-174">Peer data is identified by branching of the flattened tree.</span></span>  
  
 <span data-ttu-id="3af85-175">자세한 내용은 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3af85-175">For more information, see [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  
 
  
##  <a name="renderer-modes"></a><a name="RenderingModes"></a> <span data-ttu-id="3af85-176">렌더러 모드</span><span class="sxs-lookup"><span data-stu-id="3af85-176">Renderer Modes</span></span>  
 <span data-ttu-id="3af85-177">CSV 렌더링 확장 프로그램은 두 가지 모드로 작동할 수 있습니다. 하나는 Excel에 대해 최적화된 모드이고, 다른 하나는 RFC 4180에 지정된 CSV 사양의 엄격한 준수를 요구하는 타사 애플리케이션에 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-177">The CSV rendering extension can operate in two modes: one is optimized for Excel and the other is optimized for third-party applications that require strict CSV compliance to the CSV specification in RFC 4180.</span></span> <span data-ttu-id="3af85-178">사용하는 모드에 따라 피어 데이터 영역은 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-178">Depending on which mode you use, peer data regions are handled differently.</span></span>  
  
### <a name="default-mode"></a><span data-ttu-id="3af85-179">기본 모드</span><span class="sxs-lookup"><span data-stu-id="3af85-179">Default Mode</span></span>  
 <span data-ttu-id="3af85-180">기본 모드는 Excel용으로 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-180">The default mode is optimized for Excel.</span></span> <span data-ttu-id="3af85-181">기본 모드로 렌더링되는 경우 보고서는 여러 섹션의 CSV로 렌더링된 데이터가 있는 CSV 파일로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-181">When rendered in default mode, the report is rendered as a CSV file with multiple sections of CSV-rendered data.</span></span> <span data-ttu-id="3af85-182">각 피어 데이터 영역은 빈 줄에 의해 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-182">Each peer data region is delimited by an empty line.</span></span> <span data-ttu-id="3af85-183">보고서 본문 내부의 피어 데이터 영역은 CSV 파일 내의 별도 데이터 블록으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-183">Peer data regions within the report body are rendered as separate blocks of data within the CSV file.</span></span> <span data-ttu-id="3af85-184">그 결과 다음과 같은 CSV 파일이 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-184">The result is a CSV file in which:</span></span>  
  
-   <span data-ttu-id="3af85-185">보고서 본문의 개별 입력란은 CSV 파일 내부의 첫 번째 데이터 블록으로 한 번 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-185">Individual text boxes within the report body are rendered once as the first block of data within the CSV file.</span></span>  
  
-   <span data-ttu-id="3af85-186">보고서 본문의 각 최상위 피어 데이터 영역은 자체 데이터 블록 안에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-186">Each top-level peer data region in the report body is rendered in its own data block.</span></span>  
  
-   <span data-ttu-id="3af85-187">중첩된 데이터 영역은 동일한 데이터 블록에 대각선 방향으로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-187">Nested data regions are rendered diagonally into the same data block.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="3af85-188">서식</span><span class="sxs-lookup"><span data-stu-id="3af85-188">Formatting</span></span>  
 <span data-ttu-id="3af85-189">숫자 값은 지정된 서식 상태로 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-189">Numeric values are rendered in their formatted state.</span></span> <span data-ttu-id="3af85-190">Excel은 통화, 백분율, 날짜 등 서식이 지정된 숫자 값을 인식하여 CSV 파일을 가져올 때 각 셀에 적절하게 서식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-190">Excel can recognize formatted numeric values, such as currency, percentage and date, and format the cells appropriately when importing the CSV file.</span></span>  
  
### <a name="compliant-mode"></a><span data-ttu-id="3af85-191">규격 모드</span><span class="sxs-lookup"><span data-stu-id="3af85-191">Compliant Mode</span></span>  
 <span data-ttu-id="3af85-192">규격 모드는 타사 애플리케이션에 사용할 수 있도록 최적화되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-192">Compliant mode is optimized for third-party applications.</span></span>  
  
#### <a name="data-regions"></a><span data-ttu-id="3af85-193">데이터 영역</span><span class="sxs-lookup"><span data-stu-id="3af85-193">Data Regions</span></span>  
 <span data-ttu-id="3af85-194">파일의 첫 번째 행에만 열 머리글이 들어 있으며 각 행에는 동일한 개수의 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-194">Only the first row of the file contains the column headers and each row has the same number of columns.</span></span>  
  
#### <a name="formatting"></a><span data-ttu-id="3af85-195">서식</span><span class="sxs-lookup"><span data-stu-id="3af85-195">Formatting</span></span>  
 <span data-ttu-id="3af85-196">값에는 서식이 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-196">Values are unformatted.</span></span>  
  
##  <a name="interactivity"></a><a name="Interactivity"></a><span data-ttu-id="3af85-197">대화형 작업</span><span class="sxs-lookup"><span data-stu-id="3af85-197">Interactivity</span></span>  
 <span data-ttu-id="3af85-198">상호 작용은 이 렌더러에 의해 생성되는 어떤 CSV 형식에서도 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-198">Interactivity is not supported by either CSV formats generated by this renderer.</span></span> <span data-ttu-id="3af85-199">다음 대화형 요소는 렌더링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-199">The following interactive elements are not rendered:</span></span>  
  
-   <span data-ttu-id="3af85-200">하이퍼링크</span><span class="sxs-lookup"><span data-stu-id="3af85-200">Hyperlinks</span></span>  
  
-   <span data-ttu-id="3af85-201">표시 또는 숨기기</span><span class="sxs-lookup"><span data-stu-id="3af85-201">Show or Hide</span></span>  
  
-   <span data-ttu-id="3af85-202">문서 구조</span><span class="sxs-lookup"><span data-stu-id="3af85-202">Document Map</span></span>  
  
-   <span data-ttu-id="3af85-203">드릴스루 또는 클릭 광고 링크</span><span class="sxs-lookup"><span data-stu-id="3af85-203">Drillthrough or clickthrough links</span></span>  
  
-   <span data-ttu-id="3af85-204">최종 사용자 정렬</span><span class="sxs-lookup"><span data-stu-id="3af85-204">End user sort</span></span>  
  
-   <span data-ttu-id="3af85-205">고정 머리글</span><span class="sxs-lookup"><span data-stu-id="3af85-205">Fixes headers</span></span>  
  
-   <span data-ttu-id="3af85-206">책갈피</span><span class="sxs-lookup"><span data-stu-id="3af85-206">Bookmarks</span></span>  
  

  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a><span data-ttu-id="3af85-207">장치 정보 설정</span><span class="sxs-lookup"><span data-stu-id="3af85-207">Device Information Settings</span></span>  
 <span data-ttu-id="3af85-208">디바이스 정보 설정을 변경하여 렌더링할 모드, 구분 기호로 사용할 문자, 텍스트 한정자 기본 문자열로 사용할 문자 등 이 렌더러의 일부 기본 설정을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3af85-208">You can change some default settings for this renderer, including which mode to render in, which characters to use as delimiters and which characters to use as the text qualifier default string, by changing the device information settings.</span></span> <span data-ttu-id="3af85-209">자세한 내용은 [CSV Device Information Settings](../csv-device-information-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3af85-209">For more information, see [CSV Device Information Settings](../csv-device-information-settings.md).</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="3af85-210">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3af85-210">See Also</span></span>  
 <span data-ttu-id="3af85-211">[Reporting Services &#40;보고서 작성기 및 SSRS의 페이지 매김&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3af85-211">[Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3af85-212">[보고서 작성기 및 SSRS&#41;&#40;렌더링 동작](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3af85-212">[Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="3af85-213">[여러 보고서 렌더링 확장 프로그램에 대 한 대화형 기능 &#40;보고서 작성기 및 SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="3af85-213">[Interactive Functionality for Different Report Rendering Extensions &#40;Report Builder and SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md) </span></span>  
 <span data-ttu-id="3af85-214">[보고서 항목 &#40;보고서 작성기 및 SSRS&#41;렌더링](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="3af85-214">[Rendering Report Items &#40;Report Builder and SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="3af85-215">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="3af85-215">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
