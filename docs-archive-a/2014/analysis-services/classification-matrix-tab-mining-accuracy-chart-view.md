---
title: 분류 행렬 탭 (마이닝 정확도 차트 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
author: minewiskan
ms.author: owend
ms.openlocfilehash: d202d552b25095d0d0845ff64f9c0e289f7bba0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648070"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a><span data-ttu-id="f2d85-102">분류 행렬 탭(마이닝 정확도 차트 뷰)</span><span class="sxs-lookup"><span data-stu-id="f2d85-102">Classification Matrix Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="f2d85-103">**분류 행렬** 탭에서는 **열 매핑** 탭의 모델 표에서 선택한 각 모델에 대 한 분류 행렬을 표시 합니다. 분류 행렬은 **열 매핑** 탭에서 선택한 예측 가능한 열이 연속 되지 않은 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-103">The **Classification Matrix** tab displays a classification matrix for each model selected in the models grid on the **Column Mapping** tab. The classification matrix is only available if the predictable column that is selected in the **Column Mapping** tab is not continuous.</span></span> <span data-ttu-id="f2d85-104">**분류표** 탭에 대 한 자세한 설명은 [데이터 마이닝&#41;&#40;테스트 및 유효성 검사 ](data-mining/testing-and-validation-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2d85-104">For a more detailed description of the **Classification Matrix** tab, see [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f2d85-105">옵션</span><span class="sxs-lookup"><span data-stu-id="f2d85-105">Options</span></span>  
 <span data-ttu-id="f2d85-106">**복사**</span><span class="sxs-lookup"><span data-stu-id="f2d85-106">**Copy**</span></span>  
 <span data-ttu-id="f2d85-107">각 분류 행렬의 내용을 클립보드로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-107">Copies the content of each classification matrix to the clipboard.</span></span>  
  
 <span data-ttu-id="f2d85-108">**에 대 한 개수 \<model>\< predictable column>**</span><span class="sxs-lookup"><span data-stu-id="f2d85-108">**Counts for \<model> on \< predictable column>**</span></span>  
 <span data-ttu-id="f2d85-109">마이닝 구조의 각 마이닝 모델에 대한 분류 행렬을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-109">Displays a classification matrix for each mining model in the mining structure.</span></span> <span data-ttu-id="f2d85-110">행렬에는 다음 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-110">The matrix contains the following columns:</span></span>  
  
|<span data-ttu-id="f2d85-111">값</span><span class="sxs-lookup"><span data-stu-id="f2d85-111">Value</span></span>|<span data-ttu-id="f2d85-112">Description</span><span class="sxs-lookup"><span data-stu-id="f2d85-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2d85-113">**예측**</span><span class="sxs-lookup"><span data-stu-id="f2d85-113">**Predicted**</span></span>|<span data-ttu-id="f2d85-114">예측 가능한 열의 각 상태에 대한 행을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-114">Contains a row for each state of the predictable column.</span></span>|  
|<span data-ttu-id="f2d85-115">**\<states>실제**</span><span class="sxs-lookup"><span data-stu-id="f2d85-115">**\<states> (actual)**</span></span>|<span data-ttu-id="f2d85-116">예측 가능한 열의 각 상태에 대한 열입니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-116">A column for each state in the predictable column.</span></span> <span data-ttu-id="f2d85-117">행과 열의 상태가 일치하는 경우 셀은 해당 상태가 데이터베이스에 나타나는 실제 횟수를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-117">If the state of the row and the column correspond, the cell represents the actual number of times the state exists in the database.</span></span> <span data-ttu-id="f2d85-118">일치하지 않는 경우 셀은 예측의 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2d85-118">If they do not correspond, the cell represents the error of the prediction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2d85-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2d85-119">See Also</span></span>  
 <span data-ttu-id="f2d85-120">[마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;](mining-accuracy-chart-designer-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f2d85-120">[Mining Accuracy Chart Designer &#40;Data Mining&#41;](mining-accuracy-chart-designer-data-mining.md) </span></span>  
 <span data-ttu-id="f2d85-121">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f2d85-121">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="f2d85-122">테스트 및 유효성 검사&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="f2d85-122">Testing and Validation &#40;Data Mining&#41;</span></span>](data-mining/testing-and-validation-data-mining.md)  
  
  
