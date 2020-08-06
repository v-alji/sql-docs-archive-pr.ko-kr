---
title: '작업 2: Excel용 MDS 추가 기능을 사용 하 여 MDS에 공급자 데이터 업로드 Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 598deb57-e0cc-4e0a-aeb1-94432c094c67
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 16c5fa9db81649b30c12fae4d2e57afa8bf094e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639160"
---
# <a name="task-2-uploading-supplier-data-to-mds-using-mds-add-in-for-excel"></a><span data-ttu-id="ce317-102">태스크 2: Excel용 MDS 추가 기능을 사용하여 MDS에 공급자 데이터 업로드</span><span class="sxs-lookup"><span data-stu-id="ce317-102">Task 2: Uploading Supplier Data to MDS using MDS Add-in for Excel</span></span>
  <span data-ttu-id="ce317-103">이 작업에서는 **Excel용 MDS 추가 기능**를 사용 하 여 정리 된 데이터와 공급자 데이터를 **MDS** 에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-103">In this task, you publish the cleansed and supplier data to **MDS** using the **MDS Add-in for Excel**.</span></span> <span data-ttu-id="ce317-104">이전 단원에서 만든 **Suppliers** 모델에 **공급자** 라는 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-104">You create an entity named **Supplier** in the **Suppliers** model you created in the previous lesson.</span></span> <span data-ttu-id="ce317-105">이 엔터티는 Excel 파일의 각 열에 대한 특성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-105">The entity will have an attribute for each column in the Excel file.</span></span> <span data-ttu-id="ce317-106">공급자 엔터티의 Code 및 Name 특성은 Excel의 공급자 이름 및 **공급자** **이름** 열에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-106">The Code and Name attributes of the Supplier entity correspond to the **SupplierID** and **Supplier Name** columns in Excel.</span></span>  
  
1.  <span data-ttu-id="ce317-107">**Excel**에서 **정리 및 일치 Suppliers.xls** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-107">Open **Cleansed and Matched Suppliers.xls** in **Excel**.</span></span>  
  
2.  <span data-ttu-id="ce317-108">**Ctrl + A** 를 눌러 전체 데이터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-108">Press **CTRL+A** to select entire data.</span></span> <span data-ttu-id="ce317-109">스프레드시트에서 전체 데이터를 선택 하는 것이 **중요** 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-109">It is **important** that you select the entire data in the spreadsheet.</span></span>  
  
3.  <span data-ttu-id="ce317-110">메뉴 모음에서 **마스터 데이터** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-110">Click **Master Data** on the menu bar.</span></span>  
  
4.  <span data-ttu-id="ce317-111">리본에서 **엔터티 만들기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-111">Click **Create Entity** button on the ribbon.</span></span>  
  
     <span data-ttu-id="ce317-112">![Excel - 마스터 데이터 탭 - 엔터티 만들기 단추](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - 마스터 데이터 탭 - 엔터티 만들기 단추")</span><span class="sxs-lookup"><span data-stu-id="ce317-112">![Excel - Master Data Tab - Create Entity Button](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-01.jpg "Excel - Master Data Tab - Create Entity Button")</span></span>  
  
5.  <span data-ttu-id="ce317-113">**연결 관리** 대화 상자에서 **기존 연결** 아래에 **로컬 MDS 서버**에 대한 연결이 표시되지 않으면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-113">In **Manage Connections** dialog box, if you do not see the connection to **local MDS server** under **Existing connections**, do the following:</span></span>  
  
    1.  <span data-ttu-id="ce317-114">**새 연결 만들기**를 선택하고 **새로 만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-114">Select **Create a new connection**, and click **New** button.</span></span>  
  
    2.  <span data-ttu-id="ce317-115">**새 연결 추가** 대화 상자에서 **설명** 에 **Local MDS server** 를 입력 하 고/localhost/MDS **서버 주소**에는 \*\*http: \/ \*\* 를 입력 한 다음 **확인** 을 클릭 하 여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-115">In the **Add New Connection** dialog box, type **Local MDS Server** for **Description** and **http:\//localhost/MDS** for **MDS server address**, and click **OK** to close the dialog box.</span></span>  
  
6.  <span data-ttu-id="ce317-116">**연결 관리** 대화 상자에서 **로컬 MDS 서버** ()를 선택 하 고 `http://localhost/MDS` **테스트** 를 클릭 하 여 연결을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-116">In **Manage Connections** dialog box, select **Local MDS Server** (`http://localhost/MDS`), click **Test** to test the connection.</span></span> <span data-ttu-id="ce317-117">메시지 상자에서 **확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-117">Click **OK** on the message box.</span></span>  
  
7.  <span data-ttu-id="ce317-118">**연결** 을 클릭 하 여 MDS 서버에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-118">Click **Connect** to connect to the MDS server.</span></span>  
  
8.  <span data-ttu-id="ce317-119">**엔터티 만들기** 대화 상자에서 **모델**에 대해 **Suppliers** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-119">In the **Create Entity** dialog box, select **Suppliers** for the **Model**.</span></span>  
  
9. <span data-ttu-id="ce317-120">**버전**에 대해 **VERSION_1** 가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-120">Ensure that **VERSION_1** is selected for **Version**.</span></span>  
  
10. <span data-ttu-id="ce317-121">**새 엔터티 이름**에 대해 **공급자** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-121">Enter **Supplier** for **New entity name**.</span></span>  
  
11. <span data-ttu-id="ce317-122">**고유 식별자 필드를 포함 하는 열** 에 대해 **공급자** 를 선택 합니다 (코드를 자동으로 생성할 수도 있음).</span><span class="sxs-lookup"><span data-stu-id="ce317-122">Select **SupplierID** for **the column that contains a unique identifier** field (you can also generate a code automatically).</span></span> <span data-ttu-id="ce317-123">기본적으로 **Excel** 의 공급자 **열을** **공급자** 엔터티의 **Code** 특성에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-123">You are essentially mapping the **SupplierID** column in **Excel** to the **Code** attribute of **Supplier** entity.</span></span>  
  
12. <span data-ttu-id="ce317-124">이름 필드를 **포함 하는 열** 에 대해 **공급자 이름** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-124">Select **Supplier Name** for **the column that contains names** field.</span></span> <span data-ttu-id="ce317-125">기본적으로 **Excel** 의 **공급자 이름** 열을 **공급자** 엔터티의 **name** 특성에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-125">You are essentially mapping the **Supplier Name** column in **Excel** to the **Name** attribute of the **Supplier** entity.</span></span> <span data-ttu-id="ce317-126">**코드** 및 **이름** 특성은 MDS의 엔터티에 대 한 필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-126">The **Code** and **Name** attributes are mandatory attributes for an entity in MDS.</span></span>  
  
     <span data-ttu-id="ce317-127">![엔터티 만들기 대화 상자](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "엔터티 만들기 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="ce317-127">![Create Entity Dialog Box](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-02.jpg "Create Entity Dialog Box")</span></span>  
  
13. <span data-ttu-id="ce317-128">**확인** 을 클릭 하 여 MDS에서 엔터티를 만들고, 엔터티에 마스터 데이터를 게시 하 고, **엔터티 만들기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-128">Click **OK** to create the entity on MDS, publish the master data to the entity, and close **Create Entity** dialog box.</span></span>  
  
14. <span data-ttu-id="ce317-129">이제 엔터티의 이름인 **공급자**라는 새 시트가 표시 됩니다 .이 시트에는 Excel 스프레드시트에 추가 되 고 워크시트의 맨 위에는 해당 워크시트가 MDS 서버에 연결 되어 있음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-129">Now, you should see a new sheet titled **Supplier**, which is the name of the entity, added to your Excel spreadsheet and at the top of the worksheet you should see that the worksheet is connected to the MDS server.</span></span> <span data-ttu-id="ce317-130">원본 워크시트 ( **Sheet1**제목)는 여전히 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-130">Notice that the original worksheet (titled **Sheet1**) still exists.</span></span>  
  
     <span data-ttu-id="ce317-131">![Excel - 공급자 및 Sheet1 탭](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - 공급자 및 Sheet1 탭")</span><span class="sxs-lookup"><span data-stu-id="ce317-131">![Excel - Supplier and Sheet1 Tabs](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-03.jpg "Excel - Supplier and Sheet1 Tabs")</span></span>  
  
     <span data-ttu-id="ce317-132">![Excel - MDS 연결 정보 표시](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - MDS 연결 정보 표시")</span><span class="sxs-lookup"><span data-stu-id="ce317-132">![Excel - Showing MDS Connection Details](../../2014/tutorials/media/et-ulingsdtomdsusingmdsaddinforexcel-04.jpg "Excel - Showing MDS Connection Details")</span></span>  
  
15. <span data-ttu-id="ce317-133">**Excel** 을 열어 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ce317-133">Keep **Excel** open.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="ce317-134">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ce317-134">Next Task</span></span>  
 [<span data-ttu-id="ce317-135">태스크 3: 마스터 데이터 관리자에서 데이터 확인</span><span class="sxs-lookup"><span data-stu-id="ce317-135">Task 3: Verifying the Data in Master Data Manager</span></span>](../../2014/tutorials/task-3-verifying-the-data-in-master-data-manager.md)  
  
  
