---
title: 테스트 및 유효성 검사 태스크 및 방법 (데이터 마이닝) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- predictive modeling [Analysis Services]
- mining structures [Analysis Services], predictive modeling
- Mining Accuracy Chart [Analysis Services], how-to topics
- mining models [Analysis Services], predictive modeling
- predictive accuracy [data mining]
ms.assetid: 3a0b4dc9-5b64-4be1-aa5f-6ff26f43dbf8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 10844a7d39e49ab595eb25bb56ed3f4f5d415565
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660203"
---
# <a name="testing-and-validation-tasks-and-how-tos-data-mining"></a><span data-ttu-id="f3f35-102">테스트 및 유효성 검사 태스크 및 방법(데이터 마이닝)</span><span class="sxs-lookup"><span data-stu-id="f3f35-102">Testing and Validation Tasks and How-tos (Data Mining)</span></span>
  <span data-ttu-id="f3f35-103">**에서 데이터 마이닝 디자이너의** 마이닝 정확도 차트 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 탭을 사용하여 마이닝 구조에 있는 마이닝 모델의 예측 정확도를 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f35-103">You can use the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to compare the predictive accuracy of the mining models in your mining structure.</span></span>  
  
 <span data-ttu-id="f3f35-104">다음 4개의 차트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3f35-104">You can create four kinds of charts:</span></span>  
  
-   <span data-ttu-id="f3f35-105">리프트 차트</span><span class="sxs-lookup"><span data-stu-id="f3f35-105">Lift chart</span></span>  
  
-   <span data-ttu-id="f3f35-106">수익 차트</span><span class="sxs-lookup"><span data-stu-id="f3f35-106">Profit chart</span></span>  
  
-   <span data-ttu-id="f3f35-107">분류표</span><span class="sxs-lookup"><span data-stu-id="f3f35-107">Classification matrix</span></span>  
  
-   <span data-ttu-id="f3f35-108">교차 유효성 검사 보고서</span><span class="sxs-lookup"><span data-stu-id="f3f35-108">Cross-validation report</span></span>  
  
 <span data-ttu-id="f3f35-109">처음 세 차트는 **입력 선택** 탭을 사용하여 차트를 생성하는 데 사용되는 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f3f35-109">The first three charts use the **Input Selection** tab to define the data that is used for generating the chart.</span></span>  
  
 <span data-ttu-id="f3f35-110">교차 **유효성 검사 탭에서** 사용 가능한 추가 입력을 사용 하 여 교차 유효성 검사 차트를 만들 수 있습니다. 자세한 내용은 [교차 유효성 검사 &#40;Analysis Services-데이터 마이닝&#41;](cross-validation-analysis-services-data-mining.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3f35-110">The Cross-validation chart is created by using additional inputs, available on the **Cross-Validation** tab. For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](cross-validation-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="f3f35-111">마이닝 정확도 차트를 사용하는 방법에 대한 자세한 내용은 [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](testing-and-validation-data-mining.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3f35-111">For more information about how to use the mining accuracy chart, see [Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f3f35-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f3f35-112">In This Section</span></span>  
  
-   [<span data-ttu-id="f3f35-113">리프트 차트, 수익 차트 또는 분류표 만들기</span><span class="sxs-lookup"><span data-stu-id="f3f35-113">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>](create-a-lift-chart-profit-chart-or-classification-matrix.md)  
  
-   [<span data-ttu-id="f3f35-114">교차 유효성 검사 보고서 만들기</span><span class="sxs-lookup"><span data-stu-id="f3f35-114">Create a Cross-Validation Report</span></span>](create-a-cross-validation-report.md)  
  
-   [<span data-ttu-id="f3f35-115">모델 테스트 데이터 선택 및 매핑</span><span class="sxs-lookup"><span data-stu-id="f3f35-115">Choose and Map Model Testing Data</span></span>](choose-and-map-model-testing-data.md)  
  
-   [<span data-ttu-id="f3f35-116">모델 테스트 데이터에 필터 적용</span><span class="sxs-lookup"><span data-stu-id="f3f35-116">Apply Filters to Model Testing Data</span></span>](apply-filters-to-model-testing-data.md)  
  
-   [<span data-ttu-id="f3f35-117">마이닝 모델 테스트에 사용할 열 선택</span><span class="sxs-lookup"><span data-stu-id="f3f35-117">Choose the Column to Use for Testing a Mining Model</span></span>](choose-the-column-to-use-for-testing-a-mining-model.md)  
  
-   [<span data-ttu-id="f3f35-118">정확도 차트에 대한 입력으로 중첩 테이블 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="f3f35-118">Using Nested Table Data as an Input for an Accuracy Chart</span></span>](using-nested-table-data-as-an-input-for-an-accuracy-chart.md)  
  
  
