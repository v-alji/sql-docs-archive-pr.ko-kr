---
title: 데이터 프로파일링 태스크 및 뷰어 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], about data profiling
- data profiling
- profiling data
ms.assetid: 756840e3-aa09-45cd-9951-1a17af4b5925
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae15d1cc75f8db04c36a830e44d07800c5aecf75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649627"
---
# <a name="data-profiling-task-and-viewer"></a><span data-ttu-id="728ca-102">데이터 프로파일링 태스크 및 뷰어</span><span class="sxs-lookup"><span data-stu-id="728ca-102">Data Profiling Task and Viewer</span></span>
  <span data-ttu-id="728ca-103">데이터 프로파일링 태스크는 데이터 추출, 변환 및 로드 프로세스 내에서 데이터 프로파일링 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-103">The Data Profiling task provides data profiling functionality inside the process of extracting, transforming, and loading data.</span></span> <span data-ttu-id="728ca-104">데이터 프로파일링 태스크를 사용하면 다음과 같은 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-104">By using the Data Profiling task, you can achieve the following benefits:</span></span>  
  
-   <span data-ttu-id="728ca-105">보다 효과적으로 원본 데이터 분석</span><span class="sxs-lookup"><span data-stu-id="728ca-105">Analyze the source data more effectively</span></span>  
  
-   <span data-ttu-id="728ca-106">원본 데이터에 대한 이해도 향상</span><span class="sxs-lookup"><span data-stu-id="728ca-106">Understand the source data better</span></span>  
  
-   <span data-ttu-id="728ca-107">데이터 웨어하우스에 노출되기 전에 데이터 품질 문제 방지</span><span class="sxs-lookup"><span data-stu-id="728ca-107">Prevent data quality problems before they are introduced into the data warehouse.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="728ca-108">데이터 프로파일링 태스크는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 저장된 데이터만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-108">The Data Profiling task works only with data that is stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="728ca-109">이 태스크는 타사 또는 파일 기반 데이터 원본을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-109">It does not work with third-party or file-based data sources.</span></span>  
  
## <a name="data-profiling-overview"></a><span data-ttu-id="728ca-110">데이터 프로파일링 개요</span><span class="sxs-lookup"><span data-stu-id="728ca-110">Data Profiling Overview</span></span>  
 <span data-ttu-id="728ca-111">데이터 품질은 모든 비즈니스에서 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-111">Data quality is important to every business.</span></span> <span data-ttu-id="728ca-112">기업에서는 분석 및 비즈니스 인텔리전스 시스템을 자체 트랜잭션 시스템 위에 빌드하므로 핵심 성과 지표 및 데이터 마이닝 예측의 안정성은 기반으로 하고 있는 데이터의 유효성에 따라 전적으로 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-112">As enterprises build analytical and business intelligence systems on top of their transactional systems, the reliability of key performance indicators and of data mining predictions depends completely on the validity of the data on which they are based.</span></span> <span data-ttu-id="728ca-113">비즈니스 의사 결정에서 유효한 데이터의 중요성이 증가하고 있지만 이러한 데이터의 유효성을 확인하는 문제의 중요성 또한 증가하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-113">But although the importance of valid data for business decision-making is increasing, the challenge of making sure of this data's validity is also increasing.</span></span> <span data-ttu-id="728ca-114">데이터는 실로 다양한 시스템 및 출처와 많은 사용자로부터 기업으로 계속 흘러 들어오고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-114">Data is streaming into the enterprise constantly from diverse systems and sources, and a large numbers of users.</span></span>  
  
 <span data-ttu-id="728ca-115">데이터 품질의 메트릭은 특정 도메인이나 애플리케이션과 관련되어 있으므로 정의하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-115">Metrics for data quality can be difficult to define because they are specific to the domain or the application.</span></span> <span data-ttu-id="728ca-116">데이터 품질을 정의하는 일반적인 방법 중 하나가 데이터 프로파일링입니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-116">One common approach to defining data quality is data profiling.</span></span>  
  
 <span data-ttu-id="728ca-117">데이터 프로필은 다음을 포함할 수 있는 데이터에 대한 집계 통계 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-117">A data profile is a collection of aggregate statistics about data that might include the following:</span></span>  
  
-   <span data-ttu-id="728ca-118">Customer 테이블의 행 수</span><span class="sxs-lookup"><span data-stu-id="728ca-118">The number of rows in the Customer table.</span></span>  
  
-   <span data-ttu-id="728ca-119">State 열의 고유 값 수</span><span class="sxs-lookup"><span data-stu-id="728ca-119">The number of distinct values in the State column.</span></span>  
  
-   <span data-ttu-id="728ca-120">Zip 열의 Null 값 또는 누락된 값 수</span><span class="sxs-lookup"><span data-stu-id="728ca-120">The number of null or missing values in the Zip column.</span></span>  
  
-   <span data-ttu-id="728ca-121">City 열의 값 분포</span><span class="sxs-lookup"><span data-stu-id="728ca-121">The distribution of values in the City column.</span></span>  
  
-   <span data-ttu-id="728ca-122">State 열의 Zip 열에 대한 함수 종속성 수준(즉, 시/도는 지정된 우편 번호 값에 대해 항상 같아야 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-122">The strength of the functional dependency of the State column on the Zip column-that is, the state should always be the same for a given zip value.</span></span>  
  
 <span data-ttu-id="728ca-123">데이터 프로필이 제공하는 통계를 통해 원본 데이터를 사용하여 발생할 수 있는 품질 문제를 효과적으로 최소화하기 위해 필요한 정보를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-123">The statistics that a data profile provides gives you the information that you need in order to effectively minimize the quality issues that might occur from using the source data.</span></span>  
  
## <a name="integration-services-and-data-profiling"></a><span data-ttu-id="728ca-124">Integration Services 및 데이터 프로파일링</span><span class="sxs-lookup"><span data-stu-id="728ca-124">Integration Services and Data Profiling</span></span>  
 <span data-ttu-id="728ca-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 데이터 프로파일링 프로세스는 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-125">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], the data profiling process consist of the following steps:</span></span>  
  
 <span data-ttu-id="728ca-126">**1단계: 데이터 프로파일링 태스크 설정**</span><span class="sxs-lookup"><span data-stu-id="728ca-126">**Step 1: Setting up the Data Profiling Task**</span></span>  
 <span data-ttu-id="728ca-127">데이터 프로파일링 태스크는 컴퓨팅하려는 프로필을 구성하기 위해 사용하는 태스크입니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-127">The Data Profiling task is a task that you use to configure the profiles that you want to compute.</span></span> <span data-ttu-id="728ca-128">데이터 프로파일링 태스크를 포함하는 패키지를 실행하여 프로필을 컴퓨팅합니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-128">You then run the package that contains the Data Profiling task to compute the profiles.</span></span> <span data-ttu-id="728ca-129">이 태스크는 프로필 출력을 XML 형식으로 파일이나 패키지 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-129">The task saves the profile output in XML format to a file or a package variable.</span></span>  
  
 <span data-ttu-id="728ca-130">**자세한 내용은 다음을 참조하세요.** [데이터 프로파일링 태스크 설정](data-profiling-task.md)</span><span class="sxs-lookup"><span data-stu-id="728ca-130">**For more information:** [Setup of the Data Profiling Task](data-profiling-task.md)</span></span>  
  
 <span data-ttu-id="728ca-131">**2단계: 데이터 프로파일링 태스크가 계산하는 프로필 검토**</span><span class="sxs-lookup"><span data-stu-id="728ca-131">**Step 2: Reviewing the Profiles that the Data Profiling Task Computes**</span></span>  
 <span data-ttu-id="728ca-132">데이터 프로파일링 태스크가 계산하는 데이터 프로필을 보려면 출력을 파일로 보낸 다음 데이터 프로필 뷰어를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-132">To view the data profiles that the Data Profiling task computes, you send the output to a file, and then you use the Data Profile Viewer.</span></span> <span data-ttu-id="728ca-133">이 뷰어는 선택적 드릴다운 기능과 함께 요약 및 세부 정보 형식으로 프로필 출력을 표시하는 독립 실행형 유틸리티입니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-133">This viewer is a stand-alone utility that displays the profile output in both summary and detail format with optional drilldown capability.</span></span>  
  
 <span data-ttu-id="728ca-134">**자세한 내용은 다음을 참조하세요.** [데이터 프로필 뷰어](data-profile-viewer.md)</span><span class="sxs-lookup"><span data-stu-id="728ca-134">**For more information:** [Data Profile Viewer](data-profile-viewer.md)</span></span>  
  
### <a name="addition-of-conditional-logic-to-the-data-profiling-workflow"></a><span data-ttu-id="728ca-135">데이터 프로파일링 워크플로에 조건부 논리 추가</span><span class="sxs-lookup"><span data-stu-id="728ca-135">Addition of Conditional Logic to the Data Profiling Workflow</span></span>  
 <span data-ttu-id="728ca-136">데이터 프로파일링 태스크에는 조건부 논리를 사용하여 프로필 출력에 따라 해당 태스크를 다운스트림 태스크에 연결할 수 있는 기본 제공 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-136">The Data Profiling task does not have built-in features that allow you to use conditional logic to connect this task to downstream tasks based on the profile output.</span></span> <span data-ttu-id="728ca-137">그러나 스크립트 태스크에서 약간의 프로그래밍 작업을 수행하여 이 논리를 손쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-137">However, you can easily add this logic, with a small amount of programming, in a Script task.</span></span> <span data-ttu-id="728ca-138">예를 들어 스크립트 태스크는 데이터 프로파일링 태스크의 출력 파일에 대해 XPath 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-138">For example, the Script task could perform an XPath query against the output file of the Data Profiling task.</span></span> <span data-ttu-id="728ca-139">이 쿼리에서는 특정 열의 Null 값 비율이 특정 임계값을 초과하는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-139">The query could determine whether the percentage of null values in a particular column exceeds a certain threshold.</span></span> <span data-ttu-id="728ca-140">해당 비율이 임계값을 초과하는 경우 패키지를 중단하고 원본 데이터에서 문제를 해결한 다음 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="728ca-140">If the percentage exceeds the threshold, you could interrupt the package and resolve the problem in the source data before continuing.</span></span> <span data-ttu-id="728ca-141">자세한 내용은 [패키지 워크플로에 데이터 프로파일링 태스크 포함](incorporate-a-data-profiling-task-in-package-workflow.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="728ca-141">For more information, see [Incorporate a Data Profiling Task in Package Workflow](incorporate-a-data-profiling-task-in-package-workflow.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="728ca-142">관련 내용</span><span class="sxs-lookup"><span data-stu-id="728ca-142">Related Content</span></span>  
 [<span data-ttu-id="728ca-143">데이터 프로파일러 스키마</span><span class="sxs-lookup"><span data-stu-id="728ca-143">Data Profiler Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=251524)  
  
  
