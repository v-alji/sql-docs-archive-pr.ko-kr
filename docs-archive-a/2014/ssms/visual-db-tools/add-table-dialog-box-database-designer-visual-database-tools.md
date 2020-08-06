---
title: 테이블 추가 대화 상자(데이터베이스 디자이너)(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65555
- vdt.dlgbox.schema.addtable
ms.assetid: 3c0b1b30-795c-4240-91d6-890b8348014a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ae9d3763ef66c0a7580cc516169c2f273f36528
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648752"
---
# <a name="add-table-dialog-box-database-designer-visual-database-tools"></a><span data-ttu-id="35a48-102">테이블 추가 대화 상자(데이터베이스 디자이너)(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="35a48-102">Add Table Dialog Box (Database Designer) (Visual Database Tools)</span></span>
  <span data-ttu-id="35a48-103">이 대화 상자를 사용하면 데이터베이스 디자이너에서 테이블을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-103">Lets you add tables in Database Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35a48-104">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="35a48-105">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="35a48-106">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="35a48-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="35a48-107">UI element list</span></span>  
 <span data-ttu-id="35a48-108">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="35a48-108">**Refresh**</span></span>  
 <span data-ttu-id="35a48-109">데이터베이스의 현재 상태에 일치하도록 테이블 목록을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-109">Refreshed the list of tables to match the current state of the database.</span></span>  
  
 <span data-ttu-id="35a48-110">**추가**</span><span class="sxs-lookup"><span data-stu-id="35a48-110">**Add**</span></span>  
 <span data-ttu-id="35a48-111">선택한 하나 이상의 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-111">Adds the selected table or tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="35a48-112">여러 테이블을 다이어그램에 추가하려면 원하는 테이블을 모두 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-112">If you want to add several tables to the diagram, you can select them all before clicking **Add**.</span></span> <span data-ttu-id="35a48-113">또는 추가하려는 각 테이블을 두 번 클릭한 다음 **닫기** 를 클릭하고 작업을 마칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-113">Alternatively, you can double-click each table you want to add, then click **Close** when you are finished.</span></span>  
  
 <span data-ttu-id="35a48-114">**닫기**</span><span class="sxs-lookup"><span data-stu-id="35a48-114">**Close**</span></span>  
 <span data-ttu-id="35a48-115">테이블을 계속 추가하지 않고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="35a48-115">Closes the dialog box without adding further tables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a48-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="35a48-116">See Also</span></span>  
 [<span data-ttu-id="35a48-117">다이어그램에 테이블 추가&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="35a48-117">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
