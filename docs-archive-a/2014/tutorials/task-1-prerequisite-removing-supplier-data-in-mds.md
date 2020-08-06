---
title: '작업 1 (필수 구성 요소): MDS에서 공급자 데이터 제거 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e78dc5ff04f95d42cf440e3f80b1b349e0315a69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653695"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a><span data-ttu-id="f9ac6-102">태스크 1(필수 구성 요소): MDS에서 공급자 데이터 제거</span><span class="sxs-lookup"><span data-stu-id="f9ac6-102">Task 1 (Prerequisite): Removing Supplier Data in MDS</span></span>
  <span data-ttu-id="f9ac6-103">이 작업에서는 MDS에 저장된 공급자 데이터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-103">In this task, you remove the supplier data stored in MDS.</span></span> <span data-ttu-id="f9ac6-104">이전 단원에서는 **MDS Excel 추가 기능** 을 사용하여 데이터를 수동으로 업로드했습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-104">You uploaded the data manually using **MDS Excel Add-in** in the previous lesson.</span></span> <span data-ttu-id="f9ac6-105">이 단원에서 만드는 SSIS 패키지는 데이터를 MDS에 자동으로 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-105">The SSIS package you create in this lesson will automatically upload the data to MDS for you.</span></span> <span data-ttu-id="f9ac6-106">따라서 SSIS 패키지를 테스트하기 전에 MDS에서 공급자 데이터를 제거하고, 파생 계층을 제거하고, 공급자 및 상태 엔터티를 제거하고 포함된 데이터 없이 공급자 엔터티를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-106">Therefore, before testing the SSIS package, you need to remove the supplier data from MDS, remove the derived hierarchy, remove supplier and state entities, and create the supplier entity with no data.</span></span>  
  
1.  <span data-ttu-id="f9ac6-107">**Master Data Manager** `http://localhost/MDS` 또는 MDS를 구성할 때 지정한 웹 사이트 및 응용 프로그램으로 이동 하 여 마스터 데이터 관리자를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-107">Launch **Master Data Manager** by navigating to `http://localhost/MDS` or the website and application you specified when configuring MDS.</span></span> <span data-ttu-id="f9ac6-108">**마스터 데이터 관리자** 가 열려 있으면 상단에서 **SQL Server 2012 Master Data Services** 를 클릭하여 **홈 페이지**로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-108">If you kept the **Master Data Manager** open, click **SQL Server 2012 Master Data Services** at the top to switch to the **home page**.</span></span>  
  
2.  <span data-ttu-id="f9ac6-109">**관리 작업** 섹션에서 **시스템 관리** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-109">Click **System Administration** in the **Administrative Tasks** section.</span></span>  
  
3.  <span data-ttu-id="f9ac6-110">메뉴의 **관리** 위로 마우스를 가져가고 **파생 계층**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-110">Hover the mouse over **Manage** on the menu and click **Derived Hierarchies**.</span></span> <span data-ttu-id="f9ac6-111">**Suppliers** 모델에서 엔터티를 삭제하려면 먼저 **SuppliersInState** 파생 계층을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-111">You need to delete the derived hierarchy **SuppliersInState** before deleting the entities in the **Suppliers** model.</span></span>  
  
4.  <span data-ttu-id="f9ac6-112">**파생 계층** 목록에서 **SuppliersInState** 를 선택하고 도구 모음에서 **X(삭제)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-112">Select **SuppliersInState** from the **Derived Hierarchy** list and click **X (Delete)** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="f9ac6-113">**확인** 을 클릭하여 삭제를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-113">Click **OK** to confirm deletion.</span></span>  
  
6.  <span data-ttu-id="f9ac6-114">메뉴에서 **관리** 위로 마우스를 가져가고 **엔터티**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-114">Hover the mouse over **Manage** on the menu and click **Entities**.</span></span>  
  
7.  <span data-ttu-id="f9ac6-115">**Supplier** 를 클릭하고 도구 모음에서 **삭제(X)** 단추를 클릭하여 엔터티를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-115">Click **Supplier** and click **Delete (X)** button on toolbar to delete the entity.</span></span> <span data-ttu-id="f9ac6-116">메시지 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-116">Click **OK** on message boxes.</span></span>  
  
8.  <span data-ttu-id="f9ac6-117">이전 단계를 반복하여 **State** 엔터티를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-117">Repeat the previous step to delete **State** entity.</span></span>  
  
9. <span data-ttu-id="f9ac6-118">**마스터 데이터 관리자**를 닫지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-118">Don't close **Master Data Manager**.</span></span>  
  
10. <span data-ttu-id="f9ac6-119">**Cleansed and Matched Suppliers.xls** 파일이 열려 있는 Excel 창으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-119">Switch to the Excel window that has **Cleansed and Matched Suppliers.xls** file open.</span></span> <span data-ttu-id="f9ac6-120">하단에서 **Sheet1** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-120">Switch to the **Sheet1** tab at the bottom.</span></span>  
  
11. <span data-ttu-id="f9ac6-121">**첫 번째 머리글 행**만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-121">Select only the **first row with headers**.</span></span> <span data-ttu-id="f9ac6-122">다른 행은 선택 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-122">Don't select any other row.</span></span> <span data-ttu-id="f9ac6-123">Excel 열을 기반으로 엔터티를 만들려고 하지만 데이터를 업로드 하지 않으려는 경우</span><span class="sxs-lookup"><span data-stu-id="f9ac6-123">You want to create the entities based on the Excel columns but don't want to upload any data.</span></span> <span data-ttu-id="f9ac6-124">따라서 첫 번째 머리글 행만 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-124">Therefore you select only the first row with the headers.</span></span>  
  
12. <span data-ttu-id="f9ac6-125">메뉴 모음에서 **마스터 데이터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-125">Click **Master Data** on the menu bar.</span></span>  
  
13. <span data-ttu-id="f9ac6-126">리본에서 **엔터티 만들기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-126">Click **Create Entity** from the ribbon.</span></span>  
  
14. <span data-ttu-id="f9ac6-127">**연결 관리** 대화 상자에서 **기존 연결** 아래에 **로컬 MDS 서버**에 대한 연결이 표시되지 않으면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-127">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="f9ac6-128">**새 연결 만들기**를 선택하고 **새로 만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-128">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="f9ac6-129">새 연결 추가 대화 상자에서 **설명** 에 **Local MDS server** 를 입력 하 고/localhost/MDS **서버 주소**에는 \*\*Http: \/ \*\* 를 입력 한 다음 **확인** 을 클릭 하 여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-129">In the Add New Connection dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
15. <span data-ttu-id="f9ac6-130">**연결 관리** 대화 상자에서 **로컬 MDS 서버** ()를 선택 하 고 `http://localhost/MDS` **테스트** 를 클릭 하 여 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-130">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="f9ac6-131">메시지 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-131">Click **OK** on the message box.</span></span>  
  
16. <span data-ttu-id="f9ac6-132">**연결** 을 클릭하여 MDS 서버에 대한 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-132">Click **Connect** to make a connection to the MDS server.</span></span>  
  
17. <span data-ttu-id="f9ac6-133">**엔터티 만들기** 대화 상자에서 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-133">In the **Create Entity** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="f9ac6-134">**범위** 가 **$1:$1**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-134">Confirm that **Range** is set to **$1:$1**.</span></span>  
  
    2.  <span data-ttu-id="f9ac6-135">**모델** 에 대해 **Suppliers**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-135">Select **Suppliers** for **Model**.</span></span>  
  
    3.  <span data-ttu-id="f9ac6-136">**버전** 에 대해 **VERSION_1**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-136">Select **VERSION_1** for **Version**.</span></span>  
  
    4.  <span data-ttu-id="f9ac6-137">**새 엔터티 이름** 에 **Supplier**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-137">Type **Supplier** for **New entity name**.</span></span>  
  
    5.  <span data-ttu-id="f9ac6-138">**코드** 에 대해 **SupplierID**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-138">Select **SupplierID** for **Code**.</span></span>  
  
    6.  <span data-ttu-id="f9ac6-139">**이름** 에 대해 **Supplier Name**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-139">Select **Supplier Name** for **Name**.</span></span>  
  
    7.  <span data-ttu-id="f9ac6-140">**확인** 을 클릭하여 엔터티를 만들고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-140">Click **OK** to create the entity and close the dialog box.</span></span>  
  
18. <span data-ttu-id="f9ac6-141">**Excel** 을 닫고 파일을 **저장하지는 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="f9ac6-141">Close **Excel** and **do not save** the file.</span></span>  
  
19. <span data-ttu-id="f9ac6-142">**마스터 데이터 관리자**에서 인터넷 브라우저를 새로 고치고 **Supplier** 엔터티가 목록에 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-142">In **Master Data Manager**, refresh the internet browser and confirm that **Supplier** entity is displayed in the list.</span></span>  
  
20. <span data-ttu-id="f9ac6-143">상단에서 **SQL Server 2012 Master Data Services** 를 클릭하여 **홈 페이지** 로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-143">Switch to the **home page** by clicking **SQL Server 2012 Master Data Services** at the top.</span></span>  
  
21. <span data-ttu-id="f9ac6-144">**모델** 에 대해 **Suppliers** 모델이 선택되었고 **버전** 으로 **VERSION_1**이 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-144">Confirm that **Suppliers** model is selected for **Model** and **VERSION_1** is selected for **Version**.</span></span>  
  
22. <span data-ttu-id="f9ac6-145">**탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-145">Click **Explorer**.</span></span> <span data-ttu-id="f9ac6-146">모든 특성이 포함된 **Supplier** 엔터티가 **값 없음**으로 만들어졌는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f9ac6-146">Notice that the **Supplier** entity with all the attributes is created with **no values**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="f9ac6-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f9ac6-147">Next Step</span></span>  
 [<span data-ttu-id="f9ac6-148">작업 2 &#40;선택적&#41;: 마스터 데이터 관리자를 사용 하 여 MDS 구독 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="f9ac6-148">Task 2 &#40;Optional&#41;: Creating a MDS Subscription View using Master Data Manager</span></span>](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
