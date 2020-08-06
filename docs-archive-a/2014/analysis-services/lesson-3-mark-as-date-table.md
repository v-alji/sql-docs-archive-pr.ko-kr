---
title: '4 단원: 날짜 테이블로 표시 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c32cc336-b7d8-4122-9d62-4936344d2315
author: minewiskan
ms.author: owend
ms.openlocfilehash: c3ccc57d770d954e9523196d2393fa9dc2ada5b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652426"
---
# <a name="lesson-4-mark-as-date-table"></a><span data-ttu-id="8fe99-102">4단원: 날짜 테이블로 표시</span><span class="sxs-lookup"><span data-stu-id="8fe99-102">Lesson 4: Mark as Date Table</span></span>
  <span data-ttu-id="8fe99-103">2 단원: 데이터 추가에서는 범위 이름이 지정 된 차원 테이블을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-103">In Lesson 2: Add Data, you imported a dimension table named DimDate.</span></span> <span data-ttu-id="8fe99-104">그런 다음 3 단원: 열 이름 바꾸기에서 날짜로 열 이름 바꾸기에서 나의 날짜 테이블 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-104">You then renamed the DimDate table, in Lesson 3: Rename Columns, to simply, Date.</span></span> <span data-ttu-id="8fe99-105">해당 모델에서 이제 이 테이블의 이름은 Date이며 날짜 및 시간 데이터를 포함한다는 점에서 *날짜 테이블*이라고 부를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-105">While in your model this table is now named Date, it can also be known as a *Date table*, in that it contains date and time data.</span></span>  
  
 <span data-ttu-id="8fe99-106">잠시 후 측정값을 만들면서 해보겠지만, 계산에 시간 인텔리전스 함수를 사용할 때는 항상 *날짜 테이블* 및 이 테이블의 고유 식별자인 *날짜 열* 이 포함되는 날짜 테이블 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-106">Whenever you use Time Intelligence functions in calculations, as you will do when you create measures a little later, you must specify date table properties, which include a *Date table* and a unique identifier *Date column* in that table.</span></span> <span data-ttu-id="8fe99-107">그런 다음 다른 테이블과 Date 테이블 사이에 유효한 관계를 만들 수 있습니다. 이것은 DAX 시간 인텔리전스 함수를 사용하는 계산에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-107">You can then create valid relationships between other tables and the Date table; necessary for calculations using DAX time intelligence functions.</span></span>  
  
 <span data-ttu-id="8fe99-108">이 단원에서는 가져와 이름을 바꾼 Date 테이블을 *날짜 테이블* 로 표시하고 Date 테이블의 Date 열을 *날짜 열* (고유 식별자)로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-108">In this lesson, you will mark the imported and renamed Date table as the *Date table* and the Date column (in the Date table) as the *Date column* (unique identifier).</span></span> <span data-ttu-id="8fe99-109">모든 이름 날짜를 사용 하면 혼란 스 러 울 수 있지만 곧 아이디어를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-109">All the use of the name Date can get kind of confusing, but you'll soon get the idea.</span></span>  
  
 <span data-ttu-id="8fe99-110">이 단원에 소요되는 예상 시간: **3분**</span><span class="sxs-lookup"><span data-stu-id="8fe99-110">Estimated time to complete this lesson: **3 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8fe99-111">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8fe99-111">Prerequisites</span></span>  
 <span data-ttu-id="8fe99-112">이 항목은 테이블 형식 모델링 자습서에 포함되며 순서대로 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-112">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="8fe99-113">이 단원의 태스크를 수행하려면 이전 단원인 [3단원: 열 이름 바꾸기](rename-columns.md)를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-113">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 3: Rename Columns](rename-columns.md).</span></span>  
  
### <a name="to-set-mark-as-date-table"></a><span data-ttu-id="8fe99-114">날짜 테이블로 표시를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="8fe99-114">To set Mark as Date Table</span></span>  
  
1.  <span data-ttu-id="8fe99-115">모델 디자이너에서 **Date** 테이블(탭)을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-115">In the model designer, click the **Date** table (tab).</span></span>  
  
2.  <span data-ttu-id="8fe99-116">**테이블** 메뉴를 클릭 하 고 **날짜**를 클릭 한 다음 **날짜 테이블로 표시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-116">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**.</span></span>  
  
3.  <span data-ttu-id="8fe99-117">**날짜 테이블로 표시** 대화 상자의 **날짜** 목록 상자에서 **Date** 열을 고유 식별자로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8fe99-117">In the **Mark as Date Table** dialog box, in the **Date** listbox, select the **Date** column as the unique identifier.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8fe99-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="8fe99-118">Next Steps</span></span>  
 <span data-ttu-id="8fe99-119">이 자습서를 계속하려면 다음 단원인 [5단원: 관계 만들기](lesson-4-create-relationships.md)로 이동하세요.</span><span class="sxs-lookup"><span data-stu-id="8fe99-119">To continue this tutorial, go to the next lesson: [Lesson 5: Create Relationships](lesson-4-create-relationships.md).</span></span>  
  
  
