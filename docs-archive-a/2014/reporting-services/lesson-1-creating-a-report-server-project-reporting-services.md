---
title: '1단원: 보고서 서버 프로젝트 만들기(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a708e5114344e87edd620ef58bc50594a9b9ef8d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742915"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a><span data-ttu-id="58ac0-102">1단원: 보고서 서버 프로젝트 만들기(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="58ac0-102">Lesson 1: Creating a Report Server Project (Reporting Services)</span></span>
  <span data-ttu-id="58ac0-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에서 보고서를 만들려면 먼저 보고서 정의 파일(.rdl) 및 보고서에 필요한 다른 리소스 파일을 저장할 보고서 서버 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-103">To create a report in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you must first create a report server project where you will save your report definition (.rdl) file and any other resource files that you need for your report.</span></span> <span data-ttu-id="58ac0-104">그런 다음 실제 보고서 정의 파일을 만들고 보고서에 대한 데이터 원본, 데이터 세트 및 보고서 레이아웃을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-104">Then you will create the actual report definition file, define a data source for your report, define a dataset, and define the report layout.</span></span> <span data-ttu-id="58ac0-105">보고서를 실행하면 실제 데이터가 검색되어 레이아웃과 결합된 후 해당 보고서를 내보내고 인쇄하고 저장할 수 있는 화면에 렌더링됩니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-105">When you run the report, the actual data is retrieved and combined with the layout, and then rendered on your screen, from where you can export it, print it, or save it.</span></span>  
  
 <span data-ttu-id="58ac0-106">이 단원에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 보고서 서버 프로젝트를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-106">In this lesson, you will learn how to create a report server project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="58ac0-107">보고서 서버 프로젝트는 보고서 서버에서 실행되는 보고서를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-107">A report server project is used to create reports that run on a report server.</span></span>  
  
### <a name="to-create-a-report-server-project"></a><span data-ttu-id="58ac0-108">보고서 서버 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="58ac0-108">To create a report server project</span></span>  
  
1.  <span data-ttu-id="58ac0-109">**시작**을 클릭 하 고 **모든 프로그램**,을 차례로 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] 다음 **SQL Server Data Tools**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-109">Click **Start**, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], and then click **SQL Server Data Tools**.</span></span> <span data-ttu-id="58ac0-110">이를 처음 열면 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 기본 환경 설정의 **비즈니스 인텔리전스 설정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-110">If this is the first time you have opened [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], click **Business Intelligence Settings** for the default environment settings.</span></span>  
  
2.  <span data-ttu-id="58ac0-111">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="58ac0-112">**설치된 템플릿** 목록에서 **비즈니스 인텔리전스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-112">In the **Installed Templates** list, click **Business Intelligence**.</span></span>  
  
4.  <span data-ttu-id="58ac0-113">**보고서 서버 프로젝트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-113">Click **Report Server Project**.</span></span>  
  
5.  <span data-ttu-id="58ac0-114">**이름**에 **Tutorial**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-114">In **Name**, type **Tutorial**.</span></span>  
  
6.  <span data-ttu-id="58ac0-115">**확인**을 클릭하여 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-115">Click **OK** to create the project.</span></span>  
  
     <span data-ttu-id="58ac0-116">솔루션 탐색기에 Tutorial 프로젝트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-116">The Tutorial project is displayed in Solution Explorer.</span></span>  
  
### <a name="to-create-a-new-report-definition-file"></a><span data-ttu-id="58ac0-117">새 보고서 정의 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="58ac0-117">To create a new report definition file</span></span>  
  
1.  <span data-ttu-id="58ac0-118">솔루션 탐색기에서 **보고서**를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 **새 항목**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-118">In Solution Explorer, right-click **Reports**, point to **Add**, and click **New Item**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="58ac0-119">**솔루션 탐색기** 창이 표시되지 않으면 **보기** 메뉴에서 **솔루션 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-119">If the **Solution Explorer** window is not visible, from the **View** menu, click **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="58ac0-120">**새 항목 추가** 대화 상자의 **템플릿**에서 **보고서**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-120">In the **Add New Item** dialog box, under **Templates**, click **Report**.</span></span>  
  
3.  <span data-ttu-id="58ac0-121">**이름**에 **Sales Orders.rdl** 을 입력한 후 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-121">In **Name**, type **Sales Orders.rdl** and then click **Add**.</span></span>  
  
     <span data-ttu-id="58ac0-122">보고서 디자이너가 열리고 새 .rdl 파일이 디자인 뷰에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-122">Report Designer opens and displays the new .rdl file in Design view.</span></span>  
  
 <span data-ttu-id="58ac0-123">보고서 디자이너는 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 에서 실행되는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]구성 요소로,</span><span class="sxs-lookup"><span data-stu-id="58ac0-123">Report Designer is a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] component that runs in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="58ac0-124">두 개의 뷰, 즉 **디자인** 및 **미리 보기**뷰가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-124">It has two views: **Design** and **Preview**.</span></span> <span data-ttu-id="58ac0-125">뷰를 변경하려면 각 탭을 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-125">Click each tab to change views.</span></span>  
  
 <span data-ttu-id="58ac0-126">**보고서 데이터** 창에서 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-126">You define your data in the **Report Data** pane.</span></span> <span data-ttu-id="58ac0-127">**디자인** 뷰에서는 보고서 레이아웃을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-127">You define your report layout in **Design** view.</span></span> <span data-ttu-id="58ac0-128">보고서를 실행하고 **미리 보기** 뷰에서 보고서의 모양을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-128">You can run the report and see what it looks like in **Preview** view.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="58ac0-129">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="58ac0-129">Next Task</span></span>  
 <span data-ttu-id="58ac0-130">"Tutorial" 보고서 프로젝트를 만들고 보고서 정의 파일(.rdl)을 보고서 프로젝트에 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-130">You have successfully created a report project called "Tutorial" and added a report definition (.rdl) file to the report project.</span></span> <span data-ttu-id="58ac0-131">다음 단원에서는 보고서에 사용할 데이터 원본을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="58ac0-131">Next, you will specify a data source to use for the report.</span></span> <span data-ttu-id="58ac0-132">[2단원: 연결 정보 지정&#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58ac0-132">See [Lesson 2: Specifying Connection Information &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ac0-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58ac0-133">See Also</span></span>  
 [<span data-ttu-id="58ac0-134">기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="58ac0-134">Create a Basic Table Report &#40;SSRS Tutorial&#41;</span></span>](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
