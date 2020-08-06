---
title: '자습서: 텍스트 서식 지정(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 67d8513e-8a70-464b-b87f-e91d010cfd82
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c96b500f8aa30b77c78f75ccd1342398fd44eb2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737804"
---
# <a name="tutorial-format-text-report-builder"></a><span data-ttu-id="b092f-102">자습서: 텍스트 서식 지정(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="b092f-102">Tutorial: Format Text (Report Builder)</span></span>
  <span data-ttu-id="b092f-103">이 자습서에서는 텍스트에 서식을 지정하는 다양한 방법을 연습해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-103">In this tutorial, you can practice formatting text in various ways.</span></span> <span data-ttu-id="b092f-104">빈 보고서와 함께 데이터 원본 및 데이터 세트을 설정한 후 탐색할 단계를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-104">After you set up the blank report with the data source and dataset, you can pick and choose the steps that you want to explore.</span></span>  
  
 <span data-ttu-id="b092f-105">다음 그림에서는 만들려는 보고서와 비슷한 보고서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-105">The following illustration shows a report similar to the one you will create.</span></span>  
  
 <span data-ttu-id="b092f-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span><span class="sxs-lookup"><span data-stu-id="b092f-106">![rs_FormatTextFinal](../../2014/tutorials/media/rs-formattextfinal.gif "rs_FormatTextFinal")</span></span>  
  
 <span data-ttu-id="b092f-107">한 단계에서는 고의적으로 작업을 잘못 수행하므로 해당 작업이 잘못인 이유를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-107">In one step, you make a mistake on purpose so you can see why it is a mistake.</span></span> <span data-ttu-id="b092f-108">그런 다음 이를 올바르게 수정하여 원하는 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-108">Then you correct the mistake to achieve the desired effect.</span></span>  
  
 <span data-ttu-id="b092f-109">이 자습서에서 만드는 향상된 버전의 보고서는 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 보고서 작성기의 예제 보고서로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-109">An enhanced version of the report you create in this tutorial is available as a sample [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Report Builder report.</span></span> <span data-ttu-id="b092f-110">이 예제 보고서 및 기타 보고서를 다운로드하는 방법은 [보고서 작성기 예제 보고서(Report Builder sample reports)](https://go.microsoft.com/fwlink/?LinkId=184851)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b092f-110">For more information about downloading this sample report and others, see [Report Builder sample reports](https://go.microsoft.com/fwlink/?LinkId=184851).</span></span>  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a><span data-ttu-id="b092f-111">학습 내용</span><span class="sxs-lookup"><span data-stu-id="b092f-111">What You Will Learn</span></span>  
  
### <a name="set-up-the-report"></a><span data-ttu-id="b092f-112">보고서 설정</span><span class="sxs-lookup"><span data-stu-id="b092f-112">Set Up the Report</span></span>  
 1. [<span data-ttu-id="b092f-113">빈 보고서와 함께 데이터 원본 및 데이터 세트 만들기</span><span class="sxs-lookup"><span data-stu-id="b092f-113">Create a Blank Report with a Data Source and Dataset</span></span>](#CreateReport)  
  
 2. [<span data-ttu-id="b092f-114">보고서 디자인 화면에 필드 추가(잘못 추가한 후 올바르게 추가)</span><span class="sxs-lookup"><span data-stu-id="b092f-114">Add a Field to the Report Design Surface (Incorrectly, then Correctly)</span></span>](#AddField)  
  
 3. [<span data-ttu-id="b092f-115">보고서 디자인 화면에 테이블 추가</span><span class="sxs-lookup"><span data-stu-id="b092f-115">Add a Table to the Report Design Surface</span></span>](#AddTable)  
  
### <a name="pick-and-choose"></a><span data-ttu-id="b092f-116">선택</span><span class="sxs-lookup"><span data-stu-id="b092f-116">Pick and Choose</span></span>  
 [<span data-ttu-id="b092f-117">보고서에 하이퍼링크 추가</span><span class="sxs-lookup"><span data-stu-id="b092f-117">Add a Hyperlink to the Report</span></span>](#AddHyperlink)  
  
 [<span data-ttu-id="b092f-118">보고서의 텍스트 회전</span><span class="sxs-lookup"><span data-stu-id="b092f-118">Rotate Text in the Report</span></span>](#RotateText)  
  
 [<span data-ttu-id="b092f-119">HTML 서식을 사용하여 텍스트 표시</span><span class="sxs-lookup"><span data-stu-id="b092f-119">Displaying Text with HTML Formatting</span></span>](#FormatHTML)  
  
 [<span data-ttu-id="b092f-120">통화 서식 지정</span><span class="sxs-lookup"><span data-stu-id="b092f-120">Format Currency</span></span>](#FormatCurrency)  
  
 [<span data-ttu-id="b092f-121">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="b092f-121">Save the Report</span></span>](#Save)  
  
 <span data-ttu-id="b092f-122">이 자습서에 소요되는 예상 시간: 20분</span><span class="sxs-lookup"><span data-stu-id="b092f-122">Estimated time to complete this tutorial: 20 minutes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b092f-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b092f-123">Requirements</span></span>  
 <span data-ttu-id="b092f-124">요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b092f-124">For more information about requirements, see [Prerequisites for Tutorials &#40;Report Builder&#41;](../reporting-services/report-builder-tutorials.md).</span></span>  
  
##  <a name="create-a-blank-report-with-a-data-source-and-dataset"></a><a name="CreateReport"></a><span data-ttu-id="b092f-125">데이터 원본 및 데이터 집합을 사용 하 여 빈 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="b092f-125">Create a Blank Report with a Data Source and Dataset</span></span>  
  
#### <a name="to-create-a-blank-report"></a><span data-ttu-id="b092f-126">빈 보고서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b092f-126">To create a blank report</span></span>  
  
1.  <span data-ttu-id="b092f-127">**시작**을 클릭 하 고 **프로그램**, 보고서 작성기을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Report Builder**다음 **보고서 작성기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-127">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]**Report Builder**, and then click **Report Builder**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b092f-128">**시작** 대화 상자가 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-128">The **Getting Started** dialog box should appear.</span></span> <span data-ttu-id="b092f-129">이 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-129">If it does not, from the Report Builder button, click **New**.</span></span>  
  
2.  <span data-ttu-id="b092f-130">**시작** 대화 상자의 왼쪽 창에서 **새 보고서** 가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-130">In the left pane of the **Getting Started** dialog box, verify that **New Report** is selected.</span></span>  
  
3.  <span data-ttu-id="b092f-131">오른쪽 창에서 **빈 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-131">In the right pane, click **Blank Report**.</span></span>  
  
#### <a name="to-create-a-data-source"></a><span data-ttu-id="b092f-132">데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="b092f-132">To create a data source</span></span>  
  
1.  <span data-ttu-id="b092f-133">보고서 데이터 창에서 **새로 만들기**를 클릭 한 다음 **데이터 원본**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-133">In the Report Data pane, click **New**, and then click **Data Source**.</span></span>  
  
2.  <span data-ttu-id="b092f-134">**이름** 상자에 **TextDataSource**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-134">In the **Name** box, type: **TextDataSource**</span></span>  
  
3.  <span data-ttu-id="b092f-135">**내 보고서에 포함된 연결 사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-135">Click **Use a connection embedded in my report**.</span></span>  
  
4.  <span data-ttu-id="b092f-136">연결 형식이 Microsoft SQL Server 인지 확인 한 다음 **연결 문자열** 상자에 \*\*Data Source = \<servername> \*\* 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-136">Verify that the connection type is Microsoft SQL Server, and then in the **Connection string** box type: **Data Source = \<servername>**</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b092f-137">\<servername>식(예: Report001)은 SQL Server 데이터베이스 엔진의 인스턴스가 설치된 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-137">The expression \<servername>, for example Report001, specifies a computer on which an instance of the SQL Server Database Engine is installed.</span></span> <span data-ttu-id="b092f-138">이 자습서를 사용하기 위해 특정 데이터가 필요하지는 않습니다. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 데이터베이스에 연결하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-138">This tutorial does not need specific data; it just needs a connection to a [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] database.</span></span> <span data-ttu-id="b092f-139">**데이터 원본 연결**에 나열된 데이터 원본 연결이 이미 있는 경우 해당 데이터 원본 연결을 선택하고 다음 절차인 "데이터 세트를 만들려면"으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-139">If you already have a data source connection listed under **Data Source Connections**, you can select it and go to the next procedure, "To create a dataset."</span></span> <span data-ttu-id="b092f-140">자세한 내용은 [데이터에 연결하는 다른 방법&#40;보고서 작성기&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b092f-140">For more information, see [Alternative Ways to Get a Data Connection &#40;Report Builder&#41;](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md).</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-create-a-dataset"></a><span data-ttu-id="b092f-141">데이터 세트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="b092f-141">To create a dataset</span></span>  
  
1.  <span data-ttu-id="b092f-142">보고서 데이터 창에서 **새로 만들기**를 클릭 한 다음 **데이터 집합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-142">In the Report Data pane, click **New**, and then click **Dataset**.</span></span>  
  
2.  <span data-ttu-id="b092f-143">데이터 원본이 **TextDataSource**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-143">Verify that the data source is **TextDataSource**.</span></span>  
  
3.  <span data-ttu-id="b092f-144">**이름** 상자에 **TextDataset**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-144">In the **Name** box, type: **TextDataset.**</span></span>  
  
4.  <span data-ttu-id="b092f-145">**텍스트** 쿼리 유형이 선택되어 있는지 확인한 다음 **쿼리 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-145">Verify that the **Text** query type is selected, and then click **Query Designer**.</span></span>  
  
5.  <span data-ttu-id="b092f-146">**텍스트로 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-146">Click **Edit as Text**.</span></span>  
  
6.  <span data-ttu-id="b092f-147">쿼리 창에 다음 쿼리를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-147">Paste the following query into the query pane:</span></span>  
  
    ```  
    SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(16996.60 AS money) AS Sales, 68 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13747.25 AS money) AS Sales, 55 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Carrying Case' as Product, CAST(9248.15 AS money) As Sales, 37 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1350.00 AS money) AS Sales, 18 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1800.00 AS money) AS Sales, 24 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1125.00 AS money) AS Sales, 15 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1147.50 AS money) AS Sales, 17 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,  'Lens Adapter' as Product, CAST(742.50 AS money) AS Sales, 11 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1417.50 AS money) AS Sales, 21 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(13497.30 AS money) AS Sales, 54 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(11997.60 AS money) AS Sales, 48 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory, 'Carrying Case' as Product, CAST(10247.95 AS money) As Sales, 41 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory, 'Tripod' as Product, CAST(1200.00 AS money) AS Sales, 16 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(2025.00 AS money) AS Sales, 27 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Tripod' as Product, CAST(1425.00 AS money) AS Sales, 19 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(887.50 AS money) AS Sales, 13 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Accessories' as Subcategory, 'Lens Adapter' as Product, CAST(607.50 AS money) AS Sales, 9 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Accessories' as Subcategory,'Lens Adapter' as Product, CAST(1215.00 AS money) AS Sales, 18 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(10191.00 AS money) AS Sales, 79 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8772.00 AS money) AS Sales, 68 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(10578.00 AS money) AS Sales, 82 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(7218.10 AS money) AS Sales, 38 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory,'Digital' as Subcategory, 'Slim Digital' as Product, CAST(8357.80 AS money) AS Sales, 44 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-05' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory,'Digital' as Subcategory,'Slim Digital' as Product, CAST(9307.55 AS money) AS Sales, 49 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(3870.00 AS money) AS Sales, 30 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory,'Compact Digital' as Product, CAST(5805.00 AS money) AS Sales, 45 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate,  'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Compact Digital' as Product, CAST(8643.00 AS money) AS Sales, 67 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Lauren Johnson' as FullName,'Central' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(9877.40 AS money) AS Sales, 52 as Quantity, 'Installing Report Builder' as LinkText, 'https://go.microsoft.com/fwlink/?LinkId=154882' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Warren Pal' as FullName,'North' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(12536.70 AS money) AS Sales, 66 as Quantity, 'Getting Started with Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=160556' AS URL  
    UNION SELECT CAST('2009-01-06' AS date) as SalesDate, 'Fernando Ross' as FullName,'South' as Territory, 'Digital' as Subcategory, 'Slim Digital' as Product, CAST(6648.25 AS money) AS Sales, 35 as Quantity, 'What is New in Report Builder' as Link, 'https://go.microsoft.com/fwlink/?LinkId=165064' AS URL  
    ```  
  
7.  <span data-ttu-id="b092f-148">실행(**!**)을 클릭하여 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-148">Click Run (**!**) to run the query.</span></span>  
  
     <span data-ttu-id="b092f-149">쿼리 결과는 보고서에 표시할 수 있는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-149">The query results are the data available to display in your report.</span></span>  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="add-a-field-to-the-report-design-surface"></a><a name="AddField"></a><span data-ttu-id="b092f-150">보고서에 필드 추가 Design Surface</span><span class="sxs-lookup"><span data-stu-id="b092f-150">Add a Field to the Report Design Surface</span></span>  
 <span data-ttu-id="b092f-151">데이터 세트의 필드가 보고서에 나타나도록 하려는 경우 먼저 해당 필드를 디자인 화면으로 직접 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-151">If you want a field from your dataset to appear in a report, your first impulse may be to drag it directly to the design surface.</span></span> <span data-ttu-id="b092f-152">이 연습에서는 이러한 방법이 올바르지 않은 이유와 대신 사용할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-152">This exercise points out why that doesn't work and what to do instead.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-wrong-result"></a><span data-ttu-id="b092f-153">보고서에 필드를 추가하려면(잘못된 결과)</span><span class="sxs-lookup"><span data-stu-id="b092f-153">To add a field to the report (and get the wrong result)</span></span>  
  
1.  <span data-ttu-id="b092f-154">보고서 데이터 창의 **FullName** 필드를 디자인 화면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-154">Drag the **FullName** field from the Report Data pane to the design surface.</span></span>  
  
     <span data-ttu-id="b092f-155">보고서 작성기에서 \<Expr>로 표시된 식이 있는 입력란이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-155">Report Builder creates a text box with an expression in it, represented as \<Expr>.</span></span>  
  
2.  <span data-ttu-id="b092f-156">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-156">Click **Run**.</span></span>  
  
     <span data-ttu-id="b092f-157">쿼리의 첫 번째 레코드 **김철수 Ross**레코드는 하나 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-157">Note that there is just one record, **Fernando Ross**, which is alphabetically the first record in the query.</span></span> <span data-ttu-id="b092f-158">즉, 이 필드가 반복되어 해당 필드의 다른 레코드가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-158">The field does not repeat to show the other records in that field.</span></span>  
  
3.  <span data-ttu-id="b092f-159">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-159">Click **Design** to return to design view.</span></span>  
  
4.  <span data-ttu-id="b092f-160">입력란에서 \<Expr> 식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-160">Select the expression \<Expr> in the text box.</span></span>  
  
5.  <span data-ttu-id="b092f-161">**값** 속성에 대한 속성 창에서 다음을 확인합니다. 속성 창이 표시되지 않으면 **보기** 탭에서 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-161">In the Properties pane, for the **Value** property, you see the following (if you don't see the Properties pane, on the **View** tab, check **Properties**):</span></span>  
  
    ```  
    =First(Fields!FullName.Value, "TextDataSet")  
    ```  
  
     <span data-ttu-id="b092f-162">`First` 함수는 필드의 첫 번째 값만 검색하도록 디자인되었으므로 첫 번째 값만 검색되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-162">The `First` function is designed to retrieve only the first value in a field, and that is what it has done.</span></span>  
  
     <span data-ttu-id="b092f-163">필드를 디자인 화면으로 직접 끌어 올 때 입력란이 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-163">Dragging the field directly to the design surface created a text box.</span></span> <span data-ttu-id="b092f-164">입력란 자체는 데이터 영역이 아니므로 보고서 데이터 세트의 데이터가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-164">Text boxes by themselves are not data regions, so they do not display data from a report dataset.</span></span> <span data-ttu-id="b092f-165">테이블, 행렬 및 목록과 같은 데이터 영역의 입력란에는 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-165">Text boxes in data regions, such as tables, matrices, and lists, do display data.</span></span>  
  
6.  <span data-ttu-id="b092f-166">입력란을 선택하고 Delete 키를 누릅니다. 식이 선택된 경우 입력란을 선택하려면 Esc 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-166">Select the text box (if you have the expression selected, press ESC to select the text box), and press the DELETE key.</span></span>  
  
#### <a name="to-add-a-field-to-the-report-and-get-the-right-result"></a><span data-ttu-id="b092f-167">보고서에 필드를 추가하려면(올바른 결과)</span><span class="sxs-lookup"><span data-stu-id="b092f-167">To add a field to the report (and get the right result)</span></span>  
  
1.  <span data-ttu-id="b092f-168">리본의 **삽입** 탭에 있는 **데이터 영역** 영역에서 **목록**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-168">On the **Insert** tab of the ribbon, in the **Data Regions** area, click **List**.</span></span> <span data-ttu-id="b092f-169">디자인 화면을 클릭한 다음 끌어서 약 2인치 너비와 1인치 높이의 상자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-169">Click the design surface, and then drag to create a box that about two inches wide and one inch tall.</span></span>  
  
2.  <span data-ttu-id="b092f-170">보고서 데이터 창의 **FullName** 필드를 목록 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-170">Drag the **FullName** field from the Report Data pane to the list box.</span></span>  
  
     <span data-ttu-id="b092f-171">이번에는 보고서 작성기에서 `[FullName]` 식이 있는 입력란이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-171">This time Report Builder creates a text box with the expression `[FullName]` in it.</span></span>  
  
3.  <span data-ttu-id="b092f-172">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-172">Click **Run**.</span></span>  
  
     <span data-ttu-id="b092f-173">이번에는 입력란이 반복되어 쿼리의 모든 레코드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-173">Note that this time the box repeats to show all the records in the query.</span></span>  
  
4.  <span data-ttu-id="b092f-174">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-174">Click **Design** to return to design view.</span></span>  
  
5.  <span data-ttu-id="b092f-175">입력란에서 식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-175">Select the expression in the text box.</span></span>  
  
6.  <span data-ttu-id="b092f-176">**값** 속성에 대한 속성 창에서 다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-176">In the Properties pane, for the **Value** property, you see the following:</span></span>  
  
    ```  
    =Fields!FullName.Value  
    ```  
  
     <span data-ttu-id="b092f-177">입력란을 목록 데이터 영역으로 끌어 데이터 세트에 있는 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-177">By dragging the text box to the list data region, you display the data that is in the dataset.</span></span>  
  
7.  <span data-ttu-id="b092f-178">목록 상자를 선택하고 Delete 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-178">Select the list box and press the DELETE key.</span></span>  
  
##  <a name="add-a-table-to-the-report-design-surface"></a><a name="AddTable"></a><span data-ttu-id="b092f-179">보고서에 테이블을 추가 Design Surface</span><span class="sxs-lookup"><span data-stu-id="b092f-179">Add a Table to the Report Design Surface</span></span>  
 <span data-ttu-id="b092f-180">하이퍼링크와 회전된 텍스트를 배치할 수 있도록 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-180">Create this table so that you'll have a place to put hyperlinks and rotated text.</span></span>  
  
#### <a name="to-add-a-table-to-the-report"></a><span data-ttu-id="b092f-181">보고서에 테이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-181">To add a table to the report</span></span>  
  
1.  <span data-ttu-id="b092f-182">**삽입** 메뉴에서 **테이블**을 클릭 한 다음 **테이블 마법사**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-182">On the **Insert** menu, click **Table**, and then click **Table Wizard**.</span></span>  
  
2.  <span data-ttu-id="b092f-183">새 테이블 또는 행렬 마법사의 **데이터 집합 선택** 페이지에서 **이 보고서 또는 공유 데이터 집합의 기존 데이터 집합 선택**을 클릭 하 고 **textdataset (이 보고서)** 를 클릭 한 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-183">On the **Choose a dataset** page of the New Table or Matrix wizard, click **Choose an existing dataset in this report or a shared dataset**, and click **TextDataset (in this Report)**, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="b092f-184">**필드 정렬** 페이지에서 **지역**, **t**및 **Product** 필드를 **행 그룹**으로 끌고 **Sales** 필드를 **값**으로 끈 후 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-184">On the **Arrange fields** page, drag the **Territory**, **LinkText**, and **Product** fields to **Row groups**, drag the **Sales** field to **Values**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="b092f-185">**레이아웃 선택** 페이지에서 전체 테이블을 볼 수 있도록 **그룹 확장/축소** 확인란의 선택을 취소 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-185">On the **Choose the layout** page, clear the **Expand/collapse groups** check box so you can see the whole table, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b092f-186">**스타일 선택** 페이지에서 **슬레이트**를 클릭 한 다음 **마침**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-186">On the **Choose a style** page, click **Slate**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="b092f-187">테이블을 끌어 제목 블록 아래에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-187">Drag the table so it is below the title block.</span></span>  
  
7.  <span data-ttu-id="b092f-188">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-188">Click **Run**.</span></span>  
  
     <span data-ttu-id="b092f-189">테이블에 이상이 없어 보이지만 두 개의 합계 행이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-189">The table looks OK, but it has two Total rows.</span></span> <span data-ttu-id="b092f-190">**T** 필드에는 합계 행이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-190">The **LinkText** field doesn't need a Total row.</span></span>  
  
8.  <span data-ttu-id="b092f-191">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-191">Click **Design** to return to design view.</span></span>  
  
9. <span data-ttu-id="b092f-192">이 들어 있는 입력란을 마우스 오른쪽 단추로 클릭 `[LinkText]` 하 고 **셀 분할**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-192">Right-click the text box that contains `[LinkText]`, and click **Split Cells**.</span></span>  
  
10. <span data-ttu-id="b092f-193">셀 아래의 빈 셀을 선택한 `[LinkText]` 다음 shift 키를 누른 상태로 오른쪽에 있는 두 셀을 선택 합니다. **Product** 열의 **합계** 셀과 `[Sum(Sales)]` **Sales** 열의 셀을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-193">Select the empty cell below the `[LinkText]` cell, and then hold down the SHIFT key and select the two cells to its right: the **Total** cell in the **Product** column and the `[Sum(Sales)]` cell in the **Sales** column.</span></span>  
  
11. <span data-ttu-id="b092f-194">이 세 개의 셀을 선택한 상태에서 해당 셀 중 하나를 마우스 오른쪽 단추로 클릭 하 고 **행 삭제**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-194">With those three cells selected, right-click one of those cells and click **Delete Row**.</span></span>  
  
12. <span data-ttu-id="b092f-195">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-195">Click **Run**.</span></span>  
  
##  <a name="add-a-hyperlink-to-the-report"></a><a name="AddHyperlink"></a><span data-ttu-id="b092f-196">보고서에 하이퍼링크 추가</span><span class="sxs-lookup"><span data-stu-id="b092f-196">Add a Hyperlink to the Report</span></span>  
 <span data-ttu-id="b092f-197">이 섹션에서는 이전 섹션의 테이블에 있는 텍스트에 하이퍼링크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-197">In this section, you add a hyperlink to text in the table from the previous section.</span></span>  
  
#### <a name="to-add-a-hyperlink-to-the-report"></a><span data-ttu-id="b092f-198">보고서에 하이퍼링크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-198">To add a hyperlink to the report</span></span>  
  
1.  <span data-ttu-id="b092f-199">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-199">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b092f-200">`[LinkText]`가 들어 있는 셀을 마우스 오른쪽 단추로 클릭하고 **입력란 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-200">Right-click in the cell containing `[LinkText]`, and click **Text Box Properties**.</span></span>  
  
3.  <span data-ttu-id="b092f-201">**텍스트 상자 속성** 상자에서 **동작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-201">In the **Text Box Properties** box, click **Action**.</span></span>  
  
4.  <span data-ttu-id="b092f-202">**URL로 이동을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-202">Click **Go to URL**.</span></span>  
  
5.  <span data-ttu-id="b092f-203">**Url 선택** 상자에서 **[url]** 을 클릭 한 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-203">In the **Select URL** box, click **[URL]**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="b092f-204">텍스트가 다르게 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-204">Note that the text does not look any different.</span></span> <span data-ttu-id="b092f-205">텍스트가 링크 텍스트처럼 표시되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-205">You need to make it look like link text.</span></span>  
  
7.  <span data-ttu-id="b092f-206">`[LinkText]`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-206">Select `[LinkText]`.</span></span>  
  
8.  <span data-ttu-id="b092f-207">**홈** 탭의 **글꼴** 섹션에서 **밑줄** 단추를 클릭 하 고 **색** 단추 옆에 있는 드롭다운 화살표를 클릭 한 다음 **Blue**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-207">In the **Font** section of the **Home** tab, click the **Underline** button, and then click the drop-down arrow next to the **Color** button, and click **Blue**.</span></span>  
  
9. <span data-ttu-id="b092f-208">**실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-208">Click **Run**.</span></span>  
  
     <span data-ttu-id="b092f-209">이제 텍스트가 링크처럼 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-209">The text now looks like a link.</span></span>  
  
10. <span data-ttu-id="b092f-210">링크를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-210">Click a link.</span></span> <span data-ttu-id="b092f-211">컴퓨터가 인터넷에 연결되어 있으면 보고서 작성기 도움말 항목이 브라우저에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-211">If the computer is connected to the Internet, a browser will open to a Report Builder Help topic.</span></span>  
  
##  <a name="rotate-text-in-the-report"></a><a name="RotateText"></a><span data-ttu-id="b092f-212">보고서의 텍스트 회전</span><span class="sxs-lookup"><span data-stu-id="b092f-212">Rotate Text in the Report</span></span>  
 <span data-ttu-id="b092f-213">이 섹션에서는 이전 섹션의 테이블에 있는 텍스트 일부를 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-213">In this section, you rotate some of the text in the table from the previous sections.</span></span>  
  
#### <a name="to-rotate-text"></a><span data-ttu-id="b092f-214">텍스트를 회전하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-214">To rotate text</span></span>  
  
1.  <span data-ttu-id="b092f-215">**디자인** 을 클릭하여 디자인 뷰로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-215">Click **Design** to return to design view.</span></span>  
  
2.  <span data-ttu-id="b092f-216">가 들어 있는 셀을 클릭합니다.(!!) `[Territory].`</span><span class="sxs-lookup"><span data-stu-id="b092f-216">Click in the cell containing `[Territory].`</span></span>  
  
3.  <span data-ttu-id="b092f-217">**홈** 탭의 **글꼴** 섹션에서 **굵게** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-217">On the **Home** tab in the **Font** section, click the **Bold** button.</span></span>  
  
4.  <span data-ttu-id="b092f-218">속성 창이 열려 있지 않으면 **보기** 탭에서 **속성** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-218">If the Properties pane is not open, on the **View** tab, select the **Properties** check box.</span></span>  
  
5.  <span data-ttu-id="b092f-219">속성 창에서 WritingMode 속성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-219">Locate the WritingMode property in the Properties pane.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b092f-220">속성 창의 속성이 범주로 구성되어 있는 경우 WritingMode는 **지역화** 범주에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-220">When the properties in the Properties pane are organized into categories, WritingMode is in the **Localization** category.</span></span> <span data-ttu-id="b092f-221">셀만 선택하고 텍스트는 선택하지 말아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-221">Be sure you have selected the cell and not the text.</span></span> <span data-ttu-id="b092f-222">WritingMode는 텍스트가 아니라 입력란의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-222">WritingMode is a property of the text box, not of the text.</span></span>  
  
6.  <span data-ttu-id="b092f-223">목록 상자에서 **Rotate270**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-223">In the list box, click **Rotate270**.</span></span>  
  
7.  <span data-ttu-id="b092f-224">**단락** 섹션의 **홈** 탭에서 **가운데** 및 **가운데** 단추를 클릭 하 여 셀 가운데에서 세로 및 가로로 가운데에 있는 텍스트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-224">On the **Home** tab in the **Paragraph** section, click the **Middle** and **Center** buttons to locate the text in the center of the cell both vertically and horizontally.</span></span>  
  
8.  <span data-ttu-id="b092f-225">실행 (**!**)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-225">Click Run (**!**).</span></span>  
  
 <span data-ttu-id="b092f-226">이제 `[Territory]` 셀에 있는 텍스트가 셀의 아래쪽에서 위쪽으로 세로로 움직입니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-226">Now the text in the `[Territory]` cell runs vertically from the bottom to the top of the cells.</span></span>  
  
##  <a name="displaying-text-with-html-formatting"></a><a name="FormatHTML"></a><span data-ttu-id="b092f-227">HTML 서식을 사용 하 여 텍스트 표시</span><span class="sxs-lookup"><span data-stu-id="b092f-227">Displaying Text with HTML Formatting</span></span>  
  
#### <a name="to-display-text-formatted-as-html"></a><span data-ttu-id="b092f-228">HTML로 서식이 지정된 텍스트를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-228">To display text formatted as HTML</span></span>  
  
1.  <span data-ttu-id="b092f-229">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-229">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="b092f-230">**삽입** 탭에서 **입력란**을 클릭하고 디자인 화면에서 마우스 단추를 클릭한 다음 끌어서 테이블 아래에 약 4인치 너비와 3인치 높이의 입력란을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-230">On the **Insert** tab, click **Text Box**, and then on the design surface, click and drag to create a text box under the table, about four inches wide and three inches tall.</span></span>  
  
3.  <span data-ttu-id="b092f-231">이 텍스트를 복사하여 입력란에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-231">Copy this text and paste it into the text box:</span></span>  
  
    ```  
    <h4>Limitations of cascading style sheet attributes</h4>  
          <p>Only a basic set of <b>cascading style sheet (CSS)</b> attributes are defined:</p>  
          <ul><li>  
              text-align, text-indent  
            </li><li>  
              font-family, font-size  
            </li><li>  
              color  
            </li><li>  
              padding, padding-bottom, padding-top, padding-right, padding-left  
            </li><li>  
              font-weight  
            </li></ul>  
    ```  
  
4.  <span data-ttu-id="b092f-232">입력란의 모든 텍스트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-232">Select all of the text in the text box.</span></span>  
  
     <span data-ttu-id="b092f-233">이 속성은 입력란이 아니라 텍스트의 속성이므로 하나의 입력란에서 일반 텍스트와 HTML 태그를 스타일로 사용하는 텍스트가 혼합된 형태를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-233">This is a property of the text, not the text box, so in one text box you could have a mixture of plain text and text that uses HTML tags as styles.</span></span>  
  
5.  <span data-ttu-id="b092f-234">선택한 모든 텍스트를 마우스 오른쪽 단추로 클릭하고 **텍스트 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-234">Right-click all of the selected text and click **Text Properties**.</span></span>  
  
6.  <span data-ttu-id="b092f-235">**일반** 페이지의 **태그 형식**에서 **html-Html 태그를 스타일로 해석**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-235">On the **General** page, under **Markup type**, click **HTML - Interpret HTML tags as styles**.</span></span>  
  
7.  <span data-ttu-id="b092f-236">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-236">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="b092f-237">실행(**!**)을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-237">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="b092f-238">입력란의 텍스트가 머리글, 단락 및 글머리 기호 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-238">The text in the text box is displayed as a heading, paragraph, and bulleted list.</span></span>  
  
##  <a name="format-currency"></a><a name="FormatCurrency"></a><span data-ttu-id="b092f-239">통화 형식 지정</span><span class="sxs-lookup"><span data-stu-id="b092f-239">Format Currency</span></span>  
  
#### <a name="to-format-numbers-as-currency"></a><span data-ttu-id="b092f-240">숫자를 통화 서식으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-240">To format numbers as currency</span></span>  
  
1.  <span data-ttu-id="b092f-241">디자인 **을 클릭 하 여 디자인** 뷰로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-241">Click **Design** to switch to design view.</span></span>  
  
2.  <span data-ttu-id="b092f-242">`[Sum(Sales)]`이 들어 있는 위쪽 테이블 셀을 클릭하고 Shift 키를 누른 상태로 `[Sum(Sales)]`이 들어 있는 아래쪽 테이블 셀을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-242">Click the top table cell that contains `[Sum(Sales)]`, hold down the SHIFT key, and click the bottom table cell that contains `[Sum(Sales)]`.</span></span>  
  
3.  <span data-ttu-id="b092f-243">**홈** 탭의 **숫자** 그룹에서 **통화** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-243">On the **Home** tab, in the **Number** group, click the **Currency** button.</span></span>  
  
4.  <span data-ttu-id="b092f-244">필드 **홈** 탭의 **숫자** 그룹에서 **자리 표시자 스타일** 단추를 클릭 하 고 **샘플 값** 을 클릭 하 여 숫자의 서식을 지정 하는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-244">(Optional) On the **Home** tab, in the **Number** group, click the **Placeholder Styles** button and click **Sample Values** to see how the numbers will be formatted.</span></span>  
  
5.  <span data-ttu-id="b092f-245">(옵션) **홈** 탭에 있는 **숫자** 그룹에서 **소수 자릿수 줄이기** 단추를 두 번 클릭하여 센트가 표시되지 않는 달러 숫자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-245">(Optional) On the **Home** tab, in the **Number** group, click the **Decrease Decimals** button twice to display dollar figures with no cents.</span></span>  
  
6.  <span data-ttu-id="b092f-246">실행(**!**)을 클릭하여 보고서를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-246">Click Run (**!**) to preview the report.</span></span>  
  
 <span data-ttu-id="b092f-247">이제 보고서에 서식이 지정된 데이터가 표시되므로 보다 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-247">The report now displays formatted data and is easier to read.</span></span>  
  
##  <a name="save-the-report"></a><a name="Save"></a><span data-ttu-id="b092f-248">보고서 저장</span><span class="sxs-lookup"><span data-stu-id="b092f-248">Save the Report</span></span>  
 <span data-ttu-id="b092f-249">보고서를 보고서 서버, SharePoint 라이브러리 또는 컴퓨터에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-249">You can save reports to a report server, SharePoint library, or your computer.</span></span>  
  
 <span data-ttu-id="b092f-250">이 자습서에서는 보고서를 보고서 서버에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-250">In this tutorial, save the report to a report server.</span></span> <span data-ttu-id="b092f-251">보고서 서버에 액세스할 수 없는 경우에는 보고서를 컴퓨터에 저장하십시오.</span><span class="sxs-lookup"><span data-stu-id="b092f-251">If you do not have access to a report server, save the report to your computer.</span></span>  
  
#### <a name="to-save-the-report-on-a-report-server"></a><span data-ttu-id="b092f-252">보고서를 보고서 서버에 저장하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-252">To save the report on a report server</span></span>  
  
1.  <span data-ttu-id="b092f-253">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-253">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b092f-254">**최근에 사용한 사이트 및 서버**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-254">Click **Recent Sites and Servers**.</span></span>  
  
3.  <span data-ttu-id="b092f-255">보고서를 저장할 수 있는 권한을 가진 보고서 서버의 이름을 선택하거나 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-255">Select or type the name of the report server where you have permission to save reports.</span></span>  
  
     <span data-ttu-id="b092f-256">"보고서 서버에 연결하는 중"이라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-256">The message "Connecting to report server" appears.</span></span> <span data-ttu-id="b092f-257">연결되면 보고서 서버 관리자가 보고서의 기본 위치로 지정한 보고서 폴더의 내용이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-257">When the connection is complete, you see the contents of the report folder that the report server administrator specified as the default location for reports.</span></span>  
  
4.  <span data-ttu-id="b092f-258">**이름**에서 기본 이름을 선택한 이름으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-258">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
5.  <span data-ttu-id="b092f-259">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-259">Click **Save**.</span></span>  
  
 <span data-ttu-id="b092f-260">보고서가 보고서 서버에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-260">The report is saved to the report server.</span></span> <span data-ttu-id="b092f-261">연결된 보고서 서버의 이름이 창 아래쪽에 있는 상태 표시줄에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-261">The name of report server that you are connected to appears in the status bar at the bottom of the window.</span></span>  
  
#### <a name="to-save-the-report-on-your-computer"></a><span data-ttu-id="b092f-262">컴퓨터에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="b092f-262">To save the report on your computer</span></span>  
  
1.  <span data-ttu-id="b092f-263">**보고서 작성기** 단추에서 다른 **이름으로 저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-263">From the **Report Builder** button, click **Save As**.</span></span>  
  
2.  <span data-ttu-id="b092f-264">**바탕 화면**, **내 문서**또는 **내 컴퓨터**를 클릭한 다음 보고서를 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-264">Click **Desktop**, **My Documents**, or **My computer**, and then browse to the folder where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="b092f-265">**이름**에서 기본 이름을 선택한 이름으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-265">In **Name**, replace the default name with a name of your choosing.</span></span>  
  
4.  <span data-ttu-id="b092f-266">**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b092f-266">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b092f-267">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b092f-267">Next Steps</span></span>  
 <span data-ttu-id="b092f-268">보고서 작성기 자습서에서 텍스트의 서식을 지정 하는 방법에는 여러 가지가 있습니다. &#40;보고서 작성기&#41;추가 예제를 포함 하는 [자유 형식 보고서를 만듭니다](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) .</span><span class="sxs-lookup"><span data-stu-id="b092f-268">There are many ways to format text in Report Builder [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../reporting-services/tutorial-creating-a-free-form-report-report-builder.md) contains more examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b092f-269">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b092f-269">See Also</span></span>  
 <span data-ttu-id="b092f-270">[자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md) </span><span class="sxs-lookup"><span data-stu-id="b092f-270">[Tutorials &#40;Report Builder&#41;](report-builder-tutorials.md) </span></span>  
 <span data-ttu-id="b092f-271">[보고서 항목 서식 지정 &#40;보고서 작성기 및 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b092f-271">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b092f-272">SQL Server 2014의 보고서 작성기</span><span class="sxs-lookup"><span data-stu-id="b092f-272">Report Builder in SQL Server 2014</span></span>](report-builder/report-builder-in-sql-server-2016.md)  
  
  
