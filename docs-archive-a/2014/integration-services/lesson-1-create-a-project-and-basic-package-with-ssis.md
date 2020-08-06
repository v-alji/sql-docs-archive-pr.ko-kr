---
title: '1 단원: 프로젝트 및 기본 패키지 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a9ddc36ef242cc4e4b146e90dfa9de470e68d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651118"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a><span data-ttu-id="bd4b4-102">1단원: 프로젝트 및 기본 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="bd4b4-102">Lesson 1: Creating the Project and Basic Package</span></span>
  <span data-ttu-id="bd4b4-103">이 단원에서는 하나의 플랫 파일 원본에서 데이터를 추출하고 두 개의 조회 변환 구성 요소를 사용하여 데이터를 변환하며 **AdventureWorksDW2012** 의 **FactCurrency**팩트 테이블에 해당 데이터를 쓰는 간단한 ETL 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-103">In this lesson, you will create a simple ETL package that extracts data from a single flat file source, transforms the data using two lookup transformation components, and writes that data to the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span> <span data-ttu-id="bd4b4-104">이 단원에서는 새로운 패키지를 만들고 데이터 원본 및 대상 연결을 추가하고 구성하며 새로운 제어 흐름 및 데이터 흐름 구성 요소를 사용하여 작업하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-104">As part of this lesson, you will learn how to create new packages, add and configure data source and destination connections, and work with new control flow and data flow components.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd4b4-105">이 자습서를 실행하려면 **AdventureWorksDW2012** 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-105">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="bd4b4-106">**AdventureWorksDW2012**설치 및 배포에 대 한 자세한 내용은 [Microsoft SQL Server 제품 샘플: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-106">For more information on installing and deploying **AdventureWorksDW2012**, see [Microsoft SQL Server Product Samples: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).</span></span>  
  
## <a name="understanding-the-package-requirements"></a><span data-ttu-id="bd4b4-107">패키지 요구 사항 이해</span><span class="sxs-lookup"><span data-stu-id="bd4b4-107">Understanding the Package Requirements</span></span>  
 <span data-ttu-id="bd4b4-108">이 자습서를 사용하려면 Microsoft SQL Server Data Tools가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
  
 <span data-ttu-id="bd4b4-109">SQL Server Data Tools 설치 방법에 대한 자세한 내용은 [SQL Server Data Tools 다운로드](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).</span></span>  
  
 <span data-ttu-id="bd4b4-110">패키지를 만들기 전에 원본 데이터와 대상 양쪽에 사용되는 형식을 제대로 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-110">Before creating a package, you need a good understanding of the formatting used in both the source data and the destination.</span></span> <span data-ttu-id="bd4b4-111">이러한 데이터 형식을 모두 파악하면 원본 데이터를 대상에 매핑하는 데 필요한 변환을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-111">Once you understand both of these data formats, you will be ready to define the transformations necessary to map the source data to the destination.</span></span>  
  
### <a name="looking-at-the-source"></a><span data-ttu-id="bd4b4-112">원본 확인</span><span class="sxs-lookup"><span data-stu-id="bd4b4-112">Looking at the Source</span></span>  
 <span data-ttu-id="bd4b4-113">이 자습서에서 원본 데이터는 플랫 파일인 SampleCurrencyData.txt에 포함된 기록 통화 데이터 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-113">For this tutorial, the source data is a set of historical currency data contained in the flat file, SampleCurrencyData.txt.</span></span> <span data-ttu-id="bd4b4-114">원본 데이터에는 평균 통화 비율, 통화 키, 날짜 키, 날짜별 마지막 비율이라는 4개의 열이 있습니다</span><span class="sxs-lookup"><span data-stu-id="bd4b4-114">The source data has the following four columns: the average rate of the currency, a currency key, a date key, and the end-of-day rate.</span></span>  
  
 <span data-ttu-id="bd4b4-115">다음은 SampleCurrencyData.txt 파일에 포함된 원본 데이터의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-115">Here is an example of the source data contained in the SampleCurrencyData.txt file:</span></span>  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 <span data-ttu-id="bd4b4-116">플랫 파일 원본 데이터를 사용하여 작업할 때는 플랫 파일 연결 관리자가 플랫 파일 데이터를 해석하는 방법을 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-116">When working with flat file source data, it is important to understand how the Flat File connection manager interprets the flat file data.</span></span> <span data-ttu-id="bd4b4-117">플랫 파일 원본이 유니코드일 경우 플랫 파일 연결 관리자가 모든 열을 기본 열 너비 50인 [DT_WSTR]로 정의하고</span><span class="sxs-lookup"><span data-stu-id="bd4b4-117">If the flat file source is Unicode, the Flat File connection manager defines all columns as [DT_WSTR] with a default column width of 50.</span></span> <span data-ttu-id="bd4b4-118">플랫 파일 원본이 ANSI로 인코딩된 경우 열 너비 50인 [DT_STR]로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-118">If the flat file source is ANSI-encoded, the columns are defined as [DT_STR] with a column width of 50.</span></span> <span data-ttu-id="bd4b4-119">이 기본값을 변경하여 문자열을 데이터에 알맞은 열 유형으로 만들어야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-119">You will probably have to change these defaults to make the string column types more appropriate for your data.</span></span> <span data-ttu-id="bd4b4-120">이렇게 하려면 데이터가 쓰여지는 대상의 데이터 형식을 확인한 다음 플랫 파일 연결 관리자에서 알맞은 형식을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-120">To do this, you will need to look at the data type of the destination where the data will be written to and then choose the correct type within the Flat File connection manager.</span></span>  
  
### <a name="looking-at-the-destination"></a><span data-ttu-id="bd4b4-121">대상 확인</span><span class="sxs-lookup"><span data-stu-id="bd4b4-121">Looking at the Destination</span></span>  
 <span data-ttu-id="bd4b4-122">원본 데이터의 궁극적인 대상은 **AdventureWorksDW** 의 **FactCurrency**팩트 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-122">The ultimate destination for the source data is the **FactCurrency** fact table in **AdventureWorksDW**.</span></span> <span data-ttu-id="bd4b4-123">다음 표와 같이 **FactCurrency** 팩트 테이블에는 4개의 열이 있으며 두 차원 테이블에 대한 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-123">The **FactCurrency** fact table has four columns, and has relationships to two dimension tables, as shown in the following table.</span></span>  
  
|<span data-ttu-id="bd4b4-124">열 이름</span><span class="sxs-lookup"><span data-stu-id="bd4b4-124">Column Name</span></span>|<span data-ttu-id="bd4b4-125">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="bd4b4-125">Data Type</span></span>|<span data-ttu-id="bd4b4-126">조회 테이블</span><span class="sxs-lookup"><span data-stu-id="bd4b4-126">Lookup Table</span></span>|<span data-ttu-id="bd4b4-127">조회 열</span><span class="sxs-lookup"><span data-stu-id="bd4b4-127">Lookup Column</span></span>|  
|-----------------|---------------|------------------|-------------------|  
|<span data-ttu-id="bd4b4-128">AverageRate</span><span class="sxs-lookup"><span data-stu-id="bd4b4-128">AverageRate</span></span>|<span data-ttu-id="bd4b4-129">float</span><span class="sxs-lookup"><span data-stu-id="bd4b4-129">float</span></span>|<span data-ttu-id="bd4b4-130">없음</span><span class="sxs-lookup"><span data-stu-id="bd4b4-130">None</span></span>|<span data-ttu-id="bd4b4-131">없음</span><span class="sxs-lookup"><span data-stu-id="bd4b4-131">None</span></span>|  
|<span data-ttu-id="bd4b4-132">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="bd4b4-132">CurrencyKey</span></span>|<span data-ttu-id="bd4b4-133">int(FK)</span><span class="sxs-lookup"><span data-stu-id="bd4b4-133">int (FK)</span></span>|<span data-ttu-id="bd4b4-134">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="bd4b4-134">DimCurrency</span></span>|<span data-ttu-id="bd4b4-135">CurrencyKey(PK)</span><span class="sxs-lookup"><span data-stu-id="bd4b4-135">CurrencyKey (PK)</span></span>|  
|<span data-ttu-id="bd4b4-136">DateKey</span><span class="sxs-lookup"><span data-stu-id="bd4b4-136">DateKey</span></span>|<span data-ttu-id="bd4b4-137">int(FK)</span><span class="sxs-lookup"><span data-stu-id="bd4b4-137">Int (FK)</span></span>|<span data-ttu-id="bd4b4-138">FactOnlineSales</span><span class="sxs-lookup"><span data-stu-id="bd4b4-138">DimDate</span></span>|<span data-ttu-id="bd4b4-139">DateKey (PK)</span><span class="sxs-lookup"><span data-stu-id="bd4b4-139">DateKey (PK)</span></span>|  
|<span data-ttu-id="bd4b4-140">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="bd4b4-140">EndOfDayRate</span></span>|<span data-ttu-id="bd4b4-141">float</span><span class="sxs-lookup"><span data-stu-id="bd4b4-141">float</span></span>|<span data-ttu-id="bd4b4-142">없음</span><span class="sxs-lookup"><span data-stu-id="bd4b4-142">None</span></span>|<span data-ttu-id="bd4b4-143">없음</span><span class="sxs-lookup"><span data-stu-id="bd4b4-143">None</span></span>|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a><span data-ttu-id="bd4b4-144">대상과 호환될 원본 데이터 매핑</span><span class="sxs-lookup"><span data-stu-id="bd4b4-144">Mapping Source Data to be Compatible with the Destination</span></span>  
 <span data-ttu-id="bd4b4-145">원본 및 대상 데이터 형식을 분석하면 **CurrencyKey** 와 **DateKey** 값을 조회해야 한다는 사실을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-145">Analysis of the source and destination data formats indicates that lookups will be necessary for the **CurrencyKey** and **DateKey** values.</span></span> <span data-ttu-id="bd4b4-146">이러한 조회를 수행할 변환은 **DimCurrency** 및 **DimDate** 차원 테이블의 대체 키를 사용하여 **CurrencyKey** 및 **DateKey** 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-146">The transformations that will perform these lookups will obtain the **CurrencyKey** and **DateKey** values by using the alternate keys from **DimCurrency** and **DimDate** dimension tables.</span></span>  
  
|<span data-ttu-id="bd4b4-147">플랫 파일 열</span><span class="sxs-lookup"><span data-stu-id="bd4b4-147">Flat File Column</span></span>|<span data-ttu-id="bd4b4-148">테이블 이름</span><span class="sxs-lookup"><span data-stu-id="bd4b4-148">Table Name</span></span>|<span data-ttu-id="bd4b4-149">열 이름</span><span class="sxs-lookup"><span data-stu-id="bd4b4-149">Column Name</span></span>|<span data-ttu-id="bd4b4-150">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="bd4b4-150">Data Type</span></span>|  
|----------------------|----------------|-----------------|---------------|  
|<span data-ttu-id="bd4b4-151">0</span><span class="sxs-lookup"><span data-stu-id="bd4b4-151">0</span></span>|<span data-ttu-id="bd4b4-152">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="bd4b4-152">FactCurrency</span></span>|<span data-ttu-id="bd4b4-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="bd4b4-153">AverageRate</span></span>|<span data-ttu-id="bd4b4-154">float</span><span class="sxs-lookup"><span data-stu-id="bd4b4-154">float</span></span>|  
|<span data-ttu-id="bd4b4-155">1</span><span class="sxs-lookup"><span data-stu-id="bd4b4-155">1</span></span>|<span data-ttu-id="bd4b4-156">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="bd4b4-156">DimCurrency</span></span>|<span data-ttu-id="bd4b4-157">CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="bd4b4-157">CurrencyAlternateKey</span></span>|<span data-ttu-id="bd4b4-158">nchar (3)</span><span class="sxs-lookup"><span data-stu-id="bd4b4-158">nchar (3)</span></span>|  
|<span data-ttu-id="bd4b4-159">2</span><span class="sxs-lookup"><span data-stu-id="bd4b4-159">2</span></span>|<span data-ttu-id="bd4b4-160">FactOnlineSales</span><span class="sxs-lookup"><span data-stu-id="bd4b4-160">DimDate</span></span>|<span data-ttu-id="bd4b4-161">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="bd4b4-161">FullDateAlternateKey</span></span>|<span data-ttu-id="bd4b4-162">date</span><span class="sxs-lookup"><span data-stu-id="bd4b4-162">date</span></span>|  
|<span data-ttu-id="bd4b4-163">3</span><span class="sxs-lookup"><span data-stu-id="bd4b4-163">3</span></span>|<span data-ttu-id="bd4b4-164">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="bd4b4-164">FactCurrency</span></span>|<span data-ttu-id="bd4b4-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="bd4b4-165">EndOfDayRate</span></span>|<span data-ttu-id="bd4b4-166">float</span><span class="sxs-lookup"><span data-stu-id="bd4b4-166">float</span></span>|  
  
## <a name="lesson-tasks"></a><span data-ttu-id="bd4b4-167">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="bd4b4-167">Lesson Tasks</span></span>  
 <span data-ttu-id="bd4b4-168">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="bd4b4-168">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="bd4b4-169">1단계: 새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="bd4b4-169">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="bd4b4-170">2단계: 플랫 파일 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bd4b4-170">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="bd4b4-171">3단계: OLE DB 연결 관리자 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bd4b4-171">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="bd4b4-172">4단계: 패키지에 Data Flow Task 추가</span><span class="sxs-lookup"><span data-stu-id="bd4b4-172">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [<span data-ttu-id="bd4b4-173">5단계: 플랫 파일 원본 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bd4b4-173">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [<span data-ttu-id="bd4b4-174">6단계: 조회 변환 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bd4b4-174">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [<span data-ttu-id="bd4b4-175">7단계: OLE DB 대상 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bd4b4-175">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [<span data-ttu-id="bd4b4-176">8단계: 1단원 패키지를 쉽게 이해할 수 있도록 만들기</span><span class="sxs-lookup"><span data-stu-id="bd4b4-176">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [<span data-ttu-id="bd4b4-177">9단계: 1단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="bd4b4-177">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="bd4b4-178">단원 시작</span><span class="sxs-lookup"><span data-stu-id="bd4b4-178">Start the Lesson</span></span>  
 [<span data-ttu-id="bd4b4-179">1단계: 새 Integration Services 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="bd4b4-179">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
