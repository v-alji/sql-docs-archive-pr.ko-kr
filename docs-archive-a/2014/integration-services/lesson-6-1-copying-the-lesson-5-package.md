---
title: '1단계: 5단원 패키지 복사 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a25fcc13-987e-4f3d-8f0c-76f7e6e59920
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b30ec927084548a2371f22d857d5302e5dc84c5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661249"
---
# <a name="step-1-copying-the-lesson-5-package"></a><span data-ttu-id="daa97-102">1단계: 5단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="daa97-102">Step 1: Copying the Lesson 5 Package</span></span>
  <span data-ttu-id="daa97-103">이 태스크에서는 5단원에서 만든 Lesson 5.dtsx 패키지의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-103">In this task, you will create a copy of the Lesson 5.dtsx package that you created in Lesson 5.</span></span> <span data-ttu-id="daa97-104">또는 자습서에 포함되어 있는 완성된 5단원 패키지를 프로젝트에 추가한 다음 복사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-104">Alternatively, you can add the completed lesson 5 package that is included with the tutorial to the project, and then copy it instead.</span></span> <span data-ttu-id="daa97-105">6단원의 나머지 부분에서 이 새 복사본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-105">You will use this new copy throughout the rest of Lesson 6.</span></span>  
  
### <a name="to-copy-the-lesson-5-package"></a><span data-ttu-id="daa97-106">5단원 패키지를 복사하려면</span><span class="sxs-lookup"><span data-stu-id="daa97-106">To copy the Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="daa97-107">SQL Server Data Tools를 아직 열지 않은 경우 시작을 클릭하고 모든 프로그램, Microsoft SQL Server 2012를 차례로 가리킨 다음 SQL Server Data Tools를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-107">If SQL Server Data Tools is not already open, click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Server Data Tools.</span></span>  
  
2.  <span data-ttu-id="daa97-108">파일 메뉴에서 열기, 프로젝트/솔루션을 차례로 클릭하고 SSIS Tutorial을 선택하고 열기를 클릭한 후 SSIS Tutorial.sln을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-108">On the File menu, click Open, click Project/Solution, select SSIS Tutorial and click Open, and then double-click SSIS Tutorial.sln.</span></span>  
  
3.  <span data-ttu-id="daa97-109">솔루션 탐색기에서 Lesson 5.dtsx를 마우스 오른쪽 단추로 클릭한 후 복사를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-109">In Solution Explorer, right-click Lesson 5.dtsx, and then click Copy.</span></span>  
  
4.  <span data-ttu-id="daa97-110">솔루션 탐색기에서 SSIS 패키지를 마우스 오른쪽 단추로 클릭한 후 붙여넣기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-110">In Solution Explorer, right-click SSIS Packages, and then click Paste.</span></span>  
  
     <span data-ttu-id="daa97-111">기본적으로 복사된 패키지의 이름은 Lesson 6.dtsx가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-111">By default, the copied package is named Lesson 6.dtsx.</span></span>  
  
5.  <span data-ttu-id="daa97-112">솔루션 탐색기에서 Lesson 6.dtsx를 두 번 클릭하여 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-112">In the Solution Explorer, double-click Lesson 6.dtsx to open the package.</span></span>  
  
6.  <span data-ttu-id="daa97-113">제어 흐름 탭 배경의 아무 위치나 마우스 오른쪽 단추로 클릭한 다음 속성을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-113">Right-click anywhere in the background of the Control Flow tab then click Properties.</span></span>  
  
7.  <span data-ttu-id="daa97-114">속성 창에서 Name 속성을 Lesson 6으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-114">In the Properties window, update the Name property to Lesson 6.</span></span>  
  
8.  <span data-ttu-id="daa97-115">ID 속성 상자를 클릭하고 드롭다운 화살표를 클릭한 다음 \<Generate New ID>를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-115">Click the box for the ID property, then click the dropdown arrow, and then click \<Generate New ID>.</span></span>  
  
### <a name="to-add-the-completed-lesson-5-package"></a><span data-ttu-id="daa97-116">완성된 5단원 패키지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="daa97-116">To add the completed Lesson 5 package</span></span>  
  
1.  <span data-ttu-id="daa97-117">SQL Server Data Tools를 연 다음 SSIS 자습서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-117">Open SQL Server Data Tools and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="daa97-118">솔루션 탐색기에서 SSIS 패키지를 마우스 오른쪽 단추로 클릭한 다음 기존 패키지 추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-118">In Solution Explorer, right-click SSIS Packages, and click Add Existing Package.</span></span>  
  
3.  <span data-ttu-id="daa97-119">기존 패키지의 복사본 추가 대화 상자의 패키지 위치에서 파일 시스템을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-119">In the Add Copy of Existing Package dialog box, in Package location, select File system.</span></span>  
  
4.  <span data-ttu-id="daa97-120">찾아보기(…) 단추를 클릭하여 머신의 Lesson 5.dtsx로 이동한 다음, **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-120">Click the browse (...) button, Lesson 5.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="daa97-121">이 자습서에 대한 모든 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="daa97-122">[Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="daa97-123">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="daa97-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="daa97-125">이전 절차의 3-8단계에서 설명한 대로 5단원 패키지를 복사하여 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-125">Copy and paste the Lesson 5 package as described in steps 3-8 in the previous procedure.</span></span>  
  
     <span data-ttu-id="daa97-126">5단원 패키지를 복사한 후 솔루션에 이전 단원의 패키지가 현재 있는 경우 1-5단원에서 각 패키지를 마우스 오른쪽 단추로 클릭하고 프로젝트에서 제외를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-126">After copying the Lesson 5 package, if you currently have the packages from the previous lessons in your solution, right-click each package from lessons 1-5 and click Exclude From Project.</span></span> <span data-ttu-id="daa97-127">작업이 완료되면 솔루션에 Lesson 6.dtsx만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daa97-127">When done you should have only Lesson 6.dtsx in your solution.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="daa97-128">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="daa97-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="daa97-129">2단계: 프로젝트를 프로젝트 배포 모델로 변환</span><span class="sxs-lookup"><span data-stu-id="daa97-129">Step 2: Converting the Project to the Project Deployment Model</span></span>](lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
  
