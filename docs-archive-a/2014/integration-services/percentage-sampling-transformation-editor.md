---
title: 비율 샘플링 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c4dbd96ab952b6c88bdaa7bf56a0a2f1b3585c57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647089"
---
# <a name="percentage-sampling-transformation-editor"></a><span data-ttu-id="fdd06-102">비율 샘플링 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="fdd06-102">Percentage Sampling Transformation Editor</span></span>
  <span data-ttu-id="fdd06-103">**비율 샘플링 변환 편집기** 대화 상자에서 지정한 행의 백분율을 사용하여 입력 부분을 샘플로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-103">Use the **Percentage Sampling Transformation Editor** dialog box to split part of an input into a sample using a specified percentage of rows.</span></span> <span data-ttu-id="fdd06-104">이 변환으로 인해 입력이 두 개의 별도 출력으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="fdd06-105">비율 샘플링 변환에 대한 자세한 내용은 [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fdd06-105">To learn more about the percentage sampling transformation, see [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fdd06-106">옵션</span><span class="sxs-lookup"><span data-stu-id="fdd06-106">Options</span></span>  
 <span data-ttu-id="fdd06-107">**행의 백분율**</span><span class="sxs-lookup"><span data-stu-id="fdd06-107">**Percentage of rows**</span></span>  
 <span data-ttu-id="fdd06-108">입력에서 샘플로 사용할 행의 백분율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-108">Specify the percentage of rows in the input to use as a sample.</span></span>  
  
 <span data-ttu-id="fdd06-109">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="fdd06-110">**샘플 출력 이름**</span><span class="sxs-lookup"><span data-stu-id="fdd06-110">**Sample output name**</span></span>  
 <span data-ttu-id="fdd06-111">샘플링한 행이 포함될 출력에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="fdd06-112">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-112">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="fdd06-113">**선택하지 않은 출력 이름**</span><span class="sxs-lookup"><span data-stu-id="fdd06-113">**Unselected output name**</span></span>  
 <span data-ttu-id="fdd06-114">샘플링에서 제외된 행이 포함될 출력에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="fdd06-115">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-115">The name provided will be displayed within the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="fdd06-116">**다음과 같은 임의 초기값 사용**</span><span class="sxs-lookup"><span data-stu-id="fdd06-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="fdd06-117">변환에서 샘플을 만드는 데 사용하는 난수 생성기에 샘플링 초기값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="fdd06-118">이 옵션은 개발 및 테스트 용도로만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="fdd06-119">임의 초기값을 지정하지 않으면 Microsoft Windows 틱 수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fdd06-119">The transformation uses the Microsoft Windows tick count if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd06-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fdd06-120">See Also</span></span>  
 <span data-ttu-id="fdd06-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fdd06-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="fdd06-122">행 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="fdd06-122">Row Sampling Transformation</span></span>](data-flow/transformations/row-sampling-transformation.md)  
  
  
