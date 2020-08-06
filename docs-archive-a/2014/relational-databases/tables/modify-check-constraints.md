---
title: CHECK 제약 조건 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8377c80590612c8b68c315f7c37823eb8f5c5093
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652028"
---
# <a name="modify-check-constraints"></a><span data-ttu-id="62583-102">CHECK 제약 조건 수정</span><span class="sxs-lookup"><span data-stu-id="62583-102">Modify Check Constraints</span></span>
  <span data-ttu-id="62583-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서는 특정 조건에 대한 제약 조건을 설정 또는 해제하는 옵션 또는 제약 조건 식을 변경할 때 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 을 사용하여 CHECK 제약 조건을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="62583-103">You can modify a check constraint in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] when you want to change the constraint expression or the options that enable or disable the constraint for specific conditions.</span></span>  
  
 <span data-ttu-id="62583-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="62583-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="62583-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="62583-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="62583-106">보안</span><span class="sxs-lookup"><span data-stu-id="62583-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="62583-107">**CHECK 제약 조건을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="62583-107">**To modify a check constraint using:**</span></span>  
  
     [<span data-ttu-id="62583-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="62583-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="62583-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="62583-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="62583-110">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="62583-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="62583-111">보안</span><span class="sxs-lookup"><span data-stu-id="62583-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="62583-112">권한</span><span class="sxs-lookup"><span data-stu-id="62583-112">Permissions</span></span>  
 <span data-ttu-id="62583-113">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-113">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="62583-114">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="62583-114">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-check-constraint"></a><span data-ttu-id="62583-115">CHECK 제약 조건을 수정하려면</span><span class="sxs-lookup"><span data-stu-id="62583-115">To modify a check constraint</span></span>  
  
1.  <span data-ttu-id="62583-116">**개체 탐색기**에서 CHECK 제약 조건이 포함된 테이블을 마우스 오른쪽 단추로 클릭한 다음 **디자인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-116">In the **Object Explorer**, right-click the table containing the check constraint and select **Design**.</span></span>  
  
2.  <span data-ttu-id="62583-117">**테이블 디자이너** 메뉴에서 **CHECK 제약 조건...** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-117">On the **Table Designer** menu, click **Check Constraints...**.</span></span>  
  
3.  <span data-ttu-id="62583-118">**CHECK 제약 조건** 대화 상자의 **선택한 CHECK 제약 조건**아래에서 편집하려는 제약 조건을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-118">In the **Check Constraints** dialog box, under **Selected Check Constraint**, select the constraint you wish to edit.</span></span>  
  
4.  <span data-ttu-id="62583-119">다음 표의 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="62583-120">수행할 작업</span><span class="sxs-lookup"><span data-stu-id="62583-120">To</span></span>|<span data-ttu-id="62583-121">수행할 단계</span><span class="sxs-lookup"><span data-stu-id="62583-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="62583-122">제약 조건 식 편집</span><span class="sxs-lookup"><span data-stu-id="62583-122">Edit the constraint expression</span></span>|<span data-ttu-id="62583-123">**식** 필드에 새 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-123">Type the new expression in the **Expression** field.</span></span>|  
    |<span data-ttu-id="62583-124">제약 조건 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="62583-124">Rename the constraint</span></span>|<span data-ttu-id="62583-125">**이름** 필드에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-125">Type a new name in the **Name** field.</span></span>|  
    |<span data-ttu-id="62583-126">기존 데이터에 제약 조건 적용</span><span class="sxs-lookup"><span data-stu-id="62583-126">Apply the constraint to existing data</span></span>|<span data-ttu-id="62583-127">**만들거나 활성화할 때 기존 데이터 검사** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-127">Select the **Check Existing Data on Creation or Enabling** option.</span></span>|  
    |<span data-ttu-id="62583-128">테이블에 새 데이터를 추가하거나 테이블에서 기존 데이터를 업데이트할 때 제약 조건 비활성화</span><span class="sxs-lookup"><span data-stu-id="62583-128">Disable the constraint when new data is added to the table or when existing data is updated in the table.</span></span>|<span data-ttu-id="62583-129">**INSERT 및 UPDATE에 대해 제약 조건 적용** 옵션을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-129">Clear the **Enforce Constraint for INSERTs and UPDATEs** option.</span></span>|  
    |<span data-ttu-id="62583-130">복제 에이전트가 테이블에서 데이터를 삽입하거나 업데이트할 때 제약 조건 비활성화.</span><span class="sxs-lookup"><span data-stu-id="62583-130">Disable the constraint when a replication agent inserts or updates data in your table.</span></span>|<span data-ttu-id="62583-131">**복제에 적용** 옵션을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-131">Clear the **Enforce For Replication** option.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="62583-132">일부 데이터베이스의 경우 CHECK 제약 조건의 기능이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="62583-132">Some databases have different functionality for check constraints.</span></span>  
  
5.  <span data-ttu-id="62583-133">**닫기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-133">Click **Close**.</span></span>  
  
6.  <span data-ttu-id="62583-134">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-134">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="62583-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="62583-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="62583-136">**CHECK 제약 조건을 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="62583-136">**To modify a check constraint**</span></span>  
  
 <span data-ttu-id="62583-137">`CHECK` 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]제약 조건을 수정하려면 먼저 기존 `CHECK` 제약 조건을 삭제하고 새로운 정의를 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="62583-137">To modify a `CHECK` constraint using [!INCLUDE[tsql](../../includes/tsql-md.md)], you must first delete the existing `CHECK` constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="62583-138">자세한 내용은 [Check 제약 조건 삭제](delete-check-constraints.md) 및 [Check 제약 조건 만들기](create-check-constraints.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="62583-138">For more information, see [Delete Check Constraints](delete-check-constraints.md) and [Create Check Constraints](create-check-constraints.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
