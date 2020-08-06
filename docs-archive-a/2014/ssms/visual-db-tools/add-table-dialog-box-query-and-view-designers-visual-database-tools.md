---
title: 테이블 추가 대화 상자 (쿼리 및 뷰 디자이너) (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8d7bf30cbdd37927735c36f184208a1ded957763
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648751"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a><span data-ttu-id="17b2a-102">테이블 추가 대화 상자(쿼리 및 뷰 디자이너)(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="17b2a-102">Add Table Dialog Box (Query and View Designers) (Visual Database Tools)</span></span>
  <span data-ttu-id="17b2a-103">이 대화 상자를 사용하여 쿼리나 뷰에 테이블, 뷰, 사용자 정의 함수 또는 동의어를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-103">This dialog box lets you add tables, views, user-defined functions, or synonyms to a query or view.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17b2a-104">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="17b2a-105">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="17b2a-106">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="17b2a-107">옵션</span><span class="sxs-lookup"><span data-stu-id="17b2a-107">Options</span></span>  
 <span data-ttu-id="17b2a-108">**테이블**</span><span class="sxs-lookup"><span data-stu-id="17b2a-108">**Tables**</span></span>  
 <span data-ttu-id="17b2a-109">**다이어그램** 창에 추가할 수 있는 테이블을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-109">Lists the tables you can add to the **Diagram** pane.</span></span> <span data-ttu-id="17b2a-110">테이블을 추가하려면 테이블을 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-110">To add a table, select it and click **Add**.</span></span> <span data-ttu-id="17b2a-111">여러 테이블을 한번에 추가하려면 원하는 테이블을 모두 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-111">To add several tables at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="17b2a-112">**뷰**</span><span class="sxs-lookup"><span data-stu-id="17b2a-112">**Views**</span></span>  
 <span data-ttu-id="17b2a-113">**다이어그램** 창에 추가할 수 있는 뷰를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-113">Lists the views you can add to the **Diagram** pane.</span></span> <span data-ttu-id="17b2a-114">뷰를 추가하려면 뷰를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-114">To add a view, select it and click **Add**.</span></span> <span data-ttu-id="17b2a-115">여러 뷰를 한번에 추가하려면 원하는 뷰를 모두 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-115">To add several views at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="17b2a-116">**함수**</span><span class="sxs-lookup"><span data-stu-id="17b2a-116">**Functions**</span></span>  
 <span data-ttu-id="17b2a-117">**다이어그램** 창에 추가할 수 있는 사용자 정의 함수를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-117">Lists the user-defined functions you can add to the **Diagram** pane.</span></span> <span data-ttu-id="17b2a-118">함수를 추가하려면 함수를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-118">To add a function, select it and click **Add**.</span></span> <span data-ttu-id="17b2a-119">여러 함수를 한번에 추가하려면 원하는 함수를 모두 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-119">To add several functions at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="17b2a-120">**동의어**</span><span class="sxs-lookup"><span data-stu-id="17b2a-120">**Synonyms**</span></span>  
 <span data-ttu-id="17b2a-121">**다이어그램** 창에 추가할 수 있는 동의어를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-121">Lists the synonyms you can add to the **Diagram** pane.</span></span> <span data-ttu-id="17b2a-122">동의어를 추가하려면 동의어를 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-122">To add a synonym, select it and click **Add**.</span></span> <span data-ttu-id="17b2a-123">여러 동의어를 한번에 추가하려면 원하는 동의어를 모두 선택하고 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-123">To add several synonyms at once, select them and click **Add**.</span></span>  
  
 <span data-ttu-id="17b2a-124">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="17b2a-124">**Refresh**</span></span>  
 <span data-ttu-id="17b2a-125">목록을 마지막으로 가져온 후에 데이터베이스에서 변경된 내용을 모두 포함하도록 목록을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-125">Update the list to include any changes made to the database since the list was last retrieved.</span></span>  
  
 <span data-ttu-id="17b2a-126">**추가**</span><span class="sxs-lookup"><span data-stu-id="17b2a-126">**Add**</span></span>  
 <span data-ttu-id="17b2a-127">선택한 하나 이상의 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17b2a-127">Add the selected item or items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b2a-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17b2a-128">See Also</span></span>  
 [<span data-ttu-id="17b2a-129">쿼리 및 뷰 디자인 방법 도움말 항목&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="17b2a-129">Design Queries and Views How-to Topics &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
