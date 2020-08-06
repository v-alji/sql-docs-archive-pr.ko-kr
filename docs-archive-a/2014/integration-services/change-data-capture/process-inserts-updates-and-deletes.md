---
title: 삽입, 업데이트 및 삭제 처리 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],processing data
ms.assetid: 13a84d21-2623-4efe-b442-4125a7a2d690
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67f016aaf4f7f83c0fa506966c4e78f5b8fadef6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646578"
---
# <a name="process-inserts-updates-and-deletes"></a><span data-ttu-id="b7d0c-102">삽입, 업데이트 및 삭제 처리</span><span class="sxs-lookup"><span data-stu-id="b7d0c-102">Process Inserts, Updates, and Deletes</span></span>
  <span data-ttu-id="b7d0c-103">변경 데이터를 증분 로드하는 Integration Services 패키지의 데이터 흐름에서 두 번째 태스크는 삽입, 업데이트 및 삭제를 구분하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-103">In the data flow of an Integration Services package that performs an incremental load of change data, the second task is to separate inserts, updates, and deletes.</span></span> <span data-ttu-id="b7d0c-104">그런 다음 적절한 명령을 사용하여 대상에 해당 작업을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-104">Then, you can use appropriate commands to apply them to the destination.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7d0c-105">변경 데이터를 증분 로드하는 패키지의 데이터 흐름을 디자인하는 첫 번째 태스크는 변경 데이터를 검색하는 쿼리를 실행하는 원본 구성 요소를 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-105">The first task in designing the data flow of a package that performs an incremental load of change data is to configure the source component that runs the query that retrieves the change data.</span></span> <span data-ttu-id="b7d0c-106">이 구성 요소에 대한 자세한 내용은 [변경 데이터 검색 및 이해](retrieve-and-understand-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-106">For more information about this component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span> <span data-ttu-id="b7d0c-107">변경 데이터를 증분 로드하는 패키지를 만드는 전체 프로세스에 대한 설명은 [변경 데이터 캡처&#40;SSIS&#41;](change-data-capture-ssis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-107">For a description of the overall process for creating a package that performs an incremental load of change data, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="associating-friendly-values-to-separate-inserts-updates-and-deletes"></a><span data-ttu-id="b7d0c-108">값을 연결하여 삽입, 업데이트 및 삭제 구분</span><span class="sxs-lookup"><span data-stu-id="b7d0c-108">Associating Friendly Values to Separate Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="b7d0c-109">변경 데이터를 검색하는 쿼리 예에서 **cdc.fn_cdc_get_net_changes_<capture_instance>** 함수는 **__$operation**이라는 메타데이터의 열만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-109">In the example query that retrieves change data, the **cdc.fn_cdc_get_net_changes_<capture_instance>** function returns only the column of metadata named **__$operation**.</span></span> <span data-ttu-id="b7d0c-110">이 메타데이터 열은 변경을 발생시킨 작업을 나타내는 서수 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-110">This metadata column contains an ordinal value that indicates which operation caused the change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7d0c-111">**cdc.fn_cdc_get_net_changes_<capture_instance>** 함수를 호출하는 쿼리에 대한 자세한 내용은 [변경 데이터 검색을 위한 함수 만들기](create-the-function-to-retrieve-the-change-data.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-111">For more information about the query that uses calls the **cdc.fn_cdc_get_net_changes_<capture_instance>** function, see [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md).</span></span>  
  
 <span data-ttu-id="b7d0c-112">서수 값을 해당 작업에 일치시키는 것은 작업의 니모닉을 사용하는 것만큼 쉽지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-112">Matching an ordinal value to its corresponding operation is not as easy as using a mnemonic of the operation.</span></span> <span data-ttu-id="b7d0c-113">예를 들어 'D'로 쉽게 삭제 작업을 나타내고 'I'로 삽입 작업을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-113">For example, 'D' can easily represent a delete operation and 'I' represent an insert operation.</span></span> <span data-ttu-id="b7d0c-114">[변경 데이터 검색을 위한 함수 작성](create-the-function-to-retrieve-the-change-data.md)항목에서 만든 쿼리 예는 서수 값을 새 열에 반환되는 문자열 값으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-114">The example query that was created in the topic, [Creating the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md), makes this conversion from an ordinal value to a friendly string value that is returned in a new column.</span></span> <span data-ttu-id="b7d0c-115">다음 코드 세그먼트에서는 이 변환을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-115">The following segment of code shows this conversion:</span></span>  
  
```  
select   
    ...  
    case __$operation  
        when 1 then 'D'  
        when 2 then 'I'  
        when 4 then 'U'  
        else null  
     end as CDC_OPERATION  
```  
  
## <a name="configuring-a-conditional-split-transformation-to-direct-inserts-updates-and-deletes"></a><span data-ttu-id="b7d0c-116">조건부 분할 변환을 구성하여 직접 삽입, 업데이트 및 삭제 전송</span><span class="sxs-lookup"><span data-stu-id="b7d0c-116">Configuring a Conditional Split Transformation to Direct Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="b7d0c-117">변경 데이터 행을 직접 세 개의 출력 중 하나로 전송하려면 조건부 분할 변환이 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-117">To direct rows of change data to one of three outputs, the Conditional Split transformation is ideal.</span></span> <span data-ttu-id="b7d0c-118">변환에서는 각 행의 **CDC_OPERATION** 열 값만 검사하여 변경이 삽입, 업데이트, 삭제 중 어느 작업이었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-118">The transformation just checks the value of the **CDC_OPERATION** column in each row and determines whether that change was an insert, update, or delete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b7d0c-119">CDC_OPERATION 열은 **__$operation** 열의 숫자 값에서 파생된 문자열 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-119">The CDC_OPERATION column contains a friendly string value derived from the numeric value in the **__$operation** column.</span></span>  
  
#### <a name="to-split-inserts-updates-and-deletes-for-processing-by-using-a-conditional-split-transformation"></a><span data-ttu-id="b7d0c-120">조건부 분할 변환을 사용하여 처리를 위해 삽입, 업데이트 및 삭제를 분할하려면</span><span class="sxs-lookup"><span data-stu-id="b7d0c-120">To split inserts, updates, and deletes for processing by using a Conditional Split transformation</span></span>  
  
1.  <span data-ttu-id="b7d0c-121">**데이터 흐름** 탭에서 조건부 분할 변환을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-121">On the **Data Flow** tab, add a Conditional Split transformation.</span></span>  
  
2.  <span data-ttu-id="b7d0c-122">OLE DB 원본의 출력을 조건부 분할 변환에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-122">Connect the output of the OLE DB source to the Conditional Split transformation.</span></span>  
  
3.  <span data-ttu-id="b7d0c-123">**조건부 분할 변환 편집기**의 아래쪽 창에 다음 세 줄을 입력하여 세 개의 출력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-123">In the **Conditional Split Transformation Editor**, in the lower pane of the editor, enter the following three lines to designate the three outputs</span></span>  
  
    1.  <span data-ttu-id="b7d0c-124">조건 `CDC_OPERATION == "I"` 가 있는 줄을 입력하여 삽입된 행을 삽입의 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-124">Enter a line with the condition `CDC_OPERATION == "I"` to direct inserted rows to the output for inserts.</span></span>  
  
    2.  <span data-ttu-id="b7d0c-125">조건 `CDC_OPERATION == "U"` 가 있는 줄을 입력하여 업데이트된 행을 업데이트의 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-125">Enter a line with the condition `CDC_OPERATION == "U"` to direct updated rows to the output for updates.</span></span>  
  
    3.  <span data-ttu-id="b7d0c-126">조건 `CDC_OPERATION == "D"` 가 있는 줄을 입력하여 삭제된 행을 삭제의 출력으로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-126">Enter a line with the condition `CDC_OPERATION == "D"` to direct deleted rows to the output for deletes.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b7d0c-127">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b7d0c-127">Next Step</span></span>  
 <span data-ttu-id="b7d0c-128">처리를 위해 행을 분할한 후 다음 단계는 대상에 변경 내용을 적용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7d0c-128">After you split the rows for processing, the next step is to apply the changes to the destination.</span></span>  
  
 <span data-ttu-id="b7d0c-129">**다음 항목:** [대상에 변경 내용 적용](apply-the-changes-to-the-destination.md)</span><span class="sxs-lookup"><span data-stu-id="b7d0c-129">**Next topic:** [Apply the Changes to the Destination](apply-the-changes-to-the-destination.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d0c-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7d0c-130">See Also</span></span>  
 <span data-ttu-id="b7d0c-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="b7d0c-131">[Conditional Split Transformation](../data-flow/transformations/conditional-split-transformation.md) </span></span>  
 [<span data-ttu-id="b7d0c-132">조건부 분할 변환을 사용하여 데이터 세트 분할</span><span class="sxs-lookup"><span data-stu-id="b7d0c-132">Split a Dataset by Using the Conditional Split Transformation</span></span>](../data-flow/transformations/split-a-dataset-by-using-the-conditional-split-transformation.md)  
  
  
