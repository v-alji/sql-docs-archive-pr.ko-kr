---
title: '작업 12: 기술 자료 검색 (기술 자료 검색) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2dee66f94f1df609701f92d591f2c31863702465
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731207"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a><span data-ttu-id="a47fa-102">태스크 12: 지식 검색(기술 자료 검색)</span><span class="sxs-lookup"><span data-stu-id="a47fa-102">Task 12: Discovering Knowledge (Knowledge Discovery)</span></span>
  <span data-ttu-id="a47fa-103">이 작업에서는 **공급자 ID** 및 **공급자 이름** 도메인에 대 한 **기술 자료 검색** 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-103">In this task, you perform the **Knowledge Discovery** activity on **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="a47fa-104">이 시나리오에서 기술 자료 검색 프로세스는 주로 이러한 두 도메인의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-104">In this scenario, the knowledge discovery process mainly imports values for these two domains.</span></span>  
  
 <span data-ttu-id="a47fa-105">이 자습서에서는 기술 자료 구축을 처음부터 새로 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-105">In this tutorial, you started building knowledge base from scratch.</span></span> <span data-ttu-id="a47fa-106">기술 자료 검색 작업을 수행하여 기술 자료 만들기를 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-106">You can also start creating a knowledge base by performing a knowledge discovery activity.</span></span> <span data-ttu-id="a47fa-107">기본 페이지에서 **기술 자료 만들기** 를 클릭 하면 DQS 클라이언트에서 작업에 대해 선택한 **도메인 관리** 작업이 있는 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-107">When you click **Create a Knowledge Base** in the main page, DQS client takes you to a page with **Domain Management** activity selected for the activity.</span></span> <span data-ttu-id="a47fa-108">**활동** 을 **기술 자료 검색** 으로 변경 하 고 다음 페이지에서 기술 자료 검색 프로세스의 일부로 도메인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-108">You can change the **activity** to **Knowledge Discovery** and then in the next page you can create domains as part of the knowledge discovery process.</span></span> <span data-ttu-id="a47fa-109">자세한 내용은 [기술 자료 검색 수행](https://msdn.microsoft.com/library/hh510398.aspx) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a47fa-109">See [Perform Knowledge Discovery](https://msdn.microsoft.com/library/hh510398.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="a47fa-110">DQS 클라이언트의 기본 페이지에 있는 **최근 기술** 자료 섹션에서 **Suppliers** 기술 자료 옆에 있는 **오른쪽 화살표** 를 클릭 하 고 **기술 자료 검색**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-110">In the main page of DQS Client, in the **Recent Knowledge Base** section, click **right-arrow** next to the **Suppliers** knowledge base and click **Knowledge Discovery**.</span></span> <span data-ttu-id="a47fa-111">또는 기술 자료 **열기**를 클릭 하 고 **기술 자료 목록**에서 **Suppliers** 를 선택한 후 **기술 자료 검색** 을 **작업** 으로 선택 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-111">Alternatively, you can click **Open Knowledge Base**, select **Suppliers** from the **list of knowledge bases**, select **Knowledge Discovery** as **activity** and click **Next**.</span></span>  
  
     <span data-ttu-id="a47fa-112">![주 페이지의 기술 자료 검색 메뉴](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "주 페이지의 기술 자료 검색 메뉴")</span><span class="sxs-lookup"><span data-stu-id="a47fa-112">![Knowledge Discovery Menu on Main Page](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Knowledge Discovery Menu on Main Page")</span></span>  
  
2.  <span data-ttu-id="a47fa-113">**데이터 원본**에 대해 **Excel 파일** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-113">Select **Excel File** for **Data Source**.</span></span>  
  
3.  <span data-ttu-id="a47fa-114">**찾아보기**를 클릭 하 고 **Suppliers.xls**찾아서 선택한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-114">Click **Browse**, navigate and select **Suppliers.xls**, and click **Open**.</span></span>  
  
4.  <span data-ttu-id="a47fa-115">검색할 **공급자를** **워크시트**에 대해 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-115">Select **Suppliers for Discovery** for **Worksheet**.</span></span>  
  
5.  <span data-ttu-id="a47fa-116">**매핑** 섹션에서 **드롭다운 목록을**사용 하 여 **Excel** 파일 **의 공급 업체 열을** 공급자 **ID** 도메인 **및 공급자 이름 열** 에 **Supplier Name** 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-116">In the **Mappings** section, map **SupplierID** column from the **Excel** file to the **Supplier ID** domain and **Supplier Name** column to the **Supplier Name** domain by using **drop-down lists**.</span></span> <span data-ttu-id="a47fa-117">Excel 파일에는 **공급자 ID** 및 **공급자 이름** 도메인에 대 한 샘플 데이터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-117">The Excel file has sample data for the **Supplier ID** and **Supplier Name** domains.</span></span> <span data-ttu-id="a47fa-118">검색 프로세스에서 값을 검색하려는 도메인을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-118">In the discovery process, you can select the domains for which you want to discover the values.</span></span> <span data-ttu-id="a47fa-119">이 페이지에서 도메인을 만들고 원본 열을 이러한 도메인에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-119">You can create domains on this page and then map the source columns to those domains.</span></span> <span data-ttu-id="a47fa-120">도메인 관리 작업 중에 도메인을 만들지 않고 기술 자료 검색 작업 중에 도메인을 만드는 것은 드문 일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-120">It is not uncommon to create domains during knowledge discovery activity instead of creating domains during domain management activity.</span></span>  
  
     <span data-ttu-id="a47fa-121">![검색 프로세스의 맵 페이지](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "검색 프로세스의 맵 페이지")</span><span class="sxs-lookup"><span data-stu-id="a47fa-121">![Map Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Map Page of Discovery Process")</span></span>  
  
6.  <span data-ttu-id="a47fa-122">**다음** 을 클릭 하 여 **검색** 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-122">Click **Next** to switch to the **Discover** page.</span></span>  
  
7.  <span data-ttu-id="a47fa-123">**검색 페이지에서** **시작** 을 클릭 하 여 검색 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-123">On the **Discover** page, click **Start** to start the discovery process.</span></span> <span data-ttu-id="a47fa-124">검색은 **Suppliers.xls** 파일의 공급자 **SupplierID** 이름 및 **공급자 이름** 열에 대해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-124">Discovery is performed on the columns **SupplierID** and **Supplier Name** in the **Suppliers.xls** file.</span></span> <span data-ttu-id="a47fa-125">**공급자 ID** 및 **공급자 이름** 도메인은 검색에서 가져온 정보로 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-125">The **Supplier ID** and **Supplier Name** domains should be populated with the knowledge drawn from the discovery.</span></span>  
  
     <span data-ttu-id="a47fa-126">![검색 프로세스의 검색 페이지](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "검색 프로세스의 검색 페이지")</span><span class="sxs-lookup"><span data-stu-id="a47fa-126">![Discover Page of Discovery Process](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Discover Page of Discovery Process")</span></span>  
  
8.  <span data-ttu-id="a47fa-127">분석이 완료 되 면 페이지 아래쪽의 **프로파일러 탭** 에서 **원본 통계** 를 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-127">After the analysis has completed, review the **Source Statistics** in the **Profiler tab** at the bottom of the page.</span></span> <span data-ttu-id="a47fa-128">총 20 개의 값 (**공급** 업체 및 **Excel 워크시트**의 **공급자 이름** 값)이 포함 된 10 개의 새 레코드가 검색 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-128">Notice that 10 new records with total 20 values (**SupplierID** and **Supplier Name** values from the **Excel worksheet**) were discovered.</span></span> <span data-ttu-id="a47fa-129">또한 새 값, 고유 값, 새로운 고유 값 및 올바른 값의 개수도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-129">You will also see how many of the values are new, unique, new and unique, and valid.</span></span> <span data-ttu-id="a47fa-130">오른쪽 목록 상자에서는 검색 프로세스에 포함된 각 도메인에 대해 보다 자세한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-130">In the list box to the right, you can see more details for each domain involved in the discovery process.</span></span> <span data-ttu-id="a47fa-131">Completeness 열에서 상태 표시줄 위로 마우스를 가져가면 원본의 열에 누락된 값이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-131">If you hover the mouse over the status bar in the Completeness column, you can see if there are any missing values in the columns in the source.</span></span>  
  
     <span data-ttu-id="a47fa-132">![기술 자료 검색 결과](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "기술 자료 검색 결과")</span><span class="sxs-lookup"><span data-stu-id="a47fa-132">![Knowledge Discovery Results](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Knowledge Discovery Results")</span></span>  
  
9. <span data-ttu-id="a47fa-133">**다음** 을 클릭 하 여 **도메인 값 관리** 페이지로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-133">Click **Next** to switch to the **Manage Domain Values** page.</span></span>  
  
10. <span data-ttu-id="a47fa-134">**도메인 값 관리** 페이지의 도메인 목록에서 **공급자 이름** 도메인을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-134">In the **Manage Domain Values** page, click **Supplier Name** domain from the list of domains.</span></span>  
  
11. <span data-ttu-id="a47fa-135">오른쪽 창에서 **Lazy Country Storex** (끝에 ' x ' 표시)를 마우스 오른쪽 단추로 클릭 하 고 **lazy country Store**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-135">In the right pane, right-click **Lazy Country Storex** (notice 'x' at the end), and select **Lazy Country Store**.</span></span> <span data-ttu-id="a47fa-136">DQS는 도메인에서 맞춤법 검사기를 실행한 후 이 변경을 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-136">DQS suggests this change after running the spell checker on the domain.</span></span> <span data-ttu-id="a47fa-137">기본적으로 도메인을 만들면 맞춤법 검사기가 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-137">By default, speller is enabled on the domains you create.</span></span>  
  
     <span data-ttu-id="a47fa-138">![올바른 공급자 이름 - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "올바른 공급자 이름 - Lazy Country Store")</span><span class="sxs-lookup"><span data-stu-id="a47fa-138">![Correct Supplier Name - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Correct Supplier Name - Lazy Country Store")</span></span>  
  
12. <span data-ttu-id="a47fa-139">도메인 값 목록에서 **Lazy Country Storex** 값이 수정으로 **lazy country store** 를 사용 하 여 오류 (빨간색 **X** 표시)로 설정 되어 있는지 확인 하 고 **lazy country store** 도 유효한 값으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-139">In the domain values list, confirm that the value **Lazy Country Storex** is set as an error (red **X** mark) with **Lazy Country Store** as the correction and also the **Lazy Country Store** is also added as a valid value.</span></span>  
  
     <span data-ttu-id="a47fa-140">![도메인 값 및 다음으로 수정 값](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "도메인 값 및 다음으로 수정 값")</span><span class="sxs-lookup"><span data-stu-id="a47fa-140">![Domain Value and Correct To Value](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domain Value and Correct To Value")</span></span>  
  
13. <span data-ttu-id="a47fa-141">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-141">Click **Finish**.</span></span>  
  
14. <span data-ttu-id="a47fa-142">**SQL Server Data Quality Services** 대화 상자에서 **게시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-142">On **SQL Server Data Quality Services** dialog box, click **Publish**.</span></span>  
  
15. <span data-ttu-id="a47fa-143">성공 메시지 상자에서 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-143">Click **OK** on the success message box.</span></span>  
  
     <span data-ttu-id="a47fa-144">이 자습서의 첫 번째 단원이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a47fa-144">You have completed the first lesson of the tutorial.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="a47fa-145">다음 단계</span><span class="sxs-lookup"><span data-stu-id="a47fa-145">Next Step</span></span>  
 [<span data-ttu-id="a47fa-146">2단원: 공급자 기술 자료를 사용하여 공급자 데이터 정리</span><span class="sxs-lookup"><span data-stu-id="a47fa-146">Lesson 2: Cleansing Supplier Data using the Suppliers Knowledge Base</span></span>](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
