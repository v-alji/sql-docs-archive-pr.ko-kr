---
title: 조인 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.ppg.joinline
- vdtsql.chm:69638
ms.assetid: 0d9516bb-4ad3-4fcf-bb77-93474dea698f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7fbd2b61a080a681b5d15a4b69c466fae76e04e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727764"
---
# <a name="join-dialog-box-visual-database-tools"></a><span data-ttu-id="dcb34-102">조인 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="dcb34-102">Join Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="dcb34-103">이 대화 상자를 사용하면 테이블을 조인하기 위한 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-103">Use this dialog box to specify options for joining tables.</span></span> <span data-ttu-id="dcb34-104">이 대화 상자에 액세스하려면 **디자인** 창에서 조인 선을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-104">To access this dialog, in the **Design** pane select a join line.</span></span> <span data-ttu-id="dcb34-105">그런 다음, **속성** 창에서 **조인 조건 및 형식**을 클릭하고 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-105">Then in the **Properties** window click **Join Condition And Type**, and click the ellipses **(...)** that appear to the right of the property.</span></span>  
  
 <span data-ttu-id="dcb34-106">기본적으로 관련 테이블은 조인 열의 일치하는 정보를 포함하는 행에 기반하여 결과 집합을 만드는 내부 조인을 사용하여 조인됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-106">By default, related tables are joined using an inner join that creates a result set based on rows containing matching information in the join columns.</span></span> <span data-ttu-id="dcb34-107">**조인** 대화 상자에서 옵션을 설정하여 다른 연산자를 기반으로 하는 조인을 지정하거나 외부 조인을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-107">By setting options in the **Join** dialog box, you can specify a join based on a different operator, and you can specify an outer join.</span></span>  
  
 <span data-ttu-id="dcb34-108">테이블을 조인하는 방법에 대한 자세한 내용은 [조인을 사용한 쿼리&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dcb34-108">For more information about joining tables, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="dcb34-109">옵션</span><span class="sxs-lookup"><span data-stu-id="dcb34-109">Options</span></span>  
  
|<span data-ttu-id="dcb34-110">**용어**</span><span class="sxs-lookup"><span data-stu-id="dcb34-110">**Term**</span></span>|<span data-ttu-id="dcb34-111">**정의**</span><span class="sxs-lookup"><span data-stu-id="dcb34-111">**Definition**</span></span>|  
|--------------|--------------------|  
|<span data-ttu-id="dcb34-112">**테이블**</span><span class="sxs-lookup"><span data-stu-id="dcb34-112">**Table**</span></span>|<span data-ttu-id="dcb34-113">조인에 관련된 테이블 또는 테이블 반환 개체의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-113">The names of the tables or table-valued objects involved in the join.</span></span> <span data-ttu-id="dcb34-114">여기서는 테이블의 이름을 변경할 수 없으며 표시된 정보를 참조만 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-114">You cannot change the names of the tables here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="dcb34-115">**열**</span><span class="sxs-lookup"><span data-stu-id="dcb34-115">**Column**</span></span>|<span data-ttu-id="dcb34-116">테이블 조인에 사용된 열의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-116">The names of the columns used for joining the tables.</span></span> <span data-ttu-id="dcb34-117">연산자 목록의 연산자는 열에 있는 데이터 간의 관계를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-117">The operator in the operator list specifies the relationship between the data in the columns.</span></span> <span data-ttu-id="dcb34-118">여기서는 열의 이름을 변경할 수 없으며 표시된 정보를 참조만 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-118">You cannot change the names of the columns here - this information is displayed for information only.</span></span>|  
|<span data-ttu-id="dcb34-119">**연산자**</span><span class="sxs-lookup"><span data-stu-id="dcb34-119">**Operator**</span></span>|<span data-ttu-id="dcb34-120">조인 열과 관련시키는 데 사용되는 연산자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-120">Specify the operator used to relate the join columns.</span></span> <span data-ttu-id="dcb34-121">등호(=) 이외의 연산자를 지정하려면 목록에서 해당 연산자를 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="dcb34-121">To specify an operator other than equal (=), select it from the list.</span></span> <span data-ttu-id="dcb34-122">속성 페이지를 닫으면 선택한 연산자가 다음 그림과 같이 조인 선의 다이아몬드 모양 안에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-122">When you close the property page, the operator you selected will appear in the diamond graphic of the join line, as in the following:</span></span><br /><br /> <span data-ttu-id="dcb34-123">![Visual Database Tools 아이콘](../../database-engine/media//dv3wbii.gif "Visual Database Tools 아이콘")</span><span class="sxs-lookup"><span data-stu-id="dcb34-123">![Visual Database Tools icon](../../database-engine/media//dv3wbii.gif "Visual Database Tools icon")</span></span>|  
|<span data-ttu-id="dcb34-124">**모든 행 \<table1>**</span><span class="sxs-lookup"><span data-stu-id="dcb34-124">**All rows from \<table1>**</span></span>|<span data-ttu-id="dcb34-125">오른쪽 테이블에 일치하는 항목이 없는 경우에도 왼쪽 테이블의 모든 행이 출력되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-125">Specify that all the rows from the left table appear in the output, even if there are no corresponding matches in the right table.</span></span> <span data-ttu-id="dcb34-126">오른쪽 테이블에서 일치하는 데이터가 없는 열은 null로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-126">Columns with no matching data in the right table appear as null.</span></span> <span data-ttu-id="dcb34-127">이 옵션을 선택하면 SQL 문에 왼쪽 우선 외부 조인을 지정하는 것과 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-127">Choosing this option is equivalent to specifying LEFT OUTER JOIN in the SQL statement.</span></span>|  
|<span data-ttu-id="dcb34-128">**모든 행 \<table2>**</span><span class="sxs-lookup"><span data-stu-id="dcb34-128">**All rows from \<table2>**</span></span>|<span data-ttu-id="dcb34-129">왼쪽 테이블에 일치하는 항목이 없는 경우에도 오른쪽 테이블의 모든 행이 출력되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-129">Specify that all the rows from the right table appear in the output, even if there are no corresponding matches in the left table.</span></span> <span data-ttu-id="dcb34-130">왼쪽 테이블에서 일치하는 데이터가 없는 열은 null로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-130">Columns with no matching data in the left table appear as null.</span></span> <span data-ttu-id="dcb34-131">이 옵션을 선택하면 SQL 문에 RIGHT OUTER JOIN을 지정하는 것과 결과가 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-131">Choosing this option is equivalent to specifying RIGHT OUTER JOIN in the SQL statement.</span></span>|  
  
 <span data-ttu-id="dcb34-132">**\<table1>의 모든 행**과 **\<table2>의 모든 행**을 둘 다 선택하면 SQL 문에서 FULL OUTER JOIN을 지정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-132">Selecting both All **rows from \<table1>** and **All rows from \<table2>** is equivalent to specifying FULL OUTER JOIN in the SQL statement.</span></span>  
  
 <span data-ttu-id="dcb34-133">외부 조인을 만들기 위한 옵션을 선택하면 조인 선의 다이아몬드 모양이 변경되어 왼쪽 우선 외부 조인인지 오른쪽 우선 외부 조인인지 또는 완전 외부 조인인지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-133">When you select an option to create an outer join, the diamond graphic in the join line changes to indicate that the join is a left outer, right outer, or full outer join.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dcb34-134">"왼쪽"과 "오른쪽"이라는 말이 반드시 다이어그램 창의 테이블 위치를 의미하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-134">The words "left" and "right" do not necessarily correspond to the position of tables in the Diagram pane.</span></span> <span data-ttu-id="dcb34-135">"왼쪽"은 SQL 문에서 JOIN 키워드의 왼쪽에 이름이 나타나는 테이블을 말하고 "오른쪽"은 JOIN 키워드의 오른쪽에 이름이 나타나는 테이블을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-135">"Left" refers to the table whose name appears to the left of the keyword JOIN in the SQL statement, and "right" refers to the table whose name appears to the right of the JOIN keyword.</span></span> <span data-ttu-id="dcb34-136">**다이어그램** 창에서 테이블의 위치를 바꾸어도 여기에서 언급하는 왼쪽과 오른쪽이 바뀌는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="dcb34-136">If you move tables in the **Diagram** pane, you do not change which table is considered left or right.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb34-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dcb34-137">See Also</span></span>  
 <span data-ttu-id="dcb34-138">[Visual Database Tools를 &#40;조인을 사용 하 여 쿼리&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="dcb34-138">[Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="dcb34-139">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="dcb34-139">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
