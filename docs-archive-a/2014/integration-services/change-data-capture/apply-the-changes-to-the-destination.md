---
title: 대상에 변경 내용 적용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],applying changes
ms.assetid: 338a56db-cb14-4784-a692-468eabd30f41
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dd7ab93a299ffaab2259c3d462a5c0a69160ad5b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661262"
---
# <a name="apply-the-changes-to-the-destination"></a><span data-ttu-id="b5fa1-102">대상에 변경 내용 적용</span><span class="sxs-lookup"><span data-stu-id="b5fa1-102">Apply the Changes to the Destination</span></span>
  <span data-ttu-id="b5fa1-103">변경 데이터를 증분 로드하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지의 데이터 흐름에서 세 번째이자 마지막 태스크는 대상에 변경 내용을 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-103">In the data flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to apply the changes to your destination.</span></span> <span data-ttu-id="b5fa1-104">삽입을 적용할 구성 요소, 업데이트를 적용할 구성 요소 및 삭제를 적용할 구성 요소가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-104">You will need one component to apply inserts, one to apply updates, and one to apply deletes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fa1-105">변경 데이터를 증분 로드하는 패키지의 데이터 흐름을 디자인하는 두 번째 태스크는 삽입, 업데이트 및 삭제를 구분하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-105">The second task in designing the data flow of a package that performs an incremental load of change data is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="b5fa1-106">이 구성 요소에 대한 자세한 내용은 [삽입, 업데이트 및 삭제 처리](process-inserts-updates-and-deletes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-106">For more information about this component, see [Process Inserts, Updates, and Deletes](process-inserts-updates-and-deletes.md).</span></span> <span data-ttu-id="b5fa1-107">변경 데이터를 증분 로드하는 패키지를 만드는 전체 프로세스에 대한 설명은 [변경 데이터 캡처&#40;SSIS&#41;](change-data-capture-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="applying-inserts"></a><span data-ttu-id="b5fa1-108">삽입 적용</span><span class="sxs-lookup"><span data-stu-id="b5fa1-108">Applying Inserts</span></span>  
 <span data-ttu-id="b5fa1-109">삽입을 적용하려면 새 행을 특수한 방식으로 처리할 필요가 없으므로 OLE DB 대상을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-109">To apply inserts, you use an OLE DB destination because the new rows do not require any special handling.</span></span>  
  
#### <a name="to-process-inserts-by-using-an-ole-db-destination"></a><span data-ttu-id="b5fa1-110">OLE DB 대상을 사용하여 삽입을 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b5fa1-110">To process inserts by using an OLE DB Destination</span></span>  
  
1.  <span data-ttu-id="b5fa1-111">**데이터 흐름** 탭에서 OLE DB 대상을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-111">On the **Data flow** tab, add an OLE DB destination.</span></span>  
  
2.  <span data-ttu-id="b5fa1-112">삽입을 포함하는 출력을 조건부 분할 변환에서 OLE DB 대상에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-112">Connect the output that contains inserts from the Conditional Split transformation to the OLE DB destination.</span></span>  
  
3.  <span data-ttu-id="b5fa1-113">**OLE DB 대상 편집기**의 **연결 관리자** 페이지에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-113">In the **OLE DB Destination Editor**, on the **Connection Manager** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="b5fa1-114">대상 데이터베이스에 대한 OLE DB 연결 관리자를 선택하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-114">Select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
    2.  <span data-ttu-id="b5fa1-115">**데이터 액세스 모드** 옵션을 선택한 다음 대상 테이블을 선택하거나 대상 열을 포함하는 SQL 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-115">Select a **Data access mode** option, and then select the destination table or enter a SQL statement that contains the destination columns.</span></span>  
  
4.  <span data-ttu-id="b5fa1-116">편집기의 **매핑** 페이지에서 변경 데이터의 적절한 열을 대상 테이블에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-116">On the **Mappings** page of the editor, map the appropriate columns from the change data to the destination table.</span></span>  
  
## <a name="applying-updates"></a><span data-ttu-id="b5fa1-117">업데이트 적용</span><span class="sxs-lookup"><span data-stu-id="b5fa1-117">Applying Updates</span></span>  
 <span data-ttu-id="b5fa1-118">업데이트를 적용하려면 OLE DB 명령 변환을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-118">To apply updates, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="b5fa1-119">매개 변수가 있는 UPDATE 문을 사용하여 새 열 값으로 한 번에 한 행을 업데이트해야 하기 때문에 이 변환을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-119">You use this transformation because you have to use a parameterized UPDATE statement to update one row at a time with the new column values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fa1-120">대상 구성 요소를 사용하여 업데이트를 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-120">You can also use destination components to apply updates.</span></span> <span data-ttu-id="b5fa1-121">이 방법을 사용할 때는 대상 구성 요소를 사용하여 해당 용도로 만든 임시 테이블에 행을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-121">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="b5fa1-122">그런 다음 SQL 실행 태스크를 사용하여 임시 테이블의 대상에 대해 대량 업데이트 및 대량 삭제 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-122">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-updates-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="b5fa1-123">OLE DB 명령 변환을 사용하여 업데이트를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b5fa1-123">To process updates by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="b5fa1-124">**데이터 흐름** 탭에서 OLE DB 명령 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-124">On the **Data flow** tab, add an OLE DB Command transformation.</span></span>  
  
2.  <span data-ttu-id="b5fa1-125">업데이트를 포함하는 출력을 조건부 분할 변환에서 OLE DB 명령 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-125">Connect the output that contains updates from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="b5fa1-126">**고급 OLE DB 명령 편집기**의 **연결 관리자** 탭에서 대상 데이터베이스에 대한 OLE DB 연결 관리자를 선택하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-126">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
4.  <span data-ttu-id="b5fa1-127">**고급 OLE DB 명령 편집기**의 **구성 요소 속성** 탭에 있는 **SqlCommand**에 매개 변수가 있는 UPDATE 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-127">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab, for **SqlCommand**, enter a parameterized UPDATE statement.</span></span>  
  
     <span data-ttu-id="b5fa1-128">예를 들어 Customer 테이블에 대한 UPDATE 문에는 다음 구문이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-128">For example, an UPDATE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    update CDCSample.Customer  
    set TerritoryID  = ?,  
        CustomerType  = ?,  
        rowguid  = ?,  
        ModifiedDate  = ?  
    where CustomerID = ?  
  
    ```  
  
5.  <span data-ttu-id="b5fa1-129">편집기의 **열 매핑** 탭에서 변경 데이터의 적절한 열을 UPDATE 문의 매개 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-129">On the **Column Mappings** tab of the editor, map the appropriate columns from the change data to the parameters in the UPDATE statement.</span></span>  
  
## <a name="applying-deletes"></a><span data-ttu-id="b5fa1-130">삭제 적용</span><span class="sxs-lookup"><span data-stu-id="b5fa1-130">Applying Deletes</span></span>  
 <span data-ttu-id="b5fa1-131">삭제를 적용하려면 OLE DB 명령 변환을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-131">To apply deletes, you use an OLE DB Command transformation.</span></span> <span data-ttu-id="b5fa1-132">행을 고유하게 식별하는 열 값을 기반으로 한 번에 한 행을 삭제하는 매개 변수가 있는 DELETE 문을 사용해야 하기 때문에 이 변환을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-132">You use this transformation because you have to use a parameterized DELETE statement that deletes a single row at a time based on the column value that uniquely identifies the row.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5fa1-133">대상 구성 요소를 사용하여 삭제를 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-133">You can also use destination components to apply deletes.</span></span> <span data-ttu-id="b5fa1-134">이 방법을 사용할 때는 대상 구성 요소를 사용하여 해당 용도로 만든 임시 테이블에 행을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-134">When using this approach, you use the destination components to save the rows to temporary tables that you create for this purpose.</span></span> <span data-ttu-id="b5fa1-135">그런 다음 SQL 실행 태스크를 사용하여 임시 테이블의 대상에 대해 대량 업데이트 및 대량 삭제 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-135">Then, you use Execute SQL tasks to perform bulk update and bulk delete operations against the destination from the temporary tables.</span></span>  
  
#### <a name="to-process-deletes-by-using-an-ole-db-command-transformation"></a><span data-ttu-id="b5fa1-136">OLE DB 명령 변환을 사용하여 삭제를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b5fa1-136">To process deletes by using an OLE DB Command transformation</span></span>  
  
1.  <span data-ttu-id="b5fa1-137">**데이터 흐름** 탭에서 데이터 흐름에 OLE DB 명령 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-137">On the **Data flow** tab, add an OLE DB Command transformation to the data flow.</span></span>  
  
2.  <span data-ttu-id="b5fa1-138">삭제를 포함하는 출력을 조건부 분할 변환에서 OLE DB 명령 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-138">Connect the output that contains deletes from the Conditional Split transformation to the OLE DB Command transformation.</span></span>  
  
3.  <span data-ttu-id="b5fa1-139">고급 편집기를 열어 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-139">Open the Advanced Editor to configure the transformation.</span></span>  
  
4.  <span data-ttu-id="b5fa1-140">**고급 OLE DB 명령 편집기**의 **연결 관리자** 탭에서 대상 데이터베이스에 대한 OLE DB 연결 관리자를 선택하거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-140">In the **Advanced Editor for OLE DB Command**, on the **Connection Manager** tab, select or create an OLE DB Connection Manager for the destination database.</span></span>  
  
5.  <span data-ttu-id="b5fa1-141">**고급 OLE DB 명령 편집기**에 있는 편집기의 **구성 요소 속성** 탭에서 **SqlCommand**에 매개 변수가 있는 DELETE 문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-141">In the **Advanced Editor for OLE DB Command**, on the **Component Properties** tab of the editor, for **SqlCommand**, enter a parameterized DELETE statement.</span></span>  
  
     <span data-ttu-id="b5fa1-142">예를 들어 Customer 테이블에 대한 DELETE 문에는 다음 구문이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-142">For example, a DELETE statement for a Customer table might have the following syntax:</span></span>  
  
    ```  
    delete from Customer where CustomerID = ?  
  
    ```  
  
6.  <span data-ttu-id="b5fa1-143">편집기의 **열 매핑** 탭에서 변경 데이터의 적절한 열을 DELETE 문의 매개 변수에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-143">On the **Column Mappings** tab of the editor, map the appropriate column from the change data to the parameter in the DELETE statement.</span></span>  
  
## <a name="optimizing-inserts-and-updates-by-using-merge-functionality"></a><span data-ttu-id="b5fa1-144">MERGE 기능을 사용하여 삽입 및 업데이트 최적화</span><span class="sxs-lookup"><span data-stu-id="b5fa1-144">Optimizing Inserts and Updates by Using MERGE Functionality</span></span>  
 <span data-ttu-id="b5fa1-145">Transact-SQL MERGE 키워드와 특정 변경 데이터 캡처 옵션을 함께 사용하여 삽입 및 업데이트 처리를 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-145">You can optimize the processing of inserts and updates by combining certain change data capture options with the use of the Transact-SQL MERGE keyword.</span></span> <span data-ttu-id="b5fa1-146">MERGE 키워드에 대한 자세한 내용은 [MERGE&#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-146">For more information about the MERGE keyword, see [MERGE &#40;Transact-SQL&#41;](/sql/t-sql/statements/merge-transact-sql).</span></span>  
  
 <span data-ttu-id="b5fa1-147">변경 데이터를 검색하는 Transact-SQL 문에서 **cdc.fn_cdc_get_net_changes_<capture_instance>** 함수를 호출할 때 *all with merge*를 *row_filter_option* 매개 변수의 값으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-147">In the Transact-SQL statement that retrieves the change data, you can specify *all with merge* as the value of the *row_filter_option* parameter when you call the **cdc.fn_cdc_get_net_changes_<capture_instance>** function.</span></span> <span data-ttu-id="b5fa1-148">이 변경 데이터 캡처 함수는 삽입과 업데이트를 구분하는 데 필요한 추가 처리를 수행할 필요가 없을 때 보다 효율적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-148">This change data capture function operates more efficiently when it does not have to perform the extra processing that is required to distinguish inserts from updates.</span></span> <span data-ttu-id="b5fa1-149">*all with merge* 매개 변수 값을 지정할 때 변경 데이터의 **__$operation** 값은 삭제의 경우 1이고 삽입 또는 업데이트로 인한 변경의 경우 5입니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-149">When you specify the *all with merge* parameter value, the **__$operation** value of the change data is 1 for deletes or 5 for changes that were caused by inserts or updates.</span></span> <span data-ttu-id="b5fa1-150">변경 데이터를 검색하는 데 사용되는 Transact-SQL 함수에 대한 자세한 내용은 [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)를 참조하세요. *all with merge* 매개 변수 값을 사용하여 변경 내용을 검색한 후 삭제를 적용하고 나머지 행을 임시 테이블 또는 준비 테이블에 출력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-150">For more information about the Transact-SQL function that is used to retrieve the change data, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).After retrieving changes with the *all with merge* parameter value, you can apply deletes, and output the remaining rows to a temporary table or a staging table.</span></span> <span data-ttu-id="b5fa1-151">그런 다음 다운스트림 SQL 실행 태스크에서 단일 MERGE 문을 사용하여 준비 테이블의 모든 삽입 또는 업데이트를 대상에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5fa1-151">Then, in a downstream Execute SQL Task, you can use a single MERGE statement to apply all the inserts or updates from the staging table to the destination.</span></span>  
  
  
