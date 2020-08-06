---
title: 열 매핑 지정 대화 상자 (마이닝 정확도 차트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8ede835567f678f4152b3d1944f3c2c7160c6837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653562"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a><span data-ttu-id="3ad80-102">열 매핑 지정 대화 상자(마이닝 정확도 차트)</span><span class="sxs-lookup"><span data-stu-id="3ad80-102">Specify Column Mapping Dialog Box (Mining Accuracy Chart)</span></span>
  <span data-ttu-id="3ad80-103">**열 매핑 지정** 탭을 사용하여 외부 데이터 원본에서 테이블을 선택하고 열을 데이터 마이닝 모델에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-103">Use the **Specify Column Mapping** tab to select tables from an external data source and map the columns to a data mining model.</span></span> <span data-ttu-id="3ad80-104">그런 다음 외부 데이터를 사용하여 마이닝 모델의 정확도를 테스트하고 결과를 정확도 차트에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-104">You can then use the external data to test the accuracy of a mining model and displays the results in the accuracy chart.</span></span>  
  
 <span data-ttu-id="3ad80-105">**자세한 내용:** [테스트 및 유효성 검사&#40;데이터 마이닝&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="3ad80-105">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="3ad80-106">옵션</span><span class="sxs-lookup"><span data-stu-id="3ad80-106">Options</span></span>  
 <span data-ttu-id="3ad80-107">**마이닝 구조**</span><span class="sxs-lookup"><span data-stu-id="3ad80-107">**Mining Structure**</span></span>  
 <span data-ttu-id="3ad80-108">테스트할 모델을 포함하는 선택한 마이닝 구조를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-108">Displays the selected mining structure that contains the model that you will test.</span></span>  
  
 <span data-ttu-id="3ad80-109">**구조 선택**</span><span class="sxs-lookup"><span data-stu-id="3ad80-109">**Select Structure**</span></span>  
 <span data-ttu-id="3ad80-110">**마이닝 구조 선택** 대화 상자를 열고 다른 마이닝 구조를 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-110">Click to open the **Select Mining Structure** dialog box and select a different mining structure.</span></span>  
  
 <span data-ttu-id="3ad80-111">**입력 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="3ad80-111">**Select Input Table(s)**</span></span>  
 <span data-ttu-id="3ad80-112">리프트 차트를 생성하는 데 사용하기 위해 선택한 입력 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-112">Displays the selected input tables that are used to generate the lift chart.</span></span> <span data-ttu-id="3ad80-113">모델의 정확도를 테스트하는 데 사용할 테스트 데이터를 포함하는 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-113">Select the table that contains the test data that you will use to test the accuracy of the models.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ad80-114"> 창에 테이블이 없으면 **사례 테이블 선택** 을 클릭하여 데이터 원본 뷰에서 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-114">If the pane does not contain any tables, click **Select Case Table** to add tables from a data source view.</span></span>  
  
 <span data-ttu-id="3ad80-115">**테이블 제거**</span><span class="sxs-lookup"><span data-stu-id="3ad80-115">**Remove Table**</span></span>  
 <span data-ttu-id="3ad80-116">선택한 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-116">Removes the selected table.</span></span> <span data-ttu-id="3ad80-117">테이블을 선택하지 않았거나 **입력 테이블 선택** 목록에 테이블이 표시되지 않은 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-117">This button is disabled if a table has not been selected or if no tables are displayed in the **Select Input Tables** list.</span></span>  
  
 <span data-ttu-id="3ad80-118">**사례 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="3ad80-118">**Select Case Table**</span></span>  
 <span data-ttu-id="3ad80-119">**테이블 선택** 대화 상자를 열고 데이터 원본 뷰를 선택하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-119">Click to open the **Select Table** dialog box and select a data source view.</span></span>  
  
 <span data-ttu-id="3ad80-120">**참고** 이 단추는 사례 테이블을 선택하지 않은 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-120">**Note** This button appears only if a case table has not been selected.</span></span> <span data-ttu-id="3ad80-121">다른 사례 테이블을 선택할 수 있도록 이 단추를 활성화하려면 기존 테이블을 모두 선택한 다음 **테이블 제거**를 클릭하여 목록을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-121">To enable the button so that you can select a different case table, clear the list by selecting all existing tables and then clicking **Remove Table**.</span></span>  
  
 <span data-ttu-id="3ad80-122">**중첩 테이블 선택**</span><span class="sxs-lookup"><span data-stu-id="3ad80-122">**Select Nested Table**</span></span>  
 <span data-ttu-id="3ad80-123">**테이블 선택** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-123">Opens the **Select Table** dialog box.</span></span> <span data-ttu-id="3ad80-124">이 단추는 사례 테이블을 선택한 경우에만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-124">This button appears only if a case table has been selected.</span></span> <span data-ttu-id="3ad80-125">관련 마이닝 구조에 중첩 테이블이 없는 경우에는 이 단추를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-125">If the associated mining structure does not contain a nested table, this button is disabled.</span></span>  
  
 <span data-ttu-id="3ad80-126">**조인 수정**</span><span class="sxs-lookup"><span data-stu-id="3ad80-126">**Modify Join**</span></span>  
 <span data-ttu-id="3ad80-127">**중첩 조인 지정** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-127">Opens the **Specify Nested Join** dialog box.</span></span> <span data-ttu-id="3ad80-128">이 단추는 중첩 테이블을 선택한 경우에만 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="3ad80-128">This button is active only if the nested table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad80-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3ad80-129">See Also</span></span>  
 <span data-ttu-id="3ad80-130">[테스트 및 유효성 검사 태스크 및 방법 &#40;데이터 마이닝&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3ad80-130">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="3ad80-131">마이닝 정확도 차트 디자이너 &#40;데이터 마이닝&#41;</span><span class="sxs-lookup"><span data-stu-id="3ad80-131">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
