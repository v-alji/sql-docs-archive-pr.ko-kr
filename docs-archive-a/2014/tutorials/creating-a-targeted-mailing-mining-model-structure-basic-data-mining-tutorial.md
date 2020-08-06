---
title: 타겟 메일링 마이닝 모델 구조 만들기 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6a27f818b29120e40248044091c78205dad945bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734727"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a><span data-ttu-id="7fe08-102">타겟 메일링 마이닝 모델 구조 만들기(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="7fe08-102">Creating a Targeted Mailing Mining Model Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="7fe08-103">타겟 메일링 시나리오를 만드는 첫 번째 단계는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 데이터 마이닝 마법사를 사용하여 새 마이닝 구조와 의사 결정 트리 마이닝 모델을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-103">The first step in creating a targeted mailing scenario is to use the Data Mining Wizard in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a new mining structure and decision tree mining model.</span></span>  
  
 <span data-ttu-id="7fe08-104">이 태스크에서는 새 마이닝 구조를 설정 하 고 [!INCLUDE[msCoName](../includes/msconame-md.md)] 의사 결정 트리 알고리즘을 기반으로 초기 마이닝 모델을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-104">In this task you will set up a new mining structure, and add an initial mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="7fe08-105">구조를 만들려면 먼저 테이블 및 뷰를 선택하고 학습에 사용될 열과 테스트에 사용될 열을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-105">To create the structure, you will first select tables and views and then identify which columns will be used for training and which for testing.</span></span>  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a><span data-ttu-id="7fe08-106">타겟 메일링 시나리오의 마이닝 구조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="7fe08-106">To create a mining structure for the targeted mailing scenario</span></span>  
  
1.  <span data-ttu-id="7fe08-107">솔루션 탐색기에서 **마이닝 구조** 를 마우스 오른쪽 단추로 클릭 하 고 **새 마이닝 구조** 를 선택 하 여 데이터 마이닝 마법사를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-107">In Solution Explorer, right-click **Mining Structures** and select **New Mining Structure** to start the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="7fe08-108">**데이터 마이닝 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-108">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="7fe08-109">**정의 방법 선택** 페이지에서 **기존 관계형 데이터베이스 또는 데이터 웨어하우스** 를 선택 했는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-109">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="7fe08-110">**데이터 마이닝 구조 만들기** 페이지의 **사용할 데이터 마이닝 기술**선택 페이지에서 **Microsoft 의사 결정 트리**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-110">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Decision Trees**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fe08-111">데이터 마이닝 알고리즘을 찾을 수 없다는 경고가 나타나는 경우 프로젝트 속성이 제대로 구성되지 않은 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-111">If you get a warning that no data mining algorithms can be found, the project properties might not be configured correctly.</span></span> <span data-ttu-id="7fe08-112">이 경고는 프로젝트가 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 서버에서 데이터 마이닝 알고리즘의 목록을 검색하려고 할 때 해당 서버를 찾을 수 없으면 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-112">This warning occurs when the project attempts to retrieve a list of data mining algorithms from the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server and cannot find the server.</span></span> <span data-ttu-id="7fe08-113">기본적으로에서는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] **localhost** 를 서버로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-113">By default, [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] will use **localhost** as the server.</span></span> <span data-ttu-id="7fe08-114">다른 인스턴스나 명명된 인스턴스를 사용할 경우에는 프로젝트 속성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-114">If you are using a different instance, or a named instance, you must change the project properties.</span></span> <span data-ttu-id="7fe08-115">자세한 내용은 [Analysis Services 프로젝트 만들기 &#40;기본 데이터 마이닝 자습서&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7fe08-115">For more information, see [Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="7fe08-116">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="7fe08-117">**데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰** 창에서 **대상 메일링**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-117">On the **Select Data Source View** page, in the **Available data source views** pane, select **Targeted Mailing**.</span></span> <span data-ttu-id="7fe08-118">**찾아보기** 를 클릭 하 여 데이터 원본 뷰의 테이블을 확인 한 다음 **닫기** 를 클릭 하 여 마법사로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-118">You can click **Browse** to view the tables in the data source view and then click **Close** to return to the wizard.</span></span>  
  
7.  <span data-ttu-id="7fe08-119">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-119">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="7fe08-120">**테이블 유형 지정** 페이지에서 사례 테이블로 사용할 vTargetMail의 **사례** 열에 있는 확인란을 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-120">On the **Specify Table Types** page, select the check box in the **Case** column for vTargetMail to use it as the case table, and then click **Next**.</span></span> <span data-ttu-id="7fe08-121">나중에 테스트를 위해 ProspectiveBuyer 테이블을 사용하겠지만 지금은 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-121">You will use the ProspectiveBuyer table later for testing; ignore it for now.</span></span>  
  
9. <span data-ttu-id="7fe08-122">**학습 데이터 지정** 페이지에서 모델에 대해 하나 이상의 예측 가능한 열, 하나의 키 열 및 하나의 입력 열을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-122">On the **Specify the Training Data** page, you will identify at least one predictable column, one key column, and one input column for your model.</span></span> <span data-ttu-id="7fe08-123">**Bikebuyer** 행의 **예측 가능한** 열에서 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-123">Select the check box in the **Predictable** column in the **BikeBuyer** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fe08-124">창 맨 아래에는 경고가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-124">Notice the warning at the bottom of the window.</span></span> <span data-ttu-id="7fe08-125">하나 이상의 **입력** 및 **예측 가능한** 열을 선택할 때까지 다음 페이지로 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-125">You will not be able to navigate to the next page until you select at least one **Input** and one **Predictable** column.</span></span>  
  
10. <span data-ttu-id="7fe08-126">**제안** 을 클릭 하 여 **관련 열 제안** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-126">Click **Suggest** to open the **Suggest Related Columns** dialog box.</span></span>  
  
     <span data-ttu-id="7fe08-127">하나 이상의 예측 가능한 특성을 선택할 때마다 **제안** 단추가 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-127">The **Suggest** button is enabled whenever at least one predictable attribute has been selected.</span></span> <span data-ttu-id="7fe08-128">**관련 열 제안** 대화 상자는 예측 가능한 열과 가장 밀접 하 게 관련 된 열을 나열 하 고 예측 가능한 특성과의 상관 관계를 기준으로 특성을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-128">The **Suggest Related Columns** dialog box lists the columns that are most closely related to the predictable column, and orders the attributes by their correlation with the predictable attribute.</span></span> <span data-ttu-id="7fe08-129">신뢰도가 95%보다 큰 높은 상관 관계의 열이 자동으로 선택되어 모델에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-129">Columns with a significant correlation (confidence greater than 95%) are automatically selected to be included in the model.</span></span>  
  
     <span data-ttu-id="7fe08-130">제안 사항을 검토 한 다음 제안 무시 **를 클릭 합니다** .</span><span class="sxs-lookup"><span data-stu-id="7fe08-130">Review the suggestions, and then click **Cancel** toignore the suggestions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fe08-131">**확인**을 클릭 하면 나열 된 모든 제안이 마법사에서 입력 열로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-131">If you click **OK**, all listed suggestions will be marked as input columns in the wizard.</span></span> <span data-ttu-id="7fe08-132">제안 사항에 일부만 동의하면 값을 수동으로 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-132">If you agree with only some of the suggestions, you must change the values manually.</span></span>  
  
11. <span data-ttu-id="7fe08-133">**Customerkey** 행에서 **키** 열의 확인란을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-133">Verify that the check box in the **Key** column is selected in the **CustomerKey** row.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7fe08-134">데이터 원본 뷰의 원본 테이블이 키를 나타내면 데이터 마이닝 마법사에서 해당 열이 모델의 키로 자동 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-134">If the source table from the data source view indicates a key, the Data Mining Wizard automatically chooses that column as a key for the model.</span></span>  
  
12. <span data-ttu-id="7fe08-135">다음 행의 **입력** 열에서 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-135">Select the check boxes in the **Input** column in the following rows.</span></span> <span data-ttu-id="7fe08-136">확인란을 선택하는 동안 셀 범위를 강조 표시하고 Ctrl 키를 눌러 여러 열을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-136">You can check multiple columns by highlighting a range of cells and pressing CTRL while selecting a check box.</span></span>  
  
    -   <span data-ttu-id="7fe08-137">**연령**</span><span class="sxs-lookup"><span data-stu-id="7fe08-137">**Age**</span></span>  
  
    -   <span data-ttu-id="7fe08-138">**CommuteDistance**</span><span class="sxs-lookup"><span data-stu-id="7fe08-138">**CommuteDistance**</span></span>  
  
    -   <span data-ttu-id="7fe08-139">**EnglishEducation**</span><span class="sxs-lookup"><span data-stu-id="7fe08-139">**EnglishEducation**</span></span>  
  
    -   <span data-ttu-id="7fe08-140">**EnglishOccupation**</span><span class="sxs-lookup"><span data-stu-id="7fe08-140">**EnglishOccupation**</span></span>  
  
    -   <span data-ttu-id="7fe08-141">**성별**</span><span class="sxs-lookup"><span data-stu-id="7fe08-141">**Gender**</span></span>  
  
    -   <span data-ttu-id="7fe08-142">**GeographyKey**</span><span class="sxs-lookup"><span data-stu-id="7fe08-142">**GeographyKey**</span></span>  
  
    -   <span data-ttu-id="7fe08-143">**HouseOwnerFlag**</span><span class="sxs-lookup"><span data-stu-id="7fe08-143">**HouseOwnerFlag**</span></span>  
  
    -   <span data-ttu-id="7fe08-144">**MaritalStatus**</span><span class="sxs-lookup"><span data-stu-id="7fe08-144">**MaritalStatus**</span></span>  
  
    -   <span data-ttu-id="7fe08-145">**NumberCarsOwned**</span><span class="sxs-lookup"><span data-stu-id="7fe08-145">**NumberCarsOwned**</span></span>  
  
    -   <span data-ttu-id="7fe08-146">**NumberChildrenAtHome**</span><span class="sxs-lookup"><span data-stu-id="7fe08-146">**NumberChildrenAtHome**</span></span>  
  
    -   <span data-ttu-id="7fe08-147">**지역**</span><span class="sxs-lookup"><span data-stu-id="7fe08-147">**Region**</span></span>  
  
    -   <span data-ttu-id="7fe08-148">**TotalChildren**</span><span class="sxs-lookup"><span data-stu-id="7fe08-148">**TotalChildren**</span></span>  
  
    -   <span data-ttu-id="7fe08-149">**YearlyIncome**</span><span class="sxs-lookup"><span data-stu-id="7fe08-149">**YearlyIncome**</span></span>  
  
13. <span data-ttu-id="7fe08-150">페이지의 가장 왼쪽 열에서 다음 행의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-150">On the far left column of the page, select the check boxes in the following rows.</span></span>  
  
    -   <span data-ttu-id="7fe08-151">**AddressLine1**</span><span class="sxs-lookup"><span data-stu-id="7fe08-151">**AddressLine1**</span></span>  
  
    -   <span data-ttu-id="7fe08-152">**AddressLine2**</span><span class="sxs-lookup"><span data-stu-id="7fe08-152">**AddressLine2**</span></span>  
  
    -   <span data-ttu-id="7fe08-153">**DateFirstPurchase**</span><span class="sxs-lookup"><span data-stu-id="7fe08-153">**DateFirstPurchase**</span></span>  
  
    -   <span data-ttu-id="7fe08-154">**EmailAddress**</span><span class="sxs-lookup"><span data-stu-id="7fe08-154">**EmailAddress**</span></span>  
  
    -   <span data-ttu-id="7fe08-155">**FirstName**</span><span class="sxs-lookup"><span data-stu-id="7fe08-155">**FirstName**</span></span>  
  
    -   <span data-ttu-id="7fe08-156">**LastName**</span><span class="sxs-lookup"><span data-stu-id="7fe08-156">**LastName**</span></span>  
  
     <span data-ttu-id="7fe08-157">왼쪽 열에서만 이러한 행에 확인란이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-157">Ensure that these rows have checks only in the left column.</span></span> <span data-ttu-id="7fe08-158">이러한 열은 구조에 추가되지만 모델에 포함되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-158">These columns will be added to your structure but will not be included in the model.</span></span> <span data-ttu-id="7fe08-159">그러나 모델을 작성하면 드릴스루 및 테스트에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-159">However, after the model is built, they will be available for drillthrough and testing.</span></span> <span data-ttu-id="7fe08-160">드릴스루에 대 한 자세한 내용은 [데이터 마이닝 &#40;드릴스루 쿼리](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) 를 참조 하세요&#41;</span><span class="sxs-lookup"><span data-stu-id="7fe08-160">For more information about drillthrough, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
14. <span data-ttu-id="7fe08-161">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7fe08-161">Click **Next**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7fe08-162">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="7fe08-162">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7fe08-163">기본 데이터 마이닝 자습서 &#40;데이터 형식 및 내용 유형 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="7fe08-163">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="7fe08-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fe08-164">See Also</span></span>  
 <span data-ttu-id="7fe08-165">[데이터 마이닝 마법사 &#40;테이블 형식을 지정&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7fe08-165">[Specify Table Types &#40;Data Mining Wizard&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="7fe08-166">[데이터 마이닝 디자이너](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="7fe08-166">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="7fe08-167">Microsoft 의사 결정 트리 알고리즘</span><span class="sxs-lookup"><span data-stu-id="7fe08-167">Microsoft Decision Trees Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
