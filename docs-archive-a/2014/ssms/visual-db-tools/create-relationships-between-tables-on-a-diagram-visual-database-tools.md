---
title: 다이어그램에서 테이블 간의 관계 만들기 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- diagrams [SQL Server], designing
ms.assetid: 28e9630c-dff4-46cc-bb0e-fe77998b6ac2
author: stevestein
ms.author: sstein
ms.openlocfilehash: d7d627a37f84dcb66b2129bb9c7dbc5890ccd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740679"
---
# <a name="create-relationships-between-tables-on-a-diagram-visual-database-tools"></a><span data-ttu-id="127a5-102">다이어그램에서 테이블 간의 관계 만들기(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="127a5-102">Create Relationships Between Tables on a Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="127a5-103">다이어그램 디자이너에서 테이블 간에 열을 끌어 서로 다른 테이블의 열 간에 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-103">You can create relationships between columns in different tables in the Diagram Designer by dragging columns between tables.</span></span>  
  
### <a name="to-create-a-relationship-graphically"></a><span data-ttu-id="127a5-104">관계를 그래픽으로 만들려면</span><span class="sxs-lookup"><span data-stu-id="127a5-104">To create a relationship graphically</span></span>  
  
1.  <span data-ttu-id="127a5-105">데이터베이스 디자이너에서 다른 테이블의 열에 관련시킬 하나 이상의 데이터베이스 열에 대한 행 선택기를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-105">In Database Designer, click the row selector for one or more database columns that you want to relate to a column in another table.</span></span>  
  
2.  <span data-ttu-id="127a5-106">선택한 열을 관련 테이블로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-106">Drag the selected column(s) to the related table.</span></span>  
  
3.  <span data-ttu-id="127a5-107">**외래 키 관계** 대화 상자가 나타나고 포그라운드에 **테이블 및 열**대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-107">Two dialog boxes appear: **Foreign Key Relationship** and **Tables and Columns**, with the latter appearing in the foreground.</span></span>  
  
4.  <span data-ttu-id="127a5-108">**관계 이름** 에는 FK_*localtable*_*foreigntable*형식으로 시스템에서 제공한 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-108">**Relationship name** has a system-provided name in the format FK_*localtable*_*foreigntable*.</span></span> <span data-ttu-id="127a5-109">이 값은 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-109">You may change this value.</span></span>  
  
5.  <span data-ttu-id="127a5-110">**기본 키 테이블** 이 정확한 테이블을 지정하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-110">Verify that **Primary key table** specifies the correct table.</span></span>  
  
6.  <span data-ttu-id="127a5-111">표에 로컬 열 및 일치하는 외래 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-111">The grid lists the local columns and their matching foreign columns.</span></span> <span data-ttu-id="127a5-112">테이블 열을 추가 또는 제거하거나 매핑을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-112">You can add or remove table columns or change mappings.</span></span>  
  
7.  <span data-ttu-id="127a5-113">**확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-113">Choose **OK**.</span></span>  
  
     <span data-ttu-id="127a5-114">**외래 키 관계** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-114">The **Foreign Key Relationship** dialog box appears.</span></span> <span data-ttu-id="127a5-115">**선택한 관계** 에는 만든 관계가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-115">**Selected Relationship** shows the relationship you have created.</span></span>  
  
8.  <span data-ttu-id="127a5-116">표에서 관계 속성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-116">Change properties for the relationship in the grid.</span></span>  
  
9. <span data-ttu-id="127a5-117">**확인** 을 선택하여 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-117">Choose **OK** to create the relationship.</span></span>  
  
     <span data-ttu-id="127a5-118">데이터베이스 디자이너에서는 선택한 열 간의 관계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="127a5-118">Database Designer shows a relationship between the columns you chose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127a5-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="127a5-119">See Also</span></span>  
 <span data-ttu-id="127a5-120">[테이블 및 열 대화 상자 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-120">[Tables and Columns Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="127a5-121">[Unique 제약 조건 및 Check 제약 조건](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-121">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="127a5-122">데이터베이스 다이어그램에서 테이블 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="127a5-122">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
