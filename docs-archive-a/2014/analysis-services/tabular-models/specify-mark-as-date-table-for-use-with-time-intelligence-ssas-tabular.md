---
title: 시간 인텔리전스에 사용할 날짜 테이블로 표시 지정 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 81038369b8cb8636a2aa216f1c26783a96d5f7ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727360"
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular"></a><span data-ttu-id="2450a-102">시간 인텔리전스에 사용할 날짜 테이블로 표시 지정(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="2450a-102">Specify Mark as Date Table for use with Time Intelligence (SSAS Tabular)</span></span>
  <span data-ttu-id="2450a-103">DAX 수식에 시간 인텔리전스 함수를 사용하려면 날짜 테이블 및 날짜 데이터 형식의 고유 식별자(datetime) 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-103">In order to use time intelligence functions in DAX formulas, you must specify a date table and a unique identifier (datetime) column of the Date data type.</span></span> <span data-ttu-id="2450a-104">날짜 테이블의 열을 고유 식별자로 지정한 후에는 날짜 테이블과 임의의 팩트 테이블에 있는 열 간에 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-104">Once a column in the date table is specified as a unique identifier, you can create relationships between columns in the date table and any fact tables.</span></span>  
  
 <span data-ttu-id="2450a-105">시간 인텔리전스 함수를 사용할 때는 다음 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-105">When using time intelligence functions, the following rules apply:</span></span>  
  
-   <span data-ttu-id="2450a-106">DAX 시간 인텔리전스 함수를 사용할 때는 팩트 테이블에서 datetime 열을 지정하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-106">When using DAX time intelligence functions, never specify a datetime column from a fact table.</span></span> <span data-ttu-id="2450a-107">항상 날짜 데이터 형식의 datetime 열 하나 이상과 고유 값이 포함된 별도의 날짜 테이블을 모델에 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="2450a-107">Always create a separate date table in your model with at least one datetime column of Date data type and with unique values.</span></span>  
  
-   <span data-ttu-id="2450a-108">날짜 테이블에 연속 날짜 범위가 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="2450a-108">Make sure your date table has a continuous date range.</span></span>  
  
-   <span data-ttu-id="2450a-109">날짜 테이블의 datetime 열은 세분성이 하루여야 하며 더 세부적으로 나뉘지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-109">The datetime column in the date table should be at day granularity (without fractions of a day).</span></span>  
  
-   <span data-ttu-id="2450a-110">**날짜 테이블로 표시** 대화 상자를 사용하여 날짜 테이블 및 고유 식별자 열을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-110">You must specify a date table and a unique identifier column by using the **Mark the Date Table** dialog box.</span></span>  
  
-   <span data-ttu-id="2450a-111">팩트 테이블 및 날짜 테이블에 있는 날짜 데이터 형식의 열 간에 관계를 만드십시오.</span><span class="sxs-lookup"><span data-stu-id="2450a-111">Create relationships between fact tables and columns of Date data type in the date table.</span></span>  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a><span data-ttu-id="2450a-112">날짜 테이블 및 고유 식별자를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="2450a-112">To specify a date table and unique identifier</span></span>  
  
1.  <span data-ttu-id="2450a-113">모델 디자이너에서 날짜 테이블을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-113">In the model designer, click the date table.</span></span>  
  
2.  <span data-ttu-id="2450a-114">**테이블** 메뉴를 클릭한 다음 **날짜**, **Mark as 날짜 테이블**를 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-114">Click the **Table** menu, then click **Date**, and then click **Mark as Date Table**</span></span>  
  
3.  <span data-ttu-id="2450a-115">**날짜 테이블로 표시** 대화 상자의 **날짜** 목록 상자에서 고유 식별자로 사용할 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-115">In the **Mark as Date Table** dialog box, in the **Date** listbox, select a column to be used as a unique identifier.</span></span> <span data-ttu-id="2450a-116">이 열은 고유 값을 포함해야 하며 날짜 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-116">This column must contain unique values and should be of Date data type.</span></span> <span data-ttu-id="2450a-117">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-117">For example:</span></span>  
  
    |<span data-ttu-id="2450a-118">Date</span><span class="sxs-lookup"><span data-stu-id="2450a-118">Date</span></span>|  
    |----------|  
    |<span data-ttu-id="2450a-119">2010/7/1 오전 12:00:00</span><span class="sxs-lookup"><span data-stu-id="2450a-119">7/1/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="2450a-120">2010/7/2 오전 12:00:00</span><span class="sxs-lookup"><span data-stu-id="2450a-120">7/2/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="2450a-121">2010/7/3 오전 12:00:00</span><span class="sxs-lookup"><span data-stu-id="2450a-121">7/3/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="2450a-122">2010/7/4 오전 12:00:00</span><span class="sxs-lookup"><span data-stu-id="2450a-122">7/4/2010 12:00:00 AM</span></span>|  
    |<span data-ttu-id="2450a-123">2010/7/5 오전 12:00:00</span><span class="sxs-lookup"><span data-stu-id="2450a-123">7/5/2010 12:00:00 AM</span></span>|  
  
4.  <span data-ttu-id="2450a-124">필요한 경우 팩트 테이블과 날짜 테이블 간에 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2450a-124">If necessary, create any relationships between fact tables and the date table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2450a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2450a-125">See Also</span></span>  
 <span data-ttu-id="2450a-126">[SSAS 테이블 형식&#41;계산 &#40;](calculations-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="2450a-126">[Calculations &#40;SSAS Tabular&#41;](calculations-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="2450a-127">시간 인텔리전스 함수 &#40;DAX&#41;</span><span class="sxs-lookup"><span data-stu-id="2450a-127">Time Intelligence Functions &#40;DAX&#41;</span></span>](/dax/time-intelligence-functions-dax)  
  
  
