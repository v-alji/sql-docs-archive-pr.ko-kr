---
title: '9단계: 1단원 자습서 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9aee7acf-797b-46f2-830d-80ab64a9f0b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dff1132489c1683430b1003e88f5037664b11983
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651116"
---
# <a name="step-9-testing-the-lesson-1-tutorial-package"></a><span data-ttu-id="0aa9c-102">9단계: 1단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="0aa9c-102">Step 9: Testing the Lesson 1 Tutorial Package</span></span>
  <span data-ttu-id="0aa9c-103">이 단원에서는 다음 태스크를 수행했습니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-103">In this lesson, you have done the following tasks:</span></span>  
  
-   <span data-ttu-id="0aa9c-104">새 [!INCLUDE[ssIS](../includes/ssis-md.md)] 프로젝트를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-104">Created a new [!INCLUDE[ssIS](../includes/ssis-md.md)] project.</span></span>  
  
-   <span data-ttu-id="0aa9c-105">패키지에서 원본 및 대상 데이터에 연결하는 데 필요한 연결 관리자를 구성했습니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-105">Configured the connection managers that the package needs to connect to the source and destination data.</span></span>  
  
-   <span data-ttu-id="0aa9c-106">플랫 파일 원본에서 데이터를 가져오고 데이터에 필요한 조회 변환을 수행하고 대상의 데이터를 구성하는 데이터 흐름을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-106">Added a data flow that takes the data from a flat file source, performs the necessary Lookup transformations on the data, and configures the data for the destination.</span></span>  
  
 <span data-ttu-id="0aa9c-107">이제 패키지가 완료되었습니다!</span><span class="sxs-lookup"><span data-stu-id="0aa9c-107">Your package is now complete!</span></span> <span data-ttu-id="0aa9c-108">패키지를 테스트하십시오.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-108">It is time to test your package.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="0aa9c-109">패키지 레이아웃 확인</span><span class="sxs-lookup"><span data-stu-id="0aa9c-109">Checking the Package Layout</span></span>  
 <span data-ttu-id="0aa9c-110">패키지를 테스트하려면 먼저 1단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-110">Before you test the package you should verify that the control and data flows in the Lesson 1 package contain the objects shown in the following diagrams.</span></span>  
  
 <span data-ttu-id="0aa9c-111">**제어 흐름**</span><span class="sxs-lookup"><span data-stu-id="0aa9c-111">**Control Flow**</span></span>  
  
 <span data-ttu-id="0aa9c-112">![패키지의 제어 흐름](../../2014/tutorials/media/task9lesson1control.gif "패키지의 제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="0aa9c-112">![Control flow in package](../../2014/tutorials/media/task9lesson1control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="0aa9c-113">**데이터 흐름**</span><span class="sxs-lookup"><span data-stu-id="0aa9c-113">**Data Flow**</span></span>  
  
 <span data-ttu-id="0aa9c-114">![패키지의 데이터 흐름](../../2014/tutorials/media/task9lesson1data.gif "패키지의 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="0aa9c-114">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-1-tutorial-package"></a><span data-ttu-id="0aa9c-115">1단원 자습서 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="0aa9c-115">To run the Lesson 1 tutorial package</span></span>  
  
1.  <span data-ttu-id="0aa9c-116">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-116">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="0aa9c-117">패키지가 실행되어 1097개의 행이 **AdventureWorksDW2012** 의 **FactCurrency**팩트 테이블에 성공적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-117">The package will run, resulting in 1097 rows successfully added into the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span>  
  
2.  <span data-ttu-id="0aa9c-118">패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0aa9c-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="0aa9c-119">다음 단원</span><span class="sxs-lookup"><span data-stu-id="0aa9c-119">Next Lesson</span></span>  
 [<span data-ttu-id="0aa9c-120">2단원: 루핑 추가</span><span class="sxs-lookup"><span data-stu-id="0aa9c-120">Lesson 2: Adding Looping</span></span>](../integration-services/lesson-2-adding-looping-with-ssis.md)  
  
## <a name="see-also"></a><span data-ttu-id="0aa9c-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0aa9c-121">See Also</span></span>  
 [<span data-ttu-id="0aa9c-122">프로젝트 및 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="0aa9c-122">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
