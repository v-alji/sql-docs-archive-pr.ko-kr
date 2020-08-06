---
title: 다이어그램에 테이블 추가(Visual Database Tools) | Microsoft 문서 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
ms.assetid: 5440fdf7-ac04-4325-9f32-181f4cd402e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe5c1274ac390f4834bd8ac1088258061fc0406d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651432"
---
# <a name="add-tables-to-diagrams-visual-database-tools"></a><span data-ttu-id="5e98b-102">다이어그램에 테이블 추가(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="5e98b-102">Add Tables to Diagrams (Visual Database Tools)</span></span>
  <span data-ttu-id="5e98b-103">데이터베이스 다이어그램에 테이블을 추가하여 구조를 편집하거나 다이어그램에 있는 다른 테이블에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-103">You can add a table to your database diagram to edit its structure or relate it to other tables in your diagram.</span></span> <span data-ttu-id="5e98b-104">다이어그램에 기존의 데이터베이스 테이블을 추가하거나 데이터베이스에 아직 정의되지 않은 새 테이블을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-104">You can either add existing database tables to a diagram or insert a new table that has not yet been defined in the database.</span></span>  
  
### <a name="to-insert-a-new-table-into-a-diagram"></a><span data-ttu-id="5e98b-105">다이어그램에 새 테이블을 삽입하려면</span><span class="sxs-lookup"><span data-stu-id="5e98b-105">To insert a new table into a diagram</span></span>  
  
1.  <span data-ttu-id="5e98b-106">테이블을 만들 데이터베이스에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-106">Make sure you are connected to the database in which you want to create the table.</span></span>  
  
     <span data-ttu-id="5e98b-107">현재 다이어그램에 테이블을 만들려면 도구 모음에서 **새 테이블** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-107">To create a table in your current diagram, click the **New Table** button on the toolbar.</span></span>  
  
     <span data-ttu-id="5e98b-108">또는</span><span class="sxs-lookup"><span data-stu-id="5e98b-108">-or-</span></span>  
  
     <span data-ttu-id="5e98b-109">다이어그램 내부를 마우스 오른쪽 단추로 클릭하고 **새 테이블**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-109">Right-click in the diagram and select **New Table**.</span></span>  
  
2.  <span data-ttu-id="5e98b-110">**이름 선택** 대화 상자에서 시스템 할당 테이블 이름을 그대로 사용하거나 수정한 다음 **확인**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-110">Modify or accept the system-assigned table name, in the **Choose Name** dialog box, and then choose **OK**.</span></span>  
  
     <span data-ttu-id="5e98b-111">다이어그램에 새 테이블이 표준 뷰로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-111">A new table appears in the diagram in Standard view.</span></span>  
  
3.  <span data-ttu-id="5e98b-112">새 테이블의 첫째 셀에 열 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-112">In the first cell of the new table, type a column name.</span></span> <span data-ttu-id="5e98b-113">그런 다음 Tab 키를 눌러 다음 셀로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-113">Then press the TAB key to move to the next cell.</span></span>  
  
4.  <span data-ttu-id="5e98b-114">**데이터 형식**에서 해당 열의 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-114">Under **Data Type**, select a data type for the column.</span></span> <span data-ttu-id="5e98b-115">각 열에는 이름과 데이터 형식이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-115">Each column must have a name and data type.</span></span>  
  
     <span data-ttu-id="5e98b-116">테이블 디자이너에서 열의 다른 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-116">You can set the column's other properties in Table Designer.</span></span>  
  
5.  <span data-ttu-id="5e98b-117">테이블에 추가할 각 열에 대하여 3, 4단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-117">Repeat steps 3 and 4 for each column you want to add to the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e98b-118">데이터베이스 다이어그램을 저장하면 데이터베이스에 새 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-118">When you save your database diagram, the new table will be added to your database.</span></span>  
  
### <a name="to-add-an-existing-table-to-a-diagram"></a><span data-ttu-id="5e98b-119">다이어그램에 기존 테이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5e98b-119">To add an existing table to a diagram</span></span>  
  
1.  <span data-ttu-id="5e98b-120">편집할 테이블이 있는 데이터베이스에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-120">Make sure you are connected to the database whose tables you want to edit.</span></span>  
  
2.  <span data-ttu-id="5e98b-121">**테이블** 폴더에서 테이블을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-121">Select a table in the **Tables** folder.</span></span>  
  
3.  <span data-ttu-id="5e98b-122">데이터베이스 다이어그램으로 테이블을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-122">Drag the table into your database diagram.</span></span>  
  
4.  <span data-ttu-id="5e98b-123">마우스 단추를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-123">Release the mouse button.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e98b-124">다이어그램에서 선택한 테이블과 다른 테이블 사이에 관계가 있으면 자동으로 관계 선이 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-124">If relationships exist between the selected table and other tables in your diagram, relationship lines are automatically drawn.</span></span>  
  
### <a name="to-add-related-tables-to-a-diagram"></a><span data-ttu-id="5e98b-125">다이어그램에 관련 테이블을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="5e98b-125">To add related tables to a diagram</span></span>  
  
1.  <span data-ttu-id="5e98b-126">데이터베이스 다이어그램에서 외래 키 제약 조건이 있는 테이블을 하나 이상 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-126">Select one or more tables with foreign key constraints in the database diagram.</span></span>  
  
2.  <span data-ttu-id="5e98b-127">선택한 테이블 중 하나를 마우스 오른쪽 단추로 클릭하고 **관련 테이블 추가**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-127">Right-click any of the selected tables and choose **Add Related Tables**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5e98b-128">선택한 테이블에서 외래 키 제약 조건에 의해 참조되는 테이블과 외래 키 제약 조건이 있는 선택된 테이블을 참조하는 테이블 모두가 다이어그램에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e98b-128">Both those tables referenced by a foreign key constraint from the selected table(s) and those referencing the selected table(s) with a foreign key constraint are added to the diagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e98b-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e98b-129">See Also</span></span>  
 <span data-ttu-id="5e98b-130">[Visual Database Tools를 &#40;데이터베이스 다이어그램 작업&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="5e98b-130">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="5e98b-131">데이터베이스 다이어그램에서 테이블 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="5e98b-131">Work with Tables in Database Diagram &#40;Visual Database Tools&#41;</span></span>](work-with-tables-in-database-diagram-visual-database-tools.md)  
  
  
