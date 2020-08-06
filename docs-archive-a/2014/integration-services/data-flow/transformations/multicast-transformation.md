---
title: 멀티캐스트 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b5c0a38c966c89f426a213f302b45c390b77cfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743427"
---
# <a name="multicast-transformation"></a><span data-ttu-id="c0c54-102">멀티캐스트 변환</span><span class="sxs-lookup"><span data-stu-id="c0c54-102">Multicast Transformation</span></span>
  <span data-ttu-id="c0c54-103">멀티캐스트 변환은 입력을 하나 이상의 출력으로 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-103">The Multicast transformation distributes its input to one or more outputs.</span></span> <span data-ttu-id="c0c54-104">이 변환은 조건부 분할 변환과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-104">This transformation is similar to the Conditional Split transformation.</span></span> <span data-ttu-id="c0c54-105">둘 다 입력을 여러 출력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-105">Both transformations direct an input to multiple outputs.</span></span> <span data-ttu-id="c0c54-106">두 변환의 차이점은 멀티캐스트 변환은 모든 행을 모든 출력으로 보내고 조건부 분할은 한 행을 단일 출력으로 보낸다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-106">The difference between the two is that the Multicast transformation directs every row to every output, and the Conditional Split directs a row to a single output.</span></span> <span data-ttu-id="c0c54-107">자세한 내용은 [Conditional Split Transformation](conditional-split-transformation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c54-107">For more information, see [Conditional Split Transformation](conditional-split-transformation.md).</span></span>  
  
 <span data-ttu-id="c0c54-108">출력을 추가하여 멀티캐스트 변환을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-108">You configure the Multicast transformation by adding outputs.</span></span>  
  
 <span data-ttu-id="c0c54-109">패키지는 멀티캐스트 변환을 사용하여 데이터의 논리적 복사본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-109">Using the Multicast transformation, a package can create logical copies of data.</span></span> <span data-ttu-id="c0c54-110">이 기능은 패키지가 동일한 데이터에 여러 변환 집합을 적용해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-110">This capability is useful when the package needs to apply multiple sets of transformations to the same data.</span></span> <span data-ttu-id="c0c54-111">예를 들어 하나의 데이터 복사본이 집계되고 요약 정보만 대상에 로드되지만 대상에 로드되기 전에 조회 값과 파생 열을 사용하여 다른 데이터 복사본이 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-111">For example, one copy of the data is aggregated and only the summary information is loaded into its destination, while another copy of the data is extended with lookup values and derived columns before it is loaded into its destination.</span></span>  
  
 <span data-ttu-id="c0c54-112">이 변환은 하나의 입력과 여러 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="c0c54-112">This transformation has one input and multiple outputs.</span></span> <span data-ttu-id="c0c54-113">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-113">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-multicast-transformation"></a><span data-ttu-id="c0c54-114">멀티캐스트 변환 구성</span><span class="sxs-lookup"><span data-stu-id="c0c54-114">Configuration of the Multicast Transformation</span></span>  
 <span data-ttu-id="c0c54-115">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0c54-115">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c0c54-116">**멀티캐스트 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Multicast Transformation Editor](../../multicast-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0c54-116">For information about the properties that you can set in the **Multicast Transformation Editor** dialog box, see [Multicast Transformation Editor](../../multicast-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="c0c54-117">프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용은 [Common Properties](../../common-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c0c54-117">For information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c0c54-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="c0c54-118">Related Tasks</span></span>  
 <span data-ttu-id="c0c54-119">이 구성 요소의 속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c0c54-119">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c54-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c0c54-120">See Also</span></span>  
 <span data-ttu-id="c0c54-121">[데이터 흐름](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="c0c54-121">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="c0c54-122">Integration Services 변환</span><span class="sxs-lookup"><span data-stu-id="c0c54-122">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
