---
title: 데이터베이스 다이어그램에서 테이블 작업(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- database diagrams [SQL Server], tables
- Table Designer, database diagrams
- tables [SQL Server], database diagrams
- database diagrams [SQL Server], Table Designer
ms.assetid: ee2c5d84-22bf-4597-ac70-a27ed8cc94f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f648cd5fd08ed47c6670491ad5b7f3d75b7ead47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652487"
---
# <a name="work-with-tables-in-database-diagram-visual-database-tools"></a><span data-ttu-id="f368d-102">데이터베이스 다이어그램에서 테이블 작업(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="f368d-102">Work with Tables in Database Diagram (Visual Database Tools)</span></span>
  <span data-ttu-id="f368d-103">테이블 디자이너나 데이터베이스 다이어그램 디자이너에서 데이터베이스 테이블을 만들고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f368d-103">You can modify and create database tables in either Table Designer or Database Diagram Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f368d-104">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f368d-104">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="f368d-105">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="f368d-105">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="f368d-106">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f368d-106">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f368d-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f368d-107">In This Section</span></span>  
 [<span data-ttu-id="f368d-108">다이어그램에 테이블 추가&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-108">Add Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-109">다이어그램에 관련 테이블 추가&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-109">Add Related Tables to Diagrams &#40;Visual Database Tools&#41;</span></span>](add-related-tables-to-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-110">다이어그램에서 선택한 테이블 저장&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-110">Save Selected Tables on a Diagram &#40;Visual Database Tools&#41;</span></span>](save-selected-tables-on-a-diagram-visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-111">한 데이터베이스 다이어그램에서 다른 다이어그램으로 테이블 복사&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-111">Copy Tables from One Database Diagrams to Another &#40;Visual Database Tools&#41;</span></span>](copy-tables-from-one-database-diagrams-to-another-visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-112">데이터베이스 다이어그램에서 테이블 제거&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-112">Remove Tables from Database Diagrams &#40;Visual Database Tools&#41;</span></span>](remove-tables-from-database-diagrams-visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-113">다 대 다 관계 매핑&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-113">Map Many-to-Many Relationships &#40;Visual Database Tools&#41;</span></span>](map-many-to-many-relationships-visual-database-tools.md)  
  
 [<span data-ttu-id="f368d-114">반사 관계 그리기&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-114">Draw Reflexive Relationships &#40;Visual Database Tools&#41;</span></span>](draw-reflexive-relationships-visual-database-tools.md)  
  
## <a name="reference"></a><span data-ttu-id="f368d-115">참조</span><span class="sxs-lookup"><span data-stu-id="f368d-115">Reference</span></span>  
 [<span data-ttu-id="f368d-116">테이블 추가 대화 상자&#40;데이터베이스 디자이너&#41;&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="f368d-116">Add Table Dialog Box &#40;Database Designer&#41; &#40;Visual Database Tools&#41;</span></span>](add-table-dialog-box-database-designer-visual-database-tools.md)  
  
## <a name="related-sections"></a><span data-ttu-id="f368d-117">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="f368d-117">Related Sections</span></span>  
  
