---
title: '6단원: 애플리케이션에 ReportViewer 컨트롤 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bb04008fa47801f0500de711592a3cec45ca3dd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660344"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="ac752-102">6단원: 애플리케이션에 ReportViewer 컨트롤 추가</span><span class="sxs-lookup"><span data-stu-id="ac752-102">Lesson 6: Add a ReportViewer Control to the Application</span></span>
  <span data-ttu-id="ac752-103">보고서 마법사를 사용하여 자식 보고서를 디자인한 후에는 웹 사이트 애플리케이션에 ReportViewer 컨트롤을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-103">After you design the child report by using the Report Wizard, your next step is to add a ReportViewer control to the website application.</span></span>  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a><span data-ttu-id="ac752-104">애플리케이션에 ReportViewer 컨트롤을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ac752-104">To add a ReportViewer control to the application</span></span>  
  
1.  <span data-ttu-id="ac752-105">**솔루션 탐색기**에서 **Default.aspx**를 마우스 오른쪽 단추로 클릭한 다음 **뷰 디자이너**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-105">In **Solution Explorer**, right-click **Default.aspx**, and then click **View Designer**.</span></span>  
  
2.  <span data-ttu-id="ac752-106">**도구 모음** 창의 **AJAX 확장** 그룹에서 **ScriptManager** 컨트롤을 디자인 화면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-106">From the **AJAX Extensions** group in the **Toolbox** window, drag a **ScriptManager** control to the design surface.</span></span>  
  
3.  <span data-ttu-id="ac752-107">**보고** 그룹에서 **ReportViewer** 컨트롤을 **ScriptManager** 컨트롤 아래의 디자인 화면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-107">From the **Reporting** group, drag a **ReportViewer** control to the design surface below the **ScriptManager** control.</span></span>  
  
4.  <span data-ttu-id="ac752-108">**ReportViewer** 컨트롤의 오른쪽 위에 있는 화살표를 클릭하여 **ReportViewer 태스크** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-108">Open the **ReportViewer Tasks** window by clicking the arrow in the top right-hand corner of the **ReportViewer** control.</span></span>  
  
5.  <span data-ttu-id="ac752-109">**보고서 선택** 상자에서 만든 부모 보고서를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-109">In the **Choose Report** box, select Parent report you created.</span></span>  
  
     <span data-ttu-id="ac752-110">보고서를 선택하면 보고서에 사용된 데이터 원본의 인스턴스가 자동으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-110">When you select a report, instances of data sources used in the report are created automatically.</span></span> <span data-ttu-id="ac752-111">각 DataTable 및 해당 [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) 컨테이너를 인스턴스화하는 코드가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-111">Code is generated to instantiate each DataTable (and its [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) container).</span></span> <span data-ttu-id="ac752-112">보고서에 사용된 각 데이터 원본에 해당하는 [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) 컨트롤이 디자인 화면에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-112">An [ObjectDataSource](https://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx) control is added to the design surface, corresponding to each data source used in the report.</span></span> <span data-ttu-id="ac752-113">이 데이터 원본 컨트롤은 자동으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-113">This data source control is configured automatically.</span></span>  
  
     <span data-ttu-id="ac752-114">Microsoft Visual Studio 2012를 사용 하는 경우 ObjectDataSource 컨트롤이 프로젝트 네임 스페이스와 완전히 정규화 된 DataSet1에 바인딩되어 있는지 확인 합니다 ( **비즈니스 개체 선택** 드롭다운 목록 상자에 정규화 된 이름이 나열 된 경우 (예: projectnamespace. DataSet1TableAdapters tableadapter).</span><span class="sxs-lookup"><span data-stu-id="ac752-114">If you're using Microsoft Visual Studio 2012, make sure that the ObjectDataSource control is bound with DataSet1 that is fully qualified with the project namespace, if the fully qualified name is listed in the **Choose your business object** drop-down list box (for example, Projectnamespace.DataSet1TableAdapters.ProductTableAdapter).</span></span> <span data-ttu-id="ac752-115">ObjectDataSource를 마우스 오른쪽 단추로 클릭한 다음 **데이터 원본 구성**을 클릭하여 목록 상자에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-115">You access the list box by right-clicking ObjectDataSource, and then clicking **Configure Data Source**.</span></span>  
  
6.  <span data-ttu-id="ac752-116">빌드 메뉴에서 웹 사이트 빌드를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-116">On the Build menu, click Build website.</span></span>  
  
     <span data-ttu-id="ac752-117">보고서가 컴파일되고 보고서 식의 구문 오류와 같은 오류가 모두 **오류 목록** 영역에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-117">The report is compiled and any errors such as a syntax error in a report expression appear in the **Error List** area.</span></span> <span data-ttu-id="ac752-118">Visual Studio 창의 아래쪽에 있는 **오류 목록** 을 클릭하여 **오류 목록** 영역을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-118">Click **Error List** at the bottom of the Visual Studio window to display the **Error List** area.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="ac752-119">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ac752-119">Next Task</span></span>  
 <span data-ttu-id="ac752-120">웹 사이트 애플리케이션에 ReportViewer 컨트롤을 성공적으로 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-120">You have successfully added a ReportViewer control to the website application.</span></span> <span data-ttu-id="ac752-121">이제 부모 보고서에 드릴스루 동작을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ac752-121">Next, you will add a drillthrough action on the parent report.</span></span>  
  
  
