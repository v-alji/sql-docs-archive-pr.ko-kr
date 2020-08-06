---
title: 데이터 원본 뷰 만들기 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c1e68a88-0f82-415d-becc-78d180d4f845
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4582845c905ef95601cbff2c810633f0cc901e3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649283"
---
# <a name="creating-a-data-source-view-basic-data-mining-tutorial"></a><span data-ttu-id="e9baa-102">데이터 원본 뷰 만들기(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="e9baa-102">Creating a Data Source View (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="e9baa-103">데이터 원본 뷰는 데이터 원본을 기반으로 하고, 마이닝 구조에 사용할 수 있는 데이터 하위 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-103">A data source view is built on a data source and defines a subset of the data, which you can then use in your mining structures.</span></span> <span data-ttu-id="e9baa-104">데이터 원본 뷰를 사용하여 열을 추가하고 계산 열 및 집계를 만들고 명명된 뷰를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-104">You can also use the data source view to add columns, create calculated columns and aggregates, and add named views.</span></span> <span data-ttu-id="e9baa-105">데이터 원본 뷰를 사용하면 원래 데이터 원본을 수정하지 않고도 프로젝트와 관련된 테이블을 선택하고 테이블 간의 관계를 설정하며 데이터 구조를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-105">By using data source views, you can select the data that relates to your project, establish relationships between tables, and modify the structure of the data, without modifying the original data source.</span></span> <span data-ttu-id="e9baa-106">자세한 내용은 [다차원 모델의 데이터 원본 뷰](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9baa-106">For more information, see [Data Source Views in Multidimensional Models](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models).</span></span>  
  
### <a name="to-create-a-data-source-view"></a><span data-ttu-id="e9baa-107">데이터 원본 뷰를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e9baa-107">To create a data source view</span></span>  
  
1.  <span data-ttu-id="e9baa-108">**솔루션 탐색기**에서 **데이터 원본 뷰**를 마우스 오른쪽 단추로 클릭하고 **새 데이터 원본 뷰**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-108">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="e9baa-109">**데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-109">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="e9baa-110">**데이터 원본 선택** 페이지의 **관계형 데이터 원본**아래에서 이전 태스크에서 만든 Adventure Works DW 2012 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-110">On the **Select a Data Source** page, under **Relational data sources**, select the Adventure Works DW 2012 data source that you created in the last task.</span></span> <span data-ttu-id="e9baa-111">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-111">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e9baa-112">데이터 원본을 만들려면 **데이터 원본** 을 마우스 오른쪽 단추로 클릭하고 **새 데이터 원본** 을 클릭하여 데이터 원본 마법사를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-112">If you want to create a data source, right-click **Data Sources** and then click **New Data Source** to start the Data Source Wizard.</span></span>  
  
4.  <span data-ttu-id="e9baa-113">**테이블 및 뷰 선택** 페이지에서 다음 개체를 선택하고 오른쪽 화살표를 클릭하여 새 데이터 원본 뷰에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-113">On the **Select Tables and Views** page, select the following objects, and then click the right arrow to include them in the new data source view:</span></span>  
  
    -   <span data-ttu-id="e9baa-114">**ProspectiveBuyer (dbo)** - 잠재 자전거 구매 고객의 테이블</span><span class="sxs-lookup"><span data-stu-id="e9baa-114">**ProspectiveBuyer (dbo)** - table of prospective bike buyers</span></span>  
  
    -   <span data-ttu-id="e9baa-115">**vTargetMail (dbo)** - 자전거 구매 고객에 대한 기록 데이터의 뷰</span><span class="sxs-lookup"><span data-stu-id="e9baa-115">**vTargetMail (dbo)** - view of historical data about past bike buyers</span></span>  
  
5.  <span data-ttu-id="e9baa-116">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-116">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="e9baa-117">**마법사 완료** 페이지에서는 기본적으로 데이터 원본 뷰의 이름이 Adventure Works DW 2012로 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-117">On the **Completing the Wizard** page, by default the data source view is named Adventure Works DW 2012.</span></span> <span data-ttu-id="e9baa-118">이름을로 변경 하 `Targeted Mailing` 고 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-118">Change the name to `Targeted Mailing`, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="e9baa-119">**Targeted Mailing.dsv [디자인]** 탭에 새 데이터 원본 뷰가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e9baa-119">The new data source view opens in the **Targeted Mailing.dsv [Design]** tab.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="e9baa-120">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="e9baa-120">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="e9baa-121">기본 데이터 마이닝 &#40;데이터 원본 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="e9baa-121">Creating a Data Source &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="e9baa-122">다음 단원</span><span class="sxs-lookup"><span data-stu-id="e9baa-122">Next Lesson</span></span>  
 [<span data-ttu-id="e9baa-123">2 단원: 기본 데이터 마이닝 자습서 &#40;대상 메일링 구조 구축&#41;</span><span class="sxs-lookup"><span data-stu-id="e9baa-123">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9baa-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9baa-124">See Also</span></span>  
 [<span data-ttu-id="e9baa-125">데이터 원본 뷰 정의&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="e9baa-125">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/defining-a-data-source-view-analysis-services)  
  
  
