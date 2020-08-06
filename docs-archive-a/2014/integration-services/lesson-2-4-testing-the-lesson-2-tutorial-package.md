---
title: '4단계: 2단원 자습서 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0e8c0a25-8f79-41df-8ed2-f82a74b129cd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c055f80cbe9e6748b82569204e3a2d82e2f437e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647106"
---
# <a name="step-4-testing-the-lesson-2-tutorial-package"></a><span data-ttu-id="9c6ab-102">4단계: 2단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="9c6ab-102">Step 4: Testing the Lesson 2 Tutorial Package</span></span>
  <span data-ttu-id="9c6ab-103">Foreach 루프 컨테이너와 플랫 파일 연결 관리자가 이제 구성되었으므로 2단원 패키지에서는 Sample Data 폴더에 있는 14개의 플랫 파일을 반복 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-103">With the Foreach Loop container and the Flat File connection manager now configured, the Lesson 2 package can iterate through the collection of 14 flat files in the Sample Data folder.</span></span> <span data-ttu-id="9c6ab-104">지정한 파일 이름 기준과 일치하는 파일 이름을 찾을 때마다 Foreach 루프 컨테이너는 사용자 정의 변수를 해당 파일 이름으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-104">Each time a file name is found that matches the specified file name criteria, the Foreach Loop container populates the user-defined variable with the file name.</span></span> <span data-ttu-id="9c6ab-105">이에 따라 이 변수가 플랫 파일 연결 관리자의 ConnectionString 속성을 업데이트하면 새 플랫 파일에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-105">This variable, in turn, updates the ConnectionString property of the Flat File connection manager, and a connection to the new flat file is made.</span></span> <span data-ttu-id="9c6ab-106">Foreach 루프 컨테이너는 폴더에 있는 다음 파일에 연결하기 전에 새 플랫 파일의 데이터에 대해 수정되지 않은 데이터 흐름 태스크를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-106">The Foreach Loop container then runs the unmodified data flow task against the data in the new flat file before connecting to the next file in the folder.</span></span>  
  
 <span data-ttu-id="9c6ab-107">다음 절차를 사용하여 패키지에 추가한 새 루핑 기능을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-107">Use the following procedure to test the new looping functionality that you have added to your package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c6ab-108">1단원에서 패키지를 실행한 경우 이 단원에서 패키지를 실행하기 전에 AdventureWorksDW2012에서 dbo.FactCurrency의 레코드를 삭제해야 하며, 그렇지 않으면 패키지가 실패하고 기본 키 제약 조건 위반을 나타내는 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-108">If you ran the package from Lesson 1, you will need to delete the records from dbo.FactCurrency in AdventureWorksDW2012 before you run the package from this lesson or the package will fail with errors indicating a Violation of Primary Key constraint.</span></span> <span data-ttu-id="9c6ab-109">디버그/디버깅 시작(F5)을 선택하여 패키지를 실행하면 1단원 및 2단원이 모두 실행되므로 같은 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-109">You will receive the same errors if you run the package by selecting Debug/Start Debugging (or press F5) because both Lesson 1 and Lesson 2 will run.</span></span> <span data-ttu-id="9c6ab-110">2단원에서는 1단원에서 이미 삽입한 레코드를 삽입하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-110">Lesson 2 will attempt to insert records already inserted in Lesson 1.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="9c6ab-111">패키지 레이아웃 확인</span><span class="sxs-lookup"><span data-stu-id="9c6ab-111">Checking the Package Layout</span></span>  
 <span data-ttu-id="9c6ab-112">패키지를 테스트하려면 먼저 2단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-112">Before you test the package you should verify that the control and data flows in the Lesson 2 package contains the objects shown in the following diagrams.</span></span> <span data-ttu-id="9c6ab-113">데이터 흐름은 1단원의 데이터 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-113">The data flow should be identical to the data flow in lesson 1.</span></span>  
  
 <span data-ttu-id="9c6ab-114">**제어 흐름**</span><span class="sxs-lookup"><span data-stu-id="9c6ab-114">**Control Flow**</span></span>  
  
 <span data-ttu-id="9c6ab-115">![패키지의 제어 흐름](../../2014/tutorials/media/task4lesson2control.gif "패키지의 제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="9c6ab-115">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="9c6ab-116">**데이터 흐름**</span><span class="sxs-lookup"><span data-stu-id="9c6ab-116">**Data Flow**</span></span>  
  
 <span data-ttu-id="9c6ab-117">![패키지의 데이터 흐름](../../2014/tutorials/media/task9lesson1data.gif "패키지의 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="9c6ab-117">![Data flow in package](../../2014/tutorials/media/task9lesson1data.gif "Data flow in package")</span></span>  
  
### <a name="to-test-the-lesson-2-tutorial-package"></a><span data-ttu-id="9c6ab-118">2단원 자습서 패키지를 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="9c6ab-118">To test the Lesson 2 tutorial package</span></span>  
  
1.  <span data-ttu-id="9c6ab-119">**솔루션 탐색기**에서 **Lesson 2.dtsx** 를 마우스 오른쪽 단추로 클릭한 다음 **패키지 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-119">In **Solution Explorer**, right-click **Lesson 2.dtsx** and click **Execute Package**.</span></span>  
  
     <span data-ttu-id="9c6ab-120">패키지가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-120">The package will run.</span></span> <span data-ttu-id="9c6ab-121">출력 창에서 각 루프의 상태를 확인 하거나 **진행률** 탭을 클릭 하 여 확인할 수 있습니다. 예를 들어 Currency_VEB.txt 파일에서 대상 테이블에 1097 줄이 추가 된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-121">You can verify the status of each loop in the Output window, or by clicking on the **Progress** tab. For example, you can see that 1097 lines were added to the destination table from the file Currency_VEB.txt.</span></span>  
  
2.  <span data-ttu-id="9c6ab-122">패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6ab-122">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="9c6ab-123">다음 단원</span><span class="sxs-lookup"><span data-stu-id="9c6ab-123">Next Lesson</span></span>  
 [<span data-ttu-id="9c6ab-124">5단원: 패키지 배포 모델을 위한 패키지 구성 추가</span><span class="sxs-lookup"><span data-stu-id="9c6ab-124">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c6ab-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c6ab-125">See Also</span></span>  
 [<span data-ttu-id="9c6ab-126">프로젝트 및 패키지 실행</span><span class="sxs-lookup"><span data-stu-id="9c6ab-126">Execution of Projects and Packages</span></span>](packages/run-integration-services-ssis-packages.md)  
  
  
