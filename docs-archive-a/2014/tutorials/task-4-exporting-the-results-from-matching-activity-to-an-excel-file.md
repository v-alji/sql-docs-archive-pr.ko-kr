---
title: '작업 4: 일치 작업의 결과를 Excel 파일로 내보내기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 644454c4-3c5a-469a-90ec-e51dc7fb99fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b583e44f887fc0595fb904ec977f1de28c2fecd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735587"
---
# <a name="task-4-exporting-the-results-from-matching-activity-to-an-excel-file"></a><span data-ttu-id="41eb3-102">태스크 4: 일치 작업의 결과를 Excel 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="41eb3-102">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>
  <span data-ttu-id="41eb3-103">이 작업에서는 일치 작업의 결과를 Excel 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-103">In this task, you export the results from the matching activity to an Excel file.</span></span>

1.  <span data-ttu-id="41eb3-104">**내보내기** 페이지에서 **대상 유형** 으로 **Excel 파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-104">In the **Export** page, select **Excel File** for the **Destination Type**.</span></span>

2.  <span data-ttu-id="41eb3-105">**Survivorship 결과** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-105">Select **Survivorship Results** option.</span></span> <span data-ttu-id="41eb3-106">survivorship 프로세스에서 DQS는 사용자가 선택한 **Survivorship 규칙** 에 따라 각 클러스터에 대해 Survivor 레코드를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-106">In the survivorship process, DQS determines a survivor record for each cluster based on the **Survivorship Rule** you selected.</span></span>

3.  <span data-ttu-id="41eb3-107">**찾아보기** 를 클릭하고 출력 파일을 저장할 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-107">Click **Browse** and navigate to the folder where you want to store the output file.</span></span>

4.  <span data-ttu-id="41eb3-108">이름을 **Cleansed and Matched Suppliers.xls** 로 입력하고 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-108">Type **Cleansed and Matched Suppliers.xls** for the name and click **Open**.</span></span>

5.  <span data-ttu-id="41eb3-109">**Survivorship 규칙** 에 대해 **피벗 레코드**가 선택되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-109">Confirm that **Pivot Record** is selected for the **Survivorship Rule**.</span></span> <span data-ttu-id="41eb3-110">이 옵션을 선택하면 각 클러스터의 피벗 레코드가 클러스터의 출력으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-110">When you select this option, the pivot record for each cluster is picked for the output from a cluster.</span></span> <span data-ttu-id="41eb3-111">Survivorship 규칙의 다른 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-111">The other options for the Survivorship Rule are:</span></span>

    1.  <span data-ttu-id="41eb3-112">**가장 완전한 레코드:** 채워진 필드가 가장 많은 레코드가 Survivor 레코드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-112">**Most complete record:** Survivor record is the one with the largest number of populated fields.</span></span>

    2.  <span data-ttu-id="41eb3-113">**가장 긴 레코드:** 원본 필드에서 용어 수가 가장 많은 레코드가 Survivor 레코드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-113">**Longest record:** Survivor record is the one with the largest number of terms in source fields.</span></span>

    3.  <span data-ttu-id="41eb3-114">**가장 완전하고 가장 긴 레코드:** 채워진 필드가 가장 많고 각 필드의 용어 수가 가장 많은 레코드가 Survivor 레코드가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-114">**Most complete and longest record:** Survivor record is the one with the largest number of populated fields, and has the largest number of terms in each field.</span></span>

     <span data-ttu-id="41eb3-115">![일치하는 항목에서 결과 내보내기 페이지](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "일치하는 항목에서 결과 내보내기 페이지")</span><span class="sxs-lookup"><span data-stu-id="41eb3-115">![Export Results from Matching Page](../../2014/tutorials/media/et-exportingtheresultsfrommatoanexcelfile.jpg "Export Results from Matching Page")</span></span>

6.  <span data-ttu-id="41eb3-116">**내보내기** 를 클릭하여 결과를 Excel 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-116">Click **Export** to export the results to an Excel file.</span></span>

7.  <span data-ttu-id="41eb3-117">**닫기** 를 클릭하여 **일치하는 항목 내보내기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-117">Click **Close** to close the **Matching Export** dialog box.</span></span>

8.  <span data-ttu-id="41eb3-118">**마침** 을 클릭하여 일치 작업을 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-118">Click **Finish** to finish the matching activity.</span></span>

9. <span data-ttu-id="41eb3-119">**Cleansed and Matched Suppliers.xlsx** 파일을 열고 중복 항목이 없는지 확인합니다(SupplierID).</span><span class="sxs-lookup"><span data-stu-id="41eb3-119">Open the **Cleansed and Matched Suppliers.xlsx** file and confirm that you do not see any duplicates (SupplierID).</span></span>

 <span data-ttu-id="41eb3-120">이제 중복 항목 제거를 위해 정리 및 일치 작업이 수행된 공급자 데이터가 준비되었습니다.</span><span class="sxs-lookup"><span data-stu-id="41eb3-120">Now, you have supplier data that has been cleansed and matched to remove duplicates.</span></span>

## <a name="next-step"></a><span data-ttu-id="41eb3-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="41eb3-121">Next Step</span></span>
 [<span data-ttu-id="41eb3-122">4단원: MDS에 공급자 데이터 저장</span><span class="sxs-lookup"><span data-stu-id="41eb3-122">Lesson 4: Storing Supplier Data in MDS</span></span>](../../2014/tutorials/lesson-4-storing-supplier-data-in-mds.md)


