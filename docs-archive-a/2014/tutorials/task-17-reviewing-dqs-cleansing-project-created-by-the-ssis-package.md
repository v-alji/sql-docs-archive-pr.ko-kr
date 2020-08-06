---
title: '작업 17: SSIS 패키지에 의해 생성 된 DQS 정리 프로젝트 검토 | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0876a0b727e810f8834fcf5445958bf9884a87f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727488"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a><span data-ttu-id="eed84-102">태스크 17: SSIS 패키지로 생성된 DQS 정리 프로젝트 검토</span><span class="sxs-lookup"><span data-stu-id="eed84-102">Task 17: Reviewing DQS Cleansing Project Created by the SSIS package</span></span>
  <span data-ttu-id="eed84-103">이 작업에서는 DQS 클라이언트에서 SSIS 패키지로 생성된 DQS 프로젝트를 열고, 정리 프로세스의 결과를 검토하고, 선택적으로 대화형 정리를 수행하고, 결과를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-103">In this task, you open the DQS project created by the SSIS package in DQS Client, review the results from the cleansing process, and optionally perform interactive cleansing and export the results.</span></span>  
  
1.  <span data-ttu-id="eed84-104">**Data Quality Client**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-104">Launch **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="eed84-105">**관리** 창에서 **작업 모니터링** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-105">Click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
3.  <span data-ttu-id="eed84-106">**작업 시작 시간** 을 기준으로 목록을 정렬 하 여 최신 레코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-106">Sort the list based on **Activity Start Time** to see the latest record.</span></span>  
  
4.  <span data-ttu-id="eed84-107">프로젝트 이름이 **Cleanseandcurate**로 표시 됩니다. 공급자 데이터를 정리 합니다. GUID.</span><span class="sxs-lookup"><span data-stu-id="eed84-107">Notice that you see a name of the project in the following format: **CleanseAndCurate.Cleanse Supplier Data.GUID**.</span></span>  
  
     <span data-ttu-id="eed84-108">![SSIS 패키지를 통해 만든 DQS 정리 프로젝트](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "SSIS 패키지를 통해 만든 DQS 정리 프로젝트")</span><span class="sxs-lookup"><span data-stu-id="eed84-108">![DQS Cleansing Project Created by SSIS Package](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "DQS Cleansing Project Created by SSIS Package")</span></span>  
  
5.  <span data-ttu-id="eed84-109">**활성** 필드의 값이 **활성**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-109">Notice that the value in the **Is Active** field is **Active**.</span></span>  
  
6.  <span data-ttu-id="eed84-110">아래쪽 창에서 **프로파일러** 탭을 클릭 하 여 SSIS 패키지에서 수행한 정리 작업의 프로파일러 통계를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-110">Click **Profiler** tab in the bottom pane to see profiler statistics for the Cleansing activity that the SSIS package performed.</span></span>  
  
7.  <span data-ttu-id="eed84-111">**닫기** 를 클릭 하 여 **관리** 화면을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-111">Click **Close** to close the **Administration** screen.</span></span>  
  
8.  <span data-ttu-id="eed84-112">**DQS 클라이언트**의 기본 페이지에 있는 **데이터 품질 프로젝트** 창에서 **데이터 품질 프로젝트 열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-112">In the main page of **DQS Client**, click **Open Data Quality Project** in the **Data Quality Projects** pane.</span></span>  
  
9. <span data-ttu-id="eed84-113">프로젝트 목록에서 SSIS DQS 정리 구성 요소로 생성된 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-113">In the list of projects, select the project created by SSIS DQS Cleansing component.</span></span> <span data-ttu-id="eed84-114">프로젝트 이름은 **Cleanseandcurate 형식 이어야 합니다. 공급자 데이터를 정리 합니다. GUID (빨간색)**.</span><span class="sxs-lookup"><span data-stu-id="eed84-114">The name of the project should be in format:  **CleanseAndCurate.Cleanse Supplier Data.GUID (in red color)**.</span></span> <span data-ttu-id="eed84-115">**만든 날짜** 열을 기준으로 목록을 정렬 하 고 최신 레코드를 찾아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-115">You may need to sort the list based on **Date Created** column and look for the latest record.</span></span>  
  
10. <span data-ttu-id="eed84-116">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-116">Click **Next**.</span></span>  
  
11. <span data-ttu-id="eed84-117">**결과 관리 및 보기** 페이지는이 자습서의 앞부분에서 수행한 대화형 정리를 통해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-117">The **Manage and View Results** page should be familiar to you from the interactive cleansing you did earlier in this tutorial.</span></span>  
  
12. <span data-ttu-id="eed84-118">정리 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-118">Review the cleansing results.</span></span> <span data-ttu-id="eed84-119">또한 대화형 정리를 수행하고 다음 페이지에서 결과를 Excel 파일 또는 데이터베이스로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-119">You can also perform interactive cleansing and export results to an Excel file or to a database in the next page.</span></span>  
  
13. <span data-ttu-id="eed84-120">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-120">Click **Next**.</span></span> <span data-ttu-id="eed84-121">이 **내보내기** 페이지에서는 excel 파일, CSV 파일 또는 SQL 데이터베이스로 결과를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-121">In this **Export** page, you can export results to an excel file, CSV file, or to a SQL database.</span></span>  
  
14. <span data-ttu-id="eed84-122">**마침** 을 클릭하여 작업을 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-122">Click **Finish** to finish the activity.</span></span>  
  
15. <span data-ttu-id="eed84-123">**DQS 클라이언트**의 기본 페이지에 있는 **관리** 창에서 **작업 모니터링** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-123">In the main page of **DQS Client**, click **Activity Monitoring** in the **Administration** pane.</span></span>  
  
16. <span data-ttu-id="eed84-124">프로젝트에 대 한 **IsActive** 필드의 값이 이제 **종료** 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eed84-124">Notice that the value of **IsActive** field for the project is **Ended** now.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="eed84-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="eed84-125">Next Step</span></span>  
 [<span data-ttu-id="eed84-126">결론</span><span class="sxs-lookup"><span data-stu-id="eed84-126">Conclusion</span></span>](../../2014/tutorials/conclusion.md)  
  
  
