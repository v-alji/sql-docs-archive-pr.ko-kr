---
title: 테이블 업데이트 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 426c842b85d6404ba101b57a9b572107dbc76bb5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652486"
---
# <a name="update-table-dialog-box-visual-database-tools"></a><span data-ttu-id="7060c-102">테이블 업데이트 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="7060c-102">Update Table Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="7060c-103">이 대화 상자를 사용하면 업데이트할 테이블을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-103">This dialog box allows you to specify the table to be updated.</span></span>  
  
 <span data-ttu-id="7060c-104">이 대화 상자는 다이어그램 창에 두 개 이상의 테이블이 표시되어 있는 상태에서 쿼리 형식을 업데이트 쿼리로 변경하는 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-104">This dialog box appears if more than one table is displayed in the Diagram pane when you change a query's type to be an Update query.</span></span>  
  
 <span data-ttu-id="7060c-105">업데이트할 테이블을 선택 하 고 **확인**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-105">Select the table to update, and then choose **OK**.\</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7060c-106">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="7060c-107">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="7060c-108">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7060c-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7060c-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7060c-109">See Also</span></span>  
 [<span data-ttu-id="7060c-110">업데이트 쿼리 만들기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="7060c-110">Create Update Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
