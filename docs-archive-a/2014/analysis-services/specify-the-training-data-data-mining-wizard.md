---
title: 학습 데이터 지정 (데이터 마이닝 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87a802256d287a3e8e9e7fb65bbd91687cb71a4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653538"
---
# <a name="specify-the-training-data-data-mining-wizard"></a><span data-ttu-id="7a11a-102">학습 데이터 지정(데이터 마이닝 마법사)</span><span class="sxs-lookup"><span data-stu-id="7a11a-102">Specify the Training Data (Data Mining Wizard)</span></span>
  <span data-ttu-id="7a11a-103">**학습 데이터 지정** 페이지를 사용하여 마이닝 구조에 포함할 열을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-103">Use the **Specify the Training Data** page to identify which columns to include in the mining structure.</span></span> <span data-ttu-id="7a11a-104">모든 모델에서 열을 사용하지 않는 경우에도 열을 선택하여 구조에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-104">You can select columns to include in the structure even if you do not use them in all models.</span></span> <span data-ttu-id="7a11a-105">예를 들어 마이닝 모델에서 열로 드릴스루하려는 경우 모델이 아닌 구조에 열을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-105">For example, if you want to drill through to the columns from the mining model, you can include them in the structure but not in the model.</span></span>  
  
 <span data-ttu-id="7a11a-106">구조에 포함되는 각 테이블에 적어도 하나의 키 열이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-106">At least one key column is required for each table that is included in the structure.</span></span> <span data-ttu-id="7a11a-107">키로 선택하는 열은 테이블이 사례 테이블인지 중첩 테이블인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-107">The column that you pick as the key depends on whether the table is a case table or a nested table.</span></span> <span data-ttu-id="7a11a-108">중첩 테이블인 경우 키는 관계형 외래 키가 아니라 주로 예측 열이 되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-108">If the table is a nested table, the key is often also the predictable column, not the relational foreign key.</span></span> <span data-ttu-id="7a11a-109">중첩 키에 대한 자세한 내용은 [중첩 테이블&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/nested-tables-analysis-services-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a11a-109">To learn about nested keys, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a11a-110">다른 마이닝 알고리즘은 키를 다르게 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-110">Different mining algorithms use keys differently.</span></span> <span data-ttu-id="7a11a-111">다른 종류의 키에 대한 자세한 내용은 [콘텐츠 형식&#40;데이터 마이닝&#41;](data-mining/content-types-data-mining.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a11a-111">To learn about the different kinds of keys, see [Content Types &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).</span></span>  
  
 <span data-ttu-id="7a11a-112">**자세한 내용:** [마이닝 구조&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [마이닝 모델 열](data-mining/mining-model-columns.md), [데이터 마이닝 마법사&#40;Analysis Services - 데이터 마이닝&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [관계형 마이닝 구조 만들기](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="7a11a-112">**For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Mining Model Columns](data-mining/mining-model-columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="7a11a-113">옵션</span><span class="sxs-lookup"><span data-stu-id="7a11a-113">Options</span></span>  
 <span data-ttu-id="7a11a-114">**테이블/열**</span><span class="sxs-lookup"><span data-stu-id="7a11a-114">**Tables/Columns**</span></span>  
 <span data-ttu-id="7a11a-115">마법사의 이전 페이지에서 선택한 테이블 및 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-115">Displays the tables and columns that you selected on the previous page of the wizard.</span></span>  
  
 **\<check box>**  
 <span data-ttu-id="7a11a-116">마이닝 구조에 포함할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-116">Select the columns to include in the mining structure.</span></span>  
  
 <span data-ttu-id="7a11a-117">데이터 원본에 중첩 테이블 또는 여러 뷰가 포함된 경우 열 목록을 확장하여 중첩 테이블을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-117">If your data source includes nested tables or multiple views, expand the column list to view the nested tables.</span></span>  
  
 <span data-ttu-id="7a11a-118">**Key**</span><span class="sxs-lookup"><span data-stu-id="7a11a-118">**Key**</span></span>  
 <span data-ttu-id="7a11a-119">열을 데이터의 고유 식별자로 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-119">Select to use the column as a unique identifier for the data.</span></span>  
  
 <span data-ttu-id="7a11a-120">사례 테이블에서 키는 일반적으로 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-120">For a case table, the key is usually the unique identifier.</span></span>  
  
 <span data-ttu-id="7a11a-121">중첩 테이블에서 **키** 는 연결된 사례의 컨텍스트에 있는 행 식별자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-121">For nested table, the **Key** indicates the identifier of a row in the context of the associated case.</span></span>  
  
 <span data-ttu-id="7a11a-122">**입력**</span><span class="sxs-lookup"><span data-stu-id="7a11a-122">**Input**</span></span>  
 <span data-ttu-id="7a11a-123">열을 예측 생성 시 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-123">Select to use the column in creating predictions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7a11a-124">이 열은 마이닝 모델과 마이닝 구조를 함께 만드는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-124">This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="7a11a-125">**예측 가능**</span><span class="sxs-lookup"><span data-stu-id="7a11a-125">**Predictable**</span></span>  
 <span data-ttu-id="7a11a-126">추가 입력을 기반으로 테이블 또는 열을 예측하도록 하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-126">Select to enable the table or column to be predicted based on additional future input.</span></span>  
  
 <span data-ttu-id="7a11a-127">중첩 테이블을 예측 가능으로 표시하면 전체 중첩 테이블이 예측 가능하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-127">If you also mark a nested table as predictable, the whole nested table becomes predictable.</span></span> <span data-ttu-id="7a11a-128">중첩 테이블에 입력 또는 예측 가능으로 표시된 열이 없으면 중첩 테이블이 마이닝 구조에는 나타나지만 모델에서 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-128">If no columns in the nested table are marked as input or predictable, the nested table will appear in the mining structure, but will be ignored in the model.</span></span>  
  
 <span data-ttu-id="7a11a-129">**참고** 이 열은 마이닝 모델과 마이닝 구조를 함께 만드는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-129">**Note** This column is only available when you are creating a mining model together with the mining structure.</span></span>  
  
 <span data-ttu-id="7a11a-130">**제안**</span><span class="sxs-lookup"><span data-stu-id="7a11a-130">**Suggest**</span></span>  
 <span data-ttu-id="7a11a-131">Entropy를 기반으로 데이터 샘플을 분석하여 선택한 **예측 가능** 열에 가장 밀접히 관련되어 있는 입력 열을 식별하는 **관련 열 제안** 대화 상자를 열려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-131">Click to open the **Suggest Related Columns** dialog box, which performs an analysis on a sample of data to identify input columns that show the greatest relationship to the selected **Predictable** column based on entropy.</span></span> <span data-ttu-id="7a11a-132">이 분석은 OLAP 원본을 기반으로 하는 중첩 테이블 열 또는 마이닝 구조에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-132">This analysis also applies to nested table columns or mining structures that are based on OLAP sources.</span></span>  
  
 <span data-ttu-id="7a11a-133">**참고** 이 열은 마이닝 모델과 마이닝 구조를 함께 만드는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a11a-133">**Note** This column only available when you are creating a mining model together with the mining structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a11a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a11a-134">See Also</span></span>  
 <span data-ttu-id="7a11a-135">[데이터 마이닝 마법사 F1 도움말 &#40;Analysis Services 데이터 마이닝&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="7a11a-135">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="7a11a-136">[데이터 마이닝 마법사 &#40;관련 열 제안&#41;](suggest-related-columns-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7a11a-136">[Suggest Related Columns &#40;Data Mining Wizard&#41;](suggest-related-columns-data-mining-wizard.md) </span></span>  
 <span data-ttu-id="7a11a-137">[데이터 마이닝 마법사 &#40;테이블 형식을 지정&#41;](specify-table-types-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="7a11a-137">[Specify Table Types &#40;Data Mining Wizard&#41;](specify-table-types-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="7a11a-138">열 내용 및 데이터 형식 &#40;데이터 마이닝 마법사를 지정&#41;</span><span class="sxs-lookup"><span data-stu-id="7a11a-138">Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;</span></span>](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
