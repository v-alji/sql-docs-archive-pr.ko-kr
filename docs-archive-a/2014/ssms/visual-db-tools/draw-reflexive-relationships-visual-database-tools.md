---
title: 반사 관계 그리기(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- drawing reflexive relationships
- reflexive relationships
- database diagrams [SQL Server], relationships
ms.assetid: e218363f-faec-46d5-9904-a537fbcc994d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e5056b1a5d0d884edbc4fc818fe8c7ef5cc8ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652492"
---
# <a name="draw-reflexive-relationships-visual-database-tools"></a><span data-ttu-id="d84eb-102">반사 관계 그리기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="d84eb-102">Draw Reflexive Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="d84eb-103">반사 관계를 만들면 테이블에 있는 하나 이상의 열을 동일한 테이블에 있는 하나 이상의 다른 열에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-103">You create a reflexive relationship to link a column or columns in a table with another column or columns in the same table.</span></span> <span data-ttu-id="d84eb-104">예를 들어, `employee` 테이블에 `emp_id` 열과 `mgr_id` 열이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-104">For example, suppose the `employee` table has an `emp_id` column and a `mgr_id` column.</span></span> <span data-ttu-id="d84eb-105">각 관리자는 회사의 직원이기도 하므로 테이블 내에서 관계 선을 그려 이러한 두 열을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-105">Because each manager is also an employee, you relate these two columns by drawing a relationship line from the table to itself.</span></span> <span data-ttu-id="d84eb-106">이와 같이 관계를 설정하면 테이블에 추가되는 각 관리자 ID가 기존의 직원 ID와 일치하도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-106">This relationship ensures each manager ID that is added to the table matches an existing employee ID.</span></span>  
  
 <span data-ttu-id="d84eb-107">관계를 만들려면 먼저 테이블에 대한 기본 키나 UNIQUE 제약 조건을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-107">Before you create a relationship, you must first define a primary key or unique constraint for your table.</span></span> <span data-ttu-id="d84eb-108">그런 다음 기본 키 열을 일치하는 열에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-108">You then relate the primary key column to a matching column.</span></span> <span data-ttu-id="d84eb-109">관계를 만들면 일치하는 열이 테이블의 외래 키가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-109">Once you create the relationship, the matching column becomes a foreign key of the table.</span></span>  
  
### <a name="to-draw-a-reflexive-relationship"></a><span data-ttu-id="d84eb-110">반사 관계를 그리려면</span><span class="sxs-lookup"><span data-stu-id="d84eb-110">To draw a reflexive relationship</span></span>  
  
1.  <span data-ttu-id="d84eb-111">데이터베이스 다이어그램에서 다른 열에 연결하려는 데이터베이스 열에 대한 행 선택기를 클릭하고 포인터를 테이블 바깥으로 끌어 선을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-111">In your database diagram, click the row selector for the database column that you want to relate to another column and drag the pointer outside the table until a line appears.</span></span>  
  
2.  <span data-ttu-id="d84eb-112">선을 다시 선택된 테이블로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-112">Drag the line back to the selected table.</span></span>  
  
3.  <span data-ttu-id="d84eb-113">마우스 단추를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-113">Release the mouse button.</span></span> <span data-ttu-id="d84eb-114">**테이블 및 열** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-114">The **Tables and Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="d84eb-115">관계를 형성하려는 외래 키 열과 기본 키 테이블 및 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-115">Select the foreign key column and the primary key table and column with which you want form a relationship.</span></span>  
  
5.  <span data-ttu-id="d84eb-116">**확인** 을 두 번 선택하여 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-116">Choose **OK** twice to create the relationship.</span></span>  
  
 <span data-ttu-id="d84eb-117">테이블에 대해 쿼리를 실행할 때 반사 관계를 사용하여 자체 조인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d84eb-117">When you run queries against a table, you can use a reflexive relationship to create a self-join.</span></span> <span data-ttu-id="d84eb-118">조인을 사용하여 테이블을 쿼리하는 방법에 대한 자세한 내용은 [조인을 사용한 쿼리&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d84eb-118">For information about querying tables with joins, see [Query with Joins &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84eb-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d84eb-119">See Also</span></span>  
 [<span data-ttu-id="d84eb-120">조인을 사용한 쿼리&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="d84eb-120">Query with Joins &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
