---
title: 차트에서 그룹 추가 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0445b0ac-acae-4462-80fb-fe9735ac66db
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2ac558ccbd8855018877228b2b38debf769f1573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739345"
---
# <a name="add-or-delete-a-group-in-a-chart-report-builder-and-ssrs"></a><span data-ttu-id="76a3c-102">차트에서 그룹 추가 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="76a3c-102">Add or Delete a Group in a Chart (Report Builder and SSRS)</span></span>
  <span data-ttu-id="76a3c-103">차트 데이터 영역을 클릭하여 **차트 데이터** 창을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-103">Click in the chart data region to display the **Chart Data** pane.</span></span> <span data-ttu-id="76a3c-104">데이터 세트 필드를 **범주 그룹** 및 **계열 그룹** 영역으로 끌어서 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-104">Create groups by dragging dataset fields to the **Category Groups** and **Series Groups** areas.</span></span> <span data-ttu-id="76a3c-105">중첩된 그룹을 추가하려면 영역에 여러 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-105">To add nested groups, add multiple fields to the area.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-parent-or-child-group-to-a-chart"></a><span data-ttu-id="76a3c-106">차트에 부모 또는 자식 그룹을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="76a3c-106">To add a parent or child group to a chart</span></span>  
  
1.  <span data-ttu-id="76a3c-107">보고서 디자인 화면에서 차트의 아무 곳이나 클릭하여 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-107">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="76a3c-108">**차트 데이터** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-108">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="76a3c-109">필드를 **보고서 데이터** 창에서 **범주 그룹** 또는 **계열 그룹** 영역으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-109">Drag a field from the **Report Data** window to the **Category Groups** or **Series Groups** area.</span></span> <span data-ttu-id="76a3c-110">부모 그룹을 추가하려면 커서를 기존 그룹 앞에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-110">To add a parent group, position the cursor in front of an existing group.</span></span> <span data-ttu-id="76a3c-111">자식 그룹을 추가하려면 커서를 기존 그룹 뒤에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-111">To add a child group, position the cursor after an existing group.</span></span>  
  
### <a name="to-edit-a-category-group-on-a-chart"></a><span data-ttu-id="76a3c-112">차트에서 범주 그룹을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="76a3c-112">To edit a category group on a chart</span></span>  
  
1.  <span data-ttu-id="76a3c-113">보고서 디자인 화면에서 차트의 아무 곳이나 클릭하여 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-113">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="76a3c-114">**차트 데이터** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-114">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="76a3c-115">**범주 그룹** 영역에서 그룹을 마우스 오른쪽 단추로 클릭한 다음 **범주 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-115">Right-click the group in the **Category Groups** area, and then click **Category Group Properties**.</span></span>  
  
3.  <span data-ttu-id="76a3c-116">그룹 식, 필터, 정렬 식 및 그룹 변수를 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-116">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-series-group-on-a-chart"></a><span data-ttu-id="76a3c-117">차트에서 계열 그룹을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="76a3c-117">To edit a series group on a chart</span></span>  
  
1.  <span data-ttu-id="76a3c-118">보고서 디자인 화면에서 차트의 아무 곳이나 클릭하여 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-118">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="76a3c-119">**차트 데이터** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-119">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="76a3c-120">**계열 그룹** 영역에서 해당 그룹을 마우스 오른쪽 단추로 클릭한 다음 **계열 그룹 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-120">Right-click the group in the **Series Groups** area, and then click **Series Group Properties**.</span></span>  
  
3.  <span data-ttu-id="76a3c-121">그룹 식, 필터, 정렬 식 및 그룹 변수를 추가하거나 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-121">Add or remove group expressions, filters, sort expressions, and group variables.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-group-from-a-chart"></a><span data-ttu-id="76a3c-122">차트에서 그룹을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="76a3c-122">To delete a group from a chart</span></span>  
  
1.  <span data-ttu-id="76a3c-123">보고서 디자인 화면에서 차트의 아무 곳이나 클릭하여 차트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-123">On the report design surface, click anywhere in the chart to select it.</span></span> <span data-ttu-id="76a3c-124">**차트 데이터** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-124">The **Chart Data** pane appears.</span></span>  
  
2.  <span data-ttu-id="76a3c-125">**범주 그룹** 또는 **계열 그룹** 영역에서 해당 그룹을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="76a3c-125">Right-click the group in the **Category Groups** or **Series Groups** area, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76a3c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76a3c-126">See Also</span></span>  
 [<span data-ttu-id="76a3c-127">차트&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="76a3c-127">Charts &#40;Report Builder and SSRS&#41;</span></span>](charts-report-builder-and-ssrs.md)  
  
  
