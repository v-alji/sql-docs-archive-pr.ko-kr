---
title: '4단계: 5단원 자습서 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5215b77d-c2ec-4b25-a3de-ca49ea197d74
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 76e4692de4daa9ddd6ed0e418bed5cda74ec7650
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648431"
---
# <a name="step-4-testing-the-lesson-5-tutorial-package"></a><span data-ttu-id="5acea-102">4단계: 5단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="5acea-102">Step 4: Testing the Lesson 5 Tutorial Package</span></span>
  <span data-ttu-id="5acea-103">런타임에 패키지는 패키지를 만들 때 지정한 원래 디렉터리 이름을 사용하지 않고 런타임에 업데이트된 변수에서 `Directory` 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-103">At run time, your package will obtain the value for the `Directory` property from a variable updated at run time, rather than using the original directory name that you specified when you created the package.</span></span> <span data-ttu-id="5acea-104">SSISTutorial.dtsConfig 파일을 사용하여 변수의 값이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-104">The value of the variable is populated by the SSISTutorial.dtsConfig file.</span></span>  
  
 <span data-ttu-id="5acea-105">패키지가 런타임에 새 값으로 Directory 속성을 업데이트하도록 하려면 패키지를 실행해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="5acea-105">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="5acea-106">예제 데이터 파일이 3개만 새 디렉터리에 복사되었으므로 데이터 흐름이 원래 폴더에 있는 파일 14개를 반복하지 않고 세 번만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-106">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="5acea-107">패키지 레이아웃 확인</span><span class="sxs-lookup"><span data-stu-id="5acea-107">Checking the Package Layout</span></span>  
 <span data-ttu-id="5acea-108">패키지를 테스트하려면 먼저 5단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-108">Before you test the package you should verify that the control and data flows in the Lesson 5 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="5acea-109">제어 흐름은 4단원의 제어 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-109">The control flow should be identical to the control flow in lesson 4.</span></span> <span data-ttu-id="5acea-110">데이터 흐름은 4단원의 데이터 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-110">The data flow should be identical to the data flow in lessons 4.</span></span>  
  
 <span data-ttu-id="5acea-111">**제어 흐름**</span><span class="sxs-lookup"><span data-stu-id="5acea-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="5acea-112">![패키지의 제어 흐름](../../2014/tutorials/media/task4lesson2control.gif "패키지의 제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="5acea-112">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="5acea-113">**데이터 흐름**</span><span class="sxs-lookup"><span data-stu-id="5acea-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="5acea-114">![패키지의 데이터 흐름](../../2014/tutorials/media/task9lesson1data.gif "패키지의 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="5acea-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-5-tutorial-package"></a><span data-ttu-id="5acea-115">5단원 자습서 패키지를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="5acea-115">To test the Lesson 5 tutorial package</span></span>  
  
1.  <span data-ttu-id="5acea-116">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="5acea-117">패키지 실행이 완료 되 면 **디버그** 메뉴에서 **디버깅 중지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5acea-117">After the package has completed running, on the **Debug** menu, and then click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="5acea-118">다음 단원</span><span class="sxs-lookup"><span data-stu-id="5acea-118">Next Lesson</span></span>  
 [<span data-ttu-id="5acea-119">6단원: 프로젝트 배포 모델에 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="5acea-119">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](../integration-services/lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
  
  
