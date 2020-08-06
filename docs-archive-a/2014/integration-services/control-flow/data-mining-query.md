---
title: 데이터 마이닝 쿼리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquery.f1
ms.assetid: 948e358a-6245-429f-82c7-4cedc5e048fd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 657e4e173815fa25458e296f7eadb3d4d0696a02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651851"
---
# <a name="data-mining-query"></a><span data-ttu-id="7064f-102">데이터 마이닝 쿼리</span><span class="sxs-lookup"><span data-stu-id="7064f-102">Data Mining Query</span></span>
  <span data-ttu-id="7064f-103">디자인 창에는 데이터 마이닝 예측 쿼리를 작성할 때 사용할 수 있는 데이터 마이닝 예측 쿼리 작성기가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-103">The design pane contains the data mining prediction query builder, which you can use to build data mining prediction queries.</span></span> <span data-ttu-id="7064f-104">입력 테이블을 기반으로 하는 예측 쿼리를 디자인하거나 단일 예측 쿼리를 디자인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-104">You can design either prediction queries based on input tables, or singleton prediction queries.</span></span> <span data-ttu-id="7064f-105">쿼리를 실행하고 결과를 보려면 결과 뷰로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-105">Switch to the result view to run the query and view the results.</span></span> <span data-ttu-id="7064f-106">쿼리 뷰에서는 예측 쿼리 작성기로 만든 DMX(Data Mining Extensions) 쿼리를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-106">The query view displays the Data Mining Extensions (DMX) query created by the prediction query builder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7064f-107">옵션</span><span class="sxs-lookup"><span data-stu-id="7064f-107">Options</span></span>  
 <span data-ttu-id="7064f-108">뷰 전환 단추</span><span class="sxs-lookup"><span data-stu-id="7064f-108">Switch view button</span></span>  
 <span data-ttu-id="7064f-109">디자인 창과 쿼리 창 사이를 전환하려면 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-109">Click an icon to switch between the design and query pane.</span></span> <span data-ttu-id="7064f-110">기본적으로 디자인 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-110">By default, the design pane is open.</span></span>  
  
 <span data-ttu-id="7064f-111">디자인 창으로 전환하려면 ![디자인 아이콘](../media/ssis-designicon.gif "디자인 아이콘") 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-111">To switch to the design pane, click the ![Design icon](../media/ssis-designicon.gif "Design icon") icon.</span></span>  
  
 <span data-ttu-id="7064f-112">쿼리 창으로 전환하려면 ![SQL 아이콘](../media/ssis-queryicon.gif "SQL 아이콘") 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-112">To switch to the query pane, click the ![SQL icon](../media/ssis-queryicon.gif "SQL icon") icon.</span></span>  
  
 <span data-ttu-id="7064f-113">**마이닝 모델**</span><span class="sxs-lookup"><span data-stu-id="7064f-113">**Mining Model**</span></span>  
 <span data-ttu-id="7064f-114">예측의 기반으로 하려고 선택한 마이닝 모델을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-114">Displays the selected mining model on which you want to base predictions.</span></span>  
  
 <span data-ttu-id="7064f-115">**모델 선택**</span><span class="sxs-lookup"><span data-stu-id="7064f-115">**Select Model**</span></span>  
 <span data-ttu-id="7064f-116">**마이닝 모델 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-116">Opens the **Select Mining Model** dialog box.</span></span>  
  
 <span data-ttu-id="7064f-117">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="7064f-117">**Input Columns**</span></span>  
 <span data-ttu-id="7064f-118">예측 생성에 사용되는 선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-118">Displays the selected input columns used to generate the predictions.</span></span>  
  
 <span data-ttu-id="7064f-119">**원본**</span><span class="sxs-lookup"><span data-stu-id="7064f-119">**Source**</span></span>  
 <span data-ttu-id="7064f-120">열에 사용할 필드를 포함하는 원본을 드롭다운 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-120">Select the source containing the field that you will use for the column from the dropdown list.</span></span> <span data-ttu-id="7064f-121">**마이닝 모델** 테이블에서 선택한 마이닝 모델, **입력 테이블 선택** 테이블에서 선택한 입력 테이블, 예측 함수 또는 사용자 지정 식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-121">You can either use the mining model selected in the **Mining Model** table, the input table(s) selected in the **Select Input Table(s)** table, a prediction function, or a custom expression.</span></span>  
  
 <span data-ttu-id="7064f-122">마이닝 모델과 입력 열이 포함된 테이블에서 셀로 열을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-122">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
 <span data-ttu-id="7064f-123">**필드**</span><span class="sxs-lookup"><span data-stu-id="7064f-123">**Field**</span></span>  
 <span data-ttu-id="7064f-124">원본 테이블에서 파생된 열 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-124">Select a column from the list of columns derived from the source table.</span></span> <span data-ttu-id="7064f-125">**원본** 에서 **예측 함수**를 선택한 경우 이 셀에는 선택한 마이닝 모델에 대해 사용할 수 있는 예측 함수의 드롭다운 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-125">If you selected **Prediction Function** in **Source**, this cell contains a drop-down list of the prediction functions available for the selected mining model.</span></span>  
  
 <span data-ttu-id="7064f-126">**별칭**</span><span class="sxs-lookup"><span data-stu-id="7064f-126">**Alias**</span></span>  
 <span data-ttu-id="7064f-127">서버에서 반환한 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-127">The name of the column returned by the server.</span></span>  
  
 <span data-ttu-id="7064f-128">**표시**</span><span class="sxs-lookup"><span data-stu-id="7064f-128">**Show**</span></span>  
 <span data-ttu-id="7064f-129">열을 반환하거나 WHERE 절에서만 열을 사용하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-129">Select to return the column or to only use the column in the WHERE clause.</span></span>  
  
 <span data-ttu-id="7064f-130">**그룹**</span><span class="sxs-lookup"><span data-stu-id="7064f-130">**Group**</span></span>  
 <span data-ttu-id="7064f-131">**및/또는** 열과 함께 사용하여 식을 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-131">Use with the **And/Or** column to group expressions together.</span></span> <span data-ttu-id="7064f-132">예를 들어 (expr1 OR expr2) AND expr3과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-132">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="7064f-133">**및/또는**</span><span class="sxs-lookup"><span data-stu-id="7064f-133">**And/Or**</span></span>  
 <span data-ttu-id="7064f-134">논리적 쿼리를 만드는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-134">Use to create a logical query.</span></span> <span data-ttu-id="7064f-135">예를 들어 (expr1 OR expr2) AND expr3과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-135">For example, (expr1 OR expr2) AND expr3.</span></span>  
  
 <span data-ttu-id="7064f-136">**조건/인수**</span><span class="sxs-lookup"><span data-stu-id="7064f-136">**Criteria/Argument**</span></span>  
 <span data-ttu-id="7064f-137">열에 적용되는 조건 또는 사용자 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-137">Specify a condition or user expression that applies to the column.</span></span> <span data-ttu-id="7064f-138">마이닝 모델과 입력 열이 포함된 테이블에서 셀로 열을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7064f-138">Columns can be dragged from the tables containing the mining model and input columns to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7064f-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7064f-139">See Also</span></span>  
 <span data-ttu-id="7064f-140">[데이터 마이닝 쿼리 인터페이스](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span><span class="sxs-lookup"><span data-stu-id="7064f-140">[Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools) </span></span>  
 [<span data-ttu-id="7064f-141">DMX&#40;Data Mining Extensions&#41; 문 참조</span><span class="sxs-lookup"><span data-stu-id="7064f-141">Data Mining Extensions &#40;DMX&#41; Statement Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
