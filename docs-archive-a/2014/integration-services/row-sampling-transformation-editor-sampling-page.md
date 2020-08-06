---
title: 행 샘플링 변환 편집기 (샘플링 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729580"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a><span data-ttu-id="b5631-102">행 샘플링 변환 편집기(샘플링 페이지)</span><span class="sxs-lookup"><span data-stu-id="b5631-102">Row Sampling Transformation Editor (Sampling Page)</span></span>
  <span data-ttu-id="b5631-103">**행 샘플링 변환 편집기** 대화 상자를 사용하여 입력의 일부분을 지정된 행 수를 사용하는 샘플로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-103">Use the **Row Sampling Transformation Editor** dialog box to split a portion of an input into a sample using a specified number of rows.</span></span> <span data-ttu-id="b5631-104">이 변환으로 인해 입력이 두 개의 별도 출력으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-104">This transformation divides the input into two separate outputs.</span></span>  
  
 <span data-ttu-id="b5631-105">행 샘플링 변환에 대한 자세한 내용은 [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b5631-105">To learn more about the Row Sampling transformation, see [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5631-106">옵션</span><span class="sxs-lookup"><span data-stu-id="b5631-106">Options</span></span>  
 <span data-ttu-id="b5631-107">**행 수**</span><span class="sxs-lookup"><span data-stu-id="b5631-107">**Number of rows**</span></span>  
 <span data-ttu-id="b5631-108">입력에서 샘플로 사용할 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-108">Specify the number of rows from the input to use as a sample.</span></span>  
  
 <span data-ttu-id="b5631-109">이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-109">The value of this property can be specified by using a property expression.</span></span>  
  
 <span data-ttu-id="b5631-110">**샘플 출력 이름**</span><span class="sxs-lookup"><span data-stu-id="b5631-110">**Sample output name**</span></span>  
 <span data-ttu-id="b5631-111">샘플링한 행이 포함될 출력에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-111">Provide a unique name for the output that will include the sampled rows.</span></span> <span data-ttu-id="b5631-112">제공한 이름은 SSIS 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-112">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="b5631-113">**선택하지 않은 출력 이름**</span><span class="sxs-lookup"><span data-stu-id="b5631-113">**Unselected output name**</span></span>  
 <span data-ttu-id="b5631-114">샘플링에서 제외된 행이 포함될 출력에 사용할 고유 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-114">Provide a unique name for the output that will contain the rows excluded from the sampling.</span></span> <span data-ttu-id="b5631-115">제공한 이름은 SSIS 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-115">The name provided will be displayed within SSIS Designer.</span></span>  
  
 <span data-ttu-id="b5631-116">**다음과 같은 임의 초기값 사용**</span><span class="sxs-lookup"><span data-stu-id="b5631-116">**Use the following random seed**</span></span>  
 <span data-ttu-id="b5631-117">변환에서 샘플을 만드는 데 사용하는 난수 생성기에 샘플링 초기값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-117">Specify the sampling seed for the random number generator that the transformation uses to create a sample.</span></span> <span data-ttu-id="b5631-118">이 옵션은 개발 및 테스트 용도로만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-118">This is only recommended for development and testing.</span></span> <span data-ttu-id="b5631-119">임의 초기값을 지정하지 않으면 변환에서 Microsoft Windows 틱 수를 초기값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b5631-119">The transformation uses the Microsoft Windows tick count as a seed if a random seed is not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5631-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b5631-120">See Also</span></span>  
 <span data-ttu-id="b5631-121">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="b5631-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="b5631-122">비율 샘플링 변환</span><span class="sxs-lookup"><span data-stu-id="b5631-122">Percentage Sampling Transformation</span></span>](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
