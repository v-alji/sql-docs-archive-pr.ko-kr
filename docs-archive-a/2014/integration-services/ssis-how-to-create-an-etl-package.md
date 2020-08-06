---
title: 'SSIS 자습서: 간단한 ETL 패키지 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 780b008052a2ff64aa75b2036aa7202128f95ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734319"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a><span data-ttu-id="2f979-102">SSIS 자습서: 간단한 ETL 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="2f979-102">SSIS Tutorial: Creating a Simple ETL Package</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="2f979-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS)는 데이터 웨어하우징에 대 한 ETL (추출, 변환 및 로드) 패키지를 비롯 하 여 고성능 데이터 통합 솔루션을 빌드하기 위한 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) is a platform for building high performance data integration solutions, including extraction, transformation, and load (ETL) packages for data warehousing.</span></span> <span data-ttu-id="2f979-104">SSIS에는 패키지를 빌드하고 디버깅하기 위한 그래픽 도구 및 마법사, FTP 작업과 같은 워크플로 함수를 수행하고 SQL 문을 실행하며 전자 메일 메시지를 보내기 위한 태스크, 데이터 추출 및 로드를 위한 데이터 원본과 대상, 데이터 삭제, 집계, 병합 및 복사를 위한 변환, 패키지 실행 및 스토리지를 관리하기 위한 관리 서비스인 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 서비스, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델 프로그래밍을 위한 API(응용 프로그래밍 인터페이스)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-104">SSIS includes graphical tools and wizards for building and debugging packages; tasks for performing workflow functions such as FTP operations, executing SQL statements, and sending e-mail messages; data sources and destinations for extracting and loading data; transformations for cleaning, aggregating, merging, and copying data; a management service, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for administering package execution and storage; and application programming interfaces (APIs) for programming the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="2f979-105">이 자습서에서는 디자이너를 사용 하 여 간단한 패키지를 만드는 방법에 대해 설명 [!INCLUDE[ssIS](../includes/ssis-md.md)] [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-105">In this tutorial, you will learn how to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="2f979-106">사용자가 만든 패키지는 플랫 파일로부터 데이터를 가져와서 데이터 형식을 바꾼 다음 바뀐 데이터를 팩트 테이블에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-106">The package that you create takes data from a flat file, reformats the data, and then inserts the reformatted data into a fact table.</span></span> <span data-ttu-id="2f979-107">다음 단원에서는 패키지를 확장하여 루핑, 패키지 구성, 로깅 및 오류 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-107">In following lessons, the package is expanded to demonstrate looping, package configurations, logging and error flow.</span></span>  
  
 <span data-ttu-id="2f979-108">자습서에서 사용하는 예제 데이터를 설치하면 자습서의 각 단원에서 만들 패키지의 완성된 버전도 함께 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-108">When you install the sample data that the tutorial uses, you also install the completed versions of the packages that you will create in each lesson of the tutorial.</span></span> <span data-ttu-id="2f979-109">원하는 경우 단원을 건너뛰고 완성된 패키지를 사용하여 이후 단원에서 자습서를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-109">By using the completed packages, you can skip ahead and begin the tutorial at a later lesson if you like.</span></span> <span data-ttu-id="2f979-110">패키지 또는 새 개발 환경 작업을 처음으로 수행하는 경우에는 1단원부터 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-110">If this is your first time working with packages or the new development environment, we recommend that you begin with Lesson1.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="2f979-111">학습 내용</span><span class="sxs-lookup"><span data-stu-id="2f979-111">What You Will Learn</span></span>  
 <span data-ttu-id="2f979-112">에서 사용할 수 있는 새 도구, 컨트롤 및 기능에 익숙해지는 가장 좋은 방법은 이러한 도구를 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-112">The best way to become acquainted with the new tools, controls and features available in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to use them.</span></span> <span data-ttu-id="2f979-113">이 자습서에서는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 루핑, 구성, 오류 흐름 논리 및 로깅을 포함하는 간단한 ETL 패키지를 만드는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-113">This tutorial walks you through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple ETL package that includes looping, configurations, error flow logic and logging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f979-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2f979-114">Requirements</span></span>  
 <span data-ttu-id="2f979-115">이 자습서는 기본적인 데이터베이스 작업에 익숙한 사용자를 대상으로 하지만에서 제공 되는 새로운 기능에 대 한 노출을 제한적입니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2f979-115">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to the new features available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2f979-116">이 자습서를 사용하려면 시스템에 다음 구성 요소가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-116">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="2f979-117">**AdventureWorksDW2012** 데이터베이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-117">with the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="2f979-118">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-118">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="2f979-119">**AdventureWorksDW2012** 데이터베이스를 다운로드하려면 [SQL Server 2012용 Adventure Works](https://go.microsoft.com/fwlink/?LinkId=275026)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f979-119">To download the **AdventureWorksDW2012** database, see [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2f979-120">데이터베이스(\*.mdf 파일)에 연결할 때 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에서 기본적으로 .ldf 파일을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-120">When you attach the database (\*.mdf file), [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] will by default search for an .ldf file.</span></span> <span data-ttu-id="2f979-121">**데이터베이스 연결** 대화 상자에서 확인을 클릭하기 전에 .ldf 파일을 수동으로 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-121">You must manually remove the .ldf file before clicking OK in the **Attach Databases** dialog box.</span></span>  
    >   
    >  <span data-ttu-id="2f979-122">데이터베이스 연결에 대한 자세한 내용은 [Attach a Database](../relational-databases/databases/attach-a-database.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2f979-122">For more information about attaching databases, see [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
-   <span data-ttu-id="2f979-123">데이터 샘플링</span><span class="sxs-lookup"><span data-stu-id="2f979-123">Sample data.</span></span> <span data-ttu-id="2f979-124">예제 데이터는 [!INCLUDE[ssIS](../includes/ssis-md.md)] 단원 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-124">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="2f979-125">예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-125">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="2f979-126">[Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-126">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="2f979-127">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-127">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="2f979-128">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-128">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="2f979-129">이 자습서의 단원</span><span class="sxs-lookup"><span data-stu-id="2f979-129">Lessons in This Tutorial</span></span>  
 [<span data-ttu-id="2f979-130">1단원: 프로젝트 및 기본 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="2f979-130">Lesson 1: Creating the Project and Basic Package</span></span>](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 <span data-ttu-id="2f979-131">이 단원에서는 단일 플랫 파일에서 데이터를 추출하고, 조회 변환을 사용하여 데이터를 변환하고, 마지막으로 결과를 팩트 테이블 대상에 로드하는 간단한 ETL 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-131">In this lesson, you will create a simple ETL package that extracts data from a single flat file, transforms the data using lookup transformations and finally loads the result into a fact table destination.</span></span>  
  
 [<span data-ttu-id="2f979-132">2단원: 루핑 추가</span><span class="sxs-lookup"><span data-stu-id="2f979-132">Lesson 2: Adding Looping</span></span>](lesson-2-adding-looping-with-ssis.md)  
 <span data-ttu-id="2f979-133">이 단원에서는 1단원에서 만든 패키지를 확장하여 새 루핑 기능을 활용함으로써 여러 플랫 파일을 단일 데이터 흐름 프로세스로 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-133">In this lesson, you will expand the package you created in Lesson 1 to take advantage of new looping features to extract multiple flat files into a single data flow process.</span></span>  
  
 [<span data-ttu-id="2f979-134">3단원: 로깅 추가</span><span class="sxs-lookup"><span data-stu-id="2f979-134">Lesson 3: Adding Logging</span></span>](lesson-3-add-logging-with-ssis.md)  
 <span data-ttu-id="2f979-135">이 단원에서는 2단원에서 만든 패키지를 확장하여 새 로깅 기능을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-135">In this lesson, you will expand the package you created in Lesson 2 to take advantage of new logging features.</span></span>  
  
 [<span data-ttu-id="2f979-136">4단원: 오류 Flow 리디렉션 추가</span><span class="sxs-lookup"><span data-stu-id="2f979-136">Lesson 4: Adding Error Flow Redirection</span></span>](lesson-4-add-error-flow-redirection-with-ssis.md)  
 <span data-ttu-id="2f979-137">이 단원에서는 3단원에서 만든 패키지를 확장하여 새 오류 출력 구성을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-137">In this lesson, you will expand the package you created in lesson 3 to take advantage of new error output configurations.</span></span>  
  
 [<span data-ttu-id="2f979-138">5단원: 패키지 배포 모델을 위한 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="2f979-138">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 <span data-ttu-id="2f979-139">이 단원에서는 4단원에서 만든 패키지를 확장하여 새 패키지 구성 옵션을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-139">In this lesson, you will expand the package you created in Lesson 4 to take advantage of new package configuration options.</span></span>  
  
 [<span data-ttu-id="2f979-140">6단원: 프로젝트 배포 모델에 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="2f979-140">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 <span data-ttu-id="2f979-141">이 단원에서는 5단원에서 만든 패키지를 확장하여 프로젝트 배포 모델에서 새 매개 변수 사용을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f979-141">In this lesson, you will expand the package you created in Lesson 5 to take advantage of using new parameters with the project deployment model.</span></span>  
  
  
