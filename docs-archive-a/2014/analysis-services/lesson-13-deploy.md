---
title: '14 단원: 배포 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1a55960a0c33a386d978f3c15e489ed7bd861ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639044"
---
# <a name="lesson-14-deploy"></a><span data-ttu-id="3a73f-102">14단원: 배포</span><span class="sxs-lookup"><span data-stu-id="3a73f-102">Lesson 14: Deploy</span></span>
  <span data-ttu-id="3a73f-103">이 단원에서는 테이블 형식 모드로 실행되는 Analysis Services의 배포 서버 인스턴스를 지정하고 배포할 모델의 이름을 지정하여 배포 속성을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-103">In this lesson, you will configure deployment properties; specifying a deployment server instance of Analysis Services running in Tabular mode, and a name for the model you deploy.</span></span> <span data-ttu-id="3a73f-104">그 다음에는 모델을 해당 인스턴스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-104">You will then deploy the model to that instance.</span></span> <span data-ttu-id="3a73f-105">모델을 배포한 후 사용자는 보고 클라이언트 애플리케이션을 사용하여 모델에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-105">After it is deployed, users can connect to the model by using a reporting client application.</span></span> <span data-ttu-id="3a73f-106">자세한 내용은 [테이블 형식 모델 솔루션 배포&#40;SSAS 테이블 형식&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a73f-106">To learn more, see [Tabular Model Solution Deployment &#40;SSAS Tabular&#41;](tabular-models/tabular-model-solution-deployment-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="3a73f-107">이 단원에 소요되는 예상 시간: **5분**</span><span class="sxs-lookup"><span data-stu-id="3a73f-107">Estimated time to complete this lesson: **5 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3a73f-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3a73f-108">Prerequisites</span></span>  
 <span data-ttu-id="3a73f-109">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-109">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="3a73f-110">이 단원의 태스크를 수행하려면 이전 단원인 [13단원: Excel에서 분석](lesson-12-analyze-in-excel.md)을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-110">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 13: Analyze in Excel](lesson-12-analyze-in-excel.md).</span></span>  
  
## <a name="deploy-the-model"></a><span data-ttu-id="3a73f-111">모델 배포</span><span class="sxs-lookup"><span data-stu-id="3a73f-111">Deploy the Model</span></span>  
  
#### <a name="to-configure-deployment-properties"></a><span data-ttu-id="3a73f-112">배포 속성을 구성하려면</span><span class="sxs-lookup"><span data-stu-id="3a73f-112">To configure deployment properties</span></span>  
  
1.  <span data-ttu-id="3a73f-113">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 **솔루션 탐색기**에서 **Adventure Works Internet Sales Tabular Model** 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 상황에 맞는 메뉴에서 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-113">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], in **Solution Explorer**, right-click on the **Adventure Works Internet Sales Tabular Model** project, and then in the context menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="3a73f-114">**AW Internet Sales Tabular Model 속성 페이지** 대화 상자에서 **배포 서버**아래의 **서버** 속성에 테이블 형식 모드로 실행 중인 Analysis Services 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-114">In the **AW Internet Sales Tabular Model Property Pages** dialog box, under **Deployment Server**, in the **Server** property, type the name of an Analysis Services instance running in Tabular mode.</span></span> <span data-ttu-id="3a73f-115">나중에 이 인스턴스에 모델을 배포하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-115">This will be the instance your model will be deployed to.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3a73f-116">원격 Analysis Services 인스턴스에 배포하려면 해당 인스턴스에 대한 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-116">You must have Administrator permissions on a remote Analysis Services instance in-order to deploy to it.</span></span>  
  
3.  <span data-ttu-id="3a73f-117">**쿼리 모드** 속성이 **메모리 내**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-117">Verify the **Query Mode** property is set to **In-Memory**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3a73f-118">이 자습서를 사용하여 만든 모델은 DirectQuery 모드에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-118">The model created by using this tutorial is not supported in DirectQuery mode.</span></span>  
  
4.  <span data-ttu-id="3a73f-119">**데이터베이스** 속성에을 입력 `Adventure Works Internet Sales Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-119">In the **Database** property, type `Adventure Works Internet Sales Model`.</span></span>  
  
5.  <span data-ttu-id="3a73f-120">**큐브** 이름 속성에을 입력 `Adventure Works Internet Sales Model` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-120">In the **Cube** Name property, type `Adventure Works Internet Sales Model`.</span></span>  
  
6.  <span data-ttu-id="3a73f-121">선택 내용을 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-121">Verify your selections and then click **OK**.</span></span>  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a><span data-ttu-id="3a73f-122">Adventure Works Internet Sales 테이블 형식 모델을 배포하려면</span><span class="sxs-lookup"><span data-stu-id="3a73f-122">To deploy the Adventure Works Internet Sales tabular model</span></span>  
  
1.  <span data-ttu-id="3a73f-123">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 **빌드** 메뉴를 클릭한 다음 **AW Internet Sales Tabular Model 배포**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-123">In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click the **Build** menu, and then click **Deploy AW Internet Sales Tabular Model**.</span></span>  
  
     <span data-ttu-id="3a73f-124">배포 대화 상자가 나타나고 메타데이터 및 모델에 포함된 각 테이블의 배포 상태가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-124">The Deploy dialog box appears and displays the deployment status of the metadata as well as each table included in the model.</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="3a73f-125">결론</span><span class="sxs-lookup"><span data-stu-id="3a73f-125">Conclusion</span></span>  
 <span data-ttu-id="3a73f-126">축하합니다!</span><span class="sxs-lookup"><span data-stu-id="3a73f-126">Congratulations!</span></span> <span data-ttu-id="3a73f-127">첫 번째 Analysis Services 테이블 형식 모델을 제작하고 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-127">You are finished authoring and deploying your first Analysis Services tabular model.</span></span> <span data-ttu-id="3a73f-128">이 자습서는 테이블 형식 모델을 만드는 가장 일반적인 작업을 완료하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-128">This tutorial has helped guide you through completing the most common tasks in creating a tabular model.</span></span> <span data-ttu-id="3a73f-129">이제 Adventure Works Internet Sales Model이 배포되었으므로 SQL Server Management Studio를 사용하여 모델을 관리하고 처리 스크립트와 백업 계획을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-129">Now that your Adventure Works Internet Sales Model is deployed, you can use SQL Server Management Studio to manage the model; create process scripts and a backup plan.</span></span> <span data-ttu-id="3a73f-130">사용자는 Microsoft Excel이나 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]같은 보고 클라이언트 애플리케이션을 사용하여 모델에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a73f-130">Users can connect to the model using a reporting client application such as Microsoft Excel or [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)].</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="3a73f-131">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="3a73f-131">Additional Resources</span></span>  
 <span data-ttu-id="3a73f-132">[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] 보고서를 지원하는 테이블 형식 모델 속성에 대한 자세한 내용은 [파워 뷰 보고 속성&#40;SSAS 테이블 형식&#41;](tabular-models/properties-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3a73f-132">To learn more about tabular model properties that support [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] reports, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](tabular-models/properties-ssas-tabular.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a73f-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a73f-133">See Also</span></span>  
 <span data-ttu-id="3a73f-134">[DirectQuery 모드 &#40;SSAS 테이블 형식&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3a73f-134">[DirectQuery Mode &#40;SSAS Tabular&#41;](tabular-models/directquery-mode-ssas-tabular.md) </span></span>  
 <span data-ttu-id="3a73f-135">[SSAS 테이블 형식&#41;&#40;기본 데이터 모델링 및 배포 속성 구성](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="3a73f-135">[Configure Default Data Modeling and Deployment Properties &#40;SSAS Tabular&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="3a73f-136">테이블 형식 model 데이터베이스&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="3a73f-136">Tabular Model Databases &#40;SSAS Tabular&#41;</span></span>](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
