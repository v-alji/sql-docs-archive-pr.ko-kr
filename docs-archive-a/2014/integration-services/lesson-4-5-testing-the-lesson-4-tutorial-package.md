---
title: '5단계: 4단원 자습서 패키지 테스트 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a897f99bf68805e4e66c3b6bbe818b312077fb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735464"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a><span data-ttu-id="35d1a-102">5단계: 4단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="35d1a-102">Step 5: Testing the Lesson 4 Tutorial Package</span></span>
  <span data-ttu-id="35d1a-103">런타임에 손상된 파일인 Currency_BAD.txt가 있으면 Currency Key Lookup 변환에서 일치 항목을 생성하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-103">At run time, the corrupted file, Currency_BAD.txt, will fail to generate a match within the Currency Key Lookup transformation.</span></span> <span data-ttu-id="35d1a-104">이제 Currency Key Lookup의 오류 출력이 실패한 행을 새 실패한 행 대상으로 리디렉션하도록 구성되었으므로 해당 구성 요소가 실패하지 않으며 패키지가 성공적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-104">Because the error output of Currency Key Lookup has now been configured to redirect failed rows to the new Failed Rows destination, the component does not fail, and the package runs successfully.</span></span> <span data-ttu-id="35d1a-105">실패한 모든 오류 행은 ErrorOutput.txt에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-105">All failed error rows are written to ErrorOutput.txt.</span></span>  
  
 <span data-ttu-id="35d1a-106">이 태스크에서는 패키지를 실행하여 수정된 오류 출력 구성을 테스트한 다음</span><span class="sxs-lookup"><span data-stu-id="35d1a-106">In this task, you will test the revised error output configuration by running the package.</span></span> <span data-ttu-id="35d1a-107">패키지 실행 성공 여부에 따라 ErrorOutput.txt 파일의 내용을 표시하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-107">Upon successful package execution, you will then view the contents of the ErrorOutput.txt file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35d1a-108">ErrorOutput.txt 파일에 오류 행이 누적되지 않도록 하려면 패키지 실행 사이에 파일 내용을 직접 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-108">If you do not want to accumulate error rows in the ErrorOutput.txt file, you should manually delete the file content between package runs.</span></span>  
  
## <a name="checking-the-package-layout"></a><span data-ttu-id="35d1a-109">패키지 레이아웃 확인</span><span class="sxs-lookup"><span data-stu-id="35d1a-109">Checking the Package layout</span></span>  
 <span data-ttu-id="35d1a-110">패키지를 테스트하려면 먼저 4단원 패키지의 제어 흐름과 데이터 흐름에 다음 다이어그램에 표시된 개체가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-110">Before you test the package you should verify that the control flow and the data flow in the Lesson 4 package contain the objects shown in the following diagrams.</span></span> <span data-ttu-id="35d1a-111">제어 흐름은 2-4단원의 제어 흐름과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-111">The control flow should be identical to the control flow in lessons 2 - 4.</span></span>  
  
 <span data-ttu-id="35d1a-112">**제어 흐름**</span><span class="sxs-lookup"><span data-stu-id="35d1a-112">**Control Flow**</span></span>  
  
 <span data-ttu-id="35d1a-113">![패키지의 제어 흐름](../../2014/tutorials/media/task4lesson2control.gif "패키지의 제어 흐름")</span><span class="sxs-lookup"><span data-stu-id="35d1a-113">![Control flow in package](../../2014/tutorials/media/task4lesson2control.gif "Control flow in package")</span></span>  
  
 <span data-ttu-id="35d1a-114">**데이터 흐름**</span><span class="sxs-lookup"><span data-stu-id="35d1a-114">**Data Flow**</span></span>  
  
 <span data-ttu-id="35d1a-115">![패키지의 데이터 흐름](../../2014/tutorials/media/task5lesson5data.gif "패키지의 데이터 흐름")</span><span class="sxs-lookup"><span data-stu-id="35d1a-115">![Data flow in package](../../2014/tutorials/media/task5lesson5data.gif "Data flow in package")</span></span>  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a><span data-ttu-id="35d1a-116">4단원 자습서 패키지를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="35d1a-116">To run the Lesson 4 tutorial package</span></span>  
  
1.  <span data-ttu-id="35d1a-117">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-117">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
2.  <span data-ttu-id="35d1a-118">패키지의 실행이 완료된 후에 **디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-118">After the package has completed running, on the **Debug** menu, click **Stop Debugging**.</span></span>  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a><span data-ttu-id="35d1a-119">ErrorOutput.txt 파일의 내용을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="35d1a-119">To verify the contents of the ErrorOutput.txt file</span></span>  
  
-   <span data-ttu-id="35d1a-120">메모장이나 텍스트 편집기에서 ErrorOutput.txt 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-120">In Notepad or any other text editor, open the ErrorOutput.txt file.</span></span> <span data-ttu-id="35d1a-121">기본 열 순서는 AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription입니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-121">The default column order is: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.</span></span>  
  
     <span data-ttu-id="35d1a-122">파일의 모든 행에 일치하지 않는 CurrencyID 값인 BAD, ErrorCode 값인 -1071607778, ErrorColumn 값인 0 및 ErrorDescription 값인 "조회 중에 행에서 일치하는 항목을 생성하지 않았습니다"가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-122">Notice that all the rows in the file contain the unmatched CurrencyID value of BAD, the ErrorCode value of -1071607778, the ErrorColumn value of 0, and the ErrorDescription value "Row yielded no match during lookup".</span></span> <span data-ttu-id="35d1a-123">열 관련 오류가 아니라 조회 작업 오류이므로</span><span class="sxs-lookup"><span data-stu-id="35d1a-123">The value of the ErrorColumn is set to 0 because the error is not column specific.</span></span> <span data-ttu-id="35d1a-124">ErrorColumn 값은 0으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="35d1a-124">It is the lookup operation that failed.</span></span> <span data-ttu-id="35d1a-125">.</span><span class="sxs-lookup"><span data-stu-id="35d1a-125">.</span></span>  
  
  
