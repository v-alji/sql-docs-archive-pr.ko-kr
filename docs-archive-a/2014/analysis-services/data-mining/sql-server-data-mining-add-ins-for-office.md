---
title: Office 용 SQL Server 데이터 마이닝 추가 기능 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b64d0c8728e4752d0d5831562d43646e29f7d723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639091"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a><span data-ttu-id="64f69-102">Office용 SQL Server 데이터 마이닝 추가 기능</span><span class="sxs-lookup"><span data-stu-id="64f69-102">SQL Server Data Mining Add-Ins for Office</span></span>
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] <span data-ttu-id="64f69-103">Office용 데이터 마이닝 추가 기능은 Excel의 데이터를 사용하여 예측, 권장 또는 탐색을 위한 분석 모델을 작성할 수 있도록 지원하는 일련의 간단한 예측 분석 도구 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-103">Data Mining Add-ins for Office is a lightweight set of tools for predictive analytics that lets you use data in Excel to build analytical models for prediction, recommendation, or exploration.</span></span>  
  
 <span data-ttu-id="64f69-104">추가 기능의 마법사 및 데이터 관리 도구는 다음과 같은 일반 데이터 마이닝 작업에 대한 단계별 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-104">The wizards and data management tools in the add-ins provide step-by-step instruction for these common data mining tasks:</span></span>  
  
-   <span data-ttu-id="64f69-105">**모델링하기 전에 데이터를 구성 및 정리합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-105">**Organize and clean your data prior to modeling.**</span></span> <span data-ttu-id="64f69-106">Excel 또는 Excel 데이터 원본에 저장된 데이터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-106">Use data stored in Excel or any Excel data source.</span></span> <span data-ttu-id="64f69-107">연결을 만들어 저장한 후 데이터 원본을 다시 사용하거나 실험을 반복하거나 모델을 다시 학습시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-107">You can create and save connections to re-use data sources, repeat experiments, or re-train models.</span></span>  
  
-   <span data-ttu-id="64f69-108">**프로필을 만들고 샘플링하고 준비합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-108">**Profile, sample, and prepare.**</span></span> <span data-ttu-id="64f69-109">많은 데이터 마이닝 전문가에 따르면 데이터 마이닝 프로젝트의 70-90퍼센트가 데이터 준비에 소모됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-109">Many experienced data miners say that as much as 70-90 percent of a data mining project is spent on data preparation.</span></span> <span data-ttu-id="64f69-110">추가 기능은 다음과 같은 일반 작업에 도움이 되는 마법사와 Excel의 시각화 기능을 제공하여 데이터 준비 작업이 보다 빠르게 진행될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-110">The add-ins can make this task go faster, by providing visualizations in Excel and wizards that help you with these common tasks:</span></span>  
  
    -   <span data-ttu-id="64f69-111">데이터를 프로파일링하고 데이터의 분포 및 특성을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-111">Profile data and understand its distribution and characteristics.</span></span>  
  
    -   <span data-ttu-id="64f69-112">무작위 샘플링이나 초과 샘플링을 통해 학습 및 테스트 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-112">Create training and testing sets through random sampling or oversampling.</span></span>  
  
    -   <span data-ttu-id="64f69-113">이상값을 찾아 제거하거나 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-113">Find outliers and remove or replace them.</span></span>  
  
    -   <span data-ttu-id="64f69-114">데이터에 레이블을 다시 지정하여 분석 품질을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-114">Re-label data to improve the quality of analysis.</span></span>  
  
-   <span data-ttu-id="64f69-115">**감독 또는 자율 학습을 통해 패턴을 분석합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-115">**Analyze patterns through supervised or unsupervised learning.**</span></span> <span data-ttu-id="64f69-116">편리한 마법사를 클릭하면서 클러스터링 분석, 시장 바구니 분석 및 예측 등 몇 가지 가장 널리 사용되는 데이터 마이닝 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-116">Click through friendly wizards to perform some of the most popular data mining tasks, including clustering analysis, market basket analysis, and forecasting.</span></span>  
  
     <span data-ttu-id="64f69-117">추가 기능에 포함된 잘 알려진 시스템 학습 알고리즘 중에는 Naïve Bayes, 로지스틱 회귀, 클러스터링, 시계열 및 신경망이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-117">Among the well-known machine learning algorithms included in the add-ins are Naïve Bayes, logistic regression, clustering, time series, and neural networks.</span></span>  
  
     <span data-ttu-id="64f69-118">데이터 마이닝이 처음이라면 **쿼리** 마법사의 도움을 받아 예측 쿼리를 작성해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="64f69-118">If you are new to data mining, get help building prediction queries from the **Query** wizard.</span></span>  
  
     <span data-ttu-id="64f69-119">고급 사용자는 끌어서 놓기 **고급 쿼리 편집기**를 사용하여 사용자 지정 DMX 쿼리를 작성하거나 Excel VBA를 사용하여 예측을 자동화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-119">Advanced users can build custom DMX queries with the drag-and-drop **Advanced Query Editor**, or automate predictions using Excel VBA.</span></span>  
  
-   <span data-ttu-id="64f69-120">**문서화하고 관리합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-120">**Document and manage.**</span></span> <span data-ttu-id="64f69-121">데이터 집합을 만들고 몇 가지 모델을 작성 한 후에는 데이터 및 모델 매개 변수에 대 한 통계 요약을 생성 하 여 작업 및 정보를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-121">After you've created a data set and built some models, document your work and your insights by generating a statistical summary of the data and model parameters.</span></span>  
  
-   <span data-ttu-id="64f69-122">**탐색하고 시각화합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-122">**Explore and visualize.**</span></span> <span data-ttu-id="64f69-123">데이터 마이닝은 완전히 자동화할 수 있는 활동이 아닙니다. 의미 있는 작업을 수행 하기 위해 결과를 탐색 하 고 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-123">Data mining is not an activity that can be fully automated - you need to explore and understand your results to take meaningful action.</span></span> <span data-ttu-id="64f69-124">추가 기능은 Excel의 대화형 뷰어, 모델 다이어그램을 사용자 지정할 수 있는 Visio 템플릿, 추가 필터링이나 수정을 위해 차트와 테이블을 Excel로 내보내는 기능을 제공하므로 탐색하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-124">The add-ins help you with exploration by providing interactive viewers in Excel, Visio templates that let you customize model diagrams, and the ability to export charts and tables to Excel for additional filtering or modification.</span></span>  
  
-   <span data-ttu-id="64f69-125">**배포하고 통합합니다.**</span><span class="sxs-lookup"><span data-stu-id="64f69-125">**Deploy and integrate.**</span></span> <span data-ttu-id="64f69-126">유용한 모델을 만든 경우 관리 도구를 사용 하 여 실험 서버에서 다른 인스턴스로 모델을 내보내 프로덕션에 모델을 배치 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-126">When you've created a useful model, put your model into production, by using the management tools to export the model from your experimental server to another instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="64f69-127">또는 모델을 만든 서버에 모델을 그대로 두되 학습 데이터를 새로 고치고 Integration Services 또는 DMX 스크립트를 사용하여 예측을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-127">You can also leave the model on the server where you created it, but refresh the training data and run predictions using Integration Services or DMX scripts.</span></span>  
  
     <span data-ttu-id="64f69-128">고급 사용자는 서버로 전송된 XMLA 및 DMX 문을 표시하는 **추적** 기능을 유용하게 여길 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-128">Power users will appreciate the **Trace** functionality, that lets you see the XMLA and DMX statements sent to the server.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="64f69-129">시작하기</span><span class="sxs-lookup"><span data-stu-id="64f69-129">Getting Started</span></span>  
 <span data-ttu-id="64f69-130">도구에 대해 알아보고 도구를 설정하려면 다음 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="64f69-130">See these topics to learn about the tools and to get set up:</span></span>  
  
-   [<span data-ttu-id="64f69-131">Excel 용 데이터 마이닝 클라이언트 &#40;SQL Server 데이터 마이닝 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="64f69-131">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [<span data-ttu-id="64f69-132">Excel용 테이블 분석 도구</span><span class="sxs-lookup"><span data-stu-id="64f69-132">Table Analysis Tools for Excel</span></span>](../table-analysis-tools-for-excel.md)  
  
-   [<span data-ttu-id="64f69-133">Visio용 데이터 마이닝 셰이프</span><span class="sxs-lookup"><span data-stu-id="64f69-133">Data Mining Shapes for Visio</span></span>](../data-mining-shapes-for-visio.md)  
  
-   [<span data-ttu-id="64f69-134">데이터 마이닝 서버에 연결</span><span class="sxs-lookup"><span data-stu-id="64f69-134">Connect to a Data Mining Server</span></span>](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a><span data-ttu-id="64f69-135">지원 및 요구 사항</span><span class="sxs-lookup"><span data-stu-id="64f69-135">Support and Requirements</span></span>  
 <span data-ttu-id="64f69-136">Office용 SQL Server 데이터 마이닝 추가 기능은 무료로 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-136">The SQL Server Data Mining Add-Ins for Office is a free download.</span></span> <span data-ttu-id="64f69-137">이러한 도구를 사용하려면 다음 Office 버전 중 하나가 이미 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-137">You must have one of the following versions of Office already installed to use these tools:</span></span>  
  
-   <span data-ttu-id="64f69-138">Office 2010, 32비트 또는 64비트 버전</span><span class="sxs-lookup"><span data-stu-id="64f69-138">Office 2010, 32-bit or 64-bit version</span></span>  
  
-   <span data-ttu-id="64f69-139">Office 2013, 32비트 또는 64비트 버전</span><span class="sxs-lookup"><span data-stu-id="64f69-139">Office 2013, 32-bit or 64-bit version</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="64f69-140">사용 중인 Excel 버전에 맞는 추가 기능 버전을 다운로드하십시오.</span><span class="sxs-lookup"><span data-stu-id="64f69-140">Be sure to download the version of the add-ins that matches your version of Excel.</span></span>  
  
 <span data-ttu-id="64f69-141">데이터 마이닝 추가 기능을 사용하려면 다음 SQL Server Analysis Services 버전 중 하나에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-141">The Data Mining Add-ins requires a connection to one of the following editions of SQL Server Analysis Services:</span></span>  
  
-   <span data-ttu-id="64f69-142">엔터프라이즈</span><span class="sxs-lookup"><span data-stu-id="64f69-142">Enterprise</span></span>  
  
-   <span data-ttu-id="64f69-143">비즈니스 인텔리전스</span><span class="sxs-lookup"><span data-stu-id="64f69-143">Business Intelligence</span></span>  
  
-   <span data-ttu-id="64f69-144">Standard</span><span class="sxs-lookup"><span data-stu-id="64f69-144">Standard</span></span>  
  
 <span data-ttu-id="64f69-145">연결하는 SQL Server Analysis Services의 버전에 따라 일부 고급 알고리즘을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64f69-145">Depending on the edition of SQL Server Analysis Services that you connect to, some of the advanced algorithms might not be available.</span></span> <span data-ttu-id="64f69-146">자세한 내용은 [SQL Server 2014 버전에서 지원하는 기능](https://msdn.microsoft.com/library/cc645993.aspx)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="64f69-146">For information, see [Features Supported by the Editions of SQL Server 2014](https://msdn.microsoft.com/library/cc645993.aspx).</span></span>  
  
 <span data-ttu-id="64f69-147">설치에 대 한 추가 도움말은 다운로드 센터에서 다음 페이지를 참조 하세요.[https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span><span class="sxs-lookup"><span data-stu-id="64f69-147">For additional help with installation, see this page on the Download Center: [https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)</span></span>  
  
  
