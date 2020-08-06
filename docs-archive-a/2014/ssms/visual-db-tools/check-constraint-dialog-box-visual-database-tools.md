---
title: CHECK 제약 조건 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7244984b869a1c68e597984a1cd03e16e53d0306
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638502"
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a><span data-ttu-id="1642f-102">CHECK 제약 조건 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1642f-102">Check Constraint Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="1642f-103">이 대화 상자는 테이블 디자이너에서 테이블 정의 표를 마우스 오른쪽 단추로 클릭한 다음 **CHECK 제약 조건**을 클릭하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-103">This dialog box appears when you right-click a table definition grid in Table Designer and click **Check Constraints**.</span></span> <span data-ttu-id="1642f-104">이 대화 상자에는 데이터베이스의 테이블에 연결된 비 UNIQUE 제약 조건에 대한 속성 집합이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-104">The dialog box contains a set of properties for non-unique constraints attached to the tables in your database.</span></span> <span data-ttu-id="1642f-105">UNIQUE 제약 조건에 적용되는 속성은 **인덱스/키** 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-105">Properties applying to unique constraints appear in the **Indexes/Keys** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1642f-106">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="1642f-107">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="1642f-108">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1642f-109">옵션</span><span class="sxs-lookup"><span data-stu-id="1642f-109">Options</span></span>  
 <span data-ttu-id="1642f-110">**선택한 CHECK 제약 조건**</span><span class="sxs-lookup"><span data-stu-id="1642f-110">**Selected Check Constraints**</span></span>  
 <span data-ttu-id="1642f-111">사용할 수 있는 CHECK 제약 조건을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-111">Lists available check constraints.</span></span> <span data-ttu-id="1642f-112">제약 조건의 속성을 보려면 목록에서 제약 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-112">To view the properties of a constraint, select it in the list.</span></span>  
  
 <span data-ttu-id="1642f-113">**추가**</span><span class="sxs-lookup"><span data-stu-id="1642f-113">**Add**</span></span>  
 <span data-ttu-id="1642f-114">선택한 데이터베이스 테이블에 대한 새 제약 조건을 만들고 제약 조건에 기본 이름과 기타 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-114">Create a new constraint for the selected database table and provide a default name and other values for the constraint.</span></span> <span data-ttu-id="1642f-115">제약 조건을 유효하게 만들려면 제약 조건에 대한 식을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-115">The constraint will not become valid until an expression is entered for the constraint.</span></span>  
  
 <span data-ttu-id="1642f-116">**Delete**</span><span class="sxs-lookup"><span data-stu-id="1642f-116">**Delete**</span></span>  
 <span data-ttu-id="1642f-117">선택한 제약 조건을 테이블에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-117">Remove the selected constraint from the table.</span></span> <span data-ttu-id="1642f-118">CHECK 제약 조건 추가를 취소하려면 이 단추를 사용하여 제약 조건을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-118">To cancel the addition of a check constraint, use this button to remove the constraint.</span></span>  
  
 <span data-ttu-id="1642f-119">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="1642f-119">**General Category**</span></span>  
 <span data-ttu-id="1642f-120">확장하면 **식** 속성 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-120">Expand to show the **Expression** property field.</span></span>  
  
 <span data-ttu-id="1642f-121">**식**</span><span class="sxs-lookup"><span data-stu-id="1642f-121">**Expression**</span></span>  
 <span data-ttu-id="1642f-122">선택한 CHECK 제약 조건의 식을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-122">Displays the expression for the selected check constraint.</span></span> <span data-ttu-id="1642f-123">새 제약 조건을 만드는 경우 이 상자의 작업을 마치기 전에 식을 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-123">For new constraints, you must enter the expression before exiting this box.</span></span> <span data-ttu-id="1642f-124">기존 CHECK 제약 조건을 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-124">You can also edit existing check constraints.</span></span> <span data-ttu-id="1642f-125">자세한 내용은 [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1642f-125">For more information, see [Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md).</span></span>  
  
 <span data-ttu-id="1642f-126">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="1642f-126">**Identity Category**</span></span>  
 <span data-ttu-id="1642f-127">확장하면 **이름** 및 **설명**에 대한 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-127">Expand to show properties for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="1642f-128">**이름**</span><span class="sxs-lookup"><span data-stu-id="1642f-128">**Name**</span></span>  
 <span data-ttu-id="1642f-129">선택한 CHECK 제약 조건의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-129">Shows the name of the selected check constraint.</span></span> <span data-ttu-id="1642f-130">이 제약 조건의 이름을 변경하려면 속성 필드에 직접 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-130">To change the name of this constraint, type the text directly in the property field.</span></span>  
  
 <span data-ttu-id="1642f-131">**설명**</span><span class="sxs-lookup"><span data-stu-id="1642f-131">**Description**</span></span>  
 <span data-ttu-id="1642f-132">CHECK 제약 조건에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-132">Describing this check constraint.</span></span> <span data-ttu-id="1642f-133">속성 필드에 직접 텍스트를 입력하여 설명을 편집할 수 있고, 속성 필드의 오른쪽에 있는 줄임표( **...** )를 클릭한 다음, **설명 속성** 대화 상자에서 설명을 편집할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-133">You can edit the description by typing into the property field or you can click the ellipsis button (**...**) that appears to the right of the property field and edit the description in the **Description Property** dialog box.</span></span>  
  
 <span data-ttu-id="1642f-134">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="1642f-134">**Table Designer Category**</span></span>  
 <span data-ttu-id="1642f-135">확장하면 **만들거나 다시 활성화할 때 기존 데이터 검사**, **INSERT 및 UPDATE에 적용**, **복제에 적용**에 대한 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-135">Expand to show properties for **Check Existing Data on Creation or Re-enabling**, **Enforce For Inserts And Updates**, and **Enforce Replication**.</span></span>  
  
 <span data-ttu-id="1642f-136">**Check Existing Data On Creation or Re-Enabling**</span><span class="sxs-lookup"><span data-stu-id="1642f-136">**Check Existing Data On Creation or Re-Enabling**</span></span>  
 <span data-ttu-id="1642f-137">조건 제약에 대해 기존의 모든 데이터 즉, 제약 조건을 만들기 전부터 테이블에 있던 데이터를 검사할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-137">Specify whether all pre-existing data (data existing in the table before the constraint is created) is verified against the constraint.</span></span>  
  
 <span data-ttu-id="1642f-138">**INSERT 및 UPDATE에 적용**</span><span class="sxs-lookup"><span data-stu-id="1642f-138">**Enforce For Inserts And Updates**</span></span>  
 <span data-ttu-id="1642f-139">데이터를 테이블에 삽입하거나 테이블에서 업데이트할 때 제약 조건을 적용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-139">Specify whether the constraint is enforced when data is inserted into or updated in the table.</span></span>  
  
 <span data-ttu-id="1642f-140">**복제에 적용**</span><span class="sxs-lookup"><span data-stu-id="1642f-140">**Enforce For Replication**</span></span>  
 <span data-ttu-id="1642f-141">이 테이블에서 복제 에이전트가 삽입 또는 업데이트를 실행할 때 제약 조건을 적용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1642f-141">Indicates whether to enforce the constraint when a replication agent performs an insert or update on this table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1642f-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1642f-142">See Also</span></span>  
 <span data-ttu-id="1642f-143">[Unique 제약 조건 및 Check 제약 조건](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="1642f-143">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="1642f-144">인덱스 및 키 대화 상자 Visual Database Tools&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="1642f-144">Indexes and Keys Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
