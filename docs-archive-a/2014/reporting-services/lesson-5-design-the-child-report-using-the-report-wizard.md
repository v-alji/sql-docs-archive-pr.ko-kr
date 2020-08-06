---
title: '5단원: 보고서 마법사를 사용하여 하위 보고서 디자인 | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 19a3f927-ea97-4f40-a5f8-cd5f2598e4da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f188a914fc2a2bb8370843191a31474a54c02aa8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647510"
---
# <a name="lesson-5-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="846bf-102">5단원: 보고서 마법사를 사용하여 자식 보고서 디자인</span><span class="sxs-lookup"><span data-stu-id="846bf-102">Lesson 5: Design the Child Report using the Report Wizard</span></span>
  <span data-ttu-id="846bf-103">자식 보고서에 대한 데이터 테이블 및 데이터 연결을 만든 후에는 보고서 디자이너의 보고서 마법사를 사용하여 자식 보고서를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-103">After you create a data connection and data table for the child report, your next step is to design the child report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="846bf-104">보고서 디자이너에 대한 자세한 내용은 [보고서 디자이너로 보고서 디자인&#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="846bf-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-child-report-using-the-report-wizard"></a><span data-ttu-id="846bf-105">보고서 마법사를 사용하여 자식 보고서를 디자인하려면</span><span class="sxs-lookup"><span data-stu-id="846bf-105">To design the child report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="846bf-106">**솔루션 탐색기**에서 최상위 웹 사이트가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="846bf-107">웹 사이트를 마우스 오른쪽 단추로 클릭하고 **새 항목 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="846bf-108">**새 항목 추가** 대화 상자에서 **보고서 마법사**를 클릭하고 보고서 파일의 이름을 입력한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-108">In the **Add New Item** dialog box, click **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="846bf-109">그러면 보고서 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="846bf-110">**데이터 세트 속성** 페이지의 **데이터 원본** 상자에서 **DataSet2**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-110">In the **Dataset Properties** page, in the **Data source** box, click **DataSet2**.</span></span>  
  
     <span data-ttu-id="846bf-111">**사용 가능한 데이터 세트** 상자가 만들어진 DataTable로 자동 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-111">The **Available datasets** box is automatically updated with the DataTable you created.</span></span>  
  
5.  <span data-ttu-id="846bf-112">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="846bf-113">**필드 정렬** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="846bf-114">**ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**및 **StockedQty** 를 **사용 가능한 필드** 에서 **값** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-114">Drag **ProductID**, **PurchaseOrderID**, **PurchaseOrderDetailID**, **OrderQty**, **ReceivedQty**, **RejectedQty**, and **StockedQty** from **Available Fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="846bf-115">**Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)** 및 **Sum(StockedQty)** 옆에 있는 화살표를 클릭하고 **합계** 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-115">Click the arrow next to **Sum(ProductID)**, **Sum(PurchaseOrderID)**, **Sum(PurchaseOrderDetailID)**, **Sum(OrderQty)**, **Sum(ReceivedQty)**, **Sum(RejectedQty)**, and **Sum(StockedQty)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="846bf-116">**다음** 을 두 번 클릭한 다음 **마침** 을 클릭하여 **보고서 마법사**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="846bf-117">이제 .rdlc 파일을 만드는 작업을 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="846bf-118">보고서 디자이너에서 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-118">The file opens in Report Designer.</span></span> <span data-ttu-id="846bf-119">디자인한 테이블릭스가 이제 디자인 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="846bf-120">.rdlc 파일이 열려 있는 상태에서 다음을 수행하여 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-120">With the .rdlc file open, add a parameter by doing the following:</span></span>  
  
    1.  <span data-ttu-id="846bf-121">**보고서 데이터** 창의 **매개 변수** 를 클릭한 다음 **매개 변수 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-121">Click **Parameters** in the **Report Data** pane, and then click **Add Parameters**.</span></span>  
  
    2.  <span data-ttu-id="846bf-122">**이름** 상자에 **productid** 를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-122">Enter **productid** in the **Name** box.</span></span>  
  
    3.  <span data-ttu-id="846bf-123">**데이터 형식** 목록 상자에서 **정수** 를 선택했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-123">Confirm that **Integer** is selected in the **Data Type** list box.</span></span>  
  
    4.  <span data-ttu-id="846bf-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-124">Click **OK**.</span></span>  
  
9. <span data-ttu-id="846bf-125">.rdlc 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-125">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="846bf-126">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="846bf-126">Next Task</span></span>  
 <span data-ttu-id="846bf-127">보고서 마법사를 사용하여 성공적으로 자식 보고서를 디자인했습니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-127">You have successfully designed the child report by using the Report Wizard.</span></span> <span data-ttu-id="846bf-128">이제 웹 사이트 애플리케이션에 ReportViewer 컨트롤을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="846bf-128">Next, you will add a ReportViewer control to the website application.</span></span>  
  
  
