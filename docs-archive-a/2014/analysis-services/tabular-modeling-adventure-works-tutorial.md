---
title: 테이블 형식 모델링 (어드벤처 Works 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 140d0b43-9455-4907-9827-16564a904268
author: minewiskan
ms.author: owend
ms.openlocfilehash: 840e8fe04309486d1583bc46161a4fc66ca7b1bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653525"
---
# <a name="tabular-modeling-adventure-works-tutorial"></a><span data-ttu-id="3f880-102">테이블 형식 모델링(Adventure Works 자습서)</span><span class="sxs-lookup"><span data-stu-id="3f880-102">Tabular Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="3f880-103">이 자습서에서는 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 를 사용하여 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]Analysis Services 테이블 형식 모델을 만드는 방법을 설명하는 단원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-103">This tutorial provides lessons on how to create a [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services tabular model by using [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="3f880-104">학습 내용</span><span class="sxs-lookup"><span data-stu-id="3f880-104">What You Will Learn</span></span>  
 <span data-ttu-id="3f880-105">이 자습서에서는 다음 항목을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-105">During the course of this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="3f880-106">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 테이블 형식 모델 프로젝트를 새로 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-106">How to create a new tabular model project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="3f880-107">SQL Server 관계형 데이터베이스의 데이터를 테이블 형식 모델 프로젝트로 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-107">How to import data from a SQL Server relational database into a tabular model project.</span></span>  
  
-   <span data-ttu-id="3f880-108">모델의 테이블 간에 관계를 만들고 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-108">How to create and manage relationships between tables in the model.</span></span>  
  
-   <span data-ttu-id="3f880-109">사용자가 모델 데이터를 분석하는 데 도움을 주는 계산, 측정값 및 핵심 성과 지표를 만들고 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-109">How to create and manage calculations, measures, and Key Performance Indicators that help users analyze model data.</span></span>  
  
-   <span data-ttu-id="3f880-110">비즈니스 및 애플리케이션별 뷰포인트를 통해 사용자가 모델 데이터를 쉽게 탐색할 수 있도록 도움을 주는 큐브 뷰와 계층을 만들고 관리하는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-110">How to create and manage perspectives and hierarchies that help users more easily browse model data by providing business and application specific viewpoints.</span></span>  
  
-   <span data-ttu-id="3f880-111">다른 파티션과 독립적으로 처리할 수 있도록 테이블 데이터를 더 작은 논리적 부분으로 나누는 파티션을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-111">How to create partitions that divide table data into smaller logical parts that can be processed independent from other partitions.</span></span>  
  
-   <span data-ttu-id="3f880-112">사용자 멤버 기반 역할을 만들어 모델 개체 및 데이터를 보호하는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-112">How to secure model objects and data by creating roles with user members.</span></span>  
  
-   <span data-ttu-id="3f880-113">테이블 형식 모델을 테이블 형식 모드로 실행 중인 Analysis Services의 샌드박스 또는 프로덕션 인스턴스에 배포하는 방법</span><span class="sxs-lookup"><span data-stu-id="3f880-113">How to deploy a tabular model to a sandbox or production instance of Analysis Services running in Tabular mode.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="3f880-114">자습서 시나리오</span><span class="sxs-lookup"><span data-stu-id="3f880-114">Tutorial Scenario</span></span>  
 <span data-ttu-id="3f880-115">이 자습서는 가상 회사인 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-115">This tutorial is based on [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], a fictitious company.</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="3f880-116">는 북아메리카, 유럽 및 아시아 시장에서 금속 및 합성 소재 자전거를 생산하고 판매하는 대규모 다국적 제조 회사입니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-116">is a large, multinational manufacturing company that produces and distributes metal and composite bicycles to commercial markets in North America, Europe, and Asia.</span></span> <span data-ttu-id="3f880-117">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 의 본사는 워싱턴 주 보셀에 위치하고 있으며 직원 수는 500명입니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-117">The headquarters for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is in Bothell, Washington, where the company employs 500 workers.</span></span> <span data-ttu-id="3f880-118">또한 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 는 판매 시장에 전반에 걸쳐 몇몇 지역에 영업 팀을 운영하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-118">Additionally, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] employs several regional sales teams throughout its market base.</span></span>  
  
 <span data-ttu-id="3f880-119">영업과 마케팅 팀 및 경영 관리에 필요한 데이터 분석을 지원하기 위해 사용자가 AdventureWorksDW 예제 데이터베이스의 인터넷 매출 데이터를 분석할 수 있도록 테이블 형식 모델을 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-119">To better support the data analysis needs of sales and marketing teams and of senior management, you are tasked with creating a tabular model for users to analyze internet sales data in the AdventureWorksDW sample database.</span></span>  
  
 <span data-ttu-id="3f880-120">자습서를 완료하고 Adventure Works Internet Sales 테이블 형식 모델을 완성하려면 여러 단원을 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-120">In order to complete the tutorial, and the Adventure Works Internet Sales tabular model, you must complete a number of lessons.</span></span> <span data-ttu-id="3f880-121">각 단원에는 여러 가지 작업이 있으며 단원을 완료하려면 각 작업을 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-121">Within each lesson are a number of tasks; completing each task in order is necessary for completing the lesson.</span></span> <span data-ttu-id="3f880-122">특정 단원에는 비슷한 결과를 생성하는 여러 태스크가 포함되어 있지만 태스크를 완료하는 방법은 조금씩 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-122">While in a particular lesson there may be several tasks that accomplish a similar outcome; however, how you complete each task is slightly different.</span></span> <span data-ttu-id="3f880-123">이는 특정 태스크를 완료하는 방법에는 여러 가지가 있음을 보여 주고 이전 태스크에서 배운 기술을 사용해 보도록 하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-123">This is to show that there is often more than one way to complete a particular task, and to challenge you by using skills you learned in previous tasks.</span></span>  
  
 <span data-ttu-id="3f880-124">단원의 목적은 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에 포함된 여러 가지 기능을 사용하여 메모리 내 모드로 실행되는 기본 테이블 형식 모델을 제작하는 과정을 안내하는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-124">The purpose of the lessons is to guide you through authoring a basic tabular model running in In-Memory mode by using many of the features included in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="3f880-125">각 단원은 이전 단원에 기반을 두고 있으므로 단원을 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-125">Because each lesson builds upon the previous lesson, you should complete the lessons in order.</span></span> <span data-ttu-id="3f880-126">단원을 모두 완료하면 Adventure Works Internet Sales 예제 테이블 형식 모델이 만들어져 Analysis Services 서버에 배포되어 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-126">Once you have completed all of the lessons, you will have authored and deployed the Adventure Works Internet Sales sample tabular model on an Analysis Services server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f880-127">이 자습서에서는 배포한 테이블 형식 모델 데이터베이스를 SQL Server Management Studio를 사용하여 관리하거나 보고 클라이언트 애플리케이션을 사용하여 배포된 모델에 연결하여 모델 데이터를 탐색하는 과정을 안내하는 단원이나 정보는 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-127">This tutorial does not provide lessons or information about managing a deployed tabular model database by using SQL Server Management Studio, or using a reporting client application to connect to a deployed model to browse model data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3f880-128">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3f880-128">Prerequisites</span></span>  
 <span data-ttu-id="3f880-129">이 자습서를 완료하려면 다음 필수 구성 요소가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-129">In order to complete this tutorial, you must have the following prerequisites installed:</span></span>  
  
-   <span data-ttu-id="3f880-130">테이블 형식 모드에서 실행 중인 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services 인스턴스</span><span class="sxs-lookup"><span data-stu-id="3f880-130">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Analysis Services instance running in Tabular mode.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="3f880-131">.</span><span class="sxs-lookup"><span data-stu-id="3f880-131">.</span></span>  
  
-   <span data-ttu-id="3f880-132">AdventureWorksDW 예제 데이터베이스.</span><span class="sxs-lookup"><span data-stu-id="3f880-132">AdventureWorksDW sample database.</span></span> <span data-ttu-id="3f880-133">이 예제 데이터베이스에는 이 자습서를 완료하는 데 필요한 데이터가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-133">This sample database includes the data necessary to complete this tutorial.</span></span> <span data-ttu-id="3f880-134">예제 데이터베이스를 다운로드 하려면를 참조 하십시오 [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks) .</span><span class="sxs-lookup"><span data-stu-id="3f880-134">To download the sample database, see [https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks](https://github.com/microsoft/sql-server-samples/releases/tag/adventureworks).</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="3f880-135">Excel 2003 이상(11단원의 Excel에서 분석 기능을 사용하는 데 필요)</span><span class="sxs-lookup"><span data-stu-id="3f880-135">Excel 2003 or later (for use with the Analyze in Excel feature in lesson 11)</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="3f880-136">단원</span><span class="sxs-lookup"><span data-stu-id="3f880-136">Lessons</span></span>  
 <span data-ttu-id="3f880-137">이 자습서에는 다음 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-137">This tutorial includes the following lessons:</span></span>  
  
|<span data-ttu-id="3f880-138">단원</span><span class="sxs-lookup"><span data-stu-id="3f880-138">Lesson</span></span>|<span data-ttu-id="3f880-139">예상 완료 시간</span><span class="sxs-lookup"><span data-stu-id="3f880-139">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="3f880-140">1단원: 새 테이블 형식 모델 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-140">Lesson 1: Create a New Tabular Model Project</span></span>](lesson-1-create-a-new-tabular-model-project.md)|<span data-ttu-id="3f880-141">10분</span><span class="sxs-lookup"><span data-stu-id="3f880-141">10 minutes</span></span>|  
|[<span data-ttu-id="3f880-142">2단원: 데이터 추가</span><span class="sxs-lookup"><span data-stu-id="3f880-142">Lesson 2: Add Data</span></span>](lesson-2-add-data.md)|<span data-ttu-id="3f880-143">20분</span><span class="sxs-lookup"><span data-stu-id="3f880-143">20 minutes</span></span>|  
|[<span data-ttu-id="3f880-144">3단원: 열 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="3f880-144">Lesson 3: Rename Columns</span></span>](rename-columns.md)|<span data-ttu-id="3f880-145">20분</span><span class="sxs-lookup"><span data-stu-id="3f880-145">20 minutes</span></span>|  
|[<span data-ttu-id="3f880-146">4단원: 날짜 테이블로 표시</span><span class="sxs-lookup"><span data-stu-id="3f880-146">Lesson 4: Mark as Date Table</span></span>](lesson-3-mark-as-date-table.md)|<span data-ttu-id="3f880-147">3분</span><span class="sxs-lookup"><span data-stu-id="3f880-147">3 minutes</span></span>|  
|[<span data-ttu-id="3f880-148">5단원: 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-148">Lesson 5: Create Relationships</span></span>](lesson-4-create-relationships.md)|<span data-ttu-id="3f880-149">10분</span><span class="sxs-lookup"><span data-stu-id="3f880-149">10 minutes</span></span>|  
|[<span data-ttu-id="3f880-150">6단원: 계산 열 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-150">Lesson 6: Create Calculated Columns</span></span>](lesson-5-create-calculated-columns.md)|<span data-ttu-id="3f880-151">15분</span><span class="sxs-lookup"><span data-stu-id="3f880-151">15 minutes</span></span>|  
|[<span data-ttu-id="3f880-152">7단원: 측정값 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-152">Lesson 7: Create Measures</span></span>](lesson-6-create-measures.md)|<span data-ttu-id="3f880-153">30분</span><span class="sxs-lookup"><span data-stu-id="3f880-153">30 minutes</span></span>|  
|[<span data-ttu-id="3f880-154">8단원: 핵심 성과 지표 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-154">Lesson 8: Create Key Performance Indicators</span></span>](lesson-7-create-key-performance-indicators.md)|<span data-ttu-id="3f880-155">15분</span><span class="sxs-lookup"><span data-stu-id="3f880-155">15 minutes</span></span>|  
|[<span data-ttu-id="3f880-156">9단원: 큐브 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-156">Lesson 9: Create Perspectives</span></span>](lesson-8-create-perspectives.md)|<span data-ttu-id="3f880-157">5분</span><span class="sxs-lookup"><span data-stu-id="3f880-157">5 minutes</span></span>|  
|[<span data-ttu-id="3f880-158">10단원: 계층 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-158">Lesson 10: Create Hierarchies</span></span>](lesson-9-create-hierarchies.md)|<span data-ttu-id="3f880-159">20분</span><span class="sxs-lookup"><span data-stu-id="3f880-159">20 minutes</span></span>|  
|[<span data-ttu-id="3f880-160">11단원: 파티션 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-160">Lesson 11: Create Partitions</span></span>](lesson-10-create-partitions.md)|<span data-ttu-id="3f880-161">15분</span><span class="sxs-lookup"><span data-stu-id="3f880-161">15 minutes</span></span>|  
|[<span data-ttu-id="3f880-162">12단원: 역할 만들기</span><span class="sxs-lookup"><span data-stu-id="3f880-162">Lesson 12: Create Roles</span></span>](lesson-11-create-roles.md)|<span data-ttu-id="3f880-163">15분</span><span class="sxs-lookup"><span data-stu-id="3f880-163">15 minutes</span></span>|  
|[<span data-ttu-id="3f880-164">13단원: 도구 모음</span><span class="sxs-lookup"><span data-stu-id="3f880-164">Lesson 13: Analyze in Excel</span></span>](lesson-12-analyze-in-excel.md)|<span data-ttu-id="3f880-165">20분</span><span class="sxs-lookup"><span data-stu-id="3f880-165">20 minutes</span></span>|  
|[<span data-ttu-id="3f880-166">14단원: 배포</span><span class="sxs-lookup"><span data-stu-id="3f880-166">Lesson 14: Deploy</span></span>](lesson-13-deploy.md)|<span data-ttu-id="3f880-167">5분</span><span class="sxs-lookup"><span data-stu-id="3f880-167">5 minutes</span></span>|  
  
## <a name="supplemental-lessons"></a><span data-ttu-id="3f880-168">추가 단원</span><span class="sxs-lookup"><span data-stu-id="3f880-168">Supplemental Lessons</span></span>  
 <span data-ttu-id="3f880-169">이 자습서에는 [추가 단원](../tutorials/supplemental-lessons.md)도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-169">This tutorial also includes [Supplemental Lessons](../tutorials/supplemental-lessons.md).</span></span> <span data-ttu-id="3f880-170">이 섹션의 항목은 자습서를 완료하기 위한 필수 항목은 아니지만 고급 테이블 형식 모델 제작 기능을 더 잘 이해하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-170">Topics in this section are not required to complete the tutorial, but can be helpful in better understanding advanced tabular model authoring features.</span></span>  
  
 <span data-ttu-id="3f880-171">이 자습서에는 다음 추가 단원이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f880-171">This tutorial includes the following supplemental lessons:</span></span>  
  
|<span data-ttu-id="3f880-172">단원</span><span class="sxs-lookup"><span data-stu-id="3f880-172">Lesson</span></span>|<span data-ttu-id="3f880-173">예상 완료 시간</span><span class="sxs-lookup"><span data-stu-id="3f880-173">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="3f880-174">행 필터를 사용하여 동적 보안 구현</span><span class="sxs-lookup"><span data-stu-id="3f880-174">Implement Dynamic Security by Using Row Filters</span></span>](../tutorials/implement-dynamic-security-by-using-row-filters.md)|<span data-ttu-id="3f880-175">30분</span><span class="sxs-lookup"><span data-stu-id="3f880-175">30 minutes</span></span>|  
|<span data-ttu-id="3f880-176">[파워 뷰 보고서의 보고 속성 구성](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md) 파워 뷰 보고서의 보고 속성 구성</span><span class="sxs-lookup"><span data-stu-id="3f880-176">[Configure Reporting Properties for Power View Reports](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)Configure Reporting Properties for Power View Reports</span></span>|<span data-ttu-id="3f880-177">30분</span><span class="sxs-lookup"><span data-stu-id="3f880-177">30 minutes</span></span>|  
  
## <a name="next-step"></a><span data-ttu-id="3f880-178">다음 단계</span><span class="sxs-lookup"><span data-stu-id="3f880-178">Next Step</span></span>  
 <span data-ttu-id="3f880-179">자습서를 시작하려면 첫 번째 단원인 [1단원: 새 테이블 형식 모델 프로젝트를 만들기](lesson-1-create-a-new-tabular-model-project.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="3f880-179">To begin the tutorial, continue to the first lesson: [Lesson 1: Create a New Tabular Model Project](lesson-1-create-a-new-tabular-model-project.md).</span></span>  
  
  
