---
title: 여러 사용자가 변경한 내용 조정(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 337d505fce474a33301c18313fe6137f6bc0ec1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729972"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a><span data-ttu-id="3b469-102">여러 사용자가 변경한 내용 조정(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="3b469-102">Reconcile Changes Made by Multiple Users (Visual Database Tools)</span></span>
  <span data-ttu-id="3b469-103">다중 사용자 환경에서는 동일한 개체를 여러 사용자가 동시에 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-103">In a multiuser environment, changes can be made on the same object by multiple users at once.</span></span> <span data-ttu-id="3b469-104">이러한 상황은 테이블 또는 데이터베이스 다이어그램 디자이너에서 개체 구조에 대한 작업을 수행 중일 때 발생할 수도 있고, 쿼리 및 뷰 디자이너의 결과 창에 반환된 결과의 값에 대해 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-104">This can happen when you're working on the structure of the object in the Table or Database Diagram designers or it can happen to values in the results returned in the Query and View designer's Results pane.</span></span> <span data-ttu-id="3b469-105">이 경우 충돌이 발생할 수 있으므로 적절한 해결책이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-105">This can cause conflicts that you'll want to resolve.</span></span>  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a><span data-ttu-id="3b469-106">테이블 또는 데이터베이스 다이어그램 디자이너의 충돌</span><span class="sxs-lookup"><span data-stu-id="3b469-106">Conflicts in the Table or Database Diagram Designers</span></span>  
 <span data-ttu-id="3b469-107">예를 들어, 테이블 디자이너에서 현재 사용자가 작업 중인 것과 동일한 테이블이나 관련 테이블을 다른 사용자가 삭제하거나 이름을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-107">For example, another user might delete or rename a table while you are working with the same or a related table in Table Designer.</span></span> <span data-ttu-id="3b469-108">테이블을 저장하려고 하면 [데이터베이스 변경 감지 대화 상자&#40;Visual Database Tools&#41;](visual-database-tools.md) 가 표시되어 사용자가 테이블을 연 이후 데이터베이스가 업데이트되었음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-108">When you attempt to save your table, the [Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) notifies you that the database has been updated since you opened the table.</span></span>  
  
 <span data-ttu-id="3b469-109">또한 이 대화 상자에는 테이블을 저장하는 경우 영향을 받는 데이터베이스 개체의 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-109">This dialog box also displays a list of database objects that will be affected as a result of saving your table.</span></span> <span data-ttu-id="3b469-110">이 때 사용자는 다음 동작 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-110">At this point, you can take one of these actions:</span></span>  
  
-   <span data-ttu-id="3b469-111">테이블을 저장하고 목록의 모든 변경 내용으로 데이터베이스를 업데이트하려면 **예** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-111">Choose **Yes** to save your table and update the database with all the changes in the list.</span></span>  
  
     <span data-ttu-id="3b469-112">이 동작은 동일한 데이터베이스 개체를 공유하는 다른 테이블에도 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-112">This action could affect tables that share the same database objects.</span></span> <span data-ttu-id="3b469-113">예를 들어 `au`테이블의`id` _ `titleauthors` 열을 편집하는 동안 다른 사용자가 `authors` 열을 통해 `titleauthors` 테이블과 연결되는 `au`\_`id` 테이블에 대한 작업을 진행하는 경우</span><span class="sxs-lookup"><span data-stu-id="3b469-113">For example, suppose you edit the `au`_`id` column in the `titleauthors` table while another user is working on the `authors` table which is related to the `titleauthors` table by the `au`\_`id` column.</span></span> <span data-ttu-id="3b469-114">테이블을 저장하면 다른 사용자의 테이블에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-114">Saving your table will affect the other user's table.</span></span> <span data-ttu-id="3b469-115">마찬가지로 다른 사용자가 `qty` 테이블의 `sales` 열에 CHECK 제약 조건을 정의한 경우,</span><span class="sxs-lookup"><span data-stu-id="3b469-115">Similarly, suppose that another user defined a check constraint for the `qty` column in the `sales` table.</span></span> <span data-ttu-id="3b469-116">`qty` 열을 삭제하고 `sales` 테이블을 저장하면 다른 사용자의 CHECK 제약 조건도 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-116">If you delete the `qty` column and save the `sales` table, the other user's check constraint will be affected.</span></span>  
  
-   <span data-ttu-id="3b469-117">저장 동작을 취소하려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-117">Choose **No** to cancel the save action.</span></span>  
  
     <span data-ttu-id="3b469-118">그런 다음 테이블을 저장하지 않고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-118">You can then close the table without saving it.</span></span> <span data-ttu-id="3b469-119">테이블을 다시 열면 데이터베이스의 최신 데이터가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-119">When you reopen the table it will match what is in the database.</span></span>  
  
-   <span data-ttu-id="3b469-120">변경 내용 목록을 저장하려면 **텍스트 파일 저장** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-120">Choose **Save Text File** to save a list of the changes.</span></span>  
  
     <span data-ttu-id="3b469-121">**데이터베이스 변경 감지** 대화 상자에 표시된 데이터베이스 변경 목록을 텍스트 파일에 저장하여 다른 사용자의 변경 원인을 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-121">You can save the list of database changes shown in the **Database Changes Detected** dialog box to a text file so that you can investigate the cause of other users' changes.</span></span> <span data-ttu-id="3b469-122">예를 들어, 사용자가 삭제하려고 표시한 테이블을 다른 사용자가 편집한 경우 데이터베이스를 업데이트하기 전에 테이블을 삭제해야 할지 여부를 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-122">For example, if another user edited a table that you marked for deletion, you may want to research whether the table should be deleted before updating the database.</span></span>  
  
## <a name="conflicts-in-the-query-and-view-designer"></a><span data-ttu-id="3b469-123">쿼리 및 뷰 디자이너의 충돌</span><span class="sxs-lookup"><span data-stu-id="3b469-123">Conflicts in the Query and View Designer</span></span>  
 <span data-ttu-id="3b469-124">쿼리를 실행하거나 뷰의 결과를 반환하면 [결과 창](results-pane-visual-database-tools.md)에 데이터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-124">If you run a query or return the results of a view, the data is shown in the [Results Pane](results-pane-visual-database-tools.md).</span></span> <span data-ttu-id="3b469-125">여러 사용자가 동일한 데이터 집합에 대해 동시에 작업을 수행하는 경우 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-125">Multiple users can work on the same set of data at the same time, which can cause conflicts.</span></span>  
  
 <span data-ttu-id="3b469-126">예를 들어, 현재 사용자와 동료 사용자가 각각 `titleauthors` 테이블의 모든 데이터를 표시하도록 쿼리를 실행하는 경우를 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-126">For example, lets say you and a colleague each run a query to show all the data in the `titleauthors` table.</span></span> <span data-ttu-id="3b469-127">반환된 첫 번째 레코드의 첫 번째 이름을 동료 사용자가 Barb에서 Barbara로 변경한 경우,</span><span class="sxs-lookup"><span data-stu-id="3b469-127">Your colleague changes the first name in the first record returned from Barb to Barbara.</span></span> <span data-ttu-id="3b469-128">이 시점에서 데이터베이스의 해당 필드에 있는 데이터는 Barbara이지만 현재 사용자의 쿼리 결과에는 여전히 Barb가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-128">At this point the database has Barbara in that field, while your result set still shows Barb.</span></span> <span data-ttu-id="3b469-129">뒤늦게 현재 사용자가 Barbara를 입력하고 다른 행으로 포커스를 옮기면</span><span class="sxs-lookup"><span data-stu-id="3b469-129">Now you type in Barbara and click off of the row.</span></span> <span data-ttu-id="3b469-130">충돌 문제를 어떻게 해결할지 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-130">You will receive a message asking you how you want to resolve the conflict.</span></span>  
  
-   <span data-ttu-id="3b469-131">변경 내용으로 데이터베이스를 업데이트하려면 **예** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-131">Click **Yes** to update the database with your changes.</span></span>  
  
     <span data-ttu-id="3b469-132">이렇게 하면 다른 사용자가 변경한 내용이 무시되고 현재 사용자의 변경 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-132">This will override your colleague's changes.</span></span>  
  
-   <span data-ttu-id="3b469-133">결과 집합을 데이터베이스의 현재 상태로 업데이트하려면 **아니요** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-133">Click **No** to have your result set updated to what's currently in the database.</span></span>  
  
     <span data-ttu-id="3b469-134">이렇게 하면 현재 사용자의 변경 내용이 무시되고 다른 사용자가 변경한 내용이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-134">This will override your changes with those of your colleague's.</span></span>  
  
-   <span data-ttu-id="3b469-135">충돌을 해결하지 않은 상태로 계속 편집하려면 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-135">Click **Cancel** to continue to edit without resolving the conflict.</span></span>  
  
     <span data-ttu-id="3b469-136">이 경우 변경 내용을 데이터베이스에 커밋할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b469-136">In this case you will not be able to commit your changes to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b469-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b469-137">See Also</span></span>  
 [<span data-ttu-id="3b469-138">데이터베이스 변경 감지 대화 상자&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="3b469-138">Database Changes Detected Dialog Box &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
