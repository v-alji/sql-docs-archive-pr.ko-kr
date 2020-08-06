---
title: '3단계: 6단원 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3c7ab82e9b04fe0752252102374f745e311d830d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736561"
---
# <a name="step-3-testing-the-lesson-6-package"></a><span data-ttu-id="837f2-102">3단계: 6단원 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="837f2-102">Step 3: Testing the Lesson 6 Package</span></span>
  <span data-ttu-id="837f2-103">런타임에서 패키지는 VarFolderName 매개 변수로부터 Directory 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-103">At run time, your package will obtain the value for the Directory property from the VarFolderName parameter.</span></span>  
  
 <span data-ttu-id="837f2-104">패키지가 런타임에 새 값으로 Directory 속성을 업데이트하도록 하려면 패키지를 실행해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="837f2-104">To verify that the package updates the Directory property with the new value during run time, simply execute the package.</span></span> <span data-ttu-id="837f2-105">예제 데이터 파일이 3개만 새 디렉터리에 복사되었으므로 데이터 흐름이 원래 폴더에 있는 파일 14개를 반복하지 않고 세 번만 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-105">Because only three sample data files were copied to the new directory, the data flow will run only three times, rather than iterate through the 14 files in the original folder.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="837f2-106">패키지 레이아웃 확인</span><span class="sxs-lookup"><span data-stu-id="837f2-106">Checking the Package Layout</span></span>  
 <span data-ttu-id="837f2-107">패키지를 테스트하려면 먼저 6단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-107">Before you test the package you should verify that the control and data flows in the Lesson 6 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="837f2-108">제어 흐름은 5단원의 제어 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-108">The control flow should be identical to the control flow in lesson 5.</span></span> <span data-ttu-id="837f2-109">데이터 흐름은 5단원의 데이터 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-109">The data flow should be identical to the data flow in lesson 5.</span></span>  
  
 <span data-ttu-id="837f2-110">**제어 흐름**</span><span class="sxs-lookup"><span data-stu-id="837f2-110">**Control Flow**</span></span>  
  
 <span data-ttu-id="837f2-111">![제어 흐름](../../2014/tutorials/media/task3lesson6control.jpg "제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="837f2-111">![Control Flow](../../2014/tutorials/media/task3lesson6control.jpg "Control Flow")</span></span>  
  
 <span data-ttu-id="837f2-112">**데이터 흐름**</span><span class="sxs-lookup"><span data-stu-id="837f2-112">**Data Flow**</span></span>  
  
 <span data-ttu-id="837f2-113">![데이터 흐름](../../2014/tutorials/media/task3lesson6data.jpg "데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="837f2-113">![Data Flow](../../2014/tutorials/media/task3lesson6data.jpg "Data Flow")</span></span>  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a><span data-ttu-id="837f2-114">6 단원 자습서 패키지를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="837f2-114">TO test the Lesson 6 tutorial package</span></span>  
  
1.  <span data-ttu-id="837f2-115">디버그 메뉴에서 디버깅 시작을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-115">On the Debug menu, click Start Debugging.</span></span>  
  
2.  <span data-ttu-id="837f2-116">패키지의 실행이 완료된 후에 디버그 메뉴에서 디버깅 중지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="837f2-116">After the package has completed running, on the Debug menu, and then click Stop Debugging.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="837f2-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="837f2-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="837f2-118">4단계: 6단원 패키지 배포</span><span class="sxs-lookup"><span data-stu-id="837f2-118">Step 4: Deploying the Lesson 6 Package</span></span>](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
