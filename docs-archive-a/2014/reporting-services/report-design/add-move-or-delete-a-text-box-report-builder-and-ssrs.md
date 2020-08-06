---
title: 입력란 추가, 이동 또는 삭제(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f042cf81-d933-4ac7-9287-c074a46bde98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cd85415fd2f0bac2a37b3fbda06795e10f351b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739351"
---
# <a name="add-move-or-delete-a-text-box-report-builder-and-ssrs"></a><span data-ttu-id="8eda2-102">입력란 추가, 이동 또는 삭제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8eda2-102">Add, Move, or Delete a Text Box (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8eda2-103">입력란은 보고서에서 가장 일반적으로 사용되는 보고서 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-103">Text boxes are the most commonly used report item in reports.</span></span> <span data-ttu-id="8eda2-104">입력란을 보고서 본문에 추가하여 제목, 매개 변수 선택 항목, 기본 제공 필드 및 날짜와 같은 정보를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-104">You can add a text box to the report body to display information such as titles, parameter choices, built-in fields, and dates.</span></span>  
  
 <span data-ttu-id="8eda2-105">테이블이나 행렬의 각 셀은 실제로 입력란입니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-105">Every cell in a table or matrix is really a text box.</span></span> <span data-ttu-id="8eda2-106">테이블 및 행렬이 있는 보고서에 표시되는 거의 모든 보고서 데이터는 보고서의 각 입력란 내용을 평가하는 보고서 처리기의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-106">Almost all report data displayed in a report with tables and matrices is the result of the report processor evaluating the contents of each text box in the report.</span></span> <span data-ttu-id="8eda2-107">따라서 데이터 영역 외부의 다른 입력란과 같은 방식으로 셀의 서식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-107">As such, you can format cells in the same way you would format other text boxes outside the data region.</span></span>  
  
 <span data-ttu-id="8eda2-108">목록 데이터 영역에 입력란을 추가하려면 먼저 입력란을 추가한 다음 목록으로 끌어 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-108">To add a text box to a list data region, you must first add the text box and then drag it into the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8eda2-109">입력란을 클릭하기만 하면 입력란의 텍스트를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-109">When you click a text box, you're immediately editing the text in the text box.</span></span> <span data-ttu-id="8eda2-110">입력란의 텍스트가 아니라 입력란 자체를 선택하려면 편집 상태에서 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-110">To select the text box itself, not the text in it, press ESC.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-text-box"></a><span data-ttu-id="8eda2-111">입력란을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8eda2-111">To add a text box</span></span>  
  
1.  <span data-ttu-id="8eda2-112">디자인 뷰의 **삽입** 탭에서 **입력란**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-112">On the **Insert** tab in Design view, click **Text Box**.</span></span>  
  
2.  <span data-ttu-id="8eda2-113">디자인 화면에서 상자를 클릭한 다음 끌어 원하는 크기의 입력란을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-113">On the design surface, click and then drag a box to the desired size of the text box.</span></span> <span data-ttu-id="8eda2-114">또는 디자인 화면을 클릭하여 기본 크기의 입력란을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-114">Alternatively, click the design surface to create a text box of default size.</span></span>  
  
### <a name="to-add-a-text-box-in-a-list"></a><span data-ttu-id="8eda2-115">목록에 입력란을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="8eda2-115">To add a text box in a list</span></span>  
  
1.  <span data-ttu-id="8eda2-116">보고서 디자인 뷰의 **삽입** 탭에서 **목록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-116">On the **Insert** tab in report design view, click **List**.</span></span>  
  
2.  <span data-ttu-id="8eda2-117">디자인 화면에서 상자를 클릭한 다음 끌어 원하는 크기의 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-117">On the design surface, click and then drag a box to the desired size of the list.</span></span> <span data-ttu-id="8eda2-118">또는 디자인 화면을 클릭하여 기본 크기의 목록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-118">Alternatively, click the design surface to create a list of default size.</span></span>  
  
3.  <span data-ttu-id="8eda2-119">**삽입** 탭에서 **입력란**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-119">On the **Insert** tab, click **Text Box**.</span></span>  
  
4.  <span data-ttu-id="8eda2-120">디자인 화면에서 1단계에서 추가한 목록 안쪽에 있는 상자를 클릭한 다음 끌어 원하는 크기의 입력란을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-120">On the design surface, click and then drag a box to the desired size of the text box inside the list you added in step 1.</span></span> <span data-ttu-id="8eda2-121">또는 목록 내의 디자인 화면을 클릭하여 기본 크기의 입력란을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-121">Alternatively, click the design surface inside the list to create a text box of default size.</span></span>  
  
5.  <span data-ttu-id="8eda2-122">입력란이 목록 안쪽에 올바르게 중첩되어 있는지 확인하려면 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-122">To confirm the text box is correctly nested inside the list, select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eda2-123">입력란을 클릭하여 편집 모드에 있는 경우에는 Esc 키를 눌러 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-123">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
6.  <span data-ttu-id="8eda2-124">속성 창에서 **부모** 속성이 목록 데이터 영역에 자동으로 추가된 사각형인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-124">In the Properties pane, verify that the **Parent** property is the rectangle that was automatically added to the list data region.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eda2-125">속성 창이 표시되지 않으면 **보기** 탭에서 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-125">If the Properties pane is not visible, check **Properties** on the **View** tab.</span></span>  
  
### <a name="to-move-a-text-box"></a><span data-ttu-id="8eda2-126">입력란을 이동하려면</span><span class="sxs-lookup"><span data-stu-id="8eda2-126">To move a text box</span></span>  
  
1.  <span data-ttu-id="8eda2-127">보고서 디자인 뷰에서 입력란 내의 빈 공간을 클릭하여 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-127">In report design view, click any empty space within the text box to select the text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eda2-128">입력란을 클릭하여 편집 모드에 있는 경우에는 Esc 키를 눌러 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-128">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
2.  <span data-ttu-id="8eda2-129">입력란 핸들을 클릭하고 입력란을 새 위치로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-129">Click the text box handle and drag the text box to the new location.</span></span> <span data-ttu-id="8eda2-130">또는 화살표 키를 사용하여 선택한 입력란을 가로 또는 세로로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-130">Alternatively, you can use the arrow keys to move a selected text box horizontally or vertically.</span></span> <span data-ttu-id="8eda2-131">디자인 화면에서 더 작은 증가값으로 입력란을 이동하려면 Ctrl 키를 누른 채 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-131">To move the text box in smaller increments on the design surface, hold down CTRL plus the arrow keys.</span></span>  
  
### <a name="to-delete-a-text-box"></a><span data-ttu-id="8eda2-132">입력란을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="8eda2-132">To delete a text box</span></span>  
  
1.  <span data-ttu-id="8eda2-133">보고서 디자인 뷰에서 입력란 내의 빈 공간을 마우스 오른쪽 단추로 클릭하여 입력란을 선택한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-133">In report design view, right-click any empty space within the text box to select it, and then click **Delete**.</span></span> <span data-ttu-id="8eda2-134">또는 입력란 안의 빈 공간을 클릭한 다음 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-134">Alternatively, click any empty space within the text box, and then press DELETE.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8eda2-135">입력란을 클릭하여 편집 모드에 있는 경우에는 Esc 키를 눌러 입력란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8eda2-135">If you click in the text box and are in edit mode, press ESC to select the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eda2-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8eda2-136">See Also</span></span>  
 <span data-ttu-id="8eda2-137">[텍스트 상자 &#40;보고서 작성기 및 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8eda2-137">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8eda2-138">[식&#40;보고서 작성기 및 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8eda2-138">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8eda2-139">바로 가기 키&#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="8eda2-139">Keyboard Shortcuts &#40;Report Builder&#41;</span></span>](../report-builder/keyboard-shortcuts-report-builder.md)  
  
  
