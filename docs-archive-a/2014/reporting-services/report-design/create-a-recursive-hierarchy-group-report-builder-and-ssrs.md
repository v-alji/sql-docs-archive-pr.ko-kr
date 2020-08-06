---
title: 재귀 계층 구조 그룹 만들기(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bf86c3989170ed8cd452168a558ead348258331e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649428"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a><span data-ttu-id="fc4b8-102">재귀 계층 구조 그룹 만들기(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="fc4b8-102">Create a Recursive Hierarchy Group (Report Builder and SSRS)</span></span>
  <span data-ttu-id="fc4b8-103">재귀 계층 구조 그룹은 조직 계층의 관리자와 직원 관계에 대한 보고 구조와 같이 여러 계층 수준을 포함하는 단일 보고서 데이터 세트의 데이터를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-103">A recursive hierarchy group organizes data from a single report dataset that includes multiple hierarchical levels, such as the report-to structure for manager-employee relationships in an organizational hierarchy.</span></span>  
  
 <span data-ttu-id="fc4b8-104">테이블의 데이터를 재귀 계층 구조 그룹으로 구성하기 전에 모든 계층 데이터를 포함하는 단일 데이터 세트가 있어야 합니다. 이 데이터 세트에는 그룹화할 항목과 항목을 그룹화할 기준에 대한 개별 필드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-104">Before you can organize data in a table as a recursive hierarchy group, you must have a single dataset that contains all the hierarchical data, You must have separate fields for the item to group and for the item to group by.</span></span> <span data-ttu-id="fc4b8-105">예를 들어 관리자에 속한 직원을 재귀적으로 그룹화할 데이터 세트에 이름, 직원 이름, 직원 ID 및 관리자 ID가 들어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-105">For example, a dataset where you want to group employees recursively under their manager might contain a name, an employee name, an employee ID, and a manager ID.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-recursive-hierarchy-group"></a><span data-ttu-id="fc4b8-106">재귀 계층 구조 그룹을 만들려면</span><span class="sxs-lookup"><span data-stu-id="fc4b8-106">To create a recursive hierarchy group</span></span>  
  
1.  <span data-ttu-id="fc4b8-107">디자인 뷰에서 테이블을 추가하고 표시할 데이터 세트 필드를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-107">In Design view, add a table, and drag the dataset fields to display.</span></span> <span data-ttu-id="fc4b8-108">일반적으로 계층으로 표시할 필드가 첫 번째 열에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-108">Typically, the field that you want to show as a hierarchy is in the first column.</span></span>  
  
2.  <span data-ttu-id="fc4b8-109">테이블에서 임의의 위치를 두 번 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-109">Right-click anywhere in the table to select it.</span></span> <span data-ttu-id="fc4b8-110">그룹화 창에 선택한 테이블에 대한 그룹 세부 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-110">The Grouping pane displays the details group for the selected table.</span></span> <span data-ttu-id="fc4b8-111">행 그룹 창에서 **세부 정보**를 마우스 오른쪽 단추로 클릭한 다음 **그룹 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-111">In the Row Groups pane, right-click **Details**, and then click **Edit Group**.</span></span> <span data-ttu-id="fc4b8-112">**그룹 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-112">The **Group Properties** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="fc4b8-113">**그룹 식**에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-113">In **Group expressions**, click **Add**.</span></span> <span data-ttu-id="fc4b8-114">새 행이 표에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-114">A new row appears in the grid.</span></span>  
  
4.  <span data-ttu-id="fc4b8-115">**그룹화 대상** 목록에서 그룹화할 필드를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-115">In the **Group on** list, type or select the field to group.</span></span>  
  
5.  <span data-ttu-id="fc4b8-116">**고급**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-116">Click **Advanced**.</span></span>  
  
6.  <span data-ttu-id="fc4b8-117">**재귀적 부모** 목록에서 그룹화할 필드를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-117">In the **Recursive Parent** list, enter or select the field to group on.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="fc4b8-118">보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-118">Run the report.</span></span> <span data-ttu-id="fc4b8-119">계층을 표시할 들여쓰기가 없는 경우에도 보고서에서 재귀 계층 구조 그룹을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-119">The report displays the recursive hierarchy group, although there is no indent to show the hierarchy</span></span>  
  
### <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a><span data-ttu-id="fc4b8-120">들여쓰기 수준을 사용하여 재귀 계층 구조 그룹의 서식을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="fc4b8-120">To format a recursive hierarchy group with indent levels</span></span>  
  
1.  <span data-ttu-id="fc4b8-121">계층 형식을 표시하는 들여쓰기 수준을 추가할 필드를 포함하는 입력란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-121">Click the text box that contains the field to which you want to add indent levels to display a hierarchy format.</span></span> <span data-ttu-id="fc4b8-122">입력란에 대한 속성이 속성 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-122">The properties for the text box appear in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc4b8-123">속성 창이 표시되지 않으면 **보기** 탭에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-123">If you do not see the Properties pane, click **Properties** on the **View** tab.</span></span>  
  
2.  <span data-ttu-id="fc4b8-124">속성 창에서 노드를 확장 `Padding` 하 고 **왼쪽**을 클릭 한 다음 드롭다운 목록에서을 선택 **\<Expression...>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-124">In the Properties pane, expand the `Padding` node, click **Left**, and from the drop-down list, select **\<Expression...>**.</span></span>  
  
3.  <span data-ttu-id="fc4b8-125">식 창에서 다음 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-125">In the Expression pane, type the following expression:</span></span>  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     <span data-ttu-id="fc4b8-126">Padding 속성은 모두 *nnyy*형식의 문자열을 요구합니다. 여기서 *nn* 은 숫자이고, *yy* 는 측정 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-126">The Padding properties all require a string in the format *nnyy*, where *nn* is a number and *yy* is the unit of measure.</span></span> <span data-ttu-id="fc4b8-127">예 식은 `Level` 함수를 사용하여 재귀 수준에 따라 안쪽 여백의 크기를 늘리는 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-127">The example expression builds a string that uses the `Level` function to increase the size of the padding based on recursion level.</span></span> <span data-ttu-id="fc4b8-128">예를 들어 1 수준의 행은 (2 + (1\*10))=12pt의 패딩으로, 3 수준의 행은 (2 + (3\*10))=32pt의 패딩으로 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-128">For example, a row that has a level of 1 would result in a padding of (2 + (1\*10))=12pt, and a row that has a level of 3 would result in a padding of (2 + (3\*10))=32pt.</span></span> <span data-ttu-id="fc4b8-129">함수에 대 한 자세한 내용은 `Level` [Level](report-builder-functions-level-function.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-129">For information about the `Level` function, see [Level](report-builder-functions-level-function.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="fc4b8-130">보고서를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-130">Run the report.</span></span> <span data-ttu-id="fc4b8-131">보고서에 그룹화된 데이터의 계층 뷰가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc4b8-131">The report displays a hierarchical view of the grouped data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4b8-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc4b8-132">See Also</span></span>  
 <span data-ttu-id="fc4b8-133">[재귀 계층 구조 그룹 생성&#40;보고서 작성기 및 SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-133">[Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc4b8-134">[데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-134">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc4b8-135">[집계 함수 참조&#40;보고서 작성기 및 SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-135">[Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) </span></span>  
 <span data-ttu-id="fc4b8-136">[테이블&#40;보고서 작성기 및 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc4b8-137">[행렬&#40;보고서 작성기 및 SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="fc4b8-138">[목록&#40;보고서 작성기 및 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="fc4b8-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="fc4b8-139">테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="fc4b8-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
