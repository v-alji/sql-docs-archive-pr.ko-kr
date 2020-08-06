---
title: UNIQUE 제약 조건 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 74b044202f7e8e9bc762f025833cf2d0ff84c4c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661595"
---
# <a name="modify-unique-constraints"></a><span data-ttu-id="30a83-102">UNIQUE 제약 조건 수정</span><span class="sxs-lookup"><span data-stu-id="30a83-102">Modify Unique Constraints</span></span>
  <span data-ttu-id="30a83-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 UNIQUE 제약 조건을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-103">You can modify a unique constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="30a83-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="30a83-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="30a83-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="30a83-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="30a83-106">보안</span><span class="sxs-lookup"><span data-stu-id="30a83-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="30a83-107">**UNIQUE 제약 조건을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="30a83-107">**To modify a unique constraint using:**</span></span>  
  
     [<span data-ttu-id="30a83-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="30a83-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="30a83-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="30a83-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30a83-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="30a83-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30a83-111">보안</span><span class="sxs-lookup"><span data-stu-id="30a83-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30a83-112">권한</span><span class="sxs-lookup"><span data-stu-id="30a83-112">Permissions</span></span>  
 <span data-ttu-id="30a83-113">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="30a83-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="30a83-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-unique-constraint"></a><span data-ttu-id="30a83-115">UNIQUE 제약 조건을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="30a83-115">To modify a unique constraint</span></span>  
  
1.  <span data-ttu-id="30a83-116">**개체 탐색기**에서 UNIQUE 제약 조건이 포함된 테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-116">In the **Object Explorer**, right-click the table containing the unique constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="30a83-117">**테이블 디자이너** 메뉴에서 **인덱스/키...** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-117">On the **Table Designer** menu, click **Indexes/Keys...**.</span></span>  
  
3.  <span data-ttu-id="30a83-118">**인덱스/키** 대화 상자의 **선택한 기본/고유 키 및 인덱스**아래에서 편집하려는 제약 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-118">In the **Indexes/Keys** dialog box, under **Selected Primary/Unique Key or Index**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="30a83-119">다음 표의 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="30a83-120">수행할 작업</span><span class="sxs-lookup"><span data-stu-id="30a83-120">To</span></span>|<span data-ttu-id="30a83-121">수행할 단계</span><span class="sxs-lookup"><span data-stu-id="30a83-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="30a83-122">제약 조건이 연결된 열 변경</span><span class="sxs-lookup"><span data-stu-id="30a83-122">Change the columns that the constraint is associated with</span></span>|<span data-ttu-id="30a83-123">1) **(일반)** 아래의 표에서 **열** 을 클릭한 다음, 속성 오른쪽에 있는 줄임표 **(…)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-123">1) In the grid under **(General)**, click **Columns** and then click the ellipses **(...)** to the right of the property.</span></span><br /><br /> <span data-ttu-id="30a83-124">2) **인덱스 열** 대화 상자에서 인덱스에 대해 새 열 또는 정렬 순서 또는 두 가지 옵션을 모두 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-124">2) In the **Index Columns** dialog box, specify the new column or sort order or both for the index.</span></span>|  
    |<span data-ttu-id="30a83-125">제약 조건 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="30a83-125">Rename the constraint</span></span>|<span data-ttu-id="30a83-126">**ID**아래의 표에서 **이름** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-126">In the grid under **Identity**, type a new name in the **Name** box.</span></span> <span data-ttu-id="30a83-127">새 이름은 **선택한 기본/고유 키 또는 인덱스** 목록의 다른 이름과 중복되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-127">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="30a83-128">클러스터형 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="30a83-128">Set the clustered option</span></span>|<span data-ttu-id="30a83-129">**테이블 디자이너** 아래의 표에서 **클러스터형으로 만들기**를 선택한 다음 클러스터형 인덱스를 만들려면 드롭다운에서 예를 선택하고 비클러스터형 인덱스를 만들려면 아니요를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-129">In the grid under **Table Designer**, select **Create As Clustered** and from the dropdown choose Yes to create a clustered index and No to create a nonclustered one.</span></span> <span data-ttu-id="30a83-130">클러스터형 인덱스는 테이블마다 하나씩만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-130">Only one clustered index can exist per table.</span></span> <span data-ttu-id="30a83-131">클러스터형 인덱스가 이미 이 테이블에 있는 경우 원본 인덱스에 대해 이 설정을 먼저 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-131">If a clustered index already exists in this table, you must clear this setting on the original index.</span></span>|  
    |<span data-ttu-id="30a83-132">채우기 비율 정의</span><span class="sxs-lookup"><span data-stu-id="30a83-132">Define a fill factor</span></span>|<span data-ttu-id="30a83-133">**테이블 디자이너**아래의 표에서 **파일 사양** 범주를 확장하고 0에서 100 사이의 정수를 **채우기 비율** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-133">In the grid under **Table Designer**, expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill Factor** box.</span></span>|  
  
5.  <span data-ttu-id="30a83-134">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="to-modify-a-unique-constraint"></a><a name="TsqlProcedure"></a> <span data-ttu-id="30a83-135">**UNIQUE 제약 조건을 수정하려면 다음을 수행합니다.**</span><span class="sxs-lookup"><span data-stu-id="30a83-135">**To modify a unique constraint**</span></span>  
  
 <span data-ttu-id="30a83-136">Transact-SQL을 사용하여 UNIQUE 제약 조건을 수정하려면 먼저 기존 UNIQUE 제약 조건을 삭제하고 새로운 정의를 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="30a83-136">To modify a UNIQUE constraint using Transact-SQL, you must first delete the existing UNIQUE constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="30a83-137">자세한 내용은 [Delete Unique Constraints](delete-unique-constraints.md) 및 [Create Unique Constraints](create-unique-constraints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="30a83-137">For more information, see [Delete Unique Constraints](delete-unique-constraints.md) and [Create Unique Constraints](create-unique-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
