---
title: 테스트 집합 만들기 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: ab22597224f5c6c6006a02af81fa6583886d93b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651404"
---
# <a name="create-testing-set-data-mining-wizard"></a><span data-ttu-id="89711-102">테스트 집합 만들기(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="89711-102">Create Testing Set (Data Mining Wizard)</span></span>
  <span data-ttu-id="89711-103">**테스트 집합 만들기** 페이지를 사용하여 학습에 사용할 데이터 양과 테스트 집합으로 사용하기 위해 예약할 양을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-103">Use the **Create Testing Set** page to specify how much of the data is to be used for training, and how much is to be reserved for use as a test set.</span></span> <span data-ttu-id="89711-104">마이닝 구조를 만들 때 학습 집합과 테스트 집합으로 데이터를 분리하면 나중에 만드는 마이닝 모델의 정확도를 보다 편리하게 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-104">Separating data into a training and testing set when you create a mining structure makes it much easier to assess the accuracy of mining models that you create later.</span></span>  
  
 <span data-ttu-id="89711-105">테스트 데이터 양을 비율로 지정하거나 테스트에 사용되는 사례 수를 제한하는 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-105">You can specify the amount of testing data as a percentage, or you can specify a number to limit the number of cases used for testing.</span></span> <span data-ttu-id="89711-106">테스트에 사용할 사례의 최대 수와 비율을 모두 지정하면 두 설정이 모두 사용되어 테스트 데이터 집합에 적은 수의 사례가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="89711-106">If you specify both a percentage and a maximum number of cases to use for testing, both settings are used, and the testing data set contains the smaller number of cases.</span></span> <span data-ttu-id="89711-107">기본적으로 데이터의 30%는 테스트에 사용되고 70%는 학습에 사용되며 테스트 사례의 최대 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-107">By default, 30 percent of data is used for testing, 70 percent for training, and there is no maximum number of test cases.</span></span>  
  
 <span data-ttu-id="89711-108">기본적으로 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 는 분할을 시작할 때 사용되는 숫자 시드를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-108">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generates a numeric seed that is used to start partitioning.</span></span> <span data-ttu-id="89711-109">이 시드는 마이닝 구조의 이름을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-109">This seed is based on the name of the mining structure.</span></span> <span data-ttu-id="89711-110">마이닝 구조의 이름이 변경된 후에도 파티션을 동일하게 유지하려면 마이닝 구조의 HoldoutSeed 속성을 설정하여 시드의 값을 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89711-110">If you want to ensure that the partition stays the same even if the name of the mining structure is changed, you can specify a value for the seed, by setting the HoldoutSeed property of the mining structure.</span></span> <span data-ttu-id="89711-111">홀드아웃 시드를 변경하면 구조를 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-111">If you change the holdout seed, you must reprocess the structure.</span></span>  
  
 <span data-ttu-id="89711-112">나중에 테스트 또는 학습 데이터의 양을 변경 하려면 `HoldoutMaxCases` `HoldoutMaxPercent` **속성** 창을 사용 하 여 데이터 마이닝 구조에서 및 속성을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-112">If you later want to change the amount of testing or training data, you can modify the `HoldoutMaxCases` and `HoldoutMaxPercent` properties on the data mining structure by using the **Properties** window.</span></span> <span data-ttu-id="89711-113">그러나 변경 후에는 마이닝 구조 및 연결된 모든 마이닝 모델을 다시 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-113">However, after you make the change you must reprocess the mining structure and all associated mining models.</span></span> <span data-ttu-id="89711-114">또한 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="89711-114">The following limitations also apply:</span></span>  
  
-   <span data-ttu-id="89711-115">데이터 마이닝 구조의 분할은 데이터 마이닝 구조가 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]에 저장된 경우에만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="89711-115">Partitioning of a data mining structure is supported only when the data mining structure is stored in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="89711-116">이전 버전의에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 마이닝 구조에 대 한 파티션 정보의 캐싱을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-116">Earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] do not support caching of partition information for mining structures.</span></span>  
  
-   <span data-ttu-id="89711-117">마이닝 구조에 시계열 마이닝 모델에 필요한 Key Time 열이 포함된 경우 마이닝 구조를 분할할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-117">You cannot partition a mining structure if the mining structure contains a Key Time column, which is required for time series mining models.</span></span>  
  
-   <span data-ttu-id="89711-118">중첩 테이블에 저장되는 값을 예측하려는 경우 데이터를 분할할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="89711-118">You cannot partition data if you are trying to predict a value that is stored in a nested table.</span></span>  
  
 <span data-ttu-id="89711-119">**자세한 내용:** [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](data-mining/testing-and-validation-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md), [기본 데이터 마이닝 자습서](../../2014/tutorials/basic-data-mining-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="89711-119">**For More Information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md), [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="89711-120">옵션</span><span class="sxs-lookup"><span data-stu-id="89711-120">Options</span></span>  
 <span data-ttu-id="89711-121">**테스트용 데이터 비율**</span><span class="sxs-lookup"><span data-stu-id="89711-121">**Percentage of data for testing**</span></span>  
 <span data-ttu-id="89711-122">위쪽/아래쪽 화살표를 클릭하여 학습 집합으로 사용할 데이터 비율을 늘이거나 줄입니다. 또는 입력란에 0에서 100 사이의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-122">Click the up and down arrows to increase or decrease the percentage of data to use as a training set, or type a value between 0 and 100 in the text box.</span></span>  
  
 <span data-ttu-id="89711-123">**테스트 데이터 집합의 최대 사례 수**</span><span class="sxs-lookup"><span data-stu-id="89711-123">**Maximum number of cases in testing data set**</span></span>  
 <span data-ttu-id="89711-124">테스트에 사용할 수 있는 사례 수를 제한하려면 원하는 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-124">Type a number to limit the number of cases that can be used for testing.</span></span>  
  
 <span data-ttu-id="89711-125">데이터의 실제 사례 수보다 더 큰 수를 지정하면 모든 사례가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="89711-125">If you specify a number that is larger than the number of actual cases in the data, all the cases will be used.</span></span>  
  
 <span data-ttu-id="89711-126">기본값은 NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="89711-126">The default is NULL.</span></span> <span data-ttu-id="89711-127">이 값은 제한이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="89711-127">This means there is no limit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89711-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89711-128">See Also</span></span>  
 <span data-ttu-id="89711-129">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="89711-129">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="89711-130">[데이터 마이닝 마법사 &#40;관련 열 제안&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="89711-130">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="89711-131">[데이터 마이닝 마법사 &#40;테이블 형식을 지정&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="89711-131">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="89711-132">열 내용 및 데이터 형식 &#40;데이터 마이닝 마법사를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="89711-132">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
