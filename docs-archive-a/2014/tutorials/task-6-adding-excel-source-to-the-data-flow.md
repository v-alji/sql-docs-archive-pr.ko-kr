---
title: '작업 6: 데이터 흐름에 Excel 원본 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ae183dee04619a407655026a49b189f7bb3ac6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653687"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a><span data-ttu-id="50d39-102">태스크 6: Data Flow에 Excel 원본 추가</span><span class="sxs-lookup"><span data-stu-id="50d39-102">Task 6: Adding Excel Source to the Data Flow</span></span>
  <span data-ttu-id="50d39-103">이 작업에서는 데이터 흐름에 Excel 원본을 추가하여 원본 Excel 파일에서 공급자 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-103">In this task, you add an Excel Source to the data flow to read supplier data from the source Excel file.</span></span> <span data-ttu-id="50d39-104">Excel 원본은 Microsoft Excel 통합 문서의 워크시트 또는 범위에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-104">The Excel Source extracts data from worksheets or ranges in Microsoft Excel workbooks.</span></span> <span data-ttu-id="50d39-105">자세한 내용은 [Excel 원본](../integration-services/data-flow/excel-source.md) 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="50d39-105">See [Excel Source](../integration-services/data-flow/excel-source.md) topic for more details.</span></span>

1.  <span data-ttu-id="50d39-106">**SSIS 도구 상자** 의 **기타 원본** 에서 **데이터 흐름** 탭으로 **Excel 원본** 을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-106">Drag-drop **Excel Source** from **Other Sources** in **SSIS Toolbox** to the **Data Flow** tab.</span></span>

2.  <span data-ttu-id="50d39-107">**데이터 흐름** 탭에서 **Excel 원본** 을 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-107">Right-click on **Excel Source** in the **Data Flow** tab, and click **Rename**.</span></span>

3.  <span data-ttu-id="50d39-108">**Excel 파일에서 공급자 데이터 읽기** 를 입력하고 **Enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-108">Type **Read Supplier Data from Excel File** and press **ENTER**.</span></span>

4.  <span data-ttu-id="50d39-109">**Excel 파일에서 공급자 데이터 읽기** 를 두 번 클릭하여 **Excel 원본 편집기** 대화 상자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-109">Double-click **Read Supplier Data from Excel File** to launch the **Excel Source Editor** dialog box.</span></span>

5.  <span data-ttu-id="50d39-110">**Excel 원본 편집기** 대화 상자에서 **새로 만들기** 를 클릭하여 Excel 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-110">In the **Excel Source Editor** dialog box, click **New** to create an Excel connection.</span></span>

6.  <span data-ttu-id="50d39-111">**Excel 연결 관리자** 대화 상자에서 **찾아보기**를 클릭하고 **EIM Tutorial** 폴더의 **Suppliers.xls** 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-111">In the **Excel Connection Manager** dialog box, click **Browse**, and then select the **Suppliers.xls** file in the **EIM Tutorial** folder.</span></span> <span data-ttu-id="50d39-112">**Excel 버전** 상자에서 **Microsoft Excel 97-2003** 이 선택되어 있는지 확인하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-112">Confirm that **Microsoft Excel 97-2003** is selected in the **Excel Version** box and then click **OK**.</span></span>

     <span data-ttu-id="50d39-113">![Excel 연결 관리자 대화 상자](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel 연결 관리자 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="50d39-113">![Excel Connection Manager Dialog Box](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "Excel Connection Manager Dialog Box")</span></span>

7.  <span data-ttu-id="50d39-114">**Excel 원본 편집기** 대화 상자의 **Excel 시트의 이름** 목록 상자에서 **IncomingSuppliers$** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-114">In the **Excel Source Editor** dialog box, select **IncomingSuppliers$** in the **Name of the Excel sheet** list box.</span></span>

     <span data-ttu-id="50d39-115">![Excel 시트의 이름 - 들어오는 공급자$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Excel 시트의 이름 - 들어오는 공급자$")</span><span class="sxs-lookup"><span data-stu-id="50d39-115">![Name of Excel Sheet - Incoming Suppliers$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "Name of Excel Sheet - Incoming Suppliers$")</span></span>

8.  <span data-ttu-id="50d39-116">**미리 보기** 를 클릭하여 Excel 파일의 데이터를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-116">Click **Preview** to preview the data in Excel file.</span></span>

9. <span data-ttu-id="50d39-117">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-117">Click **OK** to close the dialog box.</span></span>

10. <span data-ttu-id="50d39-118">**SSIS 도구 상자** 의 **기타 변환** 에서 **Excel 파일에서 공급자 데이터 읽기** 아래의 **데이터 흐름** 탭으로 **DQS 정리**를 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-118">Drag-drop **DQS Cleansing** transform in **Other Transforms** on the **SSIS Toolbox** to the **Data Flow** tab under **Read Supplier Data from Excel File**.</span></span> <span data-ttu-id="50d39-119">DQS 정리 변환에서 기술 자료의 승인된 규칙을 사용하여 DQS(Data Quality Services)로 데이터를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-119">The DQS Cleansing transformation uses Data Quality Services (DQS) to correct data by applying approved rules in the knowledge base.</span></span> <span data-ttu-id="50d39-120">이 변환은 런타임에 DQS 서버에 DQS 정리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="50d39-120">This transform, at runtime, creates a DQS cleansing project on the DQS server.</span></span> <span data-ttu-id="50d39-121">자세한 내용은 [DQS 정리 변환](https://msdn.microsoft.com/library/ee677619.aspx) 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="50d39-121">See [DQS Cleansing Transformation](https://msdn.microsoft.com/library/ee677619.aspx) topic for more details.</span></span>

## <a name="next-step"></a><span data-ttu-id="50d39-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="50d39-122">Next Step</span></span>

[<span data-ttu-id="50d39-123">태스크 7: Data Flow에 DQS 정리 변환 추가</span><span class="sxs-lookup"><span data-stu-id="50d39-123">Task 7: Adding DQS Cleansing Transform to the Data Flow</span></span>](task-7-adding-dqs-cleansing-transform-to-the-data-flow.md)

### <a name="see-also"></a><span data-ttu-id="50d39-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50d39-124">See Also</span></span>

[<span data-ttu-id="50d39-125">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="50d39-125">Data Flow</span></span>](../integration-services/data-flow/data-flow.md)
