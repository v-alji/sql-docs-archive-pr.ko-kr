---
title: '작업 4 (선택 사항): 새 데이터 집합 결합, 일치 및 게시 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13a13f03-b307-4555-8e33-6d98c459d994
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9ddcec19fa8b957bf77b6ea5269b4d033779bdf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646741"
---
# <a name="task-4-optional-combining-matching-and-publishing-new-set-of-data"></a><span data-ttu-id="be227-102">태스크 4(선택 사항): 새 데이터 세트 결합, 일치 및 게시</span><span class="sxs-lookup"><span data-stu-id="be227-102">Task 4 (Optional): Combining, Matching, and Publishing New Set of Data</span></span>
  <span data-ttu-id="be227-103">시간이 지날수록 MDS 저장소에 추가하는 데이터가 늘어나게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-103">Over time, you will want to add more data to the MDS repository.</span></span> <span data-ttu-id="be227-104">데이터를 추가 하기 전에 MDS에서 이미 관리 되는 데이터와 새 데이터를 비교 하 여 중복 되거나 부정확 한 데이터를 추가 하지 않도록 하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-104">Before adding data, it can be useful to compare the new data to the data that's already managed in MDS, to ensure that you are not adding duplicate or inaccurate data.</span></span> <span data-ttu-id="be227-105">Excel용 Master Data Services 추가 기능에서는 데이터를 MDS에 게시하기 전에 두 워크시트의 데이터를 결합하고 데이터를 비교해서 중복된 항목을 식별하고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-105">In the Master Data Services Add-in for Excel, you can combine data from two worksheets and the compare the data to identify and remove duplicates before publishing the data to MDS.</span></span> <span data-ttu-id="be227-106">MDS Excel 추가 기능의 일치 기능에는 데이터에서 일치 항목을 식별하기 위해 DQS 일치 기능이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-106">The matching feature of MDS Excel Add-in uses the DQS matching functionality to identify matches in the data.</span></span> <span data-ttu-id="be227-107">이 작업에서는 MDS에 데이터를 게시하기 전에 두 워크시트의 데이터를 하나로 결합한 후 일치 작업을 수행해서 중복된 항목을 식별하고 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-107">In this task, you will combine data from a two worksheets into one and then perform the matching activity to identify and remove duplicates before publishing to MDS.</span></span> <span data-ttu-id="be227-108">자세한 내용은 Excel용 MDS 추가 기능 및 [데이터 결합](https://msdn.microsoft.com/library/hh548680.aspx) 항목 [의 데이터 품질 일치](https://msdn.microsoft.com/library/hh548681.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="be227-108">See [Data Quality Matching in the MDS Add-in for Excel](https://msdn.microsoft.com/library/hh548681.aspx) and [Combine Data](https://msdn.microsoft.com/library/hh548680.aspx) topics for more details.</span></span>  
  
1.  <span data-ttu-id="be227-109">새 **Excel**인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-109">Launch new instance of **Excel**.</span></span> <span data-ttu-id="be227-110">**시작**을 클릭 하 고 **실행**을 가리킨 다음 **Excel**을 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-110">Click **Start**, point to **Run**, type **Excel**, and click **OK**.</span></span>  
  
2.  <span data-ttu-id="be227-111">메뉴 모음에서 **마스터 데이터** 를 클릭 하 여 **마스터 데이터** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-111">Switch to the **Master Data** tab by clicking **Master Data** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="be227-112">연결 **및 로드** 그룹의 리본에서 **연결** 을 클릭 하 여 **MDS 서버**에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-112">Click **Connect** on the ribbon in the **Connect and Load** group to connect to the **MDS server**.</span></span> <span data-ttu-id="be227-113">이 연결은 이 단원의 앞 부분에서 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-113">You have configured this connection earlier in this lesson.</span></span>  
  
     <span data-ttu-id="be227-114">![Excel - 마스터 데이터 탭의 탐색기 표시 단추](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - 마스터 데이터 탭의 탐색기 표시 단추")</span><span class="sxs-lookup"><span data-stu-id="be227-114">![Excel - Show Explorer Button on Master Data Tabl](../../2014/tutorials/media/et-combinematchandpublishnewsod-01.jpg "Excel - Show Explorer Button on Master Data Tabl")</span></span>  
  
4.  <span data-ttu-id="be227-115">오른쪽에 **마스터 데이터 탐색기** 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-115">You should see the **Master Data Explorer** pane to the right.</span></span> <span data-ttu-id="be227-116">마스터 데이터 탐색기 표시 되지 않으면 리본에서 **탐색기 표시** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-116">If you do not see the Master Data Explorer, click **Show Explorer** button on the ribbon.</span></span>  
  
5.  <span data-ttu-id="be227-117">**마스터 데이터 탐색기** 창의 **모델**드롭다운 목록에서 **Suppliers** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-117">In the **Master Data Explorer** Window, select **Suppliers** in the drop-down list for the **Model**.</span></span> <span data-ttu-id="be227-118">모델에는 **공급자**가 하나씩 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-118">You should see that the model has one entity: **Supplier**.</span></span>  
  
     <span data-ttu-id="be227-119">![Excel - 마스터 데이터 탐색기 창](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - 마스터 데이터 탐색기 창")</span><span class="sxs-lookup"><span data-stu-id="be227-119">![Excel - Master Data Explorer Window](../../2014/tutorials/media/et-combinematchandpublishnewsod-02.jpg "Excel - Master Data Explorer Window")</span></span>  
  
6.  <span data-ttu-id="be227-120">엔터티 목록에서 **공급자** 를 두 번 클릭 하 여 엔터티 멤버를 Excel 워크시트로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-120">Double-click **Supplier** in the entity list to load the entity members into the Excel worksheet.</span></span>  
  
7.  <span data-ttu-id="be227-121">맨 아래에 있는 **sheet2** 를 클릭 하 여 **sheet2** 탭으로 전환 합니다. **Sheet2**가 표시 되지 않으면 새 워크시트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-121">Click **Sheet2** at the bottom to switch to the **Sheet2** tab. If you do not see **Sheet2**, add a new worksheet.</span></span>  
  
8.  <span data-ttu-id="be227-122">**Suppliers.xls** 파일 (자습서 파일에 포함 된 원본 입력 파일)을 열고 **CombineAndCleanse** 워크시트의 모든 행 (3 개)을 **Sheet2**로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-122">Open **Suppliers.xls** file (the original input file that is included in the tutorial files) and copy all (three) rows from the **CombineAndCleanse** worksheet to **Sheet2**.</span></span>  
  
9. <span data-ttu-id="be227-123">**MDS**에 연결 된 **Microsoft excel** ( **정리 및 일치 하는 공급자 목록** Excel이 아님)의 **공급 업체** 시트로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-123">Switch back to the **Supplier** sheet in the **Book 1 - Microsoft Excel** (not the **Cleansed and Matched Supplier List** Excel) that is connected to **MDS**.</span></span>  
  
10. <span data-ttu-id="be227-124">메뉴 모음에서 **마스터 데이터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-124">Click **Master Data** on the menu bar.</span></span>  
  
11. <span data-ttu-id="be227-125">리본에서 **데이터 결합** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-125">Click **Combine Data** on the ribbon.</span></span> <span data-ttu-id="be227-126">**데이터 결합** 대화 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-126">You will see the **Combine Data** dialog box.</span></span>  
  
12. <span data-ttu-id="be227-127">**데이터 결합** 대화 상자에서 다음 이미지에 표시 된 것과 같이 **MDS 데이터와 결합할 범위** 옆의 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-127">In the **Combine Data** dialog box, click the button next to **Range to combine with MDS data** text box as shown in the following image.</span></span>  
  
     <span data-ttu-id="be227-128">![Excel - 데이터 결합 대화 상자](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - 데이터 결합 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="be227-128">![Excel - Combine Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-03.jpg "Excel - Combine Data Dialog Box")</span></span>  
  
13. <span data-ttu-id="be227-129">지금은 대화 상자가 축소된 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-129">You should see the shrunken dialog box now.</span></span> <span data-ttu-id="be227-130">이제 **sheet2** 를 클릭 하 여 행이 4 개 (헤더 행 포함) 인 새 공급자 데이터가 있는 **sheet2** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-130">Now, click **Sheet2** to switch to the **Sheet2** tab that has the new supplier data with 4 rows (including one header row).</span></span>  
  
14. <span data-ttu-id="be227-131">**Sheet2**에서 **머리글 행을 포함 하는 모든 행** 을 선택 합니다 (이미 선택 되어 있는 경우에도).</span><span class="sxs-lookup"><span data-stu-id="be227-131">In the **Sheet2**, select **all rows including the header row** (even if they seem to be already selected).</span></span> <span data-ttu-id="be227-132">**MDS 데이터와 결합할 범위가** 자동으로 업데이트 되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-132">You should see the **Range to combine with MDS data** is automatically updated.</span></span>  
  
     <span data-ttu-id="be227-133">![Excel - 데이터 결합 대화 상자 - 최소화됨](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - 데이터 결합 대화 상자 - 최소화됨")</span><span class="sxs-lookup"><span data-stu-id="be227-133">![Excel - Combine Data Dialog Box - Minimized](../../2014/tutorials/media/et-combinematchandpublishnewsod-04.jpg "Excel - Combine Data Dialog Box - Minimized")</span></span>  
  
15. <span data-ttu-id="be227-134">**데이터 결합** 대화 상자를 닫지 않고 **Suppliers** 탭으로 다시 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-134">Switch back to the **Suppliers** tab without closing the **Combine Data** dialog box.</span></span>  
  
16. <span data-ttu-id="be227-135">**텍스트 상자**옆에 있는 **단추** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-135">Click the **button** next to the **text box**.</span></span> <span data-ttu-id="be227-136">이제 대화 상자가 확장된 상태로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-136">You should see that the dialog box is expanded now.</span></span> <span data-ttu-id="be227-137">**공급자** MDS **엔터티** 열과 **Excel** 열 간의 모든 매핑이 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="be227-137">You should see all the mappings between columns of the **Supplier** MDS **entity** to **Excel** columns are automatically populated.</span></span>  
  
     <span data-ttu-id="be227-138">![Excel - 데이터로 채워진 데이터 결합 대화 상자](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - 데이터로 채워진 데이터 결합 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="be227-138">![Excel - Combine Data Dialog Box Filled with Data](../../2014/tutorials/media/et-combinematchandpublishnewsod-05.jpg "Excel - Combine Data Dialog Box Filled with Data")</span></span>  
  
17. <span data-ttu-id="be227-139">**Code** 엔터티 열이 워크시트의 **공급자** 열에 매핑되고 **우편** 번호 엔터티 열이 워크시트의 **우편** 번호 열에 매핑되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-139">Ensure that **Code** entity column is mapped to the **SupplierID** column in the worksheet and **Zip Code** entity column is mapped to the **Zip Code** column in the worksheet.</span></span>  
  
18. <span data-ttu-id="be227-140">**데이터 결합** 대화 상자에서 **결합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-140">On the **Combine Data** dialog box, click **Combine**.</span></span>  
  
19. <span data-ttu-id="be227-141">세 개의 데이터 행이 워크시트 하단에 추가되었고 색상으로 표시되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-141">Confirm that three data rows are added to the bottom of the worksheet and they should be color coded.</span></span>  
  
     <span data-ttu-id="be227-142">![Excel - 결합 후 새 요소](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - 결합 후 새 요소")</span><span class="sxs-lookup"><span data-stu-id="be227-142">![Excel - New Elements after Combining](../../2014/tutorials/media/et-combinematchandpublishnewsod-06.jpg "Excel - New Elements after Combining")</span></span>  
  
20. <span data-ttu-id="be227-143">리본에서 **수학 데이터** 를 클릭 하 여 중복 항목을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-143">Click **Math Data** on the ribbon to identify duplicates.</span></span> <span data-ttu-id="be227-144">이 기능은 DQS의 일치 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-144">This feature uses the matching functionality of DQS.</span></span>  
  
21. <span data-ttu-id="be227-145">**데이터 일치** 대화 상자에서 **DQS 기술 자료**에 대 한 **공급자** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-145">In the **Match Data** dialog box, select **Suppliers** for **DQS Knowledge Base**.</span></span>  
  
     <span data-ttu-id="be227-146">![Excel - 데이터 일치 대화 상자](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - 데이터 일치 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="be227-146">![Excel - Match Data Dialog Box](../../2014/tutorials/media/et-combinematchandpublishnewsod-07.jpg "Excel - Match Data Dialog Box")</span></span>  
  
22. <span data-ttu-id="be227-147">다음 표에 표시된 대로 워크시트 열을 도메인에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-147">Map worksheet columns to domains as shown in the following table.</span></span>  
  
    |<span data-ttu-id="be227-148">워크시트 열</span><span class="sxs-lookup"><span data-stu-id="be227-148">Worksheet Column</span></span>|<span data-ttu-id="be227-149">도메인</span><span class="sxs-lookup"><span data-stu-id="be227-149">Domain</span></span>|  
    |----------------------|------------|  
    |<span data-ttu-id="be227-150">Code(MDS에서 Supplier 엔터티에 대한 Code로 업로드한 Supplier ID)</span><span class="sxs-lookup"><span data-stu-id="be227-150">Code (you uploaded Supplier ID as the Code for the Supplier entity in MDS)</span></span>|<span data-ttu-id="be227-151">Supplier ID</span><span class="sxs-lookup"><span data-stu-id="be227-151">Supplier ID</span></span>|  
    |<span data-ttu-id="be227-152">Name(MDS에 Supplier 엔터티에 대한 이름으로 업로드한 Supplier Name)</span><span class="sxs-lookup"><span data-stu-id="be227-152">Name (you uploaded Supplier Name as the Name for the Supplier entity to MDS)</span></span>|<span data-ttu-id="be227-153">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="be227-153">Supplier Name</span></span>|  
    |<span data-ttu-id="be227-154">ContactEmailAddress</span><span class="sxs-lookup"><span data-stu-id="be227-154">ContactEmailAddress</span></span>|<span data-ttu-id="be227-155">ContactEmail</span><span class="sxs-lookup"><span data-stu-id="be227-155">ContactEmail</span></span>|  
  
23. <span data-ttu-id="be227-156">**코드** 열 매핑의 **필수 구성 요소** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-156">Select **Prerequisite** for the **Code** column mapping.</span></span>  
  
24. <span data-ttu-id="be227-157">이미지에 **표시 된 것** 처럼 **연락처 전자 메일** 의 **가중치** 로 **70%** 를 **공급 업체 이름** 및 **30%** 로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-157">Enter **70%** as the **weight** for **Supplier Name** and **30%** as the **weight** for **Contact Email** as shown in the image.</span></span>  
  
25. <span data-ttu-id="be227-158">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-158">Click **OK**.</span></span>  
  
26. <span data-ttu-id="be227-159">일치 프로세스에서 **코드: S1**의 공급자에 대해 하나의 중복 항목을 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-159">The matching process should identify one duplicate for the supplier with **Code: S1**.</span></span>  
  
     <span data-ttu-id="be227-160">![Excel - 일치 결과](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - 일치 결과")</span><span class="sxs-lookup"><span data-stu-id="be227-160">![Excel - Matching Results](../../2014/tutorials/media/et-combinematchandpublishnewsod-08.jpg "Excel - Matching Results")</span></span>  
  
27. <span data-ttu-id="be227-161">**중복 행 (주황)** 을 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **삭제** 를 클릭 하 여 행을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-161">Select the **duplicate row (orange)**, right-click, and click **Delete** to delete the row.</span></span>  
  
28. <span data-ttu-id="be227-162">**CLUSTER_ID** 열은 더 이상 필요 하지 않으므로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-162">Delete the **CLUSTER_ID** column since you don't need it anymore.</span></span>  
  
29. <span data-ttu-id="be227-163">**게시** 를 클릭 하 여 S66 및 **S57** **코드가** 포함 된 다른 두 개의 새 레코드를 MDS에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-163">Click **Publish** to publish the other two new records with **Codes S66** and **S57** to MDS.</span></span>  
  
30. <span data-ttu-id="be227-164">**게시 및 주석 달기** 대화 상자에서 **주석을**추가 하 고 **게시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-164">In the **Publish and Annotate** dialog box, add an **annotation**, and click **Publish**.</span></span>  
  
31. <span data-ttu-id="be227-165">**마스터 데이터 관리자 웹 응용 프로그램**으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-165">Switch to the **Master Data Manager Web application**.</span></span>  
  
32. <span data-ttu-id="be227-166">홈 페이지에서 **모델**에 대해 **Suppliers** 를 선택 했는지 확인 하 고 **탐색기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="be227-166">On the home page, ensure that **Suppliers** is selected for the **Model**, and click **Explorer**.</span></span> <span data-ttu-id="be227-167">**탐색기** 가 이미 열려 있는 경우 인터넷 브라우저를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="be227-167">If you already have the **Explorer** open, refresh the internet browser.</span></span>  
  
33. <span data-ttu-id="be227-168">**코드** 를 기준으로 목록을 **정렬** 하 고 **S57** 및 **S66** 를 코드로 사용 하 여 레코드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-168">**Sort** the list by **Code** and look for records with **S57** and **S66** as codes.</span></span> <span data-ttu-id="be227-169">도구 모음의 **필터** 단추를 사용 하 여 목록에서 특정 레코드를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-169">You can also use the **Filter** button on the toolbar to search for a specific record in the list.</span></span>  
  
34. <span data-ttu-id="be227-170">이제 파일을 저장 하지 않고 **book1.xlsx-Microsoft Excel** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="be227-170">Now, close **Book1 - Microsoft Excel** window without saving the file.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="be227-171">다음 단계</span><span class="sxs-lookup"><span data-stu-id="be227-171">Next Step</span></span>  
 [<span data-ttu-id="be227-172">태스크 5: Excel에서 도메인 기반 특성 만들기</span><span class="sxs-lookup"><span data-stu-id="be227-172">Task 5: Creating a Domain-Based Attribute from Excel</span></span>](../../2014/tutorials/task-5-creating-a-domain-based-attribute-from-excel.md)  
  
  
