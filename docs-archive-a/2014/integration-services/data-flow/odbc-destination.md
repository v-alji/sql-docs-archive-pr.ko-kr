---
title: ODBC 대상 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.odbcdest.f1
ms.assetid: bffa63e0-c737-4b54-b4ea-495a400ffcf8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: beb29c511af62ba69ca0b9e2c595f61c57edab6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659590"
---
# <a name="odbc-destination"></a><span data-ttu-id="b1e3a-102">ODBC 대상</span><span class="sxs-lookup"><span data-stu-id="b1e3a-102">ODBC Destination</span></span>
  <span data-ttu-id="b1e3a-103">ODBC 대상은 ODBC 지원 데이터베이스 테이블로 데이터를 대량 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-103">The ODBC destination bulk loads data into ODBC-supported database tables.</span></span> <span data-ttu-id="b1e3a-104">ODBC 대상은 ODBC 연결 관리자를 사용하여 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-104">The ODBC destination uses an ODBC connection manager to connect to the data source.</span></span>  
  
 <span data-ttu-id="b1e3a-105">ODBC 대상에는 입력 열과 대상 데이터 원본 열 사이의 매핑이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-105">An ODBC destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="b1e3a-106">입력 열을 모든 대상 열에 매핑할 필요는 없지만 대상 열에 매핑된 입력 열이 없으면 대상 열의 속성에 따라 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-106">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors may occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="b1e3a-107">예를 들어 대상 열에 Null 값이 허용되지 않는 경우에는 입력 열을 해당 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-107">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="b1e3a-108">유형이 다른 열을 매핑할 수도 있지만 입력 데이터가 대상 열 유형과 호환되지 않으면 런타임에 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-108">In addition, columns of different types can be mapped, however if the input data is not compatible for the destination column type, an error occurs at runtime.</span></span> <span data-ttu-id="b1e3a-109">오류 동작 설정에 따라 오류가 무시되거나, 오류가 발생하거나, 오류 출력에 행이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-109">Depending on the error behavior setting, the error will be ignored, cause a failure, or the row is sent to the error output.</span></span>  
  
 <span data-ttu-id="b1e3a-110">ODBC 대상에는 하나의 일반 출력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-110">The ODBC destination has one regular output and one error output.</span></span>  
  
##  <a name="load-options"></a><a name="BKMK_odbcdestination_loadoptions"></a> <span data-ttu-id="b1e3a-111">로드 옵션</span><span class="sxs-lookup"><span data-stu-id="b1e3a-111">Load Options</span></span>  
 <span data-ttu-id="b1e3a-112">ODBC 대상은 두 액세스 로드 모듈 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-112">The ODBC destination can use one of two access load modules.</span></span> <span data-ttu-id="b1e3a-113">[ODBC 원본 편집기&#40;연결 관리자 페이지&#41;](../odbc-source-editor-connection-manager-page.md)에서 모드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-113">You set the mode in the [ODBC Source Editor &#40;Connection Manager Page&#41;](../odbc-source-editor-connection-manager-page.md).</span></span> <span data-ttu-id="b1e3a-114">두 모드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-114">The two modes are:</span></span>  
  
-   <span data-ttu-id="b1e3a-115">**일괄 처리**: 이 모드에서는 ODBC 대상이 인식된 ODBC 공급자 기능을 기반으로 가장 효율적인 삽입 메서드를 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-115">**Batch**: In this mode the ODBC destination attempts to use the most efficient insertion method based on the perceived ODBC provider capabilities.</span></span> <span data-ttu-id="b1e3a-116">대부분의 요즘 ODBC 공급자에게 이는 매개 변수가 포함된 INSERT 문을 준비한 다음 행 단위 배열 매개 변수 바인딩을 사용해야 함을 의미할 수 있습니다(배열 크기는 **BatchSize** 속성으로 제어됨).</span><span class="sxs-lookup"><span data-stu-id="b1e3a-116">For most modern ODBC providers, this would mean preparing an INSERT statement with parameters and then using a row-wise array parameter binding (where the array size is controlled by the **BatchSize** property).</span></span> <span data-ttu-id="b1e3a-117">**일괄 처리** 를 선택했는데 공급자가 이 메서드를 지원하지 않으면 ODBC 대상이 **행 단위** 모드로 자동 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-117">If you select **Batch** and the provider does not support this method, the ODBC destination automatically switches to the **Row-by-row** mode.</span></span>  
  
-   <span data-ttu-id="b1e3a-118">**행 단위**: 이 모드에서는 ODBC 대상이 매개 변수가 포함된 INSERT 문을 준비하고 **SQL 실행** 을 사용하여 한 번에 하나씩 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-118">**Row-by-row**: In this mode, the ODBC destination prepares an INSERT statement with parameters and uses **SQL Execute** to insert rows one at a time.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="b1e3a-119">오류 처리</span><span class="sxs-lookup"><span data-stu-id="b1e3a-119">Error Handling</span></span>  
 <span data-ttu-id="b1e3a-120">ODBC 대상에는 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-120">The ODBC destination has an error output.</span></span> <span data-ttu-id="b1e3a-121">구성 요소 오류 출력에 다음과 같은 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="b1e3a-122">**오류 코드**: 현재 오류에 해당하는 숫자입니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-122">**Error Code**: The number that corresponds to the current error.</span></span> <span data-ttu-id="b1e3a-123">오류 목록은 원본 데이터베이스에 대한 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-123">See the documentation for your source database for a list of errors.</span></span> <span data-ttu-id="b1e3a-124">SSIS 오류 코드 목록은 SSIS 오류 코드 및 메시지 참조를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-124">For a list of SSIS error codes, see the SSIS Error Code and Message Reference.</span></span>  
  
-   <span data-ttu-id="b1e3a-125">**오류 열**: 오류의 원인이 되는 원본 열입니다(변환 오류의 경우).</span><span class="sxs-lookup"><span data-stu-id="b1e3a-125">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="b1e3a-126">표준 출력 데이터 열입니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-126">The standard output data columns.</span></span>  
  
 <span data-ttu-id="b1e3a-127">오류 동작 설정에 따라 ODBC 대상은 추출 프로세스 중 발생하는 오류(데이터 변환, 잘림)를 오류 출력에 반환하는 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-127">Depending on the error behavior setting, the ODBC destination supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="b1e3a-128">자세한 내용은 [ODBC 원본 편집기&#40;오류 출력 페이지&#41;](../odbc-source-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-128">For more information, see [ODBC Source Editor &#40;Error Output Page&#41;](../odbc-source-editor-error-output-page.md).</span></span>  
  
## <a name="parallelism"></a><span data-ttu-id="b1e3a-129">병렬 처리</span><span class="sxs-lookup"><span data-stu-id="b1e3a-129">Parallelism</span></span>  
 <span data-ttu-id="b1e3a-130">동일한 컴퓨터 또는 서로 다른 컴퓨터에서 동일한 테이블 또는 서로 다른 테이블에 대해 병렬로 실행될 수 있는 ODBC 대상 구성 요소의 수에는 제한이 없습니다(일반적인 전역 세션 제한 제외).</span><span class="sxs-lookup"><span data-stu-id="b1e3a-130">There is no limitation on the number of ODBC destination components that can run in parallel against the same table or different tables, on the same machine or on different machines (other than normal global session limits).</span></span>  
  
 <span data-ttu-id="b1e3a-131">그러나 이용 중인 ODBC 공급자의 제한으로 인해 공급자를 통한 동시 연결 수가 제한될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-131">However, limitations of the ODBC provider being used may restrict the number of concurrent connections through the provider.</span></span> <span data-ttu-id="b1e3a-132">이러한 제한으로 인해 ODBC 대상에 대해 지원 가능한 병렬 인스턴스 수가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-132">These limitations limit the number of supported parallel instances possible for the ODBC destination.</span></span> <span data-ttu-id="b1e3a-133">SSIS 개발자는 이용 중인 모든 ODBC 공급자의 제한을 이해하고 SSIS 패키지를 작성할 때 해당 제한을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-133">The SSIS developer must be aware of the limitations of any ODBC provider being used and take them into consideration when building SSIS packages.</span></span>  
  
 <span data-ttu-id="b1e3a-134">또한 동일한 테이블로 동시에 로드할 경우 표준 레코드 잠금 때문에 성능이 저하될 수 있다는 사실을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-134">You must also be aware that concurrently loading into the same table may reduce performance because of standard record locking.</span></span> <span data-ttu-id="b1e3a-135">이는 로드되는 데이터와 테이블 구성에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-135">This depends on the data being loaded and on the table organization.</span></span>  
  
## <a name="troubleshooting-the-odbc-destination"></a><span data-ttu-id="b1e3a-136">ODBC 대상 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b1e3a-136">Troubleshooting the ODBC Destination</span></span>  
 <span data-ttu-id="b1e3a-137">ODBC 원본이 외부 데이터 공급자에 대해 수행하는 호출을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-137">You can log the calls that the ODBC source makes to external data providers.</span></span> <span data-ttu-id="b1e3a-138">이 로깅 기능을 사용하면 ODBC 대상이 외부 데이터 원본에 데이터를 저장할 때 발생하는 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-138">You can use this logging capability to troubleshoot the saving of data to external data sources that the ODBC destination performs.</span></span> <span data-ttu-id="b1e3a-139">ODBC 대상이 외부 데이터 공급자에 대해 수행하는 호출을 기록하려면 ODBC 드라이버 관리자 추적을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-139">To log the calls that the ODBC destination makes to external data providers, enable the ODBC driver manager trace.</span></span> <span data-ttu-id="b1e3a-140">자세한 내용은 *ODBC 데이터 원본 관리자를 사용하여 ODBC 추적을 생성하는 방법*에 대한 Microsoft 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-140">For more information, see the Microsoft documentation on *How To Generate an ODBC Trace with ODBC the Data Source Administrator*.</span></span>  
  
## <a name="configuring-the-odbc-destination"></a><span data-ttu-id="b1e3a-141">ODBC 대상 구성</span><span class="sxs-lookup"><span data-stu-id="b1e3a-141">Configuring the ODBC Destination</span></span>  
 <span data-ttu-id="b1e3a-142">SSIS 디자이너를 사용하거나 프로그래밍 방식으로 ODBC 대상을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-142">You can configure the ODBC destination programatically or through the SSIS Designer</span></span>  
  
 <span data-ttu-id="b1e3a-143">자세한 내용은 다음 항목 중 하나를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-143">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b1e3a-144">ODBC 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-144">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="b1e3a-145">ODBC 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-145">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="b1e3a-146">ODBC 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-146">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
 <span data-ttu-id="b1e3a-147">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-147">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="b1e3a-148">**고급 편집기** 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="b1e3a-148">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="b1e3a-149">**프로젝트의** 데이터 흐름 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 화면에서 ODBC 대상을 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-149">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the ODBC destination and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="b1e3a-150">고급 편집기 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [ODBC Destination Custom Properties](odbc-destination-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b1e3a-150">For more information about the properties that you can set in the Advanced Editor dialog box, see [ODBC Destination Custom Properties](odbc-destination-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1e3a-151">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b1e3a-151">In This Section</span></span>  
  
-   [<span data-ttu-id="b1e3a-152">ODBC 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-152">ODBC Destination Editor &#40;Error Output Page&#41;</span></span>](../odbc-destination-editor-error-output-page.md)  
  
-   [<span data-ttu-id="b1e3a-153">ODBC 대상 편집기&#40;매핑 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-153">ODBC Destination Editor &#40;Mappings Page&#41;</span></span>](../odbc-destination-editor-mappings-page.md)  
  
-   [<span data-ttu-id="b1e3a-154">ODBC 대상 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="b1e3a-154">ODBC Destination Editor &#40;Connection Manager Page&#41;</span></span>](../odbc-destination-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="b1e3a-155">ODBC 대상을 사용하여 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="b1e3a-155">Load Data by Using the ODBC Destination</span></span>](odbc-destination.md)  
  
-   [<span data-ttu-id="b1e3a-156">ODBC 대상 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="b1e3a-156">ODBC Destination Custom Properties</span></span>](odbc-destination-custom-properties.md)  
  
  
