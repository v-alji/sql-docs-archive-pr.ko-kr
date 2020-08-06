---
title: 변환을 사용하여 데이터 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952d8ea4eeea2dd8010a17a2b3deba41447b6231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660698"
---
# <a name="transform-data-with-transformations"></a><span data-ttu-id="ec6f3-102">변환을 사용하여 데이터 변환</span><span class="sxs-lookup"><span data-stu-id="ec6f3-102">Transform Data with Transformations</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="ec6f3-103">에는 원본, 변환 및 대상 등 3가지 유형의 데이터 흐름 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-103">includes three types of data flow components: sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="ec6f3-104">다음 다이어그램에서는 원본 하나, 변환 두 가지, 대상 하나를 포함하는 간단한 데이터 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-104">The following diagram shows a simple data flow that has a source, two transformations, and a destination.</span></span>  
  
 <span data-ttu-id="ec6f3-105">![데이터 흐름](../../media/mw-dts-08.gif "디자이너의")</span><span class="sxs-lookup"><span data-stu-id="ec6f3-105">![Data flow](../../media/mw-dts-08.gif "Data flow")</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="ec6f3-106">변환은 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-106">transformations provide the following functionality:</span></span>  
  
-   <span data-ttu-id="ec6f3-107">행 집합을 분할, 복사 및 병합하고 조회 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-107">Splitting, copying, and merging rowsets and performing lookup operations.</span></span>  
  
-   <span data-ttu-id="ec6f3-108">소문자를 대문자로 변경하는 것과 같은 변환을 적용하여 열 값을 업데이트하고 새 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-108">Updating column values and creating new columns by applying transformations such as changing lowercase to uppercase.</span></span>  
  
-   <span data-ttu-id="ec6f3-109">데이터 정리, 텍스트 마이닝 및 데이터 마이닝 예측 쿼리 실행과 같은 비즈니스 인텔리전스 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-109">Performing business intelligence operations such as cleaning data, mining text, or running data mining prediction queries.</span></span>  
  
-   <span data-ttu-id="ec6f3-110">집계 또는 정렬된 값, 예제 데이터 또는 피벗되거나 피벗되지 않은 데이터로 구성되는 새 행 집합을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-110">Creating new rowsets that consist of aggregate or sorted values, sample data, or pivoted and unpivoted data.</span></span>  
  
-   <span data-ttu-id="ec6f3-111">데이터 내보내기 및 가져오기, 감사 정보 제공, 느린 변경 차원 작업과 같은 태스크를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-111">Performing tasks such as exporting and importing data, providing audit information, and working with slowly changing dimensions.</span></span>  
  
 <span data-ttu-id="ec6f3-112">자세한 내용은 [Integration Services Transformations](integration-services-transformations.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-112">For more information, see [Integration Services Transformations](integration-services-transformations.md).</span></span>  
  
 <span data-ttu-id="ec6f3-113">사용자 지정 변환을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-113">You can also write custom transformations.</span></span> <span data-ttu-id="ec6f3-114">자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 및 [특정 유형의 데이터 흐름 구성 요소 개발](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-114">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) and [Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).</span></span>  
  
 <span data-ttu-id="ec6f3-115">데이터 흐름 디자이너에 변환을 추가한 다음 변환을 구성하기 전에 다른 변환 또는 데이터 흐름의 원본을 이 변환의 입력에 연결하여 데이터 흐름에 변환을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-115">After you add the transformation to the data flow designer, but before you configure the transformation, you connect the transformation to the data flow by connecting the output of another transformation or source in the data flow to the input of this transformation.</span></span> <span data-ttu-id="ec6f3-116">두 데이터 흐름 구성 요소 간 연결선을 경로라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-116">The connector between two data flow components is called a path.</span></span> <span data-ttu-id="ec6f3-117">구성 요소 연결 및 경로 사용 방법은 [경로에 구성 요소 연결](../../connect-components-with-paths.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec6f3-117">For more information about connecting components and working with paths, see [Connect Components with Paths](../../connect-components-with-paths.md).</span></span>  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a><span data-ttu-id="ec6f3-118">데이터 흐름에 변환을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ec6f3-118">To add a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="ec6f3-119">데이터 흐름에서 구성 요소 추가 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="ec6f3-119">Add or Delete a Component in a Data Flow</span></span>](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a><span data-ttu-id="ec6f3-120">데이터 흐름에서 변환을 연결하려면</span><span class="sxs-lookup"><span data-stu-id="ec6f3-120">To connect a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="ec6f3-121">데이터 흐름의 구성 요소 연결</span><span class="sxs-lookup"><span data-stu-id="ec6f3-121">Connect Components in a Data Flow</span></span>](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a><span data-ttu-id="ec6f3-122">변환의 속성을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="ec6f3-122">To set the properties of a transformation</span></span>  
  
-   [<span data-ttu-id="ec6f3-123">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="ec6f3-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="ec6f3-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec6f3-124">See Also</span></span>  
 <span data-ttu-id="ec6f3-125">[데이터 흐름 태스크](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="ec6f3-125">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 <span data-ttu-id="ec6f3-126">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="ec6f3-126">[Data Flow](../data-flow.md) </span></span>  
 <span data-ttu-id="ec6f3-127">[경로에 구성 요소 연결](../../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="ec6f3-127">[Connect Components with Paths](../../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="ec6f3-128">[데이터 오류 처리](../error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="ec6f3-128">[Error Handling in Data](../error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="ec6f3-129">데이터 흐름</span><span class="sxs-lookup"><span data-stu-id="ec6f3-129">Data Flow</span></span>](../data-flow.md)  
  
  
