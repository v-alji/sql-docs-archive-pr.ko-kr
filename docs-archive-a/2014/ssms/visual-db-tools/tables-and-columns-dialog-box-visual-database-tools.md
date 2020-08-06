---
title: 테이블 및 열 대화 상자(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28e0c52b74413a3a5a4122412c6028b34e974b09
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659763"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a><span data-ttu-id="204da-102">테이블 및 열 대화 상자(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="204da-102">Tables and Columns Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="204da-103">이 대화 상자를 사용하면 한 테이블의 기본 키를 다른 테이블의 외래 키에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="204da-103">Use this dialog box to map a primary key in one table to a foreign key in another.</span></span> <span data-ttu-id="204da-104">이 대화 상자를 열려면 **테이블 디자이너** 메뉴에서 **관계**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-104">To access this dialog box, from the **Table Designer** menu, click **Relationships**.</span></span> <span data-ttu-id="204da-105">**외래 키 관계** 대화 상자에서 **테이블 및 열 사양** 필드를 클릭한 다음, 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-105">In the **Foreign Key Relationships** dialog box, click the **Tables and Columns Specification** field, and then click the ellipses **(...)** to the right of the property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="204da-106">테이블이 복제용으로 게시된 경우 Transact-SQL 문 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 또는 SMO(SQL Server 관리 개체)를 사용하여 스키마를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-106">If the table is published for replication, you must make schema changes using the Transact-SQL statement [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) or SQL Server Management Objects (SMO).</span></span> <span data-ttu-id="204da-107">테이블 디자이너 또는 데이터베이스 다이어그램 디자이너를 사용하여 스키마를 변경하면 테이블 삭제 및 재생성이 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="204da-107">When schema changes are made using the Table Designer or the Database Diagram Designer, it attempts to drop and recreate the table.</span></span> <span data-ttu-id="204da-108">게시된 개체를 삭제할 수 없으므로 스키마가 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="204da-108">You cannot drop published objects, therefore the schema change will fail.</span></span>  
  
## <a name="options"></a><span data-ttu-id="204da-109">옵션</span><span class="sxs-lookup"><span data-stu-id="204da-109">Options</span></span>  
 <span data-ttu-id="204da-110">**관계 이름**</span><span class="sxs-lookup"><span data-stu-id="204da-110">**Relationship name**</span></span>  
 <span data-ttu-id="204da-111">관계의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-111">Shows the name of the relationship.</span></span>  
  
 <span data-ttu-id="204da-112">**기본 키 테이블**</span><span class="sxs-lookup"><span data-stu-id="204da-112">**Primary Key Table**</span></span>  
 <span data-ttu-id="204da-113">데이터베이스의 테이블 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="204da-113">Lists the tables in the database.</span></span> <span data-ttu-id="204da-114">관계의 기본 키 쪽에 사용할 테이블을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="204da-114">Choose the table that will be on the primary-key side of the relationship.</span></span>  
  
 <span data-ttu-id="204da-115">**외래 키 테이블**</span><span class="sxs-lookup"><span data-stu-id="204da-115">**Foreign Key Table**</span></span>  
 <span data-ttu-id="204da-116">관계의 외래 키 쪽 테이블을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-116">Shows the table on the foreign key side of the relationship.</span></span> <span data-ttu-id="204da-117">이 테이블은 테이블 디자이너에 현재 선택되어 있는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="204da-117">This is the table currently selected in Table Designer.</span></span>  
  
 <span data-ttu-id="204da-118">**기본 키 테이블 아래의 표**</span><span class="sxs-lookup"><span data-stu-id="204da-118">**Grid beneath Primary Key Table**</span></span>  
 <span data-ttu-id="204da-119">**기본 키 테이블** 목록에서 선택한 테이블의 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="204da-119">List the columns of the table selected in the **Primary Key Table** list.</span></span> <span data-ttu-id="204da-120">해당 테이블의 기본 키로 사용되는 열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="204da-120">Enter the columns contributing to that table's primary key.</span></span>  
  
 <span data-ttu-id="204da-121">**외래 키 테이블 아래의 표**</span><span class="sxs-lookup"><span data-stu-id="204da-121">**Grid beneath Foreign Key Table**</span></span>  
 <span data-ttu-id="204da-122">**외래 키 테이블** 목록에서 선택한 테이블의 열이 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="204da-122">List the columns of the table selected in the **Foreign Key Table** list.</span></span> <span data-ttu-id="204da-123">기본 키 열에 상응하는 외래 키 테이블의 외래 키 열을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="204da-123">Enter the foreign-key column of the foreign-key table that corresponds to the primary key column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="204da-124">외래 키로 선택한 열의 데이터 형식은 상응하는 기본 키 열의 데이터 형식과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-124">The columns you choose for the foreign key must have the same data type of the primary columns they correspond to.</span></span> <span data-ttu-id="204da-125">각 키 열의 수는 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-125">There must be an equal number of columns in each of the keys.</span></span> <span data-ttu-id="204da-126">예를 들어 관계의 기본 키 쪽에 있는 테이블의 기본 키가 두 개의 열로 구성되어 있는 경우 이러한 열을 각각 관계의 외래 키 쪽에 있는 테이블의 열에 일치시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="204da-126">For example, if the primary key of the table on the primary side of the relationship is made up of two columns, you will need to match each of those columns with a column in the table for the foreign key side of the relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="204da-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="204da-127">See Also</span></span>  
 [<span data-ttu-id="204da-128">외래 키 관계 만들기</span><span class="sxs-lookup"><span data-stu-id="204da-128">Create Foreign Key Relationships</span></span>](../../relational-databases/tables/create-foreign-key-relationships.md)  
  
  
