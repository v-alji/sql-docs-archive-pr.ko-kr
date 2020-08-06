---
title: '2단계: 손상된 파일 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: cd0b18dc-66c3-4d88-86ef-8e40cb660fae
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0dd5fbe942774192881489e9ea430672f9da5083
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650172"
---
# <a name="step-2-creating-a-corrupted-file"></a><span data-ttu-id="ee92d-102">2단계: 손상된 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ee92d-102">Step 2: Creating a Corrupted File</span></span>
  <span data-ttu-id="ee92d-103">변환 오류의 구성 및 처리를 보여 주기 위해 처리 시 구성 요소의 실패를 야기하는 예제 플랫 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-103">In order to demonstrate the configuration and handling of transformation errors, you will have to create a sample flat file that when processed causes a component to fail.</span></span>  
  
 <span data-ttu-id="ee92d-104">이 태스크에서는 기존 예제 플랫 파일의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-104">In this task, you will create a copy of an existing sample flat file.</span></span> <span data-ttu-id="ee92d-105">그런 다음 메모장에서 해당 파일을 열고 변환 조회를 수행하는 동안 일치 항목을 생성하지 못하도록 **CurrencyID** 열을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-105">You will then open the file in Notepad and edit the **CurrencyID** column to ensure that it will fail to produce a match during the transformations lookup.</span></span> <span data-ttu-id="ee92d-106">이 새 파일을 처리하면 조회 실패로 Currency Key Lookup 변환이 실패하며 따라서 패키지의 나머지 부분도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-106">When the new file is processed, the lookup failure will cause the Currency Key Lookup transformation to fail and therefore fail the rest of the package.</span></span> <span data-ttu-id="ee92d-107">손상된 예제 파일을 만든 다음에는 패키지를 실행하여 패키지 오류를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-107">After you have created the corrupted sample file, you will run the package to view the package failure.</span></span>  
  
### <a name="to-create-a-corrupted-sample-flat-file"></a><span data-ttu-id="ee92d-108">손상된 예제 플랫 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ee92d-108">To create a corrupted sample flat file</span></span>  
  
1.  <span data-ttu-id="ee92d-109">메모장이나 기타 텍스트 편집기에서 Currency_VEB.txt 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-109">In Notepad or any other text editor, open the Currency_VEB.txt file.</span></span>  
  
     <span data-ttu-id="ee92d-110">예제 데이터는 SSIS 단원 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-110">The sample data is included with the SSIS Lesson packages.</span></span> <span data-ttu-id="ee92d-111">예제 데이터 및 단원 패키지를 다운로드하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-111">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="ee92d-112">[Integration Services 제품 샘플](https://go.microsoft.com/fwlink/?LinkID=267527)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-112">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkID=267527).</span></span>  
  
    2.  <span data-ttu-id="ee92d-113">**다운로드** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-113">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="ee92d-114">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip 파일을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-114">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
2.  <span data-ttu-id="ee92d-115">텍스트 편집기의 찾기 및 바꾸기 기능을 사용 하 여의 모든 인스턴스를 찾아 `VEB` 로 바꿉니다 `BAD` .</span><span class="sxs-lookup"><span data-stu-id="ee92d-115">Use the text editor's find and replace feature to find all instances of `VEB` and replace them with `BAD`.</span></span>  
  
3.  <span data-ttu-id="ee92d-116">다른 예제 데이터 파일과 동일한 폴더에서 수정 된 파일을로 저장 합니다 `Currency_BAD.txt` .</span><span class="sxs-lookup"><span data-stu-id="ee92d-116">In the same folder as the other sample data files, save the modified file as `Currency_BAD.txt`.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="ee92d-117">`Currency_BAD.txt`이 다른 예제 데이터 파일과 동일한 폴더에 저장 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-117">Make sure that `Currency_BAD.txt` is saved the same folder as the other sample data files.</span></span>  
  
4.  <span data-ttu-id="ee92d-118">텍스트 편집기를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-118">Close your text editor.</span></span>  
  
### <a name="to-verify-that-an-error-will-occur-during-run-time"></a><span data-ttu-id="ee92d-119">런타임 도중 오류가 발생하는지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="ee92d-119">To verify that an error will occur during run time</span></span>  
  
1.  <span data-ttu-id="ee92d-120">**디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-120">On the **Debug** menu, click **Start Debugging**.</span></span>  
  
     <span data-ttu-id="ee92d-121">세 번째 데이터 흐름 반복에서 Lookup Currency Key 변환은 Currency_BAD.txt 파일을 처리하려고 하며 여기서 변환이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-121">On the third iteration of the data flow, the Lookup Currency Key transformation tries to process the Currency_BAD.txt file, and the transformation will fail.</span></span> <span data-ttu-id="ee92d-122">변환 실패로 인해 전체 패키지가 실패하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-122">The failure of the transformation will cause the whole package to fail.</span></span>  
  
2.  <span data-ttu-id="ee92d-123">**디버그** 메뉴에서 **디버깅 중지**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-123">On the **Debug** menu, click **Stop Debugging**.</span></span>  
  
3.  <span data-ttu-id="ee92d-124">디자인 화면에서 **실행 결과** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-124">On the design surface, click the **Execution Results** tab.</span></span>  
  
4.  <span data-ttu-id="ee92d-125">로그를 찾아보고 다음의 처리되지 않은 오류가 발생했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-125">Browse through the log and verify that the following unhandled error occurred:</span></span>  
  
     `[Lookup Currency Key[27]] Error: Row yielded no match during lookup.`  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee92d-126">27은 구성 요소의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-126">The number 27 is the ID of the component.</span></span> <span data-ttu-id="ee92d-127">이 값은 데이터 흐름을 작성할 때 할당되며 패키지 값과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee92d-127">This value is assigned when you build the data flow, and the value in your package may be different.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ee92d-128">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ee92d-128">Next Steps</span></span>  
 [<span data-ttu-id="ee92d-129">3단계: 오류 Flow 리디렉션 추가</span><span class="sxs-lookup"><span data-stu-id="ee92d-129">Step 3: Adding Error Flow Redirection</span></span>](lesson-4-3-adding-error-flow-redirection.md)  
  
  
