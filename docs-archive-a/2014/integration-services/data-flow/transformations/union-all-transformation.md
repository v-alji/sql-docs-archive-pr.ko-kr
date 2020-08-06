---
title: UNION ALL 변환 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltrans.f1
helpviewer_keywords:
- merging datasets [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 942e4b90-9c41-4e9c-a6f3-80b3afe57f2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eaaab1abf2587979e947cc1be24cbedf8f61b6e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659552"
---
# <a name="union-all-transformation"></a><span data-ttu-id="37c6b-102">UNION ALL 변환</span><span class="sxs-lookup"><span data-stu-id="37c6b-102">Union All Transformation</span></span>
  <span data-ttu-id="37c6b-103">UNION ALL 변환은 여러 개의 입력을 하나의 출력으로 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-103">The Union All transformation combines multiple inputs into one output.</span></span> <span data-ttu-id="37c6b-104">예를 들어 5개 플랫 파일 원본의 출력이 UNION ALL 변환의 입력이 되어 하나의 출력으로 결합될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-104">For example, the outputs from five different Flat File sources can be inputs to the Union All transformation and combined into one output.</span></span>  
  
## <a name="inputs-and-outputs"></a><span data-ttu-id="37c6b-105">입/출력</span><span class="sxs-lookup"><span data-stu-id="37c6b-105">Inputs and Outputs</span></span>  
 <span data-ttu-id="37c6b-106">변환 입력은 하나씩 변환 출력에 추가되며 행이 다시 정렬되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-106">The transformation inputs are added to the transformation output one after the other; no reordering of rows occurs.</span></span> <span data-ttu-id="37c6b-107">패키지에 정렬된 출력이 필요할 경우 UNION ALL 변환 대신 병합 변환을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-107">If the package requires a sorted output, you should use the Merge transformation instead of the Union All transformation.</span></span>  
  
 <span data-ttu-id="37c6b-108">UNION ALL 변환에 연결한 첫 번째 입력이 변환 출력을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-108">The first input that you connect to the Union All transformation is the input from which the transformation creates the transformation output.</span></span> <span data-ttu-id="37c6b-109">변환에 연결한 이후 입력 열은 변환 출력 열에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-109">The columns in the inputs you subsequently connect to the transformation are mapped to the columns in the transformation output.</span></span>  
  
 <span data-ttu-id="37c6b-110">입력을 병합하려면 입력 열을 출력 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-110">To merge inputs, you map columns in the inputs to columns in the output.</span></span> <span data-ttu-id="37c6b-111">하나 이상의 입력 열을 각 출력 열에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-111">A column from at least one input must be mapped to each output column.</span></span> <span data-ttu-id="37c6b-112">두 열을 매핑하려면 해당 열의 메타데이터가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-112">The mapping between two columns requires that the metadata of the columns match.</span></span> <span data-ttu-id="37c6b-113">예를 들어 매핑된 열의 데이터 형식이 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-113">For example, the mapped columns must have the same data type.</span></span>  
  
 <span data-ttu-id="37c6b-114">매핑된 열에 문자열 데이터가 포함되어 있고 출력 열의 길이가 입력 열보다 짧으면 입력 열을 포함할 수 있도록 출력 열의 길이가 자동으로 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-114">If the mapped columns contain string data and the output column is shorter in length than the input column, the output column is automatically increased in length to contain the input column.</span></span> <span data-ttu-id="37c6b-115">출력 열에 매핑되지 않은 입력 열은 출력 열에서 Null 값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-115">Input columns that are not mapped to output columns are set to null values in the output columns.</span></span>  
  
 <span data-ttu-id="37c6b-116">이 변환에는 여러 개의 입력과 하나의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-116">This transformation has multiple inputs and one output.</span></span> <span data-ttu-id="37c6b-117">오류 출력은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-117">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-union-all-transformation"></a><span data-ttu-id="37c6b-118">UNION ALL 변환 구성</span><span class="sxs-lookup"><span data-stu-id="37c6b-118">Configuration of the Union All Transformation</span></span>  
 <span data-ttu-id="37c6b-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="37c6b-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="37c6b-120">**UNION ALL 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용은 [Union All Transformation Editor](../../union-all-transformation-editor.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="37c6b-120">For more information about the properties that you can set in the **Union All Transformation Editor** dialog box, see [Union All Transformation Editor](../../union-all-transformation-editor.md).</span></span>  
  
 <span data-ttu-id="37c6b-121">프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용은 [Common Properties](../../common-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="37c6b-121">For more information about the properties that you can set programmatically, see [Common Properties](../../common-properties.md).</span></span>  
  
 <span data-ttu-id="37c6b-122">속성 설정 방법을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="37c6b-122">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="37c6b-123">데이터 흐름 구성 요소의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="37c6b-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="37c6b-124">관련 작업</span><span class="sxs-lookup"><span data-stu-id="37c6b-124">Related Tasks</span></span>  
 [<span data-ttu-id="37c6b-125">UNION ALL 변환을 사용하여 데이터 병합</span><span class="sxs-lookup"><span data-stu-id="37c6b-125">Merge Data by Using the Union All Transformation</span></span>](union-all-transformation.md)  
  
  
