---
title: '3단원: 보고서 마법사를 사용하여 부모 보고서 디자인 | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3cb6a0972a2bb63e82e80c02b3ce90912ba01c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647516"
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="f8dac-102">3단원: 보고서 마법사를 사용하여 부모 보고서 디자인</span><span class="sxs-lookup"><span data-stu-id="f8dac-102">Lesson 3: Design the Parent Report using the Report Wizard</span></span>
  <span data-ttu-id="f8dac-103">부모 보고서에 대한 데이터 테이블 및 데이터 연결을 만든 후에는 보고서 디자이너의 보고서 마법사를 사용하여 부모 보고서를 디자인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-103">After you create a data connection and a data table for the parent report, your next step is to design the parent report using the Report Wizard in Report Designer.</span></span> <span data-ttu-id="f8dac-104">보고서 디자이너에 대한 자세한 내용은 [보고서 디자이너로 보고서 디자인&#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8dac-104">For more information about Report Designer, see [Design Reports with Report Designer &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md).</span></span>  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a><span data-ttu-id="f8dac-105">보고서 마법사를 사용하여 부모 보고서를 디자인하려면</span><span class="sxs-lookup"><span data-stu-id="f8dac-105">To design the parent report using the Report Wizard</span></span>  
  
1.  <span data-ttu-id="f8dac-106">**솔루션 탐색기**에서 최상위 웹 사이트가 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-106">Make sure that the top-level website is selected in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="f8dac-107">웹 사이트를 마우스 오른쪽 단추로 클릭하고 **새 항목 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-107">Right-click on the website and select **Add New Item**.</span></span>  
  
3.  <span data-ttu-id="f8dac-108">**새 항목 추가** 대화 상자에서 **보고서 마법사**를 선택 하 고 보고서 파일의 이름을 입력 한 다음 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-108">In the **Add New Item** dialog box, select **Report Wizard**, enter a name for the report file, and then click **Add**.</span></span>  
  
     <span data-ttu-id="f8dac-109">그러면 보고서 마법사가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-109">This launches the Report Wizard.</span></span>  
  
4.  <span data-ttu-id="f8dac-110">**데이터 세트 속성** 페이지의 **데이터 원본** 상자에서, **2단원: 부모 보고서에 대한 데이터 연결 및 데이터 테이블 정의**에서 만든 [DataSet1](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-110">On the **Dataset Properties** page, in the **Data source** box, select the **DataSet1** you created in [Lesson 2: Define a Data Connection and Data Table for Parent Report](lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).</span></span>  
    <span data-ttu-id="f8dac-111">**사용 가능한 데이터 세트** 상자가 위에서 만든 **DataTable**로 자동 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-111">The **Available datasets** box is automatically updated with the **DataTable** you created above.</span></span>  
  
5.  <span data-ttu-id="f8dac-112">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-112">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="f8dac-113">**필드 정렬** 페이지에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-113">In the **Arrange Fields** page do the following:</span></span>  
  
    1.  <span data-ttu-id="f8dac-114">**ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**및 **ReorderLevel** 을 **사용 가능한 필드** 에서 **값** 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-114">Drag **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel**, and **ReorderLevel** from **Available fields** to the **Values** box.</span></span>  
  
    2.  <span data-ttu-id="f8dac-115">**합계 (ProductID)**, **sum (SafetyStockLevel)**, **sum (ReorderLevel)** 옆의 화살표를 클릭 하 고 **합계** 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-115">Click the arrow next to **Sum(ProductID)**, **Sum(SafetyStockLevel)**, **Sum(ReorderLevel)** and clear the **Sum** selection.</span></span>  
  
7.  <span data-ttu-id="f8dac-116">**다음** 을 두 번 클릭한 다음 **마침** 을 클릭하여 **보고서 마법사**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-116">Click **Next** twice, then click **Finish** to close the **Report Wizard**.</span></span>  
  
     <span data-ttu-id="f8dac-117">이제 .rdlc 파일을 만드는 작업을 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-117">You've now created the .rdlc file.</span></span> <span data-ttu-id="f8dac-118">보고서 디자이너에서 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-118">The file opens in Report Designer.</span></span> <span data-ttu-id="f8dac-119">디자인한 테이블릭스가 이제 디자인 화면에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-119">The tablix you designed is now displayed in the design surface.</span></span>  
  
8.  <span data-ttu-id="f8dac-120">.rdlc 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-120">Save the .rdlc file.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="f8dac-121">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="f8dac-121">Next Task</span></span>  
 <span data-ttu-id="f8dac-122">보고서 마법사를 사용하여 성공적으로 부모 보고서를 디자인했습니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-122">You have successfully designed the parent report using the Report Wizard.</span></span> <span data-ttu-id="f8dac-123">이제 자식 보고서에 대한 데이터 테이블 및 데이터 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f8dac-123">Next, you will create a data connection and a data table for the child report.</span></span>  
  
  
