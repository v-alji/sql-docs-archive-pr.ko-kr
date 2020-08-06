---
title: '태스크 5: 정리 결과를 Excel 파일로 내보내기 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: eaeafd65-d0d4-4a7d-a3ad-110ef644e90b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0dbdc1bef348e03e211e4933132985ea2c089b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653692"
---
# <a name="task-5-exporting-cleansing-results-to-an-excel-file"></a><span data-ttu-id="34e12-102">태스크 5: 정리 결과를 Excel 파일로 내보내기</span><span class="sxs-lookup"><span data-stu-id="34e12-102">Task 5: Exporting Cleansing Results to an Excel File</span></span>
  <span data-ttu-id="34e12-103">이 작업에서는 정리 작업의 결과를 Excel 파일로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-103">In this task, you export results from the cleansing activity to an Excel file.</span></span> <span data-ttu-id="34e12-104">자세한 내용은 [내보내기 단계](https://msdn.microsoft.com/library/hh213061.aspx#Export) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34e12-104">See [Export Stage](https://msdn.microsoft.com/library/hh213061.aspx#Export) topic for more details.</span></span>  
  
1.  <span data-ttu-id="34e12-105">오른쪽 창에서 **대상 유형**으로 **Excel** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-105">In the right pane, select **Excel** for the **Destination Type**.</span></span>  
  
2.  <span data-ttu-id="34e12-106">**찾아보기**를 클릭 하 고 출력 파일 이름을 **정리 된 공급자 List.xls**로 지정한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-106">Click **Browse**, specify the output file name as **Cleansed Supplier List.xls**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="34e12-107">정리 된 데이터만 내보내려면 **출력** 형식에 대해서 **만 데이터** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-107">Select **Data Only** for the **Output** format to export just the cleansed data.</span></span> <span data-ttu-id="34e12-108">두 번째 옵션인 **데이터 및 정리 정보**를 사용 하 여 정리 된 데이터와 함께 정리 작업 세부 정보를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-108">The second option, **Data and Cleansing Info**, lets you export cleansing activity details along with the cleansed data.</span></span> <span data-ttu-id="34e12-109">**표준화 형식** 옵션을 사용 하면 도메인에서 정의한 모든 출력 형식을 해당 도메인의 값에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-109">The **Standardize Format** option lets you apply any output formats you define on a domain to the values of that domain.</span></span> <span data-ttu-id="34e12-110">이 자습서에서는 어떠한 도메인에도 출력 형식을 정의하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-110">You have not defined an output format on any domain in the tutorial.</span></span>  
  
     <span data-ttu-id="34e12-111">![정리 결과 내보내기 페이지](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "정리 결과 내보내기 페이지")</span><span class="sxs-lookup"><span data-stu-id="34e12-111">![Export Cleansing Results Page](../../2014/tutorials/media/et-exportingcleansingresultstoanexcelfile.jpg "Export Cleansing Results Page")</span></span>  
  
4.  <span data-ttu-id="34e12-112">**내보내기** 를 클릭 하 여 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-112">Click **Export** to export the data.</span></span> <span data-ttu-id="34e12-113">아직 **마침** 을 클릭 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="34e12-113">Do not click **Finish** yet.</span></span>  
  
5.  <span data-ttu-id="34e12-114">**내보내기** 대화 상자에서 **닫기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-114">Click **Close** on the **Exporting** dialog box.</span></span>  
  
6.  <span data-ttu-id="34e12-115">**마침** 을 클릭하여 작업을 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-115">Click **Finish** to finish the activity.</span></span> <span data-ttu-id="34e12-116">**마침**을 클릭 하기 전에 결과를 내보내지 않은 경우 **dqs 클라이언트**의 기본 페이지에서 **데이터 품질 프로젝트 열기** 를 클릭 하 고, 프로젝트 목록에서 **공급자 목록 정리** 를 선택 하 고, 화면 아래쪽에서 **다음** 을 클릭 하 여 정리 프로세스의 **내보내기** 단계로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-116">If you forgot to export results before clicking **Finish**, click **Open Data Quality Project** in the main page of **DQS Client**, select **Cleanse Supplier List** from the list of projects, and click **Next** at the bottom of the screen to get to the **Export** stage of cleansing process again.</span></span> <span data-ttu-id="34e12-117">**뒤로** 단추를 클릭 하 여 **결과 관리 및 보기** 탭으로 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-117">You can also switch to **Manage and View Results** tab by clicking **Back** button.</span></span>  
  
7.  <span data-ttu-id="34e12-118">**List.xls정리 된 공급자** 를 열고 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-118">Open the **Cleansed Supplier List.xls** and do the following:</span></span>  
  
    1.  <span data-ttu-id="34e12-119">워크시트에서 adventure-work.com를 검색 하 여 adventure-work.com으로 끝나는 전자 메일 주소 (문자 ' 없음 ')가 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-119">Ensure that there are no email addresses that end with adventure-work.com (without character 's') by searching for adventure-work.com in the worksheet.</span></span>  
  
    2.  <span data-ttu-id="34e12-120">**Country** 열에 **USA** 값이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-120">See that there is no **USA** value in the **Country** column.</span></span>  
  
    3.  <span data-ttu-id="34e12-121">**Los Angeles**로 검색하고 **State**가 **CA**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-121">Search for **Los Angeles** and see that the **State** is set to **CA**.</span></span>  
  
    4.  <span data-ttu-id="34e12-122">**동료**, **Corp.** 및 **inc.** 용어가 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-122">Confirm that there are no terms **Co.**, **Corp.**, and **Inc.**.</span></span>  
  
    5.  <span data-ttu-id="34e12-123">스프레드시트에서 **주소 유효성 검사** 열을 삭제 하 고 excel 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-123">Delete the **Address Validation** column from the spreadsheet and save the excel file.</span></span> <span data-ttu-id="34e12-124">이 추가 열은 Address Validation 복합 도메인에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="34e12-124">This additional column corresponds to the Address Validation composite domain.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="34e12-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="34e12-125">Next Step</span></span>  
 [<span data-ttu-id="34e12-126">태스크 6: Cleanse Supplier List 프로젝트에서 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="34e12-126">Task 6: Importing Values from the Cleanse Supplier List Project</span></span>](../../2014/tutorials/task-6-importing-values-from-the-cleanse-supplier-list-project.md)  
  
  
