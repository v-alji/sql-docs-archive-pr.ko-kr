---
title: 변경 데이터 캡처(SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental loads [SQL Server change data capture]
- change data capture [SQL Server], Integration Services and
ms.assetid: c4aaba1b-73e5-4187-a97b-61c10069cc5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55293d4e2caa4c31cb004a2cdf1cda99769c77e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735523"
---
# <a name="change-data-capture-ssis"></a><span data-ttu-id="91778-102">변경 데이터 캡처(SSIS)</span><span class="sxs-lookup"><span data-stu-id="91778-102">Change Data Capture (SSIS)</span></span>
  <span data-ttu-id="91778-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 변경 데이터 캡처는 원본 테이블에서 데이터 마트 및 데이터 웨어하우스로의 증분 로드를 효율적으로 수행하는 문제에 대한 효과적인 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], change data capture offers an effective solution to the challenge of efficiently performing incremental loads from source tables to data marts and data warehouses.</span></span>

## <a name="what-is-change-data-capture"></a><span data-ttu-id="91778-104">변경 데이터 캡처 정의</span><span class="sxs-lookup"><span data-stu-id="91778-104">What is Change Data Capture?</span></span>
 <span data-ttu-id="91778-105">시간이 지나면서 원본 테이블은 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="91778-105">Source tables change over time.</span></span> <span data-ttu-id="91778-106">이러한 테이블을 기반으로 하는 데이터 마트나 데이터 웨어하우스에도 이러한 변경 내용이 반영되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-106">A data mart or data warehouse that is based on those tables needs to reflect these changes.</span></span> <span data-ttu-id="91778-107">그러나 전체 원본의 스냅샷을 주기적으로 복사하는 프로세스에는 시간과 리소스가 너무 많이 소모됩니다.</span><span class="sxs-lookup"><span data-stu-id="91778-107">However, a process that periodically copies a snapshot of the entire source consumes too much time and resources.</span></span> <span data-ttu-id="91778-108">또한 타임스탬프 열, 트리거 또는 복잡한 쿼리를 비롯한 대체 방법을 사용하면 성능이 저하되고 복잡성이 증가되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-108">Alternate approaches that include timestamp columns, triggers, or complex queries often hurt performance and increase complexity.</span></span> <span data-ttu-id="91778-109">따라서 소비자가 데이터의 대상 표현에 쉽게 적용할 수 있도록 구조화된 안정적인 변경 데이터 스트림이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-109">What is needed is a reliable stream of change data that is structured so that it can easily be applied by consumers to target representations of the data.</span></span> <span data-ttu-id="91778-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 변경 데이터 캡처가 이러한 솔루션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-110">Change data capture in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provides this solution.</span></span>

 <span data-ttu-id="91778-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 의 변경 데이터 캡처 기능은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 테이블에 적용된 삽입, 업데이트 및 삭제 작업을 캡처하고 변경 내용에 대한 세부 정보를 쉽게 사용할 수 있는 관계형 형식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91778-111">The change data capture feature of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] captures insert, update, and delete activity applied to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables, and makes the details of the changes available in an easily-consumed, relational format.</span></span> <span data-ttu-id="91778-112">변경 데이터 캡처에 사용되는 변경 테이블에는 행 단위로 발생한 변경 내용을 이해하는 데 필요한 메타데이터뿐만 아니라 추적된 원본 테이블의 열 구조를 미러링하는 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="91778-112">The change tables used by change data capture contain columns that mirror the column structure of the tracked source tables, along with the metadata needed to understand the changes that have occurred on a row by row basis.</span></span>

> [!NOTE]
>  <span data-ttu-id="91778-113">변경 데이터 캡처는 일부 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]버전에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-113">Change data capture is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="91778-114">버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQL Server 2014 버전에서 지 원하는 기능](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="91778-114">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>

## <a name="how-change-data-capture-works-in-integration-services"></a><span data-ttu-id="91778-115">Integration Services에서의 변경 데이터 캡처 작동 방식</span><span class="sxs-lookup"><span data-stu-id="91778-115">How Change Data Capture Works in Integration Services</span></span>
 <span data-ttu-id="91778-116">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 패키지는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에서 변경 데이터를 쉽게 수집하여 데이터 웨어하우스에 대한 증분 로드를 효율적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-116">An [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package can easily harvest the change data in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] databases to perform efficient incremental loads to a data warehouse.</span></span> <span data-ttu-id="91778-117">그러나 사용자가 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 를 사용하여 변경 데이터를 로드하려면 먼저 사용자가 변경 내용을 캡처하려는 데이터베이스 및 테이블에서 관리자가 변경 데이터 캡처를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-117">However, before you can use [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] to load change data, an administrator must enable change data capture on the database and the tables from which you want to capture changes.</span></span> <span data-ttu-id="91778-118">데이터베이스에서 변경 데이터 캡처를 구성하는 방법은 [변경 데이터 캡처 설정 및 해제&#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91778-118">For more information on how to configure change data capture on a database, see [Enable and Disable Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-data-capture-sql-server.md).</span></span>

 <span data-ttu-id="91778-119">관리자가 데이터베이스에서 변경 데이터 캡처를 설정하면 사용자가 변경 데이터를 증분 로드하는 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-119">Once an administrator has enabled change data capture on the database, you can create a package that performs an incremental load of the change data.</span></span> <span data-ttu-id="91778-120">다음 다이어그램에서는 단일 테이블에서 증분 로드를 수행하는 패키지를 만드는 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="91778-120">The following diagram shows the steps for creating such a package that performs an incremental load from a single table:</span></span>

 <span data-ttu-id="91778-121">![변경 데이터 캡처 패키지 생성 단계](../media/cdc-package-creation.gif "변경 데이터 캡처 패키지 생성 단계")</span><span class="sxs-lookup"><span data-stu-id="91778-121">![Change Data Capture Package Creation Steps](../media/cdc-package-creation.gif "Change Data Capture Package Creation Steps")</span></span>

 <span data-ttu-id="91778-122">위의 다이어그램에서 볼 수 있듯이 변경된 데이터를 증분 로드하는 패키지를 만드는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-122">As shown in the previous diagram, creating a package that performs an incremental load of changed data involves the following steps:</span></span>

 <span data-ttu-id="91778-123">**1단계: 제어 흐름 디자인** 패키지의 제어 흐름에서 다음 태스크를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-123">**Step 1: Designing the Control Flow** In the control flow in the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="91778-124">검색하려는 원본 데이터에 대한 변경 간격의 시작 및 종료 `datetime` 값을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-124">Calculate the starting and ending `datetime` values for the interval of changes to the source data that you want to retrieve.</span></span>

     <span data-ttu-id="91778-125">이러한 값을 계산하려면 SQL 실행 태스크를 사용하거나 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 식에 `datetime` 함수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-125">To calculate these values, use an Execute SQL task or [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] expressions with `datetime` functions.</span></span> <span data-ttu-id="91778-126">그런 다음 패키지에서 나중에 사용하기 위해 이러한 엔드포인트를 패키지 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-126">You then store these endpoints in package variables for use later in the package.</span></span>

     <span data-ttu-id="91778-127">**자세한 내용:**  [변경 데이터의 간격 지정](specify-an-interval-of-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="91778-127">**For more information:**  [Specify an Interval of Change Data](specify-an-interval-of-change-data.md)</span></span>

-   <span data-ttu-id="91778-128">선택한 간격에 대한 변경 데이터가 준비되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-128">Determine whether the change data for the selected interval is ready.</span></span> <span data-ttu-id="91778-129">비동기 캡처 프로세스에서 선택한 엔드포인트에 아직 도달하지 않았을 수 있기 때문에 이 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-129">This step is necessary because the asynchronous capture process might not yet have reached the selected endpoint.</span></span>

     <span data-ttu-id="91778-130">데이터가 준비되었는지 여부를 확인하려면 필요한 경우 선택한 간격에 대한 변경 데이터가 준비될 때까지 실행을 지연하는 For 루프 컨테이너로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-130">To determine whether the data is ready, start with a For Loop container to delay execution, if necessary, until the change data for the selected interval is ready.</span></span> <span data-ttu-id="91778-131">해당 루프 컨테이너 내에서 SQL 실행 태스크를 사용하여 변경 데이터 캡처에 의해 유지되는 시간 매핑 테이블을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-131">Inside the loop container, use an Execute SQL task to query the time mapping tables maintained by change data capture.</span></span> <span data-ttu-id="91778-132">그런 다음 필요한 경우 `Thread.Sleep` 메서드를 호출하는 스크립트 태스크 또는 `WAITFOR` 문이 있는 다른 SQL 실행 태스크를 사용하여 패키지 실행을 일시적으로 지연합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-132">Then, use a Script task that calls the `Thread.Sleep` method, or another Execute SQL task with a `WAITFOR` statement, to delay the execution of the package temporarily, if necessary.</span></span> <span data-ttu-id="91778-133">다른 스크립트 태스크를 사용하여 오류 상태나 시간 초과를 기록할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-133">Optionally, use another Script task to log an error condition or a timeout.</span></span>

     <span data-ttu-id="91778-134">**자세한 내용:**  [변경 데이터의 준비 여부 확인](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="91778-134">**For more information:**  [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>

-   <span data-ttu-id="91778-135">변경 데이터를 쿼리하는 데 사용할 쿼리 문자열을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-135">Prepare the query string that will be used to query for the change data.</span></span>

     <span data-ttu-id="91778-136">스크립트 태스크나 SQL 실행 태스크를 사용하여 변경 내용을 쿼리하는 데 사용할 SQL 문을 조합합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-136">Use a Script task or an Execute SQL task to assemble the SQL statement that will be used to query for changes.</span></span>

     <span data-ttu-id="91778-137">**자세한 내용:**  [변경 데이터에 대한 쿼리 준비](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="91778-137">**For more information:**  [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>

 <span data-ttu-id="91778-138">**2 단계: 변경 데이터에 대 한 쿼리 설정** 데이터를 쿼리 하는 테이블 반환 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="91778-138">**Step 2: Setting Up the Query for Change Data** Create the table-valued function that will query for the data.</span></span>

 <span data-ttu-id="91778-139">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 쿼리를 개발하고 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-139">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to develop and save the query.</span></span>

 <span data-ttu-id="91778-140">**자세한 내용:**  [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="91778-140">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

 <span data-ttu-id="91778-141">**3단계: 데이터 흐름 디자인** 패키지의 데이터 흐름에서 다음 태스크를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-141">**Step 3: Designing the Data Flow** In the data flow of the package, the following tasks need to be defined:</span></span>

-   <span data-ttu-id="91778-142">변경 테이블에서 변경 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-142">Retrieve the change data from the change tables.</span></span>

     <span data-ttu-id="91778-143">데이터를 검색하려면 원본 구성 요소를 사용하여 선택한 간격 범위에 포함되는 변경 테이블의 변경 내용을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-143">To retrieve the data, use a source component to query the change tables for the changes that fall within the selected interval.</span></span> <span data-ttu-id="91778-144">원본에서는 앞에서 만든 Transact-SQL 테이블 반환 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-144">The source calls a Transact-SQL table-valued function that you must have previously created.</span></span>

     <span data-ttu-id="91778-145">**자세한 내용:**  [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="91778-145">**For more information:**  [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md)</span></span>

-   <span data-ttu-id="91778-146">처리를 위해 변경 내용을 삽입, 업데이트 및 삭제로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-146">Split the changes into inserts, updates, and deletes for processing.</span></span>

     <span data-ttu-id="91778-147">변경 내용을 분할하려면 조건부 분할 변환을 사용하여 적절한 처리를 위해 삽입, 업데이트 및 삭제를 다른 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-147">To split the changes, use a Conditional Split transformation to direct inserts, updates, and deletes to different outputs for appropriate processing.</span></span>

     <span data-ttu-id="91778-148">**자세한 내용:**  [삽입, 업데이트 및 삭제 처리](process-inserts-updates-and-deletes.md)</span><span class="sxs-lookup"><span data-stu-id="91778-148">**For more information:**  [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md)</span></span>

-   <span data-ttu-id="91778-149">대상에 삽입, 삭제 및 업데이트를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-149">Apply the inserts, deletes, and updates to the destination.</span></span>

     <span data-ttu-id="91778-150">대상에 변경 내용을 적용하려면 대상 구성 요소를 사용하여 대상에 삽입을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-150">To apply the changes to the destination, use a destination component to apply the inserts to the destination.</span></span> <span data-ttu-id="91778-151">또한 OLE DB 명령 변환에 매개 변수가 있는 UPDATE 및 DELETE 문을 사용하여 대상에 업데이트 및 삭제를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-151">Also, use OLE DB Command transformations with parameterized UPDATE and DELETE statements to apply updates and deletes to the destination.</span></span> <span data-ttu-id="91778-152">대상 구성 요소를 통해 임시 테이블에 해당 행을 저장하여 업데이트 및 삭제를 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-152">You can also apply updates and deletes by using destination components to save the rows to temporary tables.</span></span> <span data-ttu-id="91778-153">그런 다음 SQL 실행 태스크를 사용하여 임시 테이블의 대상에 대해 대량 업데이트 및 대량 삭제 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-153">Then, use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>

     <span data-ttu-id="91778-154">**자세한 내용:**  [대상에 변경 내용 적용](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="91778-154">**For more information:**  [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>

### <a name="change-data-from-multiple-tables"></a><span data-ttu-id="91778-155">여러 테이블의 데이터 변경</span><span class="sxs-lookup"><span data-stu-id="91778-155">Change Data from Multiple Tables</span></span>
 <span data-ttu-id="91778-156">위 다이어그램에 설명된 프로세스 및 단계는 단일 테이블에서 증분 로드를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-156">The process outlined in the previous diagram and steps involves an incremental load from a single table.</span></span> <span data-ttu-id="91778-157">여러 테이블에서 증분 로드를 수행하는 경우 전반적인 프로세스는 같습니다.</span><span class="sxs-lookup"><span data-stu-id="91778-157">When having to perform an incremental load from multiple tables, the overall process is the same.</span></span> <span data-ttu-id="91778-158">그러나 여러 테이블 처리에 맞게 패키지의 디자인을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-158">However, the design of the package needs to be changed to accommodate the processing of multiple tables.</span></span> <span data-ttu-id="91778-159">여러 테이블에서 증분 로드를 수행하는 패키지를 만드는 방법은 [여러 테이블의 증분 로드 수행](perform-an-incremental-load-of-multiple-tables.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91778-159">For more information on how to create a package that performs an incremental load from multiples tables, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>

## <a name="samples-of-change-data-capture-packages"></a><span data-ttu-id="91778-160">패키지 변경 데이터 캡처 예제</span><span class="sxs-lookup"><span data-stu-id="91778-160">Samples of Change Data Capture Packages</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="91778-161">에서는 패키지에서 변경 데이터 캡처를 사용하는 방법을 보여 주는 두 가지 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="91778-161">provides two samples that demonstrate how to use change data capture in packages.</span></span> <span data-ttu-id="91778-162">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="91778-162">For more information, see the following topics:</span></span>

-   [<span data-ttu-id="91778-163">지정된 간격 동안 변경 데이터 캡처 패키지 예제 추가 정보</span><span class="sxs-lookup"><span data-stu-id="91778-163">Readme_Change Data Capture for Specified Interval Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133507)

-   [<span data-ttu-id="91778-164">마지막 요청 이후 변경 데이터 캡처 패키지 예제 추가 정보</span><span class="sxs-lookup"><span data-stu-id="91778-164">Readme_Change Data Capture since Last Request Package Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=133508)

## <a name="related-tasks"></a><span data-ttu-id="91778-165">관련 작업</span><span class="sxs-lookup"><span data-stu-id="91778-165">Related Tasks</span></span>

-   [<span data-ttu-id="91778-166">변경 데이터의 간격 지정</span><span class="sxs-lookup"><span data-stu-id="91778-166">Specify an Interval of Change Data</span></span>](specify-an-interval-of-change-data.md)

-   [<span data-ttu-id="91778-167">변경 데이터의 준비 여부 확인</span><span class="sxs-lookup"><span data-stu-id="91778-167">Determine Whether the Change Data Is Ready</span></span>](determine-whether-the-change-data-is-ready.md)

-   [<span data-ttu-id="91778-168">변경 데이터에 대한 쿼리 준비</span><span class="sxs-lookup"><span data-stu-id="91778-168">Prepare to Query for the Change Data</span></span>](prepare-to-query-for-the-change-data.md)

-   [<span data-ttu-id="91778-169">변경 데이터 검색을 위한 함수 만들기</span><span class="sxs-lookup"><span data-stu-id="91778-169">Create the Function to Retrieve the Change Data</span></span>](create-the-function-to-retrieve-the-change-data.md)

-   [<span data-ttu-id="91778-170">변경 데이터 검색 및 이해</span><span class="sxs-lookup"><span data-stu-id="91778-170">Retrieve and Understand the Change Data</span></span>](retrieve-and-understand-the-change-data.md)

-   [<span data-ttu-id="91778-171">삽입, 업데이트 및 삭제 처리</span><span class="sxs-lookup"><span data-stu-id="91778-171">Process Inserts, Updates, and Deletes</span></span>](process-inserts-updates-and-deletes.md)

-   [<span data-ttu-id="91778-172">대상에 변경 내용 적용</span><span class="sxs-lookup"><span data-stu-id="91778-172">Apply the Changes to the Destination</span></span>](apply-the-changes-to-the-destination.md)

-   [<span data-ttu-id="91778-173">여러 테이블의 증분 로드 수행</span><span class="sxs-lookup"><span data-stu-id="91778-173">Perform an Incremental Load of Multiple Tables</span></span>](perform-an-incremental-load-of-multiple-tables.md)

## <a name="related-content"></a><span data-ttu-id="91778-174">관련 내용</span><span class="sxs-lookup"><span data-stu-id="91778-174">Related Content</span></span>
 <span data-ttu-id="91778-175">sqlblog.com의 블로그 항목 - [SSIS 디자인 패턴 – 증분 로드](https://go.microsoft.com/fwlink/?LinkId=217679)</span><span class="sxs-lookup"><span data-stu-id="91778-175">Blog entry, [SSIS Design Pattern - Incremental Load](https://go.microsoft.com/fwlink/?LinkId=217679), on sqlblog.com</span></span>


