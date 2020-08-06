---
title: CDC 원본 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 064c25b129364dfcd813d71a462586303dd4ff60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660089"
---
# <a name="cdc-source"></a><span data-ttu-id="dae0a-102">CDC 원본</span><span class="sxs-lookup"><span data-stu-id="dae0a-102">CDC Source</span></span>
  <span data-ttu-id="dae0a-103">CDC 원본은 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 변경 테이블에서 특정 범위의 변경 데이터를 읽고 변경 내용을 다른 SSIS 다운스트림 구성 요소로 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-103">The CDC source reads a range of change data from [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] change tables and delivers the changes downstream to other SSIS components.</span></span>  
  
 <span data-ttu-id="dae0a-104">CDC 원본이 읽는 변경 데이터의 범위를 CDC 처리 범위라고 합니다. 이 범위는 현재 데이터 흐름이 시작되기 전에 실행되는 CDC 제어 태스크에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-104">The range of change data read by the CDC source is called the CDC Processing Range and is determine by the CDC Control task that is executed before the current data flow starts.</span></span> <span data-ttu-id="dae0a-105">CDC 처리 범위는 테이블 그룹의 CDC 처리 상태를 유지 관리하는 패키지 변수의 값에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-105">The CDC Processing Range is derived from the value of a package variable that maintains the state of the CDC processing for a group of tables.</span></span>  
  
 <span data-ttu-id="dae0a-106">CDC 원본은 데이터베이스 테이블, 뷰 또는 SQL 문을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-106">The CDC source extracts data from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database by using a database table, a view, or an SQL statement.</span></span>  
  
 <span data-ttu-id="dae0a-107">CDC 원본은 다음과 같은 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-107">The CDC source uses the following configurations:</span></span>  
  
-   <span data-ttu-id="dae0a-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 데이터베이스에 액세스하기 위한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="dae0a-108">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ADO.NET connection manager to access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC database.</span></span> <span data-ttu-id="dae0a-109">CDC 원본 연결 구성에 대한 자세한 내용은 [CDC 원본 편집기&#40;연결 관리자 페이지&#41;](../cdc-source-editor-connection-manager-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dae0a-109">For more information about configuring the CDC source connection, see [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).</span></span>  
  
-   <span data-ttu-id="dae0a-110">CDC용으로 설정된 테이블</span><span class="sxs-lookup"><span data-stu-id="dae0a-110">A table enabled for CDC.</span></span>  
  
-   <span data-ttu-id="dae0a-111">선택한 테이블에 대한 캡처 인스턴스의 이름(둘 이상이 있는 경우)</span><span class="sxs-lookup"><span data-stu-id="dae0a-111">The name of the capture instance of the selected table (if more-than-one exists).</span></span>  
  
-   <span data-ttu-id="dae0a-112">변경 처리 모드</span><span class="sxs-lookup"><span data-stu-id="dae0a-112">The change processing mode.</span></span>  
  
-   <span data-ttu-id="dae0a-113">CDC 처리 범위 결정의 기준이 되는 CDC 상태 패키지 변수의 이름.</span><span class="sxs-lookup"><span data-stu-id="dae0a-113">The name of the CDC state package variable based on which the CDC Processing range is determined.</span></span> <span data-ttu-id="dae0a-114">CDC 원본은 해당 변수를 수정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-114">The CDC source does not modify that variable.</span></span>  
  
 <span data-ttu-id="dae0a-115">CDC 원본에 의해 반환되는 데이터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC 함수인 **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** 또는 **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (사용 가능한 경우)에 의해 반환되는 데이터와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-115">The data returned by the CDC Source is the same as that returned by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC functions **cdc.fn_cdc_get_all_changes_\<capture-instance-name>** or **cdc.fn_cdc_get_net_changes_\<capture-instance-name>** (when available).</span></span> <span data-ttu-id="dae0a-116">현재 처리 범위가 테이블의 초기 로드와 겹칠 수 있는지 여부를 나타내는 **__$initial_processing** 열만 선택적으로 추가될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-116">The only optional addition is the column, **__$initial_processing** that indicates whether the current processing range can overlap with an initial load of the table.</span></span> <span data-ttu-id="dae0a-117">초기 처리에 대한 자세한 내용은 [CDC Control Task](../control-flow/cdc-control-task.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dae0a-117">For more information about initial processing, see [CDC Control Task](../control-flow/cdc-control-task.md).</span></span>  
  
 <span data-ttu-id="dae0a-118">CDC 원본에는 하나의 일반 출력과 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-118">The CDC source has one regular output and one error output.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="dae0a-119">오류 처리</span><span class="sxs-lookup"><span data-stu-id="dae0a-119">Error Handling</span></span>  
 <span data-ttu-id="dae0a-120">CDC 원본에는 하나의 오류 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-120">The CDC source has an error output.</span></span> <span data-ttu-id="dae0a-121">구성 요소 오류 출력에 다음과 같은 출력 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-121">The component error output includes the following output columns:</span></span>  
  
-   <span data-ttu-id="dae0a-122">**오류 코드**: 값은 항상 -1입니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-122">**Error Code**: The value is always -1.</span></span>  
  
-   <span data-ttu-id="dae0a-123">**오류 열**: 오류의 원인이 되는 원본 열입니다(변환 오류의 경우).</span><span class="sxs-lookup"><span data-stu-id="dae0a-123">**Error Column**: The source column causing the error (for conversion errors).</span></span>  
  
-   <span data-ttu-id="dae0a-124">**오류 행 열**: 오류의 원인이 되는 레코드 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-124">**Error Row Columns**: The record data that causes the error.</span></span>  
  
 <span data-ttu-id="dae0a-125">오류 동작 설정에 따라 CDC 원본은 추출 프로세스 중 발생하는 오류(데이터 변환, 잘림)를 오류 출력에 반환하는 작업을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-125">Depending on the error behavior setting, the CDC source supports returning errors (data conversion, truncation) that occur during the extraction process in the error output.</span></span> <span data-ttu-id="dae0a-126">자세한 내용은 [CDC 원본 편집기&#40;오류 출력 페이지&#41;](../cdc-source-editor-error-output-page.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dae0a-126">For more information, see [CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md).</span></span>  
  
## <a name="data-type-support"></a><span data-ttu-id="dae0a-127">데이터 형식 지원</span><span class="sxs-lookup"><span data-stu-id="dae0a-127">Data Type Support</span></span>  
 <span data-ttu-id="dae0a-128">Microsoft용 CDC 원본 구성 요소는 올바른 SSIS 데이터 형식에 매핑되는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-128">The CDC source component for Microsoft supports all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, which are mapped to the correct SSIS data types.</span></span>  
  
## <a name="troubleshooting-the-cdc-source"></a><span data-ttu-id="dae0a-129">CDC 원본 문제 해결</span><span class="sxs-lookup"><span data-stu-id="dae0a-129">Troubleshooting the CDC Source</span></span>  
 <span data-ttu-id="dae0a-130">다음에는 CDC 원본 문제 해결에 대한 정보가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-130">The following contains information on troubleshooting the CDC source.</span></span>  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a><span data-ttu-id="dae0a-131">이 스크립트를 사용하여 문제를 격리하고 SQL Server Management Studio에서 해당 문제를 재현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-131">Use this script to isolate problems and reproduce them in SQL Server Management Studio</span></span>  
 <span data-ttu-id="dae0a-132">CDC 원본 작업은 CDC 원본을 호출하기 전에 실행되는 CDC 제어 태스크의 작업으로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-132">The CDC source operation is governed by the operation of the CDC Control task executed before invoking the CDC source.</span></span> <span data-ttu-id="dae0a-133">CDC 제어 태스크는 시작 및 끝 LSN을 포함하기 위해 CDC 상태 패키지 변수의 값을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-133">The CDC Control task prepares the value of the CDC state package variable to contain the start and end LSNs.</span></span> <span data-ttu-id="dae0a-134">이 태스크는 다음 스크립트에 해당하는 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-134">It performs function equivalent to the following script:</span></span>  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 <span data-ttu-id="dae0a-135">각 항목이 나타내는 의미는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-135">where:</span></span>  
  
-   <span data-ttu-id="dae0a-136">\<cdc-enabled-database-name>은 변경하는 테이블이 포함된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-136">\<cdc-enabled-database-name> is the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database containing the change tables.</span></span>  
  
-   <span data-ttu-id="dae0a-137">\<value-from-state-cs>는 CDC 상태 변수에 CS/\<value-from-state-cs>/로 나타나는 값입니다. CS는 현재 처리 범위 시작을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-137">\<value-from-state-cs> is the value that appears in the CDC state variable as CS/\<value-from-state-cs>/ (CS stands for Current-processing-range-Start).</span></span>  
  
-   <span data-ttu-id="dae0a-138">\<value-from-state-ce>는 CDC 상태 변수에 CE/\<value-from-state-cs>/로 나타나는 값입니다. CE는 현재 처리 범위 끝을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-138">\<value-from-state-ce> is the value that appears in the CDC state variable as CE/\<value-from-state-cs>/ (CE stands for Current-processing-range-End).</span></span>  
  
-   <span data-ttu-id="dae0a-139">\<mode>는 CDC 처리 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-139">\<mode> are the CDC processing modes.</span></span> <span data-ttu-id="dae0a-140">처리 모드에는 **모두**, **이전 값이 포함된 모두**, **순**, **업데이트 마스크를 사용한 순 변경 내용**, **병합을 사용한 순 변경 내용**중 하나의 값이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-140">The processing modes have one of the following values **All**, **All with Old Values**, **Net**, **Net with Update Mask**, **Net with Merge**.</span></span>  
  
 <span data-ttu-id="dae0a-141">이 스크립트는 오류를 식별하고 재현하기가 쉬운 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 문제를 재현하여 문제를 격리하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-141">This script helps isolate problems by reproducing them in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], where it is easy to reproduce and identify errors.</span></span>  
  
#### <a name="sql-server-error-message"></a><span data-ttu-id="dae0a-142">SQL Server 오류 메시지</span><span class="sxs-lookup"><span data-stu-id="dae0a-142">SQL Server Error Message</span></span>  
 <span data-ttu-id="dae0a-143">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 다음 메시지가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-143">The following message may be returned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
 <span data-ttu-id="dae0a-144">**프로시저 또는 함수 cdc.fn_cdc_get_net_changes_\<..>에 제공된 인수 개수가 부족합니다.**</span><span class="sxs-lookup"><span data-stu-id="dae0a-144">**An insufficient number of arguments were supplied for the procedure or function cdc.fn_cdc_get_net_changes_\<..>.**</span></span>  
  
 <span data-ttu-id="dae0a-145">이 오류는 인수가 누락되었음을 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-145">This error does not indicate that an argument is missing.</span></span> <span data-ttu-id="dae0a-146">대신 CDC 상태 변수의 시작 또는 끝 LSN 값이 잘못되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-146">It means that the start or end LSN values in the CDC state variable are invalid.</span></span>  
  
## <a name="configuring-the-cdc-source"></a><span data-ttu-id="dae0a-147">CDC 원본 구성</span><span class="sxs-lookup"><span data-stu-id="dae0a-147">Configuring the CDC Source</span></span>  
 <span data-ttu-id="dae0a-148">SSIS 디자이너를 사용하거나 프로그래밍 방식으로 CDC 원본을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-148">You can configure the CDC source programmatically or through the SSIS Designer.</span></span>  
  
 <span data-ttu-id="dae0a-149">자세한 내용은 다음 항목 중 하나를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dae0a-149">For more information, see one of the following topics:</span></span>  
  
-   [<span data-ttu-id="dae0a-150">CDC 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-150">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="dae0a-151">CDC 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-151">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="dae0a-152">CDC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-152">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
 <span data-ttu-id="dae0a-153">**고급 편집기** 대화 상자에는 프로그래밍 방식으로 설정할 수 있는 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-153">The **Advanced Editor** dialog box contains the properties that can be set programmatically.</span></span>  
  
 <span data-ttu-id="dae0a-154">**고급 편집기** 대화 상자를 열려면</span><span class="sxs-lookup"><span data-stu-id="dae0a-154">To open the **Advanced Editor** dialog box:</span></span>  
  
-   <span data-ttu-id="dae0a-155">**프로젝트의** 데이터 흐름 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 화면에서 CDC 원본을 마우스 오른쪽 단추로 클릭하고 **고급 편집기 표시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dae0a-155">In the **Data Flow** screen of your [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] project, right click the CDC source and select **Show Advanced Editor**.</span></span>  
  
 <span data-ttu-id="dae0a-156">**고급 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [CDC Source Custom Properties](cdc-source-custom-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="dae0a-156">For more information about the properties that you can set in the **Advanced Editor** dialog box, see [CDC Source Custom Properties](cdc-source-custom-properties.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dae0a-157">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="dae0a-157">In This Section</span></span>  
  
-   [<span data-ttu-id="dae0a-158">CDC 원본 편집기&#40;연결 관리자 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-158">CDC Source Editor &#40;Connection Manager Page&#41;</span></span>](../cdc-source-editor-connection-manager-page.md)  
  
-   [<span data-ttu-id="dae0a-159">CDC 원본 편집기&#40;열 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-159">CDC Source Editor &#40;Columns Page&#41;</span></span>](../cdc-source-editor-columns-page.md)  
  
-   [<span data-ttu-id="dae0a-160">CDC 원본 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="dae0a-160">CDC Source Editor &#40;Error Output Page&#41;</span></span>](../cdc-source-editor-error-output-page.md)  
  
-   [<span data-ttu-id="dae0a-161">CDC 원본 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="dae0a-161">CDC Source Custom Properties</span></span>](cdc-source-custom-properties.md)  
  
-   [<span data-ttu-id="dae0a-162">CDC 원본을 사용하여 변경 데이터 추출</span><span class="sxs-lookup"><span data-stu-id="dae0a-162">Extract Change Data Using the CDC Source</span></span>](cdc-source.md)  
  
## <a name="related-content"></a><span data-ttu-id="dae0a-163">관련 내용</span><span class="sxs-lookup"><span data-stu-id="dae0a-163">Related Content</span></span>  
  
-   <span data-ttu-id="dae0a-164">mattmasson.com의 블로그 항목 - [CDC 원본 처리 모드](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/)</span><span class="sxs-lookup"><span data-stu-id="dae0a-164">Blog entry, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/), on mattmasson.com.</span></span>  
  
  
