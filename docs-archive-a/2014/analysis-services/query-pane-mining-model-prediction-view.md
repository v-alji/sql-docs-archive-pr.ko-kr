---
title: 쿼리 창 (마이닝 모델 예측 뷰) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
author: minewiskan
ms.author: owend
ms.openlocfilehash: e17a27190891ea9e00be21d5013d0767d61ac148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649243"
---
# <a name="query-pane-mining-model-prediction-view"></a><span data-ttu-id="b6bd5-102">쿼리 창(마이닝 모델 예측 뷰)</span><span class="sxs-lookup"><span data-stu-id="b6bd5-102">Query Pane (Mining Model Prediction View)</span></span>
  <span data-ttu-id="b6bd5-103">**쿼리** 창에서는 예측 쿼리 작성기로 만든 DMX(Data Mining Extensions) 문을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-103">The **Query** pane displays the Data Mining Expressions (DMX) statements created by Prediction Query Builder.</span></span> <span data-ttu-id="b6bd5-104">문을 수정한 다음 **쿼리 결과 뷰로 전환** 단추를 클릭하여 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-104">You can modify the statements and then click the **Switch to query result view** button to return the results.</span></span> <span data-ttu-id="b6bd5-105">다시 **디자인** 뷰로 전환하면 문에 적용한 변경 내용이 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-105">If you switch back to the **Design** view, any changes you made to the statement will be lost.</span></span>  
  
 <span data-ttu-id="b6bd5-106">**자세한 내용:** [DMX&#40;Data Mining Extensions&#41; 데이터 조작 문](/sql/dmx/dmx-statements-data-manipulation), [SQL Server Management Studio에서 DMX 쿼리 만들기](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b6bd5-106">**For More Information:** [Data Mining Extensions &#40;DMX&#41; Data Manipulation Statements](/sql/dmx/dmx-statements-data-manipulation), [Create a DMX Query in SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="b6bd5-107">옵션</span><span class="sxs-lookup"><span data-stu-id="b6bd5-107">Options</span></span>  
 <span data-ttu-id="b6bd5-108">**쿼리 결과 뷰로 전환**</span><span class="sxs-lookup"><span data-stu-id="b6bd5-108">**Switch to query result view**</span></span>  
 <span data-ttu-id="b6bd5-109">**디자인**, **쿼리**및 **결과** 창 사이를 전환하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-109">Click to switch between the **Design**, **Query**, and **Result** panes.</span></span> <span data-ttu-id="b6bd5-110">**결과** 창으로 전환하면 쿼리가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-110">Switching to the **Result** pane runs the query.</span></span>  
  
 <span data-ttu-id="b6bd5-111">**쿼리 결과 저장**</span><span class="sxs-lookup"><span data-stu-id="b6bd5-111">**Save the query result**</span></span>  
 <span data-ttu-id="b6bd5-112">**데이터 마이닝 쿼리 결과 저장** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-112">Opens the **Save Data Mining Query Result** dialog box.</span></span>  
  
 <span data-ttu-id="b6bd5-113">**단일 쿼리**</span><span class="sxs-lookup"><span data-stu-id="b6bd5-113">**Singleton query**</span></span>  
 <span data-ttu-id="b6bd5-114">입력 값의 테이블에 대한 참조를 제공하는 대신 쿼리에 직접 입력 데이터를 제공하는 단일 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-114">Lets you create a singleton query, in which you provide the input data directly in your query instead of providing a reference to a table of input values.</span></span> <span data-ttu-id="b6bd5-115">**입력 테이블 선택** 테이블이 **단일 쿼리 입력** 테이블로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-115">The **Select Input Table(s)** table is replaced by a **Singleton Query Input** table.</span></span> <span data-ttu-id="b6bd5-116">단일 쿼리로 전환하면 현재 예측 쿼리가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-116">The current prediction query will be lost if you switch to a singleton query.</span></span>  
  
 <span data-ttu-id="b6bd5-117">**쿼리 결과 새로 고침**</span><span class="sxs-lookup"><span data-stu-id="b6bd5-117">**Refresh query results**</span></span>  
 <span data-ttu-id="b6bd5-118">예측 쿼리를 다시 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-118">Reprocesses the prediction query.</span></span> <span data-ttu-id="b6bd5-119">이 옵션은 **결과** 창에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6bd5-119">This is enabled only in the **Result** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bd5-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6bd5-120">See Also</span></span>  
 <span data-ttu-id="b6bd5-121">[데이터 마이닝 쿼리 인터페이스](data-mining/data-mining-query-tools.md) </span><span class="sxs-lookup"><span data-stu-id="b6bd5-121">[Data Mining Query Interfaces](data-mining/data-mining-query-tools.md) </span></span>  
 <span data-ttu-id="b6bd5-122">[데이터 마이닝 확장 &#40;DMX&#41; 문 참조](/sql/dmx/data-mining-extensions-dmx-statements) </span><span class="sxs-lookup"><span data-stu-id="b6bd5-122">[Data Mining Extensions &#40;DMX&#41; Statement Reference](/sql/dmx/data-mining-extensions-dmx-statements) </span></span>  
 [<span data-ttu-id="b6bd5-123">예측 쿼리 작성기&#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="b6bd5-123">Prediction Query Builder &#40;Data Mining&#41;</span></span>](prediction-query-builder-data-mining.md)  
  
  
