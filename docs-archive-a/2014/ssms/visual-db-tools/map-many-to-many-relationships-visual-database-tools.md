---
title: 다 대 다 관계 매핑(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- relationships [SQL Server], many-to-many
- junction tables [SQL Server]
- many-to-many relationships [SQL Server]
- mapping many-to-many relationships [SQL Server]
- database diagrams [SQL Server], relationships
ms.assetid: 2977cf92-98b5-48b2-b0fd-8fbc7040f2b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: cbcbdbdf8d8371baa2a817e43b831535723be7ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660266"
---
# <a name="map-many-to-many-relationships-visual-database-tools"></a><span data-ttu-id="fc119-102">다 대 다 관계 매핑(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="fc119-102">Map Many-to-Many Relationships (Visual Database Tools)</span></span>
  <span data-ttu-id="fc119-103">다 대 다 관계를 사용하면 한 테이블의 각 행을 다른 테이블의 여러 행에 연결하거나 그 반대로 행을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-103">Many-to-many relationships let you relate each row in one table to many rows in another table, and vice versa.</span></span> <span data-ttu-id="fc119-104">예를 들어, 각 작가를 해당 작가의 모든 저서에 연결하고 각 도서를 모든 해당 작가에 연결하도록 `authors` 테이블과 `titles` 테이블 사이에 다 대 다 관계를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-104">For example, you could create a many-to-many relationship between the `authors` table and the `titles` table to match each author to all of his or her books and to match each book to all of its authors.</span></span> <span data-ttu-id="fc119-105">각 테이블에서 일 대 다 관계를 만드는 것만으로는 모든 도서가 한 명의 작가에게만 연결되거나 모든 작가가 한 권의 책만 쓴 것으로 잘못 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-105">Creating a one-to-many relationship from either table would incorrectly indicate that every book can have only one author, or that every author can write only one book.</span></span>  
  
 <span data-ttu-id="fc119-106">테이블 사이의 다 대 다 관계는 병합 테이블을 통해 데이터베이스에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-106">Many-to-many relationships between tables are accommodated in databases by means of junction tables.</span></span> <span data-ttu-id="fc119-107">병합 테이블에는 연결하려는 두 테이블의 기본 키 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-107">A junction table contains the primary key columns of the two tables you want to relate.</span></span> <span data-ttu-id="fc119-108">병합 테이블의 열에 일치하도록 이러한 두 테이블 각각의 기본 키 열에서 관계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-108">You then create a relationship from the primary key columns of each of those two tables to the matching columns in the junction table.</span></span> <span data-ttu-id="fc119-109">pubs 데이터베이스에서 병합 테이블은 `titleauthor` 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-109">In the pubs database, the `titleauthor` table is a junction table.</span></span>  
  
### <a name="to-create-a-many-to-many-relationship-between-tables"></a><span data-ttu-id="fc119-110">테이블 사이에 다 대 다 관계를 만들려면</span><span class="sxs-lookup"><span data-stu-id="fc119-110">To create a many-to-many relationship between tables</span></span>  
  
1.  <span data-ttu-id="fc119-111">데이터베이스 다이어그램에서 다 대 다 관계를 만들려는 두 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-111">In your database diagram, add the tables that you want to create a many-to-many relationship between.</span></span>  
  
2.  <span data-ttu-id="fc119-112">다이어그램을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **새 테이블** 을 선택하여 세 번째 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-112">Create a third table by right-clicking the diagram and choosing **New Table** from the shortcut menu.</span></span> <span data-ttu-id="fc119-113">이 테이블이 병합 테이블로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-113">This will become the junction table.</span></span>  
  
3.  <span data-ttu-id="fc119-114">**이름 선택** 대화 상자에서 시스템 할당 테이블 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-114">In the **Choose Name** dialog box, change the system-assigned table name.</span></span> <span data-ttu-id="fc119-115">예를 들어, `titles` 테이블과 `authors` 테이블 사이의 병합 테이블 이름으로 `titleauthors`를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-115">For example, the junction table between the `titles` table and the `authors` table is now named `titleauthors`.</span></span>  
  
4.  <span data-ttu-id="fc119-116">다른 두 테이블 각각의 기본 키 열을 병합 테이블에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-116">Copy the primary key columns from each of the other two tables to the junction table.</span></span> <span data-ttu-id="fc119-117">일반적인 테이블 작업의 경우와 마찬가지로 다른 열을 이 테이블에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-117">You can add other columns to this table, just as you can to any other table.</span></span>  
  
5.  <span data-ttu-id="fc119-118">병합 테이블에서 다른 두 테이블의 기본 키 열이 모두 포함되도록 기본 키를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-118">In the junction table, set the primary key to include all the primary key columns from the other two tables.</span></span> <span data-ttu-id="fc119-119">자세한 내용은 [기본 키 만들기](../../relational-databases/tables/create-primary-keys.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc119-119">For details, see [Create Primary Keys](../../relational-databases/tables/create-primary-keys.md).</span></span>  
  
6.  <span data-ttu-id="fc119-120">두 개의 각 기본 테이블과 병합 테이블 사이에 일 대 다 관계를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-120">Define a one-to-many relationship between each of the two primary tables and the junction table.</span></span> <span data-ttu-id="fc119-121">병합 테이블은 작성된 두 관계 모두에서 "다" 쪽에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-121">The junction table should be at the "many" side of both of the relationships you create.</span></span> <span data-ttu-id="fc119-122">자세한 내용은 [외래 키 관계 만들기](../../relational-databases/tables/create-foreign-key-relationships.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc119-122">For details, see [Create Foreign Key Relationships](../../relational-databases/tables/create-foreign-key-relationships.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fc119-123">데이터베이스 다이어그램에서 병합 테이블을 만들어도 관련 테이블의 데이터가 병합 테이블에 삽입되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fc119-123">The creation of a junction table in a database diagram does not insert data from the related tables into the junction table.</span></span> <span data-ttu-id="fc119-124">테이블에 데이터를 삽입하는 방법에 대한 자세한 내용은 [결과 삽입 쿼리 만들기&#40;Visual Database Tools&#41;](visual-database-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fc119-124">For information about inserting data into a table, see [Create Insert Results Queries &#40;Visual Database Tools&#41;](visual-database-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc119-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc119-125">See Also</span></span>  
 [<span data-ttu-id="fc119-126">데이터베이스 다이어그램 작업&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="fc119-126">Work with Database Diagrams &#40;Visual Database Tools&#41;</span></span>](work-with-database-diagrams-visual-database-tools.md)  
  
  
