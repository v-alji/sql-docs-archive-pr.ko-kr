---
title: ODBC 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcsource.f1
ms.assetid: abcf34eb-9140-4100-82e6-b85bccd22abe
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 792557839d60f34bdf944dab150959d4df7cb8cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648478"
---
# <a name="odbc-source"></a><span data-ttu-id="aef6b-102">ODBC 원본</span><span class="sxs-lookup"><span data-stu-id="aef6b-102">ODBC Source</span></span>
  <span data-ttu-id="aef6b-103">ODBC 원본은 데이터베이스 테이블, 뷰 또는 SQL 문을 사용하여 ODBC 지원 데이터베이스에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-103">The ODBC source extracts data from ODBC-supported database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="aef6b-104">ODBC 원본은 데이터 추출을 위한 다음 데이터 액세스 모드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-104">The ODBC source has the following data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="aef6b-105">테이블 또는 뷰</span><span class="sxs-lookup"><span data-stu-id="aef6b-105">A table or view.</span></span>  
  
-   <span data-ttu-id="aef6b-106">SQL 문의 결과</span><span class="sxs-lookup"><span data-stu-id="aef6b-106">The results of an SQL statement.</span></span>  
  
 <span data-ttu-id="aef6b-107">원본은 이용할 공급자를 지정하는 ODBC 연결 관리자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-107">The source uses an ODBC connection manager, which specifies the provider to use.</span></span>  
  
 <span data-ttu-id="aef6b-108">ODBC 원본에는 원본 데이터 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-108">An ODBC source includes the source data output columns.</span></span> <span data-ttu-id="aef6b-109">출력 열이 ODBC 대상에서 대상 열에 매핑될 경우 대상 열에 매핑된 출력 열이 없으면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-109">When output columns are mapped in the ODBC destination to the destination columns, errors may occur if no output columns are mapped to the destination columns.</span></span> <span data-ttu-id="aef6b-110">유형이 다른 열을 매핑할 수 있지만 출력 데이터가 대상과 호환되지 않으면 런타임에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-110">Columns of different types can be mapped, however if the output data is not compatible for the destination then an error occurs at runtime.</span></span> <span data-ttu-id="aef6b-111">오류 동작 설정에 따라 오류가 무시되거나, 오류가 발생하거나, 오류 출력에 행이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-111">Depending on the error behavior, setting the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="aef6b-112">ODBC 원본에는 하나의 일반 출력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-112">The ODBC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="aef6b-113">오류 처리</span><span class="sxs-lookup"><span data-stu-id="aef6b-113">Error Handling</span></span>  
 <span data-ttu-id="aef6b-114">ODBC 원본에는 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-114">The ODBC source has an error output.</span></span> <span data-ttu-id="aef6b-115">구성 요소 오류 출력에 다음과 같은 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-115">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="aef6b-116">**오류 코드**: 현재 오류에 해당하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-116">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="aef6b-117">오류 목록은 현재 사용하고 있는 ODBC 지원 데이터베이스에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-117">See the documentation for the ODBC-supported database you are using for a list of errors.</span></span> <span data-ttu-id="aef6b-118">SSIS 오류 코드 목록은 SSIS 오류 코드 및 메시지 참조를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-118">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="aef6b-119">**오류 열**: 오류의 원인이 되는 원본 열입니다(변환 오류의 경우).</span><span class="sxs-lookup"><span data-stu-id="aef6b-119">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="aef6b-120">표준 출력 데이터 열입니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-120">The standard output data columns.</span></span>  
  
 <span data-ttu-id="aef6b-121">오류 동작 설정에 따라 ODBC 원본은 추출 프로세스 중 발생하는 오류(데이터 변환, 잘림)를 오류 출력에 반환하는 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-121">Depending on the error behavior setting, the ODBC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="aef6b-122">자세한 내용은 [ODBC 대상 편집기&#40;연결 관리자 페이지&#41;](../odbc-destination-editor-connection-manager-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aef6b-122">For more information, see [ODBC Destination Editor &#40;Connection Manager Page&#41;](../odbc-destination-editor-connection-manager-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="aef6b-123">데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="aef6b-123">Data Type Support</span></span>  
 <span data-ttu-id="aef6b-124">ODBC 원본이 지원하는 데이터 형식에 대한 자세한 내용은 Connector for ODBC(Open Database Connectivity) by Attunity를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-124">For information about the data types supported by the ODBC source, see Connector for Open Database Connectivity (ODBC) by Attunity.</span></span>  
  
## <a name="extract-options"></a><span data-ttu-id="aef6b-125">추출 옵션</span><span class="sxs-lookup"><span data-stu-id="aef6b-125">Extract Options</span></span>  
 <span data-ttu-id="aef6b-126">ODBC 원본은 **일괄 처리** 또는 **행 단위** 모드에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-126">The ODBC source operates in either **Batch** or **Row-by-Row** mode.</span></span> <span data-ttu-id="aef6b-127">사용되는 모드는 **FetchMethod** 속성으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-127">The mode used is determined by the **FetchMethod** property.</span></span> <span data-ttu-id="aef6b-128">다음 목록에서는 이러한 모드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-128">The following list describes the modes.</span></span>  
  
-   <span data-ttu-id="aef6b-129">**일괄 처리**: 구성 요소가 인식된 ODBC 공급자 기능을 기반으로 가장 효율적인 인출 메서드를 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-129">**Batch**: The component attempts to use the most efficient fetch method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="aef6b-130">대부분의 최신 ODBC 공급자에게 이는 배열 바인딩을 사용한 SQLFetchScroll입니다(배열 크기는 **BatchSize** 속성으로 결정됨).</span><span class="sxs-lookup"><span data-stu-id="aef6b-130">For most modern ODBC providers, this is SQLFetchScroll with array binding (where the array size is determined by the **BatchSize** property).</span></span> <span data-ttu-id="aef6b-131">**일괄 처리** 를 선택했는데 공급자가 이 메서드를 지원하지 않으면 ODBC 대상이 **행 단위** 모드로 자동 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-131">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="aef6b-132">**행 단위**: 구성 요소가 SQLFetch를 사용하여 한 번에 하나씩 행을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-132">**Row-by Row**: The component uses SQLFetch to retrieve the rows one at a time.</span></span>  
  
 <span data-ttu-id="aef6b-133">**FetchMethod** 속성에 대한 자세한 내용은 [ODBC Source Custom Properties](odbc-source-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-133">For more information about the **FetchMethod** property, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="aef6b-134">병렬 처리</span><span class="sxs-lookup"><span data-stu-id="aef6b-134">Parallelism</span></span>  
 <span data-ttu-id="aef6b-135">동일한 컴퓨터 또는 서로 다른 컴퓨터에서 동일한 테이블 또는 서로 다른 테이블에 대해 병렬로 실행될 수 있는 ODBC 원본 구성 요소의 수에는 제한이 없습니다(일반적인 전역 세션 제한 제외).</span><span class="sxs-lookup"><span data-stu-id="aef6b-135">There is no limitation on the number of ODBC source components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="aef6b-136">그러나 이용 중인 ODBC 공급자의 제한으로 인해 공급자를 통한 동시 연결 수가 제한될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-136">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="aef6b-137">이러한 제한으로 인해 ODBC 원본에 대해 지원 가능한 병렬 인스턴스 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-137">These limitations limit the number of supported parallel instances possible for the ODBC source.</span></span> <span data-ttu-id="aef6b-138">SSIS 개발자는 이용 중인 모든 ODBC 공급자의 제한을 이해하고 SSIS 패키지를 작성할 때 해당 제한을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-138">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
## <a name="troubleshooting-the-odbc-source"></a><span data-ttu-id="aef6b-139">ODBC 원본 문제 해결</span><span class="sxs-lookup"><span data-stu-id="aef6b-139">Troubleshooting the ODBC Source</span></span>  
 <span data-ttu-id="aef6b-140">ODBC 원본이 외부 데이터 공급자에 대해 수행하는 호출을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-140">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="aef6b-141">이 로깅 기능을 사용하면 ODBC 원본이 외부 데이터 원본에서 데이터를 로드할 때 발생하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-141">You can use this logging capability to troubleshoot the loading of data from external data sources that the ODBC source performs.</span></span> <span data-ttu-id="aef6b-142">ODBC 원본이 외부 데이터 공급자에 대해 수행하는 호출을 기록하려면 ODBC 드라이버 관리자 추적을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-142">To log the calls that the ODBC source makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="aef6b-143">자세한 내용은 *ODBC 데이터 원본 관리자를 사용하여 ODBC 추적을 생성하는 방법*에 대한 Microsoft 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-143">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator.*</span></span>  
  
## <a name="configuring-the-odbc-source"></a><span data-ttu-id="aef6b-144">ODBC 원본 구성</span><span class="sxs-lookup"><span data-stu-id="aef6b-144">Configuring the ODBC Source</span></span>  
 <span data-ttu-id="aef6b-145">SSIS 디자이너를 사용하거나 프로그래밍 방식으로 ODBC 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-145">You can configure the ODBC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="aef6b-146">자세한 내용은 다음 항목 중 하나를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-146">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="aef6b-147">ODBC 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-147">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="aef6b-148">ODBC 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-148">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="aef6b-149">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-149">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="aef6b-150">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-150">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="aef6b-151">**고급 편집기** 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="aef6b-151">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="aef6b-152">**프로젝트의** 데이터 흐름 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 화면에서 ODBC 원본을 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aef6b-152">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="aef6b-153">고급 편집기 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [ODBC Source Custom Properties](odbc-source-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="aef6b-153">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Source Custom Properties](odbc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aef6b-154">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="aef6b-154">In This Section</span></span>  
  
-   [<span data-ttu-id="aef6b-155">ODBC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-155">ODBC Source Editor &#40;Error Output Page&#41;</span></span>](../odbc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="aef6b-156">ODBC 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-156">ODBC Source Editor &#40;Columns Page&#41;</span></span>](../odbc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="aef6b-157">ODBC 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="aef6b-157">ODBC Source Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="aef6b-158">ODBC 원본을 사용하여 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="aef6b-158">Extract Data by Using the ODBC Source</span></span>](odbc-source.md)  
  
-   [<span data-ttu-id="aef6b-159">ODBC Source Custom Properties</span><span class="sxs-lookup"><span data-stu-id="aef6b-159">ODBC Source Custom Properties</span></span>](odbc-source-custom-properties.md)  
  
  
