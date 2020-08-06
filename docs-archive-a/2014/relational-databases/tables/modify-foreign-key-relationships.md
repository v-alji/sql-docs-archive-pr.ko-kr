---
title: 외래 키 관계 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65538
- vdt.ppg.relationships
helpviewer_keywords:
- foreign keys [SQL Server], modifying
- modifying foreign keys
ms.assetid: 0c9ca80d-d79b-44c4-a21e-0fce39c398ec
author: stevestein
ms.author: sstein
ms.openlocfilehash: ba9010b0d634a174dd35391c870d5003aa78efa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646837"
---
# <a name="modify-foreign-key-relationships"></a><span data-ttu-id="8200d-102">외래 키 관계 수정</span><span class="sxs-lookup"><span data-stu-id="8200d-102">Modify Foreign Key Relationships</span></span>
  <span data-ttu-id="8200d-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 관계의 외래 키 측을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-103">You can modify the foreign key side of a relationship in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8200d-104">테이블의 외래 키를 수정하면 주 키 테이블의 열과 관련된 열이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-104">Modifying a table's foreign key changes which columns are related to columns in the primary key table.</span></span>  
  
 <span data-ttu-id="8200d-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="8200d-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="8200d-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="8200d-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="8200d-107">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8200d-107">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="8200d-108">보안</span><span class="sxs-lookup"><span data-stu-id="8200d-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="8200d-109">**외래 키를 수정하려면:**</span><span class="sxs-lookup"><span data-stu-id="8200d-109">**To modify a foreign key using:**</span></span>  
  
     [<span data-ttu-id="8200d-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="8200d-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="8200d-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="8200d-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="8200d-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="8200d-112">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="8200d-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="8200d-113">Limitations and Restrictions</span></span>  
 <span data-ttu-id="8200d-114">다음 경우를 제외하고 새 외래 키 열의 데이터 형식 및 크기는 관련된 기본 키 열의 데이터 형식 및 크기와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-114">The new foreign key column must match the data type and size of the primary key column to which it relates, with these exceptions:</span></span>  
  
-   <span data-ttu-id="8200d-115">`char` 열 또는 `sysname` 열은 `varchar` 열에 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-115">A `char` column or `sysname` column can relate to a `varchar` column.</span></span>  
  
-   <span data-ttu-id="8200d-116">`binary` 열은 `varbinary` 열에 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-116">A `binary` column can relate to a `varbinary` column.</span></span>  
  
-   <span data-ttu-id="8200d-117">별칭 데이터 형식은 해당 기본 형식에 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-117">An alias data type can relate to its base type.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="8200d-118">보안</span><span class="sxs-lookup"><span data-stu-id="8200d-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="8200d-119">권한</span><span class="sxs-lookup"><span data-stu-id="8200d-119">Permissions</span></span>  
 <span data-ttu-id="8200d-120">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-120">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="8200d-121">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="8200d-121">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-foreign-key"></a><span data-ttu-id="8200d-122">외래 키를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="8200d-122">To modify a foreign key</span></span>  
  
1.  <span data-ttu-id="8200d-123">**개체 탐색기**에서 외래 키를 포함하는 테이블을 확장하고 **키**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-123">In **Object Explorer**, expand the table with the foreign key and then expand **Keys**.</span></span>  
  
2.  <span data-ttu-id="8200d-124">수정할 외래 키를 마우스 오른쪽 단추로 클릭하고 **수정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-124">Right-click the foreign key to be modified and select **Modify**.</span></span>  
  
3.  <span data-ttu-id="8200d-125">**외래 키 관계** 대화 상자에서 다음과 같은 사항을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-125">In the **Foreign Key Relationships** dialog box, you can make the following modifications.</span></span>  
  
     <span data-ttu-id="8200d-126">**선택한 관계**</span><span class="sxs-lookup"><span data-stu-id="8200d-126">**Selected Relationship**</span></span>  
     <span data-ttu-id="8200d-127">기존 관계를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-127">Lists existing relationships.</span></span> <span data-ttu-id="8200d-128">관계를 선택하면 오른쪽 표에 해당 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-128">Select a relationship to show its properties in the grid to the right.</span></span> <span data-ttu-id="8200d-129">목록이 비어 있는 경우 테이블에 정의된 관계가 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-129">If the list is empty, no relationships have been defined for the table.</span></span>  
  
     <span data-ttu-id="8200d-130">**추가**</span><span class="sxs-lookup"><span data-stu-id="8200d-130">**Add**</span></span>  
     <span data-ttu-id="8200d-131">새 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-131">Create a new relationship.</span></span> <span data-ttu-id="8200d-132">관계를 유효하게 만들려면 **테이블 및 열 사양** 을 먼저 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-132">The **Tables and Columns Specifications** must be set before the relationship will be valid.</span></span>  
  
     <span data-ttu-id="8200d-133">**Delete**</span><span class="sxs-lookup"><span data-stu-id="8200d-133">**Delete**</span></span>  
     <span data-ttu-id="8200d-134">**선택한 관계** 목록에서 선택한 관계를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-134">Delete the relationship selected in the **Selected Relationships** list.</span></span> <span data-ttu-id="8200d-135">관계 추가를 취소하려면 이 단추를 사용하여 관계를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-135">To cancel the addition of a relationship, use this button to remove the relationship.</span></span>  
  
     <span data-ttu-id="8200d-136">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="8200d-136">**General Category**</span></span>  
     <span data-ttu-id="8200d-137">확장하여 **만들거나 다시 활성화할 때 기존 데이터 검사** 와 **테이블 및 열 사양**을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-137">Expand to show **Check Existing Data on Creation or RE-Enabling** and **Tables and Columns Specifications**.</span></span>  
  
     <span data-ttu-id="8200d-138">**Check Existing Data on Creation or Re-Enabling**</span><span class="sxs-lookup"><span data-stu-id="8200d-138">**Check Existing Data on Creation or Re-Enabling**</span></span>  
     <span data-ttu-id="8200d-139">제약 조건을 만들거나 다시 활성화하기 전부터 테이블에 있던 모든 데이터를 제약 조건에 대해 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-139">Verify all existing data in the table before the constraint was created or re-enabled, against the constraint.</span></span>  
  
     <span data-ttu-id="8200d-140">**테이블 및 열 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="8200d-140">**Tables and Columns Specifications Category**</span></span>  
     <span data-ttu-id="8200d-141">확장하여 어떠한 테이블의 어떠한 열이 관계에서 외래 키와 기본 키(또는 고유 키)로 사용되는지에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-141">Expand to show which columns from which tables act as the foreign key and primary (or unique) key in the relationship.</span></span> <span data-ttu-id="8200d-142">이러한 값을 편집하거나 정의하려면 속성 필드의 오른쪽에 있는 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-142">To edit or define these values, click the ellipsis button (**...**) to the right of the property field.</span></span>  
  
     <span data-ttu-id="8200d-143">**외래 키 기본 테이블**</span><span class="sxs-lookup"><span data-stu-id="8200d-143">**Foreign Key Base Table**</span></span>  
     <span data-ttu-id="8200d-144">선택한 관계에서 외래 키로 사용되는 열이 포함된 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-144">Shows which table contains the column acting as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="8200d-145">**외래 키 열**</span><span class="sxs-lookup"><span data-stu-id="8200d-145">**Foreign Key Columns**</span></span>  
     <span data-ttu-id="8200d-146">선택한 관계에서 외래 키로 사용되는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-146">Shows which column acts as a foreign key in the selected relationship.</span></span>  
  
     <span data-ttu-id="8200d-147">**Primary/Unique 키 기본 테이블**</span><span class="sxs-lookup"><span data-stu-id="8200d-147">**Primary/Unique Key Base Table**</span></span>  
     <span data-ttu-id="8200d-148">선택한 관계에서 기본 키(또는 고유 키)로 사용되는 열이 포함된 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-148">Shows which table contains the column acting as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="8200d-149">**Primary/Unique 키 열**</span><span class="sxs-lookup"><span data-stu-id="8200d-149">**Primary/Unique Key Columns**</span></span>  
     <span data-ttu-id="8200d-150">선택한 관계에서 기본 키(또는 고유 키)로 사용되는 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-150">Shows which column acts as a primary (or unique) key in the selected relationship.</span></span>  
  
     <span data-ttu-id="8200d-151">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="8200d-151">**Identity Category**</span></span>  
     <span data-ttu-id="8200d-152">확장하여 **이름** 및 **설명**에 대한 속성 필드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-152">Expand to show the property fields for **Name** and **Description**.</span></span>  
  
     <span data-ttu-id="8200d-153">**이름**</span><span class="sxs-lookup"><span data-stu-id="8200d-153">**Name**</span></span>  
     <span data-ttu-id="8200d-154">관계의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-154">Shows the name of the relationship.</span></span> <span data-ttu-id="8200d-155">새 관계를 만들면 **테이블 디자이너**의 활성 창에 있는 테이블을 기반으로 한 기본 이름이 새 관계에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-155">When a new relationship is created, it is given a default name based on the table in the active window in **Table Designer**.</span></span> <span data-ttu-id="8200d-156">언제든지 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-156">You can change the name at any time.</span></span>  
  
     <span data-ttu-id="8200d-157">**설명**</span><span class="sxs-lookup"><span data-stu-id="8200d-157">**Description**</span></span>  
     <span data-ttu-id="8200d-158">관계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-158">Describe the relationship.</span></span> <span data-ttu-id="8200d-159">자세한 설명을 기록하려면 **설명** 을 클릭한 다음 속성 필드의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-159">To write a more detailed description, click **Description** and then click the ellipsis **(...)** that appears to the right of the property field.</span></span> <span data-ttu-id="8200d-160">이렇게 하면 텍스트를 쓸 수 있는 더 큰 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-160">This provides a larger area in which to write text.</span></span>  
  
     <span data-ttu-id="8200d-161">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="8200d-161">**Table Designer Category**</span></span>  
     <span data-ttu-id="8200d-162">확장하여 **만들거나 다시 활성화할 때 기존 데이터 검사** 와 **복제에 적용**에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-162">Expand to show information for **Check Existing Data on Creation or Re-Enabling** and **Enforce for Replication**.</span></span>  
  
     <span data-ttu-id="8200d-163">**복제에 적용**</span><span class="sxs-lookup"><span data-stu-id="8200d-163">**Enforce For Replication**</span></span>  
     <span data-ttu-id="8200d-164">복제 에이전트가 이 테이블에서 삽입, 업데이트 또는 삭제를 수행할 때 제약 조건을 적용할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-164">Indicates whether to enforce the constraint when a replication agent performs an insert, update, or delete on this table.</span></span>  
  
     <span data-ttu-id="8200d-165">**외래 키 제약 조건 적용**</span><span class="sxs-lookup"><span data-stu-id="8200d-165">**Enforce Foreign Key Constraint**</span></span>  
     <span data-ttu-id="8200d-166">관계를 맺고 있는 열의 데이터를 변경할 때 외래 키 관계의 무결성 제약 조건을 위반하게 되는 경우 이러한 데이터를 변경할 수 있는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-166">Specify whether changes are allowed to the data of the columns in the relationship if those changes would invalidate the integrity of the foreign key relationship.</span></span> <span data-ttu-id="8200d-167">이러한 변경을 허용하지 않으려면 **예** 를 선택하고, 이를 허용하려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-167">Choose **Yes** if you do not want to allow such changes, and choose **No** if you do want to allow them.</span></span>  
  
     <span data-ttu-id="8200d-168">**INSERT 및 UPDATE 사양 범주**</span><span class="sxs-lookup"><span data-stu-id="8200d-168">**INSERT and UPDATE Specification Category**</span></span>  
     <span data-ttu-id="8200d-169">확장하여 관계의 **삭제 규칙** 및 **업데이트 규칙** 에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-169">Expand to show information for the **Delete Rule** and the **Update Rule** for the relationship.</span></span>  
  
     <span data-ttu-id="8200d-170">**삭제 규칙**</span><span class="sxs-lookup"><span data-stu-id="8200d-170">**Delete Rule**</span></span>  
     <span data-ttu-id="8200d-171">외래 키 관계를 맺고 있는 데이터가 포함된 행을 사용자가 삭제하려 할 때 적용할 결과를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-171">Specify what happens if a user tries to delete a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="8200d-172">**동작 안 함** 삭제가 허용되지 않고 DELETE가 롤백된다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-172">**No Action** An error message tells the user that the deletion is not allowed and the DELETE is rolled back.</span></span>  
  
    -   <span data-ttu-id="8200d-173">**계단식 배열** 외래 키 관계에 관련된 데이터가 포함된 모든 행을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-173">**Cascade** Deletes all rows containing data involved in the foreign key relationship.</span></span> <span data-ttu-id="8200d-174">논리적 레코드를 사용하는 병합 게시에 테이블이 포함되는 경우 CASCADE를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8200d-174">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="8200d-175">**Null 설정** 테이블의 모든 외래 키 열에 Null 값을 사용할 수 있으면 값을 Null로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-175">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="8200d-176">**기본값 설정** 테이블의 모든 외래 키 열에 기본값이 정의되어 있으면 열에 정의된 기본값으로 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-176">**Set Default** Sets the value to the default value defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
     <span data-ttu-id="8200d-177">**업데이트 규칙**</span><span class="sxs-lookup"><span data-stu-id="8200d-177">**Update Rule**</span></span>  
     <span data-ttu-id="8200d-178">외래 키 관계를 맺고 있는 데이터가 포함된 행을 사용자가 업데이트하려 할 때 적용할 결과를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-178">Specify what occurs if a user tries to update a row with data that is involved in a foreign key relationship:</span></span>  
  
    -   <span data-ttu-id="8200d-179">**동작 안 함** 업데이트가 허용되지 않고 UPDATE가 롤백된다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-179">**No Action** An error message tells the user that the update is not allowed and the UPDATE is rolled back.</span></span>  
  
    -   <span data-ttu-id="8200d-180">**계단식 배열** 외래 키 관계에 관련된 데이터가 포함된 모든 행을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-180">**Cascade** Updates all rows that contain data involved in the foreign key relationship.</span></span> <span data-ttu-id="8200d-181">논리적 레코드를 사용하는 병합 게시에 테이블이 포함되는 경우 CASCADE를 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="8200d-181">Do not specify CASCADE if the table will be included in a merge publication that uses logical records.</span></span>  
  
    -   <span data-ttu-id="8200d-182">**Null 설정** 테이블의 모든 외래 키 열에 Null 값을 사용할 수 있으면 값을 Null로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-182">**Set Null** Sets the value to null if all foreign key columns for the table can accept null values.</span></span>  
  
    -   <span data-ttu-id="8200d-183">**기본값 설정** 테이블의 모든 외래 키 열에 기본값이 정의되어 있으면 열에 정의된 기본값으로 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-183">**Set Default** Sets the value to the default value that is defined for the column if all foreign key columns for the table have defaults defined for them.</span></span>  
  
4.  <span data-ttu-id="8200d-184">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-184">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="8200d-185">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="8200d-185">Using Transact-SQL</span></span>  
 <span data-ttu-id="8200d-186">**외래 키를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="8200d-186">**To modify a foreign key**</span></span>  
  
 <span data-ttu-id="8200d-187">Transact-SQL을 사용하여 FOREIGN KEY 제약 조건을 수정하려면 먼저 기존 FOREIGN KEY 제약 조건을 삭제하고 새로운 정의를 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8200d-187">To modify a FOREIGN KEY constraint by using Transact-SQL, you must first delete the existing FOREIGN KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="8200d-188">자세한 내용은 [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) 및 [Create Foreign Key Relationships](create-foreign-key-relationships.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8200d-188">For more information, see [Delete Foreign Key Relationships](delete-foreign-key-relationships.md) and [Create Foreign Key Relationships](create-foreign-key-relationships.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
