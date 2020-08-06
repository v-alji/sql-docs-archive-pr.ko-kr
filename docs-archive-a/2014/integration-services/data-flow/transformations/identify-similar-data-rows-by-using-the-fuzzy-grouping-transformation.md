---
title: 유사 항목 그룹화 변환을 사용하여 유사한 데이터 행 식별 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4e6d49548c211b38a35d6f5f7efc3d50fec93588
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659572"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a><span data-ttu-id="f8b41-102">유사 항목 그룹화 변환을 사용하여 유사한 데이터 행 식별</span><span class="sxs-lookup"><span data-stu-id="f8b41-102">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="f8b41-103">유사 항목 그룹화 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크 하나의 원본이 이미 들어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-103">To add and configure a Fuzzy Grouping transformation, the package must already include at least one Data Flow task and a source.</span></span>  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a><span data-ttu-id="f8b41-104">데이터 흐름에서 유사 항목 그룹화 변환을 구현하려면</span><span class="sxs-lookup"><span data-stu-id="f8b41-104">To implement Fuzzy Grouping transformation in a data flow</span></span>  
  
1.  <span data-ttu-id="f8b41-105">[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-105">In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="f8b41-106">솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="f8b41-107">**데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 유사 항목 그룹화 변환을 디자인 화면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the Fuzzy Grouping transformation to the design surface.</span></span>  
  
4.  <span data-ttu-id="f8b41-108">데이터 원본이나 이전 변환에서 연결선을 유사 항목 그룹화 변환으로 끌어서 유사 항목 그룹화 변환을 데이터 흐름에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-108">Connect the Fuzzy Grouping transformation to the data flow by dragging the connector from the data source or a previous transformation to the Fuzzy Grouping transformation.</span></span>  
  
5.  <span data-ttu-id="f8b41-109">유사 항목 그룹화 변환을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-109">Double-click the Fuzzy Grouping transformation.</span></span>  
  
6.  <span data-ttu-id="f8b41-110">**유사 항목 그룹화 변환 편집기** 대화 상자의 **연결 관리자** 탭에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스로 연결되는 OLE DB 연결 관리자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-110">In the **Fuzzy Grouping Transformation Editor** dialog box, on the **Connection Manager** tab, select an OLE DB connection manager that connects to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b41-111">변환에는 임시 테이블 및 인덱스를 만들기 위해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 대한 연결이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-111">The transformation requires a connection to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database to create temporary tables and indexes.</span></span>  
  
7.  <span data-ttu-id="f8b41-112">**열** 탭을 클릭하고 **사용 가능한 입력 열** 목록에서 데이터 세트에서 유사 행을 식별하는 데 사용할 입력 열의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-112">Click the **Columns** tab and, in the **Available Input Columns** list, select the check box of the input columns to use to identify similar rows in the dataset.</span></span>  
  
8.  <span data-ttu-id="f8b41-113">**통과** 열의 확인란을 선택하여 변환 출력으로 통과할 입력 열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-113">Select the check box in the **Pass Through** column to identify the input columns to pass through to the transformation output.</span></span> <span data-ttu-id="f8b41-114">통과 열은 중복 행의 식별 과정에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-114">Pass-through columns are not included in the process of identification of duplicate rows.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b41-115">그룹화에 사용되는 입력 열은 통과 열로 자동으로 선택되지 않으며 그룹화에 사용되는 경우 선택을 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-115">Input columns that are used for grouping are automatically selected as pass-through columns, and they cannot be unselected while used for grouping.</span></span>  
  
9. <span data-ttu-id="f8b41-116">필요에 따라 **출력 별칭** 열에서 출력 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-116">Optionally, update the names of output columns in the **Output Alias** column.</span></span>  
  
10. <span data-ttu-id="f8b41-117">필요에 따라 **그룹 출력 별칭** 열에서 정리된 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-117">Optionally, update the names of cleaned columns in the **Group OutputAlias** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b41-118">열의 기본 이름은 "_clean" 접미사가 붙은 입력 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-118">The default names of columns are the names of the input columns with a "_clean" suffix.</span></span>  
  
11. <span data-ttu-id="f8b41-119">필요에 따라 **일치 유형** 열에서 사용할 일치 유형을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-119">Optionally, update the type of match to use in the **Match Type** column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="f8b41-120">적어도 하나 이상의 열에서 유사 항목 일치가 사용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-120">At least one column must use fuzzy matching.</span></span>  
  
12. <span data-ttu-id="f8b41-121">**최소 유사성** 열에서 최소 유사성 수준 열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-121">Specify the minimum similarity level columns in the **Minimum Similarity** column.</span></span> <span data-ttu-id="f8b41-122">값은 0에서 1 사이여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-122">The value must be between 0 and 1.</span></span> <span data-ttu-id="f8b41-123">값이 1에 가까울수록 입력 열의 유사 값이 그룹으로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-123">The closer the value is to 1, the more similar the values in the input columns must be to form a group.</span></span> <span data-ttu-id="f8b41-124">최소 유사성이 1이면 정확히 일치하는 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-124">A minimum similarity of 1 indicates an exact match.</span></span>  
  
13. <span data-ttu-id="f8b41-125">필요에 따라 **유사성 출력 별칭** 열에서 유사성 열의 이름을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-125">Optionally, update the names of similarity columns in the **Similarity Output Alias** column.</span></span>  
  
14. <span data-ttu-id="f8b41-126">데이터 값에 숫자 처리를 지정하려면 **숫자** 열의 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-126">To specify the handling of numbers in data values, update the values in the **Numerals** column.</span></span>  
  
15. <span data-ttu-id="f8b41-127">변환에서 열의 문자열 데이터를 비교하는 방법을 지정하려면 **비교 플래그** 열에서 기본으로 선택된 비교 옵션을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-127">To specify how the transformation compares the string data in a column, modify the default selection of comparison options in the **Comparison Flags** column.</span></span>  
  
16. <span data-ttu-id="f8b41-128">**고급** 탭을 클릭하여 변환이 고유 행 식별자(_key_in), 중복 행 식별자(_key_out) 및 유사성 값(_score)에 대한 출력에 추가하는 열 이름을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-128">Click the **Advanced** tab to modify the names of the columns that the transformation adds to the output for the unique row identifier (_key_in), the duplicate row identifier (_key_out), and the similarity value (_score).</span></span>  
  
17. <span data-ttu-id="f8b41-129">필요에 따라 슬라이더 막대를 움직여서 유사성 임계값을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-129">Optionally, adjust the similarity threshold by moving the slider bar.</span></span>  
  
18. <span data-ttu-id="f8b41-130">선택적으로 데이터의 구분 기호를 무시하려면 토큰 구분 기호 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-130">Optionally, clear the token delimiter check boxes to ignore delimiters in the data.</span></span>  
  
19. <span data-ttu-id="f8b41-131">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-131">Click **OK**.</span></span>  
  
20. <span data-ttu-id="f8b41-132">업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8b41-132">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b41-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f8b41-133">See Also</span></span>  
 <span data-ttu-id="f8b41-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="f8b41-134">[Fuzzy Grouping Transformation](fuzzy-grouping-transformation.md) </span></span>  
 <span data-ttu-id="f8b41-135">[Integration Services 변환](integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="f8b41-135">[Integration Services Transformations](integration-services-transformations.md) </span></span>  
 <span data-ttu-id="f8b41-136">[Integration Services 경로](../integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="f8b41-136">[Integration Services Paths](../integration-services-paths.md) </span></span>  
 [<span data-ttu-id="f8b41-137">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="f8b41-137">Data Flow Task</span></span>](../../control-flow/data-flow-task.md)  
  
  
