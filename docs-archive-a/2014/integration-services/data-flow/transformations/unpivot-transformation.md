---
title: 피벗 해제 변환 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unpivottrans.f1
helpviewer_keywords:
- Unpivot transformation
- more normalized data set [Integration Services]
- normalized data [Integration Services]
- datasets [Integration Services], normalized data
ms.assetid: f635c64b-a9c5-4f11-9c40-9cd9d5298c5d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e605dc4827a885b5dc65fbb680cce8a434b89fd5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659548"
---
# <a name="unpivot-transformation"></a><span data-ttu-id="ffb56-102">피벗 해제 변환</span><span class="sxs-lookup"><span data-stu-id="ffb56-102">Unpivot Transformation</span></span>
  <span data-ttu-id="ffb56-103">피벗 해제 변환은 단일 레코드의 여러 열 값을 단일 열에 동일 값이 포함된 여러 레코드로 확장하여 정규화되지 않은 데이터 세트를 정규화된 버전으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-103">The Unpivot transformation makes an unnormalized dataset into a more normalized version by expanding values from multiple columns in a single record into multiple records with the same values in a single column.</span></span> <span data-ttu-id="ffb56-104">예를 들어 고객 이름이 나열된 데이터 세트에 각 고객마다 하나의 행이 있고 행의 열에 제품 및 구매 수량이 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-104">For example, a dataset that lists customer names has one row for each customer, with the products and the quantity purchased shown in columns in the row.</span></span> <span data-ttu-id="ffb56-105">피벗 해제 변환으로 데이터 집합을 정규화하면 데이터 집합에 고객이 구매한 각 제품이 서로 다른 행에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-105">After the Unpivot transformation normalizes the data set, the data set contains a different row for each product that the customer purchased.</span></span>  
  
 <span data-ttu-id="ffb56-106">다음 다이어그램에서는 Product 열로 데이터를 피벗 해제하기 전의 데이터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-106">The following diagram shows a data set before the data is unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="ffb56-107">![피벗 해제 후의 데이터 세트](../../media/mw-dts-18.gif "피벗 해제 후의 데이터 세트")</span><span class="sxs-lookup"><span data-stu-id="ffb56-107">![Dataset after it is unpivoted](../../media/mw-dts-18.gif "Dataset after it is unpivoted")</span></span>  
  
 <span data-ttu-id="ffb56-108">다음 다이어그램에서는 Product 열로 데이터를 피벗 해제한 후의 데이터 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-108">The following diagram shows a data set after it has been unpivoted on the Product column.</span></span>  
  
 <span data-ttu-id="ffb56-109">![피벗 해제 전의 데이터 세트](../../media/mw-dts-17.gif "피벗 해제 전의 데이터 세트")</span><span class="sxs-lookup"><span data-stu-id="ffb56-109">![Dataset before it is unpivoted](../../media/mw-dts-17.gif "Dataset before it is unpivoted")</span></span>  
  
 <span data-ttu-id="ffb56-110">일부 경우에는 피벗 해제된 결과에 예기치 않은 값이 있는 행이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-110">Under some circumstances, the unpivot results may contain rows with unexpected values.</span></span> <span data-ttu-id="ffb56-111">예를 들어 다이어그램에 표시된 피벗 해제할 예제 데이터에서 Fred의 모든 Qty 열에 null 값이 있으면 출력에는 Fred에 대한 행이 다섯 개가 아니라 한 개만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-111">For example, if the sample data to unpivot shown in the diagram had null values in all the Qty columns for Fred, then the output would include only one row for Fred, not five.</span></span> <span data-ttu-id="ffb56-112">Qty 열에는 해당 열 데이터 형식에 따라 null이나 0이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-112">The Qty column would contain either null or zero, depending on the column data type.</span></span>  
  
## <a name="configuration-of-the-unpivot-transformation"></a><span data-ttu-id="ffb56-113">피벗 해제 변환 구성</span><span class="sxs-lookup"><span data-stu-id="ffb56-113">Configuration of the Unpivot Transformation</span></span>  
 <span data-ttu-id="ffb56-114">피벗 해제 변환에는 `PivotKeyValue` 사용자 지정 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-114">The Unpivot transformation includes the `PivotKeyValue` custom property.</span></span> <span data-ttu-id="ffb56-115">이 속성은 패키지가 로드되면 속성 식을 사용하여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-115">This property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="ffb56-116">자세한 내용은 [Integration Services&#40;SSIS&#41; 식](../../expressions/integration-services-ssis-expressions.md), [패키지에서 속성 식 사용](../../expressions/use-property-expressions-in-packages.md) 및 [변환 사용자 지정 속성](transformation-custom-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ffb56-116">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="ffb56-117">이 변환은 하나의 입력과 하나의 출력을 가지며</span><span class="sxs-lookup"><span data-stu-id="ffb56-117">This transformation has one input and one output.</span></span> <span data-ttu-id="ffb56-118">오류 출력은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-118">It has no error output.</span></span>  
  
 <span data-ttu-id="ffb56-119">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb56-119">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ffb56-120">**피벗 해제 변환 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="ffb56-120">For more information about the properties that you can set in the **Unpivot Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ffb56-121">피벗 해제 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="ffb56-121">Unpivot Transformation Editor</span></span>](../../unpivot-transformation-editor.md)  
  
 <span data-ttu-id="ffb56-122">**고급 편집기** 대화 상자를 사용하거나 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="ffb56-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ffb56-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ffb56-123">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="ffb56-124">변환 사용자 지정 속성</span><span class="sxs-lookup"><span data-stu-id="ffb56-124">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
 <span data-ttu-id="ffb56-125">속성을 설정하는 방법에 대한 자세한 내용은 [데이터 흐름 구성 요소의 속성 설정](../set-the-properties-of-a-data-flow-component.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ffb56-125">For more information about how to set the properties, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
  
