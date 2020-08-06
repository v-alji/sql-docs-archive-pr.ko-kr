---
title: 데이터 흐름에 데이터 뷰어 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data viewers [Integration Services]
- data flow [Integration Services], data viewers
- adding data viewers
ms.assetid: 5e573274-a170-4132-bfc8-a8ff3a8411e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7abd76417552ec50da736afe024a5ae36ee6a2ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646589"
---
# <a name="add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="fd01d-102">데이터 흐름에 데이터 뷰어 추가</span><span class="sxs-lookup"><span data-stu-id="fd01d-102">Add a Data Viewer to a Data Flow</span></span>
  <span data-ttu-id="fd01d-103">이 항목에서는 데이터 흐름에 데이터 뷰어를 추가 및 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-103">This topic describes how to add and configure a data viewer in a data flow.</span></span> <span data-ttu-id="fd01d-104">데이터 뷰어는 두 데이터 흐름 구성 요소 간에 이동하는 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-104">A data viewer displays data that is moving between two data flow components.</span></span> <span data-ttu-id="fd01d-105">예를 들어 데이터 뷰어는 데이터 흐름 변환으로 데이터가 수정되기 전의 데이터 원본에서 추출한 데이터를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-105">For example, a data viewer can display the data that is extracted from a data source before a transformation in the data flow modifies the data.</span></span>  
  
 <span data-ttu-id="fd01d-106">경로는 하나의 데이터 흐름 구성 요소의 출력을 다른 구성 요소의 입력에 연결함으로써 데이터 흐름의 구성 요소를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-106">A path connects components in a data flow by connecting the output of one data flow component to the input of another component.</span></span>  
  
 <span data-ttu-id="fd01d-107">패키지에 데이터 뷰어를 추가하려면 패키지에 데이터 흐름 태스크 및 최소한 두 개 이상의 연결된 데이터 흐름 구성 요소가 포함되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-107">Before you can add data viewers to a package, the package must include a Data Flow task and at least two data flow components that are connected.</span></span>  
  
### <a name="to-add-a-data-viewer-to-a-data-flow"></a><span data-ttu-id="fd01d-108">데이터 흐름에 데이터 뷰어를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="fd01d-108">To add a data viewer to a data flow</span></span>  
  
1.  <span data-ttu-id="fd01d-109">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="fd01d-110">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-110">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="fd01d-111">**제어 흐름** 이 아직 활성화되어 있지 않으면 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-111">Click the **Control Flow** tab, if it is not already active.</span></span>  
  
4.  <span data-ttu-id="fd01d-112">데이터 흐름 태스크를 클릭하여 데이터 뷰어를 첨부할 데이터 흐름을 선택하고 **데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-112">Click the Data Flow task to whose data flow you want to attach a data viewer and then click the **Data Flow** tab.</span></span>  
  
5.  <span data-ttu-id="fd01d-113">두 데이터 흐름 구성 요소 간 경로를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-113">Right-click a path between two data flow components, and click **Edit**.</span></span>  
  
6.  <span data-ttu-id="fd01d-114">**일반** 페이지에서 경로 속성을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-114">On the **General** page, you can view and edit path properties.</span></span> <span data-ttu-id="fd01d-115">예를 들어 **PathAnnotation** 드롭다운 목록에서 경로 옆에 표시되는 주석을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-115">For example, from the **PathAnnotation** drop-down list you can select the annotation that appears next to the path.</span></span>  
  
7.  <span data-ttu-id="fd01d-116">**메타데이터** 페이지에서 열 메타데이터를 보고 메타데이터를 클립보드로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-116">On the **Metadata** page, you can view the column metadata and copy the metadata to the Clipboard.</span></span>  
  
8.  <span data-ttu-id="fd01d-117">**데이터 뷰어** 페이지에서 **데이터 뷰어 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-117">On the **Data Viewer** page, click **Enable data viewer**.</span></span>  
  
9. <span data-ttu-id="fd01d-118">표시할 열 영역에서 데이터 뷰어에 표시할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-118">In the Columns to display area, select the columns you want to display in the data viewer.</span></span> <span data-ttu-id="fd01d-119">기본적으로 사용 가능한 열이 모두 선택되어 **표시된 열** 목록에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-119">By default, all the available columns are selected and listed in the **Displayed Columns** list.</span></span> <span data-ttu-id="fd01d-120">사용하지 않을 열을 선택하고 왼쪽 화살표를 클릭하여 **사용되지 않은 열** 목록으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-120">Move columns that you do not want to use to the **Unused Column** list by selecting them and then clicking the left arrow.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fd01d-121">표에서 DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2 및 DT_DBTIMESTAMPOFFSET 데이터 형식을 나타내는 값은 ISO 8601 형식 문자열로 표시되고 `T` 구분 기호는 공백 구분 기호로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-121">In the grid, values that represent the DT_DATE, DT_DBTIME2, DT_FILETIME, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types appear as ISO 8601 formatted strings and a space separator replaces the `T` separator.</span></span> <span data-ttu-id="fd01d-122">DT_DATE 및 DT_FILETIME 데이터 형식을 나타내는 값은 7자리의 소수 자릿수 초를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-122">Values that represent the DT_DATE and DT_FILETIME data types include seven digits for fractional seconds.</span></span> <span data-ttu-id="fd01d-123">DT_FILETIME 데이터 형식은 3자리의 소수 자릿수 초만 저장하기 때문에 표에는 나머지 4자리가 0으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-123">Because the DT_FILETIME data type stores only three digits of fractional seconds, the grid displays zeros for the remaining four digits.</span></span> <span data-ttu-id="fd01d-124">DT_DBTIMESTAMP 데이터 형식을 나타내는 값은 3자리의 소수 자릿수 초를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-124">Values that represent the DT_DBTIMESTAMP data type include three digits for fractional seconds.</span></span> <span data-ttu-id="fd01d-125">DT_DBTIME2, DT_DBTIMESTAMP2 및 DT_DBTIMESTAMPOFFSET 데이터 형식을 나타내는 값의 경우 소수 자릿수 초의 자릿수는 열의 데이터 형식에 대해 지정된 소수 자릿수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-125">For values that represent the DT_DBTIME2, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET data types, the number of digits for fractional seconds corresponds to the scale specified for the column's data type.</span></span> <span data-ttu-id="fd01d-126">ISO 8601 형식에 대한 자세한 내용은 [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fd01d-126">For more information about ISO 8601 formats, see [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).</span></span> <span data-ttu-id="fd01d-127">데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fd01d-127">For more information about data types, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
10. <span data-ttu-id="fd01d-128">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fd01d-128">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd01d-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fd01d-129">See Also</span></span>  
 <span data-ttu-id="fd01d-130">[Integration Services 변환](data-flow/transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="fd01d-130">[Integration Services Transformations](data-flow/transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="fd01d-131">[Integration Services 경로](data-flow/integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="fd01d-131">[Integration Services Paths](data-flow/integration-services-paths.md) </span></span>  
 <span data-ttu-id="fd01d-132">[데이터 흐름](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="fd01d-132">[Data Flow](data-flow/data-flow.md) </span></span>  
 [<span data-ttu-id="fd01d-133">데이터 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="fd01d-133">Debugging Data Flow</span></span>](troubleshooting/debugging-data-flow.md)  
  
  
