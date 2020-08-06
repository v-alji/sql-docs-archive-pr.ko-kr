---
title: '연습: 데이터베이스 다이어그램 추가 및 변경 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], about database diagrams
- database diagrams [SQL Server], designing
- database diagrams [SQL Server], creating
ms.assetid: 228caa0d-8f24-46ab-86d1-b6d8631322bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: c35eb3674c817e98a25a74cd0309fc7376fe2f58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646793"
---
# <a name="walkthrough-adding-and-changing-a-database-diagram"></a><span data-ttu-id="980f1-102">연습: 데이터베이스 다이어그램 추가 및 변경</span><span class="sxs-lookup"><span data-stu-id="980f1-102">Walkthrough: Adding and Changing a Database Diagram</span></span>
  <span data-ttu-id="980f1-103">이 연습에서는 데이터베이스 다이어그램을 만들고 수정하는 방법과 데이터베이스 다이어그램 구성 요소를 통해 데이터베이스를 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-103">This walkthrough illustrates how to create and modify a database diagram and make changes to the database through the database diagrams component.</span></span> <span data-ttu-id="980f1-104">또한 다이어그램에 테이블을 추가하고, 테이블 간에 관계를 만들고, 열에 대해 제약 조건과 인덱스를 만들며 각 테이블에 대해 표시할 정보 수준을 변경하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-104">You will see how to add tables to diagrams, create relationships between tables, create constraints and indexes on columns, and change the level of information you see for each table.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="980f1-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="980f1-105">Prerequisites</span></span>  
 <span data-ttu-id="980f1-106">이 연습을 완료하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-106">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="980f1-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예제 데이터베이스를 포함하는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 에 대한 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="980f1-107">Access to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database</span></span>  
  
-   <span data-ttu-id="980f1-108">데이터베이스 소유자 `dbo` 권한이 있는 계정</span><span class="sxs-lookup"><span data-stu-id="980f1-108">An account with database owner `dbo` privileges</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="980f1-109">충분한 권한이 없는 계정을 사용하여 테이블을 변경하려고 시도하면 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-109">If you attempt to make changes when using an account without sufficient privileges to make changes to tables, then an error message appears.</span></span>  
  
## <a name="creating-a-diagram"></a><span data-ttu-id="980f1-110">다이어그램 만들기</span><span class="sxs-lookup"><span data-stu-id="980f1-110">Creating a Diagram</span></span>  
  
#### <a name="to-create-a-new-database-diagram"></a><span data-ttu-id="980f1-111">새 데이터베이스 다이어그램을 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-111">To create a new database diagram</span></span>  
  
1.  <span data-ttu-id="980f1-112">**보기** 메뉴에서 **개체 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-112">On the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="980f1-113">데이터베이스 노드를 연 다음 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 노드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-113">Open the Databases node and then open the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] node.</span></span>  
  
3.  <span data-ttu-id="980f1-114">데이터베이스 다이어그램 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 데이터베이스 다이어그램**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-114">Right-click the Database Diagrams node and choose **New Database Diagram**.</span></span>  
  
     <span data-ttu-id="980f1-115">데이터베이스에 다이어그램을 만드는 데 필요한 개체가 없는 경우에는 다음과 같은 메시지가 나타납니다. **이 데이터베이스에는 데이터베이스 다이어그램을 사용하는 데 필요한 지원 개체가 하나 이상 없습니다. 지원 개체를 만드시겠습니까?** 라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-115">If the database does not have objects necessary to create diagrams, the following message appears: **This database does not have one or more of the support objects required to use database diagramming. Do you wish to create them?**</span></span> <span data-ttu-id="980f1-116">**예**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-116">Choose **Yes**.</span></span>  
  
     <span data-ttu-id="980f1-117">**테이블 추가** 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-117">The **Add Table** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="980f1-118">**AddressType (Person)** 및 **Address (Person)** 를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-118">Select **AddressType (Person)** and **Address (Person)** and click **Add**.</span></span>  
  
     <span data-ttu-id="980f1-119">다이어그램에 두 개의 테이블이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-119">Two tables are added to the diagram.</span></span>  
  
5.  <span data-ttu-id="980f1-120">**테이블 추가** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-120">Close the **Add Table** dialog box.</span></span>  
  
#### <a name="to-view-different-column-data"></a><span data-ttu-id="980f1-121">서로 다른 열 데이터를 보려면</span><span class="sxs-lookup"><span data-stu-id="980f1-121">To view different column data</span></span>  
  
1.  <span data-ttu-id="980f1-122">`Address` 테이블을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-122">Right-click the `Address` table.</span></span> <span data-ttu-id="980f1-123">바로 가기 메뉴에서 **테이블 뷰**를 가리킨 다음 **표준**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-123">On the shortcut menu, point to **Table View**, and then click **Standard**.</span></span>  
  
     <span data-ttu-id="980f1-124">테이블 표에 **열 이름**, **데이터 형식**및 **Null 허용**의 세 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-124">The table grid shows three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
2.  <span data-ttu-id="980f1-125">`Address` 테이블을 마우스 오른쪽 단추로 클릭하고 **테이블 뷰** 를 클릭한 다음 **키**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-125">Right-click the `Address` table, click **Table View** and select **Keys**.</span></span>  
  
     <span data-ttu-id="980f1-126">테이블 표에 테이블 열 이름이 있는 하나의 열이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-126">The table grid shows one column, with the table-column names.</span></span> <span data-ttu-id="980f1-127">이때 인덱스에 참여하는 열만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-127">Only those columns participating in indexes appear.</span></span>  
  
## <a name="creating-new-tables"></a><span data-ttu-id="980f1-128">새 테이블 만들기</span><span class="sxs-lookup"><span data-stu-id="980f1-128">Creating New Tables</span></span>  
  
#### <a name="to-create-tables-within-diagram-designer"></a><span data-ttu-id="980f1-129">다이어그램 디자이너 내에서 테이블을 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-129">To create tables within Diagram Designer</span></span>  
  
1.  <span data-ttu-id="980f1-130">기존 테이블 외부에서 다이어그램 디자이너를 마우스 오른쪽 단추로 클릭한 다음 **새 테이블**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-130">Right-click the Diagram Designer outside the existing tables and choose **New Table**.</span></span>  
  
2.  <span data-ttu-id="980f1-131">**이름 선택** 대화 상자에서 **확인** 을 클릭 하 여 기본 이름을 적용 `Table1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-131">In the **Choose Name** dialog box, click **OK** to accept the default name `Table1`.</span></span>  
  
     <span data-ttu-id="980f1-132">새 테이블 표에 **열 이름**, **데이터 형식**및 **Null 허용**의 세 열이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-132">A new table grid appears with three columns: **Column Name**, **Data Type**, and **Allow Nulls**.</span></span>  
  
3.  <span data-ttu-id="980f1-133">에 다음 정보를 추가 합니다 `Table1` .</span><span class="sxs-lookup"><span data-stu-id="980f1-133">Add the following information to `Table1`:</span></span>  
  
    |<span data-ttu-id="980f1-134">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="980f1-134">**Column Name**</span></span>|<span data-ttu-id="980f1-135">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="980f1-135">**Data Type**</span></span>|<span data-ttu-id="980f1-136">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="980f1-136">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T1col1`|`int`|<span data-ttu-id="980f1-137">checked</span><span class="sxs-lookup"><span data-stu-id="980f1-137">checked</span></span>|  
    |`T1col2`|`varchar(50)`|<span data-ttu-id="980f1-138">checked</span><span class="sxs-lookup"><span data-stu-id="980f1-138">checked</span></span>|  
    |`T1col3`|`float`|<span data-ttu-id="980f1-139">선택</span><span class="sxs-lookup"><span data-stu-id="980f1-139">checked</span></span>|  
  
4.  <span data-ttu-id="980f1-140">`T1col1` 을 마우스 오른쪽 단추로 클릭한 다음 **기본 키 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-140">Right-click `T1col1` and select **Set Primary Key**.</span></span>  
  
     <span data-ttu-id="980f1-141">열 이름 옆에 키 아이콘이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-141">A key icon will appear beside the column name.</span></span>  
  
5.  <span data-ttu-id="980f1-142">**파일** 메뉴에서 **Diagram1 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-142">From the **File** menu, click **Save Diagram1**.</span></span>  
  
6.  <span data-ttu-id="980f1-143">**이름 선택** 대화 상자에서 **확인** 을 클릭 하 여 기본 이름을 적용 `Diagram1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-143">In the **Choose Name** dialog box, click **OK** to accept the default name `Diagram1`.</span></span>  
  
7.  <span data-ttu-id="980f1-144">**을 데이터베이스에 저장한다는 메시지가 포함된** 저장 `Table1` 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-144">The **Save** dialog box appears with a message that `Table1` will be saved to the database.</span></span> <span data-ttu-id="980f1-145">**예**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-145">Click **Yes**.</span></span>  
  
## <a name="modifying-table-structure"></a><span data-ttu-id="980f1-146">테이블 구조 수정</span><span class="sxs-lookup"><span data-stu-id="980f1-146">Modifying Table Structure</span></span>  
 <span data-ttu-id="980f1-147">다이어그램 디자이너에서 CHECK 제약 조건을 추가하고 테이블 간에 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-147">You can add check constraints and make relationships between tables in Diagram Designer.</span></span>  
  
#### <a name="to-create-check-constraints"></a><span data-ttu-id="980f1-148">CHECK 제약 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-148">To create check constraints</span></span>  
  
1.  <span data-ttu-id="980f1-149">`Table1`에서 `T1col3` 행을 마우스 오른쪽 단추로 클릭한 다음 **CHECK 제약 조건**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-149">In `Table1`, right-click the `T1col3` row and choose **Check Constraints**.</span></span>  
  
     <span data-ttu-id="980f1-150">**CHECK 제약 조건** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-150">The **Check Constraints** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="980f1-151">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-151">Click **Add**.</span></span>  
  
     <span data-ttu-id="980f1-152">**선택한 CHECK 제약 조건** 목록에 새 제약 조건은 기본 이름인 `CK_Table1`로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-152">A new constraint appears in the **Selected Check Constraint** list, with the default name `CK_Table1`.</span></span>  
  
3.  <span data-ttu-id="980f1-153">표에서 **식** 행을 선택하고 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-153">Select the **Expression** row in the grid and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="980f1-154">**CHECK 제약 조건 식** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-154">The **Check Constraint Expression** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="980f1-155">`T1col3 > 5` 를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-155">Type `T1col3 > 5` and click **OK**.</span></span>  
  
     <span data-ttu-id="980f1-156">`Table1` 이제 `T1col3` 에 입력하는 모든 값이 5보다 커야 한다는 제약 조건이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-156">`Table1` now has a constraint that all values entered into `T1col3` must be greater than 5.</span></span>  
  
5.  <span data-ttu-id="980f1-157">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-157">Click **Close**.</span></span>  
  
#### <a name="to-create-relationships-between-tables"></a><span data-ttu-id="980f1-158">테이블 간에 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-158">To create relationships between tables</span></span>  
  
1.  <span data-ttu-id="980f1-159">다이어그램 디자이너에서 다음 열이 있는 `Table2` 라는 새 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-159">Create a new table in Diagram designer named `Table2` with the following columns:</span></span>  
  
    |<span data-ttu-id="980f1-160">**열 이름**</span><span class="sxs-lookup"><span data-stu-id="980f1-160">**Column Name**</span></span>|<span data-ttu-id="980f1-161">**데이터 형식**</span><span class="sxs-lookup"><span data-stu-id="980f1-161">**Data Type**</span></span>|<span data-ttu-id="980f1-162">**Null 허용**</span><span class="sxs-lookup"><span data-stu-id="980f1-162">**Allow Nulls**</span></span>|  
    |---------------------|-------------------|---------------------|  
    |`T2col1`|`int`|<span data-ttu-id="980f1-163">선택 안 함</span><span class="sxs-lookup"><span data-stu-id="980f1-163">not checked</span></span>|  
    |`T2col2`|`varchar(50)`|<span data-ttu-id="980f1-164">checked</span><span class="sxs-lookup"><span data-stu-id="980f1-164">checked</span></span>|  
    |`T2col3`|`xml`|<span data-ttu-id="980f1-165">checked</span><span class="sxs-lookup"><span data-stu-id="980f1-165">checked</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="980f1-166">외래 키 관계의 기본 키 쪽에 있는 열은 기본 키나 UNIQUE 제약 조건에 참여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-166">The columns on the primary key side of a foreign key relationship must participate in either a Primary Key or a Unique Constraint.</span></span>  
  
2.  <span data-ttu-id="980f1-167">`T2col1` 을 `T1col1`로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-167">Drag `T2col1` to `T1col1`.</span></span>  
  
     <span data-ttu-id="980f1-168">백그라운드의 **외래 키 관계** 대화 상자와 포그라운드의 **테이블 및 열** 대화 상자 두 개가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-168">Two dialog boxes appear: **Foreign Key Relationship** in the background and **Tables and Columns** in the foreground.</span></span>  
  
3.  <span data-ttu-id="980f1-169">**확인** 을 클릭하여 새 관계를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-169">Click **OK** to save the new relationship.</span></span>  
  
4.  <span data-ttu-id="980f1-170">**확인** 을 다시 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-170">Click **OK** again.</span></span>  
  
## <a name="creating-indexes"></a><span data-ttu-id="980f1-171">인덱스 만들기</span><span class="sxs-lookup"><span data-stu-id="980f1-171">Creating Indexes</span></span>  
 <span data-ttu-id="980f1-172">XML을 포함하여 대부분의 데이터 형식에 대해 인덱스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-172">You can create indexes on most types of data, including XML.</span></span>  
  
#### <a name="to-create-a-standard-index"></a><span data-ttu-id="980f1-173">표준 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-173">To create a standard index</span></span>  
  
1.  <span data-ttu-id="980f1-174">`Table1` 을 마우스 오른쪽 단추로 클릭한 다음 **인덱스/키**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-174">Right-click `Table1` and choose **Indexes/Keys**.</span></span>  
  
     <span data-ttu-id="980f1-175">**인덱스/키** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-175">The **Indexes/Keys** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="980f1-176">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-176">Click **Add**.</span></span>  
  
     <span data-ttu-id="980f1-177">**선택한 Primary/Unique 키 또는 인덱스** 목록에 새 인덱스가 `IX_Table1`과 비슷한 기본 이름으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-177">A new index appears in the **Selected Primary/Unique Key or Index** list, with a default name similar to `IX_Table1`.</span></span>  
  
3.  <span data-ttu-id="980f1-178">**열** 행을 선택하고 줄임표 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-178">Select the **Columns** row and click the ellipsis button.</span></span>  
  
     <span data-ttu-id="980f1-179">**인덱스 열** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-179">The **Index Columns** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="980f1-180">**열 이름** 아래의 드롭다운 화살표를 클릭하고 `T1col2`를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-180">Click the drop-down arrow under **Column Name** and select `T1col2`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="980f1-181">`T1col2` 아래의 셀을 선택하고 다른 열 이름을 선택하여 이 인덱스에 열을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-181">You may add additional columns to this index by selecting the cell below `T1col2` and choosing another column name.</span></span>  
  
5.  <span data-ttu-id="980f1-182">**확인** 을 클릭하여 이 인덱스를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-182">Click **OK** to save this index.</span></span>  
  
6.  <span data-ttu-id="980f1-183">**인덱스/키** 대화 상자에서 **닫기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-183">Click **Close** in the **Indexes/Keys** dialog box.</span></span>  
  
#### <a name="to-create-an-xml-index"></a><span data-ttu-id="980f1-184">XML 인덱스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="980f1-184">To create an XML index</span></span>  
  
1.  <span data-ttu-id="980f1-185">`T2col1` 을 마우스 오른쪽 단추로 클릭한 다음 **기본 키 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-185">Right-click `T2col1` and choose **Set Primary Key**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="980f1-186">XML 인덱스를 추가하려면 테이블의 다른 열을 클러스터형 기본 키로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-186">Adding an XML index requires that another column in the table be set as a clustered primary key.</span></span>  
  
2.  <span data-ttu-id="980f1-187">`T2col3` 의 `Table2` 행을 마우스 오른쪽 단추로 클릭한 다음 **XML 인덱스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-187">Right-click the `T2col3` row in `Table2` and select **XML Indexes**.</span></span>  
  
     <span data-ttu-id="980f1-188">**XML 인덱스** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-188">The **XML Indexes** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="980f1-189">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-189">Click **Add**.</span></span>  
  
     <span data-ttu-id="980f1-190">**선택한 XML 인덱스** 목록에 기본값이 지정된 XML 인덱스가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-190">An XML index with default values will be added to the **Selected XML Index** list.</span></span>  
  
4.  <span data-ttu-id="980f1-191">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-191">Click **Close**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="980f1-192">XML 인덱스는 열별로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-192">XML indexes are created per-column.</span></span> <span data-ttu-id="980f1-193">첫 번째 XML 인덱스는 기본 인덱스이고 추가 인덱스는 모두 보조 인덱스입니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-193">The first XML index is primary; any additional indexes are secondary.</span></span>  
  
## <a name="saving-the-diagram"></a><span data-ttu-id="980f1-194">다이어그램 저장</span><span class="sxs-lookup"><span data-stu-id="980f1-194">Saving the Diagram</span></span>  
 <span data-ttu-id="980f1-195">저장하기 전까지는 다이어그램에 대한 변경 내용이 데이터베이스에 게시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-195">All of the changes you make to a diagram are not posted to the database until you save it.</span></span> <span data-ttu-id="980f1-196">문제 또는 충돌이 있을 경우 대화 상자에 추가 정보가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-196">If there are problems or conflicts, a dialog box appears with more information.</span></span>  
  
#### <a name="to-save-a-database-diagram"></a><span data-ttu-id="980f1-197">데이터베이스 다이어그램을 저장하려면</span><span class="sxs-lookup"><span data-stu-id="980f1-197">To save a database diagram</span></span>  
  
1.  <span data-ttu-id="980f1-198">**파일** 메뉴에서 **Diagram1 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-198">On the **File** menu, select **Save Diagram1**.</span></span>  
  
     <span data-ttu-id="980f1-199">**저장** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-199">The **Save** dialog box appears.</span></span> <span data-ttu-id="980f1-200">**영향을 받는 테이블 경고** 를 선택하면 새 테이블이나 변경된 테이블에 대한 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-200">If **Warn about Tables Affected** is selected, information about new or changed tables is listed.</span></span>  
  
2.  <span data-ttu-id="980f1-201">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-201">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="980f1-202">오류가 발생하면 **저장 후 알림** 대화 상자에 오류와 원인이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-202">If any errors occurred, the **Post-Save Notifications** dialog box appears with the errors and their causes.</span></span> <span data-ttu-id="980f1-203">오류를 수정하고 다이어그램을 다시 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-203">Fix the errors and save the diagram again.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="980f1-204">다음 단계</span><span class="sxs-lookup"><span data-stu-id="980f1-204">Next Steps</span></span>  
 <span data-ttu-id="980f1-205">이는 기존 테이블 두 개와 새 테이블 두 개만으로 이루어진 기본 다이어그램이지만 이 다이어그램을 만들어본 사용자라면 시각적으로 새 스키마를 만들거나 기존 데이터베이스를 다이어그램으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-205">This is a basic diagram with just two existing and two new tables, but it illustrates the potential for diagramming an existing database or creating a new schema visually.</span></span> <span data-ttu-id="980f1-206">다음을 추가로 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="980f1-206">Suggestions for more exploration include:</span></span>  
  
-   <span data-ttu-id="980f1-207">관련 테이블 그룹을 포함하는 새 다이어그램 만들기</span><span class="sxs-lookup"><span data-stu-id="980f1-207">Create new diagrams containing groups of related tables</span></span>  
  
-   <span data-ttu-id="980f1-208">각 테이블에 대해 표시되는 정보의 양 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="980f1-208">Customize the amount of information shown for each table</span></span>  
  
-   <span data-ttu-id="980f1-209">레이아웃 변경 및 주석 추가</span><span class="sxs-lookup"><span data-stu-id="980f1-209">Change the layout and add annotations</span></span>  
  
-   <span data-ttu-id="980f1-210">비트맵으로 다이어그램 복사</span><span class="sxs-lookup"><span data-stu-id="980f1-210">Copy the diagram to a bitmap</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="980f1-211">참고 항목</span><span class="sxs-lookup"><span data-stu-id="980f1-211">See Also</span></span>  
 <span data-ttu-id="980f1-212">[Visual Database Tools &#40;다이어그램에 표시 되는 정보의 양을 사용자 지정&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-212">[Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 <span data-ttu-id="980f1-213">[Visual Database Tools를 &#40;데이터베이스 다이어그램 디자이너 설정&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-213">[Set Up Database Diagram Designer &#40;Visual Database Tools&#41;](set-up-database-diagram-designer-visual-database-tools.md) </span></span>  
 <span data-ttu-id="980f1-214">[다이어그램에 테이블 추가 &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-214">[Add Tables to Diagrams &#40;Visual Database Tools&#41;](add-tables-to-diagrams-visual-database-tools.md) </span></span>  
 <span data-ttu-id="980f1-215">[다이어그램에서 테이블 간의 관계 만들기 Visual Database Tools &#40;&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-215">[Create Relationships Between Tables on a Diagram &#40;Visual Database Tools&#41;](create-relationships-between-tables-on-a-diagram-visual-database-tools.md) </span></span>  
 <span data-ttu-id="980f1-216">[XML 인덱스 만들기](../../relational-databases/xml/create-xml-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-216">[Create XML Indexes](../../relational-databases/xml/create-xml-indexes.md) </span></span>  
 <span data-ttu-id="980f1-217">[Visual Database Tools를 &#40;데이터베이스 다이어그램의 이미지를 클립보드에 복사&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="980f1-217">[Copy an Image of a Database Diagram to the Clipboard &#40;Visual Database Tools&#41;](copy-an-image-of-a-database-diagram-to-the-clipboard-visual-database-tools.md) </span></span>  
 [<span data-ttu-id="980f1-218">다이어그램 레이아웃 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="980f1-218">Work with Diagram Layout &#40;Visual Database Tools&#41;</span></span>](work-with-diagram-layout-visual-database-tools.md)  
  
  
