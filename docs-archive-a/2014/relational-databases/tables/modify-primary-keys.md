---
title: 기본 키 수정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- modifying primary keys
- primary keys [SQL Server], modifying
ms.assetid: 8e2a15ba-1cd1-4408-b860-16c3ee37d635
author: stevestein
ms.author: sstein
ms.openlocfilehash: f24deeac45491f9097d90ee0407464f928a0713b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638603"
---
# <a name="modify-primary-keys"></a><span data-ttu-id="bf589-102">기본 키 수정</span><span class="sxs-lookup"><span data-stu-id="bf589-102">Modify Primary Keys</span></span>
  <span data-ttu-id="bf589-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 기본 키를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-103">You can modify a primary key in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="bf589-104">열 순서, 인덱스 이름, 클러스터형 옵션 또는 채우기 비율을 변경하여 테이블의 기본 키를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-104">You can modify the primary key of a table by changing the column order, index name, clustered option, or fill factor.</span></span>  
  
 <span data-ttu-id="bf589-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="bf589-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="bf589-106">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="bf589-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="bf589-107">보안</span><span class="sxs-lookup"><span data-stu-id="bf589-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="bf589-108">**기본 키를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="bf589-108">**To modify a primary key, using:**</span></span>  
  
     [<span data-ttu-id="bf589-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="bf589-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="bf589-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="bf589-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="bf589-111">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="bf589-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="bf589-112">보안</span><span class="sxs-lookup"><span data-stu-id="bf589-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="bf589-113">권한</span><span class="sxs-lookup"><span data-stu-id="bf589-113">Permissions</span></span>  
 <span data-ttu-id="bf589-114">테이블에 대한 ALTER 사용 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-114">Requires ALTER permission on the table.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="bf589-115">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="bf589-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-modify-a-primary-key"></a><span data-ttu-id="bf589-116">기본 키를 수정하려면</span><span class="sxs-lookup"><span data-stu-id="bf589-116">To modify a primary key</span></span>  
  
1.  <span data-ttu-id="bf589-117">수정하려는 기본 키가 포함된 테이블에 대한 테이블 디자이너를 열고 테이블 디자이너를 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **인덱스/키** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-117">Open the Table Designer for the table whose primary key you want to modify, right-click in the Table Designer, and choose **Indexes/Keys** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="bf589-118">**인덱스/키** 대화 상자의 **선택한 기본/고유 키 및 인덱스** 목록에서 기본 키 인덱스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-118">In the **Indexes/Keys** dialog box, select the primary key index from the **Selected Primary/Unique Key or Index** list.</span></span>  
  
3.  <span data-ttu-id="bf589-119">다음 표의 동작을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-119">Complete an action from the following table:</span></span>  
  
    |<span data-ttu-id="bf589-120">수행할 작업</span><span class="sxs-lookup"><span data-stu-id="bf589-120">To</span></span>|<span data-ttu-id="bf589-121">수행할 단계</span><span class="sxs-lookup"><span data-stu-id="bf589-121">Follow these steps</span></span>|  
    |--------|------------------------|  
    |<span data-ttu-id="bf589-122">기본 키 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="bf589-122">Rename the primary key</span></span>|<span data-ttu-id="bf589-123">**이름** 상자에 새 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-123">Type a new name in the **Name** box.</span></span> <span data-ttu-id="bf589-124">새 이름은 **선택한 기본/고유 키 또는 인덱스** 목록의 다른 이름과 중복되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-124">Make sure that your new name does not duplicate a name in the **Selected Primary/Unique Key or Index** list.</span></span>|  
    |<span data-ttu-id="bf589-125">클러스터형 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="bf589-125">Set the clustered option</span></span>|<span data-ttu-id="bf589-126">기본 키에 대한 클러스터형 인덱스를 만들려면 **CLUSTERED로 만들기**를 선택하고 드롭다운 목록 상자에서 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-126">To create a clustered index for the primary key, select **Create as CLUSTERED**, and select the option from the drop-down list box.</span></span> <span data-ttu-id="bf589-127">클러스터형 인덱스는 테이블마다 하나씩만 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-127">Only one clustered index can exist per table.</span></span> <span data-ttu-id="bf589-128">인덱스에 이 옵션을 사용할 수 없는 경우 기존의 클러스터형 인덱스에 대해 이 설정을 먼저 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-128">If this option is not available for your index, you must first clear this setting on the existing clustered index.</span></span><br /><br /> <span data-ttu-id="bf589-129">이 옵션을 선택하지 않으면 고유 비클러스터형 인덱스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-129">If this option is not selected, a unique nonclustered index is created.</span></span>|  
    |<span data-ttu-id="bf589-130">채우기 비율 정의</span><span class="sxs-lookup"><span data-stu-id="bf589-130">Define a fill factor</span></span>|<span data-ttu-id="bf589-131">**채우기 사양** 범주를 확장하고 0에서 100 사이의 정수를 **채우기 비율** 상자에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-131">Expand the **Fill Specification** category and type an integer from 0 to 100 in the **Fill factor** box.</span></span> <span data-ttu-id="bf589-132">채우기 비율과 그 사용 방법은 [인덱스의 채우기 비율 지정](../indexes/specify-fill-factor-for-an-index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf589-132">For more information about fill factors and their uses, see [Specify Fill Factor for an Index](../indexes/specify-fill-factor-for-an-index.md).</span></span>|  
    |<span data-ttu-id="bf589-133">열 순서 변경</span><span class="sxs-lookup"><span data-stu-id="bf589-133">Change the column order</span></span>|<span data-ttu-id="bf589-134">**열**을 선택한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-134">Select **Columns**, and then click the ellipses **(...)** to the right of the property.</span></span> <span data-ttu-id="bf589-135">**인덱스 열** 대화 상자에서 기본 키의 열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-135">In the  **Index Columns** dialog box, remove the columns from the primary key.</span></span> <span data-ttu-id="bf589-136">그런 다음 이 열을 원하는 순서로 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-136">Then add the columns back in the order you want.</span></span> <span data-ttu-id="bf589-137">키에서 열을 제거하려면 **열** 이름 목록에서 열 이름을 제거하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-137">To remove a column from the key, simply remove the column name from the **Column** name list.</span></span>|  
  
4.  <span data-ttu-id="bf589-138">**파일** 메뉴에서 _테이블 이름_**저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-138">On the **File** menu, click **Save**_table name_.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="bf589-139">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="bf589-139">Using Transact-SQL</span></span>  
 <span data-ttu-id="bf589-140">**기본 키를 수정하려면**</span><span class="sxs-lookup"><span data-stu-id="bf589-140">**To modify a primary key**</span></span>  
  
 <span data-ttu-id="bf589-141">Transact-SQL을 사용하여 PRIMARY KEY 제약 조건을 수정하려면 먼저 기존 PRIMARY KEY 제약 조건을 삭제하고 새로운 정의를 사용하여 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf589-141">To modify a PRIMARY KEY constraint using Transact-SQL, you must first delete the existing PRIMARY KEY constraint and then re-create it with the new definition.</span></span> <span data-ttu-id="bf589-142">자세한 내용은 [Delete Primary Keys](delete-primary-keys.md) 및 [Create Primary Keys](create-primary-keys.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf589-142">For more information, see [Delete Primary Keys](delete-primary-keys.md) and [Create Primary Keys](create-primary-keys.md).</span></span>  
  
###  <a name="TsqlExample"></a>  
