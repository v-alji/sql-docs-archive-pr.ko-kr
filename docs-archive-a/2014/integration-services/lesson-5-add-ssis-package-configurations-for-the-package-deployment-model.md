---
title: '5 단원: 패키지 배포 모델에 대 한 패키지 구성 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c10dd54-67cb-4b63-9e4d-aa6ff0452ecb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee03d624ac7144cf6aef0829bcb7835fe5af9c53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729624"
---
# <a name="lesson-5-adding-package-configurations-for-the-package-deployment-model"></a><span data-ttu-id="ccd21-102">5단원: 패키지 배포 모델을 위한 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="ccd21-102">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>
  <span data-ttu-id="ccd21-103">패키지 구성을 사용하면 개발 환경 외부에서 런타임 속성과 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-103">Package configurations let you set run-time properties and variables from outside of the development environment.</span></span> <span data-ttu-id="ccd21-104">구성을 통해 쉽고 유연하게 배포할 수 있는 패키지를 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-104">Configurations allow you to develop packages that are flexible and easy to both deploy and distribute.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="ccd21-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서는 다음과 같은 구성 유형을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offers the following configuration types:</span></span>  
  
-   <span data-ttu-id="ccd21-106">XML 구성 파일</span><span class="sxs-lookup"><span data-stu-id="ccd21-106">XML configuration file</span></span>  
  
-   <span data-ttu-id="ccd21-107">환경 변수</span><span class="sxs-lookup"><span data-stu-id="ccd21-107">Environment variable</span></span>  
  
-   <span data-ttu-id="ccd21-108">레지스트리 항목</span><span class="sxs-lookup"><span data-stu-id="ccd21-108">Registry entry</span></span>  
  
-   <span data-ttu-id="ccd21-109">부모 패키지 변수</span><span class="sxs-lookup"><span data-stu-id="ccd21-109">Parent package variable</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="ccd21-110">테이블</span><span class="sxs-lookup"><span data-stu-id="ccd21-110">table</span></span>  
  
 <span data-ttu-id="ccd21-111">이 단원에서는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 만든 간단한 [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) 패키지를 수정하여 패키지 배포 모델을 사용하고 패키지 구성을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-111">In this lesson, you will modify the simple [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that you created in [Lesson 4: Adding Error Flow Redirection](lesson-4-add-error-flow-redirection-with-ssis.md) to use the Package Deployment Model and take advantage of package configurations.</span></span> <span data-ttu-id="ccd21-112">또한 자습서에 포함된 완료된 4단원 패키지를 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-112">You can also copy the completed Lesson 4 package that is included with the tutorial.</span></span> <span data-ttu-id="ccd21-113">패키지 구성 마법사를 통해 Directory 속성에 매핑된 패키지 수준 변수를 사용하여 Foreach 루프 컨테이너의 `Directory` 속성을 업데이트하는 XML 구성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-113">Using the Package Configuration Wizard, you will create an XML configuration that updates the `Directory` property of the Foreach Loop container by using a package-level variable mapped to the Directory property.</span></span> <span data-ttu-id="ccd21-114">구성 파일을 생성했으면 개발 환경 외부에서 변수 값을 수정하고 수정된 속성을 새 예제 데이터 폴더로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-114">Once you have created the configuration file, you will modify the value of the variable from outside of the development environment and point the modified property to a new sample data folder.</span></span> <span data-ttu-id="ccd21-115">패키지를 다시 실행 하면 구성 파일이 변수 값을 채우고 변수는 속성을 업데이트 합니다 `Directory` .</span><span class="sxs-lookup"><span data-stu-id="ccd21-115">When you run the package again, the configuration file populates the value of the variable, and the variable in turn updates the `Directory` property.</span></span> <span data-ttu-id="ccd21-116">결과적으로 패키지는 패키지에 하드 코드된 원래 폴더의 파일이 아니라 새 데이터 폴더의 파일을 반복 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-116">As a result, the package iterates through the files in the new data folder, rather than iterating through the files in the original folder that was hard-coded in the package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ccd21-117">이 자습서를 실행하려면 **AdventureWorksDW2012** 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-117">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="ccd21-118">**AdventureWorksDW2012**의 설치 및 배포 방법에 대한 자세한 내용은 [CodePlex의 Reporting Services 제품 샘플](https://go.microsoft.com/fwlink/?LinkID=526910)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ccd21-118">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ccd21-119">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="ccd21-119">Lesson Tasks</span></span>  
 <span data-ttu-id="ccd21-120">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ccd21-120">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="ccd21-121">1단계: 4단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="ccd21-121">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
-   [<span data-ttu-id="ccd21-122">2단계: 패키지 구성 설정 및 구성</span><span class="sxs-lookup"><span data-stu-id="ccd21-122">Step 2: Enabling and Configuring Package Configurations</span></span>](lesson-5-2-enabling-and-configuring-package-configurations.md)  
  
-   [<span data-ttu-id="ccd21-123">3단계: Directory 속성 구성 값 수정</span><span class="sxs-lookup"><span data-stu-id="ccd21-123">Step 3: Modifying the Directory Property Configuration Value</span></span>](lesson-5-3-modifying-the-directory-property-configuration-value.md)  
  
-   [<span data-ttu-id="ccd21-124">4단계: 5단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="ccd21-124">Step 4: Testing the Lesson 5 Tutorial Package</span></span>](lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="ccd21-125">단원 시작</span><span class="sxs-lookup"><span data-stu-id="ccd21-125">Start the Lesson</span></span>  
  
-   [<span data-ttu-id="ccd21-126">1단계: 4단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="ccd21-126">Step 1: Copying the Lesson 4 Package</span></span>](lesson-5-1-copying-the-lesson-4-package.md)  
  
  
