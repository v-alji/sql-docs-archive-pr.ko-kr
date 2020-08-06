---
title: 데이터 마이닝 솔루션 | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
- data mining [Analysis Services], development
ms.assetid: 84f6548d-ebb0-4e10-9b29-66253fa0a04a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0ab4b5ddcc9958fa36d6c8ecae0e7fd79585b4fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649840"
---
# <a name="data-mining-solutions"></a><span data-ttu-id="d54ce-102">데이터 마이닝 솔루션</span><span class="sxs-lookup"><span data-stu-id="d54ce-102">Data Mining Solutions</span></span>
  <span data-ttu-id="d54ce-103">데이터 마이닝 솔루션은 하나 이상의 데이터 마이닝 프로젝트가 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-103">A data mining solution is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution that contains one or more data mining projects.</span></span>  
  
 <span data-ttu-id="d54ce-104">이 섹션의 항목에서는를 사용 하 여 통합 데이터 마이닝 솔루션을 디자인 하 고 구현 하는 방법에 대 한 정보를 제공 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-104">The topics in this section provide information about how to design and implement an integrated data mining solution by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="d54ce-105">데이터 마이닝 디자인 프로세스와 관련 도구에 대한 개요는 [Data Mining Concepts](data-mining-concepts.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d54ce-105">For an overview of the data mining design process and related tools, see [Data Mining Concepts](data-mining-concepts.md).</span></span>  
  
 <span data-ttu-id="d54ce-106">데이터 마이닝에 유용한 추가 프로젝트 형식에 대한 자세한 내용은 [데이터 마이닝 솔루션 관련 프로젝트](data-mining-solutions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d54ce-106">For more information about additional projects types that are useful for data mining, see [Related Projects for Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
 [<span data-ttu-id="d54ce-107">관계형 마이닝 모델과 다차원 솔루션</span><span class="sxs-lookup"><span data-stu-id="d54ce-107">Relational vs. Multidimensional Solutions</span></span>](#bkmk_RelMD)  
  
 [<span data-ttu-id="d54ce-108">데이터 마이닝 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="d54ce-108">Deploying Data Mining Solutions</span></span>](#bkmk_Deploy)  
  
 [<span data-ttu-id="d54ce-109">솔루션 연습</span><span class="sxs-lookup"><span data-stu-id="d54ce-109">Solution Walkthroughs</span></span>](#bkmk_Walkthru)  
  
##  <a name="relational-vs-multidimensional-solutions"></a><a name="bkmk_RelMD"></a><span data-ttu-id="d54ce-110">관계형 솔루션 및 다차원 솔루션</span><span class="sxs-lookup"><span data-stu-id="d54ce-110">Relational vs. Multidimensional Solutions</span></span>  
 <span data-ttu-id="d54ce-111">데이터 마이닝 솔루션은 다차원 데이터 (즉, 기존 큐브) 또는 순수 관계형 데이터 (예: 데이터 웨어하우스의 테이블 및 뷰) 또는 텍스트 파일, Excel 통합 문서 또는 기타 외부 데이터 원본 중 하나를 기반으로 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-111">A data mining solution can be based either on multidimensional data-that is, an existing cube-or on purely relational data, such as the tables and views in a data warehouse, or on text files, Excel workbooks, or other external data sources.</span></span>  
  
-   <span data-ttu-id="d54ce-112">기존 다차원 데이터베이스 솔루션 내에 데이터 마이닝 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-112">You can create data mining objects within an existing multidimensional database solution.</span></span>  
  
     <span data-ttu-id="d54ce-113">일반적으로 이미 만든 큐브를 데이터 원본으로 사용하여 데이터 마이닝을 수행하려는 경우에 이와 같은 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-113">Typically you would create a solution like this if you have already created a cube and want to perform data mining by using the cube as a data source.</span></span> <span data-ttu-id="d54ce-114">큐브를 기반으로 하는 모델을 이동 및 백업할 때는 큐브도 이동하거나 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-114">When you move and backup models based on a cube, the cube must also be moved or copied.</span></span>  
  
-   <span data-ttu-id="d54ce-115">데이터 마이닝 개체(지원되는 데이터 원본 및 데이터 원본 뷰 포함)만 포함하고 관계형 데이터 원본만 사용하는 데이터 마이닝 솔루션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-115">You can create a data mining solution that contains only data mining objects, including the supporting data sources and data source views, and that uses relational data source only.</span></span>  
  
     <span data-ttu-id="d54ce-116">이는 일반적으로 관계형 데이터 원본에 대해 처리 및 쿼리가 가장 빠르기 때문에 데이터 마이닝 모델을 만들 때 가장 선호되는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-116">This is the preferred method for creating data mining models, as processing and querying is generally fastest against relational data sources.</span></span> <span data-ttu-id="d54ce-117">또한 EXPORT 및 IMPORT 명령을 사용하여 서버 간에 모델을 쉽게 이동 및 백업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-117">You can also easily move and backup models between servers by using the EXPORT and IMPORT commands.</span></span>  
  
##  <a name="deploying-data-mining-solutions"></a><a name="bkmk_Deploy"></a><span data-ttu-id="d54ce-118">데이터 마이닝 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="d54ce-118">Deploying Data Mining Solutions</span></span>  
 <span data-ttu-id="d54ce-119">솔루션을 배포하는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 다차원 개체 및 데이터 마이닝 개체를 지원하는 모드에서 실행되고 있어야 합니다. 즉 데이터 마이닝 개체를 테이블 형식 모델 또는 PowerPivot 데이터를 호스팅하는 인스턴스에 배포할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-119">The instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to which you deploy the solution must be running in a mode that supports multidimensional objects and data mining objects; that is, you cannot deploy data mining objects to an instance that hosts tabular models or PowerPivot data.</span></span>  
  
 <span data-ttu-id="d54ce-120">따라서 Visual Studio에서 데이터 마이닝 솔루션을 만드는 경우 반드시 **Analysis Services 다차원 및 데이터 마이닝 프로젝트**템플릿을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="d54ce-120">Therefore, when you create a data mining solution in Visual Studio, be sure to use the template, **Analysis Services Multidimensional and Data Mining Project**.</span></span>  
  
 <span data-ttu-id="d54ce-121">솔루션을 배포하면 지정된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 솔루션 파일과 같은 이름의 데이터베이스에 데이터 마이닝에 사용되는 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-121">When you deploy the solution, the objects used for data mining are created in the specified [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, in a database with the same name as the solution file.</span></span>  
  
 <span data-ttu-id="d54ce-122">관계형 솔루션 및 다차원 솔루션을 배포하는 방법에 대한 자세한 내용은 [데이터 마이닝 솔루션 배포](deployment-of-data-mining-solutions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d54ce-122">For more information about how to deploy both relational and multidimensional solutions, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
##  <a name="solution-walkthrough"></a><a name="bkmk_Walkthru"></a><span data-ttu-id="d54ce-123">솔루션 연습</span><span class="sxs-lookup"><span data-stu-id="d54ce-123">Solution Walkthrough</span></span>  
 <span data-ttu-id="d54ce-124">데이터 마이닝 마법사를 사용하여 데이터 마이닝 솔루션을 만드는 방법에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-124">Provides an overview of how to create data mining solutions by using the Data Mining Wizard.</span></span>  
  
 [<span data-ttu-id="d54ce-125">관계형 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="d54ce-125">Create a Relational Mining Structure</span></span>](create-a-relational-mining-structure.md)  
 <span data-ttu-id="d54ce-126">관계형 데이터, 텍스트 파일 및 기타 데이터 원본 뷰에 통합될 수 있는 원본에서 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-126">Create a mining structure from relational data, text files, and other sources that can be combined in a data source view.</span></span>  
  
 [<span data-ttu-id="d54ce-127">OLAP 마이닝 구조 만들기</span><span class="sxs-lookup"><span data-stu-id="d54ce-127">Create an OLAP Mining Structure</span></span>](create-an-olap-mining-structure.md)  
 <span data-ttu-id="d54ce-128">OLAP 큐브의 데이터를 기반으로 하는 마이닝 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-128">Create a mining structure based on data in an OLAP cube.</span></span> <span data-ttu-id="d54ce-129">OLAP 데이터에서 만든 모델을 데이터 마이닝 차원으로 저장하거나 데이터 및 모델 집합을 새 큐브로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-129">Models that you create from OLAP data can be saved as a data mining dimension, or you can save the set of data and your models as a new cube.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d54ce-130">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d54ce-130">In This Section</span></span>  
 [<span data-ttu-id="d54ce-131">데이터 마이닝 프로젝트</span><span class="sxs-lookup"><span data-stu-id="d54ce-131">Data Mining Projects</span></span>](data-mining-projects.md)  
  
 [<span data-ttu-id="d54ce-132">데이터 마이닝 개체 처리</span><span class="sxs-lookup"><span data-stu-id="d54ce-132">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)  
  
 [<span data-ttu-id="d54ce-133">데이터 마이닝 솔루션 관련 프로젝트</span><span class="sxs-lookup"><span data-stu-id="d54ce-133">Related Projects for Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
 [<span data-ttu-id="d54ce-134">데이터 마이닝 솔루션 배포</span><span class="sxs-lookup"><span data-stu-id="d54ce-134">Deployment of Data Mining Solutions</span></span>](deployment-of-data-mining-solutions.md)  
  
## <a name="related-tasks-and-topics"></a><span data-ttu-id="d54ce-135">관련 태스크 및 항목</span><span class="sxs-lookup"><span data-stu-id="d54ce-135">Related Tasks and Topics</span></span>  
 <span data-ttu-id="d54ce-136">데이터 원본 및 마이닝 구조를 포함하여 기본 데이터 마이닝 솔루션을 만든 후에는 새 모델을 추가하고, 모델을 테스트 및 비교하고, 예측을 만들고, 데이터 하위 집합을 시험하여 솔루션을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-136">After you have created a basic data mining solution, including data sources and a mining structure, you can build on the solution by adding new models, testing and comparing models, creating predictions, and experimenting with subsets of data.</span></span>  
  
 <span data-ttu-id="d54ce-137">자세한 내용은 다음 링크를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d54ce-137">For more information, see the following links:</span></span>  
  
|<span data-ttu-id="d54ce-138">작업</span><span class="sxs-lookup"><span data-stu-id="d54ce-138">Tasks</span></span>|<span data-ttu-id="d54ce-139">토픽</span><span class="sxs-lookup"><span data-stu-id="d54ce-139">Topics</span></span>|  
|-----------|------------|  
|<span data-ttu-id="d54ce-140">만든 모델을 테스트하고, 학습 데이터의 품질에 대한 유효성을 검사하고, 데이터 마이닝 모델의 정확도를 나타내는 차트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-140">Test the models you create, validate the quality of your training data, and create charts that represent the accuracy of data mining models.</span></span>|[<span data-ttu-id="d54ce-141">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ce-141">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)|  
|<span data-ttu-id="d54ce-142">구조 및 관련 모델을 데이터로 채워 모델을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-142">Train the model by populating the structure and related models with data.</span></span> <span data-ttu-id="d54ce-143">모델을 새 데이터로 업데이트 및 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-143">Update and extend models with new data.</span></span>|[<span data-ttu-id="d54ce-144">데이터 마이닝 개체 처리</span><span class="sxs-lookup"><span data-stu-id="d54ce-144">Processing Data Mining Objects</span></span>](processing-data-mining-objects.md)|  
|<span data-ttu-id="d54ce-145">학습 데이터에 필터를 적용하거나, 다른 알고리즘을 선택하거나, 고급 알고리즘 매개 변수를 설정하여 마이닝 모델을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-145">Customize a mining model by applying filters to the training data, choosing a different algorithm, or setting advanced algorithm parameters.</span></span>|[<span data-ttu-id="d54ce-146">마이닝 모델 및 구조 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="d54ce-146">Customize Mining Models and Structure</span></span>](customize-mining-models-and-structure.md)|  
|<span data-ttu-id="d54ce-147">모델을 학습하는 데 사용되는 데이터에 필터를 적용하여 마이닝 모델을 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-147">Customize a mining model by applying filters to the data used in training the mode.</span></span>|[<span data-ttu-id="d54ce-148">구조에 마이닝 모델 추가&#40;Analysis Services - 데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ce-148">Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;</span></span>](add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|<span data-ttu-id="d54ce-149">데이터 마이닝 솔루션을 업데이트하고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="d54ce-149">Update and manage data mining solutions.</span></span>|<span data-ttu-id="d54ce-150">Link TBD</span><span class="sxs-lookup"><span data-stu-id="d54ce-150">Link TBD</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d54ce-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d54ce-151">See Also</span></span>  
 [<span data-ttu-id="d54ce-152">데이터 마이닝 자습서&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d54ce-152">Data Mining Tutorials &#40;Analysis Services&#41;</span></span>](../data-mining-tutorials-analysis-services.md)  
  
  
