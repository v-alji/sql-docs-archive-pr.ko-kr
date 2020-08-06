---
title: '6 단원: 프로젝트 배포 모델에 매개 변수 사용 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4bdc6b9dfc019822d6cf1bd9ec7d89ffcc5ea5e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648429"
---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model"></a><span data-ttu-id="51f63-102">6단원: 프로젝트 배포 모델에 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="51f63-102">Lesson 6: Using Parameters with the Project Deployment Model</span></span>
  <span data-ttu-id="51f63-103">SQL Server 2012에는 Integration Services 서버에 프로젝트를 배포할 수 있는 새로운 배포 모델이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-103">SQL Server 2012 introduces a new deployment model where you can deploy your projects to the Integration Services server.</span></span> <span data-ttu-id="51f63-104">Integration Services 서버에서는 패키지를 관리 및 실행하고 패키지에 대한 런타임 값을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-104">The Integration Services server enables you to manage and run packages, and to configure runtime values for packages.</span></span>  
  
 <span data-ttu-id="51f63-105">이 단원에서는 프로젝트 배포 모델을 사용하도록 [Lesson 5: Adding Package Configurations for the Package Deployment Model](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) 에서 만든 패키지를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-105">In this lesson, you will modify the package that you created in [Lesson 5: Adding Package Configurations for the Package Deployment Model](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) to use the Project Deployment Model.</span></span> <span data-ttu-id="51f63-106">구성 값을 예제 데이터 위치를 지정하는 매개 변수로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-106">You replace the configuration value with a parameter to specify the sample data location.</span></span> <span data-ttu-id="51f63-107">또한 자습서에 포함된 완료된 5단원 패키지를 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-107">You can also copy the completed Lesson 5 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="51f63-108">Integration Services 프로젝트 구성 마법사를 사용하여 프로젝트를 프로젝트 배포 모델로 변환하고 구성 값이 아닌 매개 변수를 사용해서 디렉터리 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-108">Using the Integration Services Project Configuration Wizard, you will convert the project to the Project Deployment Model and use a Parameter rather than a configuration value to set the Directory property.</span></span> <span data-ttu-id="51f63-109">이 단원에서는 기존 SSIS 패키지를 새로운 프로젝트 배포 모델로 변환하기 위해 수행해야 하는 단계에 대해 일부 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-109">This lesson partially covers the steps you would follow to convert existing SSIS packages to the new Project Deployment Model.</span></span>  
  
 <span data-ttu-id="51f63-110">패키지를 다시 실행하면 Integration Services 서비스가 매개 변수를 사용해서 변수 값을 채우고, 이 변수는 다시 디렉터리 속성을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-110">When you run the package again, the Integration Services service uses the parameter to populate the value of the variable, and the variable in turn updates the Directory property.</span></span> <span data-ttu-id="51f63-111">따라서 패키지 구성 파일에 설정된 폴더가 아니라 매개 변수 값으로 지정된 새 데이터 폴더의 파일이 패키지에서 반복 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-111">As a result, the package iterates through the files in the new data folder specified by the parameter value rather than the folder that was set in the package configuration file.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="51f63-112">이 자습서를 실행하려면 **AdventureWorksDW2012** 예제 데이터베이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-112">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="51f63-113">**AdventureWorksDW2012**설치 및 배포 방법에 대한 자세한 내용은 [SQL Server 예제 및 예제 데이터베이스 설치 시 고려 사항](https://technet.microsoft.com/library/ms161556%28v=sql.105%29)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51f63-113">For more information about how to install and deploy **AdventureWorksDW2012**, see [Considerations for Installing SQL Server Samples and Sample Databases](https://technet.microsoft.com/library/ms161556%28v=sql.105%29).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="51f63-114">단원 태스크</span><span class="sxs-lookup"><span data-stu-id="51f63-114">Lesson Tasks</span></span>  
 <span data-ttu-id="51f63-115">이 단원에서는 다음 태스크를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="51f63-115">This lesson contains the following tasks:</span></span>  
  
1.  [<span data-ttu-id="51f63-116">1단계: 5단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="51f63-116">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [<span data-ttu-id="51f63-117">2단계: 프로젝트를 프로젝트 배포 모델로 변환</span><span class="sxs-lookup"><span data-stu-id="51f63-117">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [<span data-ttu-id="51f63-118">3단계: 6단원 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="51f63-118">Step 3: Testing the Lesson 6 Package</span></span>](lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [<span data-ttu-id="51f63-119">4단계: 6단원 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="51f63-119">Step 4: Deploying the Lesson 6 Package</span></span>](lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="51f63-120">단원 시작</span><span class="sxs-lookup"><span data-stu-id="51f63-120">Start the Lesson</span></span>  
 [<span data-ttu-id="51f63-121">1단계: 5단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="51f63-121">Step 1: Copying the Lesson 5 Package</span></span>](lesson-6-1-copying-the-lesson-5-package.md)  
  
  
