---
title: '작업 3: 일치에 대 한 데이터 품질 프로젝트 만들기 및 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6260e911-ea8b-4c69-a39d-d1bccd565a32
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 221d6d583c61ee035c20fcb63f0ed5278f2b8678
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647389"
---
# <a name="task-3-creating-and-running-a-data-quality-project-for-matching"></a><span data-ttu-id="8ba9a-102">태스크 3: 일치에 대한 데이터 품질 프로젝트 만들기 및 실행</span><span class="sxs-lookup"><span data-stu-id="8ba9a-102">Task 3: Creating and Running a Data Quality Project for Matching</span></span>
  <span data-ttu-id="8ba9a-103">이 작업에서는 일치 작업을 위한 데이터 품질 프로젝트를 만들고 정리된 공급자 데이터에서 일치 프로세스를 실행하여 데이터에 있는 모든 중복 항목을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-103">In this task, you create a Data Quality Project for the matching activity and run the matching process on cleansed supplier data to remove any duplicates in the data.</span></span>

1.  <span data-ttu-id="8ba9a-104">**DQS 클라이언트**의 기본 페이지에서 **새 데이터 품질 프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-104">On the main page of **DQS Client**, click **New Data Quality Project**.</span></span>

2.  <span data-ttu-id="8ba9a-105">**프로젝트 이름** 에서 **Remove Supplier Duplicates**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-105">Type **Remove Supplier Duplicates** from the **Name of the project**.</span></span>

3.  <span data-ttu-id="8ba9a-106">**기술 자료 사용** 필드의 KB 목록에서 **Suppliers** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-106">Select **Suppliers** from the list of KBs for the **Use Knowledge Base** field.</span></span> <span data-ttu-id="8ba9a-107">이 기술 자료의 일치 정책은 이전 단원에서 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-107">You have created a matching policy in this knowledge base in the previous lesson.</span></span>

4.  <span data-ttu-id="8ba9a-108">오른쪽 하단 창의 **작업 목록** 에서 **일치** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-108">Select **Matching** from the **list of activities** from the bottom-right pane.</span></span>

     <span data-ttu-id="8ba9a-109">![새 데이터 품질 프로젝트 - 선택한 일치하는 항목](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "새 데이터 품질 프로젝트 - 선택한 일치하는 항목")</span><span class="sxs-lookup"><span data-stu-id="8ba9a-109">![New Data Quality Project - Matching Selected](../../2014/tutorials/media/et-creatingandrunningadqpformatching.jpg "New Data Quality Project - Matching Selected")</span></span>

5.  <span data-ttu-id="8ba9a-110">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-110">Click **Next**.</span></span>

6.  <span data-ttu-id="8ba9a-111">**맵** 페이지에서 **데이터 원본** 에 대해 **Excel 파일**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-111">In the **Map** page, select **Excel File** for **Data Source**.</span></span>

7.  <span data-ttu-id="8ba9a-112">**찾아보기** 를 클릭하고 정리 작업의 출력 파일인 **Cleansed Supplier List.xls**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-112">Click **Browse** and select **Cleansed Supplier List.xls**, which is the output file from the cleansing activity.</span></span>

8.  <span data-ttu-id="8ba9a-113">**SupplierID** 원본 열을 **Supplier ID** 도메인에 매핑하고, **Supplier Name** 열을 **Supplier Name** 도메인에 매핑하고, **ContactEmailAddress** 열을 **Contact Email** 도메인에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-113">Map **SupplierID** source column to the **Supplier ID** domain, **Supplier Name** column to **Supplier Name** domain, and **ContactEmailAddress** column to **Contact Email** domain.</span></span>

9. <span data-ttu-id="8ba9a-114">**다음** 을 클릭하여 **일치** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-114">Click **Next** to switch to the **Matching** page.</span></span>

10. <span data-ttu-id="8ba9a-115">**시작** 을 클릭하여 일치 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-115">Click **Start** to start the matching process.</span></span> <span data-ttu-id="8ba9a-116">일치 정책을 정의할 때와 동일한 입력 파일이 사용되었으므로 이전 작업과 비슷한 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-116">You should see results similar to those from the previous task because you used the same input file for defining the matching policy.</span></span>

11. <span data-ttu-id="8ba9a-117">모든 일치 레코드 및 일치 점수를 목록 상자에서 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-117">Review all the matched records and their matching score in the list box.</span></span> <span data-ttu-id="8ba9a-118">결과는 이전 작업에서 표시된 것과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-118">The results should be same as the ones you saw in the previous task.</span></span> <span data-ttu-id="8ba9a-119">이 일치 작업의 결과를 분석하려면 이전 작업의 단계를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-119">See the steps in the previous task to analyze the results from this matching activity.</span></span>

12. <span data-ttu-id="8ba9a-120">**다음** 을 클릭하여 **내보내기** 페이지로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ba9a-120">Click **Next** to switch to the **Export** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="8ba9a-121">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8ba9a-121">Next Step</span></span>
 [<span data-ttu-id="8ba9a-122">태스크 4: 일치 작업의 결과를 Excel 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="8ba9a-122">Task 4: Exporting the Results from Matching Activity to an Excel File</span></span>](../../2014/tutorials/task-4-exporting-the-results-from-matching-activity-to-an-excel-file.md)


