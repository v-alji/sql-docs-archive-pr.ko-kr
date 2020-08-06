---
title: 차원 정의 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 112696db-3838-4b50-91bd-d2ce5fa04ee5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb7a695ffc2c0588396a4a9ea655983c26cc719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639042"
---
# <a name="defining-a-dimension"></a><span data-ttu-id="a9fc9-102">차원 정의</span><span class="sxs-lookup"><span data-stu-id="a9fc9-102">Defining a Dimension</span></span>
  <span data-ttu-id="a9fc9-103">다음 태스크에서는 차원 마법사를 사용하여 Date 차원을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-103">In the following task, you will use the Dimension Wizard to build a Date dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a9fc9-104">이 단원을 수행하려면 1단원의 모든 절차를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-104">This lesson requires that you have completed all the procedures in Lesson 1.</span></span>  
  
### <a name="to-define-a-dimension"></a><span data-ttu-id="a9fc9-105">차원을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="a9fc9-105">To define a dimension</span></span>  
  
1.  <span data-ttu-id="a9fc9-106">Microsoft Visual Studio의 오른쪽에 있는 솔루션 탐색기에서 **차원**을 마우스 오른쪽 단추로 클릭한 다음 **새 차원**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-106">In Solution Explorer (on the right side of Microsoft Visual Studio), right-click **Dimensions**, and then click **New Dimension**.</span></span> <span data-ttu-id="a9fc9-107">차원 마법사가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-107">The Dimension Wizard appears.</span></span>  
  
2.  <span data-ttu-id="a9fc9-108">**차원 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-108">On the **Welcome to the Dimension Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="a9fc9-109">**생성 방법 선택** 페이지에서 **기존 테이블 사용** 옵션이 선택되어 있는지 확인하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-109">On the **Select Creation Method** page, verify that the **Use an existing table** option is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="a9fc9-110">**원본 정보 지정** 페이지에서 **Adventure Works DW 2012** 데이터 원본 뷰가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-110">On the **Specify Source Information** page, verify that the **Adventure Works DW 2012** data source view is selected.</span></span>  
  
5.  <span data-ttu-id="a9fc9-111">**주 테이블** 목록에서 **Date**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-111">In the **Main table** list, select **Date**.</span></span>  
  
6.  <span data-ttu-id="a9fc9-112">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-112">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="a9fc9-113">**차원 특성 선택** 페이지에서 다음 특성 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-113">On the **Select Dimension Attributes** page, select the check boxes next to the following attributes:</span></span>  
  
    -   <span data-ttu-id="a9fc9-114">**Date Key**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-114">**Date Key**</span></span>  
  
    -   <span data-ttu-id="a9fc9-115">**Full Date Alternate Key**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-115">**Full Date Alternate Key**</span></span>  
  
    -   <span data-ttu-id="a9fc9-116">**English Month Name**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-116">**English Month Name**</span></span>  
  
    -   <span data-ttu-id="a9fc9-117">**일정 분기**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-117">**Calendar Quarter**</span></span>  
  
    -   <span data-ttu-id="a9fc9-118">**역 년**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-118">**Calendar Year**</span></span>  
  
    -   <span data-ttu-id="a9fc9-119">**Calendar Semester**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-119">**Calendar Semester**</span></span>  
  
8.  <span data-ttu-id="a9fc9-120">**Full Date Alternate Key** 특성의 **특성 유형** 열 설정을 **일반** 에서 **날짜**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-120">Change the setting of the **Full Date Alternate Key** attribute's **Attribute Type** column from **Regular** to **Date**.</span></span> <span data-ttu-id="a9fc9-121">이렇게 하려면 **특성 유형** 열에서 **일반** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-121">To do this, click **Regular** in the **Attribute Type** column.</span></span> <span data-ttu-id="a9fc9-122">그런 다음 화살표를 클릭하여 옵션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-122">Then click the arrow to expand the options.</span></span> <span data-ttu-id="a9fc9-123">그런 다음 **날짜**  >  **달력**  >  **날짜**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-123">Next, click **Date** > **Calendar** > **Date**.</span></span> <span data-ttu-id="a9fc9-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-124">Click **OK**.</span></span> <span data-ttu-id="a9fc9-125">이 단계를 반복하여 특성의 특성 유형을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-125">Repeat these steps to change the attribute type of the attributes as follows:</span></span>  
  
    -   <span data-ttu-id="a9fc9-126">**English Month Name** 에서 **Month**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-126">**English Month Name** to **Month**</span></span>  
  
    -   <span data-ttu-id="a9fc9-127">**Calendar Quarter** 에서 **Quarter**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-127">**Calendar Quarter** to **Quarter**</span></span>  
  
    -   <span data-ttu-id="a9fc9-128">**Calendar Year** 에서 **Year**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-128">**Calendar Year** to **Year**</span></span>  
  
    -   <span data-ttu-id="a9fc9-129">**Calendar Semester** 에서 **Half Year**</span><span class="sxs-lookup"><span data-stu-id="a9fc9-129">**Calendar Semester** to **Half Year**</span></span>  
  
9. <span data-ttu-id="a9fc9-130">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-130">Click **Next**.</span></span>  
  
10. <span data-ttu-id="a9fc9-131">**마법사 완료** 페이지의 미리 보기 창에서 **Date** 차원 및 해당 특성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-131">On the **Completing the Wizard** page, in the Preview pane, you can see the **Date** dimension and its attributes.</span></span>  
  
11. <span data-ttu-id="a9fc9-132">**마침**을 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-132">Click **Finish** to complete the wizard.</span></span>  
  
     <span data-ttu-id="a9fc9-133">솔루션 탐색기의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에서 Date 차원은 **차원** 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-133">In Solution Explorer, in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, the Date dimension appears in the **Dimensions** folder.</span></span> <span data-ttu-id="a9fc9-134">차원 디자이너는 개별 환경의 가운데에 Date 차원을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-134">In the center of the development environment, Dimension Designer displays the Date dimension.</span></span>  
  
12. <span data-ttu-id="a9fc9-135">**파일** 메뉴에서 **모두 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a9fc9-135">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a9fc9-136">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="a9fc9-136">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a9fc9-137">큐브 정의</span><span class="sxs-lookup"><span data-stu-id="a9fc9-137">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="a9fc9-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a9fc9-138">See Also</span></span>  
 <span data-ttu-id="a9fc9-139">[다차원 모델의 차원](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a9fc9-139">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="a9fc9-140">[기존 테이블을 사용 하 여 차원 만들기](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span><span class="sxs-lookup"><span data-stu-id="a9fc9-140">[Create a Dimension by Using an Existing Table](multidimensional-models/create-a-dimension-by-using-an-existing-table.md) </span></span>  
 [<span data-ttu-id="a9fc9-141">차원 마법사를 사용하여 차원 만들기</span><span class="sxs-lookup"><span data-stu-id="a9fc9-141">Create a Dimension Using the Dimension Wizard</span></span>](multidimensional-models/create-a-dimension-using-the-dimension-wizard.md)  
  
  
