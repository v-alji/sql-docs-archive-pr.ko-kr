---
title: 예측 쿼리 수동 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e887e935dafcd2428859fd959cb7bc64650c660d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661420"
---
# <a name="manually-edit-a-prediction-query"></a><span data-ttu-id="2b3be-102">예측 쿼리 수동 편집</span><span class="sxs-lookup"><span data-stu-id="2b3be-102">Manually Edit a Prediction Query</span></span>
  <span data-ttu-id="2b3be-103">예측 쿼리 작성기를 사용하여 쿼리를 디자인한 후에는 데이터 마이닝 디자이너의 **마이닝 모델 예측** 의 탭에서 쿼리 텍스트 보기로 전환하여 해당 쿼리를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-103">After you have designed a query by using the Prediction Query Builder, you can modify the query by switching to Query Text view on the **Mining Model Prediction** tab of Data Mining Designer.</span></span> <span data-ttu-id="2b3be-104">쿼리 작성기가 만든 쿼리를 표시할 텍스트 편집기가 화면 맨 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-104">A text editor appears at the bottom of the screen to display the query that the query builder created.</span></span>  
  
 <span data-ttu-id="2b3be-105">쿼리 텍스트 보기로 전환은 쿼리에 항목을 추가하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-105">Switching to Query Text view is useful for making additions to the query.</span></span> <span data-ttu-id="2b3be-106">예를 들어 WHERE 절 또는 ORDER BY 절을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-106">For example, you can add a WHERE clause or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="2b3be-107">예측 쿼리 작성기의 표를 사용하여 개체 및 열 이름을 삽입하고 개별 예측 함수의 구문을 설정한 다음 수동 편집 모드로 전환하여 매개 변수 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-107">Use the grid in the Prediction Query Builder to insert the names of objects and columns and set up the syntax for individual prediction functions, and then switch to manual editing mode to change parameter values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2b3be-108">**쿼리 텍스트** 뷰에서 **디자인** 뷰로 다시 전환하면 **쿼리 텍스트** 뷰에서 변경한 내용이 모두 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-108">If you switch back to **Design** view from **Query Text** view, any changes that you made in **Query Text** view will be lost.</span></span>  
  
### <a name="modify-a-query"></a><span data-ttu-id="2b3be-109">쿼리 수정</span><span class="sxs-lookup"><span data-stu-id="2b3be-109">Modify a query</span></span>  
  
1.  <span data-ttu-id="2b3be-110">**의 데이터 마이닝 디자이너에 있는** 마이닝 모델 예측 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]탭에서 **SQL**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-110">On the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **SQL**.</span></span>  
  
     <span data-ttu-id="2b3be-111">화면 맨 아래의 표가 쿼리를 포함하는 텍스트 편집기로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-111">The grid at the bottom of the screen is replaced by a text editor that contains the query.</span></span> <span data-ttu-id="2b3be-112">이 편집기에서 쿼리 변경 내용을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-112">You can type changes to the query in this editor.</span></span>  
  
2.  <span data-ttu-id="2b3be-113">쿼리를 실행하려면 **마이닝 모델** 메뉴에서 **결과**를 선택하거나 단추를 클릭하여 쿼리 결과로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-113">To run the query, on the **Mining Model** menu, select **Result**, or click the button to switch to query results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b3be-114">만든 쿼리가 유효하지 않을 경우 결과 창에 오류도 표시되지 않고 결과도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b3be-114">If the query that you have created is invalid, the Results window does not display an error and does not display any results.</span></span> <span data-ttu-id="2b3be-115">**디자인** 단추를 클릭하거나 **마이닝 모델** 메뉴에서 **디자인** 또는 **쿼리** 를 선택하여 문제를 해결하고 쿼리를 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b3be-115">Click the **Design** button, or select **Design** or **Query** from the **Mining Model** menu to correct the problem and run the query again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b3be-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2b3be-116">See Also</span></span>  
 <span data-ttu-id="2b3be-117">[데이터 마이닝 쿼리](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="2b3be-117">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="2b3be-118">[예측 쿼리 작성기 &#40;데이터 마이닝&#41;](../prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2b3be-118">[Prediction Query Builder &#40;Data Mining&#41;](../prediction-query-builder-data-mining.md) </span></span>  
 [<span data-ttu-id="2b3be-119">6단원: 예측 만들기 및 작업&#40;기본 데이터 마이닝 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="2b3be-119">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
