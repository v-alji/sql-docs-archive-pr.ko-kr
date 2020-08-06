---
title: '13 단원: Excel에서 분석 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 129956ddc8e755d1f2b298a7ea36307d50f52344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639045"
---
# <a name="lesson-13-analyze-in-excel"></a><span data-ttu-id="1a008-102">13단원: 도구 모음</span><span class="sxs-lookup"><span data-stu-id="1a008-102">Lesson 13: Analyze in Excel</span></span>
  <span data-ttu-id="1a008-103">이 단원에서는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 에서 Excel에서 분석 기능을 사용하여 Microsoft Excel을 열고, 모델 작업 영역에 자동으로 데이터 원본을 연결하고, 워크시트에 피벗 테이블을 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-103">In this lesson, you will use the Analyze in Excel feature in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to open Microsoft Excel, automatically create a data source connection to the model workspace, and automatically add a PivotTable to the worksheet.</span></span> <span data-ttu-id="1a008-104">Excel에서 분석 기능은 모델을 배포하기 전에 모델 디자인의 효율성을 테스트하기 위한 쉽고 빠른 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-104">The Analyze in Excel feature is meant to provide a quick and easy way to test the efficacy of your model design prior to deploying your model.</span></span> <span data-ttu-id="1a008-105">이 단원에서는 데이터 분석을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-105">You will not perform any data analysis in this lesson.</span></span> <span data-ttu-id="1a008-106">이 단원의 목적은 모델 작성자인 사용자가 모델 디자인을 테스트하는 데 사용할 수 있는 도구를 습득하게 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-106">The purpose of this lesson is to familiarize you, the model author, with the tools you can use to test your model design.</span></span> <span data-ttu-id="1a008-107">모델 작성자를 위한 Excel에서 분석 기능을 사용하는 것과 달리 최종 사용자는 Excel 또는 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] 와 같은 클라이언트 보고 애플리케이션을 사용하여 배포된 모델 데이터에 연결하고 해당 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-107">Unlike using the Analyze in Excel feature, which is meant for model authors, end-users will use client reporting applications such as Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] to connect to and browse deployed model data.</span></span>  
  
 <span data-ttu-id="1a008-108">이 단원을 완료하려면 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]가 설치되어 있는 컴퓨터에 Excel이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-108">In order to complete this lesson, Excel must be installed on the same computer as [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="1a008-109">자세한 내용은 [Excel에서 분석&#40;SSAS 테이블 형식&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1a008-109">To learn more, see [Analyze in Excel &#40;SSAS Tabular&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="1a008-110">이 단원을 완료하기 위한 예상 시간: **20분**</span><span class="sxs-lookup"><span data-stu-id="1a008-110">Estimated time to complete this lesson: **20 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1a008-111">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="1a008-111">Prerequisites</span></span>  
 <span data-ttu-id="1a008-112">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="1a008-113">이 단원의 태스크를 수행하려면 이전 단원인 [11단원: 파티션 만들기](lesson-10-create-partitions.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 11: Create Partitions](lesson-10-create-partitions.md).</span></span>  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a><span data-ttu-id="1a008-114">기본 및 인터넷 판매 큐브 뷰를 사용하여 찾아보기</span><span class="sxs-lookup"><span data-stu-id="1a008-114">Browse using the Default and Internet Sales perspectives</span></span>  
 <span data-ttu-id="1a008-115">이 첫 번째 태스크에서는 모든 모델 개체가 포함되어 있는 기본 큐브 뷰와 8단원: 큐브 뷰 만들기에서 만든 Internet Sales 큐브 뷰를 사용하여 모델을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-115">In these first tasks, you will browse your model by using both the default perspective, which includes all model objects, and also by using the Internet Sales perspective you created in Lesson 8: Create Perspectives.</span></span> <span data-ttu-id="1a008-116">Internet Sales 큐브 뷰에는 Customer 테이블 개체가 제외되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-116">The Internet Sales perspective excludes the Customer table object.</span></span>  
  
#### <a name="to-browse-by-using-the-default-perspective"></a><span data-ttu-id="1a008-117">기본 큐브 뷰를 사용하여 찾아보려면</span><span class="sxs-lookup"><span data-stu-id="1a008-117">To browse by using the Default perspective</span></span>  
  
1.  <span data-ttu-id="1a008-118">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **Excel에서 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-118">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="1a008-119">**Excel에서 분석** 대화 상자에서 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-119">In the **Analyze in Excel** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="1a008-120">Excel에 새 통합 문서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-120">Excel will open with a new workbook.</span></span> <span data-ttu-id="1a008-121">현재 사용자 계정을 사용하여 데이터 원본이 연결되고 보기 가능한 필드를 정의하는 데 기본 큐브 뷰가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-121">A data source connection is created using the current user account and the Default perspective is used to define viewable fields.</span></span> <span data-ttu-id="1a008-122">피벗 테이블이 자동으로 워크시트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-122">A Pivot table is automatically added to the worksheet.</span></span>  
  
3.  <span data-ttu-id="1a008-123">Excel의 **피벗 테이블 필드 목록**에 **Date** 및 **internet Sales** 측정값이 표시 되 고 **Customer**, **date**, **Geography**, **product**, **product Category**, **product 하위 범주**및 **internet Sales** 테이블에 해당 하는 모든 열이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-123">In Excel, in the **PivotTable Field List**, notice the **Date** and **Internet Sales** measures appear, as well as the **Customer**, **Date**, **Geography**, **Product**, **Product Category**, **Product Subcategory**, and **Internet Sales** tables with all of their respective columns appear.</span></span>  
  
4.  <span data-ttu-id="1a008-124">통합 문서를 저장하지 않은 채 Excel을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-124">Close Excel without saving the workbook.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a><span data-ttu-id="1a008-125">인터넷 판매 큐브 뷰를 사용하여 찾아보려면</span><span class="sxs-lookup"><span data-stu-id="1a008-125">To browse by using the Internet Sales perspective</span></span>  
  
1.  <span data-ttu-id="1a008-126">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **Excel에서 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-126">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="1a008-127">**Excel에서 분석** 대화 상자에서 **현재 Windows 사용자** 가 선택된 채로 두고 **큐브 뷰** 드롭다운 목록 상자에서 **Internet Sales**를 선택한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-127">In the **Analyze in Excel** dialog box, leave **Current Windows User** selected, then in the **Perspective** drop-down listbox, select **Internet Sales**, and then click **OK**.</span></span> <span data-ttu-id="1a008-128">Excel이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-128">Excel opens.</span></span>  
  
3.  <span data-ttu-id="1a008-129">Excel의 **피벗 테이블 필드 목록**에서 Customer 테이블이 필드 목록에서 제외되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-129">In Excel, in the **PivotTable Field List**, notice the Customer table is excluded from the field list.</span></span>  
  
## <a name="browse-using-roles"></a><span data-ttu-id="1a008-130">역할을 사용하여 찾아보기</span><span class="sxs-lookup"><span data-stu-id="1a008-130">Browse Using Roles</span></span>  
 <span data-ttu-id="1a008-131">역할은 테이블 형식 모델의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-131">Roles are an integral part of any tabular model.</span></span> <span data-ttu-id="1a008-132">사용자가 멤버로 추가된 하나 이상의 역할이 없는 경우 사용자는 모델을 사용하여 데이터에 액세스하고 분석할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-132">Without at least one role, to which users are added as members, users will not be able to access and analyze data using your model.</span></span> <span data-ttu-id="1a008-133">Excel에서 분석 기능은 정의한 역할을 테스트하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-133">The Analyze in Excel feature provides a way for you to test the roles you have defined.</span></span>  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a><span data-ttu-id="1a008-134">Internet Sales Manager 사용자 역할을 사용하여 찾아보려면</span><span class="sxs-lookup"><span data-stu-id="1a008-134">To browse by using the Internet Sales Manager user role</span></span>  
  
1.  <span data-ttu-id="1a008-135">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **Excel에서 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-135">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="1a008-136">**Excel에서 분석** 대화 상자의 **모델에 연결하는 데 사용할 사용자 이름 또는 역할을 지정하십시오.** 에서 **역할**을 선택한 다음 드롭다운 목록 상자에서 **Internet Sales Manager**를 선택하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-136">In the **Analyze in Excel** dialog box, in **Specify the user name or role to use to connect to the model**, select **Role**, and then in the drop-down listbox, select **Internet Sales Manager**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="1a008-137">Excel에 새 통합 문서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-137">Excel will open with a new workbook.</span></span> <span data-ttu-id="1a008-138">피벗 테이블은 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-138">A Pivot table is automatically created.</span></span> <span data-ttu-id="1a008-139">피벗 테이블 필드 목록에는 새 모델에서 사용할 수 있는 모든 데이터 필드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1a008-139">The Pivot Table Field List includes all of the data fields available in your new model.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1a008-140">다음 단계</span><span class="sxs-lookup"><span data-stu-id="1a008-140">Next Steps</span></span>  
 <span data-ttu-id="1a008-141">이 자습서를 계속하려면 다음 단원인 [14단원: 배포](lesson-13-deploy.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="1a008-141">To continue this tutorial, go to the next lesson: [Lesson 14: Deploy](lesson-13-deploy.md).</span></span>  
  
  
