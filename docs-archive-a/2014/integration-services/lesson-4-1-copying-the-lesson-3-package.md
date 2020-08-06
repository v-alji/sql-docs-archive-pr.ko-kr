---
title: '1단계: 3단원 패키지 복사 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fde3bd907e8a55b1ac9a164b2960268189b19392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650174"
---
# <a name="step-1-copying-the-lesson-3-package"></a><span data-ttu-id="ea902-102">1단계: 3단원 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="ea902-102">Step 1: Copying the Lesson 3 Package</span></span>
  <span data-ttu-id="ea902-103">이 태스크에서는 3단원에서 만든 Lesson 3.dtsx 패키지의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-103">In this task, you will create a copy of the Lesson 3.dtsx package that you created in Lesson 3.</span></span> <span data-ttu-id="ea902-104">또는 3단원을 완료하지 않은 경우에는 자습서에 포함되어 있는 완성된 3단원 패키지를 프로젝트에 추가한 다음 작업을 수행할 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-104">Alternatively, if you did not complete lesson 3, you can add the completed lesson 3 package that is included with the tutorial to the project, and then make a copy of it to work with.</span></span> <span data-ttu-id="ea902-105">4단원의 나머지 부분에서 이 새 복사본을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-105">You will use this new copy throughout the rest of Lesson 4.</span></span>  
  
### <a name="to-create-the-lesson-4-package"></a><span data-ttu-id="ea902-106">4단원 패키지를 만들려면</span><span class="sxs-lookup"><span data-stu-id="ea902-106">To create the Lesson 4 package</span></span>  
  
1.  <span data-ttu-id="ea902-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools를 아직 열지 않은 경우 **시작**을 클릭하고 **모든 프로그램**, **Microsoft SQL Server**를 차례로 가리킨 다음 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-107">If [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools is not already open, click **Start**, point to **All Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="ea902-108">**파일** 메뉴에서 **열기**, **프로젝트/솔루션**을 차례로 클릭하고 **SSIS Tutorial** 을 선택한 다음 **열기**를 클릭하고 **SSIS Tutorial.sln**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-108">On the **File** menu, click **Open**, click **Project/Solution**, select **SSIS Tutorial** and click **Open**, and then double-click **SSIS Tutorial.sln**.</span></span>  
  
3.  <span data-ttu-id="ea902-109">솔루션 탐색기에서 **Lesson 3.dtsx**를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-109">In Solution Explorer, right-click **Lesson 3.dtsx**, and then click **Copy**.</span></span>  
  
4.  <span data-ttu-id="ea902-110">솔루션 탐색기에서 **SSIS 패키지**를 마우스 오른쪽 단추로 클릭 한 다음 **붙여넣기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-110">In Solution Explorer, right-click **SSIS Packages**, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="ea902-111">기본적으로 복사된 패키지의 이름은 Lesson 4.dtsx가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-111">By default, the copied package is named Lesson 4.dtsx.</span></span>  
  
5.  <span data-ttu-id="ea902-112">솔루션 탐색기에서 **Package.dtsx 단원을** 두 번 클릭 하 여 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-112">In Solution Explorer, double-click **Lesson 4.dtsx** to open the package.</span></span>  
  
6.  <span data-ttu-id="ea902-113">**제어 흐름** 탭 배경의 아무 곳이나 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-113">Right-click anywhere in the background of the **Control Flow** tab and click **Properties**.</span></span>  
  
7.  <span data-ttu-id="ea902-114">속성 창에서 속성을로 업데이트 `Name` `Lesson 4` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-114">In the Properties window, update the `Name` property to `Lesson 4`.</span></span>  
  
8.  <span data-ttu-id="ea902-115">**ID** 속성 상자를 클릭한 다음 목록에서 **\<Generate New ID>** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-115">Click the box for the **ID** property, and then in the list, click **\<Generate New ID>**.</span></span>  
  
### <a name="to-add-the-completed-lesson-3-package"></a><span data-ttu-id="ea902-116">완성된 3단원 패키지를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ea902-116">To add the completed Lesson 3 package</span></span>  
  
1.  <span data-ttu-id="ea902-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 를 연 다음 SSIS 자습서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-117">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and open the SSIS Tutorial project.</span></span>  
  
2.  <span data-ttu-id="ea902-118">솔루션 탐색기에서 **SSIS 패키지**를 마우스 오른쪽 단추로 클릭 하 고 **기존 패키지 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-118">In Solution Explorer, right-click **SSIS Packages**, and click **Add Existing Package**.</span></span>  
  
3.  <span data-ttu-id="ea902-119">**기존 패키지의 복사본 추가** 대화 상자의 **패키지 위치**에서 **파일 시스템**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-119">In the **Add Copy of Existing Package** dialog box, in **Package location**, select **File system**.</span></span>  
  
4.  <span data-ttu-id="ea902-120">찾아보기 **(...)** 단추를 클릭 하 고 컴퓨터의 package.dtsx 단원으로 이동한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-120">Click the browse **(...)** button, navigate to Lesson 3.dtsx on your machine, and then click **Open**.</span></span>  
  
     <span data-ttu-id="ea902-121">이 자습서에 대한 모든 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-121">To download all of the lesson packages for this tutorial, do the following.</span></span>  
  
    1.  <span data-ttu-id="ea902-122">[Integration Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=275027)로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-122">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="ea902-123">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-123">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="ea902-124">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-124">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
5.  <span data-ttu-id="ea902-125">이전 절차의 3-8단계에서 설명한 대로 3단원 패키지를 복사하여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea902-125">Copy and paste the Lesson 3 package as described in steps 3-8 in the previous procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="ea902-126">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="ea902-126">Next Task in Lesson</span></span>  
 [<span data-ttu-id="ea902-127">2단계: 손상된 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ea902-127">Step 2: Creating a Corrupted File</span></span>](lesson-4-2-creating-a-corrupted-file.md)  
  
  
