---
title: '2 단원: 루핑 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65efb84b4e50b470470e396bbe5681ce4b5dfac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648434"
---
# <a name="lesson-2-adding-looping"></a><span data-ttu-id="eb4cb-102">2단원: 루핑 추가</span><span class="sxs-lookup"><span data-stu-id="eb4cb-102">Lesson 2: Adding Looping</span></span>
  <span data-ttu-id="eb4cb-103">[1 단원: 프로젝트 및 기본 패키지 만들기](lesson-1-create-a-project-and-basic-package-with-ssis.md)에서는 단일 플랫 파일 원본에서 데이터를 추출 하 고, 조회 변환을 사용 하 여 데이터를 변환 하 고, 마지막으로 **AdventureWorksDW2012** 예제 데이터베이스의 **FactCurrency** 팩트 테이블로 데이터를 로드 하는 패키지를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-103">In [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md), you created a package that extracted data from a single flat file source, transformed the data using Lookup transformations, and finally loaded the data into the **FactCurrency** fact table of the **AdventureWorksDW2012** sample database.</span></span>  
  
 <span data-ttu-id="eb4cb-104">그러나 ETL(추출, 변환 및 로드) 프로세스에서 플랫 파일을 하나만 사용하는 경우는 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-104">However, it is rare for an extract, transform, and load (ETL) process to use a single flat file.</span></span> <span data-ttu-id="eb4cb-105">일반적인 ETL 프로세스는 여러 플랫 파일 원본에서 데이터를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-105">A typical ETL process would extract data from multiple flat file sources.</span></span> <span data-ttu-id="eb4cb-106">여러 원본에서 데이터를 추출하려면 반복적인 제어 흐름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-106">Extracting data from multiple sources requires an iterative control flow.</span></span> <span data-ttu-id="eb4cb-107">의 가장 중요 한 기능 중 하나는 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지에 반복 이나 반복을 쉽게 추가할 수 있는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-107">One of the most anticipated features of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is the ability to easily add iteration or looping to packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="eb4cb-108">에서는 Foreach Loop 컨테이너와 For Loop 컨테이너라는 패키지 루핑을 위한 두 가지 유형의 컨테이너를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-108">provides two types of containers for looping through packages: the Foreach Loop container and the For Loop container.</span></span> <span data-ttu-id="eb4cb-109">Foreach 루프 컨테이너는 열거자를 사용하여 루핑을 수행하지만 For 루프 컨테이너는 대개 변수 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-109">The Foreach Loop container uses an enumerator to perform the looping, whereas the For Loop container typically uses a variable expression.</span></span> <span data-ttu-id="eb4cb-110">이 단원에서는 Foreach 루프 컨테이너를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-110">This lesson uses the Foreach Loop container.</span></span>  
  
 <span data-ttu-id="eb4cb-111">Foreach 루프 컨테이너를 사용하면 패키지에서 지정한 열거자의 각 멤버에 대해 제어 흐름을 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-111">The Foreach Loop container enables a package to repeat the control flow for each member of a specified enumerator.</span></span> <span data-ttu-id="eb4cb-112">Foreach 루프 컨테이너를 사용하여 다음과 같은 항목을 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-112">With the Foreach Loop container, you can enumerate:</span></span>  
  
-   <span data-ttu-id="eb4cb-113">ADO 레코드 집합 행</span><span class="sxs-lookup"><span data-stu-id="eb4cb-113">ADO recordset rows</span></span>  
  
-   <span data-ttu-id="eb4cb-114">ADO.Net 스키마 정보</span><span class="sxs-lookup"><span data-stu-id="eb4cb-114">ADO .Net schema information</span></span>  
  
-   <span data-ttu-id="eb4cb-115">파일 및 디렉터리 구조</span><span class="sxs-lookup"><span data-stu-id="eb4cb-115">File and directory structures</span></span>  
  
-   <span data-ttu-id="eb4cb-116">시스템, 패키지 및 사용자 변수</span><span class="sxs-lookup"><span data-stu-id="eb4cb-116">System, package and user variables</span></span>  
  
-   <span data-ttu-id="eb4cb-117">변수에 포함된 열거 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="eb4cb-117">Enumerable objects contained in a variable</span></span>  
  
-   <span data-ttu-id="eb4cb-118">컬렉션의 항목</span><span class="sxs-lookup"><span data-stu-id="eb4cb-118">Items in a collection</span></span>  
  
-   <span data-ttu-id="eb4cb-119">XML 경로 언어(XPath)식의 노드</span><span class="sxs-lookup"><span data-stu-id="eb4cb-119">Nodes in an XML Path Language (XPath) expression</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="eb4cb-120">SMO(Management Objects)(!!)</span><span class="sxs-lookup"><span data-stu-id="eb4cb-120">Management Objects (SMO)</span></span>  
  
 <span data-ttu-id="eb4cb-121">이 단원에서는 1단원에서 만든 단순 ETL 패키지를 Foreach 루프 컨테이너를 사용하도록 수정하고</span><span class="sxs-lookup"><span data-stu-id="eb4cb-121">In this lesson, you will modify the simple ETL package created in Lesson 1 to take advantage of the Foreach Loop container.</span></span> <span data-ttu-id="eb4cb-122">자습서 패키지에서 폴더에 있는 모든 플랫 파일을 반복 처리할 수 있도록 사용자 정의 패키지 변수를 설정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-122">You will also set user-defined package variables to enable the tutorial package to iterate through all the flat files in the folder.</span></span> <span data-ttu-id="eb4cb-123">이전 단원을 완료하지 않은 경우 자습서에 완성된 상태로 포함된 1단원 패키지를 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-123">If you have not completed the previous lesson, you can also copy the completed Lesson 1 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="eb4cb-124">이 단원에서는 데이터 흐름을 수정하지 않고 제어 흐름만 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-124">In this lesson, you will not modify the data flow, only the control flow.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eb4cb-125">이 자습서를 실행하려면 **AdventureWorksDW2012** 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-125">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="eb4cb-126">**AdventureWorksDW2012**의 설치 및 배포 방법에 대한 자세한 내용은 [CodePlex의 Reporting Services 제품 샘플](https://go.microsoft.com/fwlink/p/?LinkID=526910)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-126">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="eb4cb-127">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="eb4cb-127">Lesson Tasks</span></span>  
 <span data-ttu-id="eb4cb-128">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="eb4cb-128">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="eb4cb-129">1단계: 1단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="eb4cb-129">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [<span data-ttu-id="eb4cb-130">2단계: Foreach 루프 컨테이너 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="eb4cb-130">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [<span data-ttu-id="eb4cb-131">3단계: 플랫 파일 연결 관리자 수정</span><span class="sxs-lookup"><span data-stu-id="eb4cb-131">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="eb4cb-132">4단계: 2단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="eb4cb-132">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="eb4cb-133">단원 시작</span><span class="sxs-lookup"><span data-stu-id="eb4cb-133">Start the Lesson</span></span>  
 [<span data-ttu-id="eb4cb-134">1단계: 1단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="eb4cb-134">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="eb4cb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eb4cb-135">See Also</span></span>  
 [<span data-ttu-id="eb4cb-136">For 루프 컨테이너</span><span class="sxs-lookup"><span data-stu-id="eb4cb-136">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
