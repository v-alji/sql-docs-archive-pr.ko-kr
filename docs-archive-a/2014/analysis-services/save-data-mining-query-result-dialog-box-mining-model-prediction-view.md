---
title: 데이터 마이닝 쿼리 결과 저장 대화 상자 (마이닝 모델 예측 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0838c90f0797a0db9c8a66cd8c5f877aaecdad0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647920"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a><span data-ttu-id="547dd-102">데이터 마이닝 쿼리 결과 저장 대화 상자(마이닝 모델 예측 뷰)</span><span class="sxs-lookup"><span data-stu-id="547dd-102">Save Data Mining Query Result Dialog Box (Mining Model Prediction View)</span></span>
  <span data-ttu-id="547dd-103">**데이터 마이닝 쿼리 결과 저장** 대화 상자를 사용하여 데이터 마이닝 쿼리 결과를 새 테이블에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-103">Use the **Save Data Mining Query Result** dialog box to save the results of a data mining query to a new table.</span></span>  
  
 <span data-ttu-id="547dd-104">데이터 원본에서 정의한 데이터베이스에 새 테이블이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-104">The new table will be created in the database defined by the data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="547dd-105">옵션</span><span class="sxs-lookup"><span data-stu-id="547dd-105">Options</span></span>  
 <span data-ttu-id="547dd-106">**데이터 원본**</span><span class="sxs-lookup"><span data-stu-id="547dd-106">**Data Source**</span></span>  
 <span data-ttu-id="547dd-107">현재 프로젝트에서 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-107">Select a data source from the current project.</span></span> <span data-ttu-id="547dd-108">올바른 데이터 원본이 없는 경우 **새로 만들기** 를 클릭하여 새 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-108">If the correct data source does not exist, click **New** to create a new data source.</span></span>  
  
 <span data-ttu-id="547dd-109">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="547dd-109">**New**</span></span>  
 <span data-ttu-id="547dd-110">**데이터 원본 마법사**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-110">Opens the **Data Source Wizard**.</span></span>  
  
 <span data-ttu-id="547dd-111">**Table Name**</span><span class="sxs-lookup"><span data-stu-id="547dd-111">**Table Name**</span></span>  
 <span data-ttu-id="547dd-112">새 테이블의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-112">Type a name for the new table.</span></span>  
  
 <span data-ttu-id="547dd-113">**기존 항목 덮어쓰기**</span><span class="sxs-lookup"><span data-stu-id="547dd-113">**Overwrite if exists**</span></span>  
 <span data-ttu-id="547dd-114">기존 테이블을 같은 이름으로 덮어쓰려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-114">Select this option if you want to overwrite an existing table with the same name.</span></span>  
  
 <span data-ttu-id="547dd-115">다음 중 하나에 해당할 경우 기존 테이블을 덮어써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-115">Overwriting the existing table is required if any of the following is true:</span></span>  
  
-   <span data-ttu-id="547dd-116">예측 쿼리에 열을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-116">You added columns to the prediction query.</span></span>  
  
-   <span data-ttu-id="547dd-117">예측 쿼리의 열 이름이나 데이터 형식을 변경했습니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-117">You changed the names or data types of any columns in the prediction query.</span></span>  
  
-   <span data-ttu-id="547dd-118">대상 테이블에서 ALTER 문을 실행했습니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-118">You ran an ALTER statement on the destination table.</span></span>  
  
 <span data-ttu-id="547dd-119">여러 열의 이름이 동일한 경우(예: 파생된 여러 열에서 기본 열 이름인 **식**을 사용할 수 있음) 중복된 이름의 각 열에 대해 별칭을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-119">If multiple columns have the same name (for example, several derived columns might have the default column name **Expression**), you must create an alias for each column with a duplicate name.</span></span> <span data-ttu-id="547dd-120">테이블의 열 이름은 고유해야 하기 때문에 열 이름이 고유하지 않을 경우 디자이너가 SQL Server에 결과를 저장하려고 할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-120">If the columns do not have unique names, an error will be raised when the designer tries to save the results to SQL Server, because columns in a table must have unique names.</span></span>  
  
 <span data-ttu-id="547dd-121">**DSV에 추가**</span><span class="sxs-lookup"><span data-stu-id="547dd-121">**Add to DSV**</span></span>  
 <span data-ttu-id="547dd-122">테이블을 기존 데이터 원본에 추가하려면 프로젝트에 포함된 데이터 원본 뷰를 선택합니다(옵션).</span><span class="sxs-lookup"><span data-stu-id="547dd-122">(Optional) Select a data source view contained in the project if you want to add the table to an existing data source.</span></span>  
  
 <span data-ttu-id="547dd-123">이 옵션은 학습 데이터, 예측 원본 데이터 및 쿼리 결과와 같은 모델에 대 한 모든 관련 테이블을 동일한 데이터 원본에 유지 하려는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="547dd-123">This option is useful if you want to keep all related tables for a model-such as training data, prediction source data, and query results-in the same data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="547dd-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="547dd-124">See Also</span></span>  
 <span data-ttu-id="547dd-125">[예측 쿼리 작성기 &#40;데이터 마이닝&#41;](prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="547dd-125">[Prediction Query Builder &#40;Data Mining&#41;](prediction-query-builder-data-mining.md) </span></span>  
 <span data-ttu-id="547dd-126">[데이터 마이닝 쿼리 인터페이스](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="547dd-126">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 [<span data-ttu-id="547dd-127">DMX&#40;Data Mining Extensions&#41; 문 참조</span><span class="sxs-lookup"><span data-stu-id="547dd-127">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
