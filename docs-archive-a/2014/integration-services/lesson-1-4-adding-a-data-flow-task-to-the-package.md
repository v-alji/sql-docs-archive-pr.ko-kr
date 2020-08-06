---
title: '4단계: 패키지에 데이터 흐름 태스크 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4fda1de99e9fcaa683f9063e2feb1b71886a5cd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651130"
---
# <a name="step-4-adding-a-data-flow-task-to-the-package"></a><span data-ttu-id="7935b-102">4단계: 패키지에 Data Flow Task 추가</span><span class="sxs-lookup"><span data-stu-id="7935b-102">Step 4: Adding a Data Flow Task to the Package</span></span>
  <span data-ttu-id="7935b-103">원본 및 대상 데이터의 연결 관리자를 만든 후에는 패키지에 데이터 흐름 태스크를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-103">After you have created the connection managers for the source and destination data, the next task is to add a Data Flow task to your package.</span></span> <span data-ttu-id="7935b-104">데이터 흐름 태스크는 원본과 대상 사이에 데이터를 이동하는 데이터 흐름 엔진을 캡슐화하여 데이터 이동 시 데이터를 변환, 정리 및 수정하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-104">The Data Flow task encapsulates the data flow engine that moves data between sources and destinations, and provides the functionality for transforming, cleaning, and modifying data as it is moved.</span></span> <span data-ttu-id="7935b-105">데이터 흐름 태스크에서 대부분의 ETL(추출, 변환 및 로드) 프로세스 작업이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-105">The Data Flow task is where most of the work of an extract, transform, and load (ETL) process occurs.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="7935b-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]데이터 흐름을 제어 흐름과 분리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-106">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separates data flow from control flow.</span></span>  
  
### <a name="to-add-a-data-flow-task"></a><span data-ttu-id="7935b-107">데이터 흐름 태스크를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="7935b-107">To add a Data Flow task</span></span>  
  
1.  <span data-ttu-id="7935b-108">**제어 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-108">Click the **Control Flow** tab.</span></span>  
  
2.  <span data-ttu-id="7935b-109">**SSIS 도구 상자**에서 **즐겨찾기**를 확장하고 **데이터 흐름 태스크** 를 **제어 흐름** 탭의 디자인 화면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-109">In the **SSIS Toolbox**, expand **Favorites**, and drag a **Data Flow Task** onto the design surfaceof the **Control Flow** tab.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7935b-110">SSIS 도구 상자를 사용할 수 없는 경우 기본 메뉴에서 SSIS 다음에 SSIS 도구 상자를 선택하여 SSIS 도구 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-110">If the SSIS Toolbox isn't available, on the main menu select SSIS then SSIS Toolbox to display the SSIS Toolbox.</span></span>  
  
3.  <span data-ttu-id="7935b-111">**제어 흐름** 디자인 화면에서 새로 추가한 **데이터 흐름 태스크**를 마우스 오른쪽 단추로 클릭 하 고 이름 **바꾸기**를 클릭 한 다음 이름을로 변경 `Extract Sample Currency Data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-111">On the **Control Flow** design surface, right-click the newly added **Data Flow Task**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
     <span data-ttu-id="7935b-112">디자인 화면에 추가한 모든 구성 요소에 고유한 이름을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-112">It is good practice to provide unique names to all components that you add to a design surface.</span></span> <span data-ttu-id="7935b-113">사용 및 유지 관리의 편의를 위해 각 구성 요소가 수행하는 기능을 나타내는 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-113">For ease of use and maintainability, the names should describe the function that each component performs.</span></span> <span data-ttu-id="7935b-114">이러한 명명 지침을 따르면 이해하기 쉬운 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-114">Following these naming guidelines allows your [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to be self-documenting.</span></span> <span data-ttu-id="7935b-115">주석을 사용하여 패키지를 설명할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-115">Another way to document your packages is by using annotations.</span></span> <span data-ttu-id="7935b-116">주석에 대한 자세한 내용은 [패키지에서 주석 사용](use-annotations-in-packages.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7935b-116">For more information about annotations, see [Use Annotations in Packages](use-annotations-in-packages.md).</span></span>  
  
4.  <span data-ttu-id="7935b-117">데이터 흐름 태스크를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 한 다음 속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7935b-117">Right-click the Data Flow task, click **Properties**, and in the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7935b-118">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="7935b-118">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7935b-119">5단계: 플랫 파일 원본 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="7935b-119">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
## <a name="see-also"></a><span data-ttu-id="7935b-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7935b-120">See Also</span></span>  
 [<span data-ttu-id="7935b-121">데이터 흐름 태스크</span><span class="sxs-lookup"><span data-stu-id="7935b-121">Data Flow Task</span></span>](control-flow/data-flow-task.md)  
  
  
