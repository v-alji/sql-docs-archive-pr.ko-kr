---
title: 인덱스 및 키 대화 상자 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68c9022f3ea7803f372e7c349e0dc75b1fc56adc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638489"
---
# <a name="indexes-and-keys-dialog-box-visual-database-tools"></a><span data-ttu-id="c434a-102">인덱스 및 키 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c434a-102">Indexes and Keys Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="c434a-103">이 대화 상자를 사용하면 인덱스, 기본 키, 고유 키를 만들거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-103">Use this dialog box to create or modify indexes, primary keys, and unique keys.</span></span> <span data-ttu-id="c434a-104">이 대화 상자에 액세스하려면 인덱스나 키가 포함된 테이블의 테이블 정의를 열고 테이블 정의 표를 마우스 오른쪽 단추로 클릭한 다음 **인덱스/키**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-104">To access this dialog box, open the table definition for the table with the index or key, right-click the table definition grid, and then click **Indexes/Keys**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c434a-105">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-105">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="c434a-106">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-106">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="c434a-107">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-107">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c434a-108">옵션</span><span class="sxs-lookup"><span data-stu-id="c434a-108">Options</span></span>  
 <span data-ttu-id="c434a-109">**선택한 Primary/Unique 키 또는 인덱스**</span><span class="sxs-lookup"><span data-stu-id="c434a-109">**Selected Primary/Unique Key or Index**</span></span>  
 <span data-ttu-id="c434a-110">기존의 기본 또는 고유 키와 인덱스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-110">Lists existing primary or unique keys and indexes.</span></span> <span data-ttu-id="c434a-111">키나 인덱스를 선택하면 오른쪽의 표에 해당 속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-111">Select one to show its properties in the grid to the right.</span></span> <span data-ttu-id="c434a-112">목록이 비어 있는 경우 테이블에 정의된 항목이 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-112">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="c434a-113">**추가**</span><span class="sxs-lookup"><span data-stu-id="c434a-113">**Add**</span></span>  
 <span data-ttu-id="c434a-114">기본 키나 인덱스 또는 고유 키나 인덱스를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-114">Create a new primary or unique key or index.</span></span>  
  
 <span data-ttu-id="c434a-115">**Delete**</span><span class="sxs-lookup"><span data-stu-id="c434a-115">**Delete**</span></span>  
 <span data-ttu-id="c434a-116">**선택된 기본/고유 키 또는 인덱스** 목록에서 선택한 키나 인덱스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-116">Delete the key or index selected in the **Selected Primary/Unique Key or Index** list.</span></span>  
  
 <span data-ttu-id="c434a-117">**일반 범주**</span><span class="sxs-lookup"><span data-stu-id="c434a-117">**General Category**</span></span>  
 <span data-ttu-id="c434a-118">확장하면 **열**, **고유**및 **형식**속성이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-118">When expanded, shows the properties **Columns**, **Is Unique**, and **Type**.</span></span>  
  
 <span data-ttu-id="c434a-119">**열**</span><span class="sxs-lookup"><span data-stu-id="c434a-119">**Columns**</span></span>  
 <span data-ttu-id="c434a-120">선택된 정렬 순서대로 키나 인덱스의 열을 나열합니다. 이 옵션을 통해 정렬 순서를 정의하기 위한 대화 상자를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-120">Lists chosen sort orders for the columns in the key or index, and provides access to a dialog box where the sort orders can be defined.</span></span> <span data-ttu-id="c434a-121">대화 상자를 표시하려면 **열** 을 클릭한 다음, 속성 필드 오른쪽에 나타나는 줄임표 단추(...)를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-121">To display the dialog box, click **Columns** and then click the ellipsis button (...) that appears to the right of the property field.</span></span>  
  
 <span data-ttu-id="c434a-122">**고유**</span><span class="sxs-lookup"><span data-stu-id="c434a-122">**Is Unique**</span></span>  
 <span data-ttu-id="c434a-123">현재 인덱스나 키에 입력한 데이터가 중복되지 않아야 하는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-123">Indicates whether data entered into this index or key must be unique.</span></span> <span data-ttu-id="c434a-124">XML 인덱스에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-124">This is unavailable for XML Indexes.</span></span>  
  
 <span data-ttu-id="c434a-125">**형식**</span><span class="sxs-lookup"><span data-stu-id="c434a-125">**Type**</span></span>  
 <span data-ttu-id="c434a-126">**선택된 기본/고유 키 또는 인덱스** 목록에서 선택한 항목이 고유 키, 기본 키 또는 인덱스인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-126">Specify whether the item selected in the **Selected Primary/Unique Key or Index** list is a unique key, a primary key, or an index.</span></span> <span data-ttu-id="c434a-127">기본 키의 경우 이 필드는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-127">For primary keys this field is read-only.</span></span>  
  
 <span data-ttu-id="c434a-128">**ID 범주**</span><span class="sxs-lookup"><span data-stu-id="c434a-128">**Identity Category**</span></span>  
 <span data-ttu-id="c434a-129">확장하면 **이름** 및 **설명**에 대한 속성 필드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-129">When expanded, it shows the property fields for **Name** and **Description**.</span></span>  
  
 <span data-ttu-id="c434a-130">**이름**</span><span class="sxs-lookup"><span data-stu-id="c434a-130">**Name**</span></span>  
 <span data-ttu-id="c434a-131">키나 인덱스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-131">Shows the name of the key or index.</span></span> <span data-ttu-id="c434a-132">키나 인덱스를 새로 만들면 테이블 디자이너의 활성 창에 있는 테이블을 기반으로 한 기본 이름이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-132">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="c434a-133">언제든지 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-133">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="c434a-134">**설명**</span><span class="sxs-lookup"><span data-stu-id="c434a-134">**Description**</span></span>  
 <span data-ttu-id="c434a-135">키나 인덱스에 대한 설명을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-135">Provides a place to describe the key or index.</span></span> <span data-ttu-id="c434a-136">자세한 설명을 기록하려면 **설명**을 클릭한 다음, 속성 필드의 오른쪽에 있는 줄임표 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-136">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="c434a-137">이렇게 하면 텍스트를 쓸 수 있는 더 큰 영역이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-137">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="c434a-138">**테이블 디자이너 범주**</span><span class="sxs-lookup"><span data-stu-id="c434a-138">**Table Designer Category**</span></span>  
 <span data-ttu-id="c434a-139">확장하면 **클러스터형으로 만들기**에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-139">When expanded, shows information for **Create as Clustered**.</span></span>  
  
 <span data-ttu-id="c434a-140">**클러스터형으로 만들기**</span><span class="sxs-lookup"><span data-stu-id="c434a-140">**Create as Clustered**</span></span>  
 <span data-ttu-id="c434a-141">클러스터형 키나 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-141">Make the key or index clustered.</span></span> <span data-ttu-id="c434a-142">한 테이블에는 클러스터형 인덱스가 하나만 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-142">Only one clustered index is allowed on a table.</span></span> <span data-ttu-id="c434a-143">테이블의 데이터는 클러스터형 인덱스의 순서대로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-143">Data in the table is stored in the order of the clustered index.</span></span> <span data-ttu-id="c434a-144">자세한 내용은 [클러스터형 인덱스 만들기](../../relational-databases/indexes/indexes.md) 및 [비클러스터형 인덱스 만들기](../../relational-databases/indexes/create-nonclustered-indexes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c434a-144">For more information, see [Create Clustered Indexes](../../relational-databases/indexes/indexes.md) and [Create Nonclustered Indexes](../../relational-databases/indexes/create-nonclustered-indexes.md).</span></span>  
  
 <span data-ttu-id="c434a-145">**데이터 공간 사양**</span><span class="sxs-lookup"><span data-stu-id="c434a-145">**Data Space Specification**</span></span>  
 <span data-ttu-id="c434a-146">확장하면 **(데이터 공간 형식)** , **파일 그룹 또는 파티션 구성표 이름**및 **파티션 열 목록**에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-146">When expanded, shows information for **(Data Space Type)**, **Filegroup or Partition Scheme Name**, and **Partition Column List**.</span></span>  
  
 <span data-ttu-id="c434a-147">**(데이터 공간 형식)**</span><span class="sxs-lookup"><span data-stu-id="c434a-147">**(Data Space Type)**</span></span>  
 <span data-ttu-id="c434a-148">현재 인덱스나 키가 파일 그룹 또는 분할 구성표에 속해 있는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-148">Indicates whether this index or key belongs to a file group or partition scheme.</span></span>  
  
 <span data-ttu-id="c434a-149">**파일 그룹 또는 파티션 구성표 이름**</span><span class="sxs-lookup"><span data-stu-id="c434a-149">**Filegroup or Partition Scheme Name**</span></span>  
 <span data-ttu-id="c434a-150">인덱스나 키가 저장된 파일 그룹 또는 분할 구성표의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-150">Shows the name of the file group or partition scheme on which it is stored.</span></span>  
  
 <span data-ttu-id="c434a-151">**파티션 열 목록**</span><span class="sxs-lookup"><span data-stu-id="c434a-151">**Partition Column List**</span></span>  
 <span data-ttu-id="c434a-152">분할 열 함수에 관련된 열의 목록을 쉼표로 구분하여 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-152">Displays a comma-separated list of columns that participate in the partition column function.</span></span> <span data-ttu-id="c434a-153">**(데이터 공간 형식)** 필드에서 파일 그룹을 선택한 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-153">Unavailable if Filegroup is selected in the **(Data Space Type)** field.</span></span>  
  
 <span data-ttu-id="c434a-154">**채우기 사양**</span><span class="sxs-lookup"><span data-stu-id="c434a-154">**Fill Specification**</span></span>  
 <span data-ttu-id="c434a-155">확장하면 **채우기 비율** 과 **인덱스 패딩**에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-155">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="c434a-156">**채우기 비율**</span><span class="sxs-lookup"><span data-stu-id="c434a-156">**Fill Factor**</span></span>  
 <span data-ttu-id="c434a-157">시스템에서 채울 수 있는 인덱스의 리프 수준 페이지에 대한 비율을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-157">Specifies what percentage of the index's leaf-level pages the system can fill.</span></span> <span data-ttu-id="c434a-158">페이지가 가득 찬 경우 시스템에서 페이지를 분할하여 새 데이터를 추가하므로 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-158">Once a page is full, the system must split the pages to add new data, impairing performance.</span></span>  
  
-   <span data-ttu-id="c434a-159">값을 100으로 설정하면 페이지가 가득차므로</span><span class="sxs-lookup"><span data-stu-id="c434a-159">A value of 100 means the pages will be full.</span></span> <span data-ttu-id="c434a-160">스토리지 공간이 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-160">This will require the least amount of storage space.</span></span> <span data-ttu-id="c434a-161">이 설정은 읽기 전용 테이블처럼 데이터를 변경하는 작업이 없을 경우에만 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-161">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="c434a-162">값이 작을 수록 데이터 페이지에 빈 공간이 더 많이 남습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-162">A lower value leaves more empty space on the data pages.</span></span> <span data-ttu-id="c434a-163">이로 인해 인덱스 증가에 따라 데이터 페이지를 분할해야 할 필요성은 줄어들지만 더 많은 스토리지 공간이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-163">This reduces the need to split data pages as indexes grow but requires more storage space.</span></span>  
  
 <span data-ttu-id="c434a-164">**인덱스 패딩**</span><span class="sxs-lookup"><span data-stu-id="c434a-164">**Pad Index**</span></span>  
 <span data-ttu-id="c434a-165">인덱스가 증가하는 경우 현재 인덱스의 중간 페이지가 **채우기 비율** 에 지정된 빈 공간(패딩)과 동일한 비율로 제공되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-165">Indicate whether intermediate pages in this index are provided the same percentage of empty space (padding) specified in **Fill Factor** when they grow.</span></span>  
  
 <span data-ttu-id="c434a-166">**중복 키 무시**</span><span class="sxs-lookup"><span data-stu-id="c434a-166">**Ignore Duplicate Keys**</span></span>  
 <span data-ttu-id="c434a-167">기존의 키 값과 동일한 키 값이 있는 일괄 삽입 작업을 진행하는 동안 행이 삽입되는 경우 적용할 결과를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-167">Specify what happens when a row is inserted during a bulk insert operation whose key value equals an existing key value.</span></span> <span data-ttu-id="c434a-168">다음 옵션을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-168">If you choose:</span></span>  
  
-   <span data-ttu-id="c434a-169">**예** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 경고가 표시되고 문제가 발생한 행을 삽입하지 않은 채 나머지 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-169">**Yes** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues a warning, ignores the offending incoming row, and tries to insert the remaining rows.</span></span>  
  
-   <span data-ttu-id="c434a-170">**아니요** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 오류 메시지가 표시되고 일괄 삽입 작업 전체가 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-170">**No** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] issues an error message and rolls back the entire bulk insert operation.</span></span>  
  
 <span data-ttu-id="c434a-171">**포함된 열**</span><span class="sxs-lookup"><span data-stu-id="c434a-171">**Included Columns**</span></span>  
 <span data-ttu-id="c434a-172">인덱스 키를 구성하는 열 전체의 이름을 쉼표로 구분된 목록으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-172">Displays a comma-separated list of the names of all the columns that constitute the index key.</span></span> <span data-ttu-id="c434a-173">하위 키 열은 비클러스터형 인덱스에 대해서만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-173">Subkey columns can only be specified for nonclustered indexes.</span></span> <span data-ttu-id="c434a-174">XML 인덱스에 대해서는 이 속성이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-174">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="c434a-175">**비활성화**</span><span class="sxs-lookup"><span data-stu-id="c434a-175">**Is Disabled**</span></span>  
 <span data-ttu-id="c434a-176">현재 인덱스가 비활성화되었는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-176">Indicates whether this index is disabled.</span></span> <span data-ttu-id="c434a-177">이 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-177">This is a read-only property.</span></span> <span data-ttu-id="c434a-178">Visual Database Tools 외부에서 인덱스를 비활성화한 경우에는 이 속성이 **예** 로만 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-178">This property is only set to **Yes** if the index has been disabled outside of the Visual Database tools.</span></span>  
  
 <span data-ttu-id="c434a-179">**전체 텍스트 키**</span><span class="sxs-lookup"><span data-stu-id="c434a-179">**Is Full-Text Key**</span></span>  
 <span data-ttu-id="c434a-180">현재 인덱스가 전체 텍스트 키인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-180">Specify whether this index is a full-text key.</span></span> <span data-ttu-id="c434a-181">전체 텍스트 키에 대한 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c434a-181">For more information on full-text keys, see SQL Server Books Online.</span></span> <span data-ttu-id="c434a-182">XML 인덱스에 대해서는 이 속성이 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-182">This property is hidden for XML indexes.</span></span>  
  
 <span data-ttu-id="c434a-183">**페이지 잠금 허용**</span><span class="sxs-lookup"><span data-stu-id="c434a-183">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="c434a-184">현재 인덱스에 대해 페이지 수준의 잠금이 허용되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-184">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="c434a-185">페이지 수준의 잠금 허용 여부는 데이터베이스 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-185">Allowing or disallowing page-level locking affects database performance.</span></span> <span data-ttu-id="c434a-186">권장 설정은 **예**입니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-186">The recommended setting is **Yes**.</span></span>  
  
 <span data-ttu-id="c434a-187">**통계 다시 계산**</span><span class="sxs-lookup"><span data-stu-id="c434a-187">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="c434a-188">인덱스를 만들 때 기본 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 통계를 새로 계산할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-188">Specify whether the underlying [!INCLUDE[ssDE](../../includes/ssde-md.md)] computes new statistics when the index is created.</span></span> <span data-ttu-id="c434a-189">통계를 다시 계산하면 인덱스 작성 속도가 느려지지만 쿼리 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-189">Re-computing statistics slows the building of indexes but will very likely improve query performance.</span></span>  
  
 <span data-ttu-id="c434a-190">**행 잠금 허용**</span><span class="sxs-lookup"><span data-stu-id="c434a-190">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="c434a-191">현재 인덱스에 대해 행 수준의 잠금이 허용되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-191">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="c434a-192">행 수준의 잠금 허용 여부는 데이터베이스 성능에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-192">Allowing or disallowing row-level locking affects database performance.</span></span> <span data-ttu-id="c434a-193">권장 설정은 **예**입니다.</span><span class="sxs-lookup"><span data-stu-id="c434a-193">The recommended setting is **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c434a-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c434a-194">See Also</span></span>  
 <span data-ttu-id="c434a-195">[Unique 제약 조건 및 Check 제약 조건](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="c434a-195">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="c434a-196">PRIMARY KEY 및 FOREIGN KEY 제약 조건</span><span class="sxs-lookup"><span data-stu-id="c434a-196">Primary and Foreign Key Constraints</span></span>](../../relational-databases/tables/primary-and-foreign-key-constraints.md)  
  
  
