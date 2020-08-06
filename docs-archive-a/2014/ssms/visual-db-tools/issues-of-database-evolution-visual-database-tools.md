---
title: 데이터베이스의 단계적 개발 문제(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80daa694cd015a83657368902b07da254e6196ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740656"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a><span data-ttu-id="b56ab-102">데이터베이스의 단계적 개발 문제(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="b56ab-102">Issues of Database Evolution (Visual Database Tools)</span></span>
  <span data-ttu-id="b56ab-103">배포된 데이터베이스의 구조를 변경하는 경우 변경 내용이 기존 데이터 및 데이터베이스 구조와 호환되도록 각별히 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-103">If you change the structure of a deployed database, you must take special care that your alteration is compatible with the existing data and database structure.</span></span> <span data-ttu-id="b56ab-104">다음과 같이 수정한 경우 특별한 단계를 수행해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-104">You might need to take special steps when you make the following modifications:</span></span>  
  
-   <span data-ttu-id="b56ab-105">**제약 조건 추가** 제약 조건을 추가하는 경우 데이터베이스에 제약 조건을 만족하지 않는 데이터가 이미 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-105">**Adding a Constraint** If you add a constraint, the database might already contain data that does not satisfy it.</span></span> <span data-ttu-id="b56ab-106">새 제약 조건을 저장하려고 하면 [저장 후 알림 대화 상자&#40;Visual Database Tools&#41;](visual-database-tools.md)가 표시되어 데이터베이스 서버에서 제약 조건을 만들 수 없음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-106">When you try to save the new constraint, the [Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not create the constraint.</span></span> <span data-ttu-id="b56ab-107">데이터베이스에서 새 제약 조건을 강제로 허용하도록 하려면 **만들 때 기존 데이터 검사** 확인란을 선택 취소하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-107">To force the database to accept the new constraint, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="b56ab-108">**관계 추가** 관계를 추가하는 경우 기본 키 테이블에 해당 행이 없는 외래 키 테이블 행이 이미 데이터베이스에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-108">**Adding a Relationship** If you add a relationship, the database might already contain rows of the foreign-key table that do not have corresponding rows in the primary-key table.</span></span> <span data-ttu-id="b56ab-109">즉, 기존 데이터가 참조 무결성을 충족하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-109">That is, the existing data might not satisfy referential integrity.</span></span> <span data-ttu-id="b56ab-110">새 관계를 저장하려고 하면 [저장 후 알림 대화 상자&#40;Visual Database Tools&#41;](visual-database-tools.md)가 표시되어 데이터베이스 서버에서 수정된 외래 키 테이블을 저장할 수 없음을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-110">When you try to save the new relationship, the[Post-Save Notifications Dialog Box &#40;Visual Database Tools&#41;](visual-database-tools.md) informs you that the database server could not save the revised foreign-key table.</span></span> <span data-ttu-id="b56ab-111">데이터베이스에 수정 내용을 강제로 적용하려면 **만들 때 기존 데이터 검사** 확인란을 선택 취소하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-111">To force the database to accept the modification, you can clear the **Check existing data on creation** check box.</span></span>  
  
-   <span data-ttu-id="b56ab-112">**인덱싱된 뷰에 적용되는 테이블 수정** Microsoft SQL Server 인덱싱된 뷰에 적용되는 테이블을 수정하면 해당 뷰의 인덱스가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-112">**Modifying a Table Contributing to an Indexed View** If you modify a table that contributes to a Microsoft SQL Server indexed view, the indexes on the view will be lost.</span></span> <span data-ttu-id="b56ab-113">인덱스 다시 만들기에 대한 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b56ab-113">See the SQL Server Books Online for information on recreating indexes.</span></span>  
  
-   <span data-ttu-id="b56ab-114">**개체 삭제** 열, 테이블 또는 뷰와 같은 개체를 삭제하는 경우 데이터베이스의 다른 개체가 이러한 삭제 대상 개체를 참조하고 있지 않은지 먼저 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-114">**Deleting an Object** If you delete an object, such as a column, table, or view, check first to be sure that the object is not referenced by another object in the database.</span></span>  
  
 <span data-ttu-id="b56ab-115">데이터베이스 디자인을 변경하는 방법에 관계 없이 변경 기록을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-115">No matter how you alter the database design, you should retain a history of the alterations.</span></span> <span data-ttu-id="b56ab-116">프로덕션 데이터베이스의 모든 수정 내용에 대한 SQL 스크립트를 유지하는 것도 변경 기록을 유지하는 한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b56ab-116">One approach is to retain SQL scripts for all modifications that you ever make to your production database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56ab-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b56ab-117">See Also</span></span>  
 <span data-ttu-id="b56ab-118">[Unique 제약 조건 및 Check 제약 조건](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="b56ab-118">[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) </span></span>  
 [<span data-ttu-id="b56ab-119">다중 사용자 환경&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="b56ab-119">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](multiuser-environments-visual-database-tools.md)  
  
  
