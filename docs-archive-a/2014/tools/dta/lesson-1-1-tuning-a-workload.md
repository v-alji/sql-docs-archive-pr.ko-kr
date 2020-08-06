---
title: 작업 튜닝 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- workloads [SQL Server], tuning
ms.assetid: 6229bf3f-1182-4bc6-8451-cedc37f4b62e
author: stevestein
ms.author: sstein
ms.openlocfilehash: f95aab55d402ac72228dcc4326ad00ea15e7471f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734792"
---
# <a name="tuning-a-workload"></a><span data-ttu-id="b041b-102">작업 튜닝</span><span class="sxs-lookup"><span data-stu-id="b041b-102">Tuning a Workload</span></span>
  <span data-ttu-id="b041b-103">데이터베이스 엔진 튜닝 관리자를 사용하여 튜닝하려고 선택한 데이터베이스와 테이블의 쿼리 성능에 가장 적합한 물리적 데이터베이스 디자인을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-103">The Database Engine Tuning Advisor can be used to find the best physical database design for query performance on the databases and tables that you select for tuning.</span></span>  
  
 <span data-ttu-id="b041b-104">이 태스크에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 예제 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-104">This task uses the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="b041b-105">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-105">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="b041b-106">예제 데이터베이스를 설치하려면 [SQL Server 예제 및 예제 데이터베이스](http://sqlserversamples.codeplex.com)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b041b-106">To install the sample databases, see [Installing SQL Server Samples and Sample Databases](http://sqlserversamples.codeplex.com).</span></span>  
  
### <a name="tune-a-workload-transact-sql-script-file"></a><span data-ttu-id="b041b-107">작업 Transact-SQL 스크립트 파일 튜닝</span><span class="sxs-lookup"><span data-stu-id="b041b-107">Tune a workload Transact-SQL script file</span></span>  
  
1.  <span data-ttu-id="b041b-108">"1. SELECT를 사용하여 행 및 열</span><span class="sxs-lookup"><span data-stu-id="b041b-108">Copy a sample SELECT statement or statements from "A.</span></span> <span data-ttu-id="b041b-109">검색"([SELECT 예제&#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql))에서 샘플 SELECT 문을 복사하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 쿼리 편집기에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-109">Using SELECT to retrieve rows and columns" in [SELECT Examples &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql) and paste the statements into the Query Editor of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="b041b-110">쉽게 찾을 수 있는 디렉터리에 **MyScript.sql**이라는 이름으로 파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-110">Save the file as **MyScript.sql** in a directory where you can easily find it.</span></span>  
  
2.  <span data-ttu-id="b041b-111">데이터베이스 엔진 튜닝 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-111">Start Database Engine Tuning Advisor.</span></span> <span data-ttu-id="b041b-112">[데이터베이스 엔진 튜닝 관리자 시작](../../relational-databases/performance/database-engine-tuning-advisor.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b041b-112">See [Launching Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
3.  <span data-ttu-id="b041b-113">데이터베이스 엔진 튜닝 관리자 GUI의 오른쪽 창에 있는 **세션 이름** 에 **MySession**을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-113">In the right pane of the Database Engine Tuning Advisor GUI, type **MySession** in **Session name**.</span></span>  
  
4.  <span data-ttu-id="b041b-114">**작업** 에 대해 **파일**을 선택하고 **작업 파일을 찾습니다.** 단추를 클릭하여 1단계에서 저장한 **MyScript.sql** 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-114">Select **File** for your **Workload**, and click the **Browse for a workload file** button to locate the **MyScript.sql** file that you saved in Step 1.</span></span>  
  
5.  <span data-ttu-id="b041b-115">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 작업 분석용 데이터베이스 **목록에서** 를 선택하고, [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 튜닝할 데이터베이스 및 테이블 선택 **표에서** 를 선택하고, **튜닝 로그 저장** 을 선택된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-115">Select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Database for workload analysis** list, select [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in the **Select databases and tables to tune** grid, and leave **Save tuning log** selected.</span></span> <span data-ttu-id="b041b-116">**작업 분석용 데이터베이스** 는 작업 튜닝 시 데이터베이스 엔진 튜닝 관리자가 연결하는 첫 번째 데이터베이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-116">**Database for workload analysis** specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span> <span data-ttu-id="b041b-117">튜닝이 시작된 후 데이터베이스 엔진 튜닝 관리자는 작업에 포함된 `USE DATABASE` 문으로 지정한 데이터베이스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-117">After tuning begins, Database Engine Tuning Advisor connects to the databases specified by the `USE DATABASE` statements contained in the workload.</span></span>  
  
6.  <span data-ttu-id="b041b-118">**튜닝 옵션** 탭을 클릭 합니다. 이 연습에서는 튜닝 옵션을 설정 하지 않지만 잠시 기본 튜닝 옵션을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-118">Click the **Tuning Options** tab. You will not set any tuning options for this practice, but take a moment to review the default tuning options.</span></span> <span data-ttu-id="b041b-119">이 탭 페이지에 대한 도움말을 보려면 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-119">Press F1 to view the Help for this tabbed page.</span></span> <span data-ttu-id="b041b-120">추가 튜닝 옵션을 보려면 **고급 옵션** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-120">Click **Advanced Options** to view additional tuning options.</span></span> <span data-ttu-id="b041b-121">**고급 튜닝 옵션** 대화 상자에서 표시된 튜닝 옵션에 대한 정보를 보려면 **도움말** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-121">Click **Help** in the **Advanced Tuning Options** dialog box for information about the tuning options that are displayed there.</span></span> <span data-ttu-id="b041b-122">기본 옵션을 선택한 상태에서 **고급 튜닝 옵션** 대화 상자를 닫으려면 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-122">Click **Cancel** to close the **Advanced Tuning Options** dialog box, leaving the default options selected.</span></span>  
  
7.  <span data-ttu-id="b041b-123">도구 모음에서 **분석 시작** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-123">Click the **Start Analysis** button on the toolbar.</span></span> <span data-ttu-id="b041b-124">데이터베이스 엔진 튜닝 관리자 작업을 분석 하는 동안 **진행률** 탭에서 상태를 모니터링할 수 있습니다. 튜닝이 완료 되 면 **권장** 구성 탭이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-124">While Database Engine Tuning Advisor is analyzing the workload, you can monitor the status on the **Progress** tab. When tuning is complete, the **Recommendations** tab is displayed.</span></span>  
  
     <span data-ttu-id="b041b-125">튜닝 중지 날짜 및 시간에 대 한 오류가 표시 되는 경우 주 **튜닝 옵션** 탭에서 **중지** 시간을 확인 합니다. 날짜 및 시간 **에 중지** 가 현재 날짜 및 시간 보다 큰지 확인 하 고 필요한 경우 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-125">If you receive an error about the tuning stop date and time, check the **Stop at** time on the main **Tuning Options** tab. Make sure the **Stop at** date and time are greater than the current date and time, and if necessary, change them.</span></span>  
  
8.  <span data-ttu-id="b041b-126">분석을 완료한 후 [!INCLUDE[tsql](../../includes/tsql-md.md)] 동작 **메뉴에서** 권장 구성 저장 **을 클릭하여** 스크립트로 권장 구성을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-126">After the analysis completes, save your recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script by clicking **Save Recommendations** on the **Actions** menu.</span></span> <span data-ttu-id="b041b-127">**다른 이름으로 저장** 대화 상자에서 권장 구성 스크립트를 저장할 디렉터리로 이동하고 파일 이름 **MyRecommendations**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-127">In the **Save As** dialog box, navigate to the directory where you want to save the recommendations script, and type the file name **MyRecommendations**.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="b041b-128">요약</span><span class="sxs-lookup"><span data-stu-id="b041b-128">Summary</span></span>  
 <span data-ttu-id="b041b-129">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에서 단순 SELECT 문 작업 튜닝을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-129">You have completed tuning a simple SELECT statement workload on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="b041b-130">데이터베이스 엔진 튜닝 관리자에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 추적 파일과 테이블을 튜닝 작업으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-130">The Database Engine Tuning Advisor can also take [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace files and tables as tuning workloads.</span></span> <span data-ttu-id="b041b-131">다음 태스크에서는 연습 튜닝의 결과로 받은 튜닝 권장 구성을 확인하고 해석하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b041b-131">The next task shows you how to view and interpret the tuning recommendations that you received as a result of the practice tuning.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="b041b-132">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="b041b-132">Next Task in Lesson</span></span>  
 [<span data-ttu-id="b041b-133">튜닝 권장 구성 보기</span><span class="sxs-lookup"><span data-stu-id="b041b-133">Viewing Tuning Recommendations</span></span>](lesson-1-2-viewing-tuning-recommendations.md)  
  
  
